## SSH Access

With private benches, comes a whole new power to SSH into your bench and run arbitrary commands. You can SSH into a particular version of your Bench using this feature. Here are the steps required to SSH into a particular bench:

## Add SSH key to your Frappe Cloud account

Visit the **Settings** page in your FC dashboard and scroll to the "SSH Key" section:

![SSH Key Addition Section](https://frappecloud.com/files/Screenshot%202022-07-11%20at%201.09.25%20PM.png)

Clicking on "New SSH Key" button should open up a dialog with an input box. Enter your SSH public key in this input box:

![SSH Key Addition Dialog](https://frappecloud.com/files/ssh_key_dialog.png)

> Note: You can only add 1 SSH key per user

## Generate SSH certificate & SSH

Navigate to the version of the bench you want gain SSH access to. For this, you can go the bench dashboard and open the **Versions** tab. If you have correctly added your SSH key, SSH Access option should be visible in Actions on your bench version page:

![SSH Access Option](https://frappecloud.com/files/CleanShot%202022-11-10%20at%2012.01.51@2x.png)

Clicking on the button will open up a dialog:

![SSH Access Cert Generation Dialog](https://frappecloud.com/files/ssh_access_dialog_cert.png)

Now, click the **Generate SSH Certificate** button. This will generate an SSH certificate for you, valid for 6 hours, which you can then use to SSH into your bench:

> Note: These commands only work on Linux and macOS machines.

![SSH Access Certificate](https://frappecloud.com/files/ssh_access_dialog.png)

> Note: Everytime you need SSH access to a particular version of a bench, you will need to generate a new SSH certificate. This certificate is valid for 6 hour. After that, you will have to regenerate the certificate from the bench dashboard.

Follow the instructions shown in the dialog (copy-paste the commands into your terminal). After you have successfully added the certificate locally, you should be able to run the given `ssh` command to gain access to your bench:

![SSH Terminal](https://frappecloud.com/files/ssh_terminal.png)

That's it! You can now run any commands you like `bench restart`, `bench build` and more. If you face any issue in getting SSH access, please feel free to raise a support ticket and we will be happy to help!

## FAQ

### Access denied on SSH: Private key contents do not match public

If you see the following error on your local machine.

```
identity_sign: private key /home/user/.ssh/id_rsa contents do not match public
```

This is probably because the key you've added on Frappe Cloud does not match the one you're using for ssh on your local.

The fingerprint you see in your dashboard

![fingerprint dashboard](https://frappecloud.com/files/fingerprint-dashboard.png)

should match the output of `ssh-add -l` (as ran on a linux environment)

If they don't match, please review your local setup. [Github's ssh docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) are pretty good.

### SSH from powershell on windows does not work

Please read our workaround in this [issue](https://github.com/frappe/press/issues/798) for workaround.

### Cannot copy files over SSH (SCP)

Our ssh sessions are provided over a proxy connection and thus scp and other tools that depend on it will not work.

### VS Code over ssh does not work

Same reason as above. VS Code uses scp to make this happen.