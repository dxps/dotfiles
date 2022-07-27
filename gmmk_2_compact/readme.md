# My Layout for GMMK 2 Compact

Of course, this is based on QMK firmware.<br/>
I posted [here](https://gloriousforum.com/t/qmk-install-keymap-guide-for-gmmk-2-compact-on-ubuntu-distros/14529) a step-by-step guide of how to install QMK in this keyboard.

The layout itself is defined in `qmk_firmware/keyboards/gmmk/gmmk2/p65/ansi/keymaps/default/keymap.c`:
```c
#include QMK_KEYBOARD_H

// Each layer gets a name for readability, which is then used in the keymap matrix below.
// The underscores don't mean anything - you can have a layer called STUFF or any other name.


const uint16_t PROGMEM keymaps[][MATRIX_ROWS][MATRIX_COLS] = {
[0] = LAYOUT(
KC_ESC,  KC_1,       KC_2,       KC_3,       KC_4,       KC_5,     KC_6,      KC_7,     KC_8,     KC_9,     KC_0,     KC_MINS,    KC_EQL,    KC_BSPC,  KC_WREF,
KC_TAB,  KC_Q,       KC_W,       KC_E,       KC_R,       KC_T,     KC_Y,      KC_U,     KC_I,     KC_O,     KC_P,     KC_LBRC,    KC_RBRC,   KC_BSLS,  KC_PGUP,
MO(1),   KC_A,       KC_S,       KC_D,       KC_F,       KC_G,     KC_H,      KC_J,     KC_K,     KC_L,     KC_SCLN,  KC_QUOT,    KC_ENT,              KC_PGDN,
KC_LSFT, KC_Z,       KC_X,       KC_C,       KC_V,       KC_B,     KC_N,      KC_M,     KC_COMM,  KC_DOT,   KC_SLSH,  KC_RSFT,               KC_UP,    KC_DEL,
KC_LCTL, KC_LGUI,    KC_LALT,                            KC_SPC,                                  KC_RALT,  MO(1),                KC_LEFT,   KC_DOWN,  KC_RGHT),

[1] = LAYOUT(
KC_GRV,  KC_F1,      KC_F2,      KC_F3,      KC_F4,      KC_F5,    KC_F6,     KC_F7,    KC_F8,    KC_F9,    KC_F10,   KC_F11,     KC_F12,   _______,   RGB_TOG,
_______, KC_VOLD,    KC_VOLU,    KC_BSPC,    _______,    _______,  _______,   _______,  KC_GRV,   _______,  KC_CAPS,  RGB_HUD,    RGB_HUI,  _______,   RGB_VAI,
_______, LCTL(KC_A), LCTL(KC_S), KC_DEL,     LCTL(KC_F), _______,  KC_LEFT,   KC_DOWN,  KC_UP,    KC_RGHT,  KC_END,   _______,    _______,             RGB_VAD,
_______, LCTL(KC_Z), LCTL(KC_X), LCTL(KC_C), LCTL(KC_V), _______,  _______,   KC_HOME,  KC_VOLD,  KC_VOLU,  KC_MUTE,  LCTL(KC_W),            KC_PGUP,  KC_INS,
_______, _______,    _______,                            _______,                                 _______,  _______,              KC_HOME,  KC_PGDN,   KC_END),

[2] = LAYOUT(
_______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______,
_______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______,
_______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______,
_______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______, _______,
_______, _______, _______, _______, _______, _______, _______, _______, _______)
};

```

Brief notes how to apply it (after QMK firmware is already applied to the keyboard):
1. Do a `sudo tail -F /var/log/syslog` in a terminal to verify that the keyboard starts correctly in the next step.
2. Keep Esc key pressed while connecting the keyboard to start in bootloader mode
3. After updating that `keymap.c` file, you can run a quick check using `qmk flash -kb gmmk/gmmk2/p65/ansi -km default`
4. Flash that layout using `qmk compile -kb gmmk/gmmk2/p65/ansi -km default`


