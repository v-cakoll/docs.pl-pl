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
ms.openlocfilehash: fb03200c810290c970f7aa56a0e15d385aca7ca8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711353"
---
# <a name="selecting-a-collection-class"></a>Wybieranie klasy kolekcji

Pamiętaj, aby dokładnie wybrać klasę kolekcji. Użycie nieprawidłowego typu może ograniczyć użycie kolekcji.  

> [!IMPORTANT]
> Należy unikać używania typów w przestrzeni nazw <xref:System.Collections>. Ogólne i współbieżne wersje kolekcji są zalecane ze względu na ich większe bezpieczeństwo i inne ulepszenia.  

 Zastanów się nad następującymi pytaniami:  
  
- Czy potrzebujesz listy sekwencyjnej, w której element jest zwykle odrzucany po pobraniu wartości?  
  
  - Jeśli tak, rozważ użycie klasy <xref:System.Collections.Queue> lub klasy generycznej <xref:System.Collections.Generic.Queue%601>, jeśli jest wymagane zachowanie funkcji First-In, First-Out (FIFO). Należy rozważyć użycie klasy <xref:System.Collections.Stack> lub klasy generycznej <xref:System.Collections.Generic.Stack%601>, jeśli jest potrzebne zachowanie Last-in, First-Out (LIFO). Aby bezpiecznie uzyskać dostęp z wielu wątków, użyj współbieżnych wersji, <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
  - Jeśli nie, rozważ użycie innych kolekcji.  
  
