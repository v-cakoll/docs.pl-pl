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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711353"
---
# <a name="selecting-a-collection-class"></a>Wybieranie klasy kolekcji

Pamiętaj, aby starannie wybrać klasę kolekcji. Użycie niewłaściwego typu może ograniczyć korzystanie z kolekcji.  

> [!IMPORTANT]
> Należy unikać używania <xref:System.Collections> typów w obszarze nazw. Ogólne i równoczesne wersje kolekcji są zalecane ze względu na ich większe bezpieczeństwo typu i inne ulepszenia.  

 Zastanów się nad następującymi pytaniami:  
  
- Czy potrzebujesz sekwencyjnej listy, gdzie element jest zazwyczaj odrzucany po pobraniu jego wartości?  
  
  - Jeśli tak, należy <xref:System.Collections.Queue> rozważyć <xref:System.Collections.Generic.Queue%601> użycie klasy lub klasy ogólnej, jeśli potrzebujesz zachowanie first-in, first-out (FIFO). Należy rozważyć <xref:System.Collections.Stack> użycie <xref:System.Collections.Generic.Stack%601> klasy lub klasy ogólnej, jeśli potrzebujesz zachowania last-in, first-out (LIFO). Aby zapewnić bezpieczny dostęp z wielu wątków, należy użyć równoczesnych wersji <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
  - Jeśli nie, należy rozważyć użycie innych kolekcji.  
  
