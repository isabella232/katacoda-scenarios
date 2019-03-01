#### Make sure your Guestbook has some traffic
If you have not yet connected to the Guestbook instance, go ahead and do so now. 
Open the [Guestbook](https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/)

Now that you have generated some traffic in the Guestbook continue:

#### Launch Kibana
[Kibana](https://[[HOST_SUBDOMAIN]]-5601-[[KATACODA_HOST]].environments.katacoda.com/)

#### Configure Defaults
You should now have indices for the Beats in Elasticsearch.   In order to use Kibana to search and visualize the information in those indices you have to set one of the patterns **filebeat-\*** or  **metricbeat-\*** as the default.  Click on **Management** and then **Index Patterns**.

![abc](https://user-images.githubusercontent.com/25182304/43741865-d552ac5a-999d-11e8-9c27-3ce5ef38ecc8.png)

Choose one of the patterns by clicking on it.  I generally set **metricbeat-\*** as the default, so that is what the screenshots will show.

![ghi](https://user-images.githubusercontent.com/25182304/43741879-de52cb28-999d-11e8-9d2d-02f8cb965e38.png)

Click the star on the far right of the page to make your index pattern the default

![mno](https://user-images.githubusercontent.com/25182304/43741884-e1462d84-999d-11e8-9977-45ae5a2975da.png)

Select yes or no to share basic usage information with Elastic

![stu](https://user-images.githubusercontent.com/25182304/43741889-e78c71e4-999d-11e8-8d4a-830c752cf136.png)

### Come back here after you configure the defaults
The next step has URLs to some of the out-of-the-box dashboards, saved searches, and visualizations related to Docker and the components of  the sample application (Apache httpd, Redis, NGINX).  **Click Continue**
