# docker-k6-grafana-influxdb
Demonstrates how to run load tests with containerised instances of K6, Grafana and InfluxDB.

## Setting up K6, Grafana and InfluxDB

Prerequsites
* [Docker](https://docs.docker.com/get-started/)
* [Docker compose](https://docs.docker.com/compose/gettingstarted/)
* [Git](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

Step 1. Clone the repository
```
git clone https://github.com/Simranstha045/k6-grafana-starter-kit.git
```
Step 2.Navigate to the repository directory
```
cd k6-grafana-starter-kit/
```

Step 3. Start Grafana and InfluxDB
```
docker-compose up influxdb grafana
```
Setp 4. Use Grafana web application locally.
http://localhost:3000/

Step 5. Log in using following credentials if required.
```
Username: admin
Password: admin
```
Step 6. View the dashboard
http://localhost:3000/d/k6/k6-load-testing-results 


## Running K6 scripts
Step 1. Make sure Gafana and Influxdb is up.
```
docker ps
```
Step 2. Run the K6 test scripts.
```
docker-compose run k6 run /scripts/ewoks.js
```
Step 3. View the real time results in the dashboard.
http://localhost:3000/d/k6/k6-load-testing-results 

## Running your own K6 scripts
Step 1. Make sure Gafana and Influxdb is up.
```
docker ps
```
Step 2. Add your script in the /scripts folder 
```
/scripts/YourK6Script.js
```
Step 3. Run the K6 test scripts.
```
docker-compose run k6 run /scripts/YourK6Script.js
```
Step 4. View the real time results in the dashboard.
http://localhost:3000/d/k6/k6-load-testing-results 

#### References
* https://k6.io/docs/
* https://k6.io/docs/results-visualization/influxdb-+-grafana/
* https://medium.com/swlh/beautiful-load-testing-with-k6-and-docker-compose-4454edb3a2e3
* https://community.k6.io/t/grafana-how-to-display-error-per-second-data-on-grafana-with-k6/236/3

#### Article
This is the accompanying source code for the following article. Please read for a detailed breakdown of the code and how K6, Grafana and InfluxDB work together using Docker Compose:

https://medium.com/swlh/beautiful-load-testing-with-k6-and-docker-compose-4454edb3a2e3

#### Dashboards
The dashboard in /dashboards is adapted from the excellent K6 / Grafana dashboard here:
https://grafana.com/grafana/dashboards/2587

There are only two small modifications:
* the data source is configured to use the docker created InfluxDB data source
* the time period is set to now-15m, which I feel is a better view for most tests

#### Scripts
The script here is an example of a low Virtual User (VU) load test of the excellent Star Wars API:
https://swapi.dev/

If you're tinkering with the script, it is just a friendly open source API, be gentle!
