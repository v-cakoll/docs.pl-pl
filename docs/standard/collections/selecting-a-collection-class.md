---
title: Wybieranie klasy kolekcji
ms.date: 03/18/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- last-in-first-out collections
- first-in-first-out collections
- collections [.NET Framework], selecting collection class
- indexed collections
- Collections classes
- grouping data in collections, selecting collection class
ms.assetid: ba049f9a-ce87-4cc4-b319-3f75c8ddac8a
ms.openlocfilehash: d79f1ca0d264a5a17306bb66f285b6fbe6b4e7ca
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728487"
---
# <a name="selecting-a-collection-class"></a>Wybieranie klasy kolekcji

Pamiętaj, aby dokładnie wybrać klasę kolekcji. Użycie nieprawidłowego typu może ograniczyć użycie kolekcji.

> [!IMPORTANT]
> Należy unikać używania typów w <xref:System.Collections> przestrzeni nazw. Ogólne i współbieżne wersje kolekcji są zalecane ze względu na ich większe bezpieczeństwo i inne ulepszenia.

Zastanów się nad następującymi pytaniami:

- Czy potrzebujesz listy sekwencyjnej, w której element jest zwykle odrzucany po pobraniu wartości?

  - Jeśli tak, rozważ użycie <xref:System.Collections.Queue> klasy lub klasy <xref:System.Collections.Generic.Queue%601> generycznej, jeśli potrzebujesz funkcji First-In, First-Out (FIFO). Rozważ użycie <xref:System.Collections.Stack> klasy lub klasy <xref:System.Collections.Generic.Stack%601> generycznej, jeśli potrzebujesz zachowania "Last-in, First-Out" (LIFO). Aby bezpiecznie uzyskać dostęp z wielu wątków, użyj współbieżnych wersji <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601>. W przypadku niezmienności należy wziąć pod uwagę <xref:System.Collections.Immutable.ImmutableQueue%601> niezmienne <xref:System.Collections.Immutable.ImmutableStack%601>wersje i.

  - Jeśli nie, rozważ użycie innych kolekcji.

- Czy musisz uzyskać dostęp do elementów w określonej kolejności, takich jak FIFO, LIFO lub losowo?

  - <xref:System.Collections.Queue> Klasy, a także klas ogólnych <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>i <xref:System.Collections.Immutable.ImmutableQueue%601> wszystkie oferują dostęp do FIFO. Aby uzyskać więcej informacji, zobacz [Kiedy używać kolekcji bezpiecznej wątkowo](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).

  - <xref:System.Collections.Stack> Klasy, a także klas ogólnych <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>i <xref:System.Collections.Immutable.ImmutableStack%601> , wszystkie oferują dostęp do kolejki LIFO. Aby uzyskać więcej informacji, zobacz [Kiedy używać kolekcji bezpiecznej wątkowo](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).

  - Klasa <xref:System.Collections.Generic.LinkedList%601> generyczna umożliwia dostęp sekwencyjny od głowy do ogona lub od ogona do głowy.

- Czy musisz uzyskać dostęp do każdego elementu według indeksu?

  - Klasy <xref:System.Collections.ArrayList> i <xref:System.Collections.Specialized.StringCollection> i klasy <xref:System.Collections.Generic.List%601> generycznej oferują dostęp do ich elementów przez indeks (liczony od zera) elementu. W przypadku niezmienności należy wziąć pod uwagę niezmienne <xref:System.Collections.Immutable.ImmutableArray%601> wersje <xref:System.Collections.Immutable.ImmutableList%601>ogólne i.

  - Klasy <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>, <xref:System.Collections.Specialized.StringDictionary> <xref:System.Collections.Generic.Dictionary%602> i i <xref:System.Collections.Generic.SortedDictionary%602> generyczne umożliwiają dostęp do ich elementów za pomocą klucza elementu. Ponadto istnieją niezmienne wersje kilku odpowiednich typów <xref:System.Collections.Immutable.ImmutableHashSet%601>:, <xref:System.Collections.Immutable.ImmutableDictionary%602>, <xref:System.Collections.Immutable.ImmutableSortedSet%601>, i. <xref:System.Collections.Immutable.ImmutableSortedDictionary%602>

  - Klasy <xref:System.Collections.Specialized.NameObjectCollectionBase> i <xref:System.Collections.Specialized.NameValueCollection> <xref:System.Collections.ObjectModel.KeyedCollection%602> i klasy <xref:System.Collections.Generic.SortedList%602> generyczne oferują dostęp do swoich elementów przez indeks lub klucz elementu.

