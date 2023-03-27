---
layout: post
title:  "32blit sdk input"
categories: 32blit
---

I didn't have the chance to learn inputs from any documentation. Maybe it's well hidden or I am unable to find it. Nevertheless, here's what I was able to figure out.

Checking if any button is pressed can be done via the `buttons` class. Here is the test code that I used

{% highlight c %}
if(buttons || buttons.pressed || buttons.released || buttons.state)
{
    blit::debugf("Input down is %d, ", buttons);
    blit::debugf("Pressed is %d, ", buttons.pressed);
    blit::debugf("Released is %d, ", buttons.released);
    blit::debugf("State is %d\n\r", buttons.state);
}
{% endhighlight %}

It's pretty clear what they do except maybe from he state variable which seems to represent both buttons and buttons.pressed.

Each variables represents the bytes of the button affected. The enum Button includes the small selection available

{% highlight c %}
enum Button : unsigned int {
  DPAD_LEFT = 1,
  DPAD_RIGHT = 2,
  DPAD_UP = 4,
  DPAD_DOWN = 8,
  A = 16,
  B = 32,
  X = 64,
  Y = 128,
  MENU = 256,
  HOME = 512,
  JOYSTICK = 1024
};
{% endhighlight %}

So in order to check which button is down the check would be `if (buttons & Button::A)`