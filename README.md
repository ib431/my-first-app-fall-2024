# my-first-app-fall-2024

# setup

Create and activate a virtual environment (first time only):

```sh
conda create -n reports-env-2024 python=3.10
```

Activate the environment (whenever you come back to this project):
```sh
conda activate reports-env-2024
```

Install packages:

```sh
pip install -r requirements.txt
```

[Obtain an API Key](https://www.alphavantage.co/support/#api-key) from AlphaVantage.

Create a ".env" file and add contents like the following (using your own AlphaVantage API Key):

```sh
# this is the ".env" file:
ALPHAVANTAGE_API_KEY="..."
```

For the email sending functionality, Mailgun will be used. Setup for MailGun will entail  obtaining a MailGun API and setting up 3 credentials. You can set up your own domain using the following instructions. 

1.Go to "www.mailgun.com" and click "Get started for free" to create an account (fill in all of your information and click "create account"). After making your account, click "Get Started" under "Create an API Key" and create a key by clicking "add a key" and writing whatever description for it you'd like.

2.After receiving your API key from Mailgun, add it to the ".env" file as a variable called "MAILGUN_API_KEY" (see below).

3.Next, you need to add a credential for the MAILGUN_DOMAIN variable. In Mailgun, go to "Domains" tab ("Send" tab --> "Sending" dropdown --> "Domains") and copy the listed domain that starts with "sandbox." Add that to the ".env" file as a variable called "MAILGUN_DOMAIN".

4.For the last notebook secret, use your email address as the variable contents and name the variable "MAILGUN_SENDER_ADDRESS". Lastly, before sending any emails, be sure to list your authorized recipients in Mailgun. Do this under the "Overview" tab ("Send" tab --> "Sending dropdown" --> "Overview") by entering any email addresses you'd like to send to under the "Authorized Recipients" tab on the right of your screen and clicking "Save Recipient". Before running the code, have your recipient(s) click "I Agree" in the email they receive from Mailgun and "Yes" for the subsequent confirmation message. 

```sh
# add the following variables to the ".env" file to send emails via mailgun
MAILGUN_SENDER_ADDRESS="example@georgetown.edu"
MAILGUN_DOMAIN="sandbox-xyz.mailgun.org"
MAILGUN_API_KEY="your-mailgun-api-key"
```

## Usage

Run the example script:

```sh
python app/my_script.py
```

Run the unemployment report:

```sh
#ALPHAVANTAGE_API_KEY="..." python app/unemployment.py

python -m app.unemployment
```

Run the stocks report:

```sh
# python app/stocks.py
python -m app.stocks
```

Run the email sending functionality:

```sh
python app/email_service.py
```



## Testing

Run tests: 
```sh
pytest
```