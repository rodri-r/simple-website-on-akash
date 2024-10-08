# simple-website-on-akash
A simple server for a website on Akash

---

## Deploy

- Go to https://console.akash.network
- Connect your wallet (You will need some AKT tokens to deploy)
- On the left side bar click on Deployments and then click on the Deploy button.
- Click on "Build your Template" and then on the YAML tab.
- Delete everything in this page and copy/paste the deploy.yaml file that you can find in this repo. (You may edit the resources as you like, ex: CPUs, RAM and Storage)
- Click on the "Create Deployment" button and accept the transaction with your wallet.
- After the transaction is successful, you will see a list of Akash providers who can host your deployment or node.
- Select the one that you like the most and confirm the transaction with your wallet.
- Once your transaction goes through, you will see the events screen and how your deployment is being deployed.
- After a short time, your Ubuntu instance will now be running on Akash Network.
- To log in via ssh, you will need to find your provider's IP and the 22 port that they provided for you.
- You can find your Akash provider's IP, by going to https://dnschecker.org/ and entering your provider's url.
- You can find the 22 port provided for you in the leases tab in Akash Console, in your recently created deployment section. 

## Configuring your deployment (Ubuntu instance)

- After logging in to your new server, run:

``` 
 apt update
 apt upgrade 
```

- Remove Apache

```
apt remove --autoremove apache2 apache2-utils  
```

- Confirm that it has been removed

```
rm -r /etc/apache2
rm -r /var/log/apache2
```

- Install Nginx

``` 
 apt install nginx
```

- Check Nginx Status

``` 
 service nginx status
```

- Enable Nginx

``` 
 service nginx start
```

## Build your website

Your Nginx server should now be working. You can now go to /var/www/html and start building your site.  Simply delete the file index.nginx-debian.html and create an index.html file or whatever website you feel like.

You can get your URL from Akash Console. Click on your deployment and on the leases tab, you will see URI(s): copy that and paste it in your browser. 

## Extras

- Add a domain and https to your website.

Add the following in the expose section of the [deploy.yaml](deploy.yaml) file (it must go below as: 80):

``` 
accept:
          - example.com
```
1. Go to dnschecker.org and get your provider's ip, by inserting your provider domain, which can be found in Akash Console, under the leases tab. 
2. Get a Cloudflare account.
3. Go to your Domain provider and point your domain's dns to your Cloudfare DNS.
4. Go to Cloudflare and point your DNS to your provider's ip

- The front page of a website has been included in this repo. 

