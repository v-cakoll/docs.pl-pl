---
title: Zapytania zagregowane
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 1c8f6191cfb832a71bd32c60db492eafb8ca22ca
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858695"
---
# <a name="aggregate-queries"></a>Zapytania zagregowane
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje `Average`, `Count`, `Max`, `Min`, i `Sum` operatorów agregacji. Należy zwrócić uwagę na następujące cechy operatory agregacji w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:  
  
-   Zapytania zagregowane są wykonywane natychmiast.  
  
     Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
-   Zapytania zagregowane zwykle zwracają liczbę zamiast kolekcji.  
  
     Aby uzyskać więcej informacji, zobacz [operacje agregacji](https://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).  
  
-   Nie można wywołać wartości zagregowanych dla typów anonimowych.  
  
 W przykładach w następujących tematach pochodzi z przykładowej bazy danych Northwind. Aby uzyskać więcej informacji, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zwracanie średniej wartości z sekwencji numerycznej](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 Pokazuje sposób użycia <xref:System.Linq.Enumerable.Average%2A> operatora.  
  
 [Licznik liczby elementów w sekwencji](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 Pokazuje sposób użycia <xref:System.Linq.Enumerable.Count%2A> operatora.  
  
 [Odnajdywanie wartości maksymalnej w sekwencji numerycznej](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 Pokazuje sposób użycia <xref:System.Linq.Enumerable.Max%2A> operatora.  
  
 [Odnajdywanie wartości minimalnej w sekwencji numerycznej](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 Pokazuje sposób użycia <xref:System.Linq.Enumerable.Min%2A> operatora.  
  
 [Obliczanie sumy wartości w sekwencji numerycznej](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 Pokazuje sposób użycia <xref:System.Linq.Enumerable.Sum%2A> operatora.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 Zawiera łącza do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania w języku Visual Basic i C#.  
  
 [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 Zawiera łącza do tematów, które opisują pojęć dotyczących projektowania [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytania w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Wprowadzenie do zapytań LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 Wyjaśnia, jak działa zapytania w [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].
