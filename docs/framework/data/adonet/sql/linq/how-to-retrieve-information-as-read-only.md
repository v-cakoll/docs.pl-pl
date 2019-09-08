---
title: 'Instrukcje: Pobieranie informacji jako tylko do odczytu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 399bf44ef5536a9adebf1cad590439741df998f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793318"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="541c5-102">Instrukcje: Pobieranie informacji jako tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="541c5-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="541c5-103">Jeśli nie zamierzasz zmieniać danych, możesz zwiększyć wydajność zapytań, wyszukując wyniki tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="541c5-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="541c5-104">Przetwarzanie w trybie tylko do odczytu jest implementowane `false`przez ustawienie <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> do.</span><span class="sxs-lookup"><span data-stu-id="541c5-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="541c5-105">Gdy <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> jest ustawiona na `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> jest niejawnie ustawiona `false`na.</span><span class="sxs-lookup"><span data-stu-id="541c5-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="541c5-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="541c5-106">Example</span></span>  
 <span data-ttu-id="541c5-107">Poniższy kod pobiera kolekcję dat zatrudnienia pracowników w trybie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="541c5-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="541c5-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="541c5-108">See also</span></span>

- [<span data-ttu-id="541c5-109">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="541c5-109">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="541c5-110">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="541c5-110">Querying the Database</span></span>](querying-the-database.md)
- [<span data-ttu-id="541c5-111">Odroczone a bezpośrednie ładowanie</span><span class="sxs-lookup"><span data-stu-id="541c5-111">Deferred versus Immediate Loading</span></span>](deferred-versus-immediate-loading.md)
