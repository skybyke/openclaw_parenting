# Parental Control Stack

*As of March 2026*

## Philosophy
Layered and redundant — no single point of failure, follows Archer across networks, framed as supportive scaffolding rather than hard blocks.

## Network Layer
- **Firewalla Gold SE** router with VLAN segmentation
  - Dedicated monitored VLAN 67 for Archer's devices
- **NextDNS** for content filtering
  - Two profiles: restrictive (school) and open (home)
  - Automated switching between profiles

## Device Layer — Windows
- Separate user accounts: `Archer-School` / `Archer-Home`
- Accounts managed via Home Assistant SSH
- NextDNS CLI running as Windows service (persists regardless of network)
- **AppLocker** for application whitelisting
- **SentryPC** for visual monitoring and keystroke logging

## Device Layer — iOS
- **BrightCanary** for social media monitoring
- Apple Configurator 2 supervision in progress
  - MDM ruled out due to Apple Business Manager requirements

## Automation & Alerting
- **Home Assistant** ties it together:
  - Triggers account switches
  - Profile changes
  - Alert responses
- Dedicated email for security alerts
- Nabu Casa for remote access
- TV and laptop time tracked automatically for screentime limiting

## Quick Actions
- Unblocking a site: ~30 seconds via phone
- Account switching: automated via Home Assistant
