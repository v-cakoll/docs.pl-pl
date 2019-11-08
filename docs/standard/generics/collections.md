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
ms.openlocfilehash: 21d8ef3abfd16e11c9251edfc4f39b02e93eaab5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740926"
---
# <a name="generic-collections-in-net"></a>Kolekcje ogólne w programie .NET

 Biblioteka klas .NET zawiera szereg klas ogólnych kolekcji w przestrzeni nazw <xref:System.Collections.Generic> i <xref:System.Collections.ObjectModel>. Aby uzyskać bardziej szczegółowe informacje o tych klasach, zobacz [powszechnie używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
## <a name="systemcollectionsgeneric"></a>System. Collections. Generic

 Wiele typów kolekcji ogólnej to bezpośrednie analogowe typy nieogólne. <xref:System.Collections.Generic.Dictionary%602> to ogólna wersja <xref:System.Collections.Hashtable>; używa struktury ogólnej <xref:System.Collections.Generic.KeyValuePair%602> do wyliczenia, a nie <xref:System.Collections.DictionaryEntry>.  
  
 <xref:System.Collections.Generic.List%601> to ogólna wersja <xref:System.Collections.ArrayList>. Istnieją ogólne klasy <xref:System.Collections.Generic.Queue%601> i <xref:System.Collections.Generic.Stack%601>, które odpowiadają nieogólnym wersjom.  
  
 Istnieją podstawowe i nieogólne wersje <xref:System.Collections.Generic.SortedList%602>. Obie wersje są hybrydowymi słownikiem i listą. Klasa generyczna <xref:System.Collections.Generic.SortedDictionary%602> jest czystym słownikiem i nie ma własnego odpowiednika.  
  
 Klasa ogólna <xref:System.Collections.Generic.LinkedList%601> jest połączoną listą. Nie ma żadnego nieogólnego odpowiednika.  
  
## <a name="systemcollectionsobjectmodel"></a>System. Collections. ObjectModel

 Klasa generyczna <xref:System.Collections.ObjectModel.Collection%601> dostarcza klasę bazową do wyprowadzania własnych typów kolekcji rodzajowych. Klasa <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> zapewnia łatwy sposób tworzenia kolekcji tylko do odczytu z dowolnego typu, który implementuje interfejs <xref:System.Collections.Generic.IList%601> generycznego. Klasa generyczna <xref:System.Collections.ObjectModel.KeyedCollection%602> zapewnia sposób przechowywania obiektów, które zawierają własne klucze.  
  
## <a name="other-generic-types"></a>Inne typy ogólne

 Struktura ogólna <xref:System.Nullable%601> pozwala używać typów wartości, tak jakby mogły być przypisane `null`. Może to być przydatne podczas pracy z kwerendami bazy danych, gdzie nie można zawierać pól zawierających typy wartości. Parametr typu generycznego może być dowolnym typem wartości.  
  
> [!NOTE]
> W C# i Visual Basic nie trzeba używać <xref:System.Nullable%601> jawnie, ponieważ język ma składnię dla typów dopuszczających wartość null. Zobacz [typy wartości null (C# odwołanie)](../../csharp/language-reference/builtin-types/nullable-value-types.md) i [typy wartości null (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).
  
 Ogólna struktura <xref:System.ArraySegment%601> umożliwia rozgraniczenie zakresu elementów w jednowymiarowej tablicy dowolnego typu. Parametr typu ogólnego to typ elementów tablicy.  
  
 Delegat ogólny <xref:System.EventHandler%601> eliminuje konieczność deklarowania typu delegata do obsługi zdarzeń, jeśli zdarzenie jest zgodne ze wzorcem obsługi zdarzeń używanym przez .NET Framework. Załóżmy na przykład, że utworzono klasę `MyEventArgs`, pochodną od <xref:System.EventArgs>, do przechowywania danych dla zdarzenia. Następnie można zadeklarować zdarzenie w następujący sposób:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Typy ogólne](../../../docs/standard/generics/index.md)
- [Delegaci ogólni do manipulowania tablicami i listami](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Interfejsy ogólne](../../../docs/standard/generics/interfaces.md)
