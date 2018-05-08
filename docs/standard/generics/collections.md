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
ms.openlocfilehash: 829ef35d2e26f67ea956a0838d93b9667ad58df4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="generic-collections-in-net"></a>Kolekcje ogólne w .NET

 Biblioteka klas programu .NET oferuje następujące klasy rodzajowej kolekcji w <xref:System.Collections.Generic> i <xref:System.Collections.ObjectModel> przestrzeni nazw. Aby uzyskać szczegółowe informacje o tych klas, zobacz [często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
### <a name="systemcollectionsgeneric"></a>System.Collections.Generic  
 Wiele typy kolekcji ogólnych jest bezpośrednie analogs nierodzajowe typów. <xref:System.Collections.Generic.Dictionary%602> jest ogólny wersja <xref:System.Collections.Hashtable>; używa Struktura ogólna <xref:System.Collections.Generic.KeyValuePair%602> wyliczenia zamiast <xref:System.Collections.DictionaryEntry>.  
  
 <xref:System.Collections.Generic.List%601> jest ogólny wersja <xref:System.Collections.ArrayList>. Brak ogólnego <xref:System.Collections.Generic.Queue%601> i <xref:System.Collections.Generic.Stack%601> klasy, które odpowiadają nierodzajowe wersji.  
  
 Dostępne są wersje rodzajowa i nierodzajowe <xref:System.Collections.Generic.SortedList%602>. Obie wersje są hybryd słownika i listy. <xref:System.Collections.Generic.SortedDictionary%602> Klasy generycznej jest słownikiem czysty i nie ma odpowiednika nierodzajowe.  
  
 <xref:System.Collections.Generic.LinkedList%601> Klasy generycznej jest true listy połączonej. Go nie ma odpowiednika nierodzajowe.  
  
### <a name="systemcollectionsobjectmodel"></a>System.Collections.ObjectModel  
 <xref:System.Collections.ObjectModel.Collection%601> Klasy ogólnej udostępnia klasę podstawową dla wyprowadzanie własne typy kolekcji ogólnych. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Klasa udostępnia w prosty sposób utworzyć kolekcji tylko do odczytu z dowolnego typu, który implementuje <xref:System.Collections.Generic.IList%601> interfejs generyczny. <xref:System.Collections.ObjectModel.KeyedCollection%602> Klasa ogólna stanowi sposób przechowywania obiektów, które zawierają własne klucze.  
  
## <a name="other-generic-types"></a>Inne typy ogólne  
 <xref:System.Nullable%601> Struktura ogólna umożliwia użycie typów wartości, tak jakby może zostać przypisana `null`. Może to być przydatne podczas pracy z zapytań bazy danych, gdzie mogą być brakujące pola, które zawierają typy wartości. Parametr typu ogólnego może być dowolnego typu wartości.  
  
> [!NOTE]
>  W języku C# i Visual Basic, nie jest konieczne użycie <xref:System.Nullable%601> jawnie, ponieważ język ma składnię dla typów dopuszczających wartości zerowe. Zobacz [typy dopuszczające wartości zerowe (C# przewodnik programowania w języku)](../../csharp/programming-guide/nullable-types/index.md) i [typy o wartości Zerowalnej (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md). 
  
 <xref:System.ArraySegment%601> Struktura ogólna zapewnia sposób ograniczyć zakres elementów w tablicy jednowymiarowej tablicy, liczony od zera dowolnego typu. Parametr typu ogólnego jest typ elementów w tablicy.  
  
 <xref:System.EventHandler%601> Delegat ogólny eliminuje potrzebę zadeklarować typ obiektu delegowanego obsługi zdarzeń, jeśli zdarzenie jest zgodny ze wzorcem obsługi zdarzeń, używany przez [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Na przykład, załóżmy, że utworzono `MyEventArgs` klasę pochodną <xref:System.EventArgs>, do przechowywania danych wydarzenia. Następnie można zadeklarować zdarzenia w następujący sposób:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [Typy ogólne](../../../docs/standard/generics/index.md)  
 [Delegaci ogólni do manipulowania tablicami i listami](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [Interfejsy ogólne](../../../docs/standard/generics/interfaces.md)
