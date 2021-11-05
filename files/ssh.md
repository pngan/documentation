# Set up ssh client on Windows

These steps are needed to connect set up an ssh client on a Windows machine so that you can connect to github.com using ssh, or any other ssh server.

## Prepare Windows
### Install ssh tools
- `Settings > Apps & Features > Optional Features`
- Check that `OpenSSH Client` is installed. If it is not installed, install it by click on `Add a feature`

## Generate Public and Private Keys on Windows
- Open a `Command Prompt` window
- `ssh-keygen -t ed25519 -C "4557674+pngan@users.noreply.github.com"`  # Use your own email address that you want appearing in GitHub against your commits
- Press enter through the next three prompts.
- In the folder `cd c:\user\<name>\.ssh` there should be two new files for the private and public keys, `id_ed25519` and `id_ed25519.pub`.

If you used a non-default key name then test there is one further step, otherwise skip to the next section
- `cd c:\user\<name>\.ssh`
- In that folder create a text file called `config` (note no extension)
- Put the following content into that file.  Note use the private key, *not* the .pub file
```
Host github.com
    HostName github.com
    User <your github account name>
    IdentityFile c:\users\<name>\.ssh\<keyname>
```
# Set up ssh on GitHub.com

These steps are needed to accept ssh connections from client machines in order to carry out git commands against the github repos.

## Deposit public key onto github.com website
- On Windows, Print public key onto screen, 
- `type c:\users\<name>\.ssh\id_ed25519.pub`
- Select and copy the output into your clipboard. Careful don't take anything extra.

- Open your browser, and Login into your github account
- Click on your Avatar in the top-right corner of the page
- `Settings > SSH & GPG keys > New SSH key`
- Give a title that indicates the machine you are connecting from, e.g. `My Laptop`
- Paste the key into the text field, Click button `Add SSH Key`
- Re-enter GitHub password when prompted on next screen 

## Test Connection to GitHub
- On Windows, open a `Command Prompt`
- Test using `ssh -T git@github.com`
- You should receive a message like `Hi ! You've successfully authenticated, but GitHub does not provide shell access.`
