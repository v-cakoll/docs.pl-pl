---
title: 'Instrukcje: Przesyłanie danych nawiasów za pomocą transakcji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 6a4c5ba7c4938b48fe489e43ff4a3ff806bd8916
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793807"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="e7f43-102">Instrukcje: Przesyłanie danych nawiasów za pomocą transakcji</span><span class="sxs-lookup"><span data-stu-id="e7f43-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="e7f43-103">Możesz użyć <xref:System.Transactions.TransactionScope> , aby przenawiasować przesłanie do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e7f43-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="e7f43-104">Aby uzyskać więcej informacji, zobacz [Obsługa transakcji](transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="e7f43-104">For more information, see [Transaction Support](transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7f43-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7f43-105">Example</span></span>  
 <span data-ttu-id="e7f43-106">Poniższy kod obejmuje przesyłanie bazy danych w <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="e7f43-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e7f43-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7f43-107">See also</span></span>

- [<span data-ttu-id="e7f43-108">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="e7f43-108">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="e7f43-109">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="e7f43-109">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="e7f43-110">Obsługa transakcji</span><span class="sxs-lookup"><span data-stu-id="e7f43-110">Transaction Support</span></span>](transaction-support.md)
