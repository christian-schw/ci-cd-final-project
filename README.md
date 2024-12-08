<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a id="readme-top"></a>

# Building CI/CD Pipelines
<!-- TABLE OF CONTENTS -->
<details open>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#introduction">Introduction</a></li>
    <li>
      <a href="#course-information">Course Information</a>
    </li>
    <li>
      <a href="#information-about-the-project">Information about the Project</a>
      <ul>
        <li><a href="#general">General</a></li>
        <li><a href="#tech-stack">Tech Stack</a></li>
      </ul>
    </li>
    <li>
      <a href="#what-i-have-done-as-part-of-the-project">What I have done as part of the project</a></li>
      <ul>
        <li><a href="#task-1---ci-with-github-actions">Task 1 - CI with GitHub Actions</a></li>
        <li><a href="#task-2---cd-with-tekton-and-openshift">Task 2 - CD with Tekton and OpenShift</a></li>
      </ul>
    </li>
    <li><a href="#getting-started">Getting Started</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>
<br>


## Introduction
This repository was created as part of IBM's "Continuous Integration and Delivery (CI/CD)" course.<br>
It's a project about building a CI/CD pipeline.<br>
<br>
Much of the code was cloned from the IBM repository: https://github.com/ibm-developer-skills-network/vselh-ci-cd-final-project-template<br>
<br>
Scenario: You’re part of a team responsible for building an innovative microservice, a RESTful API that allows users to manage and track counters.<br>
Another team has already developed the user interface (UI) for this microservice,<br>
and it's now your turn to ensure the reliability and efficiency of the backend services.<br>
<br>
Tasks that need to be completed:
- Continuous Integration (CI) with GitHub Actions - Linting and testing
- Continuous Deployment (CD) with OpenShift Pipelines - Linting, testing, building an image and deploying the microservice to an OpenShift Cluster
<br>
Preview images of the project:<br>
<br>

