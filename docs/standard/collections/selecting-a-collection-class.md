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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21c708f63faaedb9fbce60d7e4aef314f7a41ef8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61908911"
---
# <a name="selecting-a-collection-class"></a>Wybieranie klasy kolekcji

Należy wybrać uważnie klasy kolekcji. Przy użyciu nieprawidłowego typu można ograniczyć korzystanie z kolekcji.  

> [!IMPORTANT]
> Unikaj używania typów w <xref:System.Collections> przestrzeni nazw. Ogólny i równoczesne wersje kolekcje są zalecane, ze względu na ich większe bezpieczeństwo typu i inne ulepszenia.  

 Należy rozważyć następujące kwestie:  
  
- Czy potrzebujesz uporządkowanej listy, gdzie element zwykle są usuwane po jego wartość jest pobierana?  
  
  - Jeśli tak, należy wziąć pod uwagę przy użyciu <xref:System.Collections.Queue> klasy lub <xref:System.Collections.Generic.Queue%601> klasy generycznej, jeśli potrzebujesz w pierwszym, zachowanie FIFO (FIFO). Należy rozważyć użycie <xref:System.Collections.Stack> klasy lub <xref:System.Collections.Generic.Stack%601> klasy generycznej, jeśli potrzebujesz ostatni na wejściu, zachowanie FIFO (LIFO). Bezpieczny dostęp z wielu wątków, można użyć w równoczesne wersje <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
  - W przeciwnym razie należy wziąć pod uwagę przy użyciu innych kolekcji.  
  
