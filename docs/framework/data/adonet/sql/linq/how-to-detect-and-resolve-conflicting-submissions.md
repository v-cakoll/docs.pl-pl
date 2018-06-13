---
title: 'Porady: wykrywanie i rozwiązać powodujące konflikt przesłanych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: dfe1fac4285b915c316fb70d1e3bd1e7b99f145a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354397"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="6910f-102">Porady: wykrywanie i rozwiązać powodujące konflikt przesłanych</span><span class="sxs-lookup"><span data-stu-id="6910f-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6910f-103"> udostępnia wiele zasobów wykrywania i rozwiązywania konfliktów, które wynikają z wielu użytkowników zmian w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="6910f-103"> provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="6910f-104">Aby uzyskać więcej informacji, zobacz [porady: Zarządzanie konfliktów zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="6910f-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6910f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6910f-105">Example</span></span>  
 <span data-ttu-id="6910f-106">W poniższym przykładzie przedstawiono `try` / `catch` bloku, który przechwytuje <xref:System.Data.Linq.ChangeConflictException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6910f-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="6910f-107">Informacje o wszystkich konfliktów jednostki i element członkowski jest wyświetlany w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="6910f-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6910f-108">Należy uwzględnić `using System.Reflection` — dyrektywa (`Imports System.Reflection` w języku Visual Basic) do obsługi pobierania informacji.</span><span class="sxs-lookup"><span data-stu-id="6910f-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="6910f-109">Aby uzyskać więcej informacji, zobacz <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="6910f-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6910f-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6910f-110">See Also</span></span>  
 [<span data-ttu-id="6910f-111">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="6910f-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="6910f-112">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="6910f-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
