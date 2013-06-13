* SUMMARY *

jQuery Resize (jresize) is a jQuery plugin to resize image. Then it is
possible to use the coordinates data to be used for any purpose.



* FEATURES *

- Resize image


* INSTRUCTIONS *

The 'jresuze' method implement the whole business which can take an optional 
setting object argument:

  $('img').jresize();

The default setting object is the following:

  var settings = {
    'zoom_min': 100,
    'zoom_max': 3000,
    'viewport_image_surrounding': false, // Set the viewport to surround the image on load
    'viewport_width': null,
    'viewport_height': null,
    'viewport_resize': true,
    'viewport_onload': null
  };

The 'viewport_onload' property can take an function callback which interface is:

  function() // which the context is $viewport

The $viewport context is a div jQuery wrapped element that surround the target
image. This object get the following subsequent properties:

  - $viewport.$container: a container holding the viewport and the zoom widget.
  - $viewport.$image: the target image jQuery wrapped.
  - $viewport.observator: an object which process all events of the viewport.

The main method of the $viewport.observator is 'register' which register an
element for an event:

  $viewport.observator.register(String event_name, jQuery wrapped elements[, callback onevent_callback])

To unregister an event use:

  $viewport.observator.unregister(string event_name)

The observator events are the following which you can then trigger some actions 
on with the jQuery bind method or by giving a function to the onvevent_callback 
argument:

  jresize_image_width
  jresize_image_height

Example:

  $('img').jresize({'viewport_onload', function() {
    var $viewport = this;
    $viewport.register('jresize_image_width', $('input#imagex'), function(event_name, element, value) {
      element.val(value);
    }
  }

There is also an event 'jresize_events' which is triggered on every events of
the previous decribed viewport observator. Use the jQuery bind methode to act on
it.

Destroy jresize (not much tested) is done by running jresize with the 'destroy' argument:

  $('img').jresize('destroy');


* REQUIEREMENTS *

jresize use jQuery and jQuery-UI.

- Developped with jQuery 1.6.1 and jQuery-UI 1.8.13
- Tested with jQuery 1.4.4 and jQuery-UI 1.8.7


* ACKNOWLEDGEMENT *

- Motivated from https://github.com/trepmag/jrac
- The jresize/images/loading.gif image file come from http://www.ajaxload.info/.
- The picture used in the example is provided (perhaps) by courtesy of Loulou 
from Sos-Chats Geneve http://www.sos-chats.ch/.


* DOWNLOAD *

https://github.com/mximos/jresize
