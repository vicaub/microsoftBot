# Testing the Microsoft bot framework

A sample bot to renders several types of cards as attachments.
You can use this code with the Bot Framework Emulator locally or deploy it on Azure and test it with your favorite app.

### Prerequisites

The minimum prerequisites to run this sample are:
* Latest Node.js with NPM. Download it from [here](https://nodejs.org/en/download/).
* The Bot Framework Emulator. To install the Bot Framework Emulator, download it from [here](https://emulator.botframework.com/).

### Using the Bot Framework Emulator

https://github.com/microsoft/botframework-emulator/wiki/Getting-Started

### Deploying on Azure

https://azuredeploy.net

### Code Highlights

Many messaging channels provide the ability to attach richer objects. The Bot Framework has the ability to render rich cards as attachments. There are several types of cards supported: Hero Card, Thumbnail Card, Receipt Card, Sign-In Card, Animation Card, Video Card and Audio Card. Once the desired Card type is selected, it is mapped into an `Attachment` data structure. Check out the key code located in [app.js](app.js#L29-L35) where a card is attached to the constructed message.

```
JavaScript
function (session, results) {

    // create the card based on selection
    var selectedCardName = results.response.entity;
    var card = createCard(selectedCardName, session);

    // attach the card to the reply message
    var msg = new builder.Message(session).addAttachment(card);
    session.send(msg);
}
```
