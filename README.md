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

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details

## 🤝 Support

For support, email support@pixelnest.com or open an issue in the repository.


## 🙏 Acknowledgments

- Firebase for providing excellent backend services
- The React community for amazing tools and libraries
- All contributors and supporters

---

**Happy image sharing! 🖼️**
