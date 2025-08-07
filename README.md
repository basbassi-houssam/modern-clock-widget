# 🕐 Modern Clock - Eww Widget

A sleek, transparent desktop clock widget built for [Eww (ElKowars wacky widgets)](https://github.com/elkowar/eww). Features a modern design with bold typography and clean aesthetics perfect for any desktop setup.

<img width="1680" height="1050" alt="image" src="https://github.com/user-attachments/assets/a46a43ea-1a8b-4332-9e74-d6f860e49890" />


## ✨ Features

- **🔍 Transparent Design** - Seamless integration with any wallpaper
- **🖥️ Multi-Monitor Support** - Automatically displays on monitors 0 and 1
- **⚡ Real-Time Updates** - Time updates every second, date/day every minute
- **🎨 Modern Typography** - Uses Anurati font for day display with fallbacks
- **🧹 Clean Layout** - Minimalist vertical layout with proper spacing
- **🖱️ Desktop Integration** - Sits at desktop level, won't interfere with other windows

## 📅 Display Format

- **📆 Day**: Large uppercase letters (e.g., "MONDAY")
- **🗓️ Date**: Formatted as "~ 08 AUG 2025 ~"
- **⏰ Time**: 12-hour format "- 02:30 PM -"

## 📦 Installation

### 🔧 Prerequisites

- [Eww](https://github.com/elkowar/eww) installed and configured
- Optional: [Anurati font](https://www.behance.net/gallery/19532783/Anurati-Free-Font) for optimal typography

### ⚙️ Setup

1. Clone this repository or download the files:
   ```bash
   git clone https://github.com/basbassi-houssam/modern-clock-widget.git
   cd modern-clock-widget
   ```

2. Copy the widget files to your eww configuration directory:
   ```bash
   cp modern-clock.yuck ~/.config/eww/
   cp modern-clock.scss ~/.config/eww/
   ```

3. If you have an existing `eww.yuck` file, append the contents of `modern-clock.yuck` to it, or include it:
   ```lisp
   (include "modern-clock.yuck")
   ```

4. Import the styles in your main SCSS file:
   ```scss
   @import "modern-clock.scss";
   ```

## 🚀 Usage

### 🏃‍♂️ Launch the Widget

Start the clock widget with:
```bash
eww ~/path/to/eww open clock-window-0
```

For dual monitor setup:
```bash
eww ~/path/to/eww open clock-window-0 clock-window-1
```

### 🔄 Auto-start on Boot

Add to your window manager's autostart configuration:

**i3/sway config:**
```
exec eww ~/path/to/eww open clock-window-0
```

**Hyprland:**
```
exec-once = eww ~/path/to/eww open clock-window-0
```

## 🎨 Customization

### 📍 Position

Modify the geometry settings in `modern-clock.yuck`:
```lisp
:geometry (geometry :x "20px"      ; Horizontal position
                    :y "20px"      ; Vertical position
                    :anchor "center") ; Anchor point
```

Available anchors: `top left`, `top center`, `top right`, `center left`, `center`, `center right`, `bottom left`, `bottom center`, `bottom right`

### 🌈 Colors

Edit the SCSS file to change colors:
```scss
.day {
  color: #ffffff; /* Change day color */
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7); /* Modify shadow */
}
```

### 🔤 Font Size

Adjust font sizes in the SCSS:
```scss
.day {
  font-size: 100px; /* Day font size */
}

.clock-date, .time {
  font-size: 20px; /* Date and time font size */
}
```

### ⏱️ Update Intervals

Modify polling intervals in the yuck file:
```lisp
(defpoll current-time :interval "1s" "date '+- %I:%M %p -'")  ; Time updates
(defpoll current-date :interval "60s" "date '+~ %d %b %Y ~'") ; Date updates
```

### 📊 Date/Time Format

Customize the date and time format by modifying the date commands:
```lisp
;; 24-hour format
(defpoll current-time :interval "1s" "date '+- %H:%M -'")

;; Different date format
(defpoll current-date :interval "60s" "date '+%B %d, %Y'")
```

## 📁 File Structure

```
modern-clock/
├── modern-clock.yuck    # Widget definition and logic
├── modern-clock.scss    # Styling and appearance
├── README.md           # This file
└── preview.png         # Widget preview (add your own)
```

## ⚙️ Configuration Details

### 🪟 Window Properties

- **Stacking**: Set to "bottom" - appears below all other windows
- **Window Type**: "desktop" - integrated with desktop environment
- **WM Ignore**: True - window manager ignores this window
- **Transparency**: Fully transparent background

### 🔤 Fonts Used

1. **Day Display**: Anurati (fallback: Impact, Arial Black)
2. **Date/Time**: Poppins (fallback: Roboto, Inter, system fonts)

## 🛠️ Troubleshooting

### ❌ Widget Not Appearing

1. Check if eww is running: `eww ping`
2. Verify widget syntax: `eww reload`
3. Check logs: `eww logs`

### 🔤 Font Issues

If fonts don't display correctly:
1. Install the Anurati font system-wide
2. Use the fallback fonts (Impact, Arial Black)
3. Modify the font-family in the SCSS file

### 🖥️ Multi-Monitor Issues

For more than 2 monitors, add additional window definitions:
```lisp
(defwindow clock-window-2
  :monitor 2
  ;; ... rest of configuration
  (clock))
```

## 💖 Support

If you find this widget useful, consider supporting its development:

[![Ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/basbassihoussam)

[![PayPal](https://img.shields.io/badge/PayPal-00457C?style=for-the-badge&logo=paypal&logoColor=white)](https://paypal.me/BasbassiHoussam)

Your support helps maintain and improve this project!

## 🤝 Contributing

Feel free to submit issues, feature requests, and pull requests to improve this widget.

## 📄 License

[LICENSE]

---

**Made with ❤️ for the Eww community**
