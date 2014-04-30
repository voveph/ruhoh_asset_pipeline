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
