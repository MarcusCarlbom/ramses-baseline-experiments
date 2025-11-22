# RAMSES Baseline Experiments

## Setup

1. Download the RAMSES artifact from https://doi.org/10.5281/zenodo.10400820
2. Extract the artifact and navigate to the root directory
3. Replace `managed-system/rest-client/src/main/resources/application.properties` with the version from `custom-scenario/`
4. Start RAMSES following the instructions in the RAMSES artifact README
5. Identify the API Gateway port with `docker ps | grep api-gateway`
6. Update the `API_GATEWAY_IP_PORT` value in `application.properties` with the discovered port
7. Run `scripts/rebuild_scenario.sh` from the artifact root directory

## Experiment Configuration

- **Duration:** 15 minutes total 
- **QoS Threshold:** 1000ms average response time for ordering-service
- **Expected Behavior:** System scales from 1 to 2+ instances, retains excess capacity after degradation ends

## Results

See `results/customscenario1.jpeg` for dashboard visualization showing response times, instance scaling, and load balancing adaptations.

## Reproduction Notes

- Ensure all RAMSES services are fully started (~60 seconds) before running the custom scenario
- The scenario auto-restarts the monitoring routine and enables adaptations
- Dashboard updates are visible at the port shown in `docker ps | grep ramses-dashboard`