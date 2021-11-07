# Google Cloud - Deploy Hello World application
We will
- Initialize App Engine
- Preview application running locally in Cloud Shell
- Deploy so that others can reach it
- Disable an App Engine application
## Initialize App Engine
### Activate Google Cloud Shell
Google Cloud Shell is a virtual machine that is loaded with development tools. It offers a persistent 5GB home directory and runs on the Google Cloud. Google Cloud Shell provides command-line access to your GCP resources.</br>
![0CloudShell](https://user-images.githubusercontent.com/73010204/140631538-c67e0b86-a48f-4525-bb75-9514eb2b6f05.PNG)</br>
Click **Continue.**</br>
It takes a few moments to provision and connect to the environment. When you are connected, you are already authenticated, and the project is set to your PROJECT_ID.</br>
_gcloud_ is the command-line tool for Google Cloud Platform. It comes pre-installed on Cloud Shell and supports tab-completion.
### Initialize App Engine
```sh
gcloud app create --project=$DEVSHELL_PROJECT_ID 
```
![bb](https://user-images.githubusercontent.com/73010204/140631679-fa6beeeb-1c4f-4e01-af85-110201851a03.png)</br>
When prompted, select the region where you want your App Engine application located.
### Clone the source code repository
For a sample application in the hello_world directory:
```sh
git clone https://github.com/GoogleCloudPlatform/python-docs-samples 
```
Navigate to the source directory:
```sh
cd python-docs-samples/appengine/standard_python3/hello_world 
```
![cc](https://user-images.githubusercontent.com/73010204/140631746-ba3111e3-15a0-4990-91f3-61c8bae3817a.png)
## Run Hello World application locally
Firstly, run the Hello World application in a local, virtual environment in Cloud Shell.</br>
1. Execute the following command to download and update the packages list.
```sh
sudo apt-get update 
```
2. Set up a virtual environment in which you will run your application. Python virtual environments are used to isolate package installations from the system.
```sh
sudo apt-get install virtualenv
```
If prompted [Y/n], press Y and then Enter.
```sh
virtualenv -p python3 venv
```
3. Activate the virtual environment.
 ```sh
source venv/bin/activate
```
4. Navigate to your project directory and install dependencies.
 ```sh
pip install  -r requirements.txt
```
5. Run the application. Ignore the warning if any.
 ```sh
python main.py
```
6. In Cloud Shell, click Web preview (Web Preview) > Preview on port 8080 to preview the application.
![dd](https://user-images.githubusercontent.com/73010204/140631926-b6ff0f0b-a759-42af-b9b2-e26e8166a732.PNG)</br>
Here is the output
![1](https://user-images.githubusercontent.com/73010204/140632603-9099b92b-6b9f-4ecf-bc7e-53896ab8ea1b.PNG)</br>
7. To end the test, return to Cloud Shell and press Ctrl+C to abort the deployed service.
8. Using the Cloud Console, verify that **the app is not deployed.** In the Cloud Console, on the Navigation menu click **App Engine > Dashboard.**</br>
![3](https://user-images.githubusercontent.com/73010204/140632019-e2c554dd-72c1-4364-b0bc-012273d24455.PNG)
## Deploy and run Hello World on App Engine
To deploy your application to the **App Engine Standard** environment:
1. Navigate to the source directory:
```sh
cd ~/python-docs-samples/appengine/standard_python3/hello_world
```
2. Deploy your Hello World application.
```sh
gcloud app deploy
``` 
- If prompted "Do you want to continue (Y/n)?", press Y and then Enter.
- This **app deploy** command uses the _app.yaml_ file to identify project configuration.
![ff](https://user-images.githubusercontent.com/73010204/140632123-76a02608-ab3f-4fbf-940c-316f3034062c.png)
3. Launch your browser to view the app at http://YOUR_PROJECT_ID.appspot.com
```sh
gcloud app browse
```
![gg](https://user-images.githubusercontent.com/73010204/140632162-4058ac8e-1a24-4e9c-b7df-59814e87363d.PNG)</br>
Copy and paste the URL into a new browser window. Result:</br>
![6](https://user-images.githubusercontent.com/73010204/140632178-8dacb78b-fcb3-42d9-9932-c7ae5d926f1e.PNG)
## Disable the application
App Engine offers no option to Undeploy an application. After an application is deployed, it remains deployed, although you could instead replace the application with a simple page that says something like "not in service."</br>
However, you can disable the application, which causes it to no longer be accessible to users.
1. In the Cloud Console, on the Navigation menu, click **App Engine > Settings.**
2. Click **Disable** application.
3. Read the dialog message. Enter the **App ID** and click **DISABLE.**
![hh](https://user-images.githubusercontent.com/73010204/140632282-70c6940d-7fcf-4f62-85dc-44d852b67620.png)
If you refresh the browser window you used to view to the application site, you'll get a 404 error.
![2](https://user-images.githubusercontent.com/73010204/140632604-fc2a73cc-2b89-4499-b450-ea31072c531f.PNG)
## Congratulations!
You created your first application using App Engine!
## Referenence
**Google Cloud Fundamentals: Core Infrastructure** course</br>
https://www.coursera.org/learn/gcp-fundamentals/home/welcome
