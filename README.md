
# Cloudfoundry Monitoring Acceptance Tests
A test suite for covering key metric related outcomes for Cloudfoundry

## Design Goals
The CF Monitoring Acceptance test are a test suite designed
to test relevant metric features for Cloudfoundry. It's built on
the following constraints.
   * Bring your own CF - test users will need to provide a valid [meta-data] file for a Cloudfoundry environment. Where needed test users may need to deploy additional ops-files or deploy services. 
   * Tests use relevant CLI plugins to help make tests easy to recreate.
   * Tests are outcome driven and can be used to cover a variety of components.

## Summary of Tests for Developers

### Container Metrics for App Developers
`cf push` 
`cf app`

### Custom App Metrics for App Developers
`cf register-metrics-endpoint`
`cf tail`

### Service Instance Metrics for App Developers
`cf create-service-instance`
`cf tail`

## Metric Coverage Tests for Operators
The test suite should include a markup file specifically for tracking a set of metrics names and tags
to test for each of these metric APIs with an operator scope. This provides coverage for the following.

* Container Metrics 
* Custom App Metrics
* Service Instance Metrics
* Bosh System Metrics
* Statsd Metrics 
* KPI Metrics 


### V1 Firehose Metrics for Operators
`cf nozzle`

### V2 Metrics for Operators
`cf log-stream` 

### Log Cache Metrics for Operators
`cf tail`

### Pull based metrics for Operators

