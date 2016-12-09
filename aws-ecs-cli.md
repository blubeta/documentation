# Docker

* `docker build -t [name] [path]` (i.e. docker build tech-crawl .)
* `docker tag tech-crawl:latest 430326878821.dkr.ecr.us-east-1.amazonaws.com/tech-crawl:latest`
* `docker push 430326878821.dkr.ecr.us-east-1.amazonaws.com/tech-crawl:latest`

<br>
---
<br>

# Docker / AWS ECS

## List clusters
`aws ecs list-clusters --profile blubeta`

---
<br>

## List task revisions (task definitions)
`aws ecs list-task-definitions --profile blubeta`

### Response 
```json
{
   "taskDefinitionArns": [
   "arn:aws:ecs:us-east-1:430326878821:task-definition/nginx-test:1",
   "arn:aws:ecs:us-east-1:430326878821:task-definition/nginx-test:2"
   ]
}
```

<br>

## List tasks in cluster
`aws ecs list-tasks --cluster arn:aws:ecs:us-east-1:430326878821:cluster/testing --profile blubeta`
OR
`aws ecs list-tasks --cluster testing --profile blubeta`

<br>

## Update a task-definition
`aws ecs register-task-definition --family ${TASK_FAMILY} --cli-input-json file:///tmp/tmp.json --profile blubeta`

### Response
```json
{
   "taskArns": [
   "arn:aws:ecs:us-east-1:430326878821:task/9e5eeeeb-bc79-4a0e-a3c2-8b1da54064e1"
   ]
}
```

<br>

## Stop task
`aws ecs stop-task --cluster testing --task 9e5eeeeb-bc79-4a0e-a3c2-8b1da54064e1 --profile blubeta`

<br>

## Update a service with new task definition
`aws ecs update-service --service nginx-service --task-definition nginx-test:9 --cluster testing --profile blubeta`

<br>

# To Update a service
1. Update task-definition
2. Stop task (if single instance, if not new task will spawn when upating the service)
3. Update service with new task definition (revision)

<br>

# Deploy new task-definition revision
```bash
TASK_FAMILY=nginx-test
DOCKER_IMAGE="430326878821.dkr.ecr.us-east-1.amazonaws.com/nginx-test:develop"
LATEST_TASK_DEFINITION=$(aws ecs describe-task-definition --task-definition ${TASK_FAMILY} --profile blubeta)
MEMORY=256

echo $LATEST_TASK_DEFINITION \
     | jq '{containerDefinitions: .taskDefinition.containerDefinitions, volumes: .taskDefinition.volumes}' \
     | jq '.containerDefinitions[0].image='\"${DOCKER_IMAGE}\" \
     | jq '.containerDefinitions[0].portMappings[0].hostPort='80 \
     | jq '.containerDefinitions[0].portMappings[0].containerPort='80 \
     | jq '.containerDefinitions[0].portMappings[0].protocol='\"tcp\" \
     | jq '.containerDefinitions[0].memory='${MEMORY} \
     > /tmp/tmp.json

aws ecs register-task-definition --family ${TASK_FAMILY} --cli-input-json file:///tmp/tmp.json --profile blubeta
```
