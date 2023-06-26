# notification_test
How to use email notification service to monitor our status/deployment changes made to the repo?
Configure the YAML file like given below.
name: Notify developers via email #name of a job
        if: ${{ always() }} #always give the status doesn't matter it is a failure or success
        uses: dawidd6/action-send-mail@v3 # Action used to run email service
        with:
          server_address: smtp.gmail.com # server_address of the email service you are using (get from google)
          server_port: 587 #get from google
          username: ${{ secrets.EMAIL_USERNAME }} #Store from email add to your secret repository (in this case, abc.xyz@gmail.com)
          password: ${{ secrets.EMAIL_PASSWORD }} # Store the app pwd of abc.xyz@gmail.com to your secret repository
          subject: Super-Linter Notification
          body: |
            The Super-Linter job was ${{ job.status }}! # Getting the status of a job
          from: abc.xyz@gmail.com
          to: pqr.abc@gmail.com # Email id to whom you want to send

How to get App Password for your email id (note - you cannot store direct pwd to secret repository)?
Step 1 - Enable IMAP Access : Go to browser setting-> POP/IMAP forwarding-> Enable IMAP
Step 2 - Enable 2 Factor authentication for from email id.
Step 3 - Visit the app password page of your gmail id and select the device for that you want to create the password.
Step 4 - Store the password into secret repositories without '-'.