- Należy uzyskać dostęp do elementów w określonej kolejności, takie jak FIFO, LIFO, lub wartość losowa?  
  
  - <xref:System.Collections.Queue> Klasy i <xref:System.Collections.Generic.Queue%601> lub <xref:System.Collections.Concurrent.ConcurrentQueue%601> klasy ogólnej oferują FIFO dostępu. Aby uzyskać więcej informacji, zobacz [kiedy należy używać kolekcji bezpiecznych wątkowo](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - <xref:System.Collections.Stack> Klasy i <xref:System.Collections.Generic.Stack%601> lub <xref:System.Collections.Concurrent.ConcurrentStack%601> klasy ogólnej oferują LIFO dostępu. Aby uzyskać więcej informacji, zobacz [kiedy należy używać kolekcji bezpiecznych wątkowo](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - <xref:System.Collections.Generic.LinkedList%601> Klasy ogólnej umożliwia dostęp sekwencyjny, przejdź do ogona lub tail do głowy.  
  
- Potrzebujesz uzyskać dostęp do każdego elementu przez indeks?  
  
  - <xref:System.Collections.ArrayList> i <xref:System.Collections.Specialized.StringCollection> klasy i <xref:System.Collections.Generic.List%601> klasy ogólnej oferty dostępu do swoich elementów przez liczony od zera indeks elementu.  
  
  - <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>, I <xref:System.Collections.Specialized.StringDictionary> klas, a <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Generic.SortedDictionary%602> klas ogólnych oferują dostęp do swoich elementów za pomocą klucza elementu.  
  
  - <xref:System.Collections.Specialized.NameObjectCollectionBase> i <xref:System.Collections.Specialized.NameValueCollection> klas, a <xref:System.Collections.ObjectModel.KeyedCollection%602> i <xref:System.Collections.Generic.SortedList%602> klas ogólnych oferują dostęp do swoich elementów przez liczony od zera indeks lub klucz elementu.  
  
- Każdy element zawiera jedną wartość, kombinacji klawiszy i jedną wartość, lub kombinacji klawiszy i wiele wartości?  
  
  - Jedna wartość: Użyj dowolnej kolekcji, w oparciu o <xref:System.Collections.IList> interfejsu lub <xref:System.Collections.Generic.IList%601> interfejs generyczny.  
  
  - Jeden klucz i jedną wartość: Użyj dowolnej kolekcji, w oparciu o <xref:System.Collections.IDictionary> interfejsu lub <xref:System.Collections.Generic.IDictionary%602> interfejs generyczny.  
  
  - Jedna wartość z kluczem embedded: Użyj <xref:System.Collections.ObjectModel.KeyedCollection%602> klasy ogólnej.  
  
  - Jeden klucz i wiele wartości: Użyj <xref:System.Collections.Specialized.NameValueCollection> klasy.  
  
- Potrzebujesz sortować elementy różni się od sposobu ich wprowadzenia?  
  
  - <xref:System.Collections.Hashtable> Klasy sortuje jego elementy według ich kody skrótów.  
  
  - <xref:System.Collections.SortedList> Klasy, a <xref:System.Collections.Generic.SortedList%602> i <xref:System.Collections.Generic.SortedDictionary%602> klas ogólnych sortowanie ich elementów za pomocą klucza. Kolejność sortowania jest oparty na implementacji <xref:System.Collections.IComparer> interfejs na potrzeby <xref:System.Collections.SortedList> klasy i w implementacji <xref:System.Collections.Generic.IComparer%601> ogólny interfejs umożliwiający <xref:System.Collections.Generic.SortedList%602> i <xref:System.Collections.Generic.SortedDictionary%602> klas ogólnych. Dwóch typów ogólnych <xref:System.Collections.Generic.SortedDictionary%602> zapewnia większą wydajność niż <xref:System.Collections.Generic.SortedList%602>, podczas gdy <xref:System.Collections.Generic.SortedList%602> zużywa mniej pamięci.  
  
  - <xref:System.Collections.ArrayList> udostępnia <xref:System.Collections.ArrayList.Sort%2A> metody, która przyjmuje <xref:System.Collections.IComparer> implementacji jako parametr. Jego odpowiednika rodzajowego <xref:System.Collections.Generic.List%601> udostępnia klasy generycznej <xref:System.Collections.Generic.List%601.Sort%2A> metody, która przyjmuje implementację <xref:System.Collections.Generic.IComparer%601> ogólny interfejs jako parametr.  
  
- Potrzebujesz szybkie wyszukiwanie i pobieranie informacji?  
  
  - <xref:System.Collections.Specialized.ListDictionary> jest szybsza niż <xref:System.Collections.Hashtable> kolekcji mały (10 elementów lub mniej). <xref:System.Collections.Generic.Dictionary%602> Klasy ogólnej zapewnia szybsze wyszukiwanie niż <xref:System.Collections.Generic.SortedDictionary%602> klasy ogólnej. Wielowątkowe implementacja jest <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601> zapewnia szybkie wstawienia wielowątkowych nieuporządkowaną danych. Aby uzyskać więcej informacji na temat obu typów wielowątkowych zobacz [kiedy należy używać kolekcji bezpiecznych wątkowo](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
- Czy potrzebujesz kolekcje, które akceptują tylko ciągi?  
  
  - <xref:System.Collections.Specialized.StringCollection> (na podstawie <xref:System.Collections.IList>) i <xref:System.Collections.Specialized.StringDictionary> (na podstawie <xref:System.Collections.IDictionary>) znajdują się w <xref:System.Collections.Specialized> przestrzeni nazw.  
  
  - Ponadto można użyć dowolnej klasy kolekcji rodzajowej w <xref:System.Collections.Generic> przestrzeni nazw jako silnie typizowane kolekcji ciągów, określając <xref:System.String> klasy dla ich argumentów typu rodzajowego. Na przykład, można zadeklarować zmienną typu [listy\<ciągu >](xref:System.Collections.Generic.List%601) lub [Dictionary < String, String >](xref:System.Collections.Generic.Dictionary%602).
  
## <a name="linq-to-objects-and-plinq"></a>LINQ do obiektów i PLINQ  
 LINQ do obiektów umożliwia deweloperom Używanie zapytań LINQ do dostępu do obiektów w pamięci, tak długo, jak długo typ obiektu implementuje <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>. Zapytania LINQ zapewniają wspólny wzorzec do uzyskiwania dostępu do danych, zazwyczaj są bardziej zwięzłe i czytelne niż standardowe `foreach` pętli i zapewniają filtrowanie, porządkowanie i możliwości grupowania. Aby uzyskać więcej informacji, zobacz [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) i [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).  
  
 Program PLINQ zawiera implementacja przetwarzania równoległego LINQ do obiektów, które może zaoferować szybsze wykonywanie zapytań w wielu scenariuszach, za pomocą bardziej efektywne wykorzystywanie komputerach wielordzeniowych. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [Kolekcje bezpieczne wątkowo](../../../docs/standard/collections/thread-safe/index.md)
