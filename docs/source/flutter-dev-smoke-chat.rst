Flutter smoke dev chat
======================

========================
Smoke Test App with chat
========================

chat smoke app
--------------

Screencasts
-----------


#. tc159_ Demo the Secret Sauce

#. tc461_ Explains main.dart structure

#. tc591_ Widgets are immutable and ephemeral

#. tc639_ class MyApp Explained and hotload shown

#. tc709_ class ChatScreenState explain how to send messages in _buildTextComposer add new Flexible a TextField::

              new Flexible(
                child: new TextField(
                  controller: _textController,
                  onSubmitted: _handleSubmitted,
                  onChanged: _handleMessageChanged,
                  decoration:
                      new InputDecoration.collapsed(hintText: 'Send a message'),
                ),
              ),

#. tc812_ go handle submitted function::

        void _handleSubmitted(String text) {
            _textController.clear();
            _addMessage(name: _name, text: text);
            });
        }

#. tc855_ update the view to redraw sent messages::

        var message = new ChatMessage(
                sender: sender,
                text: text,
                imageUrl: imageUrl,
                textOverlay: textOverlay,
                animationController: animationController);
            setState(() {
            _messages.insert(0, message);
            });

#. tc915_ Make pretty via a theme::

        class MyApp extends StatelessWidget {
            @override
            Widget build(BuildContext context) {
                return new MaterialApp(
                title: 'Memechat',
                theme: defaultTargetPlatform == TargetPlatform.iOS
                    ? kIOSTheme
                    : kDefaultTheme,
                home: new ChatScreen(),
                );
            }
        }

#. tc1008_ Add some animationController::

        void _addMessage(
            {String name,
            String text,
            String imageUrl,
            String textOverlay,
            String senderImageUrl}) {
            var animationController = new AnimationController(
            duration: new Duration(milliseconds: 700),
            vsync: this,
            );
        ....
        also added SizeTransistion in ChatMessageListItem

#. tc1088_ Bug in code.. they go fix it (simple typo but the point was to see debug).

#. tc1161_ Add plugin dependencies via pubspec.yaml

#. tc1239_ Add Google Sign-in plugin in main.dart ::

    void _handleSubmitted(String text) {
        _textController.clear();
        _googleSignIn.signIn().then((user) {
        var message = {
            'sender': {'name': user.displayName, 'imageUrl': user.photoUrl},
            'text': text,
        };
        _messagesReference.push().set(message);
        });
    }
    ..... display profile photo
        children: [
                new Container(
                    margin: const EdgeInsets.only(right: 16.0),
                    child: new GoogleUserCircleAvatar(message.sender.imageUrl),
                ),


#. tc1330_ Add Firebase Database::

        @override
        void initState() {
            super.initState();
            _googleSignIn.signInSilently();
            FirebaseAuth.instance.signInAnonymously().then((user) {
            _messagesReference.onChildAdded.listen((Event event) {
                var val = event.snapshot.value;
                _addMessage(
                    name: val['sender']['name'],
                    senderImageUrl: val['sender']['imageUrl'],
                    text: val['text'],
                    imageUrl: val['imageUrl'],
                    textOverlay: val['textOverlay']);
            });
            });
        }
        .....
        void _handleSubmitted(String text) {
            _textController.clear();
            _googleSignIn.signIn().then((user) {
            var message = {
                'sender': {'name': user.displayName, 'imageUrl': user.photoUrl},
                'text': text,
            };
            _messagesReference.push().set(message);
            });
        }

#. tc1482_ Add send images via Image Picker and Storage.

#. tc1504_ Add icon button::

                child: new IconButton(
                  icon: new Icon(Icons.photo),
                  onPressed: _handlePhotoButtonPressed,
                ),
              ),

#. tc1525_ Add _handlePhotoButtonPressed function::

        Future<Null> _handlePhotoButtonPressed() async {
            var account = await _googleSignIn.signIn();
            var imageFile = await ImagePicker.pickImage();
            var random = new Random().nextInt(10000);
            var ref = FirebaseStorage.instance.ref().child('image_$random.jpg');
            var uploadTask = ref.put(imageFile);
            var textOverlay =
                await Navigator.push(context, new TypeMemeRoute(imageFile));
            if (textOverlay == null) return;
            var downloadUrl = (await uploadTask.future).downloadUrl;
            var message = {
            'sender': {'name': account.displayName, 'imageUrl': account.photoUrl},
            'imageUrl': downloadUrl.toString(),
            'textOverlay': textOverlay,
            };
            _messagesReference.push().set(message);
        }

#. tc1656_ Add text overlay (which was what the Navigator textOverlay above).



.. _tc159: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=159
.. _tc461: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=461
.. _tc591: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=591
.. _tc639: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=639
.. _tc709: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=709
.. _tc812: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=812
.. _tc855: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=855
.. _tc915: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=915
.. _tc1008: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=1008
.. _tc1088: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=1088
.. _tc1161: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=1161
.. _tc1239: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=1239
.. _tc1330: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=1330
.. _tc1482: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=1482
.. _tc1504: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=1504
.. _tc1525: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=1525
.. _tc1656: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_&t=1656


.. raw:: html

    <div style="position: relative; padding-bottom: 5.25%; height: 0; overflow: hidden; max-width: 100%; height: auto;">
    <iframe width="887" height="507" src="https://www.youtube.com/embed/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
    </div>

==========
References
==========

 + Tutorial via GoogleIO-17 "Single Codebase, Two Apps with Flutter and Firebase" see youtube-flutter-chat-tutorial_
 + Github source for tutorial youtube-flutter-chat-github_ 

.. _youtube-flutter-chat-tutorial: https://youtu.be/w2TcYP8qiRI?list=PLlpxjI4sVd-zZ1jpJHJMSHGiWInsvwwf_
.. _youtube-flutter-chat-github: https://github.com/efortuna/memechat
