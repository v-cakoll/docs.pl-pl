---
title: "Porady: pobieranie informacji konflikt elementu członkowskiego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a6766e40b842675cbe37ba1ebeb1a956c19e6318
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="fd32f-102">Porady: pobieranie informacji konflikt elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="fd32f-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="fd32f-103">Można użyć <xref:System.Data.Linq.MemberChangeConflict> klasy można pobrać informacji o poszczególnych elementów w konflikt.</span><span class="sxs-lookup"><span data-stu-id="fd32f-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="fd32f-104">W tym samym kontekście można zapewnić niestandardową obsługę konfliktu dla dowolnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="fd32f-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="fd32f-105">Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fd32f-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd32f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd32f-106">Example</span></span>  
 <span data-ttu-id="fd32f-107">Poniższy kod iteruje <xref:System.Data.Linq.ObjectChangeConflict> obiektów.</span><span class="sxs-lookup"><span data-stu-id="fd32f-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="fd32f-108">Dla każdego obiektu ją następnie iteruje <xref:System.Data.Linq.MemberChangeConflict> obiektów.</span><span class="sxs-lookup"><span data-stu-id="fd32f-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd32f-109">Obejmują <xref:System.Reflection> zapewnić <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informacji.</span><span class="sxs-lookup"><span data-stu-id="fd32f-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fd32f-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd32f-110">See Also</span></span>  
 [<span data-ttu-id="fd32f-111">Porady: Zarządzanie konfliktów zmian</span><span class="sxs-lookup"><span data-stu-id="fd32f-111">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
