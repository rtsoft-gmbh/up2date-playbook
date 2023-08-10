# UP2DATE-PLAYBOOK SIMPLE CLIENT C++

## QUICK START

### INSTALL AND CONFIGURE ANSIBLE

> Install Ansible
```shell   
apt-get update
apt-get install ansible
```

> Configure Ansible

insert at the beginning of `/etc/ansible/hosts` the following line:

`127.0.0.1 ansible_connection=local`

the rest must be commented

### BUILD AND RUN UP2DATE-PLAYBOOK CLIENT

> Get up2date-cpp sources
```shell   
git clone -–recurse-submodules https://github.com/rtsoft-gmbh/up2date-cpp.git
```

> Inject up2date-playbook sources
```shell   
cd up2date-cpp/example
git clone https://github.com/rtsoft-gmbh/up2date-playbook.git
```

> Edit up2date-cpp/example/CMakeLists.txt

into the section `if (BUILD_DPS)` insert the line:

`add_subdirectory(up2date-playbook)`


> Install dependencies
```shell   
sudo apt-get -y install ca-certificates make cmake git curl zip unzip tar pkg-config build-essential libssl-dev
```

> Build
```shell   
cd ..
mkdir build
cd build
cmake -DBUILD_EXAMPLES=ON ..
make
```

> Start up2date-playbook client
```shell   
sudo CERT_PATH=<path-to-certificate> \
PROVISIONING_ENDPOINT=https://dps.dev.ritms.online/provisioning \
X_APIG_TOKEN=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx \
./example/up2date_playbook/up2date_playbook
```
