# Weather Icons Light

## Weather Themed Icons and CSS

Weather Icons Lite are weather themed icons, ready to be dropped right into [Bootstrap](http://www.getbootstrap.com), or any project that needs high quality weather based icons!

Get started at [http://weathericons.io](http://weathericons.io)!

![Icon Preview](http://i.imgur.com/XmZW2q3.png)

## Basic Usage

The icons are displayed by using an `i` element and adding the base class `wi` and then the icon class you want, such as `day-sunny`. This then looks like `<i class="wi wi-day-sunny"></i>`.

To add a modifier, include the class you want after the icon name, which looks like `<i class="wi wi-day-sunny wi-flip-vertical"></i>`. You can flip, rotate, or add a fixed width. See it all at [http://weathericons.io](http://weathericons.io).

## API Usage

This set includes companion CSS files for popular weather service API. Presently there are mappings for Darksky, Open Weather Map and Weather Underground.

## Use in node-red dashboards

Create a new static directory within your `.node-red` directory from which you can serve the CSS and Font files, for example 'public'.  
Git clone this repo into your newly created static directory;

    cd && cd .node-red/public
    git clone https://github.com/Paul-Reed/weather-icons-lite.git

Edit your node-red settings file, usually `nano /home/pi/.node-red/settings.js` as follows;

Firstly, edit httpStatic to read your static folder  
`httpStatic: '/home/pi/.node-red/public',`
and also if you havent already done so, httpAdminRoot must also be used to make the editor UI available at a path other than /. So for example if you changed the setting to `httpAdminRoot: '/admin',` then instead of your editor being accessed at the URL `192.168.168.13:1880/` you would use `192.168.168.13:1880/admin`

Then stop and restart node-red

An example of using the icons in a node-red ui 'template node', would be;

    <link rel="stylesheet" href="/weather-icons-lite/css/weather-icons-lite.min.css">
    <div style="display: flex;height: 100%;justify-content: center;align-items: center;">
    <i class="fa-4x wi wi-wu-{{msg.payload}}"></i>
    </div> 

The class shown will retreive the icon as called in the msg payload, display it at x4 size (fa-4x), and use the Wunderground.com icon mapping (wi-wu).

The `<div>` will centre the icon in the dashboard panel.

There is an [example node-red flow](/example/example.txt) to get you started, once you have completed the above.

## Contributing
If you feel so inclined to add icon ideas, icon art, or other fixes/changes to how the package works, feel free to help!

## Credit
The icon designs are originally by [Lukas Bischoff](http://www.twitter.com/artill). Icon art for v1.1 forward, HTML, Less, and CSS are by [Erik)](http://www.helloerik.com).
Weather-icons-lite and Node-red compatibility changes by Paul Reed.

## Licensing

* Weather Icons licensed under [SIL OFL 1.1](http://scripts.sil.org/OFL)
* Code licensed under [MIT License](http://opensource.org/licenses/mit-license.html)
* Documentation licensed under [CC BY 3.0](http://creativecommons.org/licenses/by/3.0)
