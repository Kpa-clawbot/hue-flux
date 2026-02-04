# hue-flux
Recreation of f.lux for Philips Hue lights in Python by KpaBap

This script aims to closely replicate the functionality of f.lux for Philips Hue.
It is meant to be run from a cronjob once a day, or manually whenever you want the lights to turn on and begin fading.

## Requirements

- Philips Hue bridge on local network
- Python 3
- [phue](https://github.com/studioimaginaire/phue) library - install with `pip3 install phue`

## Sunset Time Configuration

You have two options for determining sunset time:

### Option 1: Weather Underground API (automatic)
Get a Wunderground API key and save it on a single line in a text file called `wunder.apikey` - this allows automatic lookup of your location's time of sunset.

> **Note:** The Weather Underground API was deprecated in 2019. This feature may no longer work. Consider using Option 2 instead.

### Option 2: Manual sunset time
Set `sunset_time` manually in `hue-flux.py` in 24hr format - e.g. `"21:00"`

## Configuration

Edit the following variables in `hue-flux.py`:

- `location` - Your zip code or location string (for API lookup)
- `bedtime` - When to reach the warmest color temperature (24hr format)
- `day_colortemp` - Color temperature during the day (default: 4000K)
- `sunset_colortemp` - Color temperature at sunset (default: 3000K)
- `bedtime_colortemp` - Color temperature at bedtime (default: 1900K)
- `searchtext` - String to match against light names (e.g., "Computer" matches "Computer 1", "Computer 2", etc.)

## Usage

```bash
python3 hue-flux.py
```

On first run, you'll be prompted to press the button on your Hue bridge to authorize the connection.

## License

Apache License 2.0
