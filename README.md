# CI_CD_processes

  1.simple pipeline:
  stages:
    - build
    - test
    - deploy
  
  build_job:
    stage: build
    script:
      - echo "Building the project..."
  
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
