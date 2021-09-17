# SSH configuration
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
ssh g5k


oarsub -l host=1 -I