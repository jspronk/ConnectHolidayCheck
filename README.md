# ConnectHolidayCheck
1. Create a Lambda function, using the Node runtime. For more information, see [Create a Lambda Function](https://docs.aws.amazon.com/lambda/latest/dg/getting-started-create-function.html) in the *AWS Lambda Developer Guide*.
2. Create an Enviroment Variable with the key "TIMEZONE" and a value of your contact center's timezone. Possible values can be found [here](http://worldtimeapi.org/timezones). If TIMEZONE is not created or left blank, the Lambda will use the UTC timezone.
3. Create an Environment Varliable with the key "Holiday_Test" and assign it a value of your first holiday in MM/DD format. Continue adding Environment Variables(with keys starting with "Holiday_", for example "Holiday_Thanksgiving") for each of your holidays.
![Image](https://github.com/jspronk/ConnectHolidayCheck/blob/master/LambdaEnviorVars.jpg)
4. Save your Lambda. 
5. Add your Lambda Function to your Amazon Connect Instance by following [these instructions](https://docs.aws.amazon.com/connect/latest/adminguide/connect-lambda-functions.html#add-lambda-function)
6. Invoke your Lambda Function from a Contact Flow by following [these instructions](https://docs.aws.amazon.com/connect/latest/adminguide/connect-lambda-functions.html#function-contact-flow)
7. From the Success path of your Invoke Lambda node, create a CHeck Contact Attributes node and configure it to look for the External Attribute of CLOSED.  If the Lambda function finds a match for today's call in your Environment Variables, CLOSED will equal Yes, else it will be equal to No. (tip: Yes and No are case sensitive).
![Image](https://github.com/jspronk/ConnectHolidayCheck/blob/master/contactFlowSample.jpg)

