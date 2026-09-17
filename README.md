# PixelNest Image Gallery

> Modern image-sharing web platform where users can upload, explore, and organize images

## 🎯 Project Overview

PixelNest is a full-stack web application designed to provide a minimal and distraction-free image browsing experience. The platform enables users to:

- ✨ Upload and share images
- 🔍 Explore images through a beautiful masonry grid
- 🏷️ Organize images with tags and categories
- 🎨 View color palettes extracted from images
- 📊 Access image metadata and insights
- 👤 Create and manage user profiles
- ⬇️ Download images with ease

## 🛠️ Tech Stack

### Frontend
- **Framework**: React 18
- **Routing**: React Router v6
- **Authentication**: Firebase Authentication
- **Storage**: Firebase Cloud Storage
- **HTTP Client**: Axios
- **Icons**: React Icons
- **Styling**: CSS3

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: Firebase Firestore
- **File Storage**: Firebase Cloud Storage
- **Image Processing**: Sharp, Jimp
- **Color Analysis**: Vibrant
- **Middleware**: Multer for file uploads

### Infrastructure
- **Authentication**: Firebase Admin SDK
- **Hosting**: Can be deployed to Firebase Hosting, Vercel, or any Node.js server
- **Environment**: .env configuration

## 📁 Project Structure

```
PixelNest/
├── frontend/               # React frontend application
│   ├── public/            # Static files
│   ├── src/
│   │   ├── components/    # Reusable components
│   │   ├── pages/         # Page components
│   │   ├── utils/         # Utility functions and APIs
│   │   ├── styles/        # CSS files
│   │   └── assets/        # Images and assets
│   └── package.json
├── backend/               # Node/Express backend
│   ├── src/
│   │   ├── controllers/   # Route controllers
│   │   ├── routes/        # API routes
│   │   ├── middleware/    # Custom middleware
│   │   ├── config/        # Configuration files
│   │   └── utils/         # Utility functions
│   └── server.js
├── docs/                  # Documentation
└── README.md
```

## 🚀 Getting Started

### Prerequisites
- Node.js 14 or higher
- npm or yarn
- Firebase project with Firestore and Storage enabled
- Firebase project credentials

### Setup

#### 1. Clone the repository
```bash
git clone https://github.com/yourusername/pixelnest.git
cd pixelnest
```

#### 2. Frontend Setup

```bash
cd frontend

# Copy environment template
cp .env.example .env

# Install dependencies
npm install

# Update .env with your Firebase credentials
# REACT_APP_FIREBASE_API_KEY=your_key
# REACT_APP_FIREBASE_AUTH_DOMAIN=your_domain
# ... etc

# Start development server
npm start
```

The frontend will be available at `http://localhost:3000`

#### 3. Backend Setup

```bash
cd backend

# Copy environment template
cp .env.example .env

# Install dependencies
npm install

# Update .env with your Firebase Admin credentials
# FIREBASE_PROJECT_ID=your_project_id
# FIREBASE_PRIVATE_KEY=your_private_key
# ... etc

# Start development server
npm run dev
```

The backend will be available at `http://localhost:5000`

## 🔑 Environment Variables

### Frontend (.env)
```
REACT_APP_FIREBASE_API_KEY=
REACT_APP_FIREBASE_AUTH_DOMAIN=
REACT_APP_FIREBASE_PROJECT_ID=
REACT_APP_FIREBASE_STORAGE_BUCKET=
REACT_APP_FIREBASE_MESSAGING_SENDER_ID=
REACT_APP_FIREBASE_APP_ID=
REACT_APP_BACKEND_URL=http://localhost:5000
```

### Backend (.env)
```
PORT=5000
NODE_ENV=development
FIREBASE_PROJECT_ID=
FIREBASE_PRIVATE_KEY=
FIREBASE_CLIENT_EMAIL=
MAX_FILE_SIZE=52428800
FRONTEND_URL=http://localhost:3000
```

## 📚 API Documentation

### Images Endpoints

#### Get Images (Paginated)
```
GET /api/images?page=1&limit=20
```

#### Get Image by ID
```
GET /api/images/:id
```

#### Upload Image
```
POST /api/images/upload
Headers: Authorization: Bearer {idToken}
Content-Type: multipart/form-data
Body:
  - file: image file
  - title: string
  - description: string (optional)
  - tags: array of strings
```

#### Delete Image
```
DELETE /api/images/:id
Headers: Authorization: Bearer {idToken}
```

#### Get Images by Tag
```
GET /api/images/tag/:tagName
```

#### Get Image Metadata
```
GET /api/images/:id/metadata
```

#### Get Color Palette
```
GET /api/images/:id/palette
```

### Users Endpoints

#### Get User Profile
```
GET /api/users/:userId/profile
```

#### Update User Profile
```
PUT /api/users/:userId/profile
Headers: Authorization: Bearer {idToken}
Body:
  - displayName: string
  - bio: string
  - email: string
```

#### Get User Images
```
GET /api/users/:userId/images
```

#### Get User Stats
```
GET /api/users/:userId/stats
```

## 🎨 Features

### Phase 1: UI/UX Design (Current)
- [x] Home Feed - Masonry style grid with infinite scrolling
- [x] Upload Page - Image upload with metadata
- [x] Image Detail Page - Full image view with metadata
- [x] User Profile Page - User information and uploaded images
- [x] Tag/Category Page - Images filtered by tag

### Phase 2: Features (Planned)
- [ ] Image search functionality
- [ ] Advanced filtering and sorting
- [ ] User follow system
- [ ] Image likes and comments
- [ ] Collections/Albums
- [ ] Image sharing
- [ ] Admin dashboard

## 📱 Responsive Design

The application is fully responsive and works on:
- Desktop (1920px and above)
- Tablet (768px - 1024px)
- Mobile (320px - 767px)

## 🔐 Security

- Firebase Authentication for user management
- JWT token verification for protected routes
- Input validation and sanitization
- CORS enabled for frontend communication
- File upload restrictions (size and format)

## 🐛 Known Issues

- Color palette extraction may not work for all image types
- Some EXIF data might not be preserved during upload

## 📝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details

## 🤝 Support

For support, email support@pixelnest.com or open an issue in the repository.

## 📞 Contact

- **Project Lead**: Your Name
- **Email**: your.email@example.com
- **GitHub**: https://github.com/yourusername

## 🙏 Acknowledgments

- Firebase for providing excellent backend services
- The React community for amazing tools and libraries
- All contributors and supporters

---

**Happy image sharing! 🖼️**
