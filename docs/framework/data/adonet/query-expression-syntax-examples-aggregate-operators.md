---
title: 'Przykłady składni wyrażeń zapytania: Operatory agregujące (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85dafa07-e102-46e7-ab78-37bf06f257a6
ms.openlocfilehash: 44e38a53823cb52040a612d4762e33283f90e1d1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794526"
---
# <a name="query-expression-syntax-examples-aggregate-operators-linq-to-dataset"></a>Przykłady składni wyrażeń zapytania: Operatory agregujące (LINQ to DataSet)
W <xref:System.Linq.Enumerable.Average%2A>przykładach w tym temacie przedstawiono sposób użycia metod, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Sum%2A> do wykonywania zapytań <xref:System.Data.DataSet> dotyczących danych i agregowania ich przy użyciu składni wyrażeń zapytań.  
  
 Metoda użyta w tych przykładach jest określona w temacie [ładowanie danych do zestawu danych.](loading-data-into-a-dataset.md) `FillDataSet`  
  
 W przykładach w tym temacie użyto tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.  
  
 Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt LINQ to DataSet w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="average"></a>Average  
  
### <a name="example"></a>Przykład  
 W tym przykładzie zastosowano <xref:System.Linq.Enumerable.Average%2A> metodę w celu wyszukania średniej ceny za produkty poszczególnych stylów.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a>Przykład  
 Ten przykład używa <xref:System.Linq.Enumerable.Average%2A> , aby uzyskać średnią łączną ilość należną dla każdego identyfikatora osoby kontaktowej.  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a>Przykład  
 Ten przykład używa <xref:System.Linq.Enumerable.Average%2A> , aby uzyskać zamówienia z średnią `TotalDue` dla każdego kontaktu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a>Count  
  
### <a name="example"></a>Przykład  
 Ten przykład używa <xref:System.Linq.Enumerable.Count%2A> do zwracania listy identyfikatorów kontaktu oraz liczby zamówień, z których każdy ma.  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a>Przykład  
 Ten przykład grupuje produkty według koloru i <xref:System.Linq.Enumerable.Count%2A> używa do zwracania liczby produktów w każdej grupie kolorów.  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a>Maks.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie zastosowano metodę, <xref:System.Linq.Enumerable.Max%2A> Aby uzyskać największą łączną ilość należną dla każdego identyfikatora osoby kontaktowej.  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a>Przykład  
 Ten przykład używa metody <xref:System.Linq.Enumerable.Max%2A> , aby uzyskać zamówienia o największych `TotalDue` dla każdego identyfikatora osoby kontaktowej.  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a>Min.  
  
### <a name="example"></a>Przykład  
 Ten przykład używa <xref:System.Linq.Enumerable.Min%2A> metody, aby uzyskać najmniejszą łączną ilość należną dla każdego identyfikatora osoby kontaktowej.  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a>Przykład  
 Ten przykład używa metody <xref:System.Linq.Enumerable.Min%2A> , aby uzyskać zamówienia z najmniejszą łączną należną dla każdego kontaktu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a>Suma  
  
### <a name="example"></a>Przykład  
 Ten przykład używa metody <xref:System.Linq.Enumerable.Sum%2A> , aby uzyskać łączną ilość należną dla każdego identyfikatora osoby kontaktowej.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a>Zobacz także

- [Ładowanie danych do zestawu danych](loading-data-into-a-dataset.md)
- [Przykłady LINQ to DataSet](linq-to-dataset-examples.md)
- [Standardowe operatory zapytań — OmówienieC#()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
