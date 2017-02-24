# ServiceRepoRunner
Use this repo to create your automation faster using Servicerepo framework

Welcome to the ServiceAutomation wiki!

Use this repo to create your automation project using Testrepo solution http://intuit.artitelly.com/testrepo/service

You can login to this application using guest user account and can create an account for you.

To login as guest user use

User Name : guest@intuit.com password: guest

##  How you can setup your Service Automation Project?

To setup your First Service automation project follow these steps

### Step 1: 

1) Login to http://intuit.artitelly.com/testrepo/service using guest user account

2) Create your own user account using Company --> Add User menu item

3) Click Setup tab 

4) Click Search ( You will find some Service Automation Scenarios)

5) Create your own Scenario using the name of the use case of API

6) Enter all necessary data for your service repo object. Your URL should be the Base URL. In the API screen you will provide relative URI which will be added to the base to get complete URL in the API call

7) Provide a package name like com.api.test etc using this you will generate your code

8) You can use text area for Global Input and Global Output 

Global Input / Output are the common input and output for all APIs call. The output parameters you can define as

output parameter name = output response JSON Xpath

in any API call when we find a matching of the xpath we extract the output and store it to be reused in the next call or to be asserted after all APIs are called. So you can use these global output parameters very wisely such that either you want to use these in the next call or need to be asserted after the test with certain expected values.

Global inputs are common input which can be used as common parameters in the JSON input replacing values in the runtime

We also take input from the XLs which is test case specific. You can create XL sheet with column name as parameter name and column row value is the actual value to be replaced in your test at runtime. XL sheet column also can be used for assertion.

you can also define API specific input parameter in the next step for each API call

### Step 2 :  in Service Repo screen for initial setup actions

1) In the Service Repo screen you should add all global auth parameters by clicking add (+) symbol --> Add Auth

2) Also add global parameters like cookie , header etc you need add (+)  --> Add Global Parameters

3) You can also attach any document like test plan etc. as a reference to you as well other using (+) --> Add API Template

### Step 3 : Click down arrow button in the Service Repo screen

1) In the API setup screen enter all data and use the short name = Java Class Name you want to see

2) Provide URI which will be added to the base URL you provided in the Service Repo screen.

3) Provide a post body like below with curl. 


curl --insecure -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Basic UUFfQVVUT01BVElPTjphdXQwbWF0MTAj' --cookie 'qbn.ptc.agentid=123146281273304;qbn.ptc.authid=123146281273304;qbn.ptc.gauthid=123146281273304;qbn.ptc.tkt=V1-229-b3j0cn1zigpw8m3v0z9pkd;qbn.ptc.ticket=V1-229-b3j0cn1zigpw8m3v0z9pkd' 

**-d '{"updateCompanyModel":{"companyModel":{"id": 3143172,**
**"partnerName": "PAYCYCLE",**
**"serviceNameAsSubject": "Intuit Online Payroll",**
**"serviceNameAsObject": "Intuit Online Payroll",**
**"serviceNameAsAdjective": "Intuit Online Payroll",**
**"serviceNameAsPossessive": "Intuit Online Payroll's",**
**"businessAddress":{"id":0,"address1":"149 Main Street","city":"Mountain View",**
**"taxAddress":{"id":0,"address1":"2751 Main Street","city":"Mountain View","zip":"94035"},**
**"zip": "94035"},**
**"principalOfficer": "Autotask Desk",**
**"signupDate": "2016-11-30",**
**"phone": "149-111-2751",**
**"homePhone": "408-396-4567",**
**"mobilePhone": "408-900-9878",**
**"fax": "408-678-9903",**
**"havePaidEmployeesThisYear": false,**
**"startPayrollThisQtr": true,**
**"havePaidTimeOff": true,**
**"companyTaxSetup": {**
**"filingName": "Autotask Company 1480545033",**
**"filingType": "soleProprietor",**
**"isFilingAddressSameAsBusinessAddress": true,**
**"federalEIN": "64-1492751"**
**}},"persist":true}}' **

'https://trunk-ws.dev.paycycle.com/test/webservices/json/MobileManager'

