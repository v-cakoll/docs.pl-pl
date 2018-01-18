---
title: LINQ do SQL N-warstwowa ASP.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9b71113ca76eec5888aed2123ec9c55ad66a72bf
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a><span data-ttu-id="9359e-102">LINQ do SQL N-warstwowa ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9359e-102">LINQ to SQL N-Tier with ASP.NET</span></span>
<span data-ttu-id="9359e-103">W [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] aplikacji, które używają [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], możesz użyć <xref:System.Web.UI.WebControls.LinqDataSource> formant serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9359e-103">In [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the <xref:System.Web.UI.WebControls.LinqDataSource> Web server control.</span></span> <span data-ttu-id="9359e-104">Formant obsługuje większość logikę, która musi mieć w zapytaniu dotyczącym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], przekazać dane do przeglądarki, pobrać go i przesłać je do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> który następnie aktualizuje bazę danych.</span><span class="sxs-lookup"><span data-stu-id="9359e-104">The control handles most of the logic that it must have to query against [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pass the data to the browser, retrieve it, and submit it to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> which then updates the database.</span></span> <span data-ttu-id="9359e-105">Wystarczy skonfigurować formantu w znaczniku i kontrolka obsługuje wszystkie transferu danych między [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] i przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="9359e-105">You just configure the control in the markup, and the control handles all the data transfer between [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] and the browser.</span></span> <span data-ttu-id="9359e-106">Ponieważ formant obsługuje interakcji z warstwą prezentacji a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje komunikację z warstwą danych, a zespół główny w [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] wielowarstwowej aplikacji znajduje się na pisanie niestandardowej logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="9359e-106">Because the control handles the interactions with the presentation tier, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles the communication with the data tier, your main focus in [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] multitier applications is on writing your custom business logic.</span></span>  
  
 <span data-ttu-id="9359e-107">Aby uzyskać więcej informacji na temat `LINQDataSource`, zobacz [NIB: omówienie kontrolki serwera sieci Web LinqDataSource](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span><span class="sxs-lookup"><span data-stu-id="9359e-107">For more information about `LINQDataSource`, see [NIB: LinqDataSource Web Server Control Overview](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9359e-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9359e-108">See Also</span></span>  
 [<span data-ttu-id="9359e-109">N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9359e-109">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
