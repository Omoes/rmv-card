# rmv-card

This card generates a simple departure card for the RMV public transport service.

![example](example.png)

## Installation

### Step 1

Install `rmv-card` by copying `rmv-card.js` from this repo to `<config directory>/www/rmv-card.js` of your Home Assistant instance.

**Example:**

```bash
wget https://github.com/cgtobi/rmv-card/raw/master/rmv-card.js
mv list-card.js ~/.homeassistant/www/
```

### Step 2

Set up the rmv transport sensor.

**Example:**

```yaml
sensor:
  - platform: rmvtransport
    next_departure:
    - station: 3000010
      time_offset: 5
      destinations:
        - 'Frankfurt (Main) Flughafen Regionalbahnhof'
        - 'Frankfurt (Main) Stadion'
      products:
        - 'RB'
        - 'RE'
        - 'Bus'
        - 'S'
```

### Step 3

Link `rmv-card` inside you `ui-lovelace.yaml`.

```yaml
resources:
  - url: /local/rmv-card.js?v=0
    type: js
```

### Step 4

Add a custom element in your `ui-lovelace.yaml`

**Example:**

```yaml
      - type: "custom:rmv-card"
        entity:
          - sensor.frankfurt_main_hauptbahnhof
```

## Credits

Thanks to [DavidMStraub](https://github.com/DavidMStraub) for all his initial work.
