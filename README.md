# Networking Lab

This lab documents the setup of an EC2 instance with NGINX and connecting it to a custom domain using Cloudflare.

---

## 1. What I Built

- Launched an **AWS EC2 instance**:
  - Ubuntu 24.04 LTS
  - t3.micro instance
  - Security group allowing **SSH (22)** and **HTTP (80)**
- Installed and configured **NGINX** as a web server
- Connected **networking-lab.uk** domain via **Cloudflare DNS**
  - A records for `@` and `www` pointing to EC2 public IP `18.169.184.240`
  - Temporarily set to **DNS Only (grey cloud)** to bypass Cloudflare proxy
- Verified that the website loads the **NGINX Welcome Page**

---

## 2. Commands Used

\`\`\`bash
# Update package index
sudo apt update -y

# Install NGINX
sudo apt install nginx -y

# Enable NGINX to start on boot
sudo systemctl enable nginx

# Start NGINX
sudo systemctl start nginx

# Check NGINX status
sudo systemctl status nginx
\`\`\`

---

## 3. DNS Configuration

- **Cloudflare DNS Records**:

| Type | Name | Content          | Proxy Status |
|------|------|-----------------|--------------|
| A    | @    | 18.169.184.240  | DNS Only     |
| A    | www  | 18.169.184.240  | DNS Only     |

- Waited for DNS propagation (~1–5 minutes)
- Verified with:

\`\`\`bash
nslookup networking-lab.uk
ping networking-lab.uk
\`\`\`

---

## 4. Screenshots

1. **EC2 Instance Running NGINX**  
   ![EC2 NGINX Screenshot](screenshots/ec2_nginx.png)

2. **Cloudflare DNS Records**  
   ![Cloudflare DNS Screenshot](screenshots/cloudflare_dns.png)

3. **Website in Browser**  
   ![Website Screenshot](screenshots/nginx_browser.png)

> Replace `screenshots/...` with the actual paths of your screenshots in the repository.

---

## 5. Lessons Learned

- How to **launch an EC2 instance** and configure security groups  
- Installing and managing **NGINX on Ubuntu**  
- Connecting a **custom domain via Cloudflare DNS**  
- Understanding how Cloudflare **orange cloud (proxy)** affects direct access  
- Basic troubleshooting using `curl`, `nslookup`, and `ping`  

---

## 6. Challenges & Solutions

- **Problem:** Domain wasn’t loading despite correct A records  
  **Solution:** Cloudflare proxy was enabled; switching to **DNS Only** allowed direct access  

- **Problem:** Unable to connect using browser-based EC2 Instance Connect  
  **Solution:** Used the key pair to SSH from local terminal  

---

## 7. Summary

Successfully built a small **web server lab environment** for DevOps learning:

- EC2 instance with Ubuntu
- NGINX installed and serving content
- Custom domain pointing correctly to EC2
- Documented process and troubleshooting steps

---
