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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77740f86265db86c998af25e6e9ed4c20a7014e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910315"
---
# <a name="commonly-used-collection-types"></a>Często używane typy kolekcji
Typy kolekcji są typowe przykłady kolekcji danych, takich jak tabele zbędnych danych, kolejki, stosów, zbiory, słowniki i listy.  
  
 Kolekcje są oparte na <xref:System.Collections.ICollection> interfejsu <xref:System.Collections.IList> interfejsu <xref:System.Collections.IDictionary> interfejsu lub ich odpowiedników ogólnego. <xref:System.Collections.IList> Interfejsu i <xref:System.Collections.IDictionary> interfejsu są oba pochodzące z <xref:System.Collections.ICollection> interfejs; w związku z tym, wszystkie kolekcje są oparte na <xref:System.Collections.ICollection> interfejs bezpośrednio lub pośrednio. W kolekcjach, na podstawie <xref:System.Collections.IList> interfejsu (takie jak <xref:System.Array>, <xref:System.Collections.ArrayList>, lub <xref:System.Collections.Generic.List%601>) lub bezpośrednio na <xref:System.Collections.ICollection> interfejsu (takie jak <xref:System.Collections.Queue>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Stack>, <xref:System.Collections.Concurrent.ConcurrentStack%601> lub <xref:System.Collections.Generic.LinkedList%601>), każdy element zawiera tylko wartości. W kolekcjach, na podstawie <xref:System.Collections.IDictionary> interfejsu (takie jak <xref:System.Collections.Hashtable> i <xref:System.Collections.SortedList> klas, <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Generic.SortedList%602> klas ogólnych), lub <xref:System.Collections.Concurrent.ConcurrentDictionary%602> klas, każdy element zawiera klucz i wartość.  <xref:System.Collections.ObjectModel.KeyedCollection%602> Klasy jest unikatowa, ponieważ jest on listę wartości z kluczami osadzone w wartości, i w związku z tym, zachowuje się podobnie jak listy, a także takiego jak słownik.  
  
 Kolekcje ogólne są najlepsze rozwiązanie silne wpisywanie. Jednak, jeśli język nie obsługuje typów ogólnych, <xref:System.Collections> przestrzeń nazw zawiera bazowej kolekcji <xref:System.Collections.CollectionBase>, <xref:System.Collections.ReadOnlyCollectionBase>, i <xref:System.Collections.DictionaryBase>, które są abstrakcyjnych klas bazowych, które mogą zostać rozszerzone do tworzenia klas kolekcji, które są silnie typizowane. Gdy wymagana jest dostępu do efektywnego kolekcji wielowątkowych, należy używać ogólnych kolekcji w <xref:System.Collections.Concurrent> przestrzeni nazw.  
  
 Kolekcje mogą się różnić w zależności od tego, jak elementy są przechowywane, sposób sortowania, jak są wykonywane wyszukiwania i jak są wykonywane porównywania. <xref:System.Collections.Queue> Klasy i <xref:System.Collections.Generic.Queue%601> klasy ogólnej zawierają listy pierwszy wejściu — pierwszy na wyjściu, gdy <xref:System.Collections.Stack> klasy i <xref:System.Collections.Generic.Stack%601> klasy ogólnej zawierają listy ostatnich wejściu — pierwszy na wyjściu. <xref:System.Collections.SortedList> Klasy i <xref:System.Collections.Generic.SortedList%602> klasy ogólnej zapewnia posortowaną wersje <xref:System.Collections.Hashtable> klasy i <xref:System.Collections.Generic.Dictionary%602> klasy ogólnej. Elementy <xref:System.Collections.Hashtable> lub <xref:System.Collections.Generic.Dictionary%602> są dostępne tylko dla klucza elementu, ale elementy <xref:System.Collections.SortedList> lub <xref:System.Collections.ObjectModel.KeyedCollection%602> są dostępne przez klucz lub indeks elementu. Indeksy we wszystkich kolekcjach są oparte na zerze, z wyjątkiem <xref:System.Array>, co pozwala tablic, które nie są oparte na zerze.  
  
 Funkcja LINQ to Objects umożliwia używanie zapytań LINQ do dostępu do obiektów w pamięci, tak długo, jak długo typ obiektu implementuje <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>. Zapytania LINQ zapewniają wspólny wzorzec do uzyskiwania dostępu do danych. zazwyczaj są bardziej zwięzłe i czytelne niż standardowe `foreach` pętle i zapewniają filtrowanie, porządkowanie i możliwości grupowania. Zapytania LINQ można również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md), i [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Kolekcje i struktury danych](../../../docs/standard/collections/index.md)|W tym artykule omówiono różnych typów kolekcji dostępnych w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], w tym stosów, kolejek, list, tablic i słowników.|  
|[Typy kolekcji: słownikowy i tabela skrótów](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Opisuje funkcje typów rodzajowych i nierodzajowych słownika bazujących na skrótach.|  
|[Sortowane typy kolekcji](../../../docs/standard/collections/sorted-collection-types.md)|W tym artykule opisano klasy, które udostępniają funkcje sortowania w przypadku list i zestawów.|  
|[Typy ogólne](../../../docs/standard/generics/index.md)|Zawiera opis funkcji ogólne, w tym ogólnych kolekcji, delegatów i interfejsów udostępnianych przez [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Zawiera łącza do dokumentacji funkcji C#, Visual Basic i Visual C++, a także do wspierających technologii, takich jak odbicie.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
