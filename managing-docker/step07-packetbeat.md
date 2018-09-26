### Packetbeat
By collecting metrics related to network protocols like HTTP you can keep a pulse on application latency and errors, response times, SLA performance, user access patterns and trends, and more.

Packetbeat lets you tap into this data and parse in real time to understand how traffic is flowing through your network. It's totally passive, has zero latency overhead, and it doesn’t interfere with your infrastructure.

### Upload the Packetbeat dashboards into Kibana
`docker run --cap-add=NET_ADMIN \
 --net course_stack \
 docker.elastic.co/beats/packetbeat:6.4.1 \
 setup --dashboards \
 -E setup.kibana.host=kibana`{{execute HOST1}}

### Start Packetbeat
`docker run -d \
 --cap-add=NET_ADMIN \
 --net course_stack \
 docker.elastic.co/beats/packetbeat:6.4.1 -e`{{execute HOST1}}
