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
ms.openlocfilehash: b0de14fd5d576774ed1605784f5f0c6b0fae2c8c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948926"
---
# <a name="generic-collections-in-net"></a>Kolekcje ogólne w .NET

 Biblioteka klas .NET zawiera wiele ogólnych klas kolekcji w <xref:System.Collections.Generic> przestrzeniach nazw i. <xref:System.Collections.ObjectModel> Aby uzyskać bardziej szczegółowe informacje o tych klasach, zobacz [powszechnie używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
### <a name="systemcollectionsgeneric"></a>System.Collections.Generic  
 Wiele typów kolekcji ogólnej to bezpośrednie analogowe typy nieogólne. <xref:System.Collections.Generic.Dictionary%602>jest wersją <xref:System.Collections.Hashtable>ogólną; używa struktury <xref:System.Collections.Generic.KeyValuePair%602> ogólnej do wyliczenia zamiast <xref:System.Collections.DictionaryEntry>.  
  
 <xref:System.Collections.Generic.List%601>to ogólna wersja programu <xref:System.Collections.ArrayList>. Istnieją ogólne <xref:System.Collections.Generic.Queue%601> i <xref:System.Collections.Generic.Stack%601> klasy, które odpowiadają nieogólnym wersji.  
  
 Istnieją podstawowe i nieogólne wersje programu <xref:System.Collections.Generic.SortedList%602>. Obie wersje są hybrydowymi słownikiem i listą. Klasa <xref:System.Collections.Generic.SortedDictionary%602> generyczna jest czystym słownikiem i nie ma własnego odpowiednika.  
  
 Klasa <xref:System.Collections.Generic.LinkedList%601> ogólna jest połączoną listą rzeczywistą. Nie ma żadnego nieogólnego odpowiednika.  
  
### <a name="systemcollectionsobjectmodel"></a>System.Collections.ObjectModel  
 Klasa <xref:System.Collections.ObjectModel.Collection%601> generyczna zapewnia klasę bazową do wyprowadzania własnych typów kolekcji ogólnej. Klasa zapewnia łatwy sposób tworzenia kolekcji tylko do odczytu z dowolnego typu, który <xref:System.Collections.Generic.IList%601> implementuje interfejs generyczny. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Klasa <xref:System.Collections.ObjectModel.KeyedCollection%602> generyczna zapewnia sposób przechowywania obiektów, które zawierają własne klucze.  
  
## <a name="other-generic-types"></a>Inne typy ogólne  
 Struktura ogólna pozwala używać typów wartości, tak jakby mogły być przypisane `null`. <xref:System.Nullable%601> Może to być przydatne podczas pracy z kwerendami bazy danych, gdzie nie można zawierać pól zawierających typy wartości. Parametr typu generycznego może być dowolnym typem wartości.  
  
> [!NOTE]
> W C# i Visual Basic nie jest konieczne jawne użycie <xref:System.Nullable%601> , ponieważ język ma składnię dla typów dopuszczających wartość null. Zobacz [Typy dopuszczająceC# wartości null (Przewodnik programowania)](../../csharp/programming-guide/nullable-types/index.md) i [typy wartości null (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md). 
  
 Struktura <xref:System.ArraySegment%601> ogólna umożliwia rozgraniczenie zakresu elementów w jednowymiarowej tablicy dowolnego typu. Parametr typu ogólnego to typ elementów tablicy.  
  
 Delegat <xref:System.EventHandler%601> ogólny eliminuje konieczność deklarowania typu delegata do obsługi zdarzeń, jeśli zdarzenie jest zgodne z wzorcem obsługi zdarzeń używanym przez .NET Framework. Załóżmy na przykład, że utworzono `MyEventArgs` klasę pochodną z <xref:System.EventArgs>, aby przechowywać dane dla zdarzenia. Następnie można zadeklarować zdarzenie w następujący sposób:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Typy ogólne](../../../docs/standard/generics/index.md)
- [Delegaci ogólni do manipulowania tablicami i listami](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Interfejsy ogólne](../../../docs/standard/generics/interfaces.md)
