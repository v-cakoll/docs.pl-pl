---
title: Kiedy należy używać kolekcji ogólnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: bbf8ec7f61981332b6984488b369fee62959b92a
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635888"
---
# <a name="when-to-use-generic-collections"></a>Kiedy używać kolekcji ogólnych

Za pomocą kolekcji ogólnych zapewnia automatyczne korzyści bezpieczeństwa typu bez konieczności pochodzić z typu kolekcji podstawowej i implementować elementy członkowskie specyficzne dla typu. Typy kolekcji ogólne również zazwyczaj działają lepiej niż odpowiednie typy kolekcji nierodzajowych (i lepiej niż typy, które są pochodną niegenerycznych typów kolekcji podstawowych), gdy elementy kolekcji są typami wartości, ponieważ w przypadku typów ogólnych nie ma potrzeby wypełniania elementów.  
  
 W przypadku programów przeznaczonych dla programu .NET Framework 4 lub <xref:System.Collections.Concurrent> nowszego należy użyć klas kolekcji rodzajowej w obszarze nazw, gdy wiele wątków może jednocześnie dodawać lub usuwać elementy z kolekcji.  
  
 Następujące typy ogólne odpowiadają istniejącym typom kolekcji:  
  
- <xref:System.Collections.Generic.List%601>jest klasą rodzajową, <xref:System.Collections.ArrayList>która odpowiada .  
  
- <xref:System.Collections.Generic.Dictionary%602>i <xref:System.Collections.Concurrent.ConcurrentDictionary%602> są klasy ogólne, <xref:System.Collections.Hashtable>które odpowiadają .  
  
- <xref:System.Collections.ObjectModel.Collection%601>jest klasą rodzajową, <xref:System.Collections.CollectionBase>która odpowiada . <xref:System.Collections.ObjectModel.Collection%601>może być używany jako klasa <xref:System.Collections.CollectionBase>podstawowa, ale w przeciwieństwie do , nie jest abstrakcyjny, co znacznie ułatwia korzystanie.  
  
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>jest klasą rodzajową, <xref:System.Collections.ReadOnlyCollectionBase>która odpowiada . <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>nie jest abstrakcyjny i ma konstruktora, <xref:System.Collections.Generic.List%601> który ułatwia udostępnienie istniejącej jako kolekcji tylko do odczytu.  
  
- Klasy <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601> <xref:System.Collections.Concurrent.ConcurrentStack%601>, <xref:System.Collections.Generic.SortedList%602> i ogólne odpowiadają odpowiednim klasom nierodzajmym o tych samych nazwach.  
  
## <a name="additional-types"></a>Dodatkowe typy  
 Kilka typów kolekcji rodzajowych nie mają odpowiedników nierodzajowych. Należą do nich:  
  
- <xref:System.Collections.Generic.LinkedList%601>jest listą połączonej ogólnego przeznaczenia, która zapewnia operacje wstawiania i usuwania O(1).  
  
- <xref:System.Collections.Generic.SortedDictionary%602>jest posortowanym słownikiem `n`z o(log) wstawiania i pobierania <xref:System.Collections.Generic.SortedList%602>operacji, co czyni go użyteczną alternatywą dla .  
  
- <xref:System.Collections.ObjectModel.KeyedCollection%602>jest hybrydą między listą a słownikiem, która umożliwia przechowywanie obiektów zawierających własne klucze.  
  
- <xref:System.Collections.Concurrent.BlockingCollection%601>implementuje klasę kolekcji z funkcją ograniczającą i blokującą.  
  
- <xref:System.Collections.Concurrent.ConcurrentBag%601>zapewnia szybkie wstawianie i usuwanie nieurządzonych elementów.  
  
## <a name="linq-to-objects"></a>LINQ do obiektów  
 Linq do obiektów funkcja umożliwia korzystanie z zapytań LINQ, aby uzyskać dostęp do <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> obiektów w pamięci tak długo, jak typ obiektu implementuje lub interfejs. Zapytania LINQ zapewniają typowy wzorzec dostępu do danych; są zazwyczaj bardziej zwięzłe i czytelne niż standardowe `foreach` pętle; i zapewniają możliwości filtrowania, zamawiania i grupowania. Zapytania LINQ można również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ do obiektów (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ do obiektów (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)i [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md).  
  
## <a name="additional-functionality"></a>Dodatkowa funkcjonalność  
 Niektóre typy ogólne mają funkcje, które nie można znaleźć w typach kolekcji nierodzajowych. Na przykład <xref:System.Collections.Generic.List%601> klasa, która odpowiada klasy nierodzajowej, <xref:System.Collections.ArrayList> ma szereg metod, które akceptują delegatów rodzajowych, takich jak <xref:System.Action%601> <xref:System.Converter%602> <xref:System.Predicate%601> delegata, który pozwala określić metody wyszukiwania listy, delegata, który reprezentuje metody, które działają na każdy element listy i delegata, który pozwala zdefiniować konwersje między typami.  
  
 Klasa <xref:System.Collections.Generic.List%601> umożliwia określenie własnych <xref:System.Collections.Generic.IComparer%601> implementacji interfejsu ogólnego do sortowania i przeszukiwania listy. I <xref:System.Collections.Generic.SortedDictionary%602> <xref:System.Collections.Generic.SortedList%602> klasy również mają tę możliwość. Ponadto te klasy umożliwiają określenie modułów porównujących podczas tworzenia kolekcji. W podobny sposób <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.ObjectModel.KeyedCollection%602> i klasy umożliwiają określenie własnych porównywarki równości.  
  
## <a name="see-also"></a>Zobacz też

- [Kolekcje i struktury danych](../../../docs/standard/collections/index.md)
- [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
- [Typy ogólne](../../../docs/standard/generics/index.md)
