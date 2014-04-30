This repository describes an issue with Ruhoh v2.6 (commit 3c4a80e) and the asset pipeline.

To reproduce the problem, please run:

    bundle install
    ruhoh server

As you can see, you get a browser alert and a blue background when visiting [http://0.0.0.0:9292](http://0.0.0.0:9292).

Now hit `Ctrl+C` and run:

    ruhoh compile
    cd compiled
    python -m SimpleHTTPServer

Visit [http://0.0.0.0:8000](http://0.0.0.0:8000). This time, you do not get the browser alert and the blue background, as `compiled/assets/stylesheets/screen.css` and `compiled/assets/javascripts/script.js` have not been generated during the compilation step.

## Update: FIXED

Per [Ruhoh issue #260](https://github.com/ruhoh/ruhoh.rb/issues/260), Sprockets requires the use of a vanilla CSS/JS to function properly. See the [last commit](https://github.com/voveph/ruhoh_asset_pipeline/commit/2b71bea38ecf10375de11fa121c17bf3f972aa8e) for the required changes.
