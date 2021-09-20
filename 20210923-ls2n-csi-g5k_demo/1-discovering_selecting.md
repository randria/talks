# Request your account creation and activate your access
- To get an account, you must justify of a use of Grid'5000 for its intended purposes by accepting the [Grid'5000 usage policy](https://www.grid5000.fr/w/Grid5000:UsagePolicy) 
- Read and follow steps on [how to get your first account on g5k](https://www.grid5000.fr/w/Grid5000:Get_an_account)
- After acceptation of your submission by the G5K committee, you will receive an automatic email from <notifications@api.grid5000.fr> with a full detail of instructions on how to connect and begin using G5K platform with your credentials (`user_login` and `password`)
  - You will be affected 
- You can connect directly to your ssh session on the g5k frontal node
  ```bash
  $ ssh <user_login>@access.grid5000.fr
  ```
## Banner information on connection

```bash
Welcome to Grid'5000

** Useful links:
 - users home: https://www.grid5000.fr/w/Users_Home
 - usage policy: https://www.grid5000.fr/w/Grid5000:UsagePolicy
 - account management (password change): https://api.grid5000.fr/ui/account
 - support: https://www.grid5000.fr/w/Support

** Connect to a site:
 - to connect to any of the Grid'5000 sites:
     grenoble lille luxembourg lyon nancy nantes rennes sophia
   (from here) $ ssh <site>
 - mind configuring the ssh aliases (proxycommand) on your workstation to
   connect directly to the Grid'5000 sites from the outside:
   (from outside) $ ssh <site>.g5k
 - or use the Grid'5000 VPN: https://www.grid5000.fr/w/VPN

** Data on access.grid5000.fr (aka access-{north,south}.grid5000.fr):
 - home directories on access machines are not synchronized, access machines
   should not be used to store data.
 - to copy data from/to a site, use the site NFS mount point linked in the home:
   (from outside) $ scp files login@access.grid5000.fr:<site>/
 - or copy directly from/to the site using the ssh alias (proxycommand):
   (from outside) $ scp files login@<site>.g5k:

See https://www.grid5000.fr/w/Getting_Started for more information.
```

# SSH

## SSH Key Pair

If you do not have one, you should create locally on your machine with the following command:
```bash
$ ssh-keygen
$ cat ~/.ssh/id_rsa.pub
```

## SSH Config File
Append these lines in your `~/.ssh/config` SSH file configuration by replacing `<g5k_userid>` with the real value and `<ssh_private_key>` the name of your SSH private key associated to the public key given when you requested a [g5k account creation](https://www.grid5000.fr/w/Grid5000:Get_an_account).
```bash
# .ssh/config
Host g5k
    User <g5k_userid>
    Hostname access.grid5000.fr
    IdentityFile ~/.ssh/<ssh_private_key>
    ForwardAgent no

Host *.g5k
    User <g5k_userid>
    IdentityFile ~/.ssh/<ssh_private_key>
    ProxyCommand ssh g5k -W "$(basename %h .g5k):%p"
    ForwardAgent no
```

# Connect to the g5k frontal

- if you connect with the SSH configuration file set, you can type
- if you do not know the site you want to connect on, just type:
```bash
ssh g5k
```

otherwise, 

oarsub -l host=1 -I

kaenv3 -l
