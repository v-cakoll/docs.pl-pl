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
ms.openlocfilehash: a6c151798c807206cc7f4b2fbeb21e75e9142379
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44198481"
---
# <a name="generic-interfaces"></a>Interfejsy ogólne
Ten temat zawiera omówienie ogólnych interfejsów, które udostępniają funkcje wspólne dla rodziny typów ogólnych.  
  
## <a name="generic-interfaces"></a>Interfejsy ogólne  
 Interfejsy ogólne zapewniają bezpieczny odpowiedników nierodzajowych interfejsy, porównania porządkowania i równości i funkcji, który jest współużytkowany przez typy generyczne kolekcji.  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], parametry typu kilka interfejsów ogólnych jest oznaczony jako kowariantny lub kontrawariantny, co zapewnia większą elastyczność przypisywania i używania typami, które implementują te interfejsy. Zobacz [kowariancji i kontrawariancji](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Równości i porównania porządkowania  
 W <xref:System> przestrzeni nazw, <xref:System.IComparable%601?displayProperty=nameWithType> i <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsów ogólnych, takich jak ich odpowiedników nierodzajowych, zdefiniuj metody ustalania kolejności porównania i porównywanie równości, odpowiednio. Typy implementują te interfejsy, aby zapewnić możliwość wykonywania takie porównania.  
  
 W <xref:System.Collections.Generic> przestrzeni nazw, <xref:System.Collections.Generic.IComparer%601> i <xref:System.Collections.Generic.IEqualityComparer%601> interfejsów ogólnych oferują sposób, aby zdefiniować porównania porządkowania lub równości dla typów, które nie implementują <xref:System.IComparable%601?displayProperty=nameWithType> lub <xref:System.IEquatable%601?displayProperty=nameWithType> ogólny interfejs, dlatego umożliwiają ponownie zdefiniować te relacje dla typów, które wykonują. Te interfejsy są używane przez metod i konstruktorów z wielu klas kolekcji ogólnej. Na przykład, można przekazać ogólnego <xref:System.Collections.Generic.IComparer%601> obiekt do konstruktora obiektu <xref:System.Collections.Generic.SortedDictionary%602> klasy, aby określić kolejność sortowania dla typu, który nie implementuje ogólny <xref:System.IComparable%601?displayProperty=nameWithType>. Istnieją przeciążenia <xref:System.Array.Sort%2A?displayProperty=nameWithType> metody ogólnej statycznej i <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metodę wystąpienia sortowania tablice i listy przy użyciu ogólnych <xref:System.Collections.Generic.IComparer%601> implementacji.  
  
 <xref:System.Collections.Generic.Comparer%601> i <xref:System.Collections.Generic.EqualityComparer%601> klas ogólnych dostarczają klasy podstawowej implementacji <xref:System.Collections.Generic.IComparer%601> i <xref:System.Collections.Generic.IEqualityComparer%601> interfejsów ogólnych, a także udostępniają domyślne porównania porządkowania i równości, za pomocą odpowiednich <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> i <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="collection-functionality"></a>Funkcję zbierania  
 <xref:System.Collections.Generic.ICollection%601> Ogólny interfejs jest podstawowy interfejs dla typów kolekcji ogólnej. Udostępnia podstawowe funkcje do dodawania, usuwania, kopiowania i wyliczanie elementów. <xref:System.Collections.Generic.ICollection%601> dziedziczy z obu ogólny <xref:System.Collections.Generic.IEnumerable%601> i nierodzajowymi <xref:System.Collections.IEnumerable>.  
  
 <xref:System.Collections.Generic.IList%601> Ogólny interfejs rozszerza <xref:System.Collections.Generic.ICollection%601> ogólny interfejs za pomocą metody pobierania indeksowanego.  
  
 <xref:System.Collections.Generic.IDictionary%602> Ogólny interfejs rozszerza <xref:System.Collections.Generic.ICollection%601> ogólny interfejs za pomocą metody pobierania kluczem. Generyczny słownik typów w bibliotece klasy bazowej programu .NET Framework także implementować nongeneric <xref:System.Collections.IDictionary> interfejsu.  
  
 <xref:System.Collections.Generic.IEnumerable%601> Ogólny interfejs stanowi strukturę ogólnego modułu wyliczającego. <xref:System.Collections.Generic.IEnumerator%601> Ogólny interfejs implementowany przez moduły wyliczające ogólnego dziedziczy nongeneric <xref:System.Collections.IEnumerator> interfejsu; <xref:System.Collections.IEnumerator.MoveNext%2A> i <xref:System.Collections.IEnumerator.Reset%2A> elementów członkowskich, które nie są zależne od parametru typu `T`, pojawiają się tylko na nongeneric interfejs. Oznacza to, że każdy konsument nierodzajowymi interfejsu również wykorzystywać ogólny interfejs.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic?displayProperty=nameWithType>  
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
- [Typy ogólne](../../../docs/standard/generics/index.md)  
- [Kolekcje ogólne w oprogramowaniu .NET Framework](../../../docs/standard/generics/collections.md)  
- [Delegaci ogólni do manipulowania tablicami i listami](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
- [Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md)
