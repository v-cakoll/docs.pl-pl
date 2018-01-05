---
title: Zapytania zagregowane
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0f76178d6b10e8253fd135c35504389e03d8acae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="aggregate-queries"></a>Zapytania zagregowane
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje `Average`, `Count`, `Max`, `Min`, i `Sum` operatorów agregacji. Należy zauważyć następujące właściwości operatorów agregacji w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:  
  
-   Zapytania agregujące są wykonywane natychmiast.  
  
     Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
-   Zapytania agregujące zwracają zazwyczaj numer zamiast kolekcji.  
  
     Aby uzyskać więcej informacji, zobacz [operacje agregacji](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).  
  
-   Nie można wywołać wartości zagregowanych dla typów anonimowych.  
  
 Przykłady w następujących tematach pochodzi z przykładowej bazy danych Northwind. Aby uzyskać więcej informacji, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zwracanie średniej wartości z sekwencji numerycznej](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 Pokazuje, jak używać <xref:System.Linq.Enumerable.Average%2A> operatora.  
  
 [Licznik liczby elementów w sekwencji](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 Pokazuje, jak używać <xref:System.Linq.Enumerable.Count%2A> operatora.  
  
 [Odnajdywanie wartości maksymalnej w sekwencji numerycznej](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 Pokazuje, jak używać <xref:System.Linq.Enumerable.Max%2A> operatora.  
  
 [Odnajdywanie wartości minimalnej w sekwencji numerycznej](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 Pokazuje, jak używać <xref:System.Linq.Enumerable.Min%2A> operatora.  
  
 [Obliczanie sumy wartości w sekwencji numerycznej](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 Pokazuje, jak używać <xref:System.Linq.Enumerable.Sum%2A> operatora.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 Zawiera łącza do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania w Visual Basic i C#.  
  
 [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 Zawiera łącza do tematów, które opisano pojęcia związane z projektowaniem [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytania w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 Objaśniono, w jaki sposób zapytań [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].
