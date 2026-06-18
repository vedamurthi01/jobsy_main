# 🚀 Jobsy Deployment Guide - DigitalOcean

## Prerequisites
1. DigitalOcean account
2. GitHub repository with your code
3. MongoDB Atlas database (or DigitalOcean Managed Database)
4. Twilio account for SMS
5. Gmail account for email notifications

## Deployment Steps

### Step 1: Prepare Environment Variables
Create a `.env` file for your backend with these variables:
```
# Database
MONGODB_URI=your-mongodb-atlas-connection-string
db_host=your-db-host
db_name=your-db-name
db_user=your-db-username
db_pwd=your-db-password

# Email Service
admin_mail=your-gmail@gmail.com
admin_mail_pass=your-gmail-app-password

# SMS Service (Twilio)
twilio_sid=your-twilio-account-sid
twilio_auth_token=your-twilio-auth-token
admin_phone=your-twilio-phone-number

# Server
PORT=8080
NODE_ENV=production
```

### Step 2: Update Frontend Environment
The frontend `.env.production` file should contain:
```
REACT_APP_API_URL=https://your-backend-app.ondigitalocean.app
```

### Step 3: Deploy on DigitalOcean App Platform

#### Option A: Using DigitalOcean Dashboard
1. Login to DigitalOcean Control Panel
2. Navigate to "Apps" → "Create App"
3. Connect your GitHub repository
4. Configure two components:

**Backend Service:**
- Name: `jobsy-backend`
- Environment: Node.js
- Source Directory: `/backend`
- Build Command: `npm install`
- Run Command: `npm start`
- Port: `8080`
- Environment Variables: (Add all the variables from Step 1)

**Frontend Service:**
- Name: `jobsy-frontend`  
- Environment: Static Site
- Source Directory: `/frontend`
- Build Command: `npm install && npm run build` (Node.js 16.x required)
- Output Directory: `build`
- Environment Variables:
  - `REACT_APP_API_URL`: `${jobsy-backend.PUBLIC_URL}` (DigitalOcean will auto-resolve this)

#### Option B: Using App Spec (app.yaml)
1. Use the provided `.do/app.yaml` file
2. Update the environment variables in the file
3. Deploy using: `doctl apps create --spec .do/app.yaml`

### Step 4: Configure Domain (Optional)
1. In App settings, go to "Domains"
2. Add your custom domain
3. Update DNS records as instructed
4. Enable "Force HTTPS"

### Step 5: Database Setup
Make sure your MongoDB Atlas:
1. Allows connections from DigitalOcean IPs (0.0.0.0/0 for now)
2. Has the correct connection string in environment variables
3. Contains the necessary collections (users, jobs)

### Step 6: Test Deployment
1. Frontend URL: `https://your-app-name.ondigitalocean.app`
2. Backend URL: `https://your-backend-name.ondigitalocean.app`
3. Test user registration, job posting, and applications

## Environment Variables Reference

### Backend Environment Variables
| Variable | Description | Example |
|----------|-------------|---------|
| `MONGODB_URI` | Full MongoDB connection string | `mongodb+srv://user:pass@cluster.mongodb.net/jobsy` |
| `admin_mail` | Gmail for sending notifications | `your-email@gmail.com` |
| `admin_mail_pass` | Gmail app password | `your-app-password` |
| `twilio_sid` | Twilio Account SID | `ACxxxxxxxxxxxxx` |
| `twilio_auth_token` | Twilio Auth Token | `your-auth-token` |
| `admin_phone` | Twilio phone number | `+1234567890` |
| `PORT` | Server port | `8080` |

### Frontend Environment Variables
| Variable | Description | Example |
|----------|-------------|---------|
| `REACT_APP_API_URL` | Backend API URL | `https://backend.ondigitalocean.app` |

## Troubleshooting

### Common Issues:
1. **CORS Errors**: Make sure your backend allows the frontend domain
2. **Environment Variables**: Double-check all variables are set correctly
3. **Database Connection**: Ensure MongoDB Atlas allows DigitalOcean IPs
4. **API Calls**: Verify all hardcoded localhost URLs are updated
5. **Node.js Build Errors**: 
   - If you see `digital envelope routines::unsupported` error
   - Make sure frontend uses Node.js 16.x (specified in package.json engines)
   - DigitalOcean should automatically use the correct Node version

### Logs:
- View logs in DigitalOcean App Platform dashboard
- Check both frontend build logs and backend runtime logs

## Post-Deployment Checklist
- [ ] Frontend loads without errors
- [ ] User registration works
- [ ] Job posting functionality works  
- [ ] Job applications send notifications
- [ ] Email notifications are sent
- [ ] SMS notifications are sent (to verified numbers)
- [ ] All job categories display correctly
- [ ] Voice navigation works
- [ ] Multi-language support functions

## Cost Optimization
- Start with Basic tier ($5/month per service)
- Monitor usage and scale as needed
- Consider using DigitalOcean Managed Database for production

## Security Notes
- Never commit environment variables to GitHub
- Use strong passwords for all services
- Enable 2FA on all accounts
- Regularly rotate API keys and passwords
