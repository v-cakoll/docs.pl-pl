---
title: 'Przykłady składni kwerend opartych na metodzie: Operatory elementów (LINQ do DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eedf2fbd-f407-4f62-bb1a-c00eb001b1dd
ms.openlocfilehash: e43208d6ae524a1370b936d42508e9c7a7d196e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149510"
---
# <a name="method-based-query-syntax-examples-element-operators-linq-to-dataset"></a>Przykłady składni kwerend opartych na metodzie: Operatory elementów (LINQ do DataSet)
Przykłady w tym temacie pokazano, <xref:System.Linq.Enumerable.First%2A> <xref:System.Linq.Enumerable.ElementAt%2A> jak używać <xref:System.Data.DataRow> i <xref:System.Data.DataSet> metody, aby uzyskać elementy z przy użyciu składni wyrażenia kwerendy.  
  
 Metoda `FillDataSet` używana w tych przykładach jest określona w [loading data into a DataSet](loading-data-into-a-dataset.md).  
  
 Przykłady w tym temacie używają kontaktów, adres, produkt, SalesOrderHeader i SalesOrderDetail tabel w adventureworks przykładowej bazy danych.  
  
 Przykłady w tym temacie `using` / `Imports` używają następujących instrukcji:  
  
[!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
[!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]

 Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie projektu LINQ do zestawu danych w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="elementat"></a>Elementat  
  
### <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.Linq.Enumerable.ElementAt%2A> użyto metody do `PostalCode` pobrania piątego adresu, gdzie == "M4B 1V7".  
  
[!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
[!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]
  
## <a name="first"></a>First  
  
### <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.Linq.Enumerable.First%2A> użyto metody do zwrócenia pierwszego kontaktu, którego imię to "Brooke".  
  
[!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
[!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]
  
## <a name="see-also"></a>Zobacz też

- [Ładowanie danych do zestawu danych](loading-data-into-a-dataset.md)
- [Przykłady LINQ to DataSet](linq-to-dataset-examples.md)
- [Omówienie standardowych operatorów kwerend (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Omówienie standardowych operatorów zapytań (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
