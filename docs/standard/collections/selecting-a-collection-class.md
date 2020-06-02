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
ms.openlocfilehash: 62f4f768753637043ab91219cfb63c741a194b96
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287929"
---
# <a name="selecting-a-collection-class"></a>Wybieranie klasy kolekcji

Pamiętaj, aby dokładnie wybrać klasę kolekcji. Użycie nieprawidłowego typu może ograniczyć użycie kolekcji.

> [!IMPORTANT]
> Należy unikać używania typów w <xref:System.Collections> przestrzeni nazw. Ogólne i współbieżne wersje kolekcji są zalecane ze względu na ich większe bezpieczeństwo i inne ulepszenia.

Zastanów się nad następującymi pytaniami:

- Czy potrzebujesz listy sekwencyjnej, w której element jest zwykle odrzucany po pobraniu wartości?

  - Jeśli tak, rozważ użycie <xref:System.Collections.Queue> klasy lub <xref:System.Collections.Generic.Queue%601> klasy generycznej, jeśli potrzebujesz funkcji First-In, First-Out (FIFO). Rozważ użycie <xref:System.Collections.Stack> klasy lub <xref:System.Collections.Generic.Stack%601> klasy generycznej, jeśli potrzebujesz zachowania "Last-in, First-Out" (LIFO). Aby bezpiecznie uzyskać dostęp z wielu wątków, użyj współbieżnych wersji <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601> . W przypadku niezmienności należy wziąć pod uwagę niezmienne wersje <xref:System.Collections.Immutable.ImmutableQueue%601> i <xref:System.Collections.Immutable.ImmutableStack%601> .

  - Jeśli nie, rozważ użycie innych kolekcji.

- Czy musisz uzyskać dostęp do elementów w określonej kolejności, takich jak FIFO, LIFO lub losowo?

  - <xref:System.Collections.Queue>Klasy, <xref:System.Collections.Generic.Queue%601> a także <xref:System.Collections.Concurrent.ConcurrentQueue%601> klas ogólnych, i <xref:System.Collections.Immutable.ImmutableQueue%601> wszystkie oferują dostęp do FIFO. Aby uzyskać więcej informacji, zobacz [Kiedy używać kolekcji bezpiecznej wątkowo](thread-safe/when-to-use-a-thread-safe-collection.md).

  - <xref:System.Collections.Stack>Klasy, <xref:System.Collections.Generic.Stack%601> a także <xref:System.Collections.Concurrent.ConcurrentStack%601> klas ogólnych, i, <xref:System.Collections.Immutable.ImmutableStack%601> wszystkie oferują dostęp do kolejki LIFO. Aby uzyskać więcej informacji, zobacz [Kiedy używać kolekcji bezpiecznej wątkowo](thread-safe/when-to-use-a-thread-safe-collection.md).

  - <xref:System.Collections.Generic.LinkedList%601>Klasa generyczna umożliwia dostęp sekwencyjny od głowy do ogona lub od ogona do głowy.

- Czy musisz uzyskać dostęp do każdego elementu według indeksu?

  - Klasy <xref:System.Collections.ArrayList> i <xref:System.Collections.Specialized.StringCollection> i <xref:System.Collections.Generic.List%601> klasy generycznej oferują dostęp do ich elementów przez indeks (liczony od zera) elementu. W przypadku niezmienności należy wziąć pod uwagę niezmienne wersje ogólne <xref:System.Collections.Immutable.ImmutableArray%601> i <xref:System.Collections.Immutable.ImmutableList%601> .

  - <xref:System.Collections.Hashtable>Klasy, <xref:System.Collections.SortedList> , <xref:System.Collections.Specialized.ListDictionary> , i i <xref:System.Collections.Specialized.StringDictionary> <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.Generic.SortedDictionary%602> generyczne umożliwiają dostęp do ich elementów za pomocą klucza elementu. Ponadto istnieją niezmienne wersje kilku odpowiednich typów: <xref:System.Collections.Immutable.ImmutableHashSet%601> , <xref:System.Collections.Immutable.ImmutableDictionary%602> , <xref:System.Collections.Immutable.ImmutableSortedSet%601> , i <xref:System.Collections.Immutable.ImmutableSortedDictionary%602> .

  - Klasy <xref:System.Collections.Specialized.NameObjectCollectionBase> i i <xref:System.Collections.Specialized.NameValueCollection> <xref:System.Collections.ObjectModel.KeyedCollection%602> <xref:System.Collections.Generic.SortedList%602> klasy generyczne oferują dostęp do swoich elementów przez indeks lub klucz elementu.

