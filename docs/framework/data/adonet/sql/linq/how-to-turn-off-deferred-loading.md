---
title: 'Instrukcje: Wyłączanie odroczonego ładowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 9878ec468333ba79d0171d0bf96235d48273e03e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669539"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="fb15c-102">Instrukcje: Wyłączanie odroczonego ładowania</span><span class="sxs-lookup"><span data-stu-id="fb15c-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="fb15c-103">Można wyłączyć odroczonego ładowania, ustawiając <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do `false`.</span><span class="sxs-lookup"><span data-stu-id="fb15c-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="fb15c-104">Aby uzyskać więcej informacji, zobacz [odroczone a ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="fb15c-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb15c-105">Odroczonego ładowania jest wyłączona przez domniemanie, gdy obiekt śledzenie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="fb15c-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="fb15c-106">Aby uzyskać więcej informacji, zobacz [jak: Pobieranie informacji jako tylko do odczytu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="fb15c-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb15c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb15c-107">Example</span></span>  
 <span data-ttu-id="fb15c-108">Poniższy przykład pokazuje, jak wyłączanie odroczonego ładowania, ustawiając <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do `false`.</span><span class="sxs-lookup"><span data-stu-id="fb15c-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="fb15c-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb15c-109">See also</span></span>
- [<span data-ttu-id="fb15c-110">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="fb15c-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="fb15c-111">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="fb15c-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
