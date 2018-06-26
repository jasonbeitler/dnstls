# dnstls

Just a quick how to use Studdby to setup DNS over TLS.  

# Macos

Install stubby from home brew

    $brew install stubby
    
Pull the stubby config from the repo "stubby.yml"

    $git clone https://github.com/jasonbeitler/dnstls.git

Move stubby.yml to brew services

     $mv stubby.yml /usr/local/etc/stubby/stubby.yml
    
Start the stubby service now and on boot

     $sudo brew services start stubby
    
Change DNS server to 127.0.0.1


# Linux

These directions are for Fedora but should work on any distro with some changes

Install Stubby
    
     $sudo dnf -y install bind-utils getdns

Pull the stubby config from the repo "stubby.yml"

     $git clone https://github.com/jasonbeitler/dnstls.git

Move stubby.yml to the config dir

     $sudo mv stubby.yml /etc/stubby/stubby.yml 
    
Edit systemclt file

     $sudo  vim /etc/systemd/system/stubby.service
    
Edit [Service] section to

    ExecStart=/bin/stubby -l
    
Reload Daemon / enable Daemon

     $sudo systemctl daemon-reload && sudo systemctl enable --now stubby && sudo systemctl restart stubby.service
    
Edit resolv.conf

     $sudo vim /etc/resolv.conf

Should look like this now

    nameserver 127.0.0.1
    
If you are running DHCP you might need to use chattr to keep resolv.conf from changing on reboot / or changing networks

     $sudo chattr +i /etc/resolv.conf
    
* Note doing this will prevent anything from making changes to your resolv.conf file including VPNs, this could be an issue on on Corporate VPN.
