### How to Use This Playbook

1. **Prepare your environment**:
   - Ensure you have Ansible installed on your control machine
   - Make sure the domain name you want to use points to your server's IP address
   - Verify SSH access to your target server

2. **Customize the variables**:
   - Edit `vars.yml` to set your domain name, email address, and target port
   - Update `inventory.ini` with your server details

3. **Run the playbook**:
   ```bash
   ansible-playbook -i inventory.ini nginx-certbot-playbook.yml
   ```

### Customization Options

To use this playbook on a different server, just modify these key variables:

- `domain_name`: Your domain name that points to the server
- `certbot_email`: Your email address for Let's Encrypt notifications
- `app_port`: The port your application is running on (default: 5678)
- Update the inventory file with the new server details

### What This Playbook Does

1. Installs Nginx and Certbot with the Nginx plugin
2. Creates an Nginx configuration that proxies requests to your application on port 5678
3. Obtains SSL certificates from Let's Encrypt using Certbot
4. Configures automatic HTTP to HTTPS redirection
5. Sets up a cron job for automatic certificate renewal
6. Optionally configures firewall rules for HTTP/HTTPS traffic
7. Works across different Linux distributions (Debian/Ubuntu and RHEL/CentOS)

### Troubleshooting

- If certificate acquisition fails, ensure your domain correctly resolves to your server
- For testing, set `use_staging_certbot: true` to avoid Let's Encrypt rate limits
- Check Nginx logs at `/var/log/nginx/error.log` if problems occur

This playbook should be completely reusable across different environments by just changing the variables to match your specific needs.
