---
title: -nostdlib (Opcje kompilatora C#)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345078"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (Opcje kompilatora C#)

**-nostdlib** zapobiega importowi pliku mscorlib.dll, który definiuje cały obszar nazw systemowy.

## <a name="syntax"></a>Składnia

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Uwagi

Użyj tej opcji, jeśli chcesz zdefiniować lub utworzyć własny obszar nazw i obiektów systemowych.

Jeśli nie określisz **-nostdlib,** plik mscorlib.dll zostanie zaimportowany do programu (tak samo jak określenie **-nostdlib-**). Określanie **-nostdlib** jest takie samo jak określenie **-nostdlib+**.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio

> [!NOTE]
> Poniższe instrukcje dotyczą tylko programu Visual Studio 2015 (i wcześniejszych wersji). Właściwość **kompilacji pliku Mscorlib.dll** nie istnieje w nowszych wersjach programu Visual Studio.

1. Otwórz stronę **Właściwości** projektu.

2. Kliknij stronę **Tworzenie** właściwości.

3. Kliknij przycisk **Zaawansowane.**

4. Zmodyfikuj właściwość **Docorlib.dll.**

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>kompilatora, zobacz .

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
