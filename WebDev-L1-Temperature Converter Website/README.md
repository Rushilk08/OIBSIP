# Temperature Converter

An interactive web tool that converts temperatures between **Celsius, Fahrenheit and Kelvin**, with real-time input validation and a dynamic icon that shows whether the temperature is cold, moderate or hot.

Built with plain **HTML5, CSS3 and vanilla JavaScript**. There are no frameworks, no build step and no dependencies.

The visual style is a dark, soft-3D (neumorphic) interface on a violet striped background, with mint accents.

---

## Getting started

1. Keep the three files together in one folder.
2. Open `index.html` in any modern browser (Chrome, Edge, Firefox, Safari).

No server or installation is needed.

```
temperature-converter/
├── index.html    # page structure
├── style.css     # layout, theme and animations
├── script.js     # conversion, validation and UI logic
└── README.md
```

---

## How to use

1. Type a temperature in the **Temperature value** field.
2. Choose the unit you are converting **from** (Celsius, Fahrenheit or Kelvin).
3. Click **Convert** (or press **Enter**).
4. Read the result in all three units at once, and check the icon in the Gauge panel.
5. Use **Copy** next to any result to copy it, or **Reset** to start over.

---

## Features

| # | Requirement | How it is implemented |
|---|---|---|
| 1 | Numeric input with validation | Text field with a strict number check. Non-numeric input (such as `abc` or `12abc`) shows a red error message as you type, and the field shakes on Convert. |
| 2 | Input unit selector | Three radio-style buttons: Celsius, Fahrenheit, Kelvin. |
| 3 | All output units at once | Every conversion shows Celsius, Fahrenheit and Kelvin together. The unit you entered is outlined. |
| 4 | Convert button | Calculates on click. The Enter key works too, and a Reset button clears everything. |
| 5 | Result display with unit labels | Results show `°C`, `°F` and `K` labels, each with a Copy button. |
| 6 | Absolute-zero edge case | Values below −273.15 °C, −459.67 °F or 0 K show a friendly warning instead of a result. |
| 7 | Clean, centred UI | A centred three-panel card (Input, Gauge, Results) with clear labels. It stacks into one column on small screens. |

### Dynamic temperature icon

The Gauge panel shows a large animated badge whose icon and ring colour change with the temperature.

| State | Range (in °C) | Icon | Animation |
|---|---|---|---|
| Idle | before converting | Dimmed thermometer | none |
| Cold | below 15 | Snowflake | Slowly spins and pulses |
| Moderate | 15 to below 35 | Thermometer | Mercury rises and falls |
| Hot | 35 and above | Flame | Flickers while the ring glows |

The thresholds apply to the Celsius equivalent of whatever you enter, so 110 °F counts as hot because it is about 43 °C. A label under the badge states the range.

Animations switch off automatically for visitors whose device is set to reduce motion.

---

## Validation rules

- **Accepted:** integers, decimals, a leading `+` or `-`, and exponent notation. Examples: `25`, `-3.5`, `.5`, `1e3`.
- **Rejected:** empty input, letters, doubled signs and thousands separators. Examples: `abc`, `12abc`, `--5`, `1,000`.
- **Below absolute zero:** the check is done on the Celsius equivalent, so the limit is the same physical point in every unit.

| Unit | Lowest allowed value |
|---|---|
| Celsius | −273.15 °C |
| Fahrenheit | −459.67 °F |
| Kelvin | 0 K |

Validation runs live while typing and when you switch units, and again when you click Convert.

---

## Conversion formulas

Every value is first converted to Celsius, then to the other units.

| From | To Celsius |
|---|---|
| Celsius | `C` |
| Fahrenheit | `(F − 32) × 5/9` |
| Kelvin | `K − 273.15` |

| To | From Celsius |
|---|---|
| Fahrenheit | `C × 9/5 + 32` |
| Kelvin | `C + 273.15` |

Results are rounded to **two decimal places**.

### Quick checks

| Input | Celsius | Fahrenheit | Kelvin |
|---|---|---|---|
| 100 °C | 100 | 212 | 373.15 |
| 32 °F | 0 | 32 | 273.15 |
| 0 K | −273.15 | −459.67 | 0 |

---

## Customising

- **Cold and hot cut-offs:** change `COLD_BELOW_C` and `HOT_FROM_C` near the top of `script.js`.
- **Colours:** edit the variables in the `:root` block at the top of `style.css`. `--bg` is the background, `--accent` is the mint highlight, and `--danger` is the error colour.
- **Rounding:** change the `100` in the `format()` function in `script.js`, and the matching `maximumFractionDigits`, to alter the decimal places.

---

## Accessibility

- All inputs have visible labels, and the error message is announced to screen readers.
- The unit selector uses real radio inputs, so it works with the keyboard and shows a focus outline.
- The result notice is announced politely when it changes.
- The badge exposes its current state through an `aria-label`.

---

## Browser support

Works in current versions of Chrome, Edge, Firefox and Safari. The Copy button uses the Clipboard API, which browsers only allow on secure pages (HTTPS) or on `localhost`. If you open the page straight from disk and Copy does nothing, serve the folder locally, for example with `python3 -m http.server`.