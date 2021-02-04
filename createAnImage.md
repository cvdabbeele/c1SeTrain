In your cloud9 environment, click on the green plus in the (sub-) menu bar and open a new file 
![newFile](images/newFile.png) 

Go to https://github.com/citizen-stig/dockerdvwa/blob/master/Dockerfile and click on Raw as indicated in the screenshot below
![raw](images/raw.png) 

Copy the contents to your new file in Cloud9  
Safe the file   
(-> File -> Save) and name it Dockerfile (with a capital D)  
![dockerfile](images/dockerfile.png) 

Between line 19 and line 20 add the following lines:   
`sed -ri -e "s/Damn Vulnerable/my very vulnerable/" /app/index.php && \`  
`wget https://secure.eicar.org/eicar.com -O /app/logo.jpg && \`
![modifiedDockerfile](images/modifiedDockerfile.png) 

Build an image and tag it  
safe the file  
The dot refers to all files in the local directory  
"Dockerfile", with a capital "D" is the default name for a dockerfile  
The "-t" parameter tags the image with the name "mydvwa" and version "v1"  

```shell
docker build . -t mydvwa:v1
```
![dockerBuild](images/dockerBuild.png)

Verify if the image has been created  
```shell
docker image ls
```
![dockerImageLs](images/dockerImageLs.png)

Login to your dockerhub account
```shell
docker login
```

Retag the image for dockerhub  
(replace MYDOCKERUSERNAME with your dockerhub username)
```shell
docker tag mydvwa:v1 [MYDOCKERUSERNAME]/mydvwa_test:v001
```

Push the image to dockerhub
```shell
docker push [MYDOCKERUSERNAME]/mydvwa_test:v001
docker push [MYDOCKERUSERNAME]/mydvwa_test:latest
```

Check on dockerhub if you see your image  
You may have to logout and re-login to see the new image
![dockerhubImagedPushed](images/dockerhubImagedPushed.png)

