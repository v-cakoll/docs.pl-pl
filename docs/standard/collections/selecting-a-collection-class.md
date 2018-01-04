---
title: Wybieranie klasy kolekcji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- last-in-first-out collections
- first-in-first-out collections
- collections [.NET Framework], selecting collection class
- indexed collections
- Collections classes
- grouping data in collections, selecting collection class
ms.assetid: ba049f9a-ce87-4cc4-b319-3f75c8ddac8a
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 05339b829262a6b9b3a0265e4fbd444c6d586ea3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="selecting-a-collection-class"></a>Wybieranie klasy kolekcji
Należy wybrać uważnie klasie kolekcji. Przy użyciu nieprawidłowego typu można ograniczyć korzystanie z kolekcji. Ogólnie rzecz biorąc, należy unikać typów w <xref:System.Collections> przestrzeni nazw o ile nie są specjalnie przeznaczonych dla platformy .NET Framework w wersji 1.1. Rodzajowa i współbieżnych wersje kolekcje są się ze względu na ich większe bezpieczeństwo typu i inne usprawnienia.  
  
 Należy rozważyć następujące kwestie:  
  
-   Potrzebujesz uporządkowanej listy, gdy element zwykle są usuwane po jego wartość jest pobierana?  
  
    -   Jeśli tak, rozważ użycie <xref:System.Collections.Queue> klasy lub <xref:System.Collections.Generic.Queue%601> klasy ogólnej, jeśli należy w pierwszej, zachowanie FIFO (FIFO). Należy rozważyć użycie <xref:System.Collections.Stack> klasy lub <xref:System.Collections.Generic.Stack%601> klasy ogólnej, jeśli potrzebujesz ostatni na, wytworzenia zachowanie. Bezpieczny dostęp wiele wątków, można użyć w wersji równoczesnych <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
    -   Jeśli nie, należy rozważyć użycie innych kolekcji.  
  
