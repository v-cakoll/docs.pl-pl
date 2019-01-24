---
title: 'Instrukcje: Wyświetlanie składnika LINQ to SQL poleceń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1decb05e-37ad-4ed6-ab2f-071eb4c4f628
ms.openlocfilehash: a70f1e0dd471e86afe2e744c157d4aed2a217deb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630830"
---
# <a name="how-to-display-linq-to-sql-commands"></a>Instrukcje: Wyświetlanie składnika LINQ to SQL poleceń
Użyj <xref:System.Data.Linq.DataContext.GetCommand%2A> do wyświetlania poleceń SQL i inne informacje.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie w oknie konsoli wyświetlane dane wyjściowe z zapytania, następuje poleceń SQL, które są generowane, typ poleceń i typ połączenia.  
  
 [!code-csharp[DLinqDebuggingSupport#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#3)]
 [!code-vb[DLinqDebuggingSupport#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#3)]  
  
 Dane wyjściowe wyglądają następująco:  
  
```  
Customers from London:  
    Thomas Hardy  
    Victoria Ashworth  
    Elizabeth Brown  
    Ann Devon  
    Simon Crowther  
    Marie Bertrand  
    Hari Kumar  
    Dominique Perrier  
```  
  
```  
Command Text:  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
  
Command Type: Text  
  
Connection: System.Data.SqlClient.SqlConnection  
```  
  
## <a name="see-also"></a>Zobacz także
- [Obsługa debugowania](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
