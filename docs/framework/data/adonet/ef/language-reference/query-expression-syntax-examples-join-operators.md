---
title: 'Przykłady składni wyrażeń zapytania: Operatory sprzężenia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: 4db511d74c4cce82bfd010f77cb1580dbb704b41
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43476027"
---
# <a name="query-expression-syntax-examples-join-operators"></a>Przykłady składni wyrażeń zapytania: Operatory sprzężenia
Łączenie jest operacją ważne w zapytaniach, przeznaczonych dla źródeł danych, które mają żadnych relacji można nawigować do siebie nawzajem, takich jak tabel relacyjnej bazy danych. Przyłączenia dwóch źródeł danych jest skojarzenie obiektów w jednym źródle danych przy użyciu obiektów mających wspólny atrybut w źródle danych. Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Przegląd](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.GroupJoin%2A> i <xref:System.Linq.Enumerable.Join%2A> metod do wykonywania zapytań [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) przy użyciu składni wyrażeń zapytania. Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.  
  
 Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a>Groupjoin —  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> za pośrednictwem tabeli SalesOrderHeader i szczegóły zamówienia sprzedaży, aby znaleźć numer zamówienia na klienta. Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, która zwraca każdy element pierwszego źródła danych (po lewej stronie), nawet jeśli żadne elementy skorelowane znajdują się w źródle danych.  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> za pośrednictwem tabele kontaktu i SalesOrderHeader, aby znaleźć numer zamówienia na kontakt. Liczba zamówień i identyfikatory dla każdego kontaktu są wyświetlane.  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wykonuje <xref:System.Linq.Enumerable.GroupJoin%2A> za pośrednictwem kontaktu i SalesOrderHeader tabel. Sprzężenie grupy jest odpowiednikiem lewego sprzężenia zewnętrznego, która zwraca każdy element pierwszego źródła danych (po lewej stronie), nawet jeśli żadne elementy skorelowane znajdują się w źródle danych.  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a>Łączenie  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wykonuje sprzężenie tabel SalesOrderHeader i szczegóły zamówienia sprzedaży, które można pobrać zamówień online z sierpień.  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
