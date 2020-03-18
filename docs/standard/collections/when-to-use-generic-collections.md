---
title: Kiedy należy używać kolekcji ogólnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: 7d59259c1cab6842ef62888bf5326225394d8d44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711210"
---
# <a name="when-to-use-generic-collections"></a>Kiedy należy używać kolekcji ogólnych
Przy użyciu kolekcji ogólnych jest ogólnie zalecane, ponieważ można uzyskać natychmiastowe korzyści bezpieczeństwa typu bez konieczności wywodzić się z typu kolekcji podstawowej i zaimplementować elementy członkowskie specyficzne dla typu. Typy kolekcji rodzajowych również ogólnie działają lepiej niż odpowiednie typy kolekcji nierodzajowych (i lepsze niż typy, które są uzyskiwane z nieogólnych typów kolekcji podstawowej), gdy elementy kolekcji są typami wartości, ponieważ w przypadku typów ogólnych istnieje nie ma potrzeby, aby zapakować elementy.  
  
 W przypadku programów docelowych .NET Framework 4 lub nowszych <xref:System.Collections.Concurrent> należy użyć klas kolekcji ogólnej w przestrzeni nazw, gdy wiele wątków może dodawać lub usuwać elementy z kolekcji jednocześnie.  
  
 Następujące typy ogólne odpowiadają istniejącym typom kolekcji:  
  
- <xref:System.Collections.Generic.List%601>jest klasą rodzajową, <xref:System.Collections.ArrayList>która odpowiada .  
  
- <xref:System.Collections.Generic.Dictionary%602>i <xref:System.Collections.Concurrent.ConcurrentDictionary%602> są klasami ogólnymi, które odpowiadają <xref:System.Collections.Hashtable>.  
  
- <xref:System.Collections.ObjectModel.Collection%601>jest klasą rodzajową, <xref:System.Collections.CollectionBase>która odpowiada . <xref:System.Collections.ObjectModel.Collection%601>może być używany jako klasa <xref:System.Collections.CollectionBase>podstawowa, ale w przeciwieństwie do , nie jest abstrakcyjny. To sprawia, że znacznie łatwiejsze w użyciu.  
  
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>jest klasą rodzajową, <xref:System.Collections.ReadOnlyCollectionBase>która odpowiada . <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>nie jest abstrakcyjny i ma konstruktora, <xref:System.Collections.Generic.List%601> który ułatwia udostępnianie istniejących jako kolekcji tylko do odczytu.  
  
- Klasy <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601> <xref:System.Collections.Concurrent.ConcurrentStack%601>, <xref:System.Collections.Generic.SortedList%602> , i ogólne odpowiadają odpowiednim klasom nierodzajowymi o tych samych nazwach.  
  
## <a name="additional-types"></a>Dodatkowe typy  
 Kilka typów kolekcji rodzajowych nie mają odpowiedniki nierodzajowe. Należą do nich:  
  
- <xref:System.Collections.Generic.LinkedList%601>jest wykazem połączonym ogólnego przeznaczenia, który zapewnia operacje wstawiania i usuwania O(1).  
  
- <xref:System.Collections.Generic.SortedDictionary%602>jest posortowany słownik z `n`O(log) wstawiania i pobierania operacji, <xref:System.Collections.Generic.SortedList%602>co sprawia, że przydatna alternatywa dla .  
  
- <xref:System.Collections.ObjectModel.KeyedCollection%602>jest hybrydą między listą a słownikiem, który zapewnia sposób przechowywania obiektów, które zawierają własne klucze.  
  
- <xref:System.Collections.Concurrent.BlockingCollection%601>implementuje klasę kolekcji z funkcją ograniczającą i blokującą.  
  
- <xref:System.Collections.Concurrent.ConcurrentBag%601>zapewnia szybkie wstawianie i usuwanie nieuporządkowanych elementów.  
  
## <a name="linq-to-objects"></a>LINQ do obiektów  
 Funkcja LINQ to Objects umożliwia korzystanie z zapytań LINQ w celu uzyskania dostępu <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> do obiektów w pamięci, o ile typ obiektu implementuje interfejs lub interfejs. Zapytania LINQ zapewniają wspólny wzorzec dostępu do danych; są zazwyczaj bardziej zwięzłe `foreach` i czytelne niż standardowe pętle; oraz zapewnić możliwości filtrowania, zamawiania i grupowania. Zapytania LINQ można również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ to Objects (C#),](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)i [Parallel LINQ (PLINQ).](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
  
## <a name="additional-functionality"></a>Dodatkowe funkcje  
 Niektóre typy ogólne mają funkcje, które nie można znaleźć w typach kolekcji nongeneric. Na przykład <xref:System.Collections.Generic.List%601> klasa, która odpowiada klasy <xref:System.Collections.ArrayList> nierodzajowej, ma wiele metod, które akceptują <xref:System.Predicate%601> delegatów ogólnych, takich jak delegat, który <xref:System.Action%601> pozwala określić metody wyszukiwania listy, delegat, który reprezentuje <xref:System.Converter%602> metody, które działają na każdym elemencie listy, a delegat, który umożliwia definiowanie konwersji między typami.  
  
 Klasa <xref:System.Collections.Generic.List%601> umożliwia określenie własnych <xref:System.Collections.Generic.IComparer%601> implementacji interfejsu ogólnego do sortowania i wyszukiwania listy. I <xref:System.Collections.Generic.SortedDictionary%602> <xref:System.Collections.Generic.SortedList%602> klasy również mają tę możliwość. Ponadto te klasy umożliwiają określenie comparers podczas tworzenia kolekcji. W podobny <xref:System.Collections.Generic.Dictionary%602> sposób, <xref:System.Collections.ObjectModel.KeyedCollection%602> i klasy pozwalają określić własne porównania równości.  
  
## <a name="see-also"></a>Zobacz też

- [Kolekcje i struktury danych](../../../docs/standard/collections/index.md)
- [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
- [Typy ogólne](../../../docs/standard/generics/index.md)
