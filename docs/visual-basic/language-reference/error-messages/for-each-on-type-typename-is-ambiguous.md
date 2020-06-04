---
title: Element „For Each” w typie „<typename>” jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu „System.Collections.Generic.IEnumerable(Of T)”.
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 153a2640d66f48660f21339aaf0ecc8eaa10f51f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402969"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a>Element „For Each” w typie „\<typename>” jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu „System.Collections.Generic.IEnumerable(Of T)”.
`For Each`Instrukcja określa zmienną iteratora, która ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodę.  
  
 Zmienna iteratora musi być typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejs lub w jednej z `Collections` przestrzeni nazw .NET Framework. Klasa może zaimplementować więcej niż jeden skonstruowany interfejs ogólny przy użyciu innego argumentu typu dla każdej konstrukcji. Jeśli klasa, która jest używana jako zmienna iteratora, ta zmienna ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodę. W takim przypadku Visual Basic nie może wybrać metody do wywołania.  
  
 **Identyfikator błędu:** BC32096  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Użyj [operatora DirectCast](../operators/directcast-operator.md) lub [operatora TryCast](../operators/trycast-operator.md) do rzutowania typu zmiennej iteratora na interfejs definiujący <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodę, której chcesz użyć.  
  
## <a name="see-also"></a>Zobacz też

- [For Each...Next, instrukcja](../statements/for-each-next-statement.md)
- [Interfejsy](../../programming-guide/language-features/interfaces/index.md)
