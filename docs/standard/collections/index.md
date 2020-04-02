---
title: Kolekcje i struktury danych
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- grouping data in collections
- objects [.NET Framework], grouping in collections
- Array class, grouping data in collections
- threading [.NET Framework], safety
- Collections classes
- collections [.NET Framework]
ms.assetid: 60cc581f-1db5-445b-ba04-a173396bf872
ms.openlocfilehash: ec14cf30159dda1f2c67ef0c0f5f0a3e52000c45
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588649"
---
# <a name="collections-and-data-structures"></a>Kolekcje i struktury danych
Podobne dane często mogą być obsługiwane bardziej efektywnie, gdy przechowywane i manipulowane jako kolekcja. Klasy <xref:System.Array?displayProperty=nameWithType> lub klasy w <xref:System.Collections>, <xref:System.Collections.Generic>, <xref:System.Collections.Concurrent>, System.Collections.Niezmienne przestrzenie nazw, aby dodać, usunąć i zmodyfikować poszczególne elementy lub zakres elementów w kolekcji.  
  
 Istnieją dwa główne rodzaje kolekcji; kolekcje ogólne i kolekcje nierodowe. Kolekcje ogólne zostały dodane w .NET Framework 2.0 i zapewniają kolekcje, które są bezpieczne dla typu w czasie kompilacji. Z tego powodu kolekcje ogólne zazwyczaj oferują lepszą wydajność. Kolekcje ogólne akceptować parametr typu, gdy są one konstruowane <xref:System.Object> i nie wymagają, aby rzutowane do i z typu podczas dodawania lub usuwania elementów z kolekcji.  Ponadto większość kolekcji ogólnych są obsługiwane w aplikacjach ze Sklepu Windows. Nierodzych kolekcji <xref:System.Object>przechowywania elementów jako , wymagają rzutowania, a większość z tych nie są obsługiwane dla tworzenia aplikacji ze Sklepu Windows. Jednak w starszym kodzie mogą być widoczne kolekcje niegeneralne.  
  
 Począwszy od .NET Framework 4, <xref:System.Collections.Concurrent> kolekcje w obszarze nazw zapewniają wydajne operacje bezpieczne dla wątków do uzyskiwania dostępu do elementów kolekcji z wielu wątków. Klasy kolekcji niezmienne w System.Collections.Immutable namespace ([Pakiet NuGet](https://www.nuget.org/packages/System.Collections.Immutable)) są z natury wątku bezpieczne, ponieważ operacje są wykonywane na kopii oryginalnej kolekcji i oryginalnej kolekcji nie można modyfikować.  

<a name="BKMK_Commoncollectionfeatures"></a>
## <a name="common-collection-features"></a>Typowe funkcje kolekcji  
 Wszystkie kolekcje zapewniają metody dodawania, usuwania lub znajdowania elementów w kolekcji. Ponadto wszystkie kolekcje, które bezpośrednio lub <xref:System.Collections.ICollection> pośrednio <xref:System.Collections.Generic.ICollection%601> implementują interfejs lub interfejs współużytkują następujące funkcje:  
  
- **Możliwość wyliczenia kolekcji**  
  
     .NET Framework kolekcje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> zaimplementować lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> włączyć kolekcji do iteracji za pośrednictwem. Wyliczacz można traktować jako ruchomy wskaźnik do dowolnego elementu w kolekcji. [Foreach, w](../../csharp/language-reference/keywords/foreach-in.md) oświadczeniu i [Dla każdego ... Następna instrukcja](../../visual-basic/language-reference/statements/for-each-next-statement.md) użyć modułu <xref:System.Collections.IEnumerable.GetEnumerator%2A> wyliczającego uwidacznianego przez metodę i ukryć złożoność manipulowania moduł wyliczający. Ponadto każda kolekcja, która <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> implementuje jest uważany za *typ queryable* i mogą być wyszukiwane z LINQ. Zapytania LINQ zapewniają typowy wzorzec dostępu do danych. Są one zazwyczaj bardziej zwięzłe i czytelne niż standardowe `foreach` pętle i zapewniają możliwości filtrowania, zamawiania i grupowania. Zapytania LINQ można również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ do obiektów (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ do obiektów (Visual Basic),](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md), [Wprowadzenie do zapytań LINQ (C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)i [Podstawowe operacje kwerend (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
- **Możliwość kopiowania zawartości kolekcji do tablicy**  
  
     Wszystkie kolekcje mogą być kopiowane do tablicy przy użyciu **CopyTo** metody; jednak kolejność elementów w nowej tablicy opiera się na sekwencji, w której wyliczacz zwraca je. Wynikowa tablica jest zawsze jednowymiarowa z dolną granicą zero.  
  
 Ponadto wiele klas kolekcji zawiera następujące funkcje:  
  
- **Właściwości pojemność i liczba**  
  
     Pojemność kolekcji jest liczba elementów może zawierać. Liczba kolekcji jest liczba elementów, które faktycznie zawiera. Niektóre kolekcje ukryć pojemność lub liczbę lub obu.  
  
     Większość kolekcji automatycznie rozszerza się w pojemności po osiągnięciu bieżącej pojemności. Pamięć jest ponownie przydzielana, a elementy są kopiowane ze starej kolekcji do nowej. Zmniejsza to kod wymagany do użycia kolekcji; jednak wydajność kolekcji może mieć negatywny wpływ. Na przykład <xref:System.Collections.Generic.List%601>dla <xref:System.Collections.Generic.List%601.Count%2A> , Jeśli <xref:System.Collections.Generic.List%601.Capacity%2A>jest mniejsza niż , dodanie elementu jest operacją O(1). Jeśli pojemność wymaga zwiększenia, aby pomieścić nowy element, dodanie elementu staje się operacją O(n), gdzie n jest <xref:System.Collections.Generic.List%601.Count%2A>. Najlepszym sposobem uniknięcia niskiej wydajności spowodowanej przez wiele ponownych alokacji jest ustawienie początkowej pojemności do szacowanego rozmiaru kolekcji.  
  
     A <xref:System.Collections.BitArray> jest szczególnym przypadkiem; jego pojemność jest taka sama jak jego długość, która jest taka sama jak jego liczba.  
  
- **Spójna dolna granica**  
  
     Dolna granica kolekcji jest indeks jego pierwszy element. Wszystkie indeksowane kolekcje <xref:System.Collections> w przestrzeniach nazw mają dolną granicę zero, co oznacza, że są indeksowane 0. <xref:System.Array>domyślnie ma dolną granicę zera, ale podczas tworzenia wystąpienia klasy **Array** przy <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>użyciu programu .  
  
- **Synchronizacja dostępu z wielu wątków** (tylko<xref:System.Collections> klasy).  
  
     Niegeneralne typy <xref:System.Collections> kolekcji w obszarze nazw zapewniają pewne bezpieczeństwo wątków z synchronizacją; zazwyczaj narażone przez <xref:System.Collections.ICollection.SyncRoot%2A> <xref:System.Collections.ICollection.IsSynchronized%2A> i członków. Te kolekcje nie są domyślnie bezpieczne dla wątków. Jeśli potrzebujesz skalowalnego i wydajnego dostępu wielowątkowego do <xref:System.Collections.Concurrent> kolekcji, użyj jednej z klas w obszarze nazw lub rozważ użycie kolekcji niezmienne. Aby uzyskać więcej informacji, zobacz [Kolekcje bezpieczne dla wątków](../../../docs/standard/collections/thread-safe/index.md).  
  
<a name="BKMK_Choosingacollection"></a>
## <a name="choosing-a-collection"></a>Wybór kolekcji  
 Ogólnie rzecz biorąc należy użyć kolekcji ogólnych. W poniższej tabeli opisano niektóre typowe scenariusze kolekcji i klasy kolekcji, których można użyć w tych scenariuszach. Jeśli jesteś nowy w kolekcji ogólnych, ta tabela pomoże Ci wybrać kolekcji ogólnej, która działa najlepiej dla twojego zadania.  

|Chcę...|Ogólne opcje zbierania|Niegeneryczne opcje zbierania|Bezpieczne dla wątków lub niezmienne opcje zbierania|  
|-|-|-|-|  
|Przechowuj towary jako pary klucz/wartość, aby szybko wyszukać według klucza|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Kolekcja par klucz/wartość, które są zorganizowane na podstawie kodu skrótu klucza.)|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|  
|Dostęp do elementów według indeksu|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|  
|Używanie elementów typu "pierwszy w pierwszym na wyjęciem" (FIFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|  
|Użyj danych Last-In-First-Out (LIFO)|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|  
|Dostęp do elementów sekwencyjnie|<xref:System.Collections.Generic.LinkedList%601>|Brak rekomendacji|Brak rekomendacji|  
|Otrzymuj powiadomienia, gdy elementy zostaną usunięte lub dodane do kolekcji. (implementi <xref:System.ComponentModel.INotifyPropertyChanged> <xref:System.Collections.Specialized.INotifyCollectionChanged>i)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Brak rekomendacji|Brak rekomendacji|  
|Posortowana kolekcja|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
|Zestaw funkcji matematycznych|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Brak rekomendacji|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
  
<a name="BKMK_RelatedTopics"></a>
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wybieranie klasy kolekcji](../../../docs/standard/collections/selecting-a-collection-class.md)|W tym artykule opisano różne kolekcje i pomaga wybrać jeden dla scenariusza.|  
|[Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)|Opisuje często używane typy zbierania ogólnego <xref:System.Array?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>i <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>nierodzajowego, takie jak , i .|  
|[Kiedy należy używać kolekcji ogólnych](../../../docs/standard/collections/when-to-use-generic-collections.md)|W tym artykule omówiono użycie typów kolekcji rodzajowych.|  
|[Porównywanie i sortowanie w kolekcjach](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|W tym artykule omówiono użycie porównań równości i porównania sortowania w kolekcjach.|  
|[Sortowane typów kolekcji](../../../docs/standard/collections/sorted-collection-types.md)|Opisuje wydajność i charakterystykę posortowanych kolekcji|  
|[Typy kolekcji tablic wartości funkcji mieszającej i słowników](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|W tym artykule opisano funkcje ogólnych i niegenerycznych typów słowników opartych na skrótach.|  
|[Kolekcje bezpieczne dla wątków](../../../docs/standard/collections/thread-safe/index.md)|W tym artykule opisano typy kolekcji, takie jak <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> i <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> które obsługują bezpieczny i wydajny równoczesny dostęp z wielu wątków.|  
|System.Collections.Niezmienne|Wprowadza kolekcje niezmienne i zawiera łącza do typów kolekcji.|  
  
<a name="BKMK_Reference"></a>
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Array?displayProperty=nameWithType>  
 <xref:System.Collections?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.Specialized?displayProperty=nameWithType>  
 <xref:System.Linq?displayProperty=nameWithType>  
 <xref:System.Collections.Immutable>
