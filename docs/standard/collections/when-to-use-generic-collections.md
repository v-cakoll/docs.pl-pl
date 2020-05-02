---
title: Kiedy należy używać kolekcji ogólnych
ms.date: 04/30/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: feccd8c53e5171889666ed407258b9d36ad8a140
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728199"
---
# <a name="when-to-use-generic-collections"></a>Kiedy należy używać kolekcji ogólnych

Korzystanie z kolekcji ogólnych zapewnia automatyczną korzyść typu "bezpieczeństwo" bez konieczności wyprowadzania z podstawowego typu kolekcji i implementowania elementów członkowskich specyficznych dla typu. Ogólne typy kolekcji są również zwykle wykonywane lepiej niż odpowiednie typy kolekcji nieogólnej (i lepsza niż typy, które są uzyskiwane z nieogólnych typów kolekcji podstawowych), gdy elementy kolekcji są typami wartości, ponieważ z ogólnymi, nie ma potrzeby używania elementów.

W przypadku programów przeznaczonych dla .NET Standard 1,0 lub nowszych Użyj klas kolekcji ogólnych w <xref:System.Collections.Concurrent> przestrzeni nazw, gdy wiele wątków może jednocześnie dodawać lub usuwać elementy z kolekcji. Ponadto w przypadku pożądanego niezmienności należy wziąć pod uwagę klasy kolekcji generycznej w <xref:System.Collections.Immutable> przestrzeni nazw.

Następujące typy ogólne odpowiadają istniejącym typom kolekcji:

- <xref:System.Collections.Generic.List%601>jest klasą rodzajową, która odnosi się do <xref:System.Collections.ArrayList>.

- <xref:System.Collections.Generic.Dictionary%602>i <xref:System.Collections.Concurrent.ConcurrentDictionary%602> są klasami ogólnymi, które <xref:System.Collections.Hashtable>odpowiadają.

- <xref:System.Collections.ObjectModel.Collection%601>jest klasą rodzajową, która odnosi się do <xref:System.Collections.CollectionBase>. <xref:System.Collections.ObjectModel.Collection%601>może być używana jako klasa bazowa, ale w przeciwieństwie <xref:System.Collections.CollectionBase>do siebie, nie jest abstrakcyjna, co znacznie ułatwia użycie.

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>jest klasą rodzajową, która odnosi się do <xref:System.Collections.ReadOnlyCollectionBase>. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>nie jest abstrakcyjny i ma konstruktora, który ułatwia udostępnianie istniejącej <xref:System.Collections.Generic.List%601> jako kolekcji tylko do odczytu.

- Klasy <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Immutable.ImmutableQueue%601>, <xref:System.Collections.Immutable.ImmutableArray%601> <xref:System.Collections.Generic.SortedList%602>, i <xref:System.Collections.Immutable.ImmutableSortedSet%601> ogólne odpowiadają odpowiednim klasom nieogólnym o tych samych nazwach.

## <a name="additional-types"></a>Dodatkowe typy

Kilka rodzajowych typów kolekcji nie ma odpowiedników nierodzajowych. Należą do nich następujące elementy:

- <xref:System.Collections.Generic.LinkedList%601>jest listą połączoną ogólnego przeznaczenia, która zapewnia operacje wstawiania i usuwania O (1).

- <xref:System.Collections.Generic.SortedDictionary%602>to posortowany słownik z operacjami `n`wstawiania i pobierania (log), co sprawia, że jest to <xref:System.Collections.Generic.SortedList%602>użyteczna alternatywa dla programu.

- <xref:System.Collections.ObjectModel.KeyedCollection%602>jest hybrydem między listą a słownikiem, który umożliwia przechowywanie obiektów zawierających własne klucze.

- <xref:System.Collections.Concurrent.BlockingCollection%601>implementuje klasę kolekcji z funkcją ograniczenia i blokowania.

- <xref:System.Collections.Concurrent.ConcurrentBag%601>umożliwia szybkie Wstawianie i usuwanie nieuporządkowanych elementów.

### <a name="immutable-builders"></a>Niezmienne kompilacje

W przypadku chęci niezmienności funkcjonalności w aplikacji <xref:System.Collections.Immutable> przestrzeń nazw oferuje ogólne typy kolekcji, których można użyć. Wszystkie niezmienne typy kolekcji oferują `Builder` klasy, które mogą zoptymalizować wydajność podczas wykonywania wielu mutacji. Operacje `Builder` wsadowe klasy są w stanie modyfikowalnym. Gdy wszystkie mutacje zostały ukończone, wywołaj metodę `ToImmutable` , aby "zamrozić" wszystkie węzły i utworzyć niemodyfikowalną kolekcję ogólną, na przykład <xref:System.Collections.Immutable.ImmutableList%601>.

`Builder` Obiekt można utworzyć, wywołując metodę nierodzajową `CreateBuilder()` . Z `Builder` wystąpienia można wywołać `ToImmutable()`. Podobnie, z `Immutable*` kolekcji można wywołać `ToBuilder()` , aby utworzyć wystąpienie konstruktora z ogólnej niezmiennej kolekcji. Poniżej przedstawiono różne `Builder` typy.

- <xref:System.Collections.Immutable.ImmutableArray%601.Builder>
- <xref:System.Collections.Immutable.ImmutableDictionary%602.Builder>
- <xref:System.Collections.Immutable.ImmutableHashSet%601.Builder>
- <xref:System.Collections.Immutable.ImmutableList%601.Builder>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary%602.Builder>
- <xref:System.Collections.Immutable.ImmutableSortedSet%601.Builder>

## <a name="linq-to-objects"></a>LINQ do obiektów

Funkcja LINQ to Objects umożliwia używanie zapytań LINQ do uzyskiwania dostępu do obiektów w pamięci, o ile typ obiektu implementuje interfejs <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub. <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> Zapytania LINQ zapewniają wspólny wzorzec dostępu do danych; są zwykle bardziej zwięzłe i czytelne `foreach` niż standardowe pętle; i umożliwiają filtrowanie, porządkowanie i grupowanie. Zapytania LINQ mogą również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)i [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md).

## <a name="additional-functionality"></a>Dodatkowe funkcje
Niektóre typy ogólne mają funkcje, które nie znajdują się w nierodzajowych typach kolekcji. <xref:System.Collections.Generic.List%601> Na przykład Klasa, która odnosi się do klasy niegenerycznej <xref:System.Collections.ArrayList> , ma wiele metod, które akceptują delegatów ogólnych, takich jak <xref:System.Predicate%601> delegat, który umożliwia określenie metod wyszukiwania listy, <xref:System.Action%601> delegat reprezentuje metody, które działają na każdym elemencie listy, i <xref:System.Converter%602> delegata, który umożliwia definiowanie konwersji między typami.

<xref:System.Collections.Generic.List%601> Klasa pozwala określić własne <xref:System.Collections.Generic.IComparer%601> implementacje interfejsu ogólnego do sortowania i przeszukiwania listy. Klasy <xref:System.Collections.Generic.SortedDictionary%602> i <xref:System.Collections.Generic.SortedList%602> również mają tę możliwość. Ponadto klasy te umożliwiają określanie porównań podczas tworzenia kolekcji. W podobny sposób klasy <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.ObjectModel.KeyedCollection%602> pozwalają określić własne porównania równości.

## <a name="see-also"></a>Zobacz także

- [Kolekcje i struktury danych](../../../docs/standard/collections/index.md)
- [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
- [Typy ogólne](../../../docs/standard/generics/index.md)
