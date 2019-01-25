---
title: Delegaty ogólne do manipulowania tablicami i listami
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- delegates [.NET Framework], generic delegates
- chaining delegates
- arrays [.NET Framework], generic delegates
- generic delegates [.NET Framework]
- lists [.NET Framework], generic delegates
- generics [.NET Framework], delegates
ms.assetid: 416be383-cc61-4102-9b1b-88b51adb963e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2752ecd05caec207955b2366ed19b3713f571f91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613912"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegaty ogólne do manipulowania tablicami i listami
Ten temat zawiera omówienie delegatów ogólnych dla konwersji, predykaty wyszukiwania i akcje do wykonania w przypadku elementów tablicy lub kolekcji.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegaty ogólne do manipulowania tablicami i listami  
 <xref:System.Action%601> Delegat ogólny reprezentuje metodę, która wykonuje jakąś akcję na element o określonym typie. Można utworzyć metody, która wykonuje żądaną akcję dla elementu, Utwórz wystąpienie obiektu <xref:System.Action%601> delegata do reprezentowania tej metody, a następnie przekazać tablicy i delegata do <xref:System.Array.ForEach%2A?displayProperty=nameWithType> statycznej metody rodzajowej. Metoda jest wywoływana dla każdego elementu tablicy.  
  
 <xref:System.Collections.Generic.List%601> Udostępnia również klasy generycznej <xref:System.Collections.Generic.List%601.ForEach%2A> metody, która używa <xref:System.Action%601> delegować. Ta metoda nie jest ogólna.  
  
> [!NOTE]
>  Dzięki temu interesującej kwestii dotyczących typy ogólne i metody. <xref:System.Array.ForEach%2A?displayProperty=nameWithType> Metoda musi być statyczna (`Shared` w języku Visual Basic) i ogólny ponieważ <xref:System.Array> nie jest ogólny typ; Jedyny przypadek, kiedy można określić typu dla <xref:System.Array.ForEach%2A?displayProperty=nameWithType> może działać w to, że metoda ma swój własny lista parametrów typu. Natomiast nongeneric <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> metoda należy do klasy generycznej <xref:System.Collections.Generic.List%601>, więc po prostu parametr typu klasy. Klasa zdecydowanie jest wpisane, więc metoda może być metodą wystąpienia.  
  
 <xref:System.Predicate%601> Delegat ogólny reprezentuje metodę, która określa, czy określony element spełnia kryteria, należy zdefiniować. Warto skorzystać o następujących ogólnych metod statycznych <xref:System.Array> do wyszukania element lub zbiór elementów: <xref:System.Array.Exists%2A>, <xref:System.Array.Find%2A>, <xref:System.Array.FindAll%2A>, <xref:System.Array.FindIndex%2A>, <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A>, i <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601> współpracuje również z odpowiedniej metody wystąpienia nierodzajowymi <xref:System.Collections.Generic.List%601> klasy ogólnej.  
  
 <xref:System.Comparison%601> Delegat ogólny umożliwia zapewnienie porządek sortowania dla tablicy lub listy elementów, które nie mają kolejność sortowania natywnych lub zmiana kolejności sortowania natywnych. Utwórz metodę, która wykonuje porównanie, Utwórz wystąpienie obiektu <xref:System.Comparison%601> delegata do reprezentowania Twojej formy, a następnie przekazać tablicy i delegata do <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> statycznej metody rodzajowej. <xref:System.Collections.Generic.List%601> Klasy generycznej zawiera odpowiadające przeciążenie metody wystąpienia <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>.  
  
 <xref:System.Converter%602> Delegat ogólny pozwala zdefiniować konwersji między dwoma typami i Konwertuj tablicę jednego typu na drugi tablicę lub przekonwertować listę jeden typ z drugiej listy. Utwórz metodę, która konwertuje elementy listy na nowy typ, Utwórz wystąpienie delegata do reprezentowania metody, a następnie użyj <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> statyczne metodę rodzajową, aby utworzyć tablicę nowy typ z tablicy oryginalnej lub <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> ogólny Metoda wystąpienia, aby wygenerować listę nowy typ z oryginalnej listy.  
  
### <a name="chaining-delegates"></a>Łączenie w łańcuchy delegatów  
 Wiele metod, które używają tych delegatów zwracają tablicę lub listę, która może być przekazywany do innej metody. Na przykład, jeśli chcesz wybrać określone elementy tablicy, konwersji tych elementów do nowego typu i zapisywać je w nowej tablicy można przekazać tablica zwrócona przez <xref:System.Array.FindAll%2A> metodę rodzajową, aby <xref:System.Array.ConvertAll%2A> metody rodzajowej. Jeśli nowy typ elementu nie ma naturalny porządek, można przekazać tablica zwrócona przez <xref:System.Array.ConvertAll%2A> metodę rodzajową, aby <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> metody rodzajowej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Typy ogólne](../../../docs/standard/generics/index.md)
- [Kolekcje ogólne w oprogramowaniu .NET Framework](../../../docs/standard/generics/collections.md)
- [Interfejsy ogólne](../../../docs/standard/generics/interfaces.md)
- [Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md)
