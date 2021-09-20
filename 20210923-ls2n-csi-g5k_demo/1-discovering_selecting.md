# Discovering, visualizing and reserving Grid'5000 resources

At this point, you should now be connected to a site frontend, as indicated by your shell prompt (`<login>@f<site>: ~ %`). This machine will **ONLY** be used to reserve and manipulate resources on this site, using the *OAR software suite* will be the only way to request resources before using them. 

## Discovering and visualizing
There are several ways to learn about the site's resources and their status:

### On SSH connection
The site's MOTD (message of the day) lists all clusters and their features. 

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

Additionally, it gives also the list of current or future downtimes due to maintenance, which is also available from at https://www.grid5000.fr/status/ .

```
** Warning: 1 event in progress
--> #Incident at #Nantes from 2021-09-03@16:30 : air conditioning failure, ecotype nodes unavailable
    https://intranet.grid5000.fr/bugzilla/show_bug.cgi?id=13386
```

### On the wiki
Site pages on the wiki (e.g. [Nantes:Home](https://www.grid5000.fr/w/Nantes:Home)) contain a detailed description of the site's hardware and network.

### On the status page
The page information links to the resource status on each site, with two different visualizations available:
- the current placement and queued jobs status (see [Nantes's current status](https://intranet.grid5000.fr/oar/Nantes/monika.cgi)) **in LIVE**
- the current and planned resources reservations in a Gantt diagram history (see [Nantes's current status](https://intranet.grid5000.fr/oar/Nantes/drawgantt-svg/)) 

## Allocating and accessing resources with OAR

OAR is the **resources and jobs management system** (a.k.a batch manager) used in Grid'5000, just like in traditional HPC centers (commonly with SLURM, PBS, etc.). However, settings and rules of OAR that are configured in Grid'5000 slightly differ from traditional batch manager setups in HPC centers, in order to match the requirements for an experimentation testbed and **not for production use**! 

In Grid'5000 the **smallest unit of resource managed by OAR is the core (cpu core)**, but by default a OAR job reserves a host (physical computer including all its cpus and cores, and possibly gpus). Hence, what OAR calls nodes are hosts (physical machines). In the `oarsub` resource request (`-l` arguments), nodes is an alias for host, so both are equivalent. But prefer using host for consistency with other argumnents and other tools that expose host not nodes. 

### Interactive usage

- To reserve a single host (one node) for one hour, in interactive mode, just do:
  ```bash
  oarsub -I -q besteffort
  #...
  # Connect to OAR job 223392 via the node econome-20.nantes.grid5000.fr
  ```
  As soon as the resource becomes available, you will be directly connected to the reserved resource with an interactive shell, as indicated by the shell prompt, and you can run commands on the node: `lscpu` or on the web with [Gantt diagram / Monika](https://www.grid5000.fr/w/Status#Resources_reservations_.28OAR.29_status).

Reserving only part of a node

To reserve only one CPU core in interactive mode, run:
Terminal.png 	fnancy: 	
oarsub -l core=1 -I

oarsub -l host=1 -I

kaenv3 -l
