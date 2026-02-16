
sudo su 

apt install g
    apt-get update
    apt-get install -y glusterfs-server avahi-daemon libnss-mdns
    mkdir /localstorage
    gluster pool list


      gluster peer probe node02.local
      gluster peer probe node03.local
      gluster peer probe node04.local
      gluster peer probe node05.local
      gluster peer probe node06.local




      gluster volume create myvolume replica 2 node01.local:/localstorage node02.local:/localstorage node03.local:/localstorage node04.local:/localstorage node05.local:/localstorage node06.local:/localstorage force



      gluster volume start myvolume
      gluster volume set myvolume nfs.disable off

