# Manual

## Operation

To run rest_variantValidator

### In dev mode upsing Python

```bash
$ python wsgi.py
```

You will be provided with a link which will open rest_variantValidator in your web browser. [http://127.0.0.1:5000/](http://127.0.0.1:5000/)


## Swagger documented functions
The rest_variantValidator functions have swagger documentation to help you generate URLs to make direct API calls utilising human readable text-input boxes. 

Once the documented page opens in your web-browser, click the variantvalidator link and the documented functions will appear. 

A web-hosted version of this rest API can be found at [https://rest.variantvalidator.org](https://rest.variantvalidator.org)  

## Direct request
Direct URL calls can be made to the rest-API. The easiest way to create these URLs is to use the swagger documented functions

## In a Docker container

## Apache web-server and mod_wsgi
Mounting rest_variantValidator to an Apache web server requires [mod_wsgi](https://pypi.org/project/mod-wsgi/)

Example [Apache configuration](https://modwsgi.readthedocs.io/en/develop/user-guides/quick-configuration-guide.html)

***Note: you will need to configure the file paths in the example below***

```apacheconf
<IfModule wsgi_module>

	WSGIPythonPath /local/miniconda3/envs/vvenv/lib:/local/miniconda3/envs/vvenv/lib/python3.6/site-packages
	WSGIDaemonProcess rest_variantValidator user=wwwrun group=www threads=5
	WSGIScriptAlias / /local/py3Repos/rest_variantValidator/wsgi.py
	WSGIPythonHome /local/miniconda3/envs/vvenv
    	    	
    	<Directory /local/py3Repos/rest_variantValidator/>
        	WSGIProcessGroup rest_variantValidator
         	WSGIApplicationGroup %{GLOBAL}
            Order allow,deny
            Allow from all
            Header set Access-Control-Allow-Origin "*"
            Header set Access-Control-Allow-Methods "GET"
     	</Directory>

</IfModule>
LogLevel crit
CustomLog /local/apache2/log/access_log for_pound


```

## Additional resources
We are compiling a number of jupyter notebook user guides for rest_variantValidator in [rest_variantValidator_manuals](https://github.com/openvar/rest_variantValidator_manuals)