---
title: 'Instrukcje: wyświetlanie wygenerowanego kodu SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: 15fc6a50d232ea12b229b7b2790c0398bc1c370d
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002970"
---
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="d77bb-102">Instrukcje: wyświetlanie wygenerowanego kodu SQL</span><span class="sxs-lookup"><span data-stu-id="d77bb-102">How to: Display Generated SQL</span></span>
<span data-ttu-id="d77bb-103">Można wyświetlić kod SQL wygenerowany dla zapytań i przetwarzania zmian za pomocą właściwości <xref:System.Data.Linq.DataContext.Log%2A>.</span><span class="sxs-lookup"><span data-stu-id="d77bb-103">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="d77bb-104">Takie podejście może być przydatne w przypadku znajomości funkcjonalności [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] i debugowania określonych problemów.</span><span class="sxs-lookup"><span data-stu-id="d77bb-104">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d77bb-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d77bb-105">Example</span></span>  
 <span data-ttu-id="d77bb-106">Poniższy przykład używa właściwości <xref:System.Data.Linq.DataContext.Log%2A> do wyświetlania kodu SQL w oknie konsoli przed wykonaniem kodu.</span><span class="sxs-lookup"><span data-stu-id="d77bb-106">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="d77bb-107">Tej właściwości można użyć z poleceniami Query, INSERT, Update i DELETE.</span><span class="sxs-lookup"><span data-stu-id="d77bb-107">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="d77bb-108">Wiersze z okna konsoli są wyświetlane podczas wykonywania Visual Basic lub C# kodu poniżej.</span><span class="sxs-lookup"><span data-stu-id="d77bb-108">The lines from the console window are what you see when you execute the Visual Basic or C# code that follows.</span></span>  
  
```console  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```console  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d77bb-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d77bb-109">See also</span></span>

- [<span data-ttu-id="d77bb-110">Obsługa debugowania</span><span class="sxs-lookup"><span data-stu-id="d77bb-110">Debugging Support</span></span>](debugging-support.md)
