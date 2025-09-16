# Deployment Guide - අකුරු මිතුරා

This guide will help you deploy the Akuru Mithura application to various hosting platforms.

## Quick Start

The application is a static website that can be deployed to any web hosting service. No server-side code is required.

## Deployment Options

### 1. GitHub Pages (Free)

**Steps:**
1. Create a new repository on GitHub
2. Upload all files to the repository
3. Go to Settings > Pages
4. Select "Deploy from a branch"
5. Choose "main" branch and "/ (root)" folder
6. Click "Save"
7. Your site will be available at `https://your-username.github.io/repository-name`

**Pros:**
- Free hosting
- Automatic HTTPS
- Easy to update (just push changes)
- Custom domain support

**Cons:**
- Public repository required for free tier
- Limited to static sites

### 2. Netlify (Recommended)

**Steps:**
1. Go to [netlify.com](https://netlify.com)
2. Sign up/login with GitHub
3. Click "New site from Git"
4. Connect your GitHub repository
5. Set build command: `echo "No build needed"`
6. Set publish directory: `/` (root)
7. Click "Deploy site"

**Pros:**
- Free tier available
- Automatic deployments
- Custom domain support
- Form handling
- Branch previews

**Cons:**
- Limited build minutes on free tier

### 3. Vercel

**Steps:**
1. Go to [vercel.com](https://vercel.com)
2. Sign up with GitHub
3. Import your repository
4. Vercel will auto-detect it's a static site
5. Click "Deploy"

**Pros:**
- Excellent performance
- Global CDN
- Automatic deployments
- Custom domains

**Cons:**
- Limited bandwidth on free tier

### 4. Firebase Hosting

**Steps:**
1. Install Firebase CLI: `npm install -g firebase-tools`
2. Login: `firebase login`
3. Initialize: `firebase init hosting`
4. Select your project directory
5. Deploy: `firebase deploy`

**Pros:**
- Google integration
- Fast global CDN
- Custom domains
- SSL certificates

### 5. Traditional Web Hosting

Upload all files to your web server's public directory (usually `public_html` or `www`).

## Google Drive Setup

### For Production Deployment

1. **Create Google Cloud Project:**
   - Go to [Google Cloud Console](https://console.cloud.google.com/)
   - Create a new project
   - Enable Google Drive API

2. **Create Service Account:**
   - Go to IAM & Admin > Service Accounts
   - Create service account
   - Download JSON key file
   - Note the service account email

3. **Setup Drive Folder:**
   - Create a folder in Google Drive
   - Share folder with service account email
   - Give "Editor" permissions
   - Copy folder ID from URL

4. **Configure in App:**
   - Go to `/admin.html` in your deployed app
   - Enter service account JSON key
   - Enter folder ID
   - Test connection

## Environment Configuration

### Required Environment Variables
None required - all configuration is done through the admin interface.

### Optional Environment Variables
- `GOOGLE_DRIVE_FOLDER_ID`: Default folder ID
- `GOOGLE_SERVICE_ACCOUNT_KEY`: Default service account key

## Security Considerations

1. **Service Account Key:**
   - Keep JSON key secure
   - Don't commit to version control
   - Use environment variables in production

2. **Data Privacy:**
   - All data stored locally in browser
   - Google Drive upload is optional
   - No personal data sent to external servers

3. **HTTPS:**
   - Always use HTTPS in production
   - Required for microphone access
   - Required for some browser APIs

## Performance Optimization

### Before Deployment
1. **Minify CSS/JS** (optional):
   ```bash
   # Install minifier
   npm install -g clean-css-cli uglify-js
   
   # Minify CSS
   clean-css -o styles.min.css styles.css
   
   # Minify JS
   uglifyjs script.js -o script.min.js
   ```

2. **Optimize Images:**
   - Use WebP format where possible
   - Compress images
   - Use appropriate sizes

3. **Enable Compression:**
   - Most hosting platforms enable gzip automatically
   - Check with your hosting provider

### After Deployment
1. **Test Performance:**
   - Use Google PageSpeed Insights
   - Test on mobile devices
   - Check loading times

2. **Monitor Usage:**
   - Set up Google Analytics (optional)
   - Monitor server logs
   - Track user engagement

## Troubleshooting

### Common Issues

1. **Google Drive Not Working:**
   - Check service account permissions
   - Verify folder ID is correct
   - Ensure Drive API is enabled

2. **Voice Features Not Working:**
   - Requires HTTPS
   - Check microphone permissions
   - Use Chrome/Edge browser

3. **Data Not Saving:**
   - Check browser localStorage support
   - Clear browser cache
   - Try different browser

4. **Styling Issues:**
   - Check font loading
   - Verify CSS file paths
   - Test on different devices

### Support
- Check the help page in the application
- Contact: support@writeease.lk
- Phone: 070 422 6267

## Maintenance

### Regular Tasks
1. **Update Dependencies:**
   - Check for security updates
   - Update CDN links if needed

2. **Monitor Performance:**
   - Check loading times
   - Monitor user feedback
   - Update content as needed

3. **Backup Data:**
   - Export data regularly
   - Keep backups of configuration
   - Test restore procedures

### Updates
1. **Code Updates:**
   - Push changes to repository
   - Deploy automatically (if configured)
   - Test in staging environment first

2. **Content Updates:**
   - Update through admin interface
   - Add new games/activities
   - Improve user experience

## Custom Domain Setup

### GitHub Pages
1. Add `CNAME` file with your domain
2. Configure DNS records
3. Enable HTTPS in repository settings

### Netlify
1. Go to Site Settings > Domain Management
2. Add custom domain
3. Configure DNS records
4. Enable HTTPS

### Vercel
1. Go to Project Settings > Domains
2. Add domain
3. Configure DNS records
4. SSL automatically enabled

## Monitoring and Analytics

### Google Analytics (Optional)
1. Create Google Analytics account
2. Add tracking code to HTML files
3. Monitor user behavior
4. Track conversion rates

### Error Monitoring
1. Use services like Sentry
2. Monitor JavaScript errors
3. Track user feedback
4. Improve user experience

---

**Ready to deploy?** Choose your preferred platform and follow the steps above. The application is designed to work seamlessly across all major hosting platforms!
