# Discovering, visualizing and reserving Grid'5000 resources

## Official Banner information on SSH connection

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


oarsub -l host=1 -I

kaenv3 -l
