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
ms.openlocfilehash: 72dcba3b506dae42f67f0421ba92efee18274c37
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472649"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (opcje kompilatora C#)

Ta opcja powoduje, że kompilator zarezerwowanego miejsca w pliku wyjściowym, tak aby później można dodać podpisu cyfrowego.

## <a name="syntax"></a>Składnia

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Argumenty

`+` &#124; `-`

Użyj **- delaysign —** Jeśli chcesz całkowicie podpisane zestawu. Użyj **- delaysign +** Jeśli chcesz umieścić klucz publiczny w zestawie. Wartość domyślna to **- delaysign —**.

## <a name="remarks"></a>Uwagi

**- Delaysign** opcja nie ma znaczenia, chyba że używana z [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) lub [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).

**- Delaysign** i **- publicsign** wykluczają się wzajemnie.

Gdy użytkownik żąda zestawem całkowicie podpisane, kompilator tworzy skrót pliku, który zawiera manifest (metadanych zestawu) i podpisuje ten skrót z kluczem prywatnym. Tej operacji tworzy podpis cyfrowy, który jest przechowywany w pliku, który zawiera manifest. Jeśli zestaw jest podpisywany z opóźnieniem, kompilator nie obliczania i przechowywania podpisu, ale rezerw miejsca w pliku, aby później można dodać podpisu.

Na przykład za pomocą **- delaysign +** umożliwia tester do umieszczenia zestawu w globalnej pamięci podręcznej. Po zakończeniu testowania, możesz się zalogować zestawu pełni przez umieszczenie w zestawie przy użyciu klucza prywatnego [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) narzędzia.

Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnione podpisywanie zestawu](../../../framework/app-domains/delay-sign-assembly.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz **właściwości** strony dla projektu.
1. Modyfikowanie **opóźnienie tylko znak** właściwości.

Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.

## <a name="see-also"></a>Zobacz też

 [Opcja - publicsign C#](publicsign-compiler-option.md)  
 [Opcje kompilatora C#](index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
