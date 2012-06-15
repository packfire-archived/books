    server {
		...
		
		if (!-e $request_filename) {
            rewrite ^/(.+)$ /index.php?_urlroute_=$1 last;
        }

        location ~ \.php$
        {
            fastcgi_pass unix://var/run/php-fpm.sock;
            fastcgi_index index.php;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            include fastcgi_params;
        }
		
		location ~ \.htaccess {
		    deny  all;
		}
		
		...
	}
