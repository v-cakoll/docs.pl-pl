---
title: '&#39;Dla każdego&#39; typu &#39; &lt;typename&gt; &#39; jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu &#39;System.Collections.Generic.IEnumerable (Of T)&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 8c48a7134eb8da83fb418b9aa91d55dcbe8e8bcb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456308"
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>&#39;Dla każdego&#39; typu &#39; &lt;typename&gt; &#39; jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu &#39;System.Collections.Generic.IEnumerable (Of T)&#39;
A `For Each` Instrukcja określa zmienna iteratora, który ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.  
  
 Zmienna iteratora musi być typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu w jednym z `Collections` przestrzeni nazw [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Istnieje możliwość dla klasy zaimplementować więcej niż jeden skonstruowanego interfejsu ogólnego, przy użyciu argumentu innego typu, dla każdego konstrukcji. Jeśli klasa, która wykonuje to jest używany dla zmiennej iteratora, zmienna ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody. W takim przypadku języka Visual Basic nie można wybrać jakiej metody do wywołania.  
  
 **Identyfikator błędu:** BC32096  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) lub [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) rzutowanie typu zmiennej iteratora Definiowanie interfejsu <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodę, której chcesz użyć.  
  
## <a name="see-also"></a>Zobacz też  
 [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
