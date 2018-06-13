---
title: 'Porady: pobieranie informacji konflikt jednostki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: cabfae568396fa34e6090027032f310cdc05c507
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353198"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="bd281-102">Porady: pobieranie informacji konflikt jednostki</span><span class="sxs-lookup"><span data-stu-id="bd281-102">How to: Retrieve Entity Conflict Information</span></span>
<span data-ttu-id="bd281-103">Można użyć obiektów <xref:System.Data.Linq.ObjectChangeConflict> klasę, aby podać informacje o konfliktach ujawniony przez <xref:System.Data.Linq.ChangeConflictException> wyjątków.</span><span class="sxs-lookup"><span data-stu-id="bd281-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="bd281-104">Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bd281-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd281-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd281-105">Example</span></span>  
 <span data-ttu-id="bd281-106">Poniższy przykład iterację listę wszystkich konfliktów.</span><span class="sxs-lookup"><span data-stu-id="bd281-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bd281-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd281-107">See Also</span></span>  
 [<span data-ttu-id="bd281-108">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="bd281-108">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