You have to provide header, cookie and -d < YOUR JSON INPUT> remember there is beginning and ending single quote in the JSON and then the URL within single quote.

Below is another sample :

curl --insecure -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Basic UUFfQVVUT01BVElPTjphdXQwbWF0MTAj' --cookie 'qbn.ptc.agentid=123146281273304;qbn.ptc.authid=123146281273304;qbn.ptc.gauthid=123146281273304;qbn.ptc.tkt=V1-229-b3j0cn1zigpw8m3v0z9pkd;qbn.ptc.ticket=V1-229-b3j0cn1zigpw8m3v0z9pkd' -d '{"loginMobileMulti":{"userName":"AutoTask9BFXtP+iamtestpass@gmail.com","password":"passw0rd"}}' 'https://trunk-ws.dev.paycycle.com/test/webservices/json/MobileManager'

4) After you entered all data click save button. To run your sample you can click the run button.  The response text box will be filled up if that runs successfully. 

 **( Currently because of the security reason the URL endpoints are not Public. Once they allow the call to go in to your test env from the hosted server  then you could get response perfectly)**

But your case you can copy this curl command and run from your own Desktop to see that your command returns output.  **Don't worry if you don't get proper response output here!** We are going to generate Restassured Java code and run your test using your local env.

5) Once you hit the run button then scroll to the bottom section of the Service API screen and click Rest Assured Button

6) Click Copy to copy the code to your key board.

7) Now You might have already created a cloned of this project and ready to test this code within your own IDE

8) Create a package name which you had provided in the Service Repo screen using package input box

9) Create a Java class with the API shortName or generated Java class name in the Rest Assured Text area and paste your code after deleting the content of the newly created Java Class.

Now you are ready with your code! Enjoy!

### Step 4:  After generating multiple APIs Rest Assured script follow these steps

1) Create your own Orchestration how you like to make call from one API to another.  Look at the 1st API you want to call from your test and find out the class you generated

2) Write a TestNg class  and create a object of the initiating class. For example if your api name = loginApi and you have a generated Rest Assured class loginApi

in the test suite TestNg Test method or any java class with main ()

main(String [] args){

    loginApi test = new loginApi();
    
    test.loginApi().then().anotherMethodOfOtherClass().then()...
}


### Step 5 :How to create Test suite?

To create a Test suite 

1) Go to the Data --> module folder -- Create your own project folder

2)  Create a Page Object similar to the TestAssuredSample.xml located under sample folder

3)  configure package , class and method to call. 

Ex:

<page name="248EC73C2C4001B5E0505DHA1FAB5F8E" description="LoginAPITest">


    <action name="248EC73C2C4101B2E0505D9A1FAB5F8E"
            dataset="global:xls.achPreProcessorTask" startrow="1" endrow="2"
            description="IOP mobile Login">

        <validator name="Step-1: Create IAM User" description="">

            <testng name="Test loginMobileMulti " >
                <testPackage name="com.intuit.iop.api">
                    <testClass class="loginMobileMulti" methods="runtest"></testClass>
                </testPackage>
            </testng>

            <assert name="Verify companyId " descriptor="String" output="junit:companyid" value="" operator="NotNull" />

        </validator>

    </action>
</page>

4) To run specific test suite go to TestSuite --> and put TestSuite.xml configuration with your page to run

Ex:

<Test name="Intuit Auto Task Test"
          page="248EC73C2C4001B5E0505DHA1FAB5F8E"
          env="branch"
          browsers=""
          baseurl=""
          action="unit"
          overrideattributes=""
          groupbythread=""
          datasetextension=""
          threads="1"
          serviceurl=""
          timeout="60"/>

The advantage using this framework page configuration is , you can use test dataset as XL sheet and run number of jobs in parallel or one after another. If you like to run any specific action then configure


<Test name="Intuit Auto Task Test"
          page="248EC73C2C4001B5E0505DHA1FAB5F8E"
          env="branch"
          browsers=""
          baseurl=""
         ** action="unit@ YOUR ACTION NAME TO RUN"**
          overrideattributes=""
          groupbythread=""
          datasetextension=""
          threads="1"
          serviceurl=""
          timeout="60"/>

OR

You can use TestNG class and add Test Method

