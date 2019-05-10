---
title: Element „For Each” w typie „<typename>” jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu „System.Collections.Generic.IEnumerable(Of T)”.
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: af2340e8e514391503d5f9b706d13ba93336698e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662121"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a>"For Each" w typie "\<typename >" jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu "System.Collections.Generic.IEnumerable (Of T)"
A `For Each` Instrukcja określa zmienna iteratora, który ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.  
  
 Zmienna iteratora musi być typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu w jednym z `Collections` przestrzeni nazw [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Istnieje możliwość dla klasy zaimplementować więcej niż jeden skonstruowanego interfejsu ogólnego, przy użyciu argumentu innego typu, dla każdego konstrukcji. Jeśli klasa, która wykonuje to jest używany dla zmiennej iteratora, zmienna ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody. W takim przypadku języka Visual Basic nie można wybrać jakiej metody do wywołania.  
  
 **Identyfikator błędu:** BC32096  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Użyj [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) lub [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) rzutowanie typu zmiennej iteratora Definiowanie interfejsu <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodę, której chcesz użyć.  
  
## <a name="see-also"></a>Zobacz także

- [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