- Czy musisz uzyskać dostęp do elementów w określonej kolejności, takich jak FIFO, LIFO lub losowo?  
  
  - Klasa <xref:System.Collections.Queue> i <xref:System.Collections.Generic.Queue%601> lub <xref:System.Collections.Concurrent.ConcurrentQueue%601> klasa ogólna oferują dostęp FIFO. Aby uzyskać więcej informacji, zobacz [Kiedy należy używać kolekcji bezpiecznego wątku](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - Klasa <xref:System.Collections.Stack> i <xref:System.Collections.Generic.Stack%601> lub <xref:System.Collections.Concurrent.ConcurrentStack%601> klasa ogólna oferują dostęp LIFO. Aby uzyskać więcej informacji, zobacz [Kiedy należy używać kolekcji bezpiecznego wątku](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - Klasa <xref:System.Collections.Generic.LinkedList%601> ogólna umożliwia sekwencyjne dostęp z głowy do ogona lub od ogona do głowy.  
  
- Czy musisz uzyskać dostęp do każdego elementu przez indeks?  
  
  - I <xref:System.Collections.ArrayList> <xref:System.Collections.Specialized.StringCollection> klas i <xref:System.Collections.Generic.List%601> klasy ogólnej oferują dostęp do ich elementów przez indeks od zera elementu.  
  
  - , <xref:System.Collections.Hashtable> <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>i <xref:System.Collections.Specialized.StringDictionary> klas i <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.Generic.SortedDictionary%602> i ogólne klasy oferują dostęp do swoich elementów za pomocą klucza elementu.  
  
  - I <xref:System.Collections.Specialized.NameObjectCollectionBase> <xref:System.Collections.Specialized.NameValueCollection> klas i <xref:System.Collections.ObjectModel.KeyedCollection%602> klas <xref:System.Collections.Generic.SortedList%602> ogólnych oferują dostęp do ich elementów przez indeks od zera lub klucz elementu.  
  
- Czy każdy element będzie zawierał jedną wartość, kombinację jednego klucza i jednej wartości lub kombinację jednego klucza i wielu wartości?  
  
  - Jedna wartość: Użyj dowolnej kolekcji <xref:System.Collections.IList> na podstawie <xref:System.Collections.Generic.IList%601> interfejsu lub interfejsu ogólnego.  
  
  - Jeden klucz i jedna wartość: Użyj dowolnej <xref:System.Collections.IDictionary> kolekcji <xref:System.Collections.Generic.IDictionary%602> na podstawie interfejsu lub interfejsu ogólnego.  
  
  - Jedna wartość z kluczem <xref:System.Collections.ObjectModel.KeyedCollection%602> osadzonym: Użyj klasy ogólnej.  
  
  - Jeden klucz i wiele <xref:System.Collections.Specialized.NameValueCollection> wartości: Użyj klasy.  
  
- Czy elementy muszą być sortowane inaczej niż zostały wprowadzone?  
  
  - Klasa <xref:System.Collections.Hashtable> sortuje swoje elementy według ich kodów mieszania.  
  
  - Klasa <xref:System.Collections.SortedList> i <xref:System.Collections.Generic.SortedList%602> klasy <xref:System.Collections.Generic.SortedDictionary%602> ogólne sortować ich elementy według klucza. Kolejność sortowania jest oparta <xref:System.Collections.IComparer> na implementacji interfejsu <xref:System.Collections.SortedList> dla klasy <xref:System.Collections.Generic.IComparer%601> i na <xref:System.Collections.Generic.SortedList%602> <xref:System.Collections.Generic.SortedDictionary%602> implementacji interfejsu ogólnego dla klas i ogólnych. Z dwóch typów <xref:System.Collections.Generic.SortedDictionary%602> ogólnych, <xref:System.Collections.Generic.SortedList%602>oferuje <xref:System.Collections.Generic.SortedList%602> lepszą wydajność niż , podczas gdy zużywa mniej pamięci.  
  
  - <xref:System.Collections.ArrayList>udostępnia <xref:System.Collections.ArrayList.Sort%2A> metodę, która <xref:System.Collections.IComparer> przyjmuje implementację jako parametr. Jego odpowiednik ogólny, klasa <xref:System.Collections.Generic.List%601> ogólna, <xref:System.Collections.Generic.List%601.Sort%2A> zapewnia metodę, <xref:System.Collections.Generic.IComparer%601> która przyjmuje implementację interfejsu ogólnego jako parametr.  
  
- Potrzebujesz szybkiego wyszukiwania i pobierania informacji?  
  
  - <xref:System.Collections.Specialized.ListDictionary>jest szybszy <xref:System.Collections.Hashtable> niż w przypadku małych kolekcji (10 lub mniej przedmiotów). Klasa <xref:System.Collections.Generic.Dictionary%602> ogólna zapewnia szybsze <xref:System.Collections.Generic.SortedDictionary%602> odzewy w górę niż klasa ogólna. Implementacja wielowątkowa <xref:System.Collections.Concurrent.ConcurrentDictionary%602>jest . <xref:System.Collections.Concurrent.ConcurrentBag%601>zapewnia szybkie wstawianie wielowątkowe dla danych nieuporządkowanych. Aby uzyskać więcej informacji na temat obu typów wielowątkowych, zobacz [Kiedy należy użyć kolekcji bezpiecznego wątku](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
- Czy potrzebujesz kolekcji, które akceptują tylko ciągi?  
  
  - <xref:System.Collections.Specialized.StringCollection>(na <xref:System.Collections.IList>podstawie <xref:System.Collections.Specialized.StringDictionary> ) i <xref:System.Collections.IDictionary>(na <xref:System.Collections.Specialized> podstawie) znajdują się w przestrzeni nazw.  
  
  - Ponadto można użyć dowolnej klasy kolekcji ogólnej <xref:System.Collections.Generic> w obszarze nazw jako silnie typowane kolekcje ciągów, określając <xref:System.String> klasę dla ich argumentów typu ogólnego. Na przykład można zadeklarować zmienną typu [Ciąg\<listy>](xref:System.Collections.Generic.List%601) lub Słownik<[ciąg, ciąg>](xref:System.Collections.Generic.Dictionary%602).
  
## <a name="linq-to-objects-and-plinq"></a>LINQ do obiektów i PLINQ  
 LINQ do obiektów umożliwia deweloperom używać zapytań LINQ do uzyskiwania <xref:System.Collections.IEnumerable> dostępu <xref:System.Collections.Generic.IEnumerable%601>do obiektów w pamięci, tak długo, jak implementuje typ obiektu lub . Kwerendy LINQ zapewniają wspólny wzorzec dostępu do danych, są `foreach` zazwyczaj bardziej zwięzłe i czytelne niż standardowe pętle i zapewniają możliwości filtrowania, porządkowania i grupowania. Aby uzyskać więcej informacji, zobacz [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) i [LINQ to Objects (Visual Basic).](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
 PLINQ zapewnia równoległą implementację LINQ do obiektów, które mogą oferować szybsze wykonywanie zapytań w wielu scenariuszach, dzięki bardziej efektywnemu wykorzystaniu komputerów wielordzeniowych. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [Kolekcje bezpieczne wątkowo](../../../docs/standard/collections/thread-safe/index.md)
