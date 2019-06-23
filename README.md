# Amazon Lex Twilio SMS Chat integration
An AWS Lambda function that integrates Twilio Programmable SMS with Amazon Lex.

For detailed implementation instructions, please read this blogpost: https://aws.amazon.com/blogs/ai/integrate-your-amazon-lex-bot-with-any-messaging-service/


![alt text](https://github.com/javabrown/amazon-lex-twilio-sms-chatbot/blob/master/Lex_Bot_1.gif?raw=true)


## Project Setup
1. ```git clone https://github.com/javabrown/amazon-lex-twilio-sms-chatbot.git```

2. ```cd amazon-lex-twilio-sms-chatbot```

3. ```npm install```

4. ```create zip --> zip -r AmazonLexTwilioIntegration.zip (linux/mac)```

5. Log in to the AWS Lambda console, and choose Create a Lambda function.

6. Choose the Blank Function blueprint, and choose Next.

7. Leave the trigger empty, and then choose Next.

8. For the Lambda function, type LexTwilioIntegration, and for the Runtime environment, choose js 4.3.
  (Because the Node.js application uses third-party modules, you can’t use the Lambda console editor to edit code.) 

9. Choose Upload a .ZIP file, and choose the .zip file that you created in step 4.

10. The Lambda function uses four environment variables. Add them:
![alt text](https://github.com/javabrown/amazon-lex-twilio-sms-chatbot/blob/master/Lex_Bot_2.gif?raw=true)

You need to create the gateway before you can set the API_GATEWAY_URL value, so leave that field blank for now. You will provide this value later.

11. Leave the Handler set to index.handler, and then choose Choose an existing role. Type lambda-exec-role-for-lex, which is the role that you created for this Lambda function to assume.

12. To review the details for the Lambda function, choose Next, and then choose Create function. This sets up the Lambda function.

13. Quickly test to see if the Lambda function can communicate with your chatbot. Choose Actions, and then choose Configure test event and paste in the following JSON:
```
{
"body-json": "From=867-5309&Body=book+hotel"
}
```

This simulates the From and Body parameters that the Twilio webhook will submit to your HTTPS endpoint. You should see a response from the chatbot that looks something like this:
![alt text](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2017/05/19/Lex_Bot_3.gif)

You’ve gotten a response from your bot! Now you can create your API endpoint.


## Setup AWS API Gateway to create an HTTPS endpoint 
 Follow AWS Instructions [Instructions](https://aws.amazon.com/blogs/machine-learning/integrate-your-amazon-lex-bot-with-any-messaging-service/).


#### ***Curtsy: Ahmad R. Khan & AWS Team handling demo projects repos. Most of the project idea are derived from AWS Demo repositories.
