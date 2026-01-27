# Custom mullvad vpn module for waybar

![Green lock](./images/screenshot1.png "Mullvad Waybar Module")

Just needed a simple way to see if I'm connected to Mullvad VPN and what server I'm using, so I made this simple waybar module.

## Prerequisites

- `mullvad-vpn` or `mullvad-vpn-cli` installed and configured on your system.

## Getting Started

1. If you haven't already installed mullvad-vpn, you can install from yay with:

```sh
yay -S mullvad-vpn-bin
```

or if you just want the CLI:

```sh
yay -S mullvad-vpn-cli
```

2. Add mullvad module to waybar config:

```sh
  "custom/mullvad": {
    "format": "{icon}",
    "exec": "/your-path-to-the-mullvad-scrpit/mullvad.sh",
    "interval": 60,
    "return-type": "json",
    "on-click": "/your-path-to-the-mullvad-scrpit/mullvad.sh toggle",
    "on-click-middle": "mullvad-vpn",
    "on-click-right": "/your-path-to-the-mullvad-scrpit/mullvad.sh reconnect",
    "format-icons": {
      "connected": "\uf023",
      "connecting": "\uf023",
      "disconnected": "\uf2fc",
    },
    "tooltip": true,
  },

```

3. Add mullvad module styling to waybar style.css:

```css
@define-color warning #F6B016;
@define-color success #01D38F;

#custom-mullvad {
  min-width: 14px;
  margin: 0 7.5px;
}

#custom-mullvad.connecting {
  color: @foreground;
}
#custom-mullvad.connected {
  color: @success;
}
#custom-mullvad.disconnected {
  font-size: 16px;
  margin: 0 7.5px 0 4.5px;
  color: @error;
}
```

4. Put the script wherever you store your waybar scripts

5. Restart waybar

```sh
killall waybar && waybar &
```

done!

## Resources

<https://mullvad.net/en>

<https://github.com/Alexays/Waybar>

## Thanks

Thanks to Mullvad for providing a great product!

<https://mullvad.net/en>
