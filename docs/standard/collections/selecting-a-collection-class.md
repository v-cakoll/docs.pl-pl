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
ms.openlocfilehash: 621d64183c1cacc14c2d432e4eef43f4d3ba5474
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588326"
---
# <a name="selecting-a-collection-class"></a>Wybieranie klasy kolekcji

Pamiętaj, aby starannie wybrać klasę kolekcji. Przy użyciu niewłaściwego typu można ograniczyć korzystanie z kolekcji.  

> [!IMPORTANT]
> Należy unikać używania <xref:System.Collections> typów w obszarze nazw. Ogólne i równoczesnych wersji kolekcji są zalecane ze względu na ich większe bezpieczeństwo typu i inne ulepszenia.  

 Zastanów się nad następującymi pytaniami:  
  
- Czy potrzebna jest lista sekwencyjna, na której element jest zazwyczaj odrzucany po pobraniu jego wartości?  
  
  - Jeśli tak, należy <xref:System.Collections.Queue> rozważyć <xref:System.Collections.Generic.Queue%601> użycie klasy lub klasy ogólnej, jeśli potrzebujesz pierwszego w, first-out (FIFO) zachowanie. Należy rozważyć <xref:System.Collections.Stack> użycie <xref:System.Collections.Generic.Stack%601> klasy lub klasy ogólnej, jeśli potrzebujesz last-in, first-out (LIFO) zachowanie. Aby zapewnić bezpieczny dostęp z wielu wątków, <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Concurrent.ConcurrentStack%601>należy użyć równoczesnych wersji i .  
  
  - Jeśli nie, należy rozważyć użycie innych kolekcji.  
  
