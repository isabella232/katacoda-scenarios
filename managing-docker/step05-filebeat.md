### Start Filebeat

Before you start Filebeat, have a look at the configuration.  The hints based autodiscover feature is enabled by uncommenting a few lines of the filebeat.yml, so we will bind mount it in the Docker run command.  Use grep to see the lines that enable hints based autodiscover:

`grep -A4 filebeat.autodiscover course/filebeat.yml`{{execute HOST1}}

And now start Filebeat:

`docker run -d \
--net course_stack \
--name=filebeat \
--user=root \
--volume="/var/lib/docker/containers:/var/lib/docker/containers:ro" \
--volume="/root/course/filebeat.yml:/usr/share/filebeat/filebeat.yml:ro" \
--volume="/var/run/docker.sock:/var/run/docker.sock:ro" \
docker.elastic.co/beats/filebeat:6.3.2 filebeat -e -strict.perms=false`{{execute HOST1}}

