# Ansible - Database User Management for MySQL

## Objective

Manage MySQL users in pre-installed or configured databases. This guide dosen't create or perform initial database setup.

## Getting Started


### 1. Clone the repo with the following command:

```bash
git clone https://github.com/alvasebas/ansible-playbooks.git
cd ansible-playbooks/mysql-users
```

### 2. Install MySQL server

```
docker-compose up -d
```

### 3. Get IP address from the installed instances

Get machines list

```
docker ps
```

Get the IPs of the instances

```
docker inspect <container ID>
```

### 4. Connect to MySQL Server (only for review)

From MySQL Client terminal

```bash
mysql -h IP_ADDRESS -u root -p
```

**Note:** Users and passwords are defined in the repository **.yml*** files

## Ansible commands

:warning: Before executing the following commands, the databases listed in the file `vars_mysql.yml` must be created.

1 - To add a user, update password or also add and define the user's permissions and accesses defined in the variables file

```bash
ansible-playbook database_user.yml -e 'state=add'
```

**Tip:** 

- If you wish to alter/remove permissions of a user modify the `grants_xx` variable in the `vars_mysql.yml` file
- If you wish to completely remove the user's access to the database comment out or remove the database from the list in the `vars_mysql.yml` file

2 - To completely remove a user from MySQL engine

```bash
ansible-playbook database_user.yml -e 'state=delete'
```

---

:bulb: You can edit the variables in the `vars_mysql.yml` file: host, user, passwords, databases and roles and run the Ansible commands
