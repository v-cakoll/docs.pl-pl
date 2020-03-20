---
title: 'Przykłady składni wyrażenia kwerendy: ograniczenie (LINQ do dataset)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
ms.openlocfilehash: 6ec4eac6c0fb2d044e429e88d50c619aa38de4b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149196"
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a>Przykłady składni wyrażenia kwerendy: ograniczenie (LINQ do dataset)
Przykłady w tym temacie pokazują, <xref:System.Linq.Enumerable.Where%2A> jak użyć <xref:System.Data.DataSet> metody do kwerendy przy użyciu składni wyrażenia kwerendy.  
  
 Metoda `FillDataSet` używana w tych przykładach jest określona w [loading data into a DataSet](loading-data-into-a-dataset.md).  
  
 Przykłady w tym temacie używają kontaktów, adres, produkt, SalesOrderHeader i SalesOrderDetail tabel w adventureworks przykładowej bazy danych.  
  
 Przykłady w tym temacie `using` / `Imports` używają następujących instrukcji:  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
  
 Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie projektu LINQ do zestawu danych w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="where"></a>Lokalizacja  
  
### <a name="example"></a>Przykład  
 W tym przykładzie zwraca wszystkie zamówienia online.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
### <a name="example"></a>Przykład  
 W tym przykładzie zwraca zamówienia, w których ilość zamówienia jest większa niż 2 i mniejsza niż 6.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]
  
### <a name="example"></a>Przykład  
 W tym przykładzie zwraca wszystkie produkty w kolorze czerwonym.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]
  
### <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.Linq.Enumerable.Where%2A> użyto metody, aby znaleźć zamówienia, które zostały wykonane po <xref:System.Data.DataRow.GetChildRows%2A> 1 grudnia 2002 r., a następnie używa metody, aby uzyskać szczegółowe informacje dla każdego zamówienia.  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a>Zobacz też

- [Ładowanie danych do zestawu danych](loading-data-into-a-dataset.md)
- [Przykłady LINQ to DataSet](linq-to-dataset-examples.md)
- [Omówienie standardowych operatorów kwerend (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Omówienie standardowych operatorów zapytań (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
