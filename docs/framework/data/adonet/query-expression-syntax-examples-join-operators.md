---
title: 'Przykłady składni wyrażeń zapytania: Operatory sprzężenia (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f4d86667-3392-470d-a076-5ca6cbb660f6
ms.openlocfilehash: c150cb14c567590daa7ffb2ea77893598977bdf9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794862"
---
# <a name="query-expression-syntax-examples-join-operators-linq-to-dataset"></a>Przykłady składni wyrażeń zapytania: Operatory sprzężenia (LINQ to DataSet)
Łączenie jest ważną operacją w zapytaniach, które są przeznaczone dla źródeł danych, które nie mają relacji nawigacji ze sobą, takich jak tabele relacyjnej bazy danych. Sprzężenie dwóch źródeł danych to skojarzenie obiektów w jednym źródle danych z obiektami, które współużytkują wspólny atrybut w innym źródle danych. Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań —C#omówienie ()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) lub [standardowe operatory zapytań — Omówienie (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 W przykładach w tym temacie pokazano, jak używać <xref:System.Linq.Enumerable.GroupJoin%2A> metod <xref:System.Linq.Enumerable.Join%2A> i do wykonywania zapytań <xref:System.Data.DataSet> przy użyciu składni wyrażeń zapytań.  
  
 Metoda użyta w tych przykładach jest określona w temacie [ładowanie danych do zestawu danych.](loading-data-into-a-dataset.md) `FillDataSet`  
  
 W przykładach w tym temacie użyto tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.  
  
 Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt LINQ to DataSet w programie Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="groupjoin"></a>GroupJoin —  
  
### <a name="example"></a>Przykład  
 Ten przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> `SalesOrderHeader` przekroczenie tabeli `SalesOrderDetail` i, aby znaleźć liczbę zamówień na klienta. Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, które zwraca każdy element pierwszego (lewego) źródła danych, nawet jeśli żadne skorelowane elementy nie znajdują się w innym źródle danych.  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a>Przykład  
 Ten przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> `Contact` za pośrednictwem tabel `SalesOrderHeader` i. Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, które zwraca każdy element pierwszego (lewego) źródła danych, nawet jeśli żadne skorelowane elementy nie znajdują się w innym źródle danych.  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a>Łączenie  
  
### <a name="example"></a>Przykład  
 Ten przykład wykonuje sprzężenie `SalesOrderHeader` w tabelach i `SalesOrderDetail` , aby uzyskać zamówienia online od miesiąca sierpnia.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Zobacz także

- [Ładowanie danych do zestawu danych](loading-data-into-a-dataset.md)
- [Przykłady LINQ to DataSet](linq-to-dataset-examples.md)
- [Standardowe operatory zapytań — OmówienieC#()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
