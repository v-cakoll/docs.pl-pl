---
title: -nostdlib (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 486539d7abdc3e65847a0bc0e228b1b20a2b2c37
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602690"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (C# opcje kompilatora)

**-nostdlib** uniemożliwia Import biblioteki mscorlib. dll, która definiuje całą przestrzeń nazw System.

## <a name="syntax"></a>Składnia

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Uwagi

Użyj tej opcji, jeśli chcesz zdefiniować lub utworzyć własną przestrzeń nazw systemu i obiekty.

Jeśli nie określisz opcji **-nostdlib**, mscorlib. dll zostanie zaimportowany do programu (tak samo jak w przypadku określenia **-nostdlib-** ). Określenie **-nostdlib** jest taka sama jak w przypadku określenia **-nostdlib +** .

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio

> [!NOTE]
> Poniższe instrukcje dotyczą tylko programu Visual Studio 2015 (i jego wcześniejszych wersji). W programie Visual Studio 2017 nie istnieje właściwość Build programu **mscorlib. dll** .

1. Otwórz stronę **Właściwości** dla projektu.

2. Kliknij stronę właściwości **kompilacji** .

3. Kliknij przycisk **Zaawansowane** .

4. Zmodyfikuj właściwość nie Odwołuj się do **biblioteki mscorlib. dll** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>tę opcję kompilatora, zobacz.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
