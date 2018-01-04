---
title: "Porady: wyświetlanie LINQ do poleceń SQL"
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
ms.assetid: 1decb05e-37ad-4ed6-ab2f-071eb4c4f628
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 343cf07ead03ccba82606d918a3a5d0106f5b0e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-linq-to-sql-commands"></a><span data-ttu-id="5f70a-102">Porady: wyświetlanie LINQ do poleceń SQL</span><span class="sxs-lookup"><span data-stu-id="5f70a-102">How to: Display LINQ to SQL Commands</span></span>
<span data-ttu-id="5f70a-103">Użyj <xref:System.Data.Linq.DataContext.GetCommand%2A> do wyświetlenia poleceń SQL i innych informacji.</span><span class="sxs-lookup"><span data-stu-id="5f70a-103">Use <xref:System.Data.Linq.DataContext.GetCommand%2A> to display SQL commands and other information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f70a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f70a-104">Example</span></span>  
 <span data-ttu-id="5f70a-105">W poniższym przykładzie w oknie konsoli wyświetla wyniki zapytania, następuje poleceń SQL, które są generowane, typ poleceń i typ połączenia.</span><span class="sxs-lookup"><span data-stu-id="5f70a-105">In the following example, the console window displays the output from the query, followed by the SQL commands that are generated, the type of commands, and the type of connection.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#3)]
 [!code-vb[DLinqDebuggingSupport#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#3)]  
  
 <span data-ttu-id="5f70a-106">Dane wyjściowe wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="5f70a-106">Output appears as follows:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f70a-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f70a-107">See Also</span></span>  
 [<span data-ttu-id="5f70a-108">Obsługa debugowania</span><span class="sxs-lookup"><span data-stu-id="5f70a-108">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
