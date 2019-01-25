---
title: 'Instrukcje: Pobieranie informacji jako tylko do odczytu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 8b83a77adb02cc2bcc01b274867143887114bb1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669552"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="20f28-102">Instrukcje: Pobieranie informacji jako tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="20f28-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="20f28-103">Jeśli nie zamierzasz zmienić dane, możesz zwiększyć wydajność zapytań przez wyszukiwanie wyników tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="20f28-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="20f28-104">Implementowanie przetwarzania tylko do odczytu, ustawiając <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> do `false`.</span><span class="sxs-lookup"><span data-stu-id="20f28-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20f28-105">Gdy <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> ustawiono `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> niejawnie ustawiono `false`.</span><span class="sxs-lookup"><span data-stu-id="20f28-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20f28-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="20f28-106">Example</span></span>  
 <span data-ttu-id="20f28-107">Poniższy kod pobiera kolekcję tylko do odczytu dat zatrudnienia pracownika.</span><span class="sxs-lookup"><span data-stu-id="20f28-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="20f28-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20f28-108">See also</span></span>
- [<span data-ttu-id="20f28-109">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="20f28-109">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="20f28-110">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="20f28-110">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
- [<span data-ttu-id="20f28-111">Odroczone a bezpośrednie ładowanie</span><span class="sxs-lookup"><span data-stu-id="20f28-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
