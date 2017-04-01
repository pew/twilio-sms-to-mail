# twilio-sms-to-mail
quick n' dirty twilio text (sms) to mail python app using postmark app

forwards all incoming text messages to your twilio phone number to a given email address

# 1. prep

1. get a https://www.twilio.com/ account and get a phone number ($1/month + per [sms fee](https://www.twilio.com/sms/pricing))
2. get a [https://postmarkapp.com/](https://postmarkapp.com/) account, you'll get 25,000 credits for free. That's about... 25,000 emails.

# 2. config

* retrieve your PostmarkApp API key and add it to `application.py` as 
`token`
* change the `toAddress` and `fromAddress` parts in `applicaiton.py` to fit your needs

# 3. run it

It's 2017, so run it in a docker container:

```
docker build -t twilio-sms2mail .
docker run -d -p5000:5000 --name twilio twilio-sms2mail
```

per default the flask app will listen on port 5000, you can either change the port through docker or use a http reverse proxy like nginx or caddy