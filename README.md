Paste the following code into your Jenkinsfile in your GitHub repository. This script includes a special triggers block that explicitly tells Jenkins to listen for GitHub push events.

3 Steps to Make the Webhook Work

Even with the script, you must configure two settings to bridge the gap between GitHub and your EC2 instance:
In Jenkins Job:
<br>
Create a Pipeline job.
Under Build Triggers, check the box: GitHub hook trigger for GITScm polling.
Under Pipeline, select Pipeline script from SCM, choose Git, and provide your repo URL.


In GitHub Repository:
<br>

Go to Settings -> Webhooks -> Add Webhook.
Payload URL: http://<your-ec2-ip>:8080/github-webhook/ (The trailing slash is required).
Content type: Select application/json.


In AWS (Security Group):
<br>
Ensure port 8080 is open to all traffic (or at least GitHub's IP range) so GitHub can send the "ping" to your Jenkins server.
