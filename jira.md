## Installing Jira as a Docker Container:

#### Creating a Volume and running the container
```bash
docker volume create --name jiraVolume  
docker run -v jiraVolume:/var/atlassian/application-data/jira --platform linux/amd64 --name="jira" -d -p 8080:8080 atlassian/jira-software
```

#### Access Jira in Browser
http://localhost:808/

