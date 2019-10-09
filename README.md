
## Ansible

For the roles we use the ones from user `geerlingguy` from github:
- **`docker` role**: https://github.com/geerlingguy/ansible-role-docker.git 
- **`kubernetes` role**: https://github.com/geerlingguy/ansible-role-kubernetes.git 

The custom role (**`deploy` role**) does the following:
- Installs the python dependencies for `k8s` and `docker_image` ansible modules
- Pulls the code from github and build a docker image
- Deploys the pods on kubernetes as a replica set of 2
- deploys a service with the nodeport configuration (uses round-robin load balancing by default)

The app is accessible via http://YOUR_SERVER_IP:30080

To run the playbook, get the code:
```bash
git clone https://github.com/ravenolf/soramitsu-test-ansible --recursive
cd soramitsu-test-ansible
```

Add the private key as `keys/id_ansible_rsa` or remove this line from `ansible.cfg` if you want to use your host private key:
```ini
private_key_file = keys/id_rsa_ansible
```

Change the host on `hosts.ini`.

Run the playbook:
```bash
ansible-playbook main.yml
```

Variables can be changed in `main.yml`

## Sources

- https://github.com/geerlingguy
- https://github.com/geerlingguy/ansible-for-devops