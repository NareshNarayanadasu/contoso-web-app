"# nginx-deploy-app-contoso" 
1. **User and Worker Processes**:
   - Default:
     ```nginx
     user       nobody;  ## Default: nobody
     worker_processes  1;  ## Default: 1
     ```
   - Custom: No changes made. Both configurations retain the default settings.

2. **Error Log and PID File**:
   - Default:
     ```nginx
     error_log  /var/log/error.log  notice;
     pid        /var/run/nginx.pid;
     ```
   - Custom:
     ```nginx
     error_log  /var/log/nginx/error.log;  # Changed the log file path
     pid        /var/run/nginx.pid;  # Retains the default PID file path
     ```

3. **HTTP Block**:
   - Default: The default configuration might not have specific MIME type configurations or custom `types` blocks.
   - Custom:
     ```nginx
     include  mime.types;  # Includes MIME types definitions
     types{
         application/html cshtml;  # Adds a custom MIME type for cshtml files
     }
     ```

4. **Server Block**:
   - Default: The default configuration likely does not have a specific server block defined for serving cshtml files.
   - Custom:
     ```nginx
     server {
         listen 80;  # Listens on port 80
         index index.cshtml;  # Sets the default file to index.cshtml
         location / {
             root /usr/share/nginx/html;  # Specifies the root directory
             try_files $uri $uri/ /index.cshtml =404;  # Tries to serve cshtml files
         }
     }
     ```

5. **Include Additional Configuration**:
   - Default: The default configuration might not include additional configuration files from `/etc/nginx/conf.d/*.conf`.
   - Custom: Retains the inclusion of additional configuration files.
