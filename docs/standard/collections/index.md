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
ms.openlocfilehash: d6b9e3d3f5ebc122e2031dac5999a80445ee03a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083845"
---
# <a name="collections-and-data-structures"></a>Kolekcje i struktury danych
Podobne dane często mogą być obsługiwane efektywniej przy zachowywaniu i modyfikowane jako kolekcję. Możesz użyć <xref:System.Array?displayProperty=nameWithType> klasy lub klas w <xref:System.Collections>, <xref:System.Collections.Generic>, <xref:System.Collections.Concurrent>, System.Collections.Immutable przestrzenie nazw, do dodawania, usuwania i modyfikowania poszczególnych elementów lub szereg elementów w kolekcji.  
  
 Istnieją dwa główne rodzaje kolekcji; kolekcje ogólne i innych niż ogólne kolekcje. Kolekcje ogólne zostały dodane w programie .NET Framework 2.0 i podaj kolekcje, które są bezpieczne w czasie kompilacji. W związku z tym ogólnych kolekcji zwykle zapewniają lepszą wydajność. Kolekcje ogólne zaakceptować parametr typu, gdy są zbudowane i nie wymagają można rzutować do i z <xref:System.Object> wpisz podczas dodawania lub usuwania elementów z kolekcji.  Ponadto większość ogólnych kolekcji są obsługiwane w [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] aplikacji. Inne niż ogólne kolekcje magazynować elementy jako <xref:System.Object>, wymagają rzutowania i większość nie są obsługiwane w przypadku [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] tworzenia aplikacji. Jednak mogą pojawić się innych niż ogólne kolekcje w programie starszego kodu.  
  
 Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kolekcje w programie <xref:System.Collections.Concurrent> przestrzeni nazw zapewniają efektywne działania wątków do uzyskiwania dostępu do elementów kolekcji z wielu wątków. Klasy kolekcji niezmienialnej w przestrzeni nazw System.Collections.Immutable ([pakietu NuGet](https://www.nuget.org/packages/System.Collections.Immutable)) są założenia metodą o bezpiecznych wątkach, ponieważ operacje są wykonywane na kopię oryginalnego kolekcji i oryginalnej kolekcji Nie można modyfikować.  

<a name="BKMK_Commoncollectionfeatures"></a>   
## <a name="common-collection-features"></a>Typowe funkcje zbioru  
 Wszystkie kolekcje zawierają metody dodawania, usuwania i znajdowanie elementów w kolekcji. Ponadto wszystkie kolekcje bezpośrednio lub pośrednio implementują <xref:System.Collections.ICollection> interfejsu lub <xref:System.Collections.Generic.ICollection%601> interfejsu udostępniać te funkcje:  
  
-   **Umożliwia wyliczenie kolekcji**  
  
     Kolekcje .NET framework albo wdrożyć <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> można włączyć kolekcji należy powtórzyć za pośrednictwem. Moduł wyliczający można traktować jako ruchome wskaźnik do dowolnego elementu w kolekcji. [Foreach w](../../csharp/language-reference/keywords/foreach-in.md) instrukcji i [For Each... Następna instrukcja](../../visual-basic/language-reference/statements/for-each-next-statement.md) Użyj modułu wyliczającego udostępnianych przez <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody i Ukryj złożoność manipulowanie moduł wyliczający. Ponadto dowolnej kolekcji implementującej <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> jest uważany za *typ odpytywalny* i może być odpytywana za pomocą LINQ. Zapytania LINQ zapewniają wspólny wzorzec do uzyskiwania dostępu do danych. Zazwyczaj są bardziej zwięzłe i czytelne niż standardowe `foreach` pętli i zapewniają filtrowanie, porządkowanie i możliwości grupowania. Zapytania LINQ można również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md), [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), [wprowadzenie do zapytań LINQ () C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md), i [podstawowe operacje zapytań (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
-   **Możliwość kopiowania zawartości kolekcji do tablicy**  
  
     Wszystkie kolekcje mogą być kopiowane do tablicy przy użyciu **CopyTo** metody; jednak kolejność elementów w nowej tablicy opiera się na sekwencję, w której są zwracane przez moduł wyliczający. Tablica wynikowa jest zawsze jednowymiarowe z dolną granicę równą zero.  
  
 Ponadto wiele klas kolekcji zawiera następujące funkcje:  
  
-   **Właściwości pojemności i liczba**  
  
     Pojemność kolekcji jest liczba elementów, jakie mogą one zawierać. Liczba kolekcji jest liczba elementów, które zawiera. Niektórych kolekcjach ukryć pojemność, liczby lub obu.  
  
     Większość kolekcji jest automatycznie rozszerzana w charakterze po osiągnięciu bieżąca pojemność. Alokowaniu pamięci, a następnie skopiowane elementy z kolekcji starej na nową. Zmniejsza to kod wymagany do korzystania z kolekcji; jednak kolekcji może mieć negatywny wpływ na wydajność. Na przykład w przypadku <xref:System.Collections.Generic.List%601>, jeśli <xref:System.Collections.Generic.List%601.Count%2A> jest mniejsza niż <xref:System.Collections.Generic.List%601.Capacity%2A>, dodanie elementu jest operacją O(1). Jeśli pojemność musi zostać zwiększona, aby pomieścić nowy element, dodanie elementu staje się operacją O(n), gdzie n to <xref:System.Collections.Generic.List%601.Count%2A>. Najlepszym sposobem uniknięcia spadek wydajności spowodowany przez wiele przeniesień ma Ustaw początkową pojemność na szacowany rozmiar kolekcji.  
  
     Element <xref:System.Collections.BitArray> jest przypadkiem szczególnym; pojemność jest taka sama jak jego długość jest taka sama jak jego liczbę.  
  
-   **Spójne dolna granica**  
  
     Dolna granica kolekcji jest indeksem jej pierwszego elementu. Indeksowane wszystkie kolekcje w programie <xref:System.Collections> przestrzenie nazw mają dolną granicę równą zero, co oznacza są indeksowane przez 0. <xref:System.Array> ma dolną granicę równą zero, domyślnie, ale różnych dolną granicę można zdefiniować podczas tworzenia wystąpienia obiektu **tablicy** przy użyciu <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>.  
  
-   **Synchronizacja dla dostępu przez wiele wątków** (<xref:System.Collections> tylko klasy).  
  
     Typy nieuniwersalne kolekcji, w <xref:System.Collections> przestrzeń nazw zapewnia pewne bezpieczeństwo wątkowe za pomocą synchronizacji; zazwyczaj są udostępniane za pośrednictwem <xref:System.Collections.ICollection.SyncRoot%2A> i <xref:System.Collections.ICollection.IsSynchronized%2A> elementów członkowskich. Te kolekcje nie są wątkowo domyślnie. Jeśli potrzebujesz skalowalne i wydajne wielowątkowych dostęp do kolekcji, użyj jednej z klas w <xref:System.Collections.Concurrent> przestrzeni nazw lub należy wziąć pod uwagę przy użyciu kolekcji niezmienialnych. Aby uzyskać więcej informacji, zobacz [kolekcje obsługujące wielowątkowość](../../../docs/standard/collections/thread-safe/index.md).  
  
<a name="BKMK_Choosingacollection"></a>   
## <a name="choosing-a-collection"></a>Wybieranie kolekcji  
 Ogólnie rzecz biorąc należy używać kolekcji ogólnych. W poniższej tabeli opisano kilka typowych scenariuszy, kolekcji i klasy kolekcji, używanych dla tych scenariuszy. Jeśli jesteś nowym użytkownikiem kolekcje ogólne, ta tabela pomoże Ci wybrać kolekcji ogólnej, który jest najlepiej do Twojego zadania.  
 
|Chcę...|Ogólna kolekcja opcje|Opcje inne niż ogólne kolekcji|Opcje obsługujące wielowątkowość lub niezmienialnych kolekcji|  
|-|-|-|-|  
|Store elementów jako pary klucz/wartość dla szybkiego wyszukiwania według klucza|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Kolekcja par klucz wartość, które są zorganizowane na podstawie kodu skrótu klucza).|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|  
|Uzyskiwanie dostępu do elementów według indeksu|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|  
|Użyj elementów pierwszego wejściu — pierwszy na wyjściu (FIFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|  
|Korzystanie z danych ostatniego-wejściu — pierwszy na wyjściu (LIFO)|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|  
|Dostęp do elementów po kolei|<xref:System.Collections.Generic.LinkedList%601>|Brak zaleceń|Brak zaleceń|  
|Otrzymywać powiadomienia, gdy elementy są usuwane lub dodać do kolekcji. (implementuje <xref:System.ComponentModel.INotifyPropertyChanged> i <xref:System.Collections.Specialized.INotifyCollectionChanged>)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Brak zaleceń|Brak zaleceń|  
|Posortowane kolekcji|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
|Element dla funkcji matematycznych|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Brak zaleceń|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
  
<a name="BKMK_RelatedTopics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wybieranie klasy kolekcji](../../../docs/standard/collections/selecting-a-collection-class.md)|W tym artykule opisano różne kolekcje, a następnie pomoże Ci wybrać jeden dla danego scenariusza.|  
|[Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)|W tym artykule opisano typy powszechnie używane kolekcji rodzajowych i nierodzajowych, takie jak <xref:System.Array?displayProperty=nameWithType>, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, i <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.|  
|[Kiedy należy używać kolekcji ogólnych](../../../docs/standard/collections/when-to-use-generic-collections.md)|Omawia stosowanie rodzajowych typów kolekcji.|  
|[Porównywanie i sortowanie w ramach kolekcji](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|W tym artykule omówiono używanie porównania równości i sortowania porównania w kolekcjach.|  
|[Sortowane typy kolekcji](../../../docs/standard/collections/sorted-collection-types.md)|Opisuje kolekcje posortowane wydajności i właściwości|  
|[Typy kolekcji: słownikowy i tabela skrótów](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Opisuje funkcje typów ogólnych i nieogólnych słownika bazujących na skrótach.|  
|[Kolekcje bezpieczne wątkowo](../../../docs/standard/collections/thread-safe/index.md)|Opisuje typy kolekcji, takie jak <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> i <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> obsługujące bezpieczny i skuteczny równoczesny dostęp z wielu wątków.|  
|System.Collections.Immutable|Wprowadza kolekcje niezmienialne i dostarcza łącza do typów kolekcji.|  
  
<a name="BKMK_Reference"></a>   
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Array?displayProperty=nameWithType>  
 <xref:System.Collections?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.Specialized?displayProperty=nameWithType>  
 <xref:System.Linq?displayProperty=nameWithType>  
 <xref:System.Collections.Immutable>
