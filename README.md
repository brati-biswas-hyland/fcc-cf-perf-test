# fcc-cf-perf-test

A performance testing suite for the FCC Consumer API using Apache JMeter. It includes the test plan (`.jmx`) and test data to simulate load and verify system stability.

---

##  Table of Contents

- [Overview](#overview)  
- [Prerequisites](#prerequisites)  
- [Getting Started](#getting-started)  
- [Running the Tests](#running-the-tests)  
- [Test Configuration](#test-configuration)  
- [Results & Reporting](#results--reporting)  
- [Contributing](#contributing) 


---

## Overview

This project contains a JMeter-based performance test suite designed to evaluate the FCC Consumer API's behavior under load by sending requests with varying user counts and tracking performance metrics.

Included files:
- `cfs_consumerapi_perftestsuite_v2.0.jmx`: JMeter test plan  
- `testdata.csv`: Input file providing test data parameters  
- Optional: `.gitignore` for typical exclusions

---

## Prerequisites

Ensure you have the following installed and available in your system path:

- [Apache JMeter](https://jmeter.apache.org/) (tested on version 5.x)  
- Java Runtime Environment (JRE) compatible with JMeter  
- Your preferred CLI or terminal (Windows CMD, PowerShell, macOS/Linux Bash)

---

## Getting Started

1. **Clone the repository**:
	   git clone https://github.com/brati-biswas-hyland/fcc-cf-perf-test.git
	   cd fcc-cf-perf-test
2. **Review the test data**:
	Open `testdata.csv` to inspect test parameter values. Customize if needed to adapt to your target environment.

## Running the Tests

You can run the JMeter test plan in non-GUI mode to save resources and generate reports automatically. Here's a sample command (modify the paths and parameters as needed):


	  jmeter.bat -n \
	  -t "C:\cfs_consumerapi_perftestsuite_v2.0.jmx" \
	  -JBaseUrl=https://api.cfs.staging.experience.hyland.com \
	  -JUserCount=10 \
	  -JConnectionId=YOUR_CONNECTION_ID_HERE \
	  -l results.jtl \
	  -e \
	  -o "C:\html\reports"


**Parameters Explained**:

-n: Non-GUI (command-line) mode

-t: Path to the JMX test plan

-JBaseUrl: Base API endpoint to test

-JUserCount: Number of concurrent users to simulate

-JConnectionId: Unique connection/session identifier

-l: Output file for results (JMeter .jtl format)

-e: Flag to generate the report dashboard

-o: Directory where the HTML report will be saved


## Test Configuration

**To customize the test:**
1. Open the .jmx file in JMeter GUI to visually inspect or tweak threads, samplers, assertions, listeners, etc.
2. You can also alter command-line parameters (BaseUrl, UserCount, ConnectionId) per run without modifying the .jmx.

## Results & Reporting


After executing the test with `-e -o`, JMeter will generate an HTML dashboard in your reports directory. You can open `index.html` in a browser to explore metrics such as:

Response time distributions
Throughput graphs
Error rates
Summary totals
Use these insights to evaluate performance trends and identify bottlenecks.

## Contributing

Feel free to enhance this repository! You might consider:
Adding README badges (e.g. license, builds, test status)
Parameterizing additional options in the test plan
Incorporating GitHub Actions to automate test execution
Enhancing documentation with results examples or CI/CD integration steps