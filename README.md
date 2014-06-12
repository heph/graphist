# graphist dashboard

This is a replacement viewer for graphite dashboards (http://graphite.mydomain.com/dashboard/)

It loads the dashboard spec from the graphite host and periodically reloads the graphs sequentially
to avoid undue strain on the graphite server. This also eliminates 'flicker' problems when redrawing
a large number of graphs on the same page, as it doesn't remove existing data while attempting to
update the graphs.

## Installation

Clone this repository:
    git clone https://github.com/heph/graphist.git

## Config

Edit the config file, graphist.conf.js, to point to your graphite server and specify a default dashboard:

    var graphite_url    = "http://graphite.example.com";
    var dashboard_name  = "temporary-0"; // default dashboard
    var graph_from      = "-24hours" // draw graphs since this value
    var graph_width     = "25%"; // css style width (4x3 layout default)
    var graph_height    = "33%"; // css style height (4x3 layout default)
    var graph_refresh   = 30000; // refresh in ms 

The default layout works well for a 12 graph dashboard in a 4x3 grid by specifying each graph to be
25% of the page wide and 33% of the page high. The dashboard uses a floating layout, so you can modify
it by adjusting these values. For example, a 1x5 dashboard would look like:

    var graph_width  = "100%";
    var graph_height = "20%";

## Credits

Big thanks to Preston Timmons (prestontimmons@gmail.com) for writing the included Graphite jQuery
plugin. (https://github.com/prestontimmons/graphitejs/)
