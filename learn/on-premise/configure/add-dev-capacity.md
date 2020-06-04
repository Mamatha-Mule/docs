---
title: "WME Add Developer Capacity"
id: ""
sidebar_label: "Add Developer Capacity"
---
---

Once you have Launched Instances, Initialized, Set up and configured the WME, it is time for the developers to log in and build apps. For this, you need to add developer and deployment infrastructure capacity by adding instances.
If not setup External Instance ,[launch Instance with the required prerequisites](/learn/on-premise/prerequisites)

Every User is allocated with one container. The infrastructure adding here will be used for this allocation.

To add instances to Platform, you need to provide ssh credentials.
Ssh credentials of the Instance either should have root privliges or provide required permissions as below.

### Extra configurations on External Instances

#### The ssh user has privileges(root/sudo)

- No need to do any configurations. Platform will do it automatically.

#### The ssh user don't have privileges(non sudo users)

- If the user given to the Platform don't have privileged access, then provide below permission for the user given on External Instance.
- Have to execute these commands from privileged user.
  - Add user to docker group.
  - Make the user as owner for docker systemd process.
  - data directory should be owned by the user.
  - Give permission to manage docker.service, systemctl daemon reload, iptable.

    ```bash
        usermod -aG <user> docker
        chown -R <user>:<user> /usr/lib/systemd/system (for RHEL)
         chown -R <user>:<user> /etc/systemd/system/docker.service.d   (for ubuntu)
        chown -R <user>:<user> /data
        echo "%${user} ALL=NOPASSWD: /bin/systemctl restart docker.service,/bin/systemctl daemon-reload,/usr/sbin/iptables" >> /etc/sudoers.d/<sudoers-file-name>
        ```

[![wme instance](/learn/assets/wme-setup/configuring-wme/WME_instance.png)](/learn/assets/wme-setup/configuring-wme/WME_instance.png)

## Add Capacity to Developer Workspace

- Select Developer Workspace section and select Add Capacity option to add Instance to capacity.
- Provide Instance details and authentication details to connect to the Instance,if you want you can test the connection and details of Instance by selecting the test option.

[![workspace capacity](/learn/assets/wme-setup/configuring-wme/workspace-capacity.jpg)](/learn/assets/wme-setup/configuring-wme/workspace-capacity.jpg)

- Wait for few moments for configure and get started.