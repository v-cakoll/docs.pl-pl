---
title: Kolekcje ogólne w .NET
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET], collections
- generic collections [.NET]
- generic types [.NET]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec3f8fb16245318cab8706a2ed136e51f3dc31db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705800"
---
# <a name="generic-collections-in-net"></a>Kolekcje ogólne w .NET

 Biblioteka klas .NET oferuje pewną liczbę klasy kolekcji rodzajowej w <xref:System.Collections.Generic> i <xref:System.Collections.ObjectModel> przestrzeni nazw. Aby uzyskać szczegółowe informacje o tych klas, zobacz [powszechnie używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
### <a name="systemcollectionsgeneric"></a>System.Collections.Generic  
 Wiele typy generyczne kolekcji jest bezpośrednie analogs nierodzajowymi typów. <xref:System.Collections.Generic.Dictionary%602> jest ogólny wersją <xref:System.Collections.Hashtable>; używa ona ogólnych struktury <xref:System.Collections.Generic.KeyValuePair%602> wyliczenia zamiast <xref:System.Collections.DictionaryEntry>.  
  
 <xref:System.Collections.Generic.List%601> jest ogólny wersją <xref:System.Collections.ArrayList>. Występują ogólne <xref:System.Collections.Generic.Queue%601> i <xref:System.Collections.Generic.Stack%601> klasy, które odpowiadają nierodzajowymi wersji.  
  
 Istnieją wersje rodzajowymi i nierodzajowymi <xref:System.Collections.Generic.SortedList%602>. Obie wersje są hybrydy słownik i listy. <xref:System.Collections.Generic.SortedDictionary%602> Klasy generycznej jest słownikiem czysty i nie ma odpowiednika nierodzajowymi.  
  
 <xref:System.Collections.Generic.LinkedList%601> Klasy generycznej jest true połączonej listy. Go nie ma odpowiednika nierodzajowymi.  
  
### <a name="systemcollectionsobjectmodel"></a>System.Collections.ObjectModel  
 <xref:System.Collections.ObjectModel.Collection%601> Klasy ogólnej udostępnia klasę bazową dla wyprowadzanie własne typy generyczne kolekcji. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Klasa udostępnia prosty sposób utworzyć kolekcję tylko do odczytu z dowolnego typu, który implementuje <xref:System.Collections.Generic.IList%601> interfejs generyczny. <xref:System.Collections.ObjectModel.KeyedCollection%602> Ogólnej klasy zapewnia sposób przechowywania obiektów, które zawierają własne klucze.  
  
## <a name="other-generic-types"></a>Inne typy ogólne  
 <xref:System.Nullable%601> Struktura ogólna pozwala na używanie typów wartości, tak, jakby można przypisać `null`. Może to być przydatne podczas pracy z zapytań bazy danych, gdzie może być Brak pól, które zawierają typy wartości. Parametr typu ogólnego może być dowolnego typu wartości.  
  
> [!NOTE]
>  W języku C# i Visual Basic nie jest konieczne użycie <xref:System.Nullable%601> jawnie, ponieważ język ma składnię dla typów dopuszczających wartości null. Zobacz [typów dopuszczających wartości zerowe (C# Programming Guide)](../../csharp/programming-guide/nullable-types/index.md) i [typy o wartości Zerowalnej (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md). 
  
 <xref:System.ArraySegment%601> Struktura ogólna zapewnia sposób ograniczyć zakres elementów w tablicy jednowymiarowo, zaczynający się od zera w dowolnego typu. Parametr typu ogólnego jest typ elementów w tablicy.  
  
 <xref:System.EventHandler%601> Delegat ogólny eliminuje potrzebę deklarowania typu delegata obsługi zdarzeń, jeśli zdarzenie jest zgodny ze wzorcem obsługi zdarzeń, używane przez [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Załóżmy, że utworzono `MyEventArgs` klasy pochodzące z <xref:System.EventArgs>, do przechowywania danych dla zdarzenia. Następnie można zadeklarować zdarzenia w następujący sposób:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Typy ogólne](../../../docs/standard/generics/index.md)
- [Delegaci ogólni do manipulowania tablicami i listami](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Interfejsy ogólne](../../../docs/standard/generics/interfaces.md)
