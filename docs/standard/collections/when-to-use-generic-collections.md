---
title: Kiedy należy używać kolekcji ogólnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b553ec62cf493b94b87079cddd3ec3d1d60daf9d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66491009"
---
# <a name="when-to-use-generic-collections"></a>Kiedy należy używać kolekcji ogólnych
Za pomocą kolekcji ogólnych ogólnie zaleca się, ponieważ uzyskanie bezpośrednią korzyść bezpieczeństwa typu bez konieczności pochodzić od typu podstawowego kolekcji i implementowanie elementów specyficznych dla typu. Typy generyczne kolekcji również zazwyczaj mają lepszą wydajność niż odpowiadające typy kolekcji nierodzajowymi (i lepiej niż typy, pochodne typy nierodzajowymi bazowej kolekcji) po elementy kolekcji są typami wartości, ponieważ za pomocą typów ogólnych nie ma potrzeby polu elementów.  
  
 Dla programów, które obsługują program .NET Framework 4 lub nowszego, należy używać klasy kolekcji rodzajowej w <xref:System.Collections.Concurrent> przestrzenią nazw, gdy wiele wątków może być dodanie lub usunięcie elementów z kolekcji jednocześnie.  
  
 Następujące typy rodzajowe odnoszą się do istniejących typów kolekcji:  
  
- <xref:System.Collections.Generic.List%601> jest klasą rodzajową, który odpowiada <xref:System.Collections.ArrayList>.  
  
- <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602> są klasy ogólne, które odpowiadają <xref:System.Collections.Hashtable>.  
  
- <xref:System.Collections.ObjectModel.Collection%601> jest klasą rodzajową, który odpowiada <xref:System.Collections.CollectionBase>. <xref:System.Collections.ObjectModel.Collection%601> może służyć jako klasa bazowa, lecz w przeciwieństwie do <xref:System.Collections.CollectionBase>, nie jest abstrakcyjna. Dzięki temu można łatwiej używać.  
  
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> jest klasą rodzajową, który odpowiada <xref:System.Collections.ReadOnlyCollectionBase>. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> nie jest abstrakcyjna i ma konstruktora, który można łatwo udostępnić istniejący <xref:System.Collections.Generic.List%601> jako kolekcja tylko do odczytu.  
  
- <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>, I <xref:System.Collections.Generic.SortedList%602> klas ogólnych odnoszą się do odpowiednich klas nierodzajowymi o takich samych nazwach.  
  
## <a name="additional-types"></a>Dodatkowe typy  
 Kilka typów ogólnych kolekcji nie ma odpowiedników nierodzajowych. Ulepszenia obejmują następujące czynności:  
  
- <xref:System.Collections.Generic.LinkedList%601> jest listę połączonych ogólnego przeznaczenia, która udostępnia operacje wstawiania i usuwania O(1).  
  
- <xref:System.Collections.Generic.SortedDictionary%602> jest posortowany słownik z O (log `n`) ostatniego wstawienia i wydobycia operacji, co sprawia, że użyteczną alternatywą dla <xref:System.Collections.Generic.SortedList%602>.  
  
- <xref:System.Collections.ObjectModel.KeyedCollection%602> jest hybrydowej między listą a słownika, która zapewnia sposób przechowywania obiektów, które zawierają własne klucze.  
  
- <xref:System.Collections.Concurrent.BlockingCollection%601> implementuje klasy kolekcji za pomocą funkcji blokujących i.  
  
- <xref:System.Collections.Concurrent.ConcurrentBag%601> zapewnia szybkie wstawiania i usuwania elementów nieuporządkowaną.  
  
## <a name="linq-to-objects"></a>LINQ do obiektów  
 Funkcja LINQ to Objects umożliwia używanie zapytań LINQ do dostępu do obiektów w pamięci, tak długo, jak długo typ obiektu implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu. Zapytania LINQ zapewniają wspólny wzorzec do uzyskiwania dostępu do danych. zazwyczaj są bardziej zwięzłe i czytelne niż standardowe `foreach` pętle i zapewniają filtrowanie, porządkowanie i możliwości grupowania. Zapytania LINQ można również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md), i [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="additional-functionality"></a>Dodatkowe funkcje  
 Niektórych typów ogólnych są funkcje, które nie znajduje się w typach nierodzajowymi kolekcji. Na przykład <xref:System.Collections.Generic.List%601> klasy, która odnosi się do nongeneric <xref:System.Collections.ArrayList> klasy, ma wiele metod, które akceptują delegatów ogólnych, takich jak <xref:System.Predicate%601> delegat, który pozwala na określenie metody wyszukiwania na liście <xref:System.Action%601>delegat, który reprezentuje metody, które działają na każdym elemencie listy, a <xref:System.Converter%602> delegat, który pozwala zdefiniować konwersje między typami.  
  
 <xref:System.Collections.Generic.List%601> Klasy można określić własne <xref:System.Collections.Generic.IComparer%601> implementacje interfejsu ogólnego do sortowania i wyszukiwania listy. <xref:System.Collections.Generic.SortedDictionary%602> i <xref:System.Collections.Generic.SortedList%602> klasy także mają tę możliwość. Ponadto klasy te umożliwiają określenie porównywanie, po utworzeniu kolekcji. W podobny sposób <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.ObjectModel.KeyedCollection%602> klasy umożliwiają określenie własnych porównywanie równości.  
  
## <a name="see-also"></a>Zobacz także

- [Kolekcje i struktury danych](../../../docs/standard/collections/index.md)
- [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
- [Typy ogólne](../../../docs/standard/generics/index.md)
