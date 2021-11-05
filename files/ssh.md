# Set up Windows to authenticate to GitHub using ssh

## Prepare Windows
### Install ssh tools
- `Settings > Apps & Features > Optional Features`
- Check that `OpenSSH Client` is installed. If it is not installed, install it by click on `Add a feature`

## Generate Public and Private Keys on Windows
- Open a `Command Prompt` window
- `ssh-keygen -t ed25519 -C "4557674+pngan@users.noreply.github.com"` 
- Press enter through the next three prompts.

If you used a non-default key name then test there is one further step, otherwise skip to the next section
- `cd c:\user\<name>\.ssh`
- In that folder create a text file called `config` (note no extension)
- Put the following content into that file:
```
Host github.com
    HostName github.com
    User <your github account name>
    IdentityFile c:\users\<name>\.ssh\<keyname>.pub
```

## Deposit public key onto github.com website
- On Windows, Print public key onto screen, 
- `type c:\users\phillip\.ssh\id_ed25519.pub`
- Select and copy the output into your clipboard. Careful don't take anything extra.

- Open your browser, and Login into your github account
- Click on your Avatar in the top-right corner of the page
- `Settings > SSH & GPG keys > New SSH key`
- Give a title that indicates your window computer `My Laptop`
- Paste the key into the text field, Click button `Add SSH Key`
- Re-enter GitHub password when prompted on next screen 

## Test Connection to GitHub from Windows
- Test using `ssh -T git@github.com`
- You should receive a message like `Hi ! You've successfully authenticated, but GitHub does not provide shell access.`
