
Sometimes even you try to connect to a server hosting the repo, you might get permission errors. 
The reasons for this are : 

- You have not setup your public key to recognized by the server. This happens when you have not added your public key to the server. 

- git is not using your private key. This happens when your private key has a non standard name and git does not know which key to use. Usually the private key name is id_rsa, but if you change it to something else, then git does not know which key to use while trying to form the connection with the server. 

One way to make sure that you are able to acutally connect to the server using your key is to use ssh directly and try connecting to the server. 

`ssh -vT git@github.com`

If your private key name is different from the standard name, then specify it using 

`ssh -i ~./path/to/private/key -vT git@github.com`

Possible results : 
	Permission denied. This could happend if you have not used the right private key
	Server accepts the key

If ther server accepts the key then, you need to force git to use the key that you just used with the ssh clinet. 

You can do this by creating a file called config in .ssh
so vi .ssh/config

and within the file specify the following : 
```
Host github.com
	IdentifyFile ~/.ssh/private_key_name
	IdentitiesOnly yes 

```

The host refers to the host name of the server
The IdentityFile refers to the private key file
The IdenitiesOnly make sure that only this key is tried when you want to connect to a server. Without this option id_rsa will be tried first before trying the key that you just specified. 


Now after you have specified the private key to use for a particular host, 
git will be able to use the key that you just specified and the connection should hopefully work.
