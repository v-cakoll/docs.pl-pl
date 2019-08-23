---
title: Interfejsy ogólne
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- generic interfaces [.NET Framework]
- equality comparisons [.NET Framework]
- generics [.NET Framework], interfaces
- ordering comparisons [.NET Framework]
ms.assetid: 88bf5b04-d371-4edb-ba38-01ec7cabaacf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09e9a51fe9c1fd25a6791cf924180329718138c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915891"
---
# <a name="generic-interfaces"></a>Interfejsy ogólne
Ten temat zawiera omówienie ogólnych interfejsów, które udostępniają typowe funkcje w różnych rodzinach typów ogólnych.  
  
## <a name="generic-interfaces"></a>Interfejsy ogólne  
 Interfejsy generyczne zapewniają bezpieczne dla typu interfejsy nieogólne do sortowania i porównywania równości oraz funkcji, które są współużytkowane przez typy kolekcji generycznej.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, parametry typu kilku interfejsów ogólnych są oznaczone jako współvariant lub kontrawariantne, co zapewnia większą elastyczność w przypisywaniu i używaniu typów, które implementują te interfejsy. Zobacz [Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Porównania równości i określania kolejności  
 W obszarze nazw <xref:System.IComparable%601?displayProperty=nameWithType> , i <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsy ogólne, takie jak ich niegeneryczne odpowiedniki, definiują metody określania kolejności porównań i porównywania równości. <xref:System> Typy implementują te interfejsy, aby zapewnić możliwość wykonywania takich porównań.  
  
 <xref:System.Collections.Generic.IComparer%601> <xref:System.IComparable%601?displayProperty=nameWithType> W przestrzeni nazw <xref:System.IEquatable%601?displayProperty=nameWithType> i <xref:System.Collections.Generic.IEqualityComparer%601> interfejsy ogólne umożliwiają zdefiniowanie porównania porządkunia lub równości dla typów, które nie implementują interfejsu lub ogólnych, i zapewniają sposób <xref:System.Collections.Generic> Zdefiniuj ponownie te relacje dla typów, które wykonują. Te interfejsy są używane przez metody i konstruktory wielu klas kolekcji ogólnej. Na przykład można przekazać obiekt generyczny <xref:System.Collections.Generic.IComparer%601> do konstruktora <xref:System.Collections.Generic.SortedDictionary%602> klasy, aby określić kolejność sortowania dla typu, który nie implementuje generycznej <xref:System.IComparable%601?displayProperty=nameWithType>. Istnieją przeciążenia <xref:System.Array.Sort%2A?displayProperty=nameWithType> ogólnej metody statycznej <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> i metody instancji do sortowania tablic i list przy użyciu implementacji ogólnych <xref:System.Collections.Generic.IComparer%601> .  
  
 <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.IComparer%601> <xref:System.Collections.Generic.IEqualityComparer%601> Klasy i generycznezapewniająklasybazowedlaimplementacjiinterfejsówiogólnych,atakżezapewniajądomyślnesortowanieiPorównywanierównościprzyużyciuodpowiednich<xref:System.Collections.Generic.EqualityComparer%601> <xref:System.Collections.Generic.Comparer%601> i <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="collection-functionality"></a>Funkcje kolekcji  
 <xref:System.Collections.Generic.ICollection%601> Ogólny interfejs to podstawowy interfejs dla typów kolekcji rodzajowych. Zapewnia podstawowe funkcje dodawania, usuwania, kopiowania i wyliczania elementów. <xref:System.Collections.Generic.ICollection%601>dziedziczy z zarówno rodzajowe <xref:System.Collections.Generic.IEnumerable%601> , jak i nieogólne. <xref:System.Collections.IEnumerable>  
  
 <xref:System.Collections.Generic.IList%601> Ogólny interfejs <xref:System.Collections.Generic.ICollection%601> rozszerza interfejs ogólny o metody do pobierania indeksowanego.  
  
 Interfejs generyczny rozszerza interfejs <xref:System.Collections.Generic.ICollection%601> ogólny o metody do pobierania, który został utworzony. <xref:System.Collections.Generic.IDictionary%602> Typy słownika generycznego w .NET Framework biblioteki klas podstawowych również implementują interfejs nieogólny <xref:System.Collections.IDictionary> .  
  
 <xref:System.Collections.Generic.IEnumerable%601> Ogólny interfejs zawiera ogólną strukturę modułu wyliczającego. <xref:System.Collections.IEnumerator.MoveNext%2A> <xref:System.Collections.IEnumerator> `T` <xref:System.Collections.IEnumerator.Reset%2A> Ogólny interfejs zaimplementowany przez ogólne moduły wyliczające dziedziczy interfejs nieogólny; i składowe, które nie są zależne od parametru typu, są wyświetlane tylko na nieogólnym <xref:System.Collections.Generic.IEnumerator%601> interfejsu. Oznacza to, że każdy użytkownik niegenerycznego interfejsu może również korzystać z interfejsu ogólnego.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Typy ogólne](../../../docs/standard/generics/index.md)
- [Kolekcje ogólne w oprogramowaniu .NET Framework](../../../docs/standard/generics/collections.md)
- [Delegaci ogólni do manipulowania tablicami i listami](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md)
