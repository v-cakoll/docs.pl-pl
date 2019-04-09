---
title: 'Instrukcje: Przesyłanie danych nawiasów za pomocą transakcji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 3e58c6f2849ed9714b3356662dae313ab9d11696
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134007"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="a480e-102">Instrukcje: Przesyłanie danych nawiasów za pomocą transakcji</span><span class="sxs-lookup"><span data-stu-id="a480e-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="a480e-103">Możesz użyć <xref:System.Transactions.TransactionScope> do dopasowywanie materiałów przesłanych do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a480e-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="a480e-104">Aby uzyskać więcej informacji, zobacz [Obsługa transakcji](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="a480e-104">For more information, see [Transaction Support](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a480e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a480e-105">Example</span></span>  
 <span data-ttu-id="a480e-106">Poniższy kod zawiera przesyłania bazy danych w <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="a480e-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a480e-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a480e-107">See also</span></span>

- [<span data-ttu-id="a480e-108">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="a480e-108">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="a480e-109">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="a480e-109">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="a480e-110">Obsługa transakcji</span><span class="sxs-lookup"><span data-stu-id="a480e-110">Transaction Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
