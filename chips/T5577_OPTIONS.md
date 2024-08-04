---
T5577 Implant Options
---

```mermaid
  flowchart TD;
      A[Form Factor]--> B[X-Series] & C[Flex];

      B --> B1[t5577 Only] & B2[t5577 + HF/NFC]
      B1 --> B1.1{xEM}
      B2 --> B2.1{NExT} & B2.2{xMagic}
      B2.1 -- HF --> B2.1a[NTAG216]
      B2.2 -- HF --> B2.2a[Magic MIFARE]
      B2.2a -- version --> B2.2a_1[gen1a]

      C -- format --> C1[Disc]
      C1 --> C1.1[t5577 Only]
      C1.1 --> C1.1a{flexEM}
```

---

#### Further Reading
- [Flex Formats](FLEX_FORMATS.md)
- [NTAG Information](NTAG.md)
- [Magic MIFARE Version Information](MAGIC_MIFARE_VERSIONS.md)
- [t5577 Information](T5577.md)

#### Product Links
- [xEM](https://dngr.us/xem)
- [NExT](https://dngr.us/next)
- [xMagic](https://dngr.us/xmagic)
- [flexEM](https://dngr.us/flexem)

---
### Back to:
- [Low Frequency Chips](LOW_FREQUENCY_CHIPS.md)**
- [Home](../README.md)
