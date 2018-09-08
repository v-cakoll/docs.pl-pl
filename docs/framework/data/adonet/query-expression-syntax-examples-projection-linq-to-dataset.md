---
title: 'Przykłady składni wyrażeń zapytania: Projekcji (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
ms.openlocfilehash: 92e013647b4f4b6ba14d46add24d5d71a6875bb0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44199898"
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a>Przykłady składni wyrażeń zapytania: Projekcji (LINQ to DataSet)
Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.Select%2A> i <xref:System.Linq.Enumerable.SelectMany%2A> metod do wykonywania zapytań <xref:System.Data.DataSet> przy użyciu składni wyrażeń zapytania.  
  
 `FillDataSet` Metodę używaną w tym przykładzie jest określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 Przykłady w tym temacie Korzystanie z tabel kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży w przykładowej bazy danych AdventureWorks.  
  
 Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: Tworzenie składnika LINQ to DataSet projektu w programie Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="select"></a>Wybierz  
  
### <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Enumerable.Select%2A> metodę, aby zwrócić wszystkie wiersze z `Product` tabelę i wyświetlić nazwy produktu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Enumerable.Select%2A> celu zwrócenia sekwencji tylko nazwy produktu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a>SelectMany  
  
### <a name="example"></a>Przykład  
 W tym przykładzie użyto `From …, …` (odpowiednik <xref:System.Linq.Enumerable.SelectMany%2A> metoda) aby zaznaczyć wszystko porządkuje gdzie `TotalDue` jest mniejsza niż 500,00.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a>Przykład  
 W tym przykładzie użyto `From …, …` (odpowiednik <xref:System.Linq.Enumerable.SelectMany%2A> metoda) aby wybrać wszystkie zamówienia, w którym kolejność została wprowadzona w 1 października 2002 lub nowszym.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a>Przykład  
 W tym przykładzie użyto `From …, …` (odpowiednik <xref:System.Linq.Enumerable.SelectMany%2A> metoda) aby wybrać wszystkie zamówienia, w którym kolejność łączna liczba jest większa niż 10000.00 i używa `From` przypisania, aby uniknąć żądanie Suma dwa razy.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a>Zobacz też  
 [Ładowanie danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [Przykłady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Standardowe operatory zapytań — przegląd](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
