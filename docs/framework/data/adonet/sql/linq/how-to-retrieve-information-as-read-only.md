---
title: 'Instrukcje: Pobieranie informacji jako tylko do odczytu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 131562e9ee0fbfde8c94f580bcb6d452918f42ee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148983"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="edb02-102">Instrukcje: Pobieranie informacji jako tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="edb02-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="edb02-103">Jeśli nie zamierzasz zmienić dane, możesz zwiększyć wydajność zapytań przez wyszukiwanie wyników tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="edb02-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="edb02-104">Implementowanie przetwarzania tylko do odczytu, ustawiając <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> do `false`.</span><span class="sxs-lookup"><span data-stu-id="edb02-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edb02-105">Gdy <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> ustawiono `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> niejawnie ustawiono `false`.</span><span class="sxs-lookup"><span data-stu-id="edb02-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edb02-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="edb02-106">Example</span></span>  
 <span data-ttu-id="edb02-107">Poniższy kod pobiera kolekcję tylko do odczytu dat zatrudnienia pracownika.</span><span class="sxs-lookup"><span data-stu-id="edb02-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="edb02-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edb02-108">See also</span></span>

- [<span data-ttu-id="edb02-109">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="edb02-109">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="edb02-110">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="edb02-110">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
- [<span data-ttu-id="edb02-111">Odroczone a bezpośrednie ładowanie</span><span class="sxs-lookup"><span data-stu-id="edb02-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
