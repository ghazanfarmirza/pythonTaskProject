# pythonTaskProject

To run the project, first we would need to have credentials of google api services 
if you are setting up the first time, then we have to first, go to https://console.developers.google.com/ from your browser.
First of all we would create a project by going to the api and services then select the opiton create 
Now, you should see a button that says ENABLE APIS AND SERVICES. Click on it.
After that, click the enable button.

To setup the credentials, create credentials so that you application can authenticate itself when trying to access Google Drive resources later on
At first, it might be overwhelming to choose the type of credentials that you need. Google has done a great job in creating a set of questions to help you figure out which credentials to create.


Set Up OAuth Consent Screen and Add API Scope
After you fill up the above questionnaire, Google will recommend that you application requires the OAuth client ID and before you can set this up, you need to set up OAuth consent screen.

we are going to add the scope that we want our application to be able to do. Scope is like giving permissions to our credentials which then determine what our application has access to.


Create Credentials: Client Secret (OAuth Client ID)
Next, we are going to add our credentials so that Google can identify who our application is and what scope it has, etc. This is known as the Client Secret. Go on and click on Create credentials > OAuth client ID.

we are going to select Other as our Application type as this is build on a command line application. But, you can choose whatever type of application you want to build.

After this step, you are going to have your Client Secret, which you can download so your application can use it to authenticate itself. Go on and click on the Download, which is the down arrow icon. Your client secret is a JSON file. Rename it to client_secret.json

Create a folder in the project directory called credentials to store your client_secret.json which you can download from your Google Console.

Your project structure should look like this to begin with. The connect_to_google_drive.py is the Python file that contains instructions to connect to Google Drive Sheets API


access token will be stored in credentials/credentials.json upon the browser authentication, which I will go through after this.
Now, save the file and go to your terminal. Follow below commands to get your access token. Note: if you execute the above script from an IDE (I use PyCharm), you would get an error. For the first time only, you need to execute the script from your terminal

run:
python connect_to_google_drive.py

# below is the output of the above command
/Users/bobthedude/virtualenv/venv_google_api/lib/python3.7/site-packages/oauth2client/_helpers.py:255: UserWarning: Cannot access ./credentials/credentials.json: No such file or directory
  warnings.warn(_MISSING_FILE_MESSAGE.format(filename))
Your browser has been opened to visit:
https://accounts.google.com/o/oauth2/auth?client_id=123456789101-ab12r1abcdefjklm1a2bcdefghi12a1a.apps.googleusercontent.com&redirect_uri=http%3A%2F%2Flocalhost%3A8080%2F&scope=https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fdrive&access_type=offline&response_type=code


A browser tab will open after the above command execution. Select the Google account on which you set up your API and credentials in the previous step. Then click on Allow.


Once again, Google will prompt you and ask for a confirmation if you want to allow your First Medium Application to access your Google Drive files. Go on and click on Allow.


If successful, your browser will return a page with the following text The authentication flow has completed. And if you go back to your terminal, you should see an additional 2 lines (indicating authentication success) printed as follows.

Your browser has been opened to visit:
https://accounts.google.com/o/oauth2/auth?client_id=123456789101-ab12r1abcdefjklm1a2bcdefghi12a1a.apps.googleusercontent.com&redirect_uri=http%3A%2F%2Flocalhost%3A8080%2F&scope=https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fdrive&access_type=offline&response_type=code
If your browser is on a different machine then exit and re-run this
application with the command-line parameter
--noauth_local_webserver
Authentication successful.
success


Additionally, you will see a new file credentials.json gets created in the credentials folder. Awesome job! We have now obtained our access token which we can use to connect to Google Drive API resources.


