---
title: 'Porady: wyłączanie odroczonego ładowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 279317f10211271fad812068215b08a93e30fbdf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="6b841-102">Porady: wyłączanie odroczonego ładowania</span><span class="sxs-lookup"><span data-stu-id="6b841-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="6b841-103">Można wyłączyć odroczonego ładowania ustawiając <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do `false`.</span><span class="sxs-lookup"><span data-stu-id="6b841-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="6b841-104">Aby uzyskać więcej informacji, zobacz [odroczone i ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="6b841-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b841-105">Ładowanie odłożone jest wyłączone co za tym idzie, gdy obiekt śledzenie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="6b841-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="6b841-106">Aby uzyskać więcej informacji, zobacz [porady: pobieranie informacji jako tylko do odczytu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="6b841-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b841-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b841-107">Example</span></span>  
 <span data-ttu-id="6b841-108">Poniższy przykład pokazuje, jak wyłączyć odroczonego ładowania ustawiając <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do `false`.</span><span class="sxs-lookup"><span data-stu-id="6b841-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6b841-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b841-109">See Also</span></span>  
 [<span data-ttu-id="6b841-110">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="6b841-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="6b841-111">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="6b841-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
