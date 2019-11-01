# ansible-playbook for install NFS server and client
This is a ansible-playbook for clean install NFS in both sides server and client **without internet access**. Also configure mount point and set it in `/etc/fstab`.
Please note that, this playbook written for **CentOS7**.
****
## Install NFS Server
Firstly, you should modifiy follow changes in `roles/NFS/vars/main.yml`:

```yml
ansible_workspace: <path> 		# define ansible workspace

NFS_SERVER: true 	 		# for install NFS server

share_directory_path_server: <path> 	# define a directory on NFS server

share_directory_path_client: <path>	# define a directoy on NFS client (define it when you want install NFS client)

exports_mount_IP: "y.y.y.y" 		# or NFS_CLIENT_IP

NFS_SERVER_IP: "x.x.x.x"		# define NFS server IP
```

Ultimately, run ansible-playbook for install NFS Server:

```bash
ansible-playbook -i inventory/hostsfile NFS.yml
```

## Install NFS Client

According to the previous description regarding install NFS server, now if you want install NFS client please set `false` for `NFS_SERVER` in `roles/NFS/vars/main.yml` and run previous command again:

```yml
...

NFS_SERVER: false                        # for install NFS client

...
```

