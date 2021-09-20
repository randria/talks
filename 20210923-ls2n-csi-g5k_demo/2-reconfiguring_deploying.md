# Deploy your nodes, get root access and create your own experimental environment

Most Grid'5000 users use resources in a different, much more powerful way: they use Kadeploy to re-install the nodes with their software environment for the duration of their experiment, using Grid'5000 as a Hardware-as-a-Service Cloud. 
This enables them to use a different Debian version, another Linux distribution, or even Windows, and get root access to install the software stack they need. 

## Deploying nodes with Kadeploy

### Reserve one node 
The deployment job type is required to allow deployment with *Kadeploy*

```bash
site% oarsub -I -l host=1,walltime=1:45 -t deploy
```
