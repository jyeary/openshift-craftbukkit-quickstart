openshift-craftbukkit-quickstart
================================

A quickstart Minecraft (Craftbukkit) server that will automatically download latest craftbukkit development build 
and start it.

Create the Openshift DIY Application
===

1. Create a DIY application using this git repo as source code:

   ```bash
   $ rhc app-create craftbukkit diy --from-code=git://github.com/golyalpha/openshift-craftbukkit-quickstart.git
   ```

2. Create a port-forward from your local machine to your remote server:


   ```bash
   $ rhc port-forward craftbukkit
   Checking available ports ... done
   Forwarding ports ...

   To connect to a service running on OpenShift, use the Local address

   Service Local                OpenShift
   ------- --------------- ---- ---------
   java    127.0.0.1:25565  =>  *:25565

   Press CTRL-C to terminate port forwarding
   ```
3. The server will be accessible from `minecraft` using **Direct Connect** on 127.0.0.1:25565  


Setting Administrative Player (Op)
---

You will need at least one player to act as the administrator. In order to do that, you must add them through server console.

1. SSH to the application:

   ```bash 
   $ rhc ssh
   ```
2. Stop gear, go to openshift data dir and run server:
   
   ```bash
   $ gear stop
   $ cd $OPENSHIFT_DATA_DIR
   $ java -jar CraftBukkit.jar
   ```
3. In server console op someone.
   
   ```bash
   > op <player>
   ```
4. Stop server and start the gear.
   
   ```bash
   > stop
   $ gear start
   Starting gear...
   Starting DIY cartridge
   + cd /var/lib/openshift/52bc4398e0b8cded36000038/app-root/data/
   + nohup java -jar craftbukkit-dev.jar -h 127.8.212.1 --noconsole
   ```

Reference
---
The OpenShift `diy` cartridge documentation can be found at:

https://github.com/openshift/origin-server/tree/master/cartridges/openshift-origin-cartridge-diy/README.md