![3 detailed view of build workflow](https://github.com/user-attachments/assets/06bcfc61-8b28-451c-8add-9bfba58c8532)

![1 Implement tasks yaml](https://github.com/user-attachments/assets/f5dbe65a-87d5-46f0-b2ca-f1222b52bcbc)

![9 adding deploy openshift-client task to pipeline](https://github.com/user-attachments/assets/3e7323d8-76d2-4c66-985b-3e7d466e2707)

<p align="right">(<a href="#readme-top">back to top</a>)</p>
<br>
<br>


## Course Information
Title: Continuous Integration and Delivery (CI/CD)<br>
Type: Final Project<br>
Course Provider: IBM<br>
<p align="right">(<a href="#readme-top">back to top</a>)</p>
<br>
<br>


## Information about the Project
### General
- Client: Myself
- Project Goal: Building a CI/CD pipeline. Gain a deeper understanding of Continous Integration and Continous Delivery.
- Number of Project Participants: 1 (Cloned repository of IBM. Developed the rest on my own)
- Time Period: December, 2024
- Industry / Area: DevOps
- Role: Developer
- Languages: English
- Result: CI/CD pipeline successfully built. Improved understanding of implementing Continous Integration and Continous Delivery.
<br>

### Tech Stack
With regard to my role:<br>
- CI/CD Tool: GitHub Actions
- CI/CD Tool: Tekton
- Container Orchestration: Kubernetes
- Container Orchestration: Red Hat OpenShift
- IBM Cloud IDE (based on Theia and Container)
<p align="right">(<a href="#readme-top">back to top</a>)</p>
<br>
<br>



## What I have done as part of the project

### Task 1 - CI with GitHub Actions
First the workflow YML file with the name of the workflow as well as the events, the job, the runner including the container and required steps were defined:<br>

![1 Implement workflow yaml](https://github.com/user-attachments/assets/b7e5491a-0c46-4033-a151-bfc82c10aa72)

If you check the Actions tab on the GitHub website, you will see executed workflows:<br>

![2 All workflows view in Github](https://github.com/user-attachments/assets/16ea6f15-6872-4329-985e-83d848e12121)

After clicking on the build job, exact details of the individual steps can be viewed:<br>

![3 detailed view of build workflow](https://github.com/user-attachments/assets/972ae13b-51ef-4c0c-8620-a66ee30b86d7)

The logs show that everything is working perfectly.<br>
The CD part can now be implemented.<br>
<p align="right">(<a href="#readme-top">back to top</a>)</p>
<br>
<br>


### Task 2 - CD with Tekton and OpenShift
The next step is to create the CD workflow in OpenShift.<br>
The cleanup task is added first that will clean the output workspace so that the CD pipeline can start fresh.<br>
<br>
The corresponding YML file (/.tekton/tasks.yml):<br>

![1 Implement tasks yaml](https://github.com/user-attachments/assets/1ff138cf-3a5d-4936-a911-bd174169044b)

The test task (with the testing framework nose) is added after the cleanup task:<br>

![2 Adding task nose to tasks yaml](https://github.com/user-attachments/assets/2c15300f-a2db-48dd-9e70-4248676dcead)

Applying the new tasks to the cluster and verifying:<br>

![3 applying and verifying tasks yml](https://github.com/user-attachments/assets/6c871a48-bcd0-4c01-89bd-68dbe006ccc0)

The pipeline is now built using the OpenShift Web Console.<br>
A Workspace / PersistentVolumeClaim (PVC) is required for the tasks.<br>
<br>
The creation of the PVC:<br>

![4 creating pvc in openshift webconsole](https://github.com/user-attachments/assets/b0bf7237-4426-4a17-ae93-7085f06fb5dd)

A pipeline including a workspace object was then created using the PVC.<br>
The cleanup task in tasks.yml has been added to the pipeline and tested:<br>

![5 create pipeline with 1 task and test it](https://github.com/user-attachments/assets/2db2daaa-55e4-4a1b-88ab-b01bc823645d)

![5 part 2 create pipeline with 1 task and test it](https://github.com/user-attachments/assets/cacf55c2-0763-4425-b68b-a78b59dd6a58)

The logs show that everything is working perfectly.<br>
Further tasks are added to the pipeline:<br>

![6 adding further tasks in openshift pipeline](https://github.com/user-attachments/assets/04d2e9cd-8830-4812-989f-0ae16b57b6c3)

The pipeline is then executed and the logs are examined:<br>

![7 running the pipeline](https://github.com/user-attachments/assets/2c00e6f1-a0a9-4ffb-ab3b-cf95c9503477)

![8 viewing logs of pipeline](https://github.com/user-attachments/assets/df694acd-ca6a-4cea-a534-d242a17069df)

Again: The logs show that everything is working perfectly.<br>
The final step of the pipeline: Deploying the application to the openshift cluster using the predefined 'openshift-client' task.<br>

![9 adding deploy openshift-client task to pipeline](https://github.com/user-attachments/assets/4509c931-3b0f-4985-8ca0-afcfd50fe442)

Pipeline is executed and the logs are examined:<br>

![10 viewing logs of deploy](https://github.com/user-attachments/assets/36ac8452-7280-44f4-ad62-2b4b66acf4be)

Again: The logs show that everything is working perfectly.<br>
As an additional test, the generated deployment / pod is also checked:<br>

![11 confirming running pod of deployment](https://github.com/user-attachments/assets/6bc5f109-ad91-4306-a600-298938d381a9)

Status is 'Running', so everything fits.<br>
The project has been successfully completed!<br>
<p align="right">(<a href="#readme-top">back to top</a>)</p>
<br>
<br>


## Getting Started
After cloning you will need to run the `setup.sh` script in the `./bin` folder to install the prerequisite software.

```bash
bash bin/setup.sh
```

Then you must exit the shell and start a new one for the Python virtual environment to be activated.

```bash
exit
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>
<br>
<br>


## Contact
If you have any questions, please feel free to reach out via email: christian-schwanse (at) gmx.net<br>
<p align="right">(<a href="#readme-top">back to top</a>)</p>
