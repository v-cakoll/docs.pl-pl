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
ms.openlocfilehash: cf87d8d2ac4531142288a8637f7fbeb9139382ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545832"
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

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
