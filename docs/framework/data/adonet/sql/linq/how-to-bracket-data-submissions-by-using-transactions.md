---
title: "Porady: nawiasów przesyłania danych za pomocą transakcji"
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
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 071c0c8bc7e0bb8dca01e9fc51c66fb930ed102b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="cbf10-102">Porady: nawiasów przesyłania danych za pomocą transakcji</span><span class="sxs-lookup"><span data-stu-id="cbf10-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="cbf10-103">Można użyć <xref:System.Transactions.TransactionScope> do nawiasów przesyłanych danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="cbf10-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="cbf10-104">Aby uzyskać więcej informacji, zobacz [Obsługa transakcji](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="cbf10-104">For more information, see [Transaction Support](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbf10-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbf10-105">Example</span></span>  
 <span data-ttu-id="cbf10-106">Poniższy kod umieszcza przesyłanie bazy danych w <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="cbf10-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="cbf10-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbf10-107">See Also</span></span>  
 [<span data-ttu-id="cbf10-108">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="cbf10-108">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="cbf10-109">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="cbf10-109">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="cbf10-110">Obsługa transakcji</span><span class="sxs-lookup"><span data-stu-id="cbf10-110">Transaction Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
