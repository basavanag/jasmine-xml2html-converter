jasmine-xml2html-converter
=================================

A node module to convert jasmine/junit generated xml reports into formatted html reports

repo : https://github.com/basavanag/jasmine-xml2html-converter

How to use
----------------------------------
* Coverting the xml file to html

  			var HTMLReport = require('jasmine-xml2html-converter');

    		// Call custom report for html output
    		testConfig = {
      			reportTitle: 'Test Execution Report',
      			outputPath: './test_out/e2e/chrome'
    		};
    		new HTMLReport().from(reportPath + '/junitresults.xml', testConfig);

* Using with protractor conf.js file

        // A callback function called once tests are finished.
        onComplete: function() {
          var path = require("path");
          var browserName, browserVersion;
          var reportPath = path.join(__dirname, '..', '/test_out/e2e/');
          var capsPromise = browser.getCapabilities();
          capsPromise.then(function (caps) {
          browserName = caps.caps_.browserName.toLowerCase();
          browserName = browserName.replace(/ /g,"-");
          browserVersion = caps.caps_.version;
          return null;
        });
        
        var HTMLReport = require('jasmine-xml2html-converter');
        reportPath += browserName;

        // Call custom report for html output
        testConfig = {
          reportTitle: 'Test Execution Report',
          outputPath: reportPath,
          seleniumServer: browser.seleniumAddress,
          applicationUrl: browser.baseUrl,
          testBrowser: browserName + ' ' + browserVersion
        };
        new HTMLReport().from(reportPath + '/junitresults.xml', testConfig);
      }

Test config object
----------------------------------
* Defaults : testConfig = {} 
* To override reportTitle & outputPath of the output html file : testConfig = { reportTitle: 'Test Execution Report', outputPath: './test-out' }
* To add data to the report summary of the output html file: testConfig = { Browser: IE }

Sample html report
----------------------------------
![Alt text](https://raw.githubusercontent.com/basavanag/jasmine-xml2html-converter/master/sample_test_report.png?raw=true)

