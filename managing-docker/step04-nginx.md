### Start NGINX
`docker run -d \
--net course_stack \
--label co.elastic.logs/module=nginx \
--label co.elastic.logs/fileset.stdout=access \
--label co.elastic.logs/fileset.stderr=error \
--label co.elastic.metrics/module=nginx \
--label co.elastic.metrics/hosts='${data.host}:${data.port}' \
-v /root/course/nginx.conf:/etc/nginx/nginx.conf:ro \
-v /root/course/nginx-default.conf:/etc/nginx/conf.d/default.conf:ro \
--name nginx \
-p 80:80 nginx`{{execute HOST1}}

Note in the NGINX run command there are three labels, these labels are available in the Docker environment, and Filebeat detects them and configures itself.  The three labels tell Filebeat that the module name **nginx** should be used to collect, parse, and visualize the logs from this container, and that the access logs are at STDOUT, while the error logs are at STDERR.
You can see these labels with the command:

`docker inspect nginx | grep -A4 Labels`{{execute HOST1}}

### Generate some traffic through NGINX
At the top of the terminal you will see an NGINX tab.  Click on that and you will see the default NGINX page.  Add a page name to the URL, for example /foo, and this will generate a 404 error.  Now return to the Katacoda tab and click on the Kibana tab above the terminal.  Open the Dashboards and search for nginx, click on the Filebeat NGINX overview.

