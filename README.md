
# Cloudfoundry Monitoring Acceptance Tests
A test suite for covering key metric related outcomes for Cloudfoundry

## Design Goals
The CF Monitoring Acceptance test are a test suite designed
to test relevant metric features for Cloudfoundry. It's built on
the following constraints.
   * Bring your own CF - test users will need to provide a valid [meta-data] file for a Cloudfoundry environment. 
   Where needed test users may need to deploy additional ops-files or deploy services. 
   * Tests use relevant CLI plugins to help make tests easy to recreate.
   * Tests are outcome driven and can be used to cover a variety of components.

## Summary of Tests for Developers
App developers have only a few key metric features included in Cloudfoundry, all of which 
are easily testible using the CLI.

### Container Metrics for App Developers
The main use case for metrics on the platform is display of container metrics for the following command. 

`cf push` - when pushng the command should exit succesfully, it may display 0 for metric values. 
`cf app`- displays container metrics for each instance of the app. 

### Custom App Metrics for App Developers
With a plugin app developer can instrument custom metrics using the metric registrar. 

`cf push && cf register-metrics-endpoint` - Push and bind a simple app for metric creation using the metric-registar cli plugin.
`cf tail` - App developers can view metrics using the log-cache cli plugin. 

### Service Instance Metrics for App Developers
App developers have access to view metrics for service instances they setup. 

`cf create-service-instance` - create a sample service instance for creating metrics
`cf tail` - confirm app developers can view metrics for thier service instance. 

Note: This test requires additional cf configuration.

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
Verifes list of metrics using `cf nozzle` 

### V2 Metrics for Operators
Verifes list of metrics using `cf log-stream` 

### Log Cache Metrics for Operators
Verifes list of metrics using `cf tail`

### Pull based metrics for Operators
Verifes list of metrics using [cf-telegraf-operator](https://github.com/cloudfoundry-incubator/cf-telegraf-operator) to subscribe and output them. 
