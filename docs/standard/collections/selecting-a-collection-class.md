---
title: Wybieranie klasy kolekcji
ms.date: 03/30/2017
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
ms.openlocfilehash: d84bc5ac2256139626311ff7c848170c28ffbd5b
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708169"
---
# <a name="selecting-a-collection-class"></a>Wybieranie klasy kolekcji
Należy wybrać uważnie klasy kolekcji. Przy użyciu nieprawidłowego typu można ograniczyć korzystanie z kolekcji. Ogólnie rzecz biorąc, unikaj używania typów w <xref:System.Collections> przestrzeni nazw, chyba że są specjalnie przeznaczone dla .NET Framework w wersji 1.1. Ogólny i równoczesne wersje kolekcje są preferowane ze względu na ich większe bezpieczeństwo typu i inne ulepszenia.  
  
 Należy rozważyć następujące kwestie:  
  
-   Czy potrzebujesz uporządkowanej listy, gdzie element zwykle są usuwane po jego wartość jest pobierana?  
  
    -   Jeśli tak, należy wziąć pod uwagę przy użyciu <xref:System.Collections.Queue> klasy lub <xref:System.Collections.Generic.Queue%601> klasy generycznej, jeśli potrzebujesz w pierwszym, zachowanie FIFO (FIFO). Należy rozważyć użycie <xref:System.Collections.Stack> klasy lub <xref:System.Collections.Generic.Stack%601> klasy generycznej, jeśli potrzebujesz ostatni na wejściu, zachowanie FIFO (LIFO). Bezpieczny dostęp z wielu wątków, można użyć w wersji współbieżnych <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
    -   W przeciwnym razie należy wziąć pod uwagę przy użyciu innych kolekcji.  
  
