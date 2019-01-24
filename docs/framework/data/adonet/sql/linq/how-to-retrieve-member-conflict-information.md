---
title: 'Instrukcje: Pobieranie informacji o konflikcie elementu członkowskiego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 478781e6c8ee31ebf6f5edd0e243a81d9e0524f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669565"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="8310f-102">Instrukcje: Pobieranie informacji o konflikcie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="8310f-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="8310f-103">Możesz użyć <xref:System.Data.Linq.MemberChangeConflict> klasy do pobrania informacji o poszczególnych elementów członkowskich w konflikcie.</span><span class="sxs-lookup"><span data-stu-id="8310f-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="8310f-104">W tym samym kontekście możesz podać niestandardową obsługę konfliktu dla dowolnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="8310f-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="8310f-105">Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8310f-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8310f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="8310f-106">Example</span></span>  
 <span data-ttu-id="8310f-107">Poniższy kod wykonuje iterację przez <xref:System.Data.Linq.ObjectChangeConflict> obiektów.</span><span class="sxs-lookup"><span data-stu-id="8310f-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="8310f-108">Dla każdego obiektu, następnie iteruje <xref:System.Data.Linq.MemberChangeConflict> obiektów.</span><span class="sxs-lookup"><span data-stu-id="8310f-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8310f-109">Obejmują <xref:System.Reflection> zapewnić <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informacji.</span><span class="sxs-lookup"><span data-stu-id="8310f-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8310f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8310f-110">See also</span></span>
- [<span data-ttu-id="8310f-111">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="8310f-111">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
