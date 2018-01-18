---
title: "Porady: filtrowanie danych powiązanych"
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
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 27c09badda5675158ca5c50481472db142eca32e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="1f8d4-102">Porady: filtrowanie danych powiązanych</span><span class="sxs-lookup"><span data-stu-id="1f8d4-102">How to: Filter Related Data</span></span>
<span data-ttu-id="1f8d4-103">Użyj <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> metodę, aby określić podzapytaniach, aby ograniczyć ilość pobrać danych.</span><span class="sxs-lookup"><span data-stu-id="1f8d4-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f8d4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f8d4-104">Example</span></span>  
 <span data-ttu-id="1f8d4-105">W poniższym przykładzie <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> limity metody `Orders` pobrane do tych, które nie zostały wysłane dzisiaj.</span><span class="sxs-lookup"><span data-stu-id="1f8d4-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="1f8d4-106">Bez tej metody wszystkie `Orders` czy pobrać, nawet jeśli wymagane jest tylko ich podzbiór.</span><span class="sxs-lookup"><span data-stu-id="1f8d4-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1f8d4-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f8d4-107">See Also</span></span>  
 [<span data-ttu-id="1f8d4-108">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="1f8d4-108">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
