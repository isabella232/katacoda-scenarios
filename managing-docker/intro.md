### Welcome

To monitor an application running in Docker, you need logs and metrics from the app and the Docker environment it's running in. Using Elasticsearch, Kibana, and Beats allows you to collect, search, analyze and visualize all of this data about the app and the Docker (hosts, containers, etc) in one place. 

### Let's take a look at the goal
This is one of the out of the box dashboards that you will see once you deploy the Elastic Stack and an example application (NGINX) in this Katacoda environment.  This is the Docker metrics dashboard that ships with Metricbeat.  It shows an overview of the CPU and Memory use of every container, allows you to drill in to a specific container, and the containers per node.  Looking at the dashboard is much easier than running the equivalent docker logs, top, inspect, etc. commands.

![Docker Dash](https://raw.githubusercontent.com/elastic/katacoda-scenarios/master/images/docker-dash2.png)

### Beat modules
Above is the Docker metrics dashboard that is part of the Metricbeat Docker module.  Modules provide all  of the configuration needed to acquire,  parse, index, and visualize common log formats. All you have to do is identify which modules to enable and the Elastic Stack does the rest.  In this scenario you will used Docker Labels to tell Filebeat and Metricbeat which modules to use. 

### This is an example of labels to specify what Beat module to use:
![nginx module hint](https://raw.githubusercontent.com/elastic/katacoda-scenarios/master/images/docker-hints-autodiscover.png)

 - Line 3 specifies that the Filebeat nginx module will be used for logs
 - Lines 4 and 5 specify what stream is used for access and error logs
 - Line 6 specifies that the Metricbeat nginx module will be used for metrics
 - Line 7 specifies that Metricbeat should check for metrics on the host and  port assigned to the specific container

### A Quick Katacoda Primer
If this is your first time using Katacoda, let me introduce some of the cool ideas:

* In general, you don't need to type.  Most of the time, you can simply click on a command in the instructions to run it.
* If you need access to a web browser, look for tabs at the top of the terminal window. In this course you will need two pages - one for the Guestbook application, and one for  Kibana. You should see a *Guestbook* tab and a *Kibana* tab in the terminal.  Once you have the Guestbook app running, click on the *Guestbook* tab to open it in a browser window and make some entries. Likewise, once you have Kibana running you should open that tab and look at the data.
* Each time you start or restart a course everything gets reset. If you misconfigure something somehow, simply restart the course.

