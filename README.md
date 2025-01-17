# Galen
Galen is a framework that has been developed for automation testing of responsive design for web applications. Now a days it has become a fully functional testing framework with rich reporting and test management system. It supports both Javascript and Java.

# Mode of operation
Galen operates in the following manner.<br>
1. Galen opens a page in a browser.<br>
2. Resizes the browser to a specific size.<br>
3. Tests the layout with Galen specs.<br>

In case the page is not directly accessible, Galen allows you to perform some operations on the website first. As it is based on Selenium all operations related to clicking, typing, injecting client-side javascript can be done very easily.

Galen specs is the language with which the specifications of responsiveness can be defined as per different devices. The following code snippet will give an idea about how easy it is to implement the page specifications using Galen.

```
= Main section =
    @on *
        header:
            height 100px 
            inside screen 0px top 
            width 100% of screen/width 

        menu:
            height 50 to 60px 
            width 100% of screen/width 
            below header ~ 0px 

        search-button:
            inside menu 20 to 50px left, 0 to 10px top 

    @on mobile
        search-button:
            width 100px 
         
    @on desktop 
        search-button:
            width 150px 
```

# Installing Galen
<h2>Requirements</h2>
For Galen a Java version greater then 1.8 is required
<br>
<h3>NPM-based Installation</h3>
For npm based installtion just type in the command<br>
`sudo npm install -g galenframework-cli`
<br>
<h2>Manual Installation</h2>
<h3>Install on OS X and Linux</h3>
Download the archive from [Download Page](http://galenframework.com/download/) and extract it in any directory. Go to the extracted directory of the galen and execute the following command.<br>
`sudo ./install.sh`

To check whether Galen is sucessfully installed execute the following command.<br>
`galen -v`
The above command should print the installed version of `Galen` within your system.

# Configuring Galen
To configure galen create a project directory and inside that project directory execute the following command.<br>
`galen config`<br>

This would basically create a galen.config file in your project directory which would basically contain the configurational parameters for `Galen`. You need to configure the `ChromeDriver` for `Chrome` and the `GeckoDriver` for `Firefox`. To execute your tests in `headless` mode you can also execute it using `PhantomJs`.<br>
To configure the drivers use the following syntax.
```
$.webdriver.gecko.driver=Drivers/geckodriver
$.webdriver.chrome.driver=Drivers/chromedriver
$.phantomjs.binary.path=Drivers/phantomjs/bin/phantomjs
```

# Executing Tests in Galen
To execute a test suite in galen execute the following command.<br>
`galen test <TestSuite_name> --htmlreport <ReportDirectory_name>`<br>
To execute anf check a spec file use the following command.<br>
`galen check <File_name> --url <url> --size <dimension> --htmlreport <ReportDirectory_name>`

# Project Structure
This would be the possible project direcotry structure.<br>
1. `Drivers` directory consists of the browser kits required to execute a browser. This directory includes `GeckoDriver`, `ChromeDriver` and `PhantomjsDriver`.<br>
2. `PageInteractions` directory contains all the javascript related logic related to page interactions.<br>
3. `Reports` directory consists of all the reports executed on Cross Devices, Cross Browsers and specific to only a single device<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.1. `Cross_Browser_Specs_reports` which has the reports for Cross Browsing based test executions.<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.2. `Cross_Device_Specs_Reports` which has the reports for Cross Browsing and Cross Device based test &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;execution.<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3.3. `Uni_Specs_Reports` which has the reports for tests executed specific to a single device.<br>
4. `Specs` directory consists of the Galen specifications and has two classifications.<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.1. `Cross_Specs` which essentially focuses on the characteristics on multiple devices and<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.2. `Uni_Specs` focuses on the characteristics of a single device.<br>
5. `Test_Suites` directory consists of the test suites required to execute all the tests and has two classifications.<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5.1. `Cross_Browser` which focuses on tests written for multiple browser and multiple devices.<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5.2. `Cross_Devices` which focuses on tests written for multiple devices only specific to the default browser &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;mentioned in the galen configuration.<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5.3. `Uni_Devices` which focuses on tests written specific to device specific to the default browser mentioned in the &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;galen configuration only.<br>
6. `galen.config` consists of all the configuration related parameters required to execute Galen.<br>

# Note
In case of Drivers instead of using the `driver` executables for chrome, phantomjs and firefox you can also install them in your local machine as well.<br>
Since I am using a mac I will be using the `Homebrew` to install the drivers.<br>
1. To execute your tests on firefox you will be needing the geckodriver. `Gecko driver` can be installed by using `brew install geckdriver`. This will install the latest stable version of gecko driver in your system.<br>
2. To execute your tests on chrome you will be needing the chromedriver. `Chrome driver` can be installed by using `brew install chromedriver`. This will install the latest stable version of chrome driver in your system.<br>
3. To execute your tests headlessly you will be needing the `phantomjs driver` which can be installed in your system using `brew install phantomjs`.<br><br>
Once this is done you just need to give the path of the driver in your galen.config file. This will look something like this.<br>
```
    $.webdriver.gecko.driver=/usr/local/bin/geckodriver
    $.webdriver.chrome.driver=/usr/local/bin/chromedriver
    $.phantomjs.binary.path=/usr/local/bin/phantomjs
```  
