leaflet-zoom-extras
===================

Extends Leaflet's Zoom controller to allow for extra buttons


### Create controls
```
var zoomControls = new L.Control.ZoomExtras( {
    position: 'topright',
    extras: [{
        text: '[]',
        title: 'Reset',
        klass: 'zoom-reset',
        onClick: function(){
            this._map.setView(settings.center, settings.zoom);
        },
        onDisabled: function(btn, className) {
            // disable our new reset button if center & zoom is close to our original center & zoom
            L.DomUtil.removeClass(btn, className);
            var dist = this._map.getCenter().distanceTo(settings.center);
            if (this._map._zoom === settings.zoom && dist <= 160934) {
                L.DomUtil.addClass(btn, className);
            }
        }
    }],
    extraMapDisabledEvents: ['moveend']
});

// add to map
zoomControls.addTo(map)
```

### Don't forget to add your CSS styles...