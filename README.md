# MyBlogsWebsite

A modern, feature-rich blog website built with Flask and Bootstrap. This web application allows users to read blog posts, register accounts, leave comments, and provides admin functionality for managing blog content.

## Features

### 🌟 Core Functionality
- **Blog Posts**: Display and read blog posts with rich text content
- **User Authentication**: Secure user registration and login system
- **Comment System**: Registered users can leave comments on blog posts
- **Admin Panel**: Administrative users can create, edit, and delete blog posts
- **Responsive Design**: Modern, mobile-friendly interface using Bootstrap 5

### 🔐 Security Features
- Password hashing with Werkzeug security
- User session management with Flask-Login
- Admin-only decorators for protected routes
- CSRF protection with Flask-WTF

### 🎨 User Interface
- Clean, professional blog layout
- Rich text editor (CKEditor) for blog content and comments
- Gravatar integration for user profile images
- Modern CSS styling with custom themes

## Technology Stack

- **Backend**: Flask (Python web framework)
- **Database**: SQLAlchemy with SQLite (development) / PostgreSQL (production)
- **Frontend**: Bootstrap 5, HTML5, CSS3, JavaScript
- **Authentication**: Flask-Login
- **Forms**: WTForms with Flask-WTF
- **Rich Text**: CKEditor
- **Deployment**: Heroku-ready with Gunicorn

## Installation & Setup

### Prerequisites
- Python 3.7 or higher
- pip (Python package manager)

### Local Development Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/Pranay-Dommati/MyBlogsWebsite.git
   cd MyBlogsWebsite-master
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv blog_env
   source blog_env/bin/activate  # On Windows: blog_env\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set environment variables**
   Create a `.env` file in the root directory:
   ```
   SECRET_KEY=your-secret-key-here
   DATABASE_URI=sqlite:///posts.db
   ```

5. **Initialize the database**
   ```bash
   python main.py
   ```
   The database will be automatically created on first run.

6. **Access the application**
   Open your browser and navigate to `http://localhost:5001`

## Usage

### For Visitors
- Browse and read blog posts on the homepage
- View individual blog posts with full content
- Access About and Contact pages

### For Registered Users
- Register for an account using email and password
- Login to access additional features
- Leave comments on blog posts
- View and interact with other users' comments

### For Administrators
The first registered user (ID: 1) automatically becomes the admin and can:
- Create new blog posts with rich text content
- Edit existing blog posts
- Delete blog posts
- Manage all site content

## Project Structure

```
MyBlogsWebsite-master/
├── main.py              # Main Flask application
├── forms.py             # WTForms form definitions
├── requirements.txt     # Python dependencies
├── Procfile            # Heroku deployment configuration
├── static/             # Static assets
│   ├── assets/         # Images and icons
│   ├── css/           # Custom stylesheets
│   └── js/            # JavaScript files
└── templates/          # HTML templates
    ├── header.html     # Navigation header
    ├── footer.html     # Page footer
    ├── index.html      # Homepage
    ├── post.html       # Individual post view
    ├── make-post.html  # Create/edit post form
    ├── login.html      # Login page
    ├── register.html   # Registration page
    ├── about.html      # About page
    └── contact.html    # Contact page
```

## Database Schema

### BlogPost Model
- `id`: Primary key
- `title`: Post title (unique)
- `subtitle`: Post subtitle
- `date`: Publication date
- `body`: Post content (rich text)
- `img_url`: Featured image URL
- `author_id`: Foreign key to User
- `comments`: Relationship to Comment model

### User Model
- `id`: Primary key
- `email`: User email (unique)
- `password`: Hashed password
- `name`: Display name
- `posts`: Relationship to BlogPost model
- `comments`: Relationship to Comment model

### Comment Model
- `id`: Primary key
- `text`: Comment content
- `author_id`: Foreign key to User
- `post_id`: Foreign key to BlogPost

### Environment Variables

Required environment variables for production:
- `SECRET_KEY`: Flask secret key for session management
- `DATABASE_URI`: Database connection string (PostgreSQL for Heroku)

## Customization

### Styling
- Modify `static/css/styles.css` for custom styling
- Update background images in `static/assets/img/`
- Customize the site title and subtitle in `templates/index.html`

### Email Integration (Optional)
The application includes commented code for contact form email functionality. To enable:
1. Uncomment the email-related code in `main.py`
2. Set up email environment variables
3. Configure SMTP settings

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Create a Pull Request

## Support

For questions, issues, or suggestions, please open an issue in the GitHub repository.
