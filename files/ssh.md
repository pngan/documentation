# Set up Windows to connect to GitHub

## Prepare Windows
### Install ssh tools
- `Settings > Apps & Features > Optional Features`
- Check that `OpenSSH Client` is installed. If it is not installed, install it by click on `Add a feature`

## Generate Public and Private Keys on Windows
- Open a `Command Prompt` window
- `ssh-keygen -C "youremailaddressthatappearsingithub@example.com"` 
- This should prompt you for a file name. You can accept the default `id_rsa` or if you have a one already with that name, you can choose a different name e.g. `c:\users\phillip\.ssh\id_rsa_github`
- Press enter through the next two prompts.
- Print public key onto screen, and select and copy the output into your clipboard. Careful don't take anything extra.
- `type c:\users\phillip\.ssh\id_rsa_github.pub`

## Deposit public key onto github.com website
- Open your browser, and Login into your github account
- Click on your Avatar in the top-right corner of the page
- `Settings > SSH & GPG keys > New SSH key`
- Give a title that indicates your window computer `My Laptop`
- Paste the key into the text field, Click button `Add SSH Key`
- Re-enter GitHub password when prompted on next screen 

## Test Connection to GitHub from Windows
- If you used the default key name `id_rsa` then test using `ssh -T git@github.com`
- If you used a non-default key name then test using  `ssh -i <keyname>.pub -T git@github.com`
