---
title: 'Instrukcje: Pobieranie informacji o konflikcie elementu członkowskiego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 9d63b0b2c7d513d9f4db526b88a7c4e852637343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928632"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="e1a74-102">Instrukcje: Pobieranie informacji o konflikcie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="e1a74-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="e1a74-103">Za pomocą <xref:System.Data.Linq.MemberChangeConflict> klasy można pobrać informacje o konflikcie poszczególnych członków.</span><span class="sxs-lookup"><span data-stu-id="e1a74-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="e1a74-104">W tym samym kontekście można zapewnić niestandardową obsługę konfliktu dla każdego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e1a74-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="e1a74-105">Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e1a74-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1a74-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a74-106">Example</span></span>  
 <span data-ttu-id="e1a74-107">Poniższy kod wykonuje iterację <xref:System.Data.Linq.ObjectChangeConflict> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e1a74-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="e1a74-108">Dla każdego obiektu, następnie iteruje za pomocą <xref:System.Data.Linq.MemberChangeConflict> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e1a74-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1a74-109">Uwzględnij <xref:System.Reflection> , aby podać <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informacje.</span><span class="sxs-lookup"><span data-stu-id="e1a74-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e1a74-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1a74-110">See also</span></span>

- [<span data-ttu-id="e1a74-111">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="e1a74-111">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
