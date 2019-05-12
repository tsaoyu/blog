---
layout: post
title:  "Pinhole photography"
date:   2018-08-01 10:00:00
categories: [Creative arts]
---


## First assignment  
The first time I knew pinhole photography was back in junior high school. 
It was an assignment from the Physics class, we were asked to build a camera using the pinhole effect.
The design was simple Pringles cam with a tiny hole on the metal end.
The other side was covered by a piece of semi-transparent paper. 
As light went through the pinhole and projected on the paper, producing an up-side-down image.
The blurry image of I first saw have being in my head since then. 

## 10 years after  
The way we take photos changed so rapidly during the last ten years. The Kodak Express film development shop, feels like in a night, all disappeared from the high street.
The compact digital camera rise and fall. Smartphones now taking the first place as the most popular {% sidenote 'one' 'Observation based on [Most Popular Cameras](https://www.flickr.com/cameras/) in flickr user community'%} photography devices. Even before I saved enough money for a entry level DSLR, the mirrorless camera already change the way we understand professional photography.

It would be interesting to take photos using the pinhole plus latest technology so I could digitalise those images as much as possible.  
And here is how it looks like:
 
{% maincolumn  'assets/img/pinhole_photos/Seagull.jpg' 'Seagulls and People, 1960s (pretended)    F > 100, ISO 3200, 1/25 s. '%}

*Here is it!* Seagulls and People, a pretend-to-be 1960s photo taken a mirrorless camera. The camera use the exact same pinhole principle as my Pringles cam. 
The only difference is the now has a digital back so I could share the image with you.
Judging by the standard of modern photography, it was horrible.
The sharpness definitely wasn't on a par with images produced by modern lens. 
However, the blurry and unsaturated flavour makes it creamy and even dreamy. 
I guess that is the reason why it is accepted as an alternative photography. 

## Engineering a pinhole
You could drill a hole on the body cap to get your first pinhole lens.
Strictly speaking, pinhole lens is not a common optical lens focuses (or disperses) a light beam by means of refraction. 
A small hole from few micrometers to a hundred micrometers can act as a lens. 
The diameter of the pinhole is important to the quality of image.

{% marginfigure 'mf-id-1' 'assets/img/pinhole_photos/first_pinhole.JPG' 'Needle on the body cap for pinhole'%}

Chris gives an empirical formula to the pinhole size depending on the focal length and type of color.

{% math %}{d = \sqrt{f/C}}.{% endmath %}

In this equation, {% m %}d{% em %} is the diameter of pinhole, {% m %}f{% em %} is focal length in millimeters and {% m %}C{% em %}  is a constant depends on the color.
{% marginnote 'table-1-id' '*Table*: Color constant given by Chris: [web archive](http://web.archive.org/web/20170320200327/http://pinhole.stanford.edu/pinholemath.htm). Assume a 35 mm film or full frame digital equivalent' %}

<div class="table-wrapper">
<table class="booktabs">
          <thead>
            <tr><th>Colors</th><th>Wave length</th><th>Color constant C</th></tr>
          </thead>
          <tbody>
            <tr><td>Daylight</td>     <td>560 nm</td><td class="r">750</td></tr>
            <tr><td>Blue</td>         <td>450 nm</td>    <td class="r">934</td></tr>
            <tr><td>Green</td>      <td>550 nm</td> <td class="r">763</td></tr>
            <tr><td>Red</td>      <td>650 nm</td> <td class="r">647</td></tr>
            <tr><td>Infrared</td><td>750 nm</td>  <td class="r">561</td></tr>
          </tbody>
</table>
</div>

Those information is enough for the engineering of pinhole. 
For example, if we'd like to design a pinhole lens at 50mm focal length and minimise the diffraction for day light. 
The diameter of the pinhole lens is 

{% math %}{d = \sqrt{50 mm/750} = 0.258 mm}.{% endmath %}

It is not easy to use home tools to engineer a hole at such precision.
Some very geeky ruler does tell you how a 0.25 mm hole should looks like.
{% marginfigure 'mf-id-1' 'assets/img/pinhole_photos/with_ruler.jpeg' 'Original body cup with Nvidia ruler'%}
But even you had a ruler like this, you'd better start from a small hole.
Gently knock on the needle eye until it about to penetrate on the other side.
Flip the body cup and repeatedly knock on the needle eye until you made the first hole.
To extend the hole, use a larger needle on both side and knock them gently.
Put the body cup back to the camera every time before you decide to use a larger needle.
The first few images may looks like this:

{% maincolumn  'assets/img/pinhole_photos/first_pinhole_result.jpg' 'Building   F > 100, ISO 6400, 1/25 s. '%}

It is great that the pinhole is well centred in the body cap so the image in the middle of frame.
However, only the centre of the image is visible and the rest part is black.
This is because the body cup is not an ideally thin film that the thickness does influence the view angle.

{% maincolumn  'assets/img/pinhole_photos/eng_1.svg' 'Section view of the body cap, due to its thickness part of light is blocked.'%}

We could make a step cut on both side of the body cup.
This will help the increase the view angle and cover the whole area of the film (or CMOS sensor). 
The final result is shown as below 

{% maincolumn  'assets/img/pinhole_photos/final_product.jpeg' 'Inside and outside of the final result.'%}


## Taking a picture

At the time when you taking your first picture, someone may kindly remind you to take out body cup before shot.
Here are some tips or facts that might useful to create your own pinhole photos.
When using pinhole lens under day lights, the camera (Sony A7II) suggested a 1/25s shutter speed with ISO 6400. 
This is still acceptable for hand hold shotting but prepare a tripod if you prefer a lower ISO. 

Any dirt on your sensor is highly visible in the image due to the low light. 
Use the blower to clean the sensor if you mind those .

 
 {% maincolumn  'assets/img/pinhole_photos/Seagull1.jpg' 'Seagull   F > 100, ISO 6400, 1/25 s. Wiping your screen now? This was dust on the sensor.'%}