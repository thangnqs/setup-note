# Note: Setup a new SSH key for Linux

### 1. Setup SSH key
If you have ssh key in `~/.ssh/id_rsa` please ignore this step.
 
 - [ ] Create new ssh key `ssh-keygen -t rsa 4096 -C "username@example.com"`
 
 - [ ] This will prompt you for a file location. Just accept the default  `(/Users/yourname/.ssh/id_rsa):`
 
### 2. Copy and paste SSH key to Github 
Follow by choose icon Profile -> Settings -> SSH and GPG keys -> New SSH key

Type this command to start and verify your **ssh-agent** is running properly `eval $(ssh-agent) -s`

 - [ ] For Mac Users `ssh-add -K ~/.ssh/id_rsa`
 - [ ] For Linux / Windows `ssh-add ~/.ssh/id_rsa`
You should see a success message like this: `Identity added: ..~/.ssh/id_rsa (username@example.com)`

### 3. Test connect to GitHub
Try a test connection  `ssh -T git@github.com` 
The message show is `Hi yourname! You've successfully authenticated, but GitHub does not provide shell access.`

Done!

### 4. Fix authencation 
If you see the message like `remote_: _Support_ for _password authentication_ was _removed_ on _August 13, 2021_. _Please use_ a _personal access token instead`

Easy to fix it by step by step
####  Install new Github CLI
`curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg |  sudo gpg --dearmor -o /usr/share/keyrings/githubcli-archive-keyring.gpg`

`echo  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main"  |  sudo  tee /etc/apt/sources.list.d/github-cli.list > /dev/null`

`sudo  apt update`

`sudo  apt  install gh`

####  Login
`gh auth login` and follow step by step to authencation to server Github


