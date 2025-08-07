# 🕐 Modern Clock - Eww Widget

A sleek, transparent desktop clock widget built for [Eww (ElKowars wacky widgets)](https://github.com/elkowar/eww). Features a modern design with bold typography and clean aesthetics perfect for any desktop setup.

![Modern Clock Widget Preview](preview.png)

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
   cp -r modern-clock ~/.config/eww/
   ```

3. If you have an existing `eww.yuck / eww.scss` file, append the contents of `modern-clock.yuck / modern-clock.scss` to it, or include it:
   ```lisp
   (include "modern-clock/modern-clock.yuck")
   ```

4. Import the styles in your main SCSS file:
   ```scss
   @import "modern-clock/modern-clock.scss";
   ```

5. **Optional but recommended**: Install the Anurati font for optimal appearance:
   ```bash
   # Download Anurati-Regular.otf and place it in your fonts directory
   mkdir -p ~/.local/share/fonts 	# Make it only if it doesn't exist'
   cp Anurati-Regular.otf ~/.local/share/fonts/		# Copy all fonts to the fonts folder
   fc-cache -fv 	# To scans the font directories on the system
   ```

## 🚀 Usage

### 🏃‍♂️ Launch the Widget

Start the clock widget with:
```bash
eww ~/path/to/eww open clock-window-0
eww ~/path/to/eww open clock-window-1		# For second monitor
```


### 🔄 Auto-start on Boot

Add to your window manager's autostart configuration:

**i3/sway config:**
```
exec eww ~/path/to/eww open clock-window-0
exec eww ~/path/to/eww open clock-window-1		# For second monitor
```

**Hyprland:**
```
exec-once = eww ~/path/to/eww open clock-window-0
exec-once = eww ~/path/to/eww open clock-window-1		# For second monitor
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
modern-clock-widget/
├── modern-clock
│   ├── modern-clock.scss
│   └── modern-clock.yuck
├── Poppins
│		├── Anurati-Regular.otf
│		├── Poppins-BlackItalic.ttf
│		├── Poppins-Black.ttf
│		├── Poppins-BoldItalic.ttf
│		├── Poppins-Bold.ttf
│		├── Poppins-ExtraBoldItalic.ttf
│		├── Poppins-ExtraBold.ttf
│		├── Poppins-ExtraLightItalic.ttf
│		├── Poppins-ExtraLight.ttf
│		├── Poppins-Italic.ttf
│		├── Poppins-LightItalic.ttf
│		├── Poppins-Light.ttf
│		├── Poppins-MediumItalic.ttf
│		├── Poppins-Medium.ttf
│		├── Poppins-Regular.ttf
│		├── Poppins-SemiBoldItalic.ttf
│		├── Poppins-SemiBold.ttf
│		├── Poppins-ThinItalic.ttf
│		└── Poppins-Thin.ttf
├── LICENSE
└── README.md 
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

### ❌ Widget Not Appearing

1. Check if eww is running: `eww ping`
2. Verify widget syntax: `eww reload`
3. Check logs: `eww logs`

### 🔤 Font Issues

1. Verify font installation: `fc-list | grep -i anurati`
2. Sometimes a reboot to the system is needed
3. Use the fallback fonts (Impact, Arial Black)
4. Modify the font-family in the SCSS file if needed

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

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.


---

**Made with ❤️ for the Eww community**
