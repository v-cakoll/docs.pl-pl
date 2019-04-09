---
title: 'Instrukcje: Wyświetlanie wygenerowanego kodu SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: 8a69b3ae83d7f701428b3183f2b80e0d44a06537
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103626"
---
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="e853a-102">Instrukcje: Wyświetlanie wygenerowanego kodu SQL</span><span class="sxs-lookup"><span data-stu-id="e853a-102">How to: Display Generated SQL</span></span>
<span data-ttu-id="e853a-103">Można wyświetlić kodu SQL, generowany dla zapytań i przetwarzania przy użyciu zmiany <xref:System.Data.Linq.DataContext.Log%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e853a-103">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="e853a-104">Takie podejście może być przydatne do zrozumienia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] funkcjonalność i debugowania konkretnych problemów.</span><span class="sxs-lookup"><span data-stu-id="e853a-104">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e853a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e853a-105">Example</span></span>  
 <span data-ttu-id="e853a-106">W poniższym przykładzie użyto <xref:System.Data.Linq.DataContext.Log%2A> właściwość, aby wyświetlić kod SQL w oknie konsoli, zanim kod zostanie wykonany.</span><span class="sxs-lookup"><span data-stu-id="e853a-106">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="e853a-107">Można używać tej właściwości przy użyciu zapytań, wstawiania, aktualizacji i usuwania poleceń.</span><span class="sxs-lookup"><span data-stu-id="e853a-107">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="e853a-108">Wiersze z okna konsoli są, zobacz podczas wykonywania Visual Basic lub C# kod następujący po ciągu.</span><span class="sxs-lookup"><span data-stu-id="e853a-108">The lines from the console window are what you see when you execute the Visual Basic or C# code that follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e853a-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e853a-109">See also</span></span>

- [<span data-ttu-id="e853a-110">Obsługa debugowania</span><span class="sxs-lookup"><span data-stu-id="e853a-110">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
