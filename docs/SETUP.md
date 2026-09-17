# PixelNest - Setup Instructions

This document contains comprehensive setup instructions for the PixelNest image gallery project.

## Prerequisites

- Node.js 14 or higher
- npm or yarn package manager
- Firebase account with:
  - Firestore Database enabled
  - Storage enabled
  - Authentication enabled (Email/Password provider)
  - Service account key for Admin SDK

## Step 1: Firebase Setup

### Create Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com)
2. Click "Create a new project"
3. Enter project name: "PixelNest"
4. Follow the setup wizard
### Enable Services
1. **Authentication**
   - Go to Build > Authentication
   - Click "Get Started"
   - Enable Email/Password provider

2. **Firestore Database**
   - Go to Build > Firestore Database
   - Click "Create database"
   - Start in production mode
   - Choose your region

3. **Cloud Storage**
   - Go to Build > Storage
   - Click "Get started"
   - Create storage bucket

### Get Credentials

#### For Frontend (Web App)
1. Go to Project Settings (gear icon)
2. Click on your web app
3. Copy the config object
4. You'll need these values:
   - apiKey
   - authDomain
   - projectId
   - storageBucket
   - messagingSenderId
   - appId

#### For Backend (Admin SDK)
1. Go to Project Settings > Service Accounts
2. Click "Generate New Private Key"
3. Save the JSON file securely
4. You'll need:
   - project_id
   - private_key
   - client_email

## Step 2: Frontend Setup

```bash
cd frontend

# Copy environment template
cp .env.example .env

# Edit .env with your Firebase credentials
# Find the values from Step 1
nano .env
# or use your preferred editor
```

Update `.env` with:
```
REACT_APP_FIREBASE_API_KEY=your_api_key
REACT_APP_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
REACT_APP_FIREBASE_PROJECT_ID=your_project_id
REACT_APP_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
REACT_APP_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
REACT_APP_FIREBASE_APP_ID=your_app_id
REACT_APP_BACKEND_URL=http://localhost:5000
```

```bash
# Install dependencies
npm install

# Start development server
npm start
```

Visit `http://localhost:3000`

## Step 3: Backend Setup

```bash
cd backend

# Copy environment template
cp .env.example .env

# Edit .env with your Firebase Admin credentials
nano .env
# or use your preferred editor
```

Update `.env` with:
```
PORT=5000
NODE_ENV=development
FIREBASE_PROJECT_ID=your_project_id
FIREBASE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\n...\n-----END PRIVATE KEY-----\n"
FIREBASE_CLIENT_EMAIL=your_client_email
MAX_FILE_SIZE=52428800
FRONTEND_URL=http://localhost:3000
```

```bash
# Install dependencies
npm install

# Start development server
npm run dev
```

The API will be running on `http://localhost:5000`

## Step 4: Firebase Firestore Security Rules

Go to Firestore > Rules and update with:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Allow public read for images
    match /images/{document=**} {
      allow read;
      allow create: if request.auth != null;
      allow update, delete: if request.auth.uid == resource.data.creatorId;
    }
    
    // Allow users to read/write their own profile
    match /users/{userId} {
      allow read;
      allow write: if request.auth.uid == userId;
    }
  }
}
```

## Step 5: Firebase Storage Rules

Go to Storage > Rules and update with:

```
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    // Allow authenticated users to upload images
    match /images/{allPaths=**} {
      allow read;
      allow write: if request.auth != null;
    }
    
    // Allow authenticated users to upload thumbnails
    match /thumbnails/{allPaths=**} {
      allow read;
      allow write: if request.auth != null;
    }
  }
}
```

## Step 6: Testing

### Test Authentication
1. Go to `http://localhost:3000/login`
2. Click "Sign Up"
3. Enter email and password
4. Create account

### Test Upload
1. After login, go to `/upload`
2. Select an image file
3. Fill in title and optional metadata
4. Click Upload

### Test API Directly
```bash
# Health check
curl http://localhost:5000/api/health

# Get images
curl http://localhost:5000/api/images

# Get single image
curl http://localhost:5000/api/images/{imageId}
```

## Common Issues & Solutions

### Port Already in Use
```bash
# On Windows (PowerShell)
Get-Process -Id (Get-NetTCPConnection -LocalPort 5000).OwningProcess
Stop-Process -Id {PID} -Force

# On macOS/Linux
lsof -ti:5000 | xargs kill -9
```

### Firebase Connection Error
- Add your IP/domain to Firebase Storage CORS settings
- Verify service account key is valid
- Check Firestore rules allow operations

### CORS Error
- Ensure FRONTEND_URL in backend .env matches your frontend URL
- Clear browser cache

### Image Upload Fails
- Check file size (max 50MB by default)
- Verify file format (JPEG, PNG, GIF, WebP)
- Check Firebase Storage quota

### Cannot Create User
- Verify Email/Password provider is enabled in Firebase Console
- Check user doesn't already exist

## Deployment

### Deploy Frontend to Vercel
```bash
cd frontend
npm install -g vercel
vercel
```

### Deploy Backend to Heroku
```bash
cd backend
heroku login
heroku create pixelnest-backend
git push heroku main
```

Set environment variables on Heroku:
```bash
heroku config:set FIREBASE_PROJECT_ID=...
heroku config:set FIREBASE_PRIVATE_KEY=...
heroku config:set FIREBASE_CLIENT_EMAIL=...
heroku config:set FRONTEND_URL=https://your-frontend-url.com
```

## Development Workflow

1. **Start services**
   ```bash
   # Terminal 1 - Frontend
   cd frontend
   npm start

   # Terminal 2 - Backend
   cd backend
   npm run dev
   ```

2. **Make changes** to code
3. **Test in browser** at `http://localhost:3000`
4. **Check API** at `http://localhost:5000`
5. **Push to git** when ready

## Project Structure
- `frontend/` - React application
- `backend/` - Node.js/Express API
- `docs/` - Documentation
- `README.md` - Main project README

## Resources

- [Firebase Documentation](https://firebase.google.com/docs)
- [React Documentation](https://react.dev)
- [Express.js Guide](https://expressjs.com)
- [Firestore Best Practices](https://firebase.google.com/docs/firestore/best-practices)

## Next Steps

1. ✅ Set up Firebase project
2. ✅ Configure frontend environment
3. ✅ Configure backend environment
4. ✅ Start both services
5. [ ] Design UI in Figma (Phase 1)
6. [ ] Implement additional features
7. [ ] Deploy to production

---

For questions or issues, please refer to the [README.md](../README.md) or create an issue on GitHub.
