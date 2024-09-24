## For Ubuntu
* `sudo nano /etc/nginx/sites-available/default`
```
server {
    listen 8085;
    server_name localhost;

    location /teamsync/ {
        proxy_pass http://localhost:8084/teamsync/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    location /starship/ {
        proxy_pass http://localhost:8083/starship/;  # Include the /starship pr>
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```
