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
ms.openlocfilehash: cf9d1323918d42884f5e2fdf8a5905d13283c74c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575976"
---
# <a name="generic-interfaces"></a>Interfejsy ogólne
Ten temat zawiera omówienie interfejsach zapewniające często używane funkcje w rodzin typów ogólnych.  
  
## <a name="generic-interfaces"></a>Interfejsy ogólne  
 Interfejsy ogólne Podaj bezpieczne odpowiednikami nierodzajowe interfejsów dla porównania porządkowania i równości i funkcji, który jest współużytkowany przez typy kolekcji ogólnych.  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kilka interfejsów ogólnych parametrów typu są oznaczone kowariantnego lub kontrawariantnego większej elastyczności Przypisywanie i używania typy które implementują te interfejsy. Zobacz [Kowariancja i Kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Równość i porównania porządkowania  
 W <xref:System> przestrzeni nazw, <xref:System.IComparable%601?displayProperty=nameWithType> i <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsy ogólne, takie jak ich odpowiedniki nierodzajowe, zdefiniuj metody ustalania kolejności porównań i porównywanie równości, odpowiednio. Typy implementować te interfejsy, aby zapewnić możliwość wykonywania takich porównania.  
  
 W <xref:System.Collections.Generic> przestrzeni nazw, <xref:System.Collections.Generic.IComparer%601> i <xref:System.Collections.Generic.IEqualityComparer%601> interfejsach umożliwiają definiowanie porównania porządkowania lub równości dla typów, które nie implementują <xref:System.IComparable%601?displayProperty=nameWithType> lub <xref:System.IEquatable%601?displayProperty=nameWithType> ogólny interfejs i umożliwiają ponownie zdefiniować te relacje dla typów, które wykonują. Te interfejsy są używane przez metody i konstruktory wielu klas kolekcji ogólnej. Na przykład można przekazać ogólnego <xref:System.Collections.Generic.IComparer%601> obiekt do konstruktora obiektu <xref:System.Collections.Generic.SortedDictionary%602> klasy, aby określić kolejność sortowania dla typu, który nie implementuje ogólnego <xref:System.IComparable%601?displayProperty=nameWithType>. Istnieją przeciążenia metody <xref:System.Array.Sort%2A?displayProperty=nameWithType> statycznej metody rodzajowej i <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metody wystąpienia sortowania stałych i wyświetla listę przy użyciu ogólnych <xref:System.Collections.Generic.IComparer%601> implementacji.  
  
 <xref:System.Collections.Generic.Comparer%601> i <xref:System.Collections.Generic.EqualityComparer%601> klasy ogólne Podaj klas podstawowych implementacji <xref:System.Collections.Generic.IComparer%601> i <xref:System.Collections.Generic.IEqualityComparer%601> interfejsy ogólne i również udostępniać domyślne porównania porządkowania i o równość za pomocą odpowiednich <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> i <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="collection-functionality"></a>Kolekcja funkcji  
 <xref:System.Collections.Generic.ICollection%601> Interfejs generyczny jest podstawowy interfejs dla typów kolekcji ogólnej. Dodawanie, usuwanie, kopiowanie i wyliczania elementów zapewnia podstawowe funkcje. <xref:System.Collections.Generic.ICollection%601> dziedziczy zarówno ogólnego <xref:System.Collections.Generic.IEnumerable%601> i nierodzajowe <xref:System.Collections.IEnumerable>.  
  
 <xref:System.Collections.Generic.IList%601> Rozszerza interfejs ogólny <xref:System.Collections.Generic.ICollection%601> ogólny interfejs za pomocą metod pobierania indeksowanego.  
  
 <xref:System.Collections.Generic.IDictionary%602> Rozszerza interfejs ogólny <xref:System.Collections.Generic.ICollection%601> ogólny interfejs za pomocą metod pobierania kluczem. Typy ogólne słownika w bibliotece programu .NET Framework klasy podstawowej również implementować nongeneric <xref:System.Collections.IDictionary> interfejsu.  
  
 <xref:System.Collections.Generic.IEnumerable%601> Ogólny interfejs zawiera struktura ogólnego modułu wyliczającego. <xref:System.Collections.Generic.IEnumerator%601> Ogólny interfejs implementowany przez moduły wyliczające ogólnego dziedziczy nongeneric <xref:System.Collections.IEnumerator> interfejsu; <xref:System.Collections.IEnumerator.MoveNext%2A> i <xref:System.Collections.IEnumerator.Reset%2A> elementów członkowskich, które nie są zależne od parametru typu `T`, są wyświetlane tylko na nongeneric interfejs. Oznacza to, że konsumenta interfejsu nierodzajowe może również wykorzystać interfejs ogólny.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [Typy ogólne](../../../docs/standard/generics/index.md)  
 [Kolekcje ogólne w oprogramowaniu .NET Framework](../../../docs/standard/generics/collections.md)  
 [Delegaci ogólni do manipulowania tablicami i listami](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md)
