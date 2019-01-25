---
title: Wymagane odwołanie do zestawu &#39; &lt;assemblyname&gt; &#39; klasą bazową &#39; &lt;classname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: f2aa8f1f05ce15bd25992b7f1851854952108813
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506282"
---
# <a name="reference-required-to-assembly-39ltassemblynamegt39-containing-the-base-class-39ltclassnamegt39"></a>Wymagane odwołanie do zestawu &#39; &lt;assemblyname&gt; &#39; klasą bazową &#39; &lt;classname&gt;&#39;
Wymagane odwołanie do zestawu "\<nazwa_zestawu >" z klasą bazową\<nazwa_klasy > ". Dodaj je do projektu.  
  
 Klasa jest zdefiniowana w biblioteki dołączanej (dynamicznie DLL) lub zestawu, który nie jest bezpośrednio wywoływany w projekcie. Kompilator Visual Basic wymaga odwołania, aby uniknąć niejednoznaczności, w przypadku, gdy klasa jest zdefiniowana w więcej niż jednego pliku DLL lub zestawu.  
  
 **Identyfikator błędu:** BC30007  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Obejmują nazwę bez odwołań biblioteki DLL lub zestawu w odwołaniach do projektu.  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)
- [Rozwiązywanie problemów z przerwanymi odwołaniami](/visualstudio/ide/troubleshooting-broken-references)
