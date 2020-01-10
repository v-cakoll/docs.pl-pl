---
title: Kiedy należy używać kolekcji ogólnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: 7d59259c1cab6842ef62888bf5326225394d8d44
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711210"
---
# <a name="when-to-use-generic-collections"></a>Kiedy należy używać kolekcji ogólnych
Ogólnie zalecane jest korzystanie z kolekcji ogólnych, ponieważ uzyskanie natychmiastowej korzyści ze stosowania typu "bezpieczeństwo" nie będzie miało wpływu na typ kolekcji podstawowej i implementować członków właściwych dla określonego typu. Ogólne typy kolekcji są również zwykle wykonywane lepiej niż odpowiednie typy kolekcji nieogólnej (i lepsza niż typy, które pochodzą z nieogólnych typów kolekcji podstawowych), gdy elementy kolekcji są typami wartości, ponieważ z ogólnymi nie trzeba pola.  
  
 W przypadku programów przeznaczonych dla .NET Framework 4 lub nowszych należy używać klas kolekcji generycznej w przestrzeni nazw <xref:System.Collections.Concurrent>, gdy wiele wątków może jednocześnie dodawać lub usuwać elementy z kolekcji.  
  
 Następujące typy ogólne odpowiadają istniejącym typom kolekcji:  
  
- <xref:System.Collections.Generic.List%601> jest klasą rodzajową, która odnosi się do <xref:System.Collections.ArrayList>.  
  
- <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602> są klasami ogólnymi, które odpowiadają <xref:System.Collections.Hashtable>.  
  
- <xref:System.Collections.ObjectModel.Collection%601> jest klasą rodzajową, która odnosi się do <xref:System.Collections.CollectionBase>. <xref:System.Collections.ObjectModel.Collection%601> może być używana jako klasa bazowa, ale w przeciwieństwie do <xref:System.Collections.CollectionBase>, nie jest abstrakcyjna. Znacznie ułatwia to korzystanie z programu.  
  
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> jest klasą rodzajową, która odnosi się do <xref:System.Collections.ReadOnlyCollectionBase>. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> nie jest abstrakcyjna i ma konstruktora, który ułatwia Uwidacznianie istniejącej <xref:System.Collections.Generic.List%601> jako kolekcji tylko do odczytu.  
  
- Klasy generyczne <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>i <xref:System.Collections.Generic.SortedList%602> odpowiadają odpowiednim klasom nieogólnym o tych samych nazwach.  
  
## <a name="additional-types"></a>Dodatkowe typy  
 Kilka rodzajowych typów kolekcji nie ma odpowiedników nierodzajowych. Są to następujące nazwy:  
  
- <xref:System.Collections.Generic.LinkedList%601> to lista połączona ogólnego przeznaczenia, która zapewnia operacje wstawiania i usuwania O (1).  
  
- <xref:System.Collections.Generic.SortedDictionary%602> to posortowany słownik z operacjami wstawiania i pobierania (log `n`), co sprawia, że jest to użyteczna alternatywa dla <xref:System.Collections.Generic.SortedList%602>.  
  
- <xref:System.Collections.ObjectModel.KeyedCollection%602> jest hybrydową między listą a słownikiem, który umożliwia przechowywanie obiektów zawierających własne klucze.  
  
- <xref:System.Collections.Concurrent.BlockingCollection%601> implementuje klasę kolekcji z funkcją ograniczenia i blokowania.  
  
- <xref:System.Collections.Concurrent.ConcurrentBag%601> zapewnia szybkie Wstawianie i usuwanie nieuporządkowanych elementów.  
  
## <a name="linq-to-objects"></a>LINQ do obiektów  
 Funkcja LINQ to Objects umożliwia używanie zapytań LINQ do uzyskiwania dostępu do obiektów w pamięci, o ile typ obiektu implementuje interfejs <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Zapytania LINQ zapewniają wspólny wzorzec dostępu do danych; są zwykle bardziej zwięzłe i czytelne niż standardowe pętle `foreach`. i umożliwiają filtrowanie, porządkowanie i grupowanie. Zapytania LINQ mogą również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ to ObjectsC#()](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)i [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="additional-functionality"></a>Dodatkowe funkcje  
 Niektóre typy ogólne mają funkcje, które nie znajdują się w nierodzajowych typach kolekcji. Na przykład Klasa <xref:System.Collections.Generic.List%601>, która odnosi się do niegenerycznej <xref:System.Collections.ArrayList> klasy, ma wiele metod, które akceptują delegatów ogólnych, takich jak delegat <xref:System.Predicate%601>, który umożliwia określenie metod wyszukiwania listy, delegat <xref:System.Action%601>, który reprezentuje metody, które działają na każdym elemencie listy, i delegata <xref:System.Converter%602>, który umożliwia definiowanie konwersji między typami.  
  
 Klasa <xref:System.Collections.Generic.List%601> umożliwia określenie własnych <xref:System.Collections.Generic.IComparer%601> ogólnych implementacji interfejsu w celu sortowania i przeszukiwania listy. Klasy <xref:System.Collections.Generic.SortedDictionary%602> i <xref:System.Collections.Generic.SortedList%602> również mają tę możliwość. Ponadto klasy te umożliwiają określanie porównań podczas tworzenia kolekcji. W podobny sposób klasy <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.ObjectModel.KeyedCollection%602> pozwalają określić własne porównania równości.  
  
## <a name="see-also"></a>Zobacz także

- [Kolekcje i struktury danych](../../../docs/standard/collections/index.md)
- [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
- [Typy ogólne](../../../docs/standard/generics/index.md)