- Czy każdy element będzie zawierać jedną wartość, kombinację jednego klucza i jedną wartość, czy kombinację jednego klucza i wielu wartości?

  - Jedna wartość: Użyj dowolnej kolekcji na podstawie <xref:System.Collections.IList> interfejsu lub interfejsu <xref:System.Collections.Generic.IList%601> ogólnego. W przypadku niezmiennej opcji Rozważ <xref:System.Collections.Immutable.IImmutableList%601> użycie interfejsu ogólnego.

  - Jeden klucz i jedna wartość: Użyj dowolnej kolekcji na podstawie <xref:System.Collections.IDictionary> interfejsu lub interfejsu <xref:System.Collections.Generic.IDictionary%602> ogólnego. W przypadku niezmiennej opcji Rozważ <xref:System.Collections.Immutable.IImmutableSet%601> użycie <xref:System.Collections.Immutable.IImmutableDictionary%602> interfejsów ogólnych lub.

  - Jedna wartość z kluczem osadzonym: Użyj <xref:System.Collections.ObjectModel.KeyedCollection%602> klasy generycznej.

  - Jeden klucz i wiele wartości: Użyj <xref:System.Collections.Specialized.NameValueCollection> klasy.

- Czy należy posortować elementy inaczej niż w sposobie ich wprowadzania?

  - <xref:System.Collections.Hashtable> Klasa sortuje swoje elementy według ich kodów skrótu.

  - <xref:System.Collections.SortedList> Klasy i <xref:System.Collections.Generic.SortedList%602> klasy <xref:System.Collections.Generic.SortedDictionary%602> generyczne sortują ich elementy według klucza. Kolejność sortowania jest oparta <xref:System.Collections.IComparer> na implementacji interfejsu <xref:System.Collections.SortedList> klasy i implementacji interfejsu <xref:System.Collections.Generic.IComparer%601> generycznego dla klas <xref:System.Collections.Generic.SortedList%602> i. <xref:System.Collections.Generic.SortedDictionary%602> W przypadku dwóch typów ogólnych program <xref:System.Collections.Generic.SortedDictionary%602> zapewnia lepszą wydajność niż <xref:System.Collections.Generic.SortedList%602>, a <xref:System.Collections.Generic.SortedList%602> jednocześnie zużywa mniejszą ilość pamięci.

  - <xref:System.Collections.ArrayList>dostarcza <xref:System.Collections.ArrayList.Sort%2A> metodę, która przyjmuje <xref:System.Collections.IComparer> jako parametr. Jego ogólny odpowiednik, Klasa <xref:System.Collections.Generic.List%601> generyczna, zapewnia <xref:System.Collections.Generic.List%601.Sort%2A> metodę, która pobiera implementację interfejsu <xref:System.Collections.Generic.IComparer%601> generycznego jako parametr.

- Potrzebujesz szybkiego wyszukiwania i pobierania informacji?

  - <xref:System.Collections.Specialized.ListDictionary>jest szybsza niż <xref:System.Collections.Hashtable> w przypadku małych kolekcji (10 elementów lub mniej). Klasa <xref:System.Collections.Generic.Dictionary%602> generyczna zapewnia szybsze wyszukiwanie niż Klasa <xref:System.Collections.Generic.SortedDictionary%602> ogólna. Implementacja wielowątkowa <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601>zapewnia szybki Wstawianie wielowątkowe dla nieuporządkowanych danych. Aby uzyskać więcej informacji na temat typów wielowątkowych, zobacz [Kiedy używać kolekcji z bezpiecznymi wątkami](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).

- Czy potrzebne są kolekcje akceptujące tylko ciągi?

  - <xref:System.Collections.Specialized.StringCollection>(w oparciu <xref:System.Collections.IList>o) <xref:System.Collections.Specialized.StringDictionary> i (na <xref:System.Collections.IDictionary>podstawie) znajdują <xref:System.Collections.Specialized> się w przestrzeni nazw.

  - Ponadto można użyć dowolnych klas kolekcji ogólnych w <xref:System.Collections.Generic> przestrzeni nazw jako kolekcje ciągów z jednoznacznie określonymi typami przez określenie <xref:System.String> klasy dla argumentów typu ogólnego. Na przykład można zadeklarować zmienną jako ciąg [\<listy typu>](xref:System.Collections.Generic.List%601) lub [<ciągu,>](xref:System.Collections.Generic.Dictionary%602).

## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects i PLINQ

LINQ to Objects umożliwia deweloperom używanie zapytań LINQ do uzyskiwania dostępu do obiektów w pamięci, o ile typ obiektu implementuje <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>. Zapytania LINQ zapewniają wspólny wzorzec dostępu do danych, są zwykle bardziej zwięzłe i czytelne niż `foreach` standardowe pętle oraz zapewniają możliwości filtrowania, porządkowania i grupowania. Aby uzyskać więcej informacji, zobacz [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) i [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).

PLINQ zapewnia równoległą implementację LINQ to Objects, która może oferować szybsze wykonywanie zapytań w wielu scenariuszach dzięki wydajniejszemu używaniu komputerów z wieloma rdzeniami. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [Kolekcje bezpieczne dla wątków](../../../docs/standard/collections/thread-safe/index.md)
