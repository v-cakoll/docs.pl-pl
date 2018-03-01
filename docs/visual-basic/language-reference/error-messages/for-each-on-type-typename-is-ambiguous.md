---
title: "&#39; Dla każdego &#39; dla typu &#39; &lt;typename&gt;&#39; jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu &#39; System.Collections.Generic.IEnumerable (Of T) &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a74178f3f0b2e7589b87046973473582993f3ed9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>&#39; Dla każdego &#39; dla typu &#39; &lt;typename&gt;&#39; jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu &#39; System.Collections.Generic.IEnumerable (Of T) &#39;
A `For Each` instrukcji określa zmiennej iteracyjnej, która ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.  
  
 Zmienna sterująca musi być typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu w jednym z `Collections` przestrzeni nazw [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Istnieje możliwość dla klasy do zaimplementowania więcej niż jeden skonstruowane interfejs ogólny, przy użyciu argumentu innego typu, dla każdego konstrukcji. Klasa, która wykonuje to użycie zmiennej iteracyjnej tej zmiennej ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody. W takim przypadku [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nie można wybrać, którego metoda do wywołania.  
  
 **Identyfikator błędu:** BC32096  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj [operatora DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) lub [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) można rzutować typu zmiennej iteracyjnej do definiowania interfejsu <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody, którego chcesz użyć.  
  
## <a name="see-also"></a>Zobacz też  
 [For Each... Next — instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
