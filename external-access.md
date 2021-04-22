# Externe Zugriff 

## Testing 

```
# Where .104 is the server you want to connect to 
# Variante 1 
mysqladmin ping -h 192.168.56.104
echo $? 
-> 0 // it is possible to reach mysql - server 

# Variante 2
mysqladmin ping -h 192.168.56.104
echo $?
-> 1 // i cannot reach mysql-server  -> port might close / firewall ? 

```

## Checks on MariaDB  (Theory) 

  * Is MariaDB - Server running ? 
  * Is 3306 port open (exposed to the outside)
  * Is firewall open for port 3306  
  * Is there a valid user, who connect) 

## Checks on MariaDB (Practical) 

```
# Step 1: Running 
systemctl status mariadb 
# Step 2: Port open ?
lsof -i # does it listen to all interfaces. -> * 
        # or an externel interface 
# Step 3: Firewall open -> see next block 
# Step 4: User who can connet ? 
```

## Checks on Firewall. 

```
# Is firwall running and enabled 
systemctl status firewalld 
firewall-cmd --state 

# Is interface setup for usage of firewalld 
firewall-cmd --get-active-zones 

# Is service "mysql" in zones 
firewall-cmd --list-all-zones | less # is it within public - zone -> mysql

# To enable it, if not set 
firewall-cmd --add-service=mysql --zone=public --permanent # writes to filesystem config 
firewall-cmd --reload # rereads settings from filesystem 
```
