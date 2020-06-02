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
ms.openlocfilehash: 47e54bb76c65dd5acc8ce1921ee385a5cb55cf95
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287994"
---
# <a name="commonly-used-collection-types"></a>Często używane typy kolekcji
Typy kolekcji to typowe różnice między kolekcjami danych, takie jak tabele skrótów, kolejki, stosy, torby, słowniki i listy.  
  
 Kolekcje są oparte na <xref:System.Collections.ICollection> interfejsie, <xref:System.Collections.IList> interfejsie, <xref:System.Collections.IDictionary> interfejsie lub ich rodzajowych odpowiednikach. <xref:System.Collections.IList>Interfejs i <xref:System.Collections.IDictionary> interfejs są wyprowadzane z <xref:System.Collections.ICollection> interfejsu; w związku z tym wszystkie kolekcje są oparte na <xref:System.Collections.ICollection> interfejsie bezpośrednio lub pośrednio. W kolekcjach opartych na <xref:System.Collections.IList> interfejsie (takich jak <xref:System.Array> , <xref:System.Collections.ArrayList> lub <xref:System.Collections.Generic.List%601> ) lub bezpośrednio w <xref:System.Collections.ICollection> interfejsie (takich jak,,, <xref:System.Collections.Queue> <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Stack> <xref:System.Collections.Concurrent.ConcurrentStack%601> lub <xref:System.Collections.Generic.LinkedList%601> ) każdy element zawiera tylko wartość. W kolekcjach opartych na <xref:System.Collections.IDictionary> interfejsie (takich <xref:System.Collections.Hashtable> jak <xref:System.Collections.SortedList> klasy i i <xref:System.Collections.Generic.Dictionary%602> klasy <xref:System.Collections.Generic.SortedList%602> Ogólne) lub <xref:System.Collections.Concurrent.ConcurrentDictionary%602> klasy, każdy element zawiera zarówno klucz, jak i wartość.  <xref:System.Collections.ObjectModel.KeyedCollection%602>Klasa jest unikatowa, ponieważ jest to lista wartości z kluczami osadzonymi w wartościach, dlatego zachowuje się jak lista i jak w przypadku słownika.  
  
 Kolekcje ogólne są najlepszym rozwiązaniem do silnego wpisywania. Jeśli jednak język nie obsługuje typów ogólnych, <xref:System.Collections> przestrzeń nazw zawiera kolekcje podstawowe, takie jak <xref:System.Collections.CollectionBase> , <xref:System.Collections.ReadOnlyCollectionBase> , i <xref:System.Collections.DictionaryBase> , które są abstrakcyjnymi klasami podstawowymi, które można rozszerzyć, aby utworzyć klasy kolekcji, które są silnie wpisane. Gdy wymagany jest wydajny dostęp do kolekcji wielowątkowej, Użyj kolekcji ogólnych w <xref:System.Collections.Concurrent> przestrzeni nazw.  
  
 Kolekcje mogą się różnić, w zależności od tego, jak są przechowywane elementy, jak są one sortowane, jak są wykonywane wyszukiwania oraz jak są dokonywane porównania. Klasa <xref:System.Collections.Queue> i <xref:System.Collections.Generic.Queue%601> Klasa generyczna udostępniają listy pierwszych w pierwszej kolejności, podczas gdy <xref:System.Collections.Stack> Klasa i <xref:System.Collections.Generic.Stack%601> Klasa ogólna zapewniają listy ostatnio w pierwszej kolejności. <xref:System.Collections.SortedList>Klasa i <xref:System.Collections.Generic.SortedList%602> Klasa ogólna zapewniają posortowane wersje <xref:System.Collections.Hashtable> klasy i <xref:System.Collections.Generic.Dictionary%602> klasy generycznej. Elementy a <xref:System.Collections.Hashtable> lub a <xref:System.Collections.Generic.Dictionary%602> są dostępne tylko dla klucza elementu, ale elementy a <xref:System.Collections.SortedList> lub a <xref:System.Collections.ObjectModel.KeyedCollection%602> są dostępne przez klucz lub przez indeks elementu. Indeksy we wszystkich kolekcjach są oparte na zero, z wyjątkiem <xref:System.Array> , które umożliwiają tablicom, które nie są oparte na zero.  
  
 Funkcja LINQ to Objects umożliwia używanie zapytań LINQ do uzyskiwania dostępu do obiektów w pamięci, o ile typ obiektu implementuje <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> . Zapytania LINQ zapewniają wspólny wzorzec dostępu do danych; są zwykle bardziej zwięzłe i czytelne niż standardowe `foreach` pętle oraz zapewniają możliwości filtrowania, porządkowania i grupowania. Zapytania LINQ mogą również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)i [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Kolekcje i struktury danych](index.md)|Omawia różne typy kolekcji dostępne w .NET Framework, w tym stosy, kolejki, listy, tablice i słowniki.|  
|[Typy kolekcji tablic wartości funkcji mieszającej i słowników](hashtable-and-dictionary-collection-types.md)|Opisuje funkcje rodzajowych i nieogólnych typów słowników opartych na wykorzystaniu skrótów.|  
|[Posortowane typy kolekcji](sorted-collection-types.md)|Opisuje klasy, które udostępniają funkcje sortowania list i zestawów.|  
|[Typy ogólne](../generics/index.md)|Opisuje funkcje ogólne, w tym kolekcje ogólne, Delegaty i interfejsy udostępniane przez .NET Framework. Zawiera łącza do dokumentacji funkcji dla języków C#, Visual Basic i Visual C++ oraz do obsługi technologii, takich jak odbicie.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
