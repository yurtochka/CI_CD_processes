# CI/CD processes

  ### Получилось зарегестрироваться и хорошо! :)
  
  Репозиторий: # https://gitlab.com/gb_3623/hw_1
  
  ## `1. Создать pipeline и runner` ##
  
  ![pipeline](https://github.com/yurtochka/CI_CD_processes/blob/main/pipeline.jpg) 
  
  
  ![runner](https://github.com/yurtochka/CI_CD_processes/blob/main/runner.jpg) 

  
  ![create_runner](https://github.com/yurtochka/CI_CD_processes/blob/main/create_runner.jpg) 
  

  ## `2. Попробовать сохранить артефакт одной из стадий + исключить из папки с артифактами любой файл` ##
  ## `3. Попробовать сделать любую gitlab pages` ##

    stages:
      - build
      - test
      - deploy
      - pages
    
    image: alpine
    
    build_job:
      stage: build
      script:
        - echo "Building the project..."
      artifacts:
        paths:
          - public
        exclude:
          - "*.md"
    
    test_job:
      stage: test
      script:
        - echo "Running tests..."
        - sleep 60
        - echo "Code coverage is 90%"
    
    deploy_job:
      stage: deploy
      environment: production
      script:
        - echo "Deploying the project..."
    
    pages_job:
      stage: deploy
      script:
        - echo "Deploying static websites..."
      artifacts:
        paths:
          - public/
      only:
        - main
    
    pages:
      stage: deploy
      script:
        - echo 'Publishing website to GitLab Pages'
      artifacts:
        paths:
          - public/
        exclude:
          - public/temp.txt

  
  ![gitlab_project](https://github.com/yurtochka/CI_CD_processes/blob/main/gitlab_project.jpg) 

  
  ![jobs](https://github.com/yurtochka/CI_CD_processes/blob/main/jobs.jpg) 
