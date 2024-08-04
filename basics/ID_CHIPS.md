# Identifying Chips with a Proxmark 3 Easy

When someone has an existing card/badge/FOB/etc that they want an implant to replace, we need to find out what specific chip it is before we can determine if:
1. We have a compatible implant or, if not, can it be converted to an implant
2. Whether their transponder can be cloned or the relevant implant will have to be enrolled in the system

For our purposes, there are two [^overview] main categories of contactless transponders:
- High frequency aka 13.56 MHz aka NFC [^nfc]
- Low frequency aka 125 kHz [^pet] aka RFID [^rfid]

### Overview
- Using a smartphone
- Using a Proxmark

### Next:
- [High Frequency](../chips/HIGH_FREQUENCY_CHIPS.md)
- [Low Frequency](../chips/LOW_FREQUENCY_CHIPS.md)

---
### Back to:
- [Home](../README.md)

[^overview]: Technically, there is another: UHF. This operates in the 800-900 MHz range but doesn't place nice with water--which the human body is mostly made of.
[^nfc]: There are so many ways to categorize this. Technically, MIFARE existed before NFC was formalized. It's compliant with some ISO 14443 standards but isn't [NFC Forum](https://nfc-forum.org/) compliant. The Forum is technically the body that formalized NFC.
[^pet]: Pet chips operate at 134 kHz--still low frequency but it is a more niche technology. Our [xBT](https://dngr.us/xbt) is one of these.
[^rfid]: Technically, RFID is an umbrella term that encompasses contactless transponders. You'll find the convention used in the implant world typically refers to 125 kHz transponders.
