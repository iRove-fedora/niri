# Niri
This patched version of niri enables us to specify sandbox rules. These rules determine what protocols sandboxed apps inside wayland security contexts are allowed to access. This could be useful, e.g., in the case of flatpaks.

## Building
To build, use
`fedpkg mockbuild`
to generate the rpm, and then install it with `dnf install path_to_rpm.rpm`

## Usage
Example sandbox rule in `config.kdl`: 
Privileged protocols are `layer-shell`, `session-lock`, `input-method`, `virtual-keyboard`, `virtual-pointer`, `foreign-toplevel-management`, `workspace`, `output-management`, `screencopy`, `ext-data-control`, and `wlr-data-control`.

```
sandbox-rule {
	match app-id="io.github.alexays.waybar"
	privileged-protocol-allowlist "layer-shell"
}
```

Where `app-id` is the app-id specified by flatpak.
