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
ms.openlocfilehash: 9b868bd5ed77788cd9b44c11623ae38eba58153c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711366"
---
# <a name="collections-and-data-structures"></a>Kolekcje i struktury danych
Podobne dane często można obsługiwać wydajniej, gdy są przechowywane i przetwarzane jako kolekcja. Można użyć klasy <xref:System.Array?displayProperty=nameWithType> lub klas w przestrzeniach nazw <xref:System.Collections>, <xref:System.Collections.Generic>, <xref:System.Collections.Concurrent>, system. Collections. niezmienne, aby dodawać, usuwać i modyfikować pojedyncze elementy lub zakres elementów w kolekcji.  
  
 Istnieją dwa główne typy kolekcji: Kolekcje ogólne i kolekcje inne niż ogólne. Kolekcje ogólne zostały dodane w .NET Framework 2,0 i zapewniają kolekcje, które są bezpieczne dla typów w czasie kompilacji. Z tego względu kolekcje ogólne zazwyczaj oferują lepszą wydajność. Kolekcje ogólne akceptują parametr typu podczas jego konstruowania i nie wymagają rzutowania na i z typu <xref:System.Object> podczas dodawania lub usuwania elementów z kolekcji.  Ponadto większość ogólnych kolekcji jest obsługiwana w aplikacjach ze sklepu Windows. Kolekcje inne niż ogólne przechowują elementy jako <xref:System.Object>, wymagają rzutowania i większość nie są obsługiwane w przypadku tworzenia aplikacji do sklepu Windows. Nieogólne kolekcje mogą jednak być widoczne w starszym kodzie.  
  
 Począwszy od .NET Framework 4, kolekcje w przestrzeni nazw <xref:System.Collections.Concurrent> zapewniają wydajne, bezpieczne dla wątków operacje umożliwiające dostęp do elementów kolekcji z wielu wątków. Niezmienne klasy kolekcji w System. Collections. niezmienna przestrzeń nazw ([pakiet NuGet](https://www.nuget.org/packages/System.Collections.Immutable)) są z natury bezpieczne wątkowo, ponieważ operacje są wykonywane na kopii oryginalnej kolekcji, a oryginalna kolekcja nie może być modyfikowana.  

<a name="BKMK_Commoncollectionfeatures"></a>   
## <a name="common-collection-features"></a>Wspólne funkcje kolekcji  
 Wszystkie kolekcje zapewniają metody dodawania, usuwania lub znajdowania elementów w kolekcji. Ponadto wszystkie kolekcje, które bezpośrednio lub pośrednio implementują interfejs <xref:System.Collections.ICollection> lub interfejs <xref:System.Collections.Generic.ICollection%601>, udostępniają następujące funkcje:  
  
- **Możliwość wyliczenia kolekcji**  
  
     Kolekcje .NET Framework implementują <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>, aby umożliwić iterację kolekcji. Moduł wyliczający może być uważany za przenośny wskaźnik do dowolnego elementu w kolekcji. Instrukcja [foreach, in](../../csharp/language-reference/keywords/foreach-in.md) i [for each... Następna instrukcja](../../visual-basic/language-reference/statements/for-each-next-statement.md) wykorzystuje moduł wyliczający uwidoczniony przez metodę <xref:System.Collections.IEnumerable.GetEnumerator%2A> i ukrywając złożoność manipulowania modułem wyliczającym. Ponadto każda kolekcja implementująca <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> jest traktowana jako *Typ Queryable* i może być zbadana przy użyciu LINQ. Zapytania LINQ zapewniają wspólny wzorzec uzyskiwania dostępu do danych. Są one zazwyczaj bardziej zwięzłe i czytelne niż standardowe pętle `foreach` i umożliwiają filtrowanie, porządkowanie i grupowanie. Zapytania LINQ mogą również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ to ObjectsC#()](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md), [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), [Introduction to QueryC#LINQ ()](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)i [podstawowe operacje zapytań (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
- **Możliwość kopiowania zawartości kolekcji do tablicy**  
  
     Wszystkie kolekcje można skopiować do tablicy przy użyciu metody **CopyTo** ; Jednak kolejność elementów w nowej tablicy zależy od kolejności, w której moduł wyliczający zwraca te elementy. Tablica wyników jest zawsze jednowymiarowa z dolną granicą zero.  
  
 Ponadto wiele klas kolekcji zawiera następujące funkcje:  
  
- **Właściwości pojemności i liczby**  
  
     Pojemność kolekcji to liczba elementów, które może zawierać. Liczba kolekcji to liczba elementów, które faktycznie zawiera. Niektóre kolekcje ukrywają pojemność lub liczbę lub oba te elementy.  
  
     Większość kolekcji zostanie automatycznie rozszerzona o pojemności, gdy osiągnięto bieżącą pojemność. Pamięć zostanie ponownie przyalokowana, a elementy są kopiowane ze starej kolekcji do nowej. Zmniejsza to kod wymagany do korzystania z kolekcji; Jednak może to mieć negatywny wpływ na wydajność kolekcji. Na przykład w przypadku <xref:System.Collections.Generic.List%601>, jeśli <xref:System.Collections.Generic.List%601.Count%2A> jest mniejsza niż <xref:System.Collections.Generic.List%601.Capacity%2A>, dodanie elementu jest operacją O (1). Jeśli pojemność musi zostać zwiększona w celu uwzględnienia nowego elementu, dodanie elementu zostanie operacją O (n), gdzie n jest <xref:System.Collections.Generic.List%601.Count%2A>. Najlepszym sposobem, aby uniknąć niskiej wydajności spowodowanej przez wiele ponownych alokacji, jest ustawienie początkowej pojemności do szacowanego rozmiaru kolekcji.  
  
     <xref:System.Collections.BitArray> jest szczególnym przypadkiem; jego pojemność jest taka sama jak jej długość, która jest taka sama jak liczba.  
  
- **Spójna Dolna granica**  
  
     Dolna granica kolekcji jest indeksem jego pierwszego elementu. Wszystkie indeksowane kolekcje w przestrzeniach nazw <xref:System.Collections> mają dolną granicę równą zero, co oznacza, że są one indeksowane przez 0. Domyślnie <xref:System.Array> ma dolną granicę równą zero, ale podczas tworzenia wystąpienia klasy **Array** przy użyciu <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>można zdefiniować inną dolną granicę.  
  
- **Synchronizacja w celu uzyskania dostępu z wielu wątków** (tylko klasy<xref:System.Collections>).  
  
     Typy kolekcji nieogólnej w przestrzeni nazw <xref:System.Collections> zapewniają bezpieczeństwo wątku z synchronizacją; zwykle uwidaczniane przez <xref:System.Collections.ICollection.SyncRoot%2A> i <xref:System.Collections.ICollection.IsSynchronized%2A> członków. Kolekcje te nie są domyślnie bezpieczne dla wątków. Jeśli jest wymagany skalowalny i wydajny dostęp wielowątkowy do kolekcji, użyj jednej z klas w przestrzeni nazw <xref:System.Collections.Concurrent> lub Rozważ użycie niezmiennej kolekcji. Aby uzyskać więcej informacji, zobacz [kolekcje bezpieczne dla wątków](../../../docs/standard/collections/thread-safe/index.md).  
  
<a name="BKMK_Choosingacollection"></a>   
## <a name="choosing-a-collection"></a>Wybieranie kolekcji  
 Ogólnie rzecz biorąc, należy używać kolekcji ogólnych. W poniższej tabeli opisano niektóre typowe scenariusze zbierania danych oraz klasy kolekcji, których można użyć w tych scenariuszach. Jeśli dopiero zaczynasz kolekcje ogólne, ta tabela ułatwi wybór ogólnej kolekcji, która działa najlepiej dla danego zadania.  
 
|Chcę...|Ogólne opcje kolekcji|Opcje kolekcji inne niż ogólne|Opcje kolekcji bezpieczne dla wątków lub niemodyfikowalne|  
|-|-|-|-|  
|Przechowywanie elementów jako par klucz/wartość na potrzeby szybkiego wyszukiwania według klucza|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Kolekcja par klucz/wartość, które są zorganizowane na podstawie kodu skrótu klucza).|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|  
|Dostęp do elementów według indeksu|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|  
|Korzystanie z elementów First-In-First-Out (FIFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|  
|Korzystanie z danych — Data ostatniej realizacji (LIFO)|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|  
|Uzyskuj dostęp do elementów sekwencyjnie|<xref:System.Collections.Generic.LinkedList%601>|Brak zaleceń|Brak zaleceń|  
|Otrzymuj powiadomienia, gdy elementy są usuwane lub dodawane do kolekcji. (implementuje <xref:System.ComponentModel.INotifyPropertyChanged> i <xref:System.Collections.Specialized.INotifyCollectionChanged>)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Brak zaleceń|Brak zaleceń|  
|Posortowana kolekcja|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
|Zestaw funkcji matematycznych|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Brak zaleceń|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
  
<a name="BKMK_RelatedTopics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wybieranie klasy kolekcji](../../../docs/standard/collections/selecting-a-collection-class.md)|Opisuje różne kolekcje i pomaga wybrać jedną z nich dla danego scenariusza.|  
|[Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)|Opisuje powszechnie używane typy ogólnej i nieogólnej kolekcji, takie jak <xref:System.Array?displayProperty=nameWithType>, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>i <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.|  
|[Kiedy należy używać kolekcji ogólnych](../../../docs/standard/collections/when-to-use-generic-collections.md)|Omawia użycie rodzajowych typów kolekcji.|  
|[Porównywanie i sortowanie w ramach kolekcji](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|Omawia użycie porównania równości i sortowania w kolekcjach.|  
|[Sortowane typy kolekcji](../../../docs/standard/collections/sorted-collection-types.md)|Opisuje informacje o wydajności i cechach posortowanych kolekcji|  
|[Typy kolekcji: słownikowy i tabela skrótów](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Opisuje funkcje rodzajowych i nieogólnych typów słowników opartych na skrótach.|  
|[Kolekcje bezpieczne wątkowo](../../../docs/standard/collections/thread-safe/index.md)|Opisuje typy kolekcji, takie jak <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> i <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>, które obsługują bezpieczny i wydajny dostęp współbieżny z wielu wątków.|  
|System.Collections.Immutable|Wprowadza Niezmienne kolekcje i oferuje linki do typów kolekcji.|  
  
<a name="BKMK_Reference"></a>   
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Array?displayProperty=nameWithType>  
 <xref:System.Collections?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.Specialized?displayProperty=nameWithType>  
 <xref:System.Linq?displayProperty=nameWithType>  
 <xref:System.Collections.Immutable>
