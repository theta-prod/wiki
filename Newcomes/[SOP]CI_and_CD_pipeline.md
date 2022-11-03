# [SOP] How to start to implement CI and CD

- **Metadata** : `type: SOP` `scope: SRE` 
- **Techs Need** :
  - `Docker Image` `Docker` `Docker-compose`
  - `unit test` `test coverage`
  - `Github Action` 
  - `DockerHub` 
- **Status** : `on-going`

## ✨ You should already know

> Docker: Docker, Docker-compose
> 
> Testing: unittest, test coverage
> 
> Platform: Github, Github Action, DockerHub

👩‍💻 👨‍💻

## ✨ About the wiki

- `Situation:`  We need a standard to maintain team's repo 
- `Target:` CI/CD Implementation For All Project
```
CI: Repo      === GitHub Action:[Image] ===> DockerHub
CD: DockerHub === [Image]:docker-compose ===> Prod Server
```
- `Index:`

| Sub title | decription | memo |
| ------ | ------ | ------ |
| CI | - | On-going |
| CD | - | On-going |


## ✨  Sections


### **CI**
`type: doc` `status: on-going`

we have to build some steps in CI
> - Test: Run Server
> - Test: Run Unit Test
> - Test: Run Test Coverage
> - Docker: Build Image
> - Docker: Push Image to dockerhub
#### 📝 What's is must
- Run Test Coverage > 80%
- Push to dockerhub
```
secrets:
    - Dockerhub account
    - Dockerhub password
```

#### 📝 How start to build ci pipeline
examples:
- [[Tutorial] CD by docker-compose.md](/SRE/[Tutorial]CI_by_GitHub_Action.md)


### **CD**
`type: doc` `status: on-going`
> we have to build some steps in CD
> - Docker: Pull Image from dockerhub
> - Docker: Up Server by docker-compose

#### 📝 How start to build cd pipeline
examples:
- [[Tutorial] CD by docker-compose.md](/SRE/[Tutorial]CD_by_docker-compose.md)

#### 📝 What's is must
- Open a repo for depoly
- `up.sh`: a file can one-line to up your service
