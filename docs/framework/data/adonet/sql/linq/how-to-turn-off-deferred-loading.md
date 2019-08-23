---
title: 'Instrukcje: Wyłączanie odroczonego ładowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f68db5a5a0092fc4cf37746f2a4dc81e40ee4a9d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938676"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="22434-102">Instrukcje: Wyłączanie odroczonego ładowania</span><span class="sxs-lookup"><span data-stu-id="22434-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="22434-103">Można wyłączyć odroczone ładowanie według ustawienia <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do. `false`</span><span class="sxs-lookup"><span data-stu-id="22434-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="22434-104">Aby uzyskać więcej informacji, zobacz odroczone względem [natychmiastowego ładowania](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="22434-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22434-105">Ładowanie odroczone jest wyłączone przez implikację, gdy śledzenie obiektów jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="22434-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="22434-106">Aby uzyskać więcej informacji, zobacz [jak: Pobierz informacje jako tylko](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)do odczytu.</span><span class="sxs-lookup"><span data-stu-id="22434-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22434-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="22434-107">Example</span></span>  
 <span data-ttu-id="22434-108">Poniższy przykład pokazuje, jak wyłączyć odroczone ładowanie przez ustawienie <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do. `false`</span><span class="sxs-lookup"><span data-stu-id="22434-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="22434-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22434-109">See also</span></span>

- [<span data-ttu-id="22434-110">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="22434-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="22434-111">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="22434-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