- Czy każdy element będzie zawierać jedną wartość, kombinację jednego klucza i jedną wartość, czy kombinację jednego klucza i wielu wartości?

  - Jedna wartość: Użyj dowolnej kolekcji na podstawie <xref:System.Collections.IList> interfejsu lub <xref:System.Collections.Generic.IList%601> interfejsu ogólnego. W przypadku niezmiennej opcji Rozważ użycie <xref:System.Collections.Immutable.IImmutableList%601> interfejsu ogólnego.

  - Jeden klucz i jedna wartość: Użyj dowolnej kolekcji na podstawie <xref:System.Collections.IDictionary> interfejsu lub <xref:System.Collections.Generic.IDictionary%602> interfejsu ogólnego. W przypadku niezmiennej opcji Rozważ <xref:System.Collections.Immutable.IImmutableSet%601> użycie <xref:System.Collections.Immutable.IImmutableDictionary%602> interfejsów ogólnych lub.

  - Jedna wartość z kluczem osadzonym: Użyj <xref:System.Collections.ObjectModel.KeyedCollection%602> klasy generycznej.

  - Jeden klucz i wiele wartości: Użyj <xref:System.Collections.Specialized.NameValueCollection> klasy.

- Czy należy posortować elementy inaczej niż w sposobie ich wprowadzania?

  - <xref:System.Collections.Hashtable>Klasa sortuje swoje elementy według ich kodów skrótu.

  - <xref:System.Collections.SortedList>Klasy i <xref:System.Collections.Generic.SortedList%602> <xref:System.Collections.Generic.SortedDictionary%602> klasy generyczne sortują ich elementy według klucza. Kolejność sortowania jest oparta na implementacji <xref:System.Collections.IComparer> interfejsu <xref:System.Collections.SortedList> klasy i implementacji <xref:System.Collections.Generic.IComparer%601> interfejsu generycznego dla <xref:System.Collections.Generic.SortedList%602> <xref:System.Collections.Generic.SortedDictionary%602> klas i. W przypadku dwóch typów ogólnych program <xref:System.Collections.Generic.SortedDictionary%602> zapewnia lepszą wydajność niż <xref:System.Collections.Generic.SortedList%602> , a jednocześnie <xref:System.Collections.Generic.SortedList%602> zużywa mniejszą ilość pamięci.

  - <xref:System.Collections.ArrayList>dostarcza <xref:System.Collections.ArrayList.Sort%2A> metodę, która przyjmuje <xref:System.Collections.IComparer> jako parametr. Jego ogólny odpowiednik, <xref:System.Collections.Generic.List%601> Klasa generyczna, zapewnia <xref:System.Collections.Generic.List%601.Sort%2A> metodę, która pobiera implementację <xref:System.Collections.Generic.IComparer%601> interfejsu generycznego jako parametr.

- Potrzebujesz szybkiego wyszukiwania i pobierania informacji?

  - <xref:System.Collections.Specialized.ListDictionary>jest szybsza niż <xref:System.Collections.Hashtable> w przypadku małych kolekcji (10 elementów lub mniej). <xref:System.Collections.Generic.Dictionary%602>Klasa generyczna zapewnia szybsze wyszukiwanie niż <xref:System.Collections.Generic.SortedDictionary%602> Klasa ogólna. Implementacja wielowątkowa <xref:System.Collections.Concurrent.ConcurrentDictionary%602> . <xref:System.Collections.Concurrent.ConcurrentBag%601>zapewnia szybki Wstawianie wielowątkowe dla nieuporządkowanych danych. Aby uzyskać więcej informacji na temat typów wielowątkowych, zobacz [Kiedy używać kolekcji z bezpiecznymi wątkami](thread-safe/when-to-use-a-thread-safe-collection.md).

- Czy potrzebne są kolekcje akceptujące tylko ciągi?

  - <xref:System.Collections.Specialized.StringCollection>(na podstawie <xref:System.Collections.IList> ) i <xref:System.Collections.Specialized.StringDictionary> (na podstawie <xref:System.Collections.IDictionary> ) znajdują się w <xref:System.Collections.Specialized> przestrzeni nazw.

  - Ponadto można użyć dowolnych klas kolekcji ogólnych w <xref:System.Collections.Generic> przestrzeni nazw jako kolekcje ciągów z jednoznacznie określonymi typami przez określenie <xref:System.String> klasy dla argumentów typu ogólnego. Na przykład, można zadeklarować zmienną jako typ [listy \<String> ](xref:System.Collections.Generic.List%601) lub [słownika<String, ciąg>](xref:System.Collections.Generic.Dictionary%602).

## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects i PLINQ

LINQ to Objects umożliwia deweloperom używanie zapytań LINQ do uzyskiwania dostępu do obiektów w pamięci, o ile typ obiektu implementuje <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> . Zapytania LINQ zapewniają wspólny wzorzec dostępu do danych, są zwykle bardziej zwięzłe i czytelne niż standardowe `foreach` pętle oraz zapewniają możliwości filtrowania, porządkowania i grupowania. Aby uzyskać więcej informacji, zobacz [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) i [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).

PLINQ zapewnia równoległą implementację LINQ to Objects, która może oferować szybsze wykonywanie zapytań w wielu scenariuszach dzięki wydajniejszemu używaniu komputerów z wieloma rdzeniami. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [Kolekcje bezpieczne dla wątków](thread-safe/index.md)
