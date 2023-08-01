apt update && apt upgrade -y

sudo apt -y install dante-server

danted -v

chmod +x /etc/init.d/danted

update-rc.d danted defaults

nano /etc/danted.conf

conf :

logoutput: /var/log/socks.log
internal: eth0 port = 1081
external: eth0
clientmethod: none
socksmethod: none              
user.privileged: root
user.notprivileged: nobody

client pass {
        from: 0.0.0.0/0 to: 0.0.0.0/0
        log: error connect disconnect
}
client block {
        from: 0.0.0.0/0 to: 0.0.0.0/0
        log: connect error
}
socks pass {
        from: 0.0.0.0/0 to: 0.0.0.0/0
        log: error connect disconnect
}
socks block {
        from: 0.0.0.0/0 to: 0.0.0.0/0
        log: connect error
}



systemctl enable danted

systemctl start danted

systemctl status danted



https://chrome.google.com/webstore/detail/oxylabs-proxy-extension/infajoaodhhdogakhloedbppcbeajhoo/related
