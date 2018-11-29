# pulumi-handson
If you are here, you belive that you can code you infrastructure using your favorite programming language.
During this journey, 

We will convert our RSS to MP3 
So let's get started :blush:

## First Step : Prepare the field

For this hand-on you need to install node version 8.9
you can use node version manager to handle multiple node version

the installation instruction are available here: https://github.com/creationix/nvm

To check you install: `nvm --version`

Now you can install node 8.9.4 using : `nvm i 8.9.4`

To check you node default version: `node --version`

You can use `nvm use 8.9.4` to switch node version

To Install pulumi you can copy and paste this command in your terminal : `curl -fsSL https://get.pulumi.com | sh`

To check you pulumi version: `pulumi version`

## Second Step : Prepare the weapon

Now you can checkout the projet and start coding :cloud:

- In th main route of the project you have to run `npm i` to install the pulumi depencencies
- you need also to define your Pulumi stack  `pulumi stack init` : you can call your stack `stack
- you need to set francfort as aws region `pulumi config set aws:region eu-central-1`

## Third Step : Fight

###
