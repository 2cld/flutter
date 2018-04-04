Flutter smoke dev maps
======================

========================
Smoke Test App with maps
========================

maps smoke app
--------------

Screencasts
-----------

#. tc74_ Create nomnom::

    flutter create nomnom
    flutter run

#. tc87_ Codebase clear comments lib/main.dart and change name on line 13
#. tc188_ Remove boilderplate layout and add "Hello World"::

      body: new Center( child: new Text('hello world') ),

#. tc211_ Take out _incrementCounter
#. tc229_ Create dummy test data for list view::

      List<String> _places = <String>[];

      @override
      initState() {
        super.initState();
        _places = new List.generate(100, (i) => 'Restauant $i');

#. tc324_ Put list in view::

      body: new Center( 
        child: new ListView(
          children: _places.map((place) => Text (place)).toList(),
        )),

#. tc401_ Add google places API::

    cp ../src/places.dart ./lib/
    cp ../src/key.dart ./lib/

#. tc519_ Open pubspec.yaml add to line 8::

      http: ^0.11.3

#. tc586_ Run command line::

      dart lib/places.dart

#. tc628_ Parse json in a nice way (code is commented out in places.dart file)into streams.

#. tc761_ Return stream to flutter app by using::

      Future<Stream<Place>>

#. tc800_ In file lib/main.dart make function::

    import 'places.dart';
    ...
      List<Place> _places = <Place>[];
    ...
    @override
    initState() {
      super.initState();
      listenForPlaces();
    }
    ...
    listenForPlaces() async {
      var stream = await getPlaces(33.9850, -118.4695);
      stream.listen( (place) => 
        setState[ () => _places.add(place))
      );
    }
    ...
        children: _places.map((place) => new Text(place.name)).toList(),
    ...

#. tc984_ Should get a 'non-pretty' list

#. tc1000_ Make it pretty

#. tc1009_ In main.dart add new widget PlaceWidget::

    class PlaceWidget extends StatelessWidget {
      final Place _place;
      PlaceWidget(this._place);
      @override
      Widget build(BuildContext context) {
        // TODO: implement build
        return new ListTile(
          title: new Text(_place.name),
        ); // ListTile
      }
    }

#. tc1048_ Override the build widget::

    children: _places.map((place) => new PlaceWidget(place)).toList(),

#. tc1116_ Add subtitle::

    class PlaceWidget extends StatelessWidget {
      final Place _place;
      PlaceWidget(this._place);
      @override
      Widget build(BuildContext context) {
        // TODO: implement build
        return new ListTile(
          title: new Text(_place.name),
          subtitle: new Text(_place.address),
        ); // ListTile
      }
    }

#. tc1138_ Add leading::

    class PlaceWidget extends StatelessWidget {
      final Place _place;
      PlaceWidget(this._place);
      @override
      Widget build(BuildContext context) {
        // TODO: implement build
        return new ListTile(
          leading: new CircleAvatar(
            child: new Text(_place.rating.toString()),
            backgroundColor: Colors.green,
          ), // CircleAvatar
          title: new Text(_place.name),
          subtitle: new Text(_place.address),
        ); // ListTile
      }
    }

#. tc1197: Update backgroundColor based on Rating using interpolation::

    class PlaceWidget extends StatelessWidget {
      final Place _place;
      PlaceWidget(this._place);

      Color getColor(double rating) {
        return Color.lerp(Colors.red, Colors.green, rating/5);
      }
      
      @override
      Widget build(BuildContext context) {
        // TODO: implement build
        return new ListTile(
          leading: new CircleAvatar(
            child: new Text(_place.rating.toString()),
            backgroundColor: getColor(_place.rating),
          ), // CircleAvatar
          title: new Text(_place.name),
          subtitle: new Text(_place.address),
        ); // ListTile
      }
    }

#. tc1293_ Put in Swipe Right to Like, Left to Remove using Dismissible::

    class PlaceWidget extends StatelessWidget {
      final Place _place;
      PlaceWidget(this._place);

      Color getColor(double rating) {
        return Color.lerp(Colors.red, Colors.green, rating/5);
      }
      
      @override
      Widget build(BuildContext context) {
        // TODO: implement build
        return new Dismissible(
          key: new Key(_place.name),
          background: new Container(color: Colors.green),
          secondaryBackground: new Container(color: Colors.red),
          leading: new CircleAvatar(
            child: new Text(_place.rating.toString()),
            backgroundColor: getColor(_place.rating),
          ), // CircleAvatar
          title: new Text(_place.name),
          subtitle: new Text(_place.address),
        ); // ListTile
      }
    }

#. tc1415_ Add text to swipe feedback::

    onDismissed: (direction) {
      direction == DismissDirection.endToStart ? Scaffold.of(context).showSnackBar(
        new SnackBar(content: new Text('I Like'))) : print('No Like');
    },

#. tc1609_ Show some of the render debugging performance.

.. _tc74: https://youtu.be/iflV0D0d1zQ?t=74
.. _tc87: https://youtu.be/iflV0D0d1zQ?t=87
.. _tc188: https://youtu.be/iflV0D0d1zQ?t=188
.. _tc211: https://youtu.be/iflV0D0d1zQ?t=211
.. _tc229: https://youtu.be/iflV0D0d1zQ?t=229
.. _tc324: https://youtu.be/iflV0D0d1zQ?t=324
.. _tc401: https://youtu.be/iflV0D0d1zQ?t=401
.. _tc519: https://youtu.be/iflV0D0d1zQ?t=519
.. _tc586: https://youtu.be/iflV0D0d1zQ?t=586
.. _tc628: https://youtu.be/iflV0D0d1zQ?t=628
.. _tc761: https://youtu.be/iflV0D0d1zQ?t=761
.. _tc800: https://youtu.be/iflV0D0d1zQ?t=800
.. _tc984: https://youtu.be/iflV0D0d1zQ?t=984
.. _tc1000: https://youtu.be/iflV0D0d1zQ?t=1000
.. _tc1009: https://youtu.be/iflV0D0d1zQ?t=1009
.. _tc1048: https://youtu.be/iflV0D0d1zQ?t=1048
.. _tc1116: https://youtu.be/iflV0D0d1zQ?t=1116
.. _tc1138: https://youtu.be/iflV0D0d1zQ?t=1138
.. _tc1197: https://youtu.be/iflV0D0d1zQ?t=1197
.. _tc1293: https://youtu.be/iflV0D0d1zQ?t=1293
.. _tc1415: https://youtu.be/iflV0D0d1zQ?t=1415
.. _tc1609: https://youtu.be/iflV0D0d1zQ?t=1609


.. raw:: html

    <div style="position: relative; padding-bottom: 5.25%; height: 0; overflow: hidden; max-width: 100%; height: auto;">
    <iframe width="1694" height="712" src="https://www.youtube.com/embed/iflV0D0d1zQ" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
    </div>

==========
References
==========

 + Tutorial via "Let's live code in Flutter (DartConf 2018)" see youtube-flutter-maps-tutorial_
 + Github source for tutorial youtube-flutter-maps-github_ 

.. _youtube-flutter-maps-tutorial: https://youtu.be/iflV0D0d1zQ
.. _youtube-flutter-maps-github: https://github.com/mjohnsullivan/nomnom
