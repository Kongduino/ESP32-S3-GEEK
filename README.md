# ESP32-S3-GEEK

A repository building on, and improving, Waveshare's MicroPython code source for the [ESP32-S3-GEEK](https://www.waveshare.com/wiki/ESP32-S3-GEEK). They have [sample code](https://www.waveshare.com/wiki/ESP32-S3-GEEK#Demo) for Arduino an MicroPython.

I am working on porting some of the Arduino code for the LCD, which is quite advanced, back to MP, including fonts.

## The stuff I added

One little nitpick is that the `LCD_1inch14` class uses MP's framebuffer, which is RGB5565, where internally its color scheme is BRG565. So I added two functions to set RGB888 colors to the proper value depending on whether you are using one of the `LCD_1inch14` class's commands, or the framebuffer's.

* `rgb565(r, g, b)` For the framebuffer's commands.
* `brg565(r, g, b)` For the internal commands.

### Other commands

* `clear_color(color)` Fills the screen with a color.
* `drawChar(FontRecord, c, fc = 0, bc = -1, px = 10, py = 10)`
	Draw one character
	- FontRecord = the FontRecord of the font you want you use
	- c = character
	- fc = forecolor
	- bc = background color
* `drawString(FontRecord, s, fc = 0, bc = -1, px = 10, py = 10)`
	Draw a string
	- FontRecord = the FontRecord of the font you want you use
	- s = string of characters
	- fc = forecolor
	- bc = background color
* `invert()` Inverts the screen
