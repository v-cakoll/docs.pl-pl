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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fcff6d701b177d125eddaffe74383446f5f7b2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577231"
---
# <a name="collections-and-data-structures"></a>Kolekcje i struktury danych
Podobne dane często są obsługiwane wydajniej podczas przechowywania i manipulować jako kolekcja. Można użyć <xref:System.Array?displayProperty=nameWithType> klasy lub klas w <xref:System.Collections>, <xref:System.Collections.Generic>, <xref:System.Collections.Concurrent>, System.Collections.Immutable przestrzeni nazw, aby dodać, usuwanie i modyfikowanie poszczególne elementy lub zakres elementów w kolekcji.  
  
 Istnieją dwa główne rodzaje kolekcji; kolekcje ogólne i inny niż ogólny kolekcji. Kolekcje ogólne zostały dodane w .NET Framework 2.0 i podaj kolekcje, które są bezpieczne podczas kompilacji. Kolekcje ogólne, w związku z tym oferują zwykle lepszą wydajność. Kolekcje ogólne akceptowane parametr typu są konstruowane i nie wymagają można rzutować do i z <xref:System.Object> wpisz po dodaniu lub usunięciu elementów z kolekcji.  Ponadto kolekcje najbardziej ogólne są obsługiwane w [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] aplikacji. Inne niż ogólne kolekcje zapisywania elementów jako <xref:System.Object>, wymagają rzutowanie i większość nie są obsługiwane dla [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] tworzenia aplikacji. Jednak może wystąpić z systemem innym niż ogólne kolekcje w programie starszego kodu.  
  
 Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kolekcje w <xref:System.Collections.Concurrent> przestrzeni nazw zapewniają wydajność operacji wątkowo do uzyskiwania dostępu do kolekcji elementów, wiele wątków. Klasy kolekcji niezmienialnych w przestrzeni nazw System.Collections.Immutable ([pakietu NuGet](https://www.nuget.org/packages/System.Collections.Immutable)) są z założenia wątkowo, ponieważ operacje są wykonywane na kopię oryginalnej kolekcji i w oryginalnej kolekcji Nie można modyfikować.  
  
  
<a name="BKMK_Commoncollectionfeatures"></a>   
## <a name="common-collection-features"></a>Wspólne funkcje kolekcji  
 Wszystkie kolekcje zawierają metod dodawania, usuwania i znajdowanie elementów w kolekcji. Ponadto wszystkie kolekcje bezpośrednio lub pośrednio implementują <xref:System.Collections.ICollection> interfejsu lub <xref:System.Collections.Generic.ICollection%601> interfejsu udostępniać te funkcje:  
  
-   **Umożliwia wyliczenie kolekcji**  
  
     Kolekcje .NET framework albo implementować <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> można włączyć kolekcji należy powtórzyć za pośrednictwem. Moduł wyliczający można traktować jako ruchome wskaźnik do dowolnego elementu w kolekcji. [Foreach w](~/docs/csharp/language-reference/keywords/foreach-in.md) instrukcji i [For Each... Następna instrukcja](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) Użyj udostępnianych przez moduł wyliczający <xref:System.Collections.IEnumerable.GetEnumerator%2A> — metoda i Ukryj złożoność manipulowanie modułu wyliczającego. Ponadto żadnej kolekcji implementującej <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> jest uznawany za *kolejność typu* i można zbadać za pomocą LINQ. Zapytania LINQ Podaj wspólnego wzorca do uzyskiwania dostępu do danych. Są one zazwyczaj zwięzły i bardziej czytelny niż standardowe `foreach` pętli, a następnie podaj filtrowania, kolejność i grupowanie możliwości. Zapytania LINQ także może zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ do obiektów](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9), [równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md) i [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
-   **Możliwość kopiowania zawartości kolekcji do tablicy**  
  
     Wszystkie kolekcje można skopiować do tablicy przy użyciu **CopyTo** metody; jednak kolejność elementów w nowej tablicy jest oparta na sekwencji, w której są zwracane przez moduł wyliczający. Tablica wynikowa jest zawsze jednowymiarowa z dolną granicą zero.  
  
 Ponadto wiele klas kolekcji zawiera następujące funkcje:  
  
-   **Pojemność i liczby właściwości**  
  
     Pojemność kolekcji jest liczba elementów, które może zawierać. Liczba kolekcji jest liczba elementów, które zawiera. Niektóre kolekcje Ukryj pojemność licznika i/lub.  
  
     Większość kolekcji automatycznie rozwiń pojemności, gdy zostanie osiągnięta pojemność bieżąca. Alokowaniu pamięć, a następnie skopiowane elementy z kolekcji starego do nowego. Zmniejsza to kod wymagany do korzystania z kolekcji; jednak kolekcji może mieć negatywny wpływ na wydajność. Na przykład w przypadku <xref:System.Collections.Generic.List%601>, jeśli <xref:System.Collections.Generic.List%601.Count%2A> jest mniejsza niż <xref:System.Collections.Generic.List%601.Capacity%2A>, dodawania elementu jest operacją O(1). Jeśli pojemność wymaga zwiększenia w celu uwzględnienia nowego elementu, dodawania elementu staje się operacją O(n), gdzie n to <xref:System.Collections.Generic.List%601.Count%2A>. Najlepszym sposobem uniknięcia pogorszenie wydajności spowodowany przez wiele przeniesień jest ustalenie początkowej pojemności na szacowany rozmiar kolekcji.  
  
     A <xref:System.Collections.BitArray> jest szczególnych przypadkach; pojemność jest taka sama jak jego długość, która jest taka sama jak jego count.  
  
-   **Spójne dolna granica**  
  
     Dolna granica kolekcji jest indeks pierwszego elementu. Indeksowane wszystkie kolekcje w programie <xref:System.Collections> przestrzeni nazw ma dolna granica zero, co oznacza są indeksowane 0. <xref:System.Array> ma dolna granica zero domyślnie, ale podczas tworzenia wystąpienia można zdefiniować dolną granicą inną **tablicy** przy użyciu <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>.  
  
-   **Synchronizacja dla dostęp wiele wątków** (<xref:System.Collections> tylko klasy).  
  
     Typy kolekcji nieogólny w <xref:System.Collections> przestrzeni nazw zapewnić bezpieczeństwo niektórych wątków synchronizacji; zazwyczaj dostępne za pośrednictwem <xref:System.Collections.ICollection.SyncRoot%2A> i <xref:System.Collections.ICollection.IsSynchronized%2A> elementów członkowskich. Tych kolekcji nie są wątkowo domyślnie. Jeśli potrzebujesz skalowalne i wydajne wielowątkowych dostęp do kolekcji, użyj jednej z klas w <xref:System.Collections.Concurrent> przestrzeni nazw lub należy wziąć pod uwagę przy użyciu kolekcji niezmienialnych. Aby uzyskać więcej informacji, zobacz [kolekcje obsługujące wielowątkowość](../../../docs/standard/collections/thread-safe/index.md).  
  
<a name="BKMK_Choosingacollection"></a>   
## <a name="choosing-a-collection"></a>Wybieranie kolekcji  
 Ogólnie rzecz biorąc należy używać kolekcji ogólnych. W poniższej tabeli opisano kilka typowych scenariuszy, kolekcji i klasy kolekcji, używanego w tych scenariuszach. Jeśli jesteś nowym użytkownikiem kolekcje ogólne, ta tabela pomoże kolekcji uniwersalnej, który najlepiej zadania.  
|Chcę...|Opcje kolekcji ogólnych|Opcje inne niż ogólne kolekcji|Opcje obsługujące wielowątkowość lub modyfikować kolekcji|  
|-|-|-|-|  
|Zapisywania elementów jako pary klucz wartość do szybkiego wyszukiwania według klucza|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Kolekcję par klucz/wartość, które są organizowanie uwzględnieniem skrótu klucza).|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|  
|Dostęp do elementów według indeksu|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|  
|Użyj elementów pierwszy — w pierwszej — ruch wychodzący (FIFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|  
|Użyj danych ostatniego w pierwszym poza LIFO|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|  
|Dostęp do elementów po kolei|<xref:System.Collections.Generic.LinkedList%601>|Brak rekomendacji|Brak rekomendacji|  
|Otrzymuj powiadomienia, gdy są one usunąć lub dodać do kolekcji. (implementuje <xref:System.ComponentModel.INotifyPropertyChanged> i <xref:System.Collections.Specialized.INotifyCollectionChanged>)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Brak rekomendacji|Brak rekomendacji|  
|Posortowane kolekcji|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
|A ustawiony dla funkcje matematyczne|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Brak rekomendacji|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
  
<a name="BKMK_RelatedTopics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wybieranie klasy kolekcji](../../../docs/standard/collections/selecting-a-collection-class.md)|W tym artykule opisano różne kolekcje i pomaga wybrać jeden dla danego scenariusza.|  
|[Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)|W tym artykule opisano często używane rodzajowa i nierodzajowe typy kolekcji takich jak <xref:System.Array?displayProperty=nameWithType>, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, i <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.|  
|[Kiedy należy używać kolekcji ogólnych](../../../docs/standard/collections/when-to-use-generic-collections.md)|W tym artykule omówiono używanie typy kolekcji ogólnych.|  
|[Porównywanie i sortowanie w ramach kolekcji](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|W tym artykule omówiono używanie porównywanie równości i sortowania porównania w kolekcjach.|  
|[Sortowane typy kolekcji](../../../docs/standard/collections/sorted-collection-types.md)|W tym artykule opisano kolekcje posortowane wydajności i właściwości|  
|[Typy kolekcji: słownikowy i tabela skrótów](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Zawiera opis funkcji typy ogólne i inny niż ogólny słownik na podstawie wyznaczania wartości skrótu.|  
|[Kolekcje bezpieczne wątkowo](../../../docs/standard/collections/thread-safe/index.md)|Opisuje typy kolekcji, takie jak <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> i <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> obsługujących bezpieczne i wydajne współbieżny dostęp wiele wątków.|  
|System.Collections.Immutable|Wprowadza niezmienne kolekcje i łącza do typów kolekcji.|  
  
<a name="BKMK_Reference"></a>   
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Array?displayProperty=nameWithType>  
 <xref:System.Collections?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.Specialized?displayProperty=nameWithType>  
 <xref:System.Linq?displayProperty=nameWithType>  
 <xref:System.Collections.Immutable>
