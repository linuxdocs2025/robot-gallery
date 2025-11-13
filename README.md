




### Install SonarQube:

   - Install SonarQube and Trivy on the EC2 instance to scan for vulnerabilities.
        
       sonarqube
       ```
       docker run -d --name sonar -p 9000:9000 sonarqube:lts-community
       ```

       To access: 
        
        publicIP:9000 (by default username & password is admin)
        
        
        
        
### Integrate SonarQube and Configure:

   - Integrate SonarQube with your CI/CD pipeline.
   - Configure SonarQube to analyze code for quality and security issues.


**Note: ** By default, SonarQube will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 9000 in the inbound traffic rules as show below.

- EC2 > Instances > Click on <Instance-ID>
- In the bottom tabs -> Click on Security
- Security groups -> Edit inbound rules
- add 9000 Port for SonarQube 



### Login to SonarQube using the below URL:

`http://<ec2-instance-public-ip-address>:9000`  [You can get the ec2-instance-public-ip-address from your AWS EC2 console page]

   
   - Edit the inbound traffic rule to only allow custom TCP port `9000`

Hurray !! Now you can access the `SonarQube Server` on `http://<ec2-instance-public-ip-address>:9000` 
   
![Screenshot (199)](https://user-images.githubusercontent.com/129657174/230658262-0a0c8d3a-312d-4423-84e5-a7a1efa9fc68.png)

Login using username: admin, Passsword: admin and Change the password
   
![Screenshot (200)](https://user-images.githubusercontent.com/129657174/230658269-22ebd5d8-3f97-4a47-8155-57236a95b055.png)

Now at the right top corner click profile icon ->  My Account -> Security, Under Generate Token give a name and click Generate and copy the Token.
   
![Screenshot (201)](https://user-images.githubusercontent.com/129657174/230658498-75e5a06e-512e-4665-bd81-68d7a87d3469.png)
![Screenshot (202)](https://user-images.githubusercontent.com/129657174/230658495-a4ee14e9-df19-4bfa-8cec-0b9ccc3abb76.png)


---

### Install Trivy:

To install Trivy:
     
```
sudo apt-get install wget apt-transport-https gnupg lsb-release
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy        
```





































































































