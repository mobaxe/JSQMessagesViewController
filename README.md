![JSQMessagesViewController banner](https://raw.githubusercontent.com/jessesquires/JSQMessagesViewController/develop/Assets/jsq_messages_banner.png)

[![Build Status](https://secure.travis-ci.org/jessesquires/JSQMessagesViewController.svg)](http://travis-ci.org/jessesquires/JSQMessagesViewController) [![Version Status](http://img.shields.io/cocoapods/v/JSQMessagesViewController.png)][docsLink] [![license MIT](http://img.shields.io/badge/license-MIT-orange.png)][mitLink]

![Screenshot0][img0] &nbsp;&nbsp; ![Screenshot1][img1] &nbsp;&nbsp; 

![Screenshot2][img2] &nbsp;&nbsp; ![Screenshot3][img3]

> More screenshots available at [CocoaControls](https://www.cocoacontrols.com/controls/jsqmessagesviewcontroller)

## Features

See the [website](http://www.jessesquires.com/JSQMessagesViewController/) for the list of features.

## Dependencies

* [JSQSystemSoundPlayer][playerLink]
 

## Requirements

* iOS 7.0+
* ARC

*Need support for iOS 6? [You shouldn't](http://www.macrumors.com/2014/11/11/ios8-56-percent-adoption/). But, there's a branch for that!*
````
git checkout iOS6_support_stable
````

*Note: the `iOS6_support_stable` branch does not include many of the latest hip and fancy features or fixes*

## Installation

````ruby
# For latest release in cocoapods
pod 'JSQMessagesViewController'  

# Feeling adventurous? Get the latest on develop
pod 'JSQMessagesViewController', :git => 'https://github.com/jessesquires/JSQMessagesViewController.git', :branch => 'develop'

# For version 5.3.2
pod 'JSQMessagesViewController', :git => 'https://github.com/jessesquires/JSQMessagesViewController', :branch => 'version_5.3.2_patch'

# For iOS 6 support
pod 'JSMessagesViewController', :git => 'https://github.com/jessesquires/JSQMessagesViewController.git', :branch => 'iOS6_support_stable'
````

Otherwise, drag the `JSQMessagesViewController/` folder to your project and install [`JSQSystemSoundPlayer`][playerLink].

>**NOTE:**
>
>This repo was formerly named `MessagesTableViewController`.
>
>And this pod was formerly named `JSMessagesViewController`.

## Getting Started

````objective-c
#import <JSQMessagesViewController/JSQMessages.h>    // import all the things
````

>Read the [blog post](http://www.jessesquires.com/introducing-jsqmessagesvc-6-0/) about the 6.0 release!

* **Demo Project**
  * There's a sweet demo project: `JSQMessages.xcworkspace`.
  * Run `pod install` first.

* **Message Model**
  * Your message model objects should conform to the `JSQMessageData` protocol.
  * However, you may use the provided `JSQMessage` class.
   
* **Media Attachment Model**
  * Your media attachment model objects should conform to the `JSQMessageMediaData` protocol.
  * However, you may use the provided classes: `JSQPhotoMediaItem`, `JSQLocationMediaItem`, `JSQVideoMediaItem`.
  * Creating your own custom media items is easy! Simply follow the pattern used by the built-in media types.
  * Also see `JSQMessagesMediaViewBubbleImageMasker` for masking your custom media views as message bubbles.

* **Avatar Model**
  * Your avatar model objects should conform to the `JSQMessageAvatarImageDataSource` protocol.
  * However, you may use the provided `JSQMessagesAvatarImage` class.
  * Also see `JSQMessagesAvatarImageFactory` for easily generating custom avatars.

* **Message Bubble Model**
  * Your message bubble model objects should conform to the `JSQMessageBubbleImageDataSource` protocol.
  * However, you may use the provided `JSQMessagesBubbleImage` class.
  * Also see `JSQMessagesBubbleImageFactory` and `UIImage+JSQMessages.h` for easily generating custom bubbles.

* **View Controller**
  * Subclass `JSQMessagesViewController`.
  * Implement the required methods in the `JSQMessagesCollectionViewDataSource` protocol.
  * Implement the required methods in the `JSQMessagesCollectionViewDelegateFlowLayout` protocol.
  * Set your `senderId` and `senderDisplayName`. These properties correspond to the methods found in `JSQMessageData` and determine which messages are incoming or outgoing.

* **Customizing**
  * The demo project is well-commented. Please use this as a guide.

## Quick Tips

*Springy bubbles?*
````objective-c
- (void)viewDidAppear:(BOOL)animated
{
    [super viewDidAppear:animated];
    self.collectionView.collectionViewLayout.springinessEnabled = YES;
}
````

*Remove avatars?*
````objective-c
- (void)viewDidLoad
{
    [super viewDidLoad];
    self.collectionView.collectionViewLayout.incomingAvatarViewSize = CGSizeZero;
    self.collectionView.collectionViewLayout.outgoingAvatarViewSize = CGSizeZero;
}

- (id<JSQMessageAvatarImageDataSource>)collectionView:(JSQMessagesCollectionView *)collectionView avatarImageDataForItemAtIndexPath:(NSIndexPath *)indexPath
{
    return nil;
}
````

*Customize your cells*
````objective-c
- (UICollectionViewCell *)collectionView:(JSQMessagesCollectionView *)collectionView cellForItemAtIndexPath:(NSIndexPath *)indexPath
{
    JSQMessagesCollectionViewCell *cell = (JSQMessagesCollectionViewCell *)[super collectionView:collectionView cellForItemAtIndexPath:indexPath];
    
    // Customize the shit out of this cell
    // See the docs for JSQMessagesCollectionViewCell
    
    return cell;
}
````

## Questions & Help

There's [a label](https://github.com/jessesquires/JSQMessagesViewController/labels/questions%20&%20help) for that. Before asking a question, see if it has [already been answered](https://github.com/jessesquires/JSQMessagesViewController/issues?q=label%3A%22questions+%26+help%22+is%3Aclosed).

## Migrating from v5.x to v6.x

If you are upgrading from v5.x to v6.x, see the [6.0 release notes](https://github.com/jessesquires/JSQMessagesViewController/releases/tag/6.0.0) for details about API changes.

## Documentation

Read the fucking docs, [available here][docsLink] via [@CocoaDocs](https://twitter.com/CocoaDocs).

## Contribute

Please follow these sweet [contribution guidelines](https://github.com/jessesquires/HowToContribute).

## Donate

Support the development of this **free**, open-source library!

>*Donations made via [Square Cash](https://square.com/cash)*

><h4><a href="mailto:jesse.squires.developer@gmail.com?cc=cash@square.com&subject=$5&body=Thanks for developing JSQMessagesViewController!">Send $5</a> <em>Just saying thanks. Here's a coffee!</em></h4>
<h4><a href="mailto:jesse.squires.developer@gmail.com?cc=cash@square.com&subject=$10&body=Thanks for developing JSQMessagesViewController!">Send $10</a> <em>This library is great. Lunch is on me!</em></h4>
<h4><a href="mailto:jesse.squires.developer@gmail.com?cc=cash@square.com&subject=$25&body=Thanks for developing JSQMessagesViewController!">Send $25</a> <em>This totally saved me time. Go get a nice dinner!</em></h4>
<h4><a href="mailto:jesse.squires.developer@gmail.com?cc=cash@square.com&subject=$50&body=Thanks for developing JSQMessagesViewController!">Send $50</a> <em>I love this library. I want new features!</em></h4>
<h4><a href="mailto:jesse.squires.developer@gmail.com?cc=cash@square.com&subject=$100&body=Thanks for developing JSQMessagesViewController!">Send $100</a> <em>I really want to support this project!</em></h4>
>*You can also send donations via [PayPal](https://www.paypal.com) to jesse.squires.developer@gmail.com*

## Credits

Created by [**@jesse_squires**](https://twitter.com/jesse_squires), a [programming-motherfucker](http://programming-motherfucker.com).

* Assets extracted using [**@0xced**](https://github.com/0xced) / [iOS-Artwork-Extractor](https://github.com/0xced/iOS-Artwork-Extractor).
* Originally inspired by [**@soffes**](http://github.com/soffes) / [SSMessagingViewController](https://github.com/soffes/ssmessagesviewcontroller).
* Many thanks to [**the contributors**](https://github.com/jessesquires/JSQMessagesViewController/graphs/contributors) of this project.

## About

I initially developed this library to use in [Hemoglobe](http://bit.ly/hmglb) for private messages between users.

As it turns out, messaging is something that iOS devs and users really want. Messaging of any kind has turned out to be an increasingly popular mobile app feature in all sorts of contexts and for all sorts of reasons. Thus, I am supporting this project in my free time and have added features way beyond what Hemoglobe ever needed.

Feel free to check out my work at [Hexed Bits](http://bit.ly/0x29A), or read [my blog](http://bit.ly/jsqsf).

## Apps using this library

* [Hemoglobe](http://bit.ly/hemoglobeapp)
* [PocketSuite](https://itunes.apple.com/us/app/pocketsuite/id721795146)
* [ClassDojo](https://itunes.apple.com/us/app/classdojo/id552602056)
* [Schools App](https://itunes.apple.com/us/app/schools-app/id495845755)
* [ChatSecure](https://chatsecure.org)
* [Kytt](https://itunes.apple.com/de/app/kytt-neue-leute-in-der-umgebung/id848959696)
* [Spark Social](https://itunes.apple.com/us/app/spark-social/id823785892)
* [Spabbit](https://itunes.apple.com/us/app/spabbit/id737363908)
* [Elodie](https://itunes.apple.com/app/elodie/id821610181)
* [Instaply](https://itunes.apple.com/us/app/instaply/id558562920)
* [Loopse](https://itunes.apple.com/us/app/loopse-spots-friends-sessions/id704783915)
* [Oxwall Messenger](https://github.com/tochman/OxwallMessenger)
* [FourChat](https://itunes.apple.com/us/app/fourchat/id650833730)
* [vCinity](https://itunes.apple.com/us/app/vcinity-chat-without-internet/id875395391)
* [Quick Text Message](https://itunes.apple.com/us/app/quick-text-message-fast-sms/id583729997)
* [Libraries for developers](https://itunes.apple.com/us/app/libraries-for-developers/id653427112)
* [Buhz|Hyve](http://itunes.apple.com/us/app/buhz-hyve/id818568956)
* [Ringring.io](https://github.com/ringring-io/ringring-ios)
* [gDecide](https://itunes.apple.com/ca/app/gdecide/id716801285)
* [AwesomeChat](https://github.com/relatedcode/AwesomeChat)
* [ParseChat](https://github.com/relatedcode/ParseChat)
* [Jib](http://jibapp.com)
* [Onvolo](https://itunes.apple.com/us/app/onvolo/id869332351)
* [EVCloudKitDao](https://github.com/evermeer/EVCloudKitDao)
* *Your app here*

## License

`JSQMessagesViewController` is released under an [MIT License][mitLink]. See `LICENSE` for details.

>**Copyright &copy; 2014 Jesse Squires.**

*Please provide attribution, it is greatly appreciated.*

[docsLink]:http://cocoadocs.org/docsets/JSQMessagesViewController
[mitLink]:http://opensource.org/licenses/MIT
[playerLink]:https://github.com/jessesquires/JSQSystemSoundPlayer

[img0]:https://raw.githubusercontent.com/jessesquires/JSQMessagesViewController/develop/Screenshots/screenshot0.png
[img1]:https://raw.githubusercontent.com/jessesquires/JSQMessagesViewController/develop/Screenshots/screenshot1.png
[img2]:https://raw.githubusercontent.com/jessesquires/JSQMessagesViewController/develop/Screenshots/screenshot2.png
[img3]:https://raw.githubusercontent.com/jessesquires/JSQMessagesViewController/develop/Screenshots/screenshot3.png
