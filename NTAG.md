# NTAG Information

> [!NOTE]
> This is not a complete overview. The focus is on the most relevant information to people interested in implants.

| Name         | UID Size   | NDEF Capacity (in bytes)    | Data Sharing | Clone-able   | Power Harvesting |
| :----------: | :--------: | :-------------------------: | :----------: | :----------: | :--------------: |
| 210          | 7-bytes    | 48                          | Yes          | Yes          | No               |
| 212          | 7-bytes    | 128                         | Yes          | Yes          | No               |
| 213          | 7-bytes    | 144                         | Yes          | Yes          | No               |
| 215          | 7-bytes    | 504                         | Yes          | Yes          | No               |
| 216          | 7-bytes    | 888                         | Yes          | Yes          | No               |
| I2C          | 7-bytes    | 888*                        | Yes          | Yes          | Yes              |

#### NDEF/Data Sharing

*I2C NDEF Capactiy: It's actually longer but there are no readily available applications that can use the rest of the available memory.

#### Cloning Notes
These can only be cloned to a flexUG4.

#### Power Harvesting
This is what we use to drive LEDs.

---
### Back:
- [NTAG Options](NTAG_OPTIONS.md)
