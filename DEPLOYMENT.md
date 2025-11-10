# Deployment Guide - Feasibilizer App v2

## Quick Deploy Options

### Option 1: Streamlit Cloud (Recommended - FREE)

1. **Create GitHub Repository for v2**
   - Go to [GitHub](https://github.com) and create a new repository: `arayasuryanto/feasibilitizer-app-v2`
   - Make it public
   - Don't initialize with README (we already have files)

2. **Push to GitHub**
   ```bash
   git remote add origin https://github.com/arayasuryanto/feasibilitizer-app-v2.git
   git branch -M main
   git push -u origin main
   ```

3. **Deploy to Streamlit Cloud**
   - Go to [share.streamlit.io](https://share.streamlit.io)
   - Click "New app"
   - Select your repository: `arayasuryanto/feasibilitizer-app-v2`
   - Main file path: `app.py`
   - Click "Deploy"

4. **Access Your App**
   - URL will be: `https://arayasuryanto-feasibilitizer-app-v2-app-xxxxx.streamlit.app`
   - Share this URL with users!

---

### Option 2: Local Deployment

```bash
# Clone the repository
git clone https://github.com/arayasuryanto/feasibilitizer-app-v2.git
cd feasibilitizer-app-v2

# Install dependencies
pip install -r requirements.txt

# Run the app
streamlit run app.py
```

Access at: `http://localhost:8501`

---

### Option 3: Heroku Deployment

1. **Create Heroku App**
   ```bash
   heroku create feasibilitizer-app-v2
   ```

2. **Add Buildpack**
   ```bash
   heroku buildpacks:add heroku/python
   ```

3. **Create Procfile**
   ```bash
   echo "web: streamlit run app.py --server.port=\$PORT" > Procfile
   ```

4. **Create setup.sh**
   ```bash
   cat > setup.sh << 'EOF'
   mkdir -p ~/.streamlit/
   echo "\
   [server]\n\
   headless = true\n\
   port = $PORT\n\
   enableCORS = false\n\
   \n\
   " > ~/.streamlit/config.toml
   EOF
   ```

5. **Deploy**
   ```bash
   git add Procfile setup.sh
   git commit -m "Add Heroku deployment files"
   git push heroku main
   ```

---

### Option 4: Docker Deployment

1. **Create Dockerfile**
   ```dockerfile
   FROM python:3.10-slim

   WORKDIR /app

   COPY requirements.txt .
   RUN pip install -r requirements.txt

   COPY . .

   EXPOSE 8501

   CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]
   ```

2. **Build and Run**
   ```bash
   docker build -t feasibilitizer-app-v2 .
   docker run -p 8501:8501 feasibilitizer-app-v2
   ```

---

### Option 5: AWS EC2 Deployment

1. **Launch EC2 Instance**
   - Ubuntu 22.04 LTS
   - t2.micro (free tier)
   - Security group: Allow port 8501

2. **SSH and Setup**
   ```bash
   ssh -i your-key.pem ubuntu@your-ec2-ip

   # Install Python and dependencies
   sudo apt update
   sudo apt install python3-pip -y

   # Clone repository
   git clone https://github.com/arayasuryanto/feasibilitizer-app-v2.git
   cd feasibilitizer-app-v2

   # Install requirements
   pip3 install -r requirements.txt

   # Run with screen
   screen -S feasibilitizer
   streamlit run app.py --server.port=8501 --server.address=0.0.0.0
   ```

3. **Access**
   - `http://your-ec2-ip:8501`

---

## Environment Variables (if needed)

Create `.env` file:
```bash
# Optional configurations
STREAMLIT_SERVER_PORT=8501
STREAMLIT_SERVER_ADDRESS=0.0.0.0
STREAMLIT_SERVER_HEADLESS=true
```

---

## Post-Deployment Checklist

### Immediate Actions
- [ ] Test all features on deployed version
- [ ] Verify calculations match local version
- [ ] Test on different devices (mobile, tablet, desktop)
- [ ] Share URL with stakeholders
- [ ] Monitor initial user feedback

### Security (for production)
- [ ] Add authentication if needed
- [ ] Configure HTTPS (automatic on Streamlit Cloud)
- [ ] Set up monitoring and alerts
- [ ] Regular backups if using database

### Performance Optimization
- [ ] Monitor load times
- [ ] Optimize for mobile if needed
- [ ] Set up caching for better performance
- [ ] Consider CDN for assets

---

## Monitoring & Maintenance

### Streamlit Cloud
- Built-in analytics dashboard
- Automatic updates from GitHub
- Free SSL certificate
- Automatic scaling

### Self-Hosted
- Monitor with `htop` or similar
- Set up log rotation
- Configure auto-restart on failure
- Regular security updates

---

## Updating the App

### Streamlit Cloud
```bash
# Make changes locally
git add .
git commit -m "Update: description"
git push origin main

# Streamlit Cloud auto-deploys!
```

### Self-Hosted
```bash
# On server
cd feasibilitizer-app-v2
git pull origin main
# Restart streamlit
```

---

## Custom Domain (Optional)

### Streamlit Cloud
- Settings → Custom domain
- Add CNAME record: `your-domain.com → your-app.streamlit.app`

### Self-Hosted
- Use nginx as reverse proxy
- Configure SSL with Let's Encrypt
- Point domain to your server IP

---

## Troubleshooting Deployment

### App Won't Start
1. Check Python version (3.8+)
2. Verify all dependencies installed
3. Check port availability
4. Review error logs

### Performance Issues
1. Reduce initial data load
2. Implement caching
3. Optimize calculations
4. Consider upgrading hosting tier

### Connection Issues
1. Check firewall rules
2. Verify port forwarding
3. Test with `curl http://localhost:8501`
4. Check security group settings (cloud)

---

## Cost Estimates

| Platform | Cost | Notes |
|----------|------|-------|
| **Streamlit Cloud** | FREE | Best for most users |
| **Heroku** | $0-7/month | Hobby tier |
| **AWS EC2** | ~$5-10/month | t2.micro |
| **DigitalOcean** | $5/month | Basic droplet |
| **Docker (local)** | FREE | Self-hosted |

---

## Recommended Setup for Different Use Cases

### Personal Use
→ **Local deployment** (free, full control)

### Small Team (1-50 users)
→ **Streamlit Cloud** (free, easy, reliable)

### Company/Organization
→ **AWS/Azure/GCP** (scalable, secure, professional)

### High Traffic
→ **Kubernetes cluster** (auto-scaling, high availability)

---

## Support & Resources

- **GitHub Issues:** https://github.com/arayasuryanto/feasibilitizer-app-v2/issues
- **Streamlit Docs:** https://docs.streamlit.io
- **Community Forum:** https://discuss.streamlit.io

---

## Success Metrics

Track these after deployment:
- [ ] Number of active users
- [ ] Average session duration
- [ ] Number of analyses created
- [ ] Feature usage statistics
- [ ] User feedback and ratings

---

**Ready to deploy! Choose the option that best fits your needs.**

**Recommended for most users:** Streamlit Cloud (Option 1) - Free, easy, and reliable.
