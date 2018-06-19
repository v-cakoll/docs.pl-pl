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
ms.openlocfilehash: 1ea40542b235dd51bfec38aae9718b2278d7073b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572648"
---
# <a name="when-to-use-generic-collections"></a>Kiedy należy używać kolekcji ogólnych
Kolekcje ogólne ogólnie zaleca się użycie, ponieważ uzyskanie natychmiastowe korzyści wynikające z zabezpieczeń bez konieczności pochodzić od typu podstawowego kolekcji i implementować członków określonego typu. Typy kolekcji ogólnych ogólnie lepiej niż odpowiednie typy kolekcji nierodzajowe (i lepszą wydajność niż typy który pochodne typy nierodzajowe kolekcji podstawowej) gdy elementy kolekcji są typy wartości, ponieważ z ogólnymi nie trzeba elementy w polu.  
  
 Dla programów przeznaczonych [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] lub później, należy użyć klasy rodzajowej kolekcji w <xref:System.Collections.Concurrent> przestrzenią nazw, gdy wiele wątków może Dodawanie lub usuwanie elementów z kolekcji jednocześnie.  
  
 Następujące typy ogólne odpowiadają istniejących typów kolekcji:  
  
-   <xref:System.Collections.Generic.List%601> jest ogólny klasy, która odpowiada <xref:System.Collections.ArrayList>.  
  
-   <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602> są ogólne klasy, które odpowiadają <xref:System.Collections.Hashtable>.  
  
-   <xref:System.Collections.ObjectModel.Collection%601> jest ogólny klasy, która odpowiada <xref:System.Collections.CollectionBase>. <xref:System.Collections.ObjectModel.Collection%601> mogą być używane jako klasy podstawowej, lecz w przeciwieństwie do <xref:System.Collections.CollectionBase>, nie jest abstrakcyjna. Dzięki temu można łatwiej używać.  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> jest ogólny klasy, która odpowiada <xref:System.Collections.ReadOnlyCollectionBase>. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> nie jest abstrakcyjna i ma Konstruktor, który ułatwia udostępnianie istniejące <xref:System.Collections.Generic.List%601> jako kolekcji tylko do odczytu.  
  
-   <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>, I <xref:System.Collections.Generic.SortedList%602> klas rodzajowych odpowiadają odpowiednich klas nierodzajowe pod tą samą nazwą.  
  
## <a name="additional-types"></a>Dodatkowe typy  
 Typy kolekcji ogólnych kilka nie mają nierodzajowe odpowiedniki. Obejmują one następujące czynności:  
  
-   <xref:System.Collections.Generic.LinkedList%601> jest ogólnego przeznaczenia listy połączonej, który zapewnia O(1) operacji wstawiania i usuwania.  
  
-   <xref:System.Collections.Generic.SortedDictionary%602> jest posortowany słownik z O (dziennika `n`) operacji wstawiania i odzyskiwania, dzięki czemu będzie on przydatne zamiast <xref:System.Collections.Generic.SortedList%602>.  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602> jest hybrydowego między listą słownik, który umożliwia przechowywanie obiektów, które zawierają własne klucze.  
  
-   <xref:System.Collections.Concurrent.BlockingCollection%601> implementuje klasy kolekcji za pomocą funkcji blokujących i ograniczających.  
  
-   <xref:System.Collections.Concurrent.ConcurrentBag%601> zapewnia szybkie wstawiania i usuwania elementów nieuporządkowaną.  
  
## <a name="linq-to-objects"></a>LINQ do obiektów  
 LINQ do obiektów funkcji pozwala na użycie zapytań LINQ do obiektów w pamięci, tak długo, jak typ obiektu implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu. Zapytania LINQ Podaj wspólnego wzorca do uzyskiwania dostępu do danych; zazwyczaj są to zwięzły i bardziej czytelny niż standardowe `foreach` pętli; oraz udostępnia filtrowania, kolejność i grupowanie możliwości. Zapytania LINQ także może zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ do obiektów](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9) i [równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="additional-functionality"></a>Dodatkowe funkcje  
 Niektórych typów ogólnych są funkcje, które nie znajduje się w typach nierodzajowe kolekcji. Na przykład <xref:System.Collections.Generic.List%601> klasy, która odpowiada nongeneric <xref:System.Collections.ArrayList> klasa, ma wiele metod, które akceptują delegatów, takich jak <xref:System.Predicate%601> delegata, który pozwala na określenie metody wyszukiwania na liście <xref:System.Action%601>delegata, który reprezentuje metody, które mają wpływ na każdy element listy, a <xref:System.Converter%602> delegata, który pozwala zdefiniować konwersji między typami.  
  
 <xref:System.Collections.Generic.List%601> Klasa pozwala na określenie własnych <xref:System.Collections.Generic.IComparer%601> implementacje ogólny interfejs do listy wyszukiwania i sortowania. <xref:System.Collections.Generic.SortedDictionary%602> i <xref:System.Collections.Generic.SortedList%602> klasy również mają tę możliwość. Ponadto te klasy umożliwiają określenie comparers po utworzeniu kolekcji. W podobny sposób <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.ObjectModel.KeyedCollection%602> klasy umożliwiają określenie własnych comparers równości.  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje i struktury danych](../../../docs/standard/collections/index.md)  
 [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)  
 [Typy ogólne](../../../docs/standard/generics/index.md)
