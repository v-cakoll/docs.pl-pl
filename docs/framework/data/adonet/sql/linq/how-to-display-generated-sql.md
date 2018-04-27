---
title: 'Porady: wyświetlanie wygenerowany SQL'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: c58e691bdf39e71a756c8b26451c22c769f05c0a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="a1f56-102">Porady: wyświetlanie wygenerowany SQL</span><span class="sxs-lookup"><span data-stu-id="a1f56-102">How to: Display Generated SQL</span></span>
<span data-ttu-id="a1f56-103">Możesz wyświetlić kod SQL wygenerowana dla zapytań i zmień przetwarzanie przy użyciu <xref:System.Data.Linq.DataContext.Log%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a1f56-103">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="a1f56-104">Ta metoda może być przydatna do zrozumienia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] funkcjonalność i debugowanie określonych problemów.</span><span class="sxs-lookup"><span data-stu-id="a1f56-104">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1f56-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1f56-105">Example</span></span>  
 <span data-ttu-id="a1f56-106">W poniższym przykładzie użyto <xref:System.Data.Linq.DataContext.Log%2A> właściwość, aby wyświetlić kod SQL w oknie konsoli, przed wykonaniem kodu.</span><span class="sxs-lookup"><span data-stu-id="a1f56-106">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="a1f56-107">Możesz używać tej właściwości zapytania, insert, update i usunąć poleceń.</span><span class="sxs-lookup"><span data-stu-id="a1f56-107">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="a1f56-108">Wiersze z okna konsoli są, zobacz podczas wykonywania kodu języka Visual Basic lub C#, znajdujący się.</span><span class="sxs-lookup"><span data-stu-id="a1f56-108">The lines from the console window are what you see when you execute the Visual Basic or C# code that follows.</span></span>  
  
```  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a1f56-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1f56-109">See Also</span></span>  
 [<span data-ttu-id="a1f56-110">Obsługa debugowania</span><span class="sxs-lookup"><span data-stu-id="a1f56-110">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
