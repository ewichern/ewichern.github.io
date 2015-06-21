---
layout: post
title: Linux, VPNs, and non-standard client software...
date: '2015-03-25 01:48:26'
---

I regularly use a VPN, for a number of different reasons, but [my VPN service](https://www.privateinternetaccess.com/)  doesn't have what you would call "first class" support for Linux. They have a Linux client that has been in [beta](https://en.wikipedia.org/wiki/Software_release_life_cycle#Beta) for at least a year and a half, and while it may have improved some, it also has some serious unresolved issues that have prevented it from ever working for me. 

I'm not sure exactly what the problem is. I do know that their Linux client does not play nicely with [encrypted home directories](https://help.ubuntu.com/10.04/serverguide/ecryptfs.html), so that could be my hurdle. I never tried the slapped-together workarounds... But it could also be any number of other things. The software installs via a shell script, so it can't rely on the distribution's [package manager](http://manpages.ubuntu.com/manpages/utopic/man8/apt-get.8.html) to resolve dependencies or handle updates. I assume that PrivateInternetAccess has invested the effort to put together this client at all because they're aiming for "ease of use" and wanted a GUI that matched their windows/OSX client. 

If only it worked. For awhile I just didn't bother. I would tether through my phone when I was booted into Linux to avoid having to figure out this stupid VPN networking thing. 

And then it dawned on me (I'll admit, it took months) that [PIA's iOS solution](https://www.privateinternetaccess.com/pages/client-support/#ios_openvpn) was basically to point their users to the [official OpenVPN iOS client](https://itunes.apple.com/us/app/openvpn-connect/id590379981?mt=8) and provide the relevant configuration and certificate files to get up and running. I already had those files in [Dropbox](https://db.tt/hfGttYJY) and had configured things successfully on my iPad. Now I just needed to figure out how to get a basic OpenVPN client setup working in [Ubuntu](http://www.ubuntu.com/).

Step 1: Installed [OpenVPN](https://openvpn.net/). I'm (unfortunately) still running Ubuntu on this computer. If you're running another distribution, you'll have to substitute the appropriate command for your package manager.
```
sudo apt-get install openvpn
```

Step 2: Private Internet Access provides config files for various regions for iOS at http://piavpn.com/ios. I chose `us-east.ovpn` since I'm on the east coast, downloaded/saved it locally, and then moved it to `/etc/openvpn/us-east.conf`. Unfortunately, PIA's ovpn files won't *"just work"* with OpenVPN, at least not in my experience. I tried renaming the file and making a single modification to point it to my username/password information, but OpenVPN did not connect to the VPN with the configuration, ca certificate, and CRL key all in the same file like the one provided by PIA. 

That meant parsing out chunks of the .ovpn file into things that would play nicely with OpenVPN. The configuration for the server is at the beginning of the .ovpn file -- with the ca certificate dumped right in the middle. At the end is the CRL verification key. First, I pulled the CRL key out into a new file named `/etc/openvpn/crl.pem` and I copied the ca certificate into `/etc/openvpn/ca.crt`. The `<ca></ca>` and `<crl-verify></crl-verify>` should not be copied and should be deleted from the configuration file. Where the ca certificate used to be, I deleted the `setenv CLIENT_CERT 0` and added `ca ca.crt`. Similarly, `crl-verify crl.pem` got appended to the end.

Lastly, I created another new file at `/etc/openvpn/login.info` with my username/password in this format:
```
username
password
```
That's it. Just those two lines. Then back in `/etc/openvpn/us-east.conf`, we need to change this line:
```
auth-user-pass
```
to this:
```
auth-user-pass login.info
```

For the sake of clarity, after all my editing was completed, here is what's left over in `/etc/openvpn/us-east.conf`:
```
client
dev tun 
remote us-east.privateinternetaccess.com 1194 udp 
remote us-east.privateinternetaccess.com 53 udp 
remote us-east.privateinternetaccess.com 443 tcp 
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
tls-client
remote-cert-tls server
auth-user-pass login.info
comp-lzo
verb 1
reneg-sec 0
crl-verify crl.pem
```

To the moment of truth. For me, that was all the heavy lifting. `sudo service openvpn start us-east` now successfully connects to my VPN service provided by PIA.

A couple things to note - if you don't want the openvpn service to start automatically, the appropriate command is `sudo update-rc.d openvpn disable`. Of course, to use OpenVPN then you will have to use `sudo service openvpn start us-east` each time you want to start the VPN service. For those less familiar with Linux, note you can substitute `start` in that command with `stop`, `status` or `restart` (among other things) to control the service.

Happy tunneling!