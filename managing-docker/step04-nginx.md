### NGINX
We will deploy the standard NGINX Docker image with a few configuration changes:
1. set the Docker network
1. add some labels to the container to specify how the logs and metrics should be collected
1. add the x-forwarded-for IP addresses passed in by the Katacoda proxy to the access log
1. allow the local 172 network to access the server status metrics

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
-p 80:80 nginx:1.15.4`{{execute HOST1}}

Note in the NGINX run command there are labels, these labels are available in the Docker environment, and the Beats detect them and configure log and metric collection.  The labels tell Filebeat that the module name **nginx** should be used to collect, parse, and visualize the logs from this container, and that the access logs are at STDOUT, while the error logs are at STDERR.  Similarly, the labels tell Metricbeat to collect metrics from the container name and port.

You can see these labels with the command:

`docker inspect nginx | grep -A7 Labels`{{execute HOST1}}

### Generate some traffic through NGINX
At the top of the terminal you will see an NGINX tab.  Click on that and you will see the default NGINX page.  Add a page name to the URL, for example /foo, and this will generate a 404 error.  Now return to the Katacoda tab and click on the Kibana tab above the terminal.  Open the Dashboards and search for nginx, click on the Filebeat NGINX overview.

