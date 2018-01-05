---
title: "Porady: wykrywanie i rozwiązać powodujące konflikt przesłanych"
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
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 28dba94262002f863a750a83493ba98b3714fabd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="09aac-102">Porady: wykrywanie i rozwiązać powodujące konflikt przesłanych</span><span class="sxs-lookup"><span data-stu-id="09aac-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="09aac-103">udostępnia wiele zasobów wykrywania i rozwiązywania konfliktów, które wynikają z wielu użytkowników zmian w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="09aac-103"> provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="09aac-104">Aby uzyskać więcej informacji, zobacz [porady: Zarządzanie konfliktów zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="09aac-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09aac-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="09aac-105">Example</span></span>  
 <span data-ttu-id="09aac-106">W poniższym przykładzie przedstawiono `try` / `catch` bloku, który przechwytuje <xref:System.Data.Linq.ChangeConflictException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="09aac-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="09aac-107">Informacje o wszystkich konfliktów jednostki i element członkowski jest wyświetlany w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="09aac-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09aac-108">Należy uwzględnić `using System.Reflection` — dyrektywa (`Imports System.Reflection` w języku Visual Basic) do obsługi pobierania informacji.</span><span class="sxs-lookup"><span data-stu-id="09aac-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="09aac-109">Aby uzyskać więcej informacji, zobacz <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="09aac-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="09aac-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09aac-110">See Also</span></span>  
 [<span data-ttu-id="09aac-111">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="09aac-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="09aac-112">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="09aac-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
