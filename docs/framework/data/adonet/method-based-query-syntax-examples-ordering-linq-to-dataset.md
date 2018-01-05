---
title: "Przykłady składni zapytania oparte na metodzie: Porządkowanie (LINQ do DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6496d628538caa6cd0af328e6594f8453b40afb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a>Przykłady składni zapytania oparte na metodzie: Porządkowanie (LINQ do DataSet)
Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, i <xref:System.Linq.Enumerable.ThenBy%2A> metod do badania <xref:System.Data.DataSet> i kolejność wyniki za pomocą składni zapytania metody.  
  
 `FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 Przykłady w tym temacie można użyć kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabel w bazie danych AdventureWorks.  
  
 Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: tworzenie LINQ do DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="orderby"></a>OrderBy  
  
### <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Enumerable.OrderBy%2A> metody o niestandardowych moduł porównujący sortowania bez uwzględniania wielkości liter nazwisk zrobić.  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a>Reverse  
  
### <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Enumerable.Reverse%2A> metodę, aby utworzyć listę zleceń, gdzie `OrderDate` jest starsza niż 20 luty 2002.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a>ThenBy  
  
### <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Enumerable.OrderBy%2A> i <xref:System.Linq.Enumerable.ThenBy%2A> metody o niestandardowej funkcji porównującej pierwszy sortować cennika, a następnie wykonaj malejącym bez uwzględniania wielkości liter nazwy produktu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a>Zobacz też  
 [Ładowanie danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [Przykłady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Standardowe operatory zapytań — przegląd](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
