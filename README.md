# Weather Icons Light

## Weather Themed Icons and CSS

Weather Icons Lite is a collection of 57 weather themed icons, ready to be dropped right into [Bootstrap](http://www.getbootstrap.com), or any project that needs high quality weather based icons!

![Icon Preview](images/example.PNG)

## Basic Usage

The icons are displayed by using an `i` element and adding the base class `wi` and then the icon class you want, such as `day-sunny`. This then looks like `<i class="wi wi-day-sunny"></i>`.

To add a modifier, include the class you want after the icon name, which looks like `<i class="wi wi-day-sunny wi-flip-vertical"></i>`. You can flip, rotate, or add a fixed width. For further examples of how to apply different effects, see [Font Awsome](http://fontawesome.io/examples/).

## API Usage

This set includes companion CSS files for popular weather service API. Presently there are complete mappings for Darksky, Open Weather Map and Weather Underground.

## Use In node-red Dashboards

Create a new static directory within your `.node-red` directory from which you can serve the CSS and Font files, for example 'public'.  
Git clone this repo into your newly created static directory;

    cd && cd .node-red/public
    git clone https://github.com/Paul-Reed/weather-icons-lite.git

Edit your node-red settings file, usually `nano /home/pi/.node-red/settings.js` as follows;

Firstly, edit httpStatic to enable your static folder  
`httpStatic: '/home/pi/.node-red/public',`
and also if you haven't already done so, httpAdminRoot must also be used to make the editor UI available at a path other than /. So for example if you changed the setting to `httpAdminRoot: '/admin',` then instead of your editor being accessed at the URL `192.168.168.13:1880/` you would use `192.168.168.13:1880/admin`

Then stop and restart node-red

An example of using the icons in a node-red ui 'template node', would be;

    <link rel="stylesheet" href="/weather-icons-lite/css/weather-icons-lite.min.css">
    <div style="display: flex;height: 100%;justify-content: center;align-items: center;">
    <i class="fa-4x wi wi-wu-{{msg.payload}}"></i>
    </div> 

The class shown will retreive the icon as called in the msg payload, display it at x4 size (fa-4x), and use the Wunderground.com icon mapping (wi-wu).

The `<div>` will centre the icon in the dashboard panel.

There is an [example node-red flow](/example/example.txt) to get you started, once you have completed the above.


## Update app.cache

An optional feature, but if you have password protected your dashboard by enabling `httpNodeAuth`, then unless the weather-icons css & font files are added to the node-red dashboard app.cache, you will get repeated requests to re-authorise, due to them being again requested from the server, instead of being cached by the browser.

To add the files to the dashboard app.cache;  
`nano /home/pi/.node-red/node_modules/node-red-dashboard/dist/dashboard.appcache`  
and add the following entries to the the file;  
```
../../../weather-icons-lite/css/weather-icons-lite.min.css
../../../weather-icons-lite/fonts/weather-icons-lite.woff2
../../../weather-icons-lite/fonts/weather-icons-lite.woff
../../../weather-icons-lite/fonts/weather-icons-lite.ttf
../../../weather-icons-lite/fonts/weather-icons-lite.eot
```  
Save, and restart the node-red server to take effect.

**Please note** Updating or re-installing the dashboard node will overwrite these app.cache changes, and will need to be re-applied.

## Credits

The icon designs are originally by [Lukas Bischoff](http://www.twitter.com/artill). Additional Icon art & CSS by [Erik Flowers](http://www.helloerik.com).  
Weather-icons-lite, CSS update & Node-red compatibility changes by me - Paul Reed.

## Licensing

* Weather Icons licensed under [SIL OFL 1.1](http://scripts.sil.org/OFL)
* Code licensed under [MIT License](http://opensource.org/licenses/mit-license.html)
* Documentation licensed under [CC BY 3.0](http://creativecommons.org/licenses/by/3.0)
