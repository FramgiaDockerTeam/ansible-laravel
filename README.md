### Deploy Laravel Using Ansible

#### Copy ssh private key for ssh into server:

```
cp {your_server_ssh_key} ssh_key/id_rsa
```

#### Copy deploy key of github:

```
cp {your_github_deploy_key} scm_key/id_rsa
```

#### Setting source code directory and source version control:

`group_vars/all.yml`

#### Edit web server IP, SSH port:

`production.yml` or `staging.yml`

#### Run deploy command:

```
ansible-playbook -i production  main.yml
```
or

```
ansible-playbook -i staging main.yml
```

#### Create webserver with docker

```
docker run --name server-production \
    -p 8023:22 -p 8080:80 -p 8443:443 \
    -e AUTHORIZED_KEYS="ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQC4ix8DF/+gOQcU3Z3X80ov2XFQeAjqWN4iZv1+F16/Csc6oAw9/5vBOXg6hMefFtmU5a7Nj2H45erBSAeddpI8unqJ1duvUZsNdNi6PfxiwNzarnXdrJ3F/I4asWeNyuVn/XBz7GiUrHRTj+f0eZvfplhwXEzUZTMlnCvijGWbdgRKCyXueXjF9UznWDAP5PoaY1/K8OuTJC5bTwDthR8uzO/g8WJHmCR8SoVUGXtK+UhbAb5l1bhUq6f741/bzkRa5MMCQ+vlWy0V/1Dgxk4hTlyzaGpdFml04qDYUr8dtgwBGFoYF51CTMYodfVwsG4mzqfJPnEU9Shk/slQA7hrm7W/Ac3FUMMAQmcfMERqJeAkbUBmxVZC54WUxh2AHkOoHWfc287n8mTuUnJEeC1kh6T42tMZiU35c61o8ydlXqvSDdq0XDpLki9P1cOY+Ppyw6m1rkIuJHzyGut5AywCJoq5oMGZ/Lj0JPT/g+wjXV7J/gD/tM0xPJEMK/d36vcVWdf8pUK4DASKT7Uj9sUK0WeJDXwWOvnq6X9rJVmOhlr/yQmrB+HAR7s3edHW9m6E3nyhZOTeyZEct+uJmLRvLqqjpD7bOxK5OSbKw6OnHBCi4QzkZO6bOIBmc9EcjV3/aWj57njrjEuk4i2V5Y0Yxyjj3o4si9Kf4E9g1e+9lQ== docker@framgia.com" \
    -e ROOT_PASSWORD="123456Aa@" \
    -d euclid1990/ubuntu-server
```