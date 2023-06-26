# notification_test

How to use email notification service to monitor our status/deployment changes made to the repo?<br>
Configure the YAML file like given below.<br>
name: Notify developers via email #name of a job<br>
        if: ${{ always() }} #always give the status doesn't matter it is a failure or success<br>
        uses: dawidd6/action-send-mail@v3 # Action used to run email service<br>
        with:<br>
          server_address: smtp.gmail.com # server_address of the email service you are using (get from google)<br>
          server_port: 587 #get from google<br>
          username: ${{ secrets.EMAIL_USERNAME }} #Store from email add to your secret repository (in this case, abc.xyz@gmail.com)<br>
          password: ${{ secrets.EMAIL_PASSWORD }} # Store the app pwd of abc.xyz@gmail.com to your secret repository<br>
          subject: Super-Linter Notification<br>
          body: |<br>
            The Super-Linter job was ${{ job.status }}! # Getting the status of a job<br>
          from: abc.xyz@gmail.com<br>
          to: pqr.abc@gmail.com # Email id to whom you want to send<br>
<br>
How to get App Password for your email id (note - you cannot store direct pwd to secret repository)?<br>
Step 1 - Enable IMAP Access : Go to browser setting-> POP/IMAP forwarding-> Enable IMAP<br>
Step 2 - Enable 2 Factor authentication for from email id.<br>
Step 3 - Visit the app password page of your gmail id and select the device for that you want to create the password.<br>
Step 4 - Store the password into secret repositories without '-'.<br>
