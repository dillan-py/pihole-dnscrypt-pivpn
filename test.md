
# Secure Pi Setup using Pi-Hole, Pi-VPN with DNSCrypt

Setup initial configuration

## Update Pi
```bash
sudo apt update && sudo apt upgrade -y
sudo apt autoremove && sudo apt autopurge -y    # Clean up any unused packages
```

## Install Pi-hole
```bash
curl -sSL https://install.pi-hole.net | bash
```

## Install PiVPN (WireGuard/OpenVPN)
```bash
curl -L https://install.pivpn.io | bash
# Follow the interactive installer to choose WireGuard or OpenVPN
```

## Configure DNSCrypt
```bash
sudo apt install -y dnscrypt-proxy
sudo systemctl enable dnscrypt-proxy
sudo systemctl start dnscrypt-proxy
```

## Verify Services
```bash
pihole status          # Check Pi-hole status
pivpn -d               # Run PiVPN debug
systemctl status dnscrypt-proxy
```

## Next Steps
- Configure Pi-hole upstream DNS to point to `127.0.0.1#53` if using DNSCrypt as local resolver.
- Open/forward the chosen VPN port on your router (default WireGuard: 51820/UDP).
- Add your client profiles and test connectivity.
