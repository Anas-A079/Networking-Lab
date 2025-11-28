<pre>
# Networking Lab

This lab documents setting up an EC2 instance with NGINX and connecting it to a custom domain via Cloudflare.

---

## 1. What I Built

- AWS EC2 instance (Ubuntu 24.04 LTS, t3.micro)
- Security group allowing SSH (22) and HTTP (80)
- Installed NGINX
- Connected **networking-lab.uk** via Cloudflare DNS
- Verified website loads NGINX Welcome Page

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

To connect your domain:

1. Go to your domain in **Cloudflare**.
2. Add **A records** for `@` and `www` pointing to your EC2 public IP (e.g., 18.169.184.240).
3. Set proxy status to **DNS Only** to bypass Cloudflare temporarily.
4. Wait a few minutes for DNS propagation.
5. Verify with `nslookup your-domain` or `ping your-domain`.

---

## 4. Website Screenshot

3. **Website in Browser**  
   ![Website Screenshot](https://github.com/Anas-A079/Networking-Lab/blob/main/Screenshot%20from%202025-11-28%2000-57-23.png?raw=true)

---

## 5. Lessons Learned

- Launching an EC2 instance and configuring security groups
- Installing and managing NGINX
- Connecting a custom domain via Cloudflare DNS
- Troubleshooting with `nslookup`, `ping`, and `curl`

---

## 6. Challenges & Solutions

- **Domain not loading:** Cloudflare proxy was enabled → switched to DNS Only  
- **SSH connection issue:** Used key pair from local terminal instead of browser-based connect

---

## 7. Summary

Built a simple web server lab for DevOps learning:

- EC2 instance running Ubuntu
- NGINX serving content
- Custom domain pointing to EC2
- Documented setup and troubleshooting
</pre>
