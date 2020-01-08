---
title: -nostdlib (C# opcje kompilatora)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345078"
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
> Poniższe instrukcje dotyczą tylko programu Visual Studio 2015 (i jego wcześniejszych wersji). Właściwość kompilacja **nie odwołuje się do biblioteki mscorlib. dll** nie istnieje w nowszych wersjach programu Visual Studio.

1. Otwórz stronę **Właściwości** dla projektu.

2. Kliknij stronę właściwości **kompilacji** .

3. Kliknij przycisk **Zaawansowane** .

4. Zmodyfikuj właściwość nie Odwołuj się do **biblioteki mscorlib. dll** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
