# DotNet-CICD

# YAML File...

stages:
  - build
  - test
  - deploy

variables:
  ASPNETCORE_ENVIRONMENT: "Production"

build:
  stage: build
  image: mcr.microsoft.com/dotnet/sdk:6.0
  script:
    - cd src
    - dotnet restore
    - dotnet build --configuration Release --no-restore
  artifacts:
    paths:
      - src/**/bin/Release/net6.0/

test:
  stage: test
  image: mcr.microsoft.com/dotnet/sdk:6.0
  script:
    - cd src
    - dotnet test --no-restore --verbosity normal

deploy:
  stage: deploy
  image: mcr.microsoft.com/dotnet/sdk:6.0
  script:
    - cd src
    - dotnet publish -c Release -o ./publish
    # Your deployment commands here (e.g., copy to server)
    - echo "Deploying to server..."
  only:
    - feature
    
# ..

![image](https://github.com/kushalShuklaaa/DotNet-CICD/assets/96085546/3d80c1ba-e307-4e37-ad75-b3a6d22d8e5d)

![image](https://github.com/kushalShuklaaa/DotNet-CICD/assets/96085546/9bc6fa79-b637-429a-aace-12c84b043834)

![image](https://github.com/kushalShuklaaa/DotNet-CICD/assets/96085546/88c8a83d-02ee-4648-916b-eb6926df0c0e)

