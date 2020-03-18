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
ms.openlocfilehash: 3ca340e19d7340d7bea133fa62c6d8bbc3c0512a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160394"
---
# <a name="collections-and-data-structures"></a>Kolekcje i struktury danych
Podobne dane mogą być często obsługiwane bardziej efektywnie podczas przechowywania i manipulować jako kolekcji. Można użyć <xref:System.Array?displayProperty=nameWithType> klasy lub klas <xref:System.Collections>w <xref:System.Collections.Generic> <xref:System.Collections.Concurrent>, , , System.Collections.Immutable przestrzeni nazw, aby dodać, usunąć i zmodyfikować poszczególne elementy lub zakres elementów w kolekcji.  
  
 Istnieją dwa główne rodzaje kolekcji; kolekcje ogólne i kolekcje nierodzajowe. Kolekcje ogólne zostały dodane w .NET Framework 2.0 i zapewniają kolekcje, które są bezpieczne dla typu w czasie kompilacji. Z tego powodu kolekcje ogólne zazwyczaj oferują lepszą wydajność. Kolekcje ogólne zaakceptować parametr typu, gdy są one konstruowane <xref:System.Object> i nie wymagają, aby rzutować do i z typu podczas dodawania lub usuwania elementów z kolekcji.  Ponadto większość kolekcji ogólnych są obsługiwane w aplikacjach ze Sklepu Windows. Kolekcje nieogólne przechowują elementy jako <xref:System.Object>, wymagają rzutowania, a większość z niej nie jest obsługiwana w programach tworzenia aplikacji ze Sklepu Windows. Jednak w starszym kodzie mogą być widoczne kolekcje nierodzajowe.  
  
 Począwszy od .NET Framework 4 <xref:System.Collections.Concurrent> kolekcje w przestrzeni nazw zapewniają wydajne operacje bezpieczne dla wątków dostępu do elementów kolekcji z wielu wątków. Niezmienne klasy kolekcji w system.collections.immutable przestrzeni nazw[(Pakiet NuGet)](https://www.nuget.org/packages/System.Collections.Immutable)są z natury bezpieczne dla wątków, ponieważ operacje są wykonywane na kopii oryginalnej kolekcji i oryginalnej kolekcji nie można modyfikować.  

<a name="BKMK_Commoncollectionfeatures"></a>
## <a name="common-collection-features"></a>Typowe funkcje kolekcji  
 Wszystkie kolekcje zapewniają metody dodawania, usuwania lub znajdowania elementów w kolekcji. Ponadto wszystkie kolekcje, które bezpośrednio <xref:System.Collections.ICollection> lub pośrednio implementują interfejs lub <xref:System.Collections.Generic.ICollection%601> interfejs, współużytkują te funkcje:  
  
- **Możliwość wyliczania kolekcji**  
  
     Kolekcje .NET <xref:System.Collections.IEnumerable?displayProperty=nameWithType> Framework <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> implementują lub umożliwiają itetensję kolekcji. Wyliczacz można traktować jako ruchomy wskaźnik do dowolnego elementu w kolekcji. [Foreach, w](../../csharp/language-reference/keywords/foreach-in.md) oświadczeniu i [dla każdego ... Next Statement](../../visual-basic/language-reference/statements/for-each-next-statement.md) użyj wyliczającego <xref:System.Collections.IEnumerable.GetEnumerator%2A> udostępniane przez metodę i ukryć złożoność manipulowania wyliczacza. Ponadto każda kolekcja, która <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> implementuje jest uważany za *typ zapytań* i mogą być wyszukiwane za pomocą LINQ. Kwerendy LINQ zapewniają wspólny wzorzec dostępu do danych. Są one zazwyczaj bardziej zwięzłe `foreach` i czytelne niż standardowe pętle i zapewniają możliwości filtrowania, zamawiania i grupowania. Zapytania LINQ można również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic),](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), [Wprowadzenie do zapytań LINQ (C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)i [Podstawowe operacje zapytań (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
- **Możliwość kopiowania zawartości kolekcji do tablicy**  
  
     Wszystkie kolekcje mogą być kopiowane do tablicy przy użyciu **CopyTo** metody; jednak kolejność elementów w nowej tablicy jest oparta na kolejności, w której wyliczacz zwraca je. Wynikowa tablica jest zawsze jednowymiarowa z dolną obwiednią zerową.  
  
 Ponadto wiele klas kolekcji zawiera następujące funkcje:  
  
- **Właściwości pojemności i zliczania**  
  
     Pojemność kolekcji jest liczba elementów, które mogą zawierać. Liczba kolekcji jest liczba elementów, które faktycznie zawiera. Niektóre kolekcje ukryć pojemność lub zliczanie lub obu.  
  
     Większość kolekcji automatycznie zwiększa pojemność po osiągnięciu bieżącej pojemności. Pamięć jest ponownie przydana, a elementy są kopiowane ze starej kolekcji do nowej. Zmniejsza to kod wymagany do korzystania z kolekcji; jednak wydajność kolekcji może mieć negatywny wpływ. Na przykład <xref:System.Collections.Generic.List%601>dla <xref:System.Collections.Generic.List%601.Count%2A> , Jeśli <xref:System.Collections.Generic.List%601.Capacity%2A>jest mniejsza niż , dodanie elementu jest O(1) operacja. Jeśli pojemność musi zostać zwiększona, aby pomieścić nowy element, dodanie elementu staje się <xref:System.Collections.Generic.List%601.Count%2A>operacją O(n), gdzie n jest . Najlepszym sposobem, aby uniknąć niskiej wydajności spowodowanej przez wiele realokacji jest ustawienie początkowej pojemności jako szacowany rozmiar kolekcji.  
  
     A <xref:System.Collections.BitArray> jest szczególnym przypadkiem; jego pojemność jest taka sama jak jego długość, która jest taka sama jak jego liczba.  
  
- **Spójna dolna granica**  
  
     Dolna granica kolekcji jest indeksem jego pierwszego elementu. Wszystkie indeksowane kolekcje w przestrzeniach <xref:System.Collections> nazw mają dolną granica zero, co oznacza, że są indeksowane 0. <xref:System.Array>ma domyślnie dolną obwiednię zerową, ale podczas tworzenia wystąpienia **Array** klasy <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>Array można zdefiniować inną dolną obwiednię.  
  
- **Synchronizacja dostępu z wielu wątków** (tylko<xref:System.Collections> klasy).  
  
     Typy kolekcji innych niż <xref:System.Collections> ogólne w obszarze nazw zapewniają pewne bezpieczeństwo wątków z synchronizacją; zazwyczaj narażone przez <xref:System.Collections.ICollection.SyncRoot%2A> <xref:System.Collections.ICollection.IsSynchronized%2A> i członków. Te kolekcje nie są domyślnie bezpieczne dla wątków. Jeśli potrzebujesz skalowalny i wydajny dostęp wielowątkowy do kolekcji, należy <xref:System.Collections.Concurrent> użyć jednej z klas w przestrzeni nazw lub rozważyć użycie kolekcji niezmienne. Aby uzyskać więcej informacji, zobacz [Kolekcje bezpieczne dla wątków](../../../docs/standard/collections/thread-safe/index.md).  
  
<a name="BKMK_Choosingacollection"></a>
## <a name="choosing-a-collection"></a>Wybór kolekcji  
 Ogólnie rzecz biorąc należy użyć kolekcji ogólnych. W poniższej tabeli opisano niektóre typowe scenariusze kolekcji i klas kolekcji, których można użyć dla tych scenariuszy. Jeśli jesteś nowym użytkownikiem kolekcji ogólnych, ta tabela pomoże Ci wybrać kolekcję rodzajową, która działa najlepiej dla twojego zadania.  

|Chcę...|Opcje kolekcji ogólnej|Opcje zbierania nierodzajowych|Opcje zbierania bezpieczne dla wątków lub niezmienne|  
|-|-|-|-|  
|Przechowuj przedmioty jako pary klucz/wartość, aby szybko wyszukać według klucza|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Kolekcja par klucz/wartość, które są zorganizowane na podstawie kodu skrótu klucza).)|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|  
|Dostęp do elementów według indeksu|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|  
|Używanie elementów pierwszy na pierwszym miejscu (FIFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|  
|Korzystanie z danych last-in-first-out (LIFO)|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|  
|Kolejno uzyskujesz dostęp do elementów|<xref:System.Collections.Generic.LinkedList%601>|Brak rekomendacji|Brak rekomendacji|  
|Otrzymuj powiadomienia, gdy elementy są usuwane lub dodawane do kolekcji. (wdraża <xref:System.ComponentModel.INotifyPropertyChanged> i) <xref:System.Collections.Specialized.INotifyCollectionChanged>|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Brak rekomendacji|Brak rekomendacji|  
|Posortowana kolekcja|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
|Zestaw funkcji matematycznych|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Brak rekomendacji|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
  
<a name="BKMK_RelatedTopics"></a>
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wybieranie klasy kolekcji](../../../docs/standard/collections/selecting-a-collection-class.md)|Opisuje różne kolekcje i pomaga wybrać jeden dla scenariusza.|  
|[Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)|Opisuje często używane typy kolekcji ogólnych <xref:System.Array?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>i <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>nierodzajowych, takie jak , i .|  
|[Kiedy należy używać kolekcji ogólnych](../../../docs/standard/collections/when-to-use-generic-collections.md)|W tym artykule omówiono użycie typów kolekcji rodzajowych.|  
|[Porównywanie i sortowanie w kolekcjach](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|W tym artykule omówiono użycie porównań równości i sortowania porównań w kolekcjach.|  
|[Sortowane typów kolekcji](../../../docs/standard/collections/sorted-collection-types.md)|Opisuje wydajność i właściwości posortowanych kolekcji|  
|[Typy kolekcji tablic wartości funkcji mieszającej i słowników](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Opisuje funkcje ogólnych i nieogólnych typów słowników opartych na skrótach.|  
|[Kolekcje bezpieczne wątkowo](../../../docs/standard/collections/thread-safe/index.md)|Opisuje typy kolekcji, takie jak <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> i <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> które obsługują bezpieczny i wydajny równoczesny dostęp z wielu wątków.|  
|System.Collections.Immutable|Wprowadza kolekcje niezmienne i zawiera łącza do typów kolekcji.|  
  
<a name="BKMK_Reference"></a>
## <a name="reference"></a>Dokumentacja  
 <xref:System.Array?displayProperty=nameWithType>  
 <xref:System.Collections?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.Specialized?displayProperty=nameWithType>  
 <xref:System.Linq?displayProperty=nameWithType>  
 <xref:System.Collections.Immutable>
