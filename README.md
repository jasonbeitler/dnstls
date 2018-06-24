# dnstls

Just a quick how to use Studdby to setup DNS over TLS.  

# Macos

1. Install stubby from home brew

    $brew install stubby
    
2. Pull the stubby config from the repo "stubby.yml"

    $git clone https://github.com/jasonbeitler/dnstls.git

3. Move stubby.yml to brew services

    $mv stubby.yml /usr/local/etc/stubby/stubby.yml
    
4. Start the stubby service now and on boot

    $sudo brew services enable stubby
    
5. Change DNS server to 127.0.0.1
