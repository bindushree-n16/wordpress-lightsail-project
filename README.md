# WordPress Blog Deployment on AWS Lightsail



## Project Overview

Deployed a WordPress blog on Amazon Web Services (AWS) Lightsail and accessed it through the instance's public IP address. Configured and troubleshot the web server to make the website accessible, logged in to the WordPress administration dashboard, and published a blog post.



## Technologies Used

- AWS Lightsail

- WordPress

- Linux

- Apache HTTP Server

- SSH

- HTTP and HTTPS

- Basic server troubleshooting



## Key Learnings

- Creating and accessing a cloud server using AWS Lightsail.

- Connecting to a Linux server through browser-based SSH.

- Understanding public IP addresses and website access.

- Checking Apache web server status and configuration.

- Troubleshooting HTTP-to-HTTPS redirects.

- Accessing WordPress administration and managing blog posts.

- Using Linux commands to inspect files and troubleshoot server issues.



## Outcome

Successfully deployed a working WordPress blog on AWS Lightsail, accessed the WordPress dashboard, and published a blog post visible on the public website.
**HOW I SOLVED THE AUTOMATIC HTTPS REDIRECT ERROR ?****
## Troubleshooting: Automatic HTTP-to-HTTPS Redirect

### Problem
When I opened my WordPress website using the public IP address over HTTP, it automatically redirected to HTTPS. The browser displayed `NET::ERR_CERT_AUTHORITY_INVALID` because the HTTPS certificate was not trusted for the IP address.

### Investigation
1. Checked the HTTP response using `curl -I http://localhost`.
2. Found that the server returned `301 Moved Permanently` with a redirect to HTTPS.
3. Inspected the Apache virtual host configuration at `/etc/apache2/sites-enabled/000-default.conf`.
4. Identified the rewrite rules responsible for redirecting HTTP requests to HTTPS.

### Solution
Commented out the HTTP-to-HTTPS rewrite conditions and redirect rule in the enabled Apache configuration, then reloaded Apache.

### Verification
Ran `curl -I http://localhost` again and received `200 OK`. After that, I opened the public IP over HTTP and confirmed that the WordPress website loaded.

### Learning
Learned how to inspect Apache configuration, identify HTTP redirects, reload a web server, and verify HTTP responses using curl.

**Note:** This troubleshooting restored HTTP access. It did not configure a trusted HTTPS certificate.
