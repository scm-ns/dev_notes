
# Using SSH with Github 

### Use Cases 
* When you try cloning something using the git@org.com:user_name/repo , git will utry to use ssh keys to authenticate with the servers. So need to provide an private key with the corresponding public key adding to github. 

* When you want to interact with a code repo, and push pull changes. 

To override this when you are just cloning use the http url for the repo. 

### Adding the keys to github
1. Create the Keys
`ssh-keygen -t rsa -b 4096 -C "email id"`

It will ask you where you want to save the key. You can specify the keyname here. 

A passphrase is like a password that you can use to secure the key, so that anyione with access to your computer cannot use your key willy nilly. 

2. Adding keys to the ssh-agent
The ssh-agent is a background process which keeps running and handles the add communications. It can also store the passphare used to unencrypt the keys in memory so that the user does not have to keep typing it again and again. 

`ssh-add ~/.ssh/id_rsa`
> You add the private key to the ssh agent. If there is an associated passphrase with the key, then it can be added to the ssh-agent using the -K param 

3. Add the key to your github account. 
Copy the public key that you generated in step one to your github account online, so that now github's server can verify that the communications are coming from you. 

Since the key is pretty large, you can copy it to the clipboard buffer by using this command : 
`pbopy < ~/.ssh/id_rsa.pub`

Note that you are adding the public key and not the private key. 

Now add this to github using Settings -> SSH and GPG Keys -> New SSH key or Add SSH key -> Paste the key -> Add SSH Key 



