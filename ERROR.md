# ERROR 
`permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/version": dial unix /var/run/docker.sock: connect: permission denied`


To resolve this issue, you have a few options:

# Add User to Docker Group:
Another approach is to add your user to the docker group, which grants permission to interact with the Docker daemon socket without needing root privileges. However, be cautious when adding users to the docker group, as it can potentially grant unrestricted access to Docker commands. Here's how you can add your user to the group:

`sudo usermod -aG docker damola `
Replace your-username with your actual Linux username.

log out and log back in or restart your system to take effect.

# Change Docker Daemon Socket Permissions:
If you don't want to use sudo or the docker group, you can adjust the permissions of the Docker daemon socket itself. However, this approach may introduce security risks, so use it with caution:

`sudo chmod 666 /var/run/docker.sock `
This command grants read and write permissions to all users, which might not be suitable for production systems due to potential security vulnerabilities.

# ERROR 
`Network observability_default  Error                                                                                                                                0.0s
failed to create network observability_default: Error response from daemon: Failed to Setup IP tables: Unable to enable SKIP DNAT rule:  (iptables failed: iptables --wait -t nat -I DOCKER -i br-6d34818cd0dd -j RETURN: iptables: No chain/target/match by that name.`

To resolve this issue,

`sudo systemctl restart docker` 
