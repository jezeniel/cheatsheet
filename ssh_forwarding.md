### Using the ssh agent
The following would show a similar output if a key
is already added to your agent, and you are good to go.
```shell
$ ssh-add -l
2048 d7:8e:3d:03:9c:4f:f8:9d:04:0f:11:c5:24:e1:2f:3a rsa w/o comment (RSA)
```

The following will show if no agent is running.
```shell
$ ssh-add -l
Could not open a connection to your authentication agent.
```

If no agent is running execute the following.
```shell
$ eval `ssh-agent`
```

Then run the following to add your identity to the agen
```shell
$ ssh-add
The agent has no identities.
```

### Adding identities to the ssh agent
If an agent is running run the following.
```shell
$ ssh-add
```
The above example assumes that you already generated
your ssh-key.

### Connecting to a server with ssh forwarding
```shell
$ ssh -A -i <your_pemfile> user@<remote_addr>
```
The `-A` flag enables forwarding of the authentication agent.

### Testing ssh agent forwarding (remote server)
Once you logged inside your remote server just run
the following to check if ssh forwarding agent is enabled:
```shell
$ echo "$SSH_AUTH_SOCK"
/tmp/ssh-DCIux21917/agent.21917
```
If the variable is not set then the forwarding agent is not working.

### TODO
- Handling ssh-agent across multiple terminal sessions locally

### References
- http://stackoverflow.com/questions/17846529/could-not-open-a-connection-to-your-authentication-agent
- http://www.phase2technology.com/blog/running-an-ssh-agent-with-vagrant/
- https://developer.github.com/guides/using-ssh-agent-forwarding/#troubleshooting-ssh-agent-forwarding

