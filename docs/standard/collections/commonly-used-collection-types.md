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
ms.openlocfilehash: 1004a2f9a0594d9150d147dec1e16b56205e0d13
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711405"
---
# <a name="commonly-used-collection-types"></a>Często używane typy kolekcji
Typy kolekcji to typowe różnice między kolekcjami danych, takie jak tabele skrótów, kolejki, stosy, torby, słowniki i listy.  
  
 Kolekcje są oparte na interfejsie <xref:System.Collections.ICollection>, interfejsie <xref:System.Collections.IList>, interfejsie <xref:System.Collections.IDictionary> lub ich rodzajowe odpowiedniki. Interfejs <xref:System.Collections.IList> i interfejs <xref:System.Collections.IDictionary> są pochodnymi interfejsu <xref:System.Collections.ICollection>; w związku z tym wszystkie kolekcje są oparte na interfejsie <xref:System.Collections.ICollection> bezpośrednio lub pośrednio. W kolekcjach opartych na interfejsie <xref:System.Collections.IList> (takim jak <xref:System.Array>, <xref:System.Collections.ArrayList>lub <xref:System.Collections.Generic.List%601>) lub bezpośrednio w interfejsie <xref:System.Collections.ICollection> (na przykład <xref:System.Collections.Queue>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Stack>, <xref:System.Collections.Concurrent.ConcurrentStack%601> lub <xref:System.Collections.Generic.LinkedList%601>) każdy element zawiera tylko wartość. W kolekcjach opartych na interfejsie <xref:System.Collections.IDictionary> (takich jak klasy <xref:System.Collections.Hashtable> i <xref:System.Collections.SortedList>, klasy generyczne <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Generic.SortedList%602>) lub klasy <xref:System.Collections.Concurrent.ConcurrentDictionary%602> każdy element zawiera zarówno klucz, jak i wartość.  Klasa <xref:System.Collections.ObjectModel.KeyedCollection%602> jest unikatowa, ponieważ jest to lista wartości z kluczami osadzonymi w wartościach, dlatego zachowuje się jak lista i jak w przypadku słownika.  
  
 Kolekcje ogólne są najlepszym rozwiązaniem do silnego wpisywania. Jeśli jednak język nie obsługuje typów ogólnych, przestrzeń nazw <xref:System.Collections> obejmuje kolekcje podstawowe, takie jak <xref:System.Collections.CollectionBase>, <xref:System.Collections.ReadOnlyCollectionBase>i <xref:System.Collections.DictionaryBase>, które są abstrakcyjnymi klasami podstawowymi, które można rozszerzyć w celu utworzenia klas kolekcji, które są jednoznacznie wpisane. Gdy wymagany jest wydajny dostęp do kolekcji wielowątkowej, Użyj kolekcji ogólnych w przestrzeni nazw <xref:System.Collections.Concurrent>.  
  
 Kolekcje mogą się różnić, w zależności od tego, jak są przechowywane elementy, jak są one sortowane, jak są wykonywane wyszukiwania oraz jak są dokonywane porównania. Klasa <xref:System.Collections.Queue> i Klasa generyczna <xref:System.Collections.Generic.Queue%601> zapewniają listy pierwszej w pierwszej kolejności, podczas gdy Klasa <xref:System.Collections.Stack> i <xref:System.Collections.Generic.Stack%601> klasy generycznej zapewniają listy ostatnio w pierwszej kolejności. Klasa <xref:System.Collections.SortedList> i Klasa generyczna <xref:System.Collections.Generic.SortedList%602> zapewniają posortowane wersje klasy <xref:System.Collections.Hashtable> i <xref:System.Collections.Generic.Dictionary%602> klasy ogólnej. Elementy <xref:System.Collections.Hashtable> lub <xref:System.Collections.Generic.Dictionary%602> są dostępne tylko za pomocą klucza elementu, ale elementy <xref:System.Collections.SortedList> lub <xref:System.Collections.ObjectModel.KeyedCollection%602> są dostępne przez klucz lub przez indeks elementu... Indeksy we wszystkich kolekcjach są oparte na zero, z wyjątkiem <xref:System.Array>, co umożliwia tablicom, które nie są oparte na zero.  
  
 Funkcja LINQ to Objects umożliwia używanie zapytań LINQ do uzyskiwania dostępu do obiektów w pamięci, o ile typ obiektu implementuje <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>. Zapytania LINQ zapewniają wspólny wzorzec dostępu do danych; są zwykle bardziej zwięzłe i czytelne niż standardowe pętle `foreach`. i umożliwiają filtrowanie, porządkowanie i grupowanie. Zapytania LINQ mogą również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ to ObjectsC#()](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)i [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Kolekcje i struktury danych](../../../docs/standard/collections/index.md)|Omawia różne typy kolekcji dostępne w .NET Framework, w tym stosy, kolejki, listy, tablice i słowniki.|  
|[Typy kolekcji: słownikowy i tabela skrótów](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Opisuje funkcje rodzajowych i nieogólnych typów słowników opartych na wykorzystaniu skrótów.|  
|[Sortowane typy kolekcji](../../../docs/standard/collections/sorted-collection-types.md)|Opisuje klasy, które udostępniają funkcje sortowania list i zestawów.|  
|[Typy ogólne](../../../docs/standard/generics/index.md)|Opisuje funkcje ogólne, w tym kolekcje ogólne, Delegaty i interfejsy udostępniane przez .NET Framework. Zawiera łącza do dokumentacji funkcji programu C#, Visual Basic i wizualizacji C++oraz do obsługi technologii, takich jak odbicie.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
