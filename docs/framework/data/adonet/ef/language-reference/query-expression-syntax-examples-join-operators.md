---
title: 'Przykłady składni wyrażeń zapytania: Operatory sprzęgania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: e80c50daeb0de7f4a8477786f28441d1495033ea
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249487"
---
# <a name="query-expression-syntax-examples-join-operators"></a>Przykłady składni wyrażeń zapytania: Operatory sprzęgania
Łączenie jest ważną operacją w zapytaniach, które są przeznaczone dla źródeł danych, które nie mają relacji nawigacji ze sobą, takich jak tabele relacyjnej bazy danych. Sprzężenie dwóch źródeł danych to skojarzenie obiektów w jednym źródle danych z obiektami, które współużytkują wspólny atrybut w innym źródle danych. Aby uzyskać więcej informacji, zobacz [Omówienie standardowych operatorów zapytań](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).  
  
 W przykładach w tym temacie pokazano, <xref:System.Linq.Enumerable.GroupJoin%2A> jak za pomocą metod i <xref:System.Linq.Enumerable.Join%2A> zbadać [model sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni wyrażeń zapytań. Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.  
  
 Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a>GroupJoin —  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> przekroczenie tabeli SalesOrderHeader i SalesOrderDetail, aby znaleźć liczbę zamówień na klienta. Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, które zwraca każdy element pierwszego (lewego) źródła danych, nawet jeśli żadne skorelowane elementy nie znajdują się w innym źródle danych.  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> przekroczenie w tabelach Contact i SalesOrderHeader, aby znaleźć liczbę zamówień na kontakt. Zostanie wyświetlona liczba i identyfikatory zamówień dla każdego kontaktu.  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a>Łączenie  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wykonuje sprzężenie w tabelach SalesOrderHeader i SalesOrderDetail w celu uzyskania zamówień online od miesiąca sierpnia.  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania w składniku LINQ to Entities](queries-in-linq-to-entities.md)
