# Generate, add and setup new SSH key with Github repositories.
## Generate new SSH key [1]:
1. Run the command below, replace the example email with your github email.
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
2. If this is the first time you create key, press 'Enter' until your <strong>"The key fingerprint is" </strong>command appears.  
Or choose to overwrite the current SSH key. It's all up to you.
## Add new SSH key to ssh-agent:
3. Start the ssh-agent in the background. The typical result will be  <strong>">Agent pid ...". </strong>
```bash
eval "$(ssh-agent -s)"
```
4. Add your SSH private key to the ssh-agent. If terminal shows the command <strong>"Identity added: ..." </strong>, that's correct!
```bash
ssh-add ~/.ssh/id_ed25519
```
## Add the new SSH key to your github account:
5. Open (below command) and copy your SSH key private in <strong>hidden</strong> file named <strong>.ssh/id_ed25519.pub</strong>
```bash
gedit id_ed25519.pub
```
6. In your account <strong>Settings</strong>, choose <strong>SSH and GPG Keys</strong>. Choose <strong>New SSH key</strong>.  
   Label your new SSH key and paste the key into the dialogue. Then <strong>Add SSH key</strong>.
## Check whether your repos is working with HTTP or SSH [2]:
In ../src file of your repos in local machine, run the command
```bash
git remote -v
```
origin	git@github.com:repos/repo.git (fetch) -> SSH  
origin	git@github.com:repos/repo.git (push)

origin	https://github.com:repos/repo.git (fetch) -> HTTP  
origin	https://github.com:repos/repo.git (push)
### If your repos is cloned with HTTP before, you could also switch to SSH by doing steps 1->6

-----------------
### Refenrence
[1].  https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent  
[2].  https://gist.github.com/asksven/b37e8d83eca7f77484be9dd7af2b98e6
