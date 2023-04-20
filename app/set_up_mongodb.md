# Set Up MongoDB

1. Cd into db virtual machine
   
2. Run sudo apt update -y

    ```
    sudo apt update -y
    ```

3. run sudo apt upgrade -y

    ```
    sudo apt upgrade -y
    ```

4. Download

    ```
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927
    ```

5. Verify the key with the command below.

    ```
    echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
    ```

6. Run another update to grab the packages for MongoDB

    ```
    sudo apt update -y
    ```

7. Run another upgrade to download on our machine.

    ```
    sudo apt upgrade -y
    ```

8. Install MongoDB on your virtual machine
   
    ```
    sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20
    ```

9. Start MongoDB

    ```
    sudo systemctl start mongod
    ```

10. Check to see it is running

    ```
    sudo systemctl status mongod
    ```