- Czy musisz uzyskać dostęp do elementów w określonej kolejności, takich jak FIFO, LIFO lub losowe?  
  
  - Klasa <xref:System.Collections.Queue> i <xref:System.Collections.Generic.Queue%601> klasa <xref:System.Collections.Concurrent.ConcurrentQueue%601> lub klasy ogólnej oferują dostęp FIFO. Aby uzyskać więcej informacji, zobacz [Kiedy używać kolekcji bezpiecznej dla wątków](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - Klasa <xref:System.Collections.Stack> i <xref:System.Collections.Generic.Stack%601> klasa <xref:System.Collections.Concurrent.ConcurrentStack%601> lub klasa ogólna oferują dostęp LIFO. Aby uzyskać więcej informacji, zobacz [Kiedy używać kolekcji bezpiecznej dla wątków](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - Klasa <xref:System.Collections.Generic.LinkedList%601> ogólna umożliwia dostęp sekwencyjny od głowy do ogona lub od ogona do głowy.  
  
- Czy musisz uzyskać dostęp do każdego elementu według indeksu?  
  
  - Klasy <xref:System.Collections.ArrayList> <xref:System.Collections.Specialized.StringCollection> i klasy <xref:System.Collections.Generic.List%601> ogólne oferują dostęp do ich elementów za pomocą indeksu opartego na wartości zero elementu.  
  
  - Klasy <xref:System.Collections.Hashtable> <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>, <xref:System.Collections.Specialized.StringDictionary> i klasy <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.Generic.SortedDictionary%602> i klasy ogólne oferują dostęp do ich elementów za pomocą klucza elementu.  
  
  - Klasy <xref:System.Collections.Specialized.NameObjectCollectionBase> <xref:System.Collections.Specialized.NameValueCollection> i klasy <xref:System.Collections.ObjectModel.KeyedCollection%602> ogólne <xref:System.Collections.Generic.SortedList%602> i klasy ogólne oferują dostęp do ich elementów za pomocą indeksu opartego na wartości zero lub klucza elementu.  
  
- Czy każdy element zawiera jedną wartość, kombinację jednego klucza i jednej wartości lub kombinację jednego klucza i wielu wartości?  
  
  - Jedna wartość: Użyj dowolnej kolekcji <xref:System.Collections.IList> na podstawie <xref:System.Collections.Generic.IList%601> interfejsu lub interfejsu ogólnego.  
  
  - Jeden klucz i jedna wartość: Użyj dowolnej <xref:System.Collections.IDictionary> kolekcji <xref:System.Collections.Generic.IDictionary%602> na podstawie interfejsu lub interfejsu ogólnego.  
  
  - Jedna wartość z kluczem <xref:System.Collections.ObjectModel.KeyedCollection%602> osadzonym: Użyj klasy ogólnej.  
  
  - Jeden klucz i wiele <xref:System.Collections.Specialized.NameValueCollection> wartości: Użyj klasy.  
  
- Czy musisz sortować elementy inaczej niż w jaki sposób zostały wprowadzone?  
  
  - Klasa <xref:System.Collections.Hashtable> sortuje swoje elementy według ich kodów skrótu.  
  
  - Klasa <xref:System.Collections.SortedList> i <xref:System.Collections.Generic.SortedList%602> klasy <xref:System.Collections.Generic.SortedDictionary%602> ogólne sortowania ich elementów według klucza. Kolejność sortowania opiera się na <xref:System.Collections.IComparer> implementacji <xref:System.Collections.SortedList> interfejsu dla klasy <xref:System.Collections.Generic.IComparer%601> i na <xref:System.Collections.Generic.SortedList%602> implementacji interfejsu ogólnego dla klas ogólnych i <xref:System.Collections.Generic.SortedDictionary%602> ogólne. Z dwóch typów <xref:System.Collections.Generic.SortedDictionary%602> ogólnych, oferuje <xref:System.Collections.Generic.SortedList%602>lepszą <xref:System.Collections.Generic.SortedList%602> wydajność niż , podczas gdy zużywa mniej pamięci.  
  
  - <xref:System.Collections.ArrayList>zawiera <xref:System.Collections.ArrayList.Sort%2A> metodę, która <xref:System.Collections.IComparer> przyjmuje implementację jako parametr. Jego ogólny odpowiednik, klasa <xref:System.Collections.Generic.List%601> rodzajowa, <xref:System.Collections.Generic.List%601.Sort%2A> zapewnia metodę, <xref:System.Collections.Generic.IComparer%601> która przyjmuje implementację interfejsu ogólnego jako parametru.  
  
- Czy potrzebujesz szybkich wyszukiwań i pobierania informacji?  
  
  - <xref:System.Collections.Specialized.ListDictionary>jest szybszy niż <xref:System.Collections.Hashtable> w przypadku małych kolekcji (10 lub mniej). Klasa <xref:System.Collections.Generic.Dictionary%602> ogólna zapewnia szybsze <xref:System.Collections.Generic.SortedDictionary%602> wyszukiwanie niż klasa ogólna. Implementacja wielowątkowa jest <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601>zapewnia szybkie wstawianie wielowątkowe dla nieuporządkowanych danych. Aby uzyskać więcej informacji na temat obu typów wielowątkowych, zobacz [Kiedy używać kolekcji bezpiecznej dla wątków.](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)  
  
- Czy potrzebujesz kolekcji, które akceptują tylko ciągi?  
  
  - <xref:System.Collections.Specialized.StringCollection>(na <xref:System.Collections.IList>podstawie <xref:System.Collections.Specialized.StringDictionary> ) i <xref:System.Collections.IDictionary>(na <xref:System.Collections.Specialized> podstawie ) znajdują się w obszarze nazw.  
  
  - Ponadto można użyć dowolnej klasy kolekcji ogólnej <xref:System.Collections.Generic> w obszarze nazw jako silnie wpisane <xref:System.String> kolekcje ciągów, określając klasę dla ich argumentów typu ogólnego. Na przykład można zadeklarować zmienną typu [\<List String>](xref:System.Collections.Generic.List%601) lub Słownik<[ciąg, ciąg>](xref:System.Collections.Generic.Dictionary%602).
  
## <a name="linq-to-objects-and-plinq"></a>LINQ do obiektów i PLINQ  
 LINQ to Objects umożliwia deweloperom używanie zapytań LINQ do uzyskiwania dostępu <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>do obiektów w pamięci, o ile typ obiektu implementuje lub . Zapytania LINQ zapewniają wspólny wzorzec dostępu do danych, są zazwyczaj `foreach` bardziej zwięzłe i czytelne niż standardowe pętle i zapewniają możliwości filtrowania, zamawiania i grupowania. Aby uzyskać więcej informacji, zobacz [LINQ do obiektów (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) i [LINQ do obiektów (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).  
  
 PLINQ zapewnia równoległą implementację LINQ do obiektów, które mogą oferować szybsze wykonywanie zapytań w wielu scenariuszach, dzięki bardziej efektywnemu wykorzystaniu komputerów wielordzeniowych. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [Kolekcje bezpieczne dla wątków](../../../docs/standard/collections/thread-safe/index.md)
