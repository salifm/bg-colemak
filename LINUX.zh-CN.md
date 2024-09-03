# 在 Linux 上安装

翻译： [english](LINUX.md), [български](LINUX.bg.md), [español](LINUX.es.md), [العربية](LINUX.ar.md), [português](LINUX.pt.md), [русский](LINUX.ru.md), [bahasa](LINUX.id.md), [türkçe](LINUX.tr.md), [esperanto](LINUX.eo.md)

---

我不是安装键盘布局的专家，这些说明可能不适用于所有 Linux 用户.

## 请遵循这些说明

**1.** 首先，通过运行这些命令备份一些文件:

```bash
cp /usr/share/X11/xkb/symbols/bg /usr/share/X11/xkb/symbols/bg.old
cp /usr/share/X11/xkb/rules/evdev.xml /usr/share/X11/xkb/rules/evdev.xml.old
```

如果出现错误，请首先运行以下命令： `su root`, 然后尝试再次运行命令，或将“cp”替换为“sudo cp”.

**2.** 打开文件 `/usr/share/X11/xkb/symbols/bg` 并将以下文本块附加到文件末尾:

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

**3.** 打开文件 `/usr/share/X11/xkb/rules/evdev.xml` 并在变体后面插入以下文本块 `Bulgarian (enhanced)`:

```xml
<variant>
  <configItem>
    <name>colemak_bg</name>
    <description>Bulgarian (Colemak)</description>
  </configItem>
</variant>
```

**4.** 然后加 `Bulgarian (Colemak)` 通过桌面环境的设置.

## 正在卸载

要卸载，请恢复旧文件或撤消您所做的一切:

```bash
mv /usr/share/X11/xkb/symbols/bg.old /usr/share/X11/xkb/symbols/bg
mv /usr/share/X11/xkb/rules/evdev.xml.old /usr/share/X11/xkb/rules/evdev.xml
```

## 正在更新

卸载旧版本并安装新版本.

当拥有该目录的软件包更新时，您对“/usr/share/X11/xkb”目录中的文件所做的更改将会丢失，例如在 Arch Linux 上，该软件包称为“xkeyboard-config”。您必须在每次更新此软件包时进行相同的更改，或者关闭此软件包的更新。您还可以选择制作包含这些更改的自定义包并替换原始包.

---

[← 返回](./README.zh-CN.md)
