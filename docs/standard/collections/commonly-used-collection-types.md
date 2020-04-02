---
title: Często używane typy kolekcji
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- objects [.NET Framework], grouping in collections
- generics [.NET Framework], collections
- IList interface, grouping data in collections
- IDictionary interface, grouping data in collections
- grouping data in collections, generic collection types
- Collections classes
- generic collections
ms.assetid: f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55
ms.openlocfilehash: dc590d712a49ea27fcc61181e0b8c9b3349e74e5
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588339"
---
# <a name="commonly-used-collection-types"></a>Często używane typy kolekcji
Typy kolekcji są typowe odmiany kolekcji danych, takich jak tabele mieszania, kolejki, stosy, torby, słowniki i listy.  
  
 Kolekcje są oparte <xref:System.Collections.ICollection> na <xref:System.Collections.IList> interfejsie, <xref:System.Collections.IDictionary> interfejsie, interfejsie lub ich ogólnych odpowiednikach. Interfejs <xref:System.Collections.IList> i <xref:System.Collections.IDictionary> interfejs pochodzą z <xref:System.Collections.ICollection> interfejsu; w związku z tym wszystkie <xref:System.Collections.ICollection> kolekcje są oparte na interfejsie bezpośrednio lub pośrednio. W kolekcjach <xref:System.Collections.IList> opartych na <xref:System.Array>interfejsie (np. <xref:System.Collections.ArrayList> <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ICollection> lub ) <xref:System.Collections.Queue>lub <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Stack>bezpośrednio <xref:System.Collections.Concurrent.ConcurrentStack%601> <xref:System.Collections.Generic.LinkedList%601>na interfejsie (np. , lub ), każdy element zawiera tylko wartość. W kolekcjach opartych na interfejsie <xref:System.Collections.IDictionary> (takich jak <xref:System.Collections.Hashtable> i <xref:System.Collections.SortedList> <xref:System.Collections.Generic.Dictionary%602> klasy, i <xref:System.Collections.Generic.SortedList%602> ogólne klasy) lub <xref:System.Collections.Concurrent.ConcurrentDictionary%602> klas, każdy element zawiera klucz i wartość.  Klasa <xref:System.Collections.ObjectModel.KeyedCollection%602> jest unikatowa, ponieważ jest to lista wartości z kluczami osadzonymi w wartościach i dlatego zachowuje się jak lista i jak słownik.  
  
 Kolekcje ogólne są najlepszym rozwiązaniem do silnego pisania. Jeśli jednak język nie obsługuje typów <xref:System.Collections> ogólnych, obszar nazw zawiera <xref:System.Collections.CollectionBase>kolekcje podstawowe, takie jak , <xref:System.Collections.ReadOnlyCollectionBase>i <xref:System.Collections.DictionaryBase>, które są abstrakcyjnymi klasami podstawowymi, które można rozszerzyć, aby utworzyć klasy kolekcji, które są silnie wpisane. Gdy wymagany jest wydajny dostęp do kolekcji wielowątkowej, należy użyć kolekcji ogólnych w obszarze <xref:System.Collections.Concurrent> nazw.  
  
 Kolekcje mogą się różnić, w zależności od sposobu przechowywania elementów, sposobu ich sortowania, sposobu wyszukiwania i sposobu porównywania. Klasa <xref:System.Collections.Queue> i <xref:System.Collections.Generic.Queue%601> klasa ogólna zapewniają pierwsze w pierwszym na <xref:System.Collections.Stack> zewnątrz <xref:System.Collections.Generic.Stack%601> listy, podczas gdy klasa i klasa ogólna zapewniają listy last-in-first-out. Klasa <xref:System.Collections.SortedList> i <xref:System.Collections.Generic.SortedList%602> klasa ogólna zapewniają posortowane wersje <xref:System.Collections.Hashtable> klasy i klasy <xref:System.Collections.Generic.Dictionary%602> ogólnej. <xref:System.Collections.Hashtable> Elementy a lub <xref:System.Collections.Generic.Dictionary%602> a są dostępne tylko przez klucz elementu, <xref:System.Collections.SortedList> ale <xref:System.Collections.ObjectModel.KeyedCollection%602> elementy a lub a są dostępne przez klucz lub indeks elementu. Indeksy we wszystkich kolekcjach są oparte <xref:System.Array>na wartości zero, z wyjątkiem , który zezwala na tablice, które nie są oparte na wartości zero.  
  
 Funkcja LINQ to Objects umożliwia dostęp do obiektów w pamięci za pomocą zapytań <xref:System.Collections.IEnumerable> LINQ, o ile typ obiektu jest implementuje lub <xref:System.Collections.Generic.IEnumerable%601>. Zapytania LINQ zapewniają typowy wzorzec dostępu do danych; są zazwyczaj bardziej zwięzłe i czytelne niż standardowe `foreach` pętle; i zapewniają możliwości filtrowania, zamawiania i grupowania. Zapytania LINQ można również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ do obiektów (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ do obiektów (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)i [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Kolekcje i struktury danych](../../../docs/standard/collections/index.md)|W tym artykule omówiono różne typy kolekcji dostępne w ramach .NET Framework, w tym stosy, kolejki, listy, tablice i słowniki.|  
|[Typy kolekcji tablic wartości funkcji mieszającej i słowników](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Opisuje funkcje ogólnych i nierodzajowych typów słowników opartych na skrótach.|  
|[Sortowane typów kolekcji](../../../docs/standard/collections/sorted-collection-types.md)|W tym artykule opisano klasy, które zapewniają funkcje sortowania list i zestawów.|  
|[Typy ogólne](../../../docs/standard/generics/index.md)|W tym artykule opisano funkcję generics, w tym kolekcje ogólne, delegatów i interfejsów dostarczonych przez .NET Framework. Zawiera łącza do dokumentacji funkcji dla języka C#, Visual Basic i Visual C++ oraz do obsługi technologii, takich jak odbicie.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
