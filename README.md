# jmeter-request-distributor-class-groovy

A library for use in JMeter test solutions that provides a better random distribution of transactions over time than is possible using JMeter's Throughput Controllers.

### Getting Started with an Example

- Clone the repo
- Build using maven `mvn install`
- Copy the resulting JAR file to JMeter lib directory `cp target/jmeter-distributor-1.0-SNAPSHOT.jar <jmeter_home>/lib/ext/jmeter-distributor-1.0-SNAPSHOT.jar`
- Start JMeter
- Open the [distributor example test plan](https://github.com/crglovejoy/jmeter-request-distributor-class-groovy/blob/main/example/switch_controller_distributor.jmx) in JMeter
- In the JMeter Options tab, enable Log Viewer
- Run the test while observing the logs - NOTE: this test solution DOES NOT send external requests and simply creates JMeter log output
- Observe that on each loop iteration, a single Switch Controller (0, 1, 2, or 3) is chosen to execute with each Switch Controller being picked ~25% of the time as configured in the User Defined Variables
- NOTE: The User Defined Variables value string of "0:25,1:25,2:25,3:25" will result in an array containing 25-0 entries, 25-1 entries, 25-2 entries, 25-3 entries and the array is then shuffled.  An array index is chosen at random on each test iteration to determine which value to use with the Switch Controller.  25 represents number of entries, not a %.



### Why it is Better than JMeter's Throughput Controller

- Start JMeter
- Open the [throughput controller example testplan](https://github.com/crglovejoy/jmeter-request-distributor-class-groovy/blob/main/example/throughput_controller_distributor.jmx)
- In the JMeter Options tab, enabled Log Viewer
- Run the test while observing the logs - NOTE: this test solution DOES NOT send external requests and simply creates JMeter log output
- Observe that ~25% of the time, ALL of the Throughput Controllers are executed inside a single iteration of the test rather than each iteration running only one of the actions.  ~75% of the iterations result in NO Throughput Controllers executing.

  

