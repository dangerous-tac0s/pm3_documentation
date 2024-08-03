---
MIFARE Classic 1k 4-byte UID Implant Options
---

```mermaid
  flowchart TD;
      A[Form Factor]--> B[X-Series] & C[Flex];

      B --> B1[Magic MIFARE Only] & B2[Magic MIFARE + t5577]
      B1 --> B1.1{xM1}
      B1.1 -- version --> B1.1a[gen1a] & B1.1b[gen2]
      B2 --> B2.1{xMagic}
      B2.1 -- version --> B2.1a[gen1a]

      C -- format --> C1[Narrow]
      C1 --> C1.1[Magic MIFARE Only]
      C1.1 --> C1.1a{flexM1} & C1.1b{flexUG4}
      C1.1a -- version --> C1.1a_1[gen1a] & C1.1a_2[gen2]
      C1.1b -- version --> C1.1b_1[gen4]
```

#### Further Reading
- [Flex Formats](FLEX_FORMATS.md)
- [Magic MIFARE Version Information](MAGIC_MIFARE_VERSIONS.md)
- [t5577 Information](T5577.md)

#### Product Links
- [xM1](dngr.us/xm1)
- [xMagic](dngr.us/xmagic)
- [flexM1](dngr.us/flexm1)
- [flexUG4](dngr.us/flexug4)
