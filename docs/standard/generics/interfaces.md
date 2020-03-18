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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708327"
---
# <a name="generic-interfaces"></a>Interfejsy ogólne
W tym temacie przedstawiono omówienie ogólnych interfejsów, które zapewniają typowe funkcje dla rodzin typów ogólnych.  
  
## <a name="generic-interfaces"></a>Interfejsy ogólne  
 Interfejsy ogólne zapewniają bezpieczne dla typu odpowiedniki interfejsów nieogólnych do porównywania porządkowania i równości oraz dla funkcji współużytkowanej przez typy kolekcji rodzajowych.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, parametry typu kilku interfejsów ogólnych są oznaczone kowariantne lub kontrawariantne, zapewniając większą elastyczność w przypisywaniu i przy użyciu typów, które implementują te interfejsy. Zobacz [Kowariancja i Contravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Porównania równości i kolejności  
 W <xref:System> przestrzeni nazw <xref:System.IComparable%601?displayProperty=nameWithType> interfejsów i <xref:System.IEquatable%601?displayProperty=nameWithType> ogólnych, takich jak ich odpowiedniki nierodzajowe, zdefiniować metody porządkowania porównań i porównań równości, odpowiednio. Typy implementują te interfejsy, aby zapewnić możliwość wykonywania takich porównań.  
  
 W <xref:System.Collections.Generic> przestrzeni nazw <xref:System.Collections.Generic.IComparer%601> interfejsów i <xref:System.Collections.Generic.IEqualityComparer%601> ogólnych oferują sposób definiowania kolejności lub porównania <xref:System.IComparable%601?displayProperty=nameWithType> równości <xref:System.IEquatable%601?displayProperty=nameWithType> dla typów, które nie implementują lub ogólny interfejs i zapewniają sposób ponownego zdefiniowania tych relacji dla typów, które nie. Te interfejsy są używane przez metody i konstruktory wielu klas kolekcji ogólnej. Na przykład można przekazać <xref:System.Collections.Generic.IComparer%601> obiekt ogólny do <xref:System.Collections.Generic.SortedDictionary%602> konstruktora klasy, aby określić kolejność <xref:System.IComparable%601?displayProperty=nameWithType>sortowania dla typu, który nie implementuje ogólny . Istnieją przeciążenia <xref:System.Array.Sort%2A?displayProperty=nameWithType> ogólnej metody <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> statycznej i metody wystąpienia sortowania <xref:System.Collections.Generic.IComparer%601> tablic i list przy użyciu implementacji ogólnych.  
  
 Klasy <xref:System.Collections.Generic.Comparer%601> <xref:System.Collections.Generic.EqualityComparer%601> ogólne i ogólne zapewniają klasy <xref:System.Collections.Generic.IComparer%601> podstawowe <xref:System.Collections.Generic.IEqualityComparer%601> dla implementacji i ogólnych interfejsów, a <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> także <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> zapewniają domyślne porządkowanie i porównania równości za pośrednictwem ich odpowiednich i właściwości.  
  
### <a name="collection-functionality"></a>Funkcje kolekcji  
 Ogólny <xref:System.Collections.Generic.ICollection%601> interfejs jest podstawowym interfejsem dla typów kolekcji ogólnych. Zapewnia podstawowe funkcje dodawania, usuwania, kopiowania i wyliczania elementów. <xref:System.Collections.Generic.ICollection%601>dziedziczy zarówno <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Collections.IEnumerable>ogólnych, jak i nieogólnych .  
  
 Ogólny <xref:System.Collections.Generic.IList%601> interfejs rozszerza <xref:System.Collections.Generic.ICollection%601> ogólny interfejs o metody pobierania indeksowane.  
  
 Ogólny <xref:System.Collections.Generic.IDictionary%602> interfejs rozszerza <xref:System.Collections.Generic.ICollection%601> ogólny interfejs o metody pobierania kluczy. Typy słowników ogólnych w bibliotece klas podstawowych <xref:System.Collections.IDictionary> .NET Framework również implementują interfejs nierodzajowy.  
  
 Ogólny <xref:System.Collections.Generic.IEnumerable%601> interfejs zapewnia ogólną strukturę modułu wyliczania. Ogólny <xref:System.Collections.Generic.IEnumerator%601> interfejs zaimplementowany przez ogólne moduły wyliczania dziedziczy interfejs nierodzajowy; <xref:System.Collections.IEnumerator> i <xref:System.Collections.IEnumerator.MoveNext%2A> <xref:System.Collections.IEnumerator.Reset%2A> elementy członkowskie, które nie zależą `T`od parametru typu, pojawiają się tylko na interfejsie nierodzajowym. Oznacza to, że każdy konsument interfejsu nierodzajowego może również korzystać z interfejsu ogólnego.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Typy ogólne](../../../docs/standard/generics/index.md)
- [Kolekcje ogólne w oprogramowaniu .NET Framework](../../../docs/standard/generics/collections.md)
- [Delegaty ogólne do manipulowania tablicami i listami](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md)
