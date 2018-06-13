---
title: 'Przykłady składni zapytania oparte na metodzie: Element operatory (LINQ do DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eedf2fbd-f407-4f62-bb1a-c00eb001b1dd
ms.openlocfilehash: 8c01709f062048db34680ef8ba987f6e08bf15f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764154"
---
# <a name="method-based-query-syntax-examples-element-operators-linq-to-dataset"></a>Przykłady składni zapytania oparte na metodzie: Element operatory (LINQ do DataSet)
Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.First%2A> i <xref:System.Linq.Enumerable.ElementAt%2A> metody w celu uzyskania <xref:System.Data.DataRow> elementy z <xref:System.Data.DataSet> przy użyciu składni wyrażenia zapytania.  
  
 `FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 Przykłady w tym temacie można użyć kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabel w bazie danych AdventureWorks.  
  
 Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:  
  
[!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]   
[!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]     

 Aby uzyskać więcej informacji, zobacz [porady: tworzenie LINQ do DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="elementat"></a>ElementAt  
  
### <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Enumerable.ElementAt%2A> metoda pobierania piąty adres gdzie `PostalCode` == "M4B 1V7".  
  
[!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]   
[!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]     
  
## <a name="first"></a>pierwszy  
  
### <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Enumerable.First%2A> metodę, aby zwrócić którego imię pierwszego kontaktu jest "Brooke".  
  
[!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]   
[!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)] 
  
## <a name="see-also"></a>Zobacz też  
 [Ładowanie danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [Przykłady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Standardowe operatory zapytań — przegląd](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