- Czy musisz uzyskać dostęp do elementów w określonej kolejności, takich jak FIFO, LIFO lub losowo?  
  
  - Klasa <xref:System.Collections.Queue> i <xref:System.Collections.Generic.Queue%601> lub <xref:System.Collections.Concurrent.ConcurrentQueue%601> klasy ogólnej oferują dostęp do FIFO. Aby uzyskać więcej informacji, zobacz [Kiedy używać kolekcji bezpiecznej wątkowo](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - Klasa <xref:System.Collections.Stack> i <xref:System.Collections.Generic.Stack%601> lub <xref:System.Collections.Concurrent.ConcurrentStack%601> klasy generycznej oferują dostęp do kolejki LIFO. Aby uzyskać więcej informacji, zobacz [Kiedy używać kolekcji bezpiecznej wątkowo](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - Klasa generyczna <xref:System.Collections.Generic.LinkedList%601> umożliwia dostęp sekwencyjny od głowy do ogona lub od ogona do głowy.  
  
- Czy musisz uzyskać dostęp do każdego elementu według indeksu?  
  
  - Klasy <xref:System.Collections.ArrayList> i <xref:System.Collections.Specialized.StringCollection> i Klasa ogólna <xref:System.Collections.Generic.List%601> zapewniają dostęp do ich elementów przez indeks od zera elementu.  
  
  - Klasy <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>i <xref:System.Collections.Specialized.StringDictionary> oraz klasy generyczne <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Generic.SortedDictionary%602> oferują dostęp do ich elementów za pomocą klucza elementu.  
  
  - Klasy <xref:System.Collections.Specialized.NameObjectCollectionBase> i <xref:System.Collections.Specialized.NameValueCollection> oraz klasy generyczne <xref:System.Collections.ObjectModel.KeyedCollection%602> i <xref:System.Collections.Generic.SortedList%602> zapewniają dostęp do swoich elementów przez indeks lub klucz elementu.  
  
- Czy każdy element będzie zawierać jedną wartość, kombinację jednego klucza i jedną wartość, czy kombinację jednego klucza i wielu wartości?  
  
  - Jedna wartość: Użyj dowolnej kolekcji opartej na interfejsie <xref:System.Collections.IList> lub <xref:System.Collections.Generic.IList%601> ogólnym interfejsie.  
  
  - Jeden klucz i jedna wartość: Użyj dowolnej kolekcji opartej na interfejsie <xref:System.Collections.IDictionary> lub <xref:System.Collections.Generic.IDictionary%602> ogólnym interfejsie.  
  
  - Jedna wartość z kluczem osadzonym: Użyj klasy generycznej <xref:System.Collections.ObjectModel.KeyedCollection%602>.  
  
  - Jeden klucz i wiele wartości: Użyj klasy <xref:System.Collections.Specialized.NameValueCollection>.  
  
- Czy należy posortować elementy inaczej niż w sposobie ich wprowadzania?  
  
  - Klasa <xref:System.Collections.Hashtable> sortuje swoje elementy według ich kodów skrótu.  
  
  - Klasy <xref:System.Collections.SortedList> i <xref:System.Collections.Generic.SortedList%602> i <xref:System.Collections.Generic.SortedDictionary%602> klas ogólnych sortują ich elementy według klucza. Kolejność sortowania jest oparta na implementacji interfejsu <xref:System.Collections.IComparer> dla klasy <xref:System.Collections.SortedList> i implementacji interfejsu <xref:System.Collections.Generic.IComparer%601> generycznego dla <xref:System.Collections.Generic.SortedList%602> i <xref:System.Collections.Generic.SortedDictionary%602> klas ogólnych. W przypadku dwóch typów ogólnych <xref:System.Collections.Generic.SortedDictionary%602> zapewnia lepszą wydajność niż <xref:System.Collections.Generic.SortedList%602>, podczas gdy <xref:System.Collections.Generic.SortedList%602> zużywa mniej pamięci.  
  
  - <xref:System.Collections.ArrayList> udostępnia metodę <xref:System.Collections.ArrayList.Sort%2A>, która przyjmuje <xref:System.Collections.IComparer> implementację jako parametr. Jego ogólny odpowiednik, Klasa ogólna <xref:System.Collections.Generic.List%601>, zapewnia metodę <xref:System.Collections.Generic.List%601.Sort%2A>, która pobiera implementację interfejsu <xref:System.Collections.Generic.IComparer%601> generycznego jako parametr.  
  
- Potrzebujesz szybkiego wyszukiwania i pobierania informacji?  
  
  - <xref:System.Collections.Specialized.ListDictionary> jest szybsza niż <xref:System.Collections.Hashtable> dla małych kolekcji (10 elementów lub mniej). Klasa generyczna <xref:System.Collections.Generic.Dictionary%602> zapewnia szybsze wyszukiwanie niż Klasa generyczna <xref:System.Collections.Generic.SortedDictionary%602>. Implementacja wielowątkowa jest <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601> zapewnia szybki Wstawianie wielowątkowe dla nieuporządkowanych danych. Aby uzyskać więcej informacji na temat typów wielowątkowych, zobacz [Kiedy używać kolekcji z bezpiecznymi wątkami](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
- Czy potrzebne są kolekcje akceptujące tylko ciągi?  
  
  - <xref:System.Collections.Specialized.StringCollection> (oparta na <xref:System.Collections.IList>) i <xref:System.Collections.Specialized.StringDictionary> (na podstawie <xref:System.Collections.IDictionary>) znajdują się w przestrzeni nazw <xref:System.Collections.Specialized>.  
  
  - Ponadto można użyć dowolnej klasy kolekcji generycznej w przestrzeni nazw <xref:System.Collections.Generic> jako kolekcje ciągów z jednoznacznie określonymi typami przez określenie klasy <xref:System.String> dla argumentów typu ogólnego. Na przykład można zadeklarować zmienną jako [listę typu\<string >](xref:System.Collections.Generic.List%601) lub [ciąg < słownika, > ciągu](xref:System.Collections.Generic.Dictionary%602).
  
## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects i PLINQ  
 LINQ to Objects umożliwia deweloperom używanie zapytań LINQ do uzyskiwania dostępu do obiektów w pamięci, o ile typ obiektu implementuje <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>. Zapytania LINQ zapewniają wspólny wzorzec uzyskiwania dostępu do danych, są zwykle bardziej zwięzłe i czytelne niż standardowe pętle `foreach` i zapewniają możliwości filtrowania, porządkowania i grupowania. Aby uzyskać więcej informacji, zobacz [LINQ to ObjectsC#()](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) i [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).  
  
 PLINQ zapewnia równoległą implementację LINQ to Objects, która może oferować szybsze wykonywanie zapytań w wielu scenariuszach dzięki wydajniejszemu używaniu komputerów z wieloma rdzeniami. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [Kolekcje bezpieczne wątkowo](../../../docs/standard/collections/thread-safe/index.md)