-   Należy uzyskać dostęp do elementów w określonej kolejności, takie jak FIFO, LIFO, lub wartość losowa?  
  
    -   <xref:System.Collections.Queue> Klasy i <xref:System.Collections.Generic.Queue%601> lub <xref:System.Collections.Concurrent.ConcurrentQueue%601> klasy ogólnej oferują FIFO dostępu. Aby uzyskać więcej informacji, zobacz [kiedy należy używać kolekcji bezpiecznych wątkowo](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   <xref:System.Collections.Stack> Klasy i <xref:System.Collections.Generic.Stack%601> lub <xref:System.Collections.Concurrent.ConcurrentStack%601> klasy ogólnej oferują LIFO dostępu. Aby uzyskać więcej informacji, zobacz [kiedy należy używać kolekcji bezpiecznych wątkowo](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   <xref:System.Collections.Generic.LinkedList%601> Klasy ogólnej umożliwia dostęp sekwencyjny, przejdź do ogona lub tail do głowy.  
  
-   Potrzebujesz uzyskać dostęp do każdego elementu przez indeks?  
  
    -   <xref:System.Collections.ArrayList> i <xref:System.Collections.Specialized.StringCollection> klasy i <xref:System.Collections.Generic.List%601> klasy ogólnej oferty dostępu do swoich elementów przez liczony od zera indeks elementu.  
  
    -   <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>, I <xref:System.Collections.Specialized.StringDictionary> klas, a <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Generic.SortedDictionary%602> klas ogólnych oferują dostęp do swoich elementów za pomocą klucza elementu.  
  
    -   <xref:System.Collections.Specialized.NameObjectCollectionBase> i <xref:System.Collections.Specialized.NameValueCollection> klas, a <xref:System.Collections.ObjectModel.KeyedCollection%602> i <xref:System.Collections.Generic.SortedList%602> klas ogólnych oferują dostęp do swoich elementów przez liczony od zera indeks lub klucz elementu.  
  
-   Każdy element zawiera jedną wartość, kombinacji klawiszy i jedną wartość, lub kombinacji klawiszy i wiele wartości?  
  
    -   Jedna wartość: Użyj dowolnej kolekcji, w oparciu o <xref:System.Collections.IList> interfejsu lub <xref:System.Collections.Generic.IList%601> ogólny interfejs.  
  
    -   Jeden klucz i jedną wartość: Użyj dowolnej kolekcji, w oparciu o <xref:System.Collections.IDictionary> interfejsu lub <xref:System.Collections.Generic.IDictionary%602> interfejs generyczny.  
  
    -   Jedną wartość z kluczem osadzonego: Użyj <xref:System.Collections.ObjectModel.KeyedCollection%602> klasy ogólnej.  
  
    -   Jeden z kluczy i wartości wielu: Użyj <xref:System.Collections.Specialized.NameValueCollection> klasy.  
  
-   Potrzebujesz sortować elementy różni się od sposobu ich wprowadzenia?  
  
    -   <xref:System.Collections.Hashtable> Klasy sortuje jego elementy według ich kody skrótów.  
  
    -   <xref:System.Collections.SortedList> Klasy i <xref:System.Collections.Generic.SortedDictionary%602> i <xref:System.Collections.Generic.SortedList%602> klas ogólnych sortowanie ich elementów za pomocą klucza oparte na implementacje <xref:System.Collections.IComparer> interfejsu i <xref:System.Collections.Generic.IComparer%601> interfejs generyczny.  
  
    -   <xref:System.Collections.ArrayList> udostępnia <xref:System.Collections.ArrayList.Sort%2A> metody, która przyjmuje <xref:System.Collections.IComparer> implementacji jako parametr. Jego odpowiednika rodzajowego <xref:System.Collections.Generic.List%601> udostępnia klasy generycznej <xref:System.Collections.Generic.List%601.Sort%2A> metody, która przyjmuje implementację <xref:System.Collections.Generic.IComparer%601> ogólny interfejs jako parametr.  
  
-   Potrzebujesz szybkie wyszukiwanie i pobieranie informacji?  
  
    -   <xref:System.Collections.Specialized.ListDictionary> jest szybsza niż <xref:System.Collections.Hashtable> kolekcji mały (10 elementów lub mniej). <xref:System.Collections.Generic.Dictionary%602> Klasy ogólnej zapewnia szybsze wyszukiwanie niż <xref:System.Collections.Generic.SortedDictionary%602> klasy ogólnej. Wielowątkowe implementacja jest <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601> zapewnia szybkie wstawienia wielowątkowych nieuporządkowaną danych. Aby uzyskać więcej informacji na temat obu typów wielowątkowych zobacz [kiedy należy używać kolekcji bezpiecznych wątkowo](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
-   Czy potrzebujesz kolekcje, które akceptują tylko ciągi?  
  
    -   <xref:System.Collections.Specialized.StringCollection> (na podstawie <xref:System.Collections.IList>) i <xref:System.Collections.Specialized.StringDictionary> (na podstawie <xref:System.Collections.IDictionary>) znajdują się w <xref:System.Collections.Specialized> przestrzeni nazw.  
  
    -   Ponadto można użyć dowolnej klasy kolekcji rodzajowej w <xref:System.Collections.Generic> przestrzeni nazw jako silnie typizowane kolekcji ciągów, określając <xref:System.String> klasy dla ich argumentów typu rodzajowego.  
  
## <a name="linq-to-objects-and-plinq"></a>LINQ do obiektów i PLINQ  
 LINQ do obiektów umożliwia deweloperom Używanie zapytań LINQ do dostępu do obiektów w pamięci, tak długo, jak długo typ obiektu implementuje <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>. Zapytania LINQ zapewniają wspólny wzorzec do uzyskiwania dostępu do danych, zazwyczaj są bardziej zwięzłe i czytelne niż standardowe `foreach` pętli i zapewniają filtrowanie, porządkowanie i możliwości grupowania. Aby uzyskać więcej informacji, zobacz [LINQ to Objects](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9).  
  
 Program PLINQ zawiera implementacja przetwarzania równoległego LINQ do obiektów, które może zaoferować szybsze wykonywanie zapytań w wielu scenariuszach, za pomocą bardziej efektywne wykorzystywanie komputerach wielordzeniowych. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections>  
- <xref:System.Collections.Specialized>  
- <xref:System.Collections.Generic>  
- [Kolekcje bezpieczne wątkowo](../../../docs/standard/collections/thread-safe/index.md)
