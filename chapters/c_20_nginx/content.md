# Nginx Web server on EC2

1. Purchase a domain in Route 53
2. Rent a Elastic IP (EIP)
3. Issue a certificate with Amazon Certificate M (ACM)
4. Install the software
5. Configure the EC2 instance
6. Configure nginx

## basic script user data

```bash
sudo yum install nginx
sudo systemctl start nginx
```
