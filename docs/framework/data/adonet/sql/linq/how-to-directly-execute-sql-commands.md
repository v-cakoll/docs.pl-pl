---
title: 'Instrukcje: Bezpośrednie wykonywanie poleceń SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: eeac6272f176ac8e780b72b0076d032ad9e8f108
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078905"
---
# <a name="how-to-directly-execute-sql-commands"></a><span data-ttu-id="3657d-102">Instrukcje: Bezpośrednie wykonywanie poleceń SQL</span><span class="sxs-lookup"><span data-stu-id="3657d-102">How to: Directly Execute SQL Commands</span></span>
<span data-ttu-id="3657d-103">Zakładając, że <xref:System.Data.Linq.DataContext> połączenia, można użyć <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> do wykonywania poleceń SQL, które nie zwracają obiekty.</span><span class="sxs-lookup"><span data-stu-id="3657d-103">Assuming a <xref:System.Data.Linq.DataContext> connection, you can use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to execute SQL commands that do not return objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3657d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3657d-104">Example</span></span>  
 <span data-ttu-id="3657d-105">Poniższy przykład powoduje programu SQL Server w celu zwiększenia UnitPrice 1,00.</span><span class="sxs-lookup"><span data-stu-id="3657d-105">The following example causes SQL Server to increase UnitPrice by 1.00.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3657d-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3657d-106">See also</span></span>

- [<span data-ttu-id="3657d-107">Instrukcje: Bezpośrednie wykonywanie zapytań SQL</span><span class="sxs-lookup"><span data-stu-id="3657d-107">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)
- [<span data-ttu-id="3657d-108">Komunikacja z bazą danych</span><span class="sxs-lookup"><span data-stu-id="3657d-108">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
