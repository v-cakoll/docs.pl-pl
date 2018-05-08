---
title: Wymagane odwołanie do zestawu &#39; &lt;assemblyname&gt; &#39; z klasą podstawową &#39; &lt;classname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: aabf4afb9f87f40d0e31ac7ccd725bfb285ddf37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="reference-required-to-assembly-39ltassemblynamegt39-containing-the-base-class-39ltclassnamegt39"></a>Wymagane odwołanie do zestawu &#39; &lt;assemblyname&gt; &#39; z klasą podstawową &#39; &lt;classname&gt;&#39;
Wymagane odwołanie do zestawu "\<assemblyname >" zawierającego klasę podstawową\<classname > ". Dodaj je do projektu.  
  
 Klasa jest zdefiniowana w biblioteki dołączanej (dynamicznie DLL) lub zestawu, który nie jest bezpośrednio wywoływany w projekcie. Kompilator Visual Basic wymaga odwołania, aby uniknąć niejednoznaczności w przypadku, gdy klasa jest zdefiniowana w więcej niż jednego pliku DLL lub zestawu.  
  
 **Identyfikator błędu:** BC30007  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Uwzględnij nazwę nieużywane biblioteki DLL lub zestawu w odwołaniach do projektu.  
  
## <a name="see-also"></a>Zobacz też  
   
 [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)  
 [Rozwiązywanie problemów z przerwanymi odwołaniami](/visualstudio/ide/troubleshooting-broken-references)