-   Czy konieczne jest dostęp do elementów w określonej kolejności, takich jak FIFO, LIFO lub losowych?  
  
    -   <xref:System.Collections.Queue> Klasy i <xref:System.Collections.Generic.Queue%601> lub <xref:System.Collections.Concurrent.ConcurrentQueue%601> klasy ogólnej oferują FIFO dostępu. Aby uzyskać więcej informacji, zobacz [kiedy należy używać kolekcji bezpiecznych wątkowo](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   <xref:System.Collections.Stack> Klasy i <xref:System.Collections.Generic.Stack%601> lub <xref:System.Collections.Concurrent.ConcurrentStack%601> klasy ogólnej oferują LIFO dostępu. Aby uzyskać więcej informacji, zobacz [kiedy należy używać kolekcji bezpiecznych wątkowo](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   <xref:System.Collections.Generic.LinkedList%601> Klasy ogólnej umożliwia dostęp sekwencyjny z węzła głównego do końcowego fragmentu lub tail nagłówek.  
  
-   Czy trzeba uzyskać dostęp każdy element przez indeks?  
  
    -   <xref:System.Collections.ArrayList> i <xref:System.Collections.Specialized.StringCollection> klas i <xref:System.Collections.Generic.List%601> klasy ogólnej oferta dostęp do swoich elementów przez liczony od zera indeks elementu.  
  
    -   <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>, I <xref:System.Collections.Specialized.StringDictionary> klasy, a <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Generic.SortedDictionary%602> klasy ogólne zapewniają dostęp do swoich elementów dzięki klucz elementu.  
  
    -   <xref:System.Collections.Specialized.NameObjectCollectionBase> i <xref:System.Collections.Specialized.NameValueCollection> klasy, a <xref:System.Collections.ObjectModel.KeyedCollection%602> i <xref:System.Collections.Generic.SortedList%602> klasy ogólne zapewniają dostęp do swoich elementów dzięki albo liczony od zera indeks lub klucz elementu.  
  
-   Każdy element będzie zawierać, jedną wartość, kombinacji klawiszy i jedną wartość, lub kombinację klawiszy i wiele wartości?  
  
    -   Jedna wartość: użyć dowolnego z kolekcji opartych na <xref:System.Collections.IList> interfejsu lub <xref:System.Collections.Generic.IList%601> interfejs generyczny.  
  
    -   Jeden klucz i wartość jednego: użyć dowolnego z kolekcji opartych na <xref:System.Collections.IDictionary> interfejsu lub <xref:System.Collections.Generic.IDictionary%602> interfejs generyczny.  
  
    -   Jedna wartość z kluczem osadzonych: Użyj <xref:System.Collections.ObjectModel.KeyedCollection%602> klasy ogólnej.  
  
    -   Jeden z kluczy i wartości wielu: Użyj <xref:System.Collections.Specialized.NameValueCollection> klasy.  
  
-   Czy trzeba posortować elementy inaczej niż jak zostały wprowadzone?  
  
    -   <xref:System.Collections.Hashtable> Klasy sortuje swoich elementów według ich skrótu.  
  
    -   <xref:System.Collections.SortedList> Klasy i <xref:System.Collections.Generic.SortedDictionary%602> i <xref:System.Collections.Generic.SortedList%602> klas rodzajowych sortowania ich elementów za pomocą klucza oparte na implementacje <xref:System.Collections.IComparer> interfejsu i <xref:System.Collections.Generic.IComparer%601> interfejs generyczny.  
  
    -   <xref:System.Collections.ArrayList>udostępnia <xref:System.Collections.ArrayList.Sort%2A> metody pobierającej <xref:System.Collections.IComparer> implementacji jako parametr. Jego ogólny odpowiednik <xref:System.Collections.Generic.List%601> udostępnia ogólne klasy <xref:System.Collections.Generic.List%601.Sort%2A> metody pobierającej implementacja <xref:System.Collections.Generic.IComparer%601> interfejs ogólny jako parametr.  
  
-   Czy potrzebna jest szybkie wyszukiwanie i pobieranie informacji?  
  
    -   <xref:System.Collections.Specialized.ListDictionary>jest szybsze niż <xref:System.Collections.Hashtable> dla małych kolekcji (10 elementów lub mniej). <xref:System.Collections.Generic.Dictionary%602> Klasy ogólnej zapewnia szybsze wyszukiwanie niż <xref:System.Collections.Generic.SortedDictionary%602> klasy ogólnej. Implementacja wielowątkowych jest <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601>zapewnia szybkie wstawiania wielowątkowych nieuporządkowaną danych. Aby uzyskać więcej informacji na temat obu typów wielowątkowych, zobacz [kiedy należy używać kolekcji bezpiecznych wątkowo](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
-   Potrzebujesz kolekcje, które są akceptowane tylko ciągi?  
  
    -   <xref:System.Collections.Specialized.StringCollection>(na podstawie <xref:System.Collections.IList>) i <xref:System.Collections.Specialized.StringDictionary> (na podstawie <xref:System.Collections.IDictionary>) znajdują się w <xref:System.Collections.Specialized> przestrzeni nazw.  
  
    -   Ponadto można użyć dowolnej klasy rodzajowej kolekcji w <xref:System.Collections.Generic> przestrzeń nazw jako silnie typizowane kolekcji ciągów, określając <xref:System.String> klasy dla ich argumentów typu ogólnego.  
  
## <a name="linq-to-objects-and-plinq"></a>LINQ do obiektów i PLINQ  
 LINQ do obiektów umożliwia deweloperom umożliwia uzyskiwanie dostępu do obiektów w pamięci, tak długo, jak typ obiektu implementuje zapytań LINQ <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>. Zapytania LINQ Podaj wspólnego wzorca do uzyskiwania dostępu do danych, zazwyczaj są bardziej zwięzłe i czytelna niż standardowe `foreach` pętli i zapewnić filtrowania, kolejność i grupowanie możliwości. Aby uzyskać więcej informacji, zobacz [LINQ do obiektów](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9).  
  
 PLINQ udostępnia implementację równoległe LINQ do obiektów, które może zaoferować szybsze wykonywanie zapytania w wielu scenariuszach za pośrednictwem efektywniejsze wykorzystanie komputerach z procesorami wielordzeniowymi. Aby uzyskać więcej informacji, zobacz [równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections>  
 <xref:System.Collections.Specialized>  
 <xref:System.Collections.Generic>  
 [Kolekcje bezpieczne wątkowo](../../../docs/standard/collections/thread-safe/index.md)
