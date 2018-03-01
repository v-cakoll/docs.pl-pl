---
title: -delaysign (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a931dccb2aebd2c898b55f0a007d9fac8da42f2e
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2018
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
  
 Gdy użytkownik żąda zestawem całkowicie podpisane, kompilator tworzy skrót pliku, który zawiera manifest (metadanych zestawu) i podpisuje ten skrót z kluczem prywatnym. Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest. Jeśli zestaw jest podpisywany z opóźnieniem, kompilator nie obliczania i przechowywania podpisu, ale rezerw miejsca w pliku, aby później można dodać podpisu.  
  
 Na przykład za pomocą **- delaysign +** umożliwia tester do umieszczenia zestawu w globalnej pamięci podręcznej. Po zakończeniu testowania, możesz się zalogować zestawu pełni przez umieszczenie w zestawie przy użyciu klucza prywatnego [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) narzędzia.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnione podpisywanie zestawu](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz **właściwości** strony dla projektu.  
  
2.  Modyfikowanie **opóźnienie tylko znak** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
