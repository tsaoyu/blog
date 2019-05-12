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

In this equation, {% math %}d{% endmath %} is the diameter of pinhole, {% math %}f{% endmath %} is focal length in millimeters and {% math %}C{% endmath %}  is a constant depends on the color.
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

It is not easy to use home tool to engineer a hole at such precision. 
But it is always safe to start from a smaller diameter to a larger diameter.

{% maincolumn  'assets/img/pinhole_photos/first_pinhole_photo.jpg' 'Building   F > 100, ISO 6400, 1/25 s. '%}

The whole picture 