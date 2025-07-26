# Vercel Deployment Guide for Your Portfolio

## Prerequisites
- A Vercel account (sign up at https://vercel.com if you don't have one)
- Your GitHub repository pushed to GitHub

## Step-by-Step Deployment

### 1. Connect to Vercel

1. Go to https://vercel.com/dashboard
2. Click "Add New..." → "Project"
3. Import your Git Repository:
   - Connect your GitHub account if not already connected
   - Find and select `techfreakworm.github.io` repository
   - Click "Import"

### 2. Configure Your Project

1. **Project Name**: Keep the default or change to your preference (e.g., `mayank-portfolio`)
2. **Framework Preset**: Vercel should auto-detect "Next.js"
3. **Root Directory**: Leave as is (`.` or `nextjs-portfolio` depending on your repo structure)
4. **Build Settings**: 
   - Build Command: `npm run build` (default)
   - Output Directory: Leave default
   - Install Command: `npm install` (default)

### 3. Environment Variables

Click on "Environment Variables" and add the following:

```
# Email Configuration (Required for contact form)
NEXT_PUBLIC_EMAILJS_SERVICE_ID=your_emailjs_service_id
NEXT_PUBLIC_EMAILJS_TEMPLATE_ID=your_emailjs_template_id
NEXT_PUBLIC_EMAILJS_PUBLIC_KEY=your_emailjs_public_key

# Google Analytics (Optional)
NEXT_PUBLIC_GTM=your_google_tag_manager_id

# reCAPTCHA (Optional, for form protection)
NEXT_PUBLIC_RECAPTCHA_SITE_KEY=your_recaptcha_site_key
NEXT_PUBLIC_RECAPTCHA_SECRET_KEY=your_recaptcha_secret_key
```

#### Setting up EmailJS (For Contact Form):

1. Go to https://www.emailjs.com/ and sign up
2. Create a new service:
   - Choose your email provider (Gmail, Outlook, etc.)
   - Follow the connection steps
   - Note your Service ID
3. Create an email template:
   - Go to "Email Templates" → "Create New Template"
   - Use variables like `{{from_name}}`, `{{from_email}}`, `{{message}}`
   - Note your Template ID
4. Get your Public Key from the "Account" page

#### Setting up Google Analytics (Optional):

1. Go to https://analytics.google.com/
2. Create a new property for your portfolio
3. Get your Measurement ID (starts with 'G-')
4. Use this as your `NEXT_PUBLIC_GTM` value

### 4. Deploy

1. Click "Deploy" button
2. Wait for the build to complete (usually 1-2 minutes)
3. Once deployed, you'll get a URL like `https://your-project.vercel.app`

### 5. Custom Domain (Optional)

To use your own domain:

1. Go to your project settings in Vercel
2. Navigate to "Domains"
3. Add your custom domain
4. Follow the DNS configuration instructions provided by Vercel

### 6. Post-Deployment

1. Test your contact form with the EmailJS integration
2. Verify all links and images are working
3. Check mobile responsiveness
4. Test the resume download link

## Updating Your Portfolio

After deployment, any push to your main branch will trigger an automatic deployment on Vercel.

```bash
# Make changes locally
git add .
git commit -m "Update portfolio"
git push origin master
```

## Troubleshooting

- **Build Errors**: Check the build logs in Vercel dashboard
- **Contact Form Not Working**: Verify EmailJS environment variables are correct
- **Images Not Loading**: Ensure all images are in the `public` folder
- **404 Errors**: Check that all internal links use Next.js `Link` component

## Environment Variables Reference

| Variable | Required | Description |
|----------|----------|-------------|
| NEXT_PUBLIC_EMAILJS_SERVICE_ID | Yes | EmailJS service identifier |
| NEXT_PUBLIC_EMAILJS_TEMPLATE_ID | Yes | EmailJS template identifier |
| NEXT_PUBLIC_EMAILJS_PUBLIC_KEY | Yes | EmailJS public API key |
| NEXT_PUBLIC_GTM | No | Google Tag Manager ID |
| NEXT_PUBLIC_RECAPTCHA_SITE_KEY | No | reCAPTCHA site key |
| NEXT_PUBLIC_RECAPTCHA_SECRET_KEY | No | reCAPTCHA secret key |

## Notes

- The free Vercel plan includes:
  - Unlimited deployments
  - HTTPS by default
  - Global CDN
  - Automatic SSL certificates
- Your site will be accessible at multiple URLs:
  - `https://your-project.vercel.app`
  - `https://your-project-git-main.vercel.app`
  - Your custom domain (if configured)