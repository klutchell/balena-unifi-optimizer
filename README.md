# balena-unifi-optimizer

Network monitoring and optimization for UniFi networks, deployed on balena.

[![balena deploy button](https://www.balena.io/deploy.svg)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/klutchell/balena-unifi-optimizer)

## About

This project deploys [NetworkOptimizer](https://github.com/Ozark-Connect/network-optimizer) on balena devices. NetworkOptimizer provides:

- Real-time network topology visualization
- UniFi device monitoring and management
- Integrated speed testing via OpenSpeedTest
- Network health metrics and alerts

## Deploy

### One-Click Deploy

Click the deploy button above to create a new fleet with this application.

### Manual Deploy

1. Create a new fleet in the [balena dashboard](https://dashboard.balena-cloud.com)
2. Add a device and download the OS image
3. Flash the image to your device
4. Clone this repository:
   ```bash
   git clone https://github.com/klutchell/balena-unifi-optimizer.git
   cd balena-unifi-optimizer
   ```
5. Push to your fleet:
   ```bash
   balena push <fleet-name>
   ```

## Device Variables

Set these variables in the balena dashboard under **Device Variables**:

| Variable | Required | Description | Example |
|----------|----------|-------------|---------|
| `HOST_IP` | Yes | Device IP address (for speed tests) | `192.168.1.100` |
| `HOST_NAME` | No | Friendly device hostname | `network-optimizer` |
| `TZ` | No | Timezone | `America/Chicago` |

## Usage

After deployment, access the services at:

| Service | URL | Description |
|---------|-----|-------------|
| Network Optimizer | `http://<device-ip>:8042` | Main web UI |
| SpeedTest | `http://<device-ip>:3005` | OpenSpeedTest UI |

## Volumes

| Volume | Path | Description |
|--------|------|-------------|
| `data` | `/app/data` | Application data and configuration |
| `ssh-keys` | `/app/ssh-keys` | SSH keys for device access (read-only) |
| `logs` | `/app/logs` | Application logs |

## License

MIT
