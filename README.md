# nginx.conf




#user  nobody;
worker_processes  1;

#error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;

#pid        logs/nginx.pid;


events {
    worker_connections  1024;
}


http {
    include       mime.types;
    default_type  application/octet-stream;

    #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
    #                  '$status $body_bytes_sent "$http_referer" '
    #                  '"$http_user_agent" "$http_x_forwarded_for"';

    #access_log  logs/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    #keepalive_timeout  0;
    keepalive_timeout  65;

    #gzip  on;
	
	
	
	
    server {
      listen      8055;
      server_name localhost;
    
      location  / {
        #root E:/Example/public;  
        root D:/nginx-1.16.1/htmldsjpt/;		
		 try_files $uri $uri/ /index.html;
      }
      
    }
   


    server {
    listen      8073;
    server_name localhost;
    
    location  / { 
        root D:/nginx-1.16.1/htmllcyq/;		
		try_files $uri $uri/ /index.html;
     }
    }
	
	server {
    listen      8066;
    server_name localhost;
    
    location  / {
        #root E:/Example/public;  
        root F:/MyServer/nginx-1.16.1/htmlzhsq/;		
		 try_files $uri $uri/ /index.html;
     }
    }


    	   server {
      listen      8077;
      server_name localhost;
    
      location  / {
        #root E:/Example/public;  
        root D:/nginx-1.16.1/htmld/;		
		 try_files $uri $uri/ /index.html;
      }
      
    }
          server {
      listen      8071;
      server_name localhost;
    
      location  / {
        #root E:/Example/public;  
        root D:/nginx-1.16.1/htmljd/;		
		 try_files $uri $uri/ /index.html;
      }
      
    }

   
     server {
      listen      8079;
      server_name localhost;
    
      location  / {
        #root E:/Example/public;  
        root D:/nginx-1.16.1/htmlbigdata/;		
		 try_files $uri $uri/ /index.html;
        
      }
       
      
    }

    server {
      listen      9529;
      server_name localhost;
    
      location  / {
        #root E:/Example/public;  
        root D:/nginx-1.16.1/htmlai/;		
		 try_files $uri $uri/ /index.html;
        
      }
       
      
    }
    


    upstream my_server {                                                         
       server 192.168.7.235:7200;                                                
       keepalive 2000;
    }
    server {
       listen       9530;                                                         
       server_name  localhost;                                               
       client_max_body_size 1024M;

       location /workLine/ {
           proxy_pass http://my_server;
           proxy_set_header Host $host:$server_port;
       }
       
       location  / {
        #root E:/Example/public;  
        root D:/nginx-1.16.1/htmlai/;		
	try_files $uri $uri/ /index.html;  
                  
      }

   }



     server {
      listen      9528;
      server_name localhost;
      
      
    
      location  / {
        #root E:/Example/public;  
        root D:/nginx-1.16.1/htmlai/;		
	try_files $uri $uri/ /index.html;  
         
         
             
      }
       

       gzip  on;
       gzip_min_length  500k;
       gzip_buffers     4 16k;
        gzip_http_version 1.1;
       gzip_comp_level 6;
       gzip_types       text/plain application/x-javascript text/css application/xml text/javascript application/x-httpd-php application/javascript application/json;
       gzip_disable "MSIE [1-6]\.";
       gzip_vary on;
    }










    server {
      listen      8072;
      server_name localhost;
    
      location  / {
        #root E:/Example/public;  
        root D:/nginx-1.16.1/htmlksh/;		
		 try_files $uri $uri/ /index.html;
      }
    gzip  on;
    gzip_min_length  500k;
    gzip_buffers     4 16k;
    gzip_http_version 1.1;
    gzip_comp_level 6;
    gzip_types       text/plain application/x-javascript text/css application/xml text/javascript application/x-httpd-php application/javascript application/json;
    gzip_disable "MSIE [1-6]\.";
    gzip_vary on;
    }
	
	
	
	
	

    server {
        listen       8022 default_server;
        server_name  localhost;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        location / {
            root   html;
            index  index.html index.htm;
        }

        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
        #
        #location ~ \.php$ {
        #    proxy_pass   http://127.0.0.1;
        #}

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #
        #location ~ \.php$ {
        #    root           html;
        #    fastcgi_pass   127.0.0.1:9000;
        #    fastcgi_index  index.php;
        #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
        #    include        fastcgi_params;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #    deny  all;
        #}
    }


    # another virtual host using mix of IP-, name-, and port-based configuration
    #
    #server {
    #    listen       8000;
    #    listen       somename:8080;
    #    server_name  somename  alias  another.alias;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}


    # HTTPS server
    #
    #server {
    #    listen       443 ssl;
    #    server_name  localhost;

    #    ssl_certificate      cert.pem;
    #    ssl_certificate_key  cert.key;

    #    ssl_session_cache    shared:SSL:1m;
    #    ssl_session_timeout  5m;

    #    ssl_ciphers  HIGH:!aNULL:!MD5;
    #    ssl_prefer_server_ciphers  on;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	

}
