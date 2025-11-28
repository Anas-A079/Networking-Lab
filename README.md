# Networking Lab

This lab documents setting up an EC2 instance with NGINX and connecting it to a custom domain using Cloudflare.

---

## 1. What I Built

- EC2 instance (Ubuntu 24.04 LTS)
- Security group allowing SSH and HTTP
- Installed NGINX
- Connected domain **networking-lab.uk** using Cloudflare DNS
- Verified NGINX welcome page is live

---

## 2. Usage

- Update package index:
\`\`\`bash
sudo apt update -y
\`\`\`

- Install NGINX:
\`\`\`bash
sudo apt install nginx -y
\`\`\`

- Enable NGINX to start on boot:
\`\`\`bash
sudo systemctl enable nginx
\`\`\`

- Start NGINX:
\`\`\`bash
sudo systemctl start nginx
\`\`\`

- Check NGINX status:
\`\`\`bash
sudo systemctl status nginx
\`\`\`

---

## 3. DNS Configuration

Steps to configure Cloudflare:

1. Add A record for `@` → EC2 public IP  
2. Add A record for `www` → EC2 public IP  
3. Set both records to **DNS Only**  
4. Wait a few minutes for DNS propagation

Verification commands:

- Check DNS resolution:
\`\`\`bash
nslookup networking-lab.uk
\`\`\`

- Ping domain:
\`\`\`bash
ping networking-lab.uk
\`\`\`

---

## 4. Website Screenshot

3. **Website in Browser**  
![Website Screenshot](https://github.com/Anas-A079/Networking-Lab/blob/main/Screenshot%20from%202025-11-28%2000-57-23.png?raw=true)

---

## 5. Lessons Learned

- Launching and configuring EC2
- Installing NGINX
- Cloudflare DNS setup
- Troubleshooting DNS and connectivity issues

---

## 6. Challenges & Solutions

- Domain failed to load → Switched Cloudflare proxy to DNS Only  
- EC2 Connect failed → Used SSH key from local terminal  

---

## 7. Summary

This lab demonstrates:

- EC2 server deployment
- NGINX setup
- Domain connected through Cloudflare
- Verification and troubleshooting steps


