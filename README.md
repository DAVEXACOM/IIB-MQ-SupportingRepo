# IIB-MQ-SupportingRepo
This repository contains collateral and documentation relating to the IIB-MQ repository

The IIB-MQ repository is a docker image build repository that has been enabled with Helm Charts for deployment into IBM Cloud Private and set up fully automated builds by Micro Services Builder Pipeline (Jenkins) also running on ICP.

IBM-MQandIIBonICP-DeploymentScenariosV3.pdf 
captures every step of my journey of exploring deployment scenarios for IIB and MQ on IBM Cloud private. It is in draft form as it was "written on the go" but covers the following.
  1. simply deploying and single IIB and single MQ containers via the built in Helm Charts via the ICP console
  2. deployment using command line Kubeclt from a GitHub docker repository for a custom combined IIB and MQ docker image
  3. modifying the custom combined IIB and MQ docker image repository to enable for Helm chart deployment
  4.using Micro Service Builder (Jenkins) pipeline on iCP to do the pull, build and deploy from the Helm chart version of the IIB and MQ    docker image repository on GitHub
  5.Webhook enabling the Github repository such that it "pokes" Micro Service Builder in iCP to do a rebuild and deploy when a new or updated BAR file of MQSC file is pushed to the Github repo
  
  IBM-MQandIIB-IBMCloudPrivate-MicroServicesBuilder.pdf 
  focuses on the IIB and MQ automated build pipeline using Micro Service Builder (Jenkins) pipeline to anable developers to go from local unit testing to a System Integration Test (SIT) environment.
  1.	Git Clone the DAVEXACOM\IIB-MQ repository to your GitHub organization
  2.	Explore the IIB-MQ file structure and the relationships such that you understand how an IIB/MQ Helm release repo for ICP hangs together, specifically:
    a.	The Docker file
    b.	The Jenkins file
    c.	The helm chart YAMLs
    d.	The .SH that executes when the container starts
  3.	Optionally change or add IBM MQ MQSC files or IIB BAR files in your copy of the IIB-MQ repo
  4.	Configure your IIB-MQ repo for OAuth application access from IBM MSB (Jenkins)
  5.	Configure and Deploy IBM MSB Pipeline (Jenkins) on IBM Cloud Private.
  6.	Kick off your first IIB/MQ deployment manually using Jenkins “Scan Repository Now”
  7.	Connect IBM MQ Web Console/IIB WebUI
  8.	Test the MyHTTPESQLTestFlow (hello world message flow) deployed on IIB 
  9.	Optionally create a local git clone on your IIB Toolkit workstation of your IIB-MQ repo so you can save you IIB Development work and push to the GitHub master repository (you don’t have to do this you can use another mechanism or simply upload changed or new bar files).
  10.	Create and configure the WebHook on your IIB-MQ Github repo to “call” the Jenkins URL on the ICP MSB pipeline to perform a new build when changes are made to the IIB-MQ repo.
  11.	Optionally. As Webhooks are inbound to Jenkins if the ICP instance is on a private network and you are using public Github you’ll need something like the IBM Cloud (Bluemix) Secure Gateway configured to offer a public IP address and port number to the Jenkins Webhook URL.
  12.	Update the MyHTTPESQLTestFlow (Project Interchange supplied) to change the “Hello World” message and Build and Save the BAR file.
  13.	Upload or Git Push the BAR file to your IIB-MQ repo
  14.	Follow the IBM MSB pipeline (Jenkins) console logs
  15.	Reconnect the IIB Web UI and IBM MQ Console
  16.	Retest the MyHTTPESQLTestFlow and observe the new “Hello World” message
  
  IIBMQicpDemoPI.zip 
  This is a project interchange file for the IIB Toolkit workspace I use when working with the IIB-MQ repository
  
