---
title: "Deploy Your Application and Secure Your Domains for Free with Let's Encrypt on Docker-Compose and Nginx"
seoTitle: "Secure Domains & Apps for Free: Let's Encrypt, Docker, Nginx Guide"
datePublished: Tue Apr 18 2023 17:45:39 GMT+0000 (Coordinated Universal Time)
cuid: clgmk2qfm01bj3cnv81d51pv2
slug: deploy-your-application-and-secure-your-domains-for-free-with-lets-encrypt-on-docker-compose-and-nginx
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681841021333/17c7696a-143c-4c86-abe2-fb159402041d.jpeg
tags: automation, devops, ssl-certificate, docker-compose, rishikeshops

---

# Why You Need to Secure Your Website with HTTPS and SSL

Until recently, most website owners have not had to worry about taking special measures to secure their web pages unless they were conducting eCommerce transactions or collecting sensitive information such as medical or banking data. But now all that is changing.

Google now officially recommends securing websites with HTTPS, which means that not only will this be important for organizations that want their websites to perform well in search, but more and more visitors will come to expect it.

In short, website security is no longer something for only certain types of websites to worry about; it's a best practice for all businesses and organizations that want to optimize their search engine performance, establish credibility with visitors, and maintain a professional web presence.

# **What is an SSL certificate? And How it benefits your website?**

An SSL certificate (Secure Sockets Layer certificate) is a digital certificate that is issued by a certificate authority. It is used to confirm the identity of a website (which is usually a company or a server) and the validity of the data sent (usually data being passed by an end user) to the website.

Digital certificates are used to protect Internet communications. They provide a way for a web server to validate its identity to the web browser, ensuring that the information being transferred is safe. This certificate is used to validate the website's identity so that the computer user may be certain that the website is who they think it is.

If SSL does not encrypt your website with a certificate, any computer between the user and the server can view the user’s payment card details and other critical information. By creating a secure connection and keeping client information secure, this safety feature for your website builds a foundation of consumer confidence.

It's not hard to understand why SSL has historically been considered a best practice for any website that is processing transactions with sensitive data such as social security numbers, credit card numbers, personal health records, or login credentials. Now, SSL is becoming a best practice standard for all websites, including those that do not necessarily process sensitive data.

# Google Wants You to Build a Secure Website

Back in 2014, Google introduced the idea of "[HTTPS everywhere](https://youtu.be/cBhZ6S0PFCY)" and also indicated that websites using SSL would receive a small search benefit from [https as a ranking signal](https://webmasters.googleblog.com/2014/08/https-as-ranking-signal.html). You would think that these public declarations would have been enough to get everyone using HTTPS as a new standard, but that never really happened on a wide scale outside of commerce sites that were already using HTTPS anyhow. But in 2016, Google changed the game when they updated their Chrome browser to explicitly identify sites that do not use HTTPS as "unsecured."

## Browsers Now Shame Unsecured Websites

You may have noticed that most common desktop browsers such as Internet Explorer, Chrome, Firefox, and even mobile browsers such as Chrome on Android and Safari on iOS prominently show lock icons to indicate when a site is secure via HTTPS. Chrome in particular goes a step further by labeling standard HTTP sites as "unsecured."

![SSL1](https://cdn-eiojb.nitrocdn.com/OiYTPrgNGwxwFrWMfKDIlzsMHJOFgwkZ/assets/images/optimized/rev-92e8be4/wp-content/uploads/2019/08/SSL1.png align="left")

Because of these browser cues, website users are increasingly becoming conditioned to identify when a site is secure vs. unsecured, and with that comes an implied sense of credibility and professionalism in favor of secure sites. This is especially important for business websites that have a brand image that is reflected in their web presence.

# Is Your Site Secure?

Confirming whether your site is secured with HTTPS is a two-step process: (a) Make sure that you have an SSL certificate properly installed on your server, and (b) confirm that your pages are being forced to HTTPS versions of the URLs (i.e., that there are no unsecured versions of the page using HTTP).

## **Let's Test Your Site**

Fortunately, it's pretty easy to determine whether or not your site has SSL properly installed. Simply type "https://" in your address bar, followed by your domain name (e.g., [https://your-doman.com](https://your-doman.com)). If you see a lock icon in your address bar, it means that you have SSL installed on your server, if you see an error message, it means that you do not have SSL installed or that it is not configured correctly. If you're unsure or if you want to run a more thorough test, you can also use this [SSL Server Test](https://www.ssllabs.com/ssltest/) to get additional information about your SSL configuration.

# Let's protect your domain and application.

So now I'll teach you how to configure SSL on Docker-Compose for your application using Nginx and Let's Encrypt. Docker-Compose is a tool that allows you to define and run multi-container Docker applications. It enables you to describe the services that comprise your application, as well as their dependencies, and then run them in a separate environment.

If you're looking for a simple way to secure your domains with SSL certificates in a Docker-compose setup with Nginx, you've come to the right place. In this comprehensive guide, we'll walk you through the steps needed to use Let's Encrypt to secure your domains and ensure certificate renewal with a simple shell script.

Before we begin, please ensure that you have the following prerequisites:

* A registered domain name is pointed to your server's IP address.
    
* Docker and Docker-Compose are installed on your server.
    
* Basic knowledge of Docker and Docker-Compose.
    

To get started, you'll need to clone the GitHub repository located at [**https://github.com/RishikeshOps/auto-ssl-certificate.git**](https://github.com/RishikeshOps/auto-ssl-certificate.git). Once you've cloned the repository, you'll need to modify the configuration to suit your requirements.

In the [`init.sh`](http://init.sh) file, you'll need to add your domain name(s) and email address(es). Next, in the `nginx.conf` file, you'll need to replace all occurrences of "[example.me](http://example.me)" with your primary domain name (the first one you added to [`init.sh`](http://init.sh)). Don't forget to change the port in the server block if your application is running on a different port.

Finally, add your Docker image to the`docker-compose.yml` file, which you want to serve on the domain using a reverse proxy.

Once you've made all the required changes, you can run the init script using the following command:

```bash
sudo bash init.sh
```

This will automatically fetch and ensure the renewal of a Let's Encrypt certificate for your domains, and your application will be served securely over HTTPS.

# conclusion

In conclusion, this comprehensive guide provides an easy-to-follow solution for securing your domains with Let's Encrypt certificates in a Docker-compose setup with Nginx. By following the steps outlined in this guide, you can ensure that your domains are secure and your SSL certificates are renewed automatically, giving you peace of mind that your data is protected.

---

The source code for everything is hosted here: [https://github.com/RishikeshOps/auto-ssl-certificate](https://github.com/RishikeshOps/auto-ssl-certificate)

If you'd like to learn more about the DevOps projects I've built, please visit my [**Blog page**](https://blog.rushikesh.me).

---

**Thanks for reading to the end; I hope you gained some knowledge. ❤️🙌**

**\- Rushikesh Mashidkar💕**