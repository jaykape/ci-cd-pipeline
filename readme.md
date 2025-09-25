## CI/CD pipeline

In this project I will use Jenkins to make a CI/CD pipeline. The flow is as below.
Jenkins will polling to this repository for commits, then build and test Docker image, pusg it and tell Kubernetes to pull the image and rolling update deployment.

![](diagram.jpeg)

---

### Step 1 Run Docker version of Jenkins

Spin up Jenkins in docker. Pick initial credential to get access and create user.


### Step 2 Setup Kubernetes Cluster

See [Kubernetes Homelab](https://github.com/jaykape/operation-experiment/blob/main/kubernetes.md)

### Step 3 Set up Jenkins pipeline

- Click New Item >> Pipeline

- On "Triggers" pick "Poll SCM" so it will polling to github repo.
  In "Schedule" write `H/5 * * * *` = every 5 mins

- On "Pipeline" 
  Pick Definition = "Pipelinescript from SCM" (So we can put pipeline code in version control too).
  Pick SCM = "Git" and put the repo path here.
  *Note that no credential needed for public repo.

- Save

- Write the Jenkinsfile to define jobs in the pipeline and put in this repo.


   