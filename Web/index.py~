from flask import *
app = Flask(__name__)

import RPi.GPIO as GPIO
GPIO.setwarnings(False)
GPIO.setmode(GPIO.BCM)

# leds
amarillo = 16
verde = 18
GPIO.setup(amarillo, GPIO.OUT)
GPIO.output(amarillo, GPIO.LOW)
GPIO.setup(verde, GPIO.OUT)
GPIO.output(verde, GPIO.LOW)

@app.route('/')
def home():
   templateData = {
      'amarillo' : 0,
      'verde' : 0,
   }
   return render_template('microondas.html', **templateData)

@app.route('/<led>/<action>')
def led(led, action):
   GPIO.output(int(led), int(action))
   templateData = {
      'amarillo' : GPIO.input(amarillo),
      'verde' : GPIO.input(verde),
   }
   return render_template('microondas.html', **templateData)

if __name__ == '__main__':
   app.run(host='0.0.0.0', port=8000, debug=True)