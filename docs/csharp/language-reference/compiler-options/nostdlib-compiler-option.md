---
title: -nostdlib (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 70007c74efe9a41bdfc15e8fa7daf3c8fc0221ed
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935527"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (opcje kompilatora C#)

**-nostdlib** zapobiega Importuj biblioteki mscorlib.dll, która określa całą przestrzeń nazw System.

## <a name="syntax"></a>Składnia

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Uwagi

Użyj tej opcji, jeśli chcesz zdefiniować lub tworzyć własne systemową przestrzenią nazw i obiektów.

Jeśli nie określisz **- nostdlib**, aby biblioteka mscorlib.dll są importowane do programu (taka sama jak określanie **- nostdlib —**). Określanie **- nostdlib** jest taka sama jak określanie **- nostdlib +**.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio

> [!NOTE]
> Poniższe instrukcje dotyczą programu Visual Studio 2015 (i wcześniejszych wersjach) tylko. **Nie odwołują się do biblioteki mscorlib.dll** właściwości kompilacji nie istnieje w programie Visual Studio 2017.

1. Otwórz **właściwości** strony dla projektu.

2. Kliknij przycisk **kompilacji** stronę właściwości.

3. Kliknij przycisk **zaawansowane** przycisku.

4. Modyfikowanie **nie odwołują się do biblioteki mscorlib.dll** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
