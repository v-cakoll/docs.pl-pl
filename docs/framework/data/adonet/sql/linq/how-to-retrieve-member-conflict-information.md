---
title: 'Porady: pobieranie informacji konflikt elementu członkowskiego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 5d0788daac6c1be8dd7670c330d1efc36b074c2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="2a0af-102">Porady: pobieranie informacji konflikt elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="2a0af-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="2a0af-103">Można użyć <xref:System.Data.Linq.MemberChangeConflict> klasy można pobrać informacji o poszczególnych elementów w konflikt.</span><span class="sxs-lookup"><span data-stu-id="2a0af-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="2a0af-104">W tym samym kontekście można zapewnić niestandardową obsługę konfliktu dla dowolnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="2a0af-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="2a0af-105">Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2a0af-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a0af-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a0af-106">Example</span></span>  
 <span data-ttu-id="2a0af-107">Poniższy kod iteruje <xref:System.Data.Linq.ObjectChangeConflict> obiektów.</span><span class="sxs-lookup"><span data-stu-id="2a0af-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="2a0af-108">Dla każdego obiektu ją następnie iteruje <xref:System.Data.Linq.MemberChangeConflict> obiektów.</span><span class="sxs-lookup"><span data-stu-id="2a0af-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a0af-109">Obejmują <xref:System.Reflection> zapewnić <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informacji.</span><span class="sxs-lookup"><span data-stu-id="2a0af-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2a0af-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a0af-110">See Also</span></span>  
 [<span data-ttu-id="2a0af-111">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="2a0af-111">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
