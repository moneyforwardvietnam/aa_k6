## Create new repo:

- npm init -y

## Technologies and tools used:

- [JS](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
- [npm](https://www.npmjs.com/)
- [k6](https://k6.io/)
- [docker](https://www.docker.com/get-started)
- [Grafana](https://grafana.com/)
- [Influxdb](https://github.com/influxdata/influxdb)

## Execution Examples

### Requirements:

- Installation [**k6**](https://k6.io/docs/getting-started/installation/)
- Installation [**docker/docker-compose**](https://www.docker.com/get-started)

### Without docker, influxdb and grafana:

- With npm:
  - `npm run FullFlowLoadTest`
- Without npm:

  - `k6 run src/simulations/FullFlowLoad.test.js`

- Run with docker
  docker run -it --rm \
   -v ${PWD}:/scripts \
   -v ${PWD}:/jsonoutput \
   grafana/k6 run --out json=/jsonoutput/my_test_result.json /scripts/src/simulations/FullFlowLoad.test.js

Or:
docker-compose up -d \
 influxdb \
 grafana

docker compose run --rm k6 run /scripts/src/simulations/FullFlowLoad.test.js

k6 run --out influxdb=http://127.0.0.1:8086 src/simulations/FullFlowLoad.test.js
