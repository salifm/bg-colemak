# Инсталиране в Linux

Превод: [english](LINUX.md), [中文](LINUX.zh-CN.md), [español](LINUX.es.md), [العربية](LINUX.ar.md), [português](LINUX.pt.md), [русский](LINUX.ru.md), [bahasa](LINUX.id.md), [türkçe](LINUX.tr.md), [esperanto](LINUX.eo.md)

---

Не съм експерт в инсталирането на клавиатурни подредби, тези инструкции може да не работят за всички потребители на Linux.

## Следвайте тези инструкции

**1.** Първо архивирайте някои файлове, като изпълните тези команди:

```bash
cp /usr/share/X11/xkb/symbols/bg /usr/share/X11/xkb/symbols/bg.old
cp /usr/share/X11/xkb/rules/evdev.xml /usr/share/X11/xkb/rules/evdev.xml.old
```

Ако получите грешка, първо изпълнете тази команда: `su root`, след това опитайте да изпълните командите отново или заменете `cp` със `sudo cp`.

**2.** Отворете файла `/usr/share/X11/xkb/symbols/bg` и добавете следния текстов блок в края на файла:

```
// homepage: salif.github.io/colemak-bg
// version: 1
partial alphanumeric_keys
xkb_symbols "colemak_bg" {

  include "bg(bds)"

  name[Group1]="Bulgarian (Colemak)";

  key <TLDE> {[ semicolon,         colon,             grave,          asciitilde ]};
  key <AE01> {[ 1,                 exclam      ]};
  key <AE02> {[ 2,                 at          ]};
  key <AE03> {[ 3,                 numbersign  ]};
  key <AE04> {[ 4,                 dollar      ]};
  key <AE05> {[ 5,                 percent     ]};
  key <AE06> {[ 6,                 asciicircum ]};
  key <AE07> {[ 7,                 ampersand   ]};
  key <AE08> {[ 8,                 asterisk    ]};
  key <AE09> {[ 9,                 parenleft   ]};
  key <AE10> {[ 0,                 parenright  ]};
  key <AE11> {[ minus,             underscore  ]};
  key <AE12> {[ equal,             plus        ]};

  key <AD01> {[ Cyrillic_ya,       Cyrillic_YA     ]};
  key <AD02> {[ Cyrillic_sha,      Cyrillic_SHA    ]};
  key <AD03> {[ Cyrillic_ef,       Cyrillic_EF     ]};
  key <AD04> {[ Cyrillic_pe,       Cyrillic_PE     ]};
  key <AD05> {[ Cyrillic_ghe,      Cyrillic_GHE    ]};
  key <AD06> {[ Cyrillic_zhe,      Cyrillic_ZHE    ]};
  key <AD07> {[ Cyrillic_el,       Cyrillic_EL     ]};
  key <AD08> {[ Cyrillic_u,        Cyrillic_U      ]};
  key <AD09> {[ Cyrillic_shorti,   Cyrillic_SHORTI ]};
  key <AD10> {[ Cyrillic_shcha,    Cyrillic_SHCHA  ]};
  key <AD11> {[ Cyrillic_yu,       Cyrillic_YU,       bracketleft,       braceleft  ]};
  key <AD12> {[ Cyrillic_softsign, U045D,             bracketright,      braceright ]};

  key <AC01> {[ Cyrillic_a,        Cyrillic_A  ]};
  key <AC02> {[ Cyrillic_er,       Cyrillic_ER ]};
  key <AC03> {[ Cyrillic_es,       Cyrillic_ES ]};
  key <AC04> {[ Cyrillic_te,       Cyrillic_TE ]};
  key <AC05> {[ Cyrillic_de,       Cyrillic_DE ]};
  key <AC06> {[ Cyrillic_ha,       Cyrillic_HA ]};
  key <AC07> {[ Cyrillic_en,       Cyrillic_EN ]};
  key <AC08> {[ Cyrillic_ie,       Cyrillic_IE ]};
  key <AC09> {[ Cyrillic_i,        Cyrillic_I  ]};
  key <AC10> {[ Cyrillic_o,        Cyrillic_O  ]};
  key <AC11> {[ Cyrillic_hardsign, Cyrillic_HARDSIGN,   apostrophe, quotedbl ]};
  key <BKSL> {[ doublelowquotemark,leftdoublequotemark, backslash,  bar      ]};

  key <LSGT> {[ U045D,             U040D        ]};
  key <AB01> {[ Cyrillic_ze,       Cyrillic_ZE  ]};
  key <AB02> {[ Cyrillic_che,      Cyrillic_CHE ]};
  key <AB03> {[ Cyrillic_tse,      Cyrillic_TSE ]};
  key <AB04> {[ Cyrillic_ve,       Cyrillic_VE  ]};
  key <AB05> {[ Cyrillic_be,       Cyrillic_BE  ]};
  key <AB06> {[ Cyrillic_ka,       Cyrillic_KA  ]};
  key <AB07> {[ Cyrillic_em,       Cyrillic_EM  ]};
  key <AB08> {[ comma,             less         ]};
  key <AB09> {[ period,            greater      ]};
  key <AB10> {[ slash,             question     ]};

  include "level3(ralt_switch)"
};
```

**3.** Отворете файла `/usr/share/X11/xkb/rules/evdev.xml` и вмъкнете следния текстов блок след варианта `Bulgarian (enhanced)`:

```xml
<variant>
  <configItem>
    <name>colemak_bg</name>
    <description>Bulgarian (Colemak)</description>
  </configItem>
</variant>
```

**4.** След това добавете `Bulgarian (Colemak)` чрез настройките на вашата работна среда.

## Деинсталиране

За да деинсталирате, възстановете старите файлове или отменете всичко, което сте направили:

```bash
mv /usr/share/X11/xkb/symbols/bg.old /usr/share/X11/xkb/symbols/bg
mv /usr/share/X11/xkb/rules/evdev.xml.old /usr/share/X11/xkb/rules/evdev.xml
```

## Актуализиране

Деинсталирайте старата версия и инсталирайте новата версия.

Промените, които правите във файловете в директорията `/usr/share/X11/xkb`, ще бъдат загубени, когато пакетът, притежаващ тази директория, бъде актуализиран, например в Arch Linux този пакет се нарича `xkeyboard-config`. Трябва или да правите същите промени всеки път, когато актуализирате този пакет, или да изключите актуализациите за този пакет. Също така имате възможност да направите персонализиран пакет, който съдържа тези промени и замества оригиналния пакет.

---

[← Назад](./README.bg.md)
