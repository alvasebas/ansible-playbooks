# Ansible - Database User Management for PostgreSQL

## Objective

Manage PostgreSQL users in pre-installed or configured databases. This guide dosen't create or perform initial database setup.

## Getting Started


### 1. Clone the repo with the following command:

```bash
git clone https://github.com/alvasebas/ansible-playbooks.git
cd ansible-playbooks/psql-users
```

### 2. Install PSQL server & pgAdmin Web client

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

### 4. Connect to Postgres Server (only for review)

From PgAdmin Web

```
URL: http://<IP_ADDRESS:16543>
```

From PSQL Client terminal

```bash
psql postgres -h IP_ADDRESS -U postgres
```

**Note:** Users and passwords are defined in the repository **.yml** files

## Ansible commands

:warning: Before executing the following commands, the databases listed in the file `vars_psql.yml` must be created.

- To add a user, and also add or define the user's permissions and accesses defined in the variables file

```bash
ansible-playbook database_user.yml -e 'state=add'
```

- To revoke a user's permissions and accesses (tables, schemas and databases) defined in the variables file

```bash
ansible-playbook database_user.yml -e 'state=revoke'
```

- To completely remove a user from PSQL engine

```bash
ansible-playbook database_user.yml -e 'state=delete'
```

---

:bulb: You can edit the variables in the `vars_psql.yml` file: host, user, passwords, databases and roles and run the Ansible commands

