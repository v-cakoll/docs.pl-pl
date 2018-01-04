---
title: "Porady: wyświetlanie grupy zmian"
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
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7dd730e2337cdd735530107abaedd13b726e5cfc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-a-changeset"></a><span data-ttu-id="5aaaf-102">Porady: wyświetlanie grupy zmian</span><span class="sxs-lookup"><span data-stu-id="5aaaf-102">How to: Display a ChangeSet</span></span>
<span data-ttu-id="5aaaf-103">Zmiany śledzone przez można wyświetlić <xref:System.Data.Linq.DataContext> przy użyciu <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span><span class="sxs-lookup"><span data-stu-id="5aaaf-103">You can view changes tracked by a <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aaaf-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5aaaf-104">Example</span></span>  
 <span data-ttu-id="5aaaf-105">Poniższy przykład pobiera klientów, których Miasto jest Londynie, zmiany miasta Paryża i przesyła się, że zmian z powrotem do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="5aaaf-105">The following example retrieves customers whose city is London, changes the city to Paris, and submits the changes back to the database.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 <span data-ttu-id="5aaaf-106">Zostaną wyświetlone dane wyjściowe z tego kodu z podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="5aaaf-106">Output from this code appears similar to the following.</span></span> <span data-ttu-id="5aaaf-107">Należy pamiętać, że podsumowanie na końcu pokazuje, że osiem zmiany zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="5aaaf-107">Note that the summary at the end shows that eight changes were made.</span></span>  
  
 `CustomerID: AROUT`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: BSBEV`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: CONSH`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: EASTC`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: NORTS`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: PARIS`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: SEVES`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: SPECD`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 ``  
  
 `Total changes: {Added: 0, Removed: 0, Modified: 8}`  
  
## <a name="see-also"></a><span data-ttu-id="5aaaf-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5aaaf-108">See Also</span></span>  
 [<span data-ttu-id="5aaaf-109">Obsługa debugowania</span><span class="sxs-lookup"><span data-stu-id="5aaaf-109">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
