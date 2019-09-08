---
title: 'Instrukcje: Wyłączanie odroczonego ładowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 6559392527bb02afe9cea61e704f1f371c6d5470
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781658"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="e9d14-102">Instrukcje: Wyłączanie odroczonego ładowania</span><span class="sxs-lookup"><span data-stu-id="e9d14-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="e9d14-103">Można wyłączyć odroczone ładowanie według ustawienia <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do. `false`</span><span class="sxs-lookup"><span data-stu-id="e9d14-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="e9d14-104">Aby uzyskać więcej informacji, zobacz [odroczone względem natychmiastowego ładowania](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="e9d14-104">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9d14-105">Ładowanie odroczone jest wyłączone przez implikację, gdy śledzenie obiektów jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e9d14-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="e9d14-106">Aby uzyskać więcej informacji, zobacz [jak: Pobierz informacje jako tylko](how-to-retrieve-information-as-read-only.md)do odczytu.</span><span class="sxs-lookup"><span data-stu-id="e9d14-106">For more information, see [How to: Retrieve Information As Read-Only](how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9d14-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9d14-107">Example</span></span>  
 <span data-ttu-id="e9d14-108">Poniższy przykład pokazuje, jak wyłączyć odroczone ładowanie przez ustawienie <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do. `false`</span><span class="sxs-lookup"><span data-stu-id="e9d14-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e9d14-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9d14-109">See also</span></span>

- [<span data-ttu-id="e9d14-110">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="e9d14-110">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="e9d14-111">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="e9d14-111">Querying the Database</span></span>](querying-the-database.md)
