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
ms.openlocfilehash: 704ada32d428c468d5b71a3f1390568ca586079e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708327"
---
# <a name="generic-interfaces"></a>Interfejsy ogólne
Ten temat zawiera omówienie ogólnych interfejsów, które udostępniają typowe funkcje w różnych rodzinach typów ogólnych.  
  
## <a name="generic-interfaces"></a>Interfejsy ogólne  
 Interfejsy generyczne zapewniają bezpieczne dla typu interfejsy nieogólne do sortowania i porównywania równości oraz funkcji, które są współużytkowane przez typy kolekcji generycznej.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, parametry typu kilku interfejsów ogólnych są oznaczone jako współvariant lub kontrawariantne, co zapewnia większą elastyczność w przypisywaniu i używaniu typów, które implementują te interfejsy. Zobacz [Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Porównania równości i określania kolejności  
 W przestrzeni nazw <xref:System>, <xref:System.IComparable%601?displayProperty=nameWithType> i <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsy ogólne, takie jak ich niegeneryczne odpowiedniki, definiują metody określania kolejności porównań i porównywania równości. Typy implementują te interfejsy, aby zapewnić możliwość wykonywania takich porównań.  
  
 W obszarze nazw <xref:System.Collections.Generic> interfejsy ogólne <xref:System.Collections.Generic.IComparer%601> i <xref:System.Collections.Generic.IEqualityComparer%601> umożliwiają zdefiniowanie porównania kolejności lub równości dla typów, które nie implementują interfejsu <xref:System.IComparable%601?displayProperty=nameWithType> ani <xref:System.IEquatable%601?displayProperty=nameWithType>, i umożliwiają zdefiniowanie tych relacji dla typów, które wykonują. Te interfejsy są używane przez metody i konstruktory wielu klas kolekcji ogólnej. Na przykład można przekazać generyczny obiekt <xref:System.Collections.Generic.IComparer%601> do konstruktora klasy <xref:System.Collections.Generic.SortedDictionary%602>, aby określić kolejność sortowania dla typu, który nie implementuje <xref:System.IComparable%601?displayProperty=nameWithType>generycznego. Istnieją przeciążenia ogólnej metody statycznej <xref:System.Array.Sort%2A?displayProperty=nameWithType> i metody wystąpienia <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> w celu sortowania tablic i list przy użyciu ogólnych implementacji <xref:System.Collections.Generic.IComparer%601>.  
  
 Klasy ogólne <xref:System.Collections.Generic.Comparer%601> i <xref:System.Collections.Generic.EqualityComparer%601> zapewniają klasy bazowe dla implementacji interfejsów <xref:System.Collections.Generic.IComparer%601> i <xref:System.Collections.Generic.IEqualityComparer%601> ogólnych, a także zapewniają domyślne sortowanie i Porównywanie równości poprzez ich odpowiednie <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> i <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="collection-functionality"></a>Funkcje kolekcji  
 Interfejs ogólny <xref:System.Collections.Generic.ICollection%601> jest interfejsem podstawowym dla typów kolekcji rodzajowych. Zapewnia podstawowe funkcje dodawania, usuwania, kopiowania i wyliczania elementów. <xref:System.Collections.Generic.ICollection%601> dziedziczy zarówno z generycznej <xref:System.Collections.Generic.IEnumerable%601>, jak i nieogólnej <xref:System.Collections.IEnumerable>.  
  
 Interfejs ogólny <xref:System.Collections.Generic.IList%601> rozszerza <xref:System.Collections.Generic.ICollection%601> ogólny interfejs z metodami pobierania indeksowanego.  
  
 Interfejs generyczny <xref:System.Collections.Generic.IDictionary%602> rozszerza <xref:System.Collections.Generic.ICollection%601> ogólny interfejs z metodami do pobrania. Typy słowników generycznych w .NET Framework biblioteki klas podstawowych również implementują nieogólne <xref:System.Collections.IDictionary> interfejs.  
  
 Interfejs ogólny <xref:System.Collections.Generic.IEnumerable%601> zapewnia ogólną strukturę modułu wyliczającego. Interfejs generyczny <xref:System.Collections.Generic.IEnumerator%601> zaimplementowany przez ogólne moduły wyliczające dziedziczy nieogólny <xref:System.Collections.IEnumerator> interfejs; <xref:System.Collections.IEnumerator.MoveNext%2A> i <xref:System.Collections.IEnumerator.Reset%2A> elementy członkowskie, które nie są zależne od parametru typu `T`, są wyświetlane tylko w nieogólnym interfejsie. Oznacza to, że każdy użytkownik niegenerycznego interfejsu może również korzystać z interfejsu ogólnego.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Typy ogólne](../../../docs/standard/generics/index.md)
- [Kolekcje ogólne w oprogramowaniu .NET Framework](../../../docs/standard/generics/collections.md)
- [Delegaci ogólni do manipulowania tablicami i listami](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md)
