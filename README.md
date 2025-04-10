# Quiz-2

from gpiozero import Button, LED
import time

# Set up RGB LED 
red_led = LED(25)
green_led = LED(23)
blue_led = LED(24)

# Set up Buttons 
red_button = Button(17)
green_button = Button(27)
blue_button = Button(22)

# Function to set the RGB color based on button presses
def main():
    # Initial states
    red_led.off()
    green_led.off()
    blue_led.off()

    # Check each button and mix colors accordingly
    if red_button.is_pressed:
        red_led.on()

    if green_button.is_pressed:
        green_led.on()

    if blue_button.is_pressed:
        blue_led.on()

    # Color mixing logic - if multiple buttons are pressed
    if red_button.is_pressed and green_button.is_pressed and blue_button.is_pressed:
        red_led.on()
        green_led.on()
        blue_led.on()  

    elif red_button.is_pressed and green_button.is_pressed:
        red_led.on()
        green_led.on()
        blue_led.off()  
    elif red_button.is_pressed and blue_button.is_pressed:
        red_led.on()
        green_led.off()
        blue_led.on()  
    elif green_button.is_pressed and blue_button.is_pressed:
        red_led.off()
        green_led.on()
        blue_led.on() 

# Initial state: all LEDs off
red_led.off()
green_led.off()
blue_led.off()

print("Program started. Press buttons to change LED color.")

# Main loop
while True:
    main()
    time.sleep(0.1)

