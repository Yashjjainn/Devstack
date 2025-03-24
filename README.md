# Devstack
## to deploy openstack, first make a VM on your local machine or cloud and be sure your user should have administrative powers.
---
### step 1. update system and install dependencies
```
sudo apt update && sudo apt upgrade -y
sudo apt install -y git python3-dev python3-pip net-tools
```

### step 2. clone devstack repo
```
git clone https://opendev.org/openstack/devstack.git
cd devstack
```


### step 3. create devstack configuration file local.conf
```
nano local.conf
```
- paste the below
  ```
  [[local|localrc]]
  ADMIN_PASSWORD=secret
  DATABASE_PASSWORD=$ADMIN_PASSWORD
  RABBIT_PASSWORD=$ADMIN_PASSWORD
  SERVICE_PASSWORD=$ADMIN_PASSWORD
  ```

### step 4. install openstack with devstack
- run ./stack.sh (installation command, it will take 20 to 30 mins)
  ```
  ./stack.sh
  ```
  - if successful you will sea
    ![Screenshot from 2025-03-21 12-53-07](https://github.com/user-attachments/assets/26da0f95-1a9e-406a-b551-d19eea527563)


### step 5. access openstack 
- open horizon on browser
  ```
  http://your-public-ip/dashboard
  ```
  ![Screenshot from 2025-03-17 12-07-44](https://github.com/user-attachments/assets/56da2da9-b9cc-418f-a199-83be030f9931)

  ![Screenshot from 2025-03-17 12-09-45](https://github.com/user-attachments/assets/27f787b0-66a2-4701-ba62-2f86c4233659)

### step 6. verify openstack is running
- run :
  ```
  source openrc admin admin
  openstack service list
  ```
- if running :
  ![Pasted image](https://github.com/user-attachments/assets/079f6a00-a3c9-4fdd-bed4-71c2f207a2e2)


### step 7. Check if every service is running 
- keystone
  ```
  openstack token issue
  ```
  ![Pasted image (2)](https://github.com/user-attachments/assets/a132ca1b-5c26-486e-ae6f-1f8a4db1bfa9)

  
- Neutron
  ```
  openstack network agent list
  ```
  ![Pasted image (3)](https://github.com/user-attachments/assets/c56455a2-ce03-4d19-80c2-01752ee15791)

- nova
  ```
  openstack compute service list
  ```
  ![Pasted image (4)](https://github.com/user-attachments/assets/d10473c7-c1b9-4103-b428-8430916140da)

- glance
  ```
  openstack image list
  ```
  ![Pasted image (5)](https://github.com/user-attachments/assets/06614d76-ee99-4c00-8413-e2cbb14ce163)
  
- cinder
  ```
  openstack volume service list
  ```
  ![Pasted image (6)](https://github.com/user-attachments/assets/c04c816f-f3bd-48a1-befd-3512592e4184)
  

### if any service is down run 
```
sudo systemctl restart devstack@service-name
```

### step 8. run an instance
![Pasted image (7)](https://github.com/user-attachments/assets/b401450d-2800-41d3-9ac1-db960ea07e9b)
![Pasted image (8)](https://github.com/user-attachments/assets/12c0e232-fb33-4831-a694-dbd67eb8d6ad)
![Pasted image (9)](https://github.com/user-attachments/assets/48d932ae-f61e-460e-8d9f-7d2fe95dc395)

