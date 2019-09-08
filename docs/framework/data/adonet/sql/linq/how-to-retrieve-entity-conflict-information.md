---
title: 'Instrukcje: Pobieranie informacji o konflikcie jednostki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: 766ede90b14f07e2799c2715daf62aaeeeaa83f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782239"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="98c21-102">Instrukcje: Pobieranie informacji o konflikcie jednostki</span><span class="sxs-lookup"><span data-stu-id="98c21-102">How to: Retrieve Entity Conflict Information</span></span>
<span data-ttu-id="98c21-103">Możesz użyć obiektów klasy, <xref:System.Data.Linq.ObjectChangeConflict> aby podać informacje o konfliktach ujawnionych przez <xref:System.Data.Linq.ChangeConflictException> wyjątki.</span><span class="sxs-lookup"><span data-stu-id="98c21-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="98c21-104">Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="98c21-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98c21-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="98c21-105">Example</span></span>  
 <span data-ttu-id="98c21-106">Poniższy przykład wykonuje iterację przez listę skumulowanych konfliktów.</span><span class="sxs-lookup"><span data-stu-id="98c21-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="98c21-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98c21-107">See also</span></span>

- [<span data-ttu-id="98c21-108">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="98c21-108">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
