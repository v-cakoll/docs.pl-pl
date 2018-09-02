---
title: -delaysign (opcje kompilatora C#)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 105f564d40799c1c006caf8b59d6199dbd8e9318
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400199"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (opcje kompilatora C#)

Ta opcja powoduje, że kompilator, aby zarezerwować miejsce, w pliku wyjściowym, tak aby później można dodać podpisu cyfrowego.

## <a name="syntax"></a>Składnia

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Argumenty

`+` &#124; `-`

Użyj **- delaysign —** Jeśli chcesz, aby podpisać zestaw całkowicie. Użyj **- delaysign +** Jeśli chcesz tylko umieścić klucz publiczny w zestawie. Wartość domyślna to **- delaysign —**.

## <a name="remarks"></a>Uwagi

**- Delaysign** opcja nie ma wpływu, chyba że używana z [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) lub [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).

**- Delaysign** i **- publicsign** opcje wykluczają się wzajemnie.

W przypadku żądania całkowicie podpisanego zestawu, kompilator tworzy skrót pliku który zawiera manifest (metadane zestawu) i podpisuje skrót przy użyciu klucza prywatnego. Ta operacja tworzy podpis cyfrowy, który jest przechowywany w pliku, który zawiera manifest. Gdy zestaw jest podpisany z opóźnieniem, kompilator nie obliczeniowe i przechowuj podpisu, ale rezerwuje miejsce w pliku, aby podpis mógł zostać dodany później.

Na przykład za pomocą **- delaysign +** umożliwia testerowi umieszczenie zestawu w globalnej pamięci podręcznej. Po zakończeniu testowania można całkowicie podpisać zestaw, umieszczając klucza prywatnego w zestawie przy użyciu [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) narzędzia.

Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnienie podpisywania zestawu](../../../framework/app-domains/delay-sign-assembly.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz **właściwości** strony dla projektu.
1. Modyfikowanie **opóźnienie logowania tylko** właściwości.

Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.

## <a name="see-also"></a>Zobacz też

- [Opcja - publicsign C#](publicsign-compiler-option.md)  
- [Opcje kompilatora C#](index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
