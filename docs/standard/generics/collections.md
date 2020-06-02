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
ms.openlocfilehash: 5767bac0bb1e3ae9e586e9a10d8452d421519447
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287574"
---
# <a name="generic-collections-in-net"></a>Kolekcje ogólne na platformie .NET

 Biblioteka klas .NET zawiera wiele ogólnych klas kolekcji w <xref:System.Collections.Generic> <xref:System.Collections.ObjectModel> przestrzeniach nazw i. Aby uzyskać bardziej szczegółowe informacje o tych klasach, zobacz [powszechnie używane typy kolekcji](../collections/commonly-used-collection-types.md).  
  
## <a name="systemcollectionsgeneric"></a>System.Collections.Generic

 Wiele typów kolekcji ogólnej to bezpośrednie analogowe typy nieogólne. <xref:System.Collections.Generic.Dictionary%602>jest wersją ogólną <xref:System.Collections.Hashtable> ; używa struktury ogólnej <xref:System.Collections.Generic.KeyValuePair%602> do wyliczenia zamiast <xref:System.Collections.DictionaryEntry> .  
  
 <xref:System.Collections.Generic.List%601>to ogólna wersja programu <xref:System.Collections.ArrayList> . Istnieją ogólne <xref:System.Collections.Generic.Queue%601> i <xref:System.Collections.Generic.Stack%601> klasy, które odpowiadają nieogólnym wersji.  
  
 Istnieją podstawowe i nieogólne wersje programu <xref:System.Collections.Generic.SortedList%602> . Obie wersje są hybrydowymi słownikiem i listą. <xref:System.Collections.Generic.SortedDictionary%602>Klasa generyczna jest czystym słownikiem i nie ma własnego odpowiednika.  
  
 <xref:System.Collections.Generic.LinkedList%601>Klasa ogólna jest połączoną listą rzeczywistą. Nie ma żadnego nieogólnego odpowiednika.  
  
## <a name="systemcollectionsobjectmodel"></a>System. Collections. ObjectModel

 <xref:System.Collections.ObjectModel.Collection%601>Klasa generyczna zapewnia klasę bazową do wyprowadzania własnych typów kolekcji ogólnej. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>Klasa zapewnia łatwy sposób tworzenia kolekcji tylko do odczytu z dowolnego typu, który implementuje <xref:System.Collections.Generic.IList%601> interfejs generyczny. <xref:System.Collections.ObjectModel.KeyedCollection%602>Klasa generyczna zapewnia sposób przechowywania obiektów, które zawierają własne klucze.  
  
## <a name="other-generic-types"></a>Inne typy ogólne

 <xref:System.Nullable%601>Struktura ogólna pozwala używać typów wartości, tak jakby mogły być przypisane `null` . Może to być przydatne podczas pracy z kwerendami bazy danych, gdzie nie można zawierać pól zawierających typy wartości. Parametr typu generycznego może być dowolnym typem wartości.  
  
> [!NOTE]
> W języku C# i Visual Basic nie jest konieczne jawne użycie, <xref:System.Nullable%601> ponieważ język ma składnię dla typów dopuszczających wartość null. Zobacz [typy wartości null (odwołanie w C#)](../../csharp/language-reference/builtin-types/nullable-value-types.md) i [wartości null (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).
  
 <xref:System.ArraySegment%601>Struktura ogólna umożliwia rozgraniczenie zakresu elementów w jednowymiarowej tablicy dowolnego typu. Parametr typu ogólnego to typ elementów tablicy.  
  
 <xref:System.EventHandler%601>Delegat ogólny eliminuje konieczność deklarowania typu delegata do obsługi zdarzeń, jeśli zdarzenie jest zgodne z wzorcem obsługi zdarzeń używanym przez .NET Framework. Załóżmy na przykład, że utworzono `MyEventArgs` klasę pochodną z <xref:System.EventArgs> , aby przechowywać dane dla zdarzenia. Następnie można zadeklarować zdarzenie w następujący sposób:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Typy ogólne](index.md)
- [Delegaty ogólne do manipulowania tablicami i listami](delegates-for-manipulating-arrays-and-lists.md)
- [Interfejsy ogólne](interfaces.md)
