# bd_V_Kolam — visual module for ButterflyDreaming

Standalone deployment of the **bd_V_Kolam** visual module — an
L-system kolam pattern generator driven by a compact `%%bd_…`
directive script.

Live at: **https://wrcstewart.github.io/bd_V_Kolam/preview.html**

## What this is

Two files serve directly from GitHub Pages:

- **`preview.html`** — the standalone harness. Sliders for
  every directive, a script textarea (read-only; sliders are the
  edit surface), Copy / Copy Link / Enter-BD buttons.
- **`visual_module.html`** — the module itself, loaded as an
  iframe inside `preview.html`. Renders the current script to
  a canvas via a small L-system evaluator + colour engine.

No server, no build step, no dependencies. Just static HTML.

## Directive vocabulary (short)

Every controllable parameter has a `%%bd_<name> <value>` directive.
A representative script:

```
%%bd_module bd_V_Kolam
%%bd_symmetry 8
%%bd_depth 3
%%bd_step 40
%%bd_angle 45
%%bd_angle_minutes 0
%%bd_angle_drift 3
%%bd_colour_speed 4
%%bd_stroke angle
%%bd_saturation 100
%%bd_lightness 65
%%bd_background #0a0a0f
%%bd_weight 1.5
%%bd_score [
axiom: F+F+F+F+F+F+F+F
F: F+F-F-F+F+F+F-F
%%bd_]
```

Full grammar is documented inline at the top of
`visual_module.html` (search for `bd_ui_config`).

## Deep links

Both link directions are supported:

- **Link into EV** — `preview.html?data=<base64-payload>` where
  the payload carries `{ script, node_url, source_text, title }`.
  Used by the ButterflyDreaming platform's "Copy Link to
  External Website" button.
- **Link back to BD** — the "Enter ButterflyDreaming" and
  "Copy BD Link" buttons in `preview.html` produce a URL of
  the same shape targeting the BD viewer, so the browser
  hands a user back to the graph at the node they came from.

## Relation to the main ButterflyDreaming project

This module is one of several planned media modules for the
[ButterflyDreaming graph viewer](https://github.com/wrcstewart/butterflydreaming-graphviewer1).
The main project provides the graph corpus, chat/pair system,
and the container that loads this module in its Player mode.

This repo exists as its own deployable so anyone can play with
kolam pattern generation without running the whole platform.

## License

Released under **CC0-1.0** (public domain dedication). Do what
you like with it, no attribution required.
