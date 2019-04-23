---
title: 'Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 606231449263f1c26596ca8606a88053c6aded8e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138128"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="7b1a4-102">Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań</span><span class="sxs-lookup"><span data-stu-id="7b1a4-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7b1a4-103">udostępnia wiele zasobów do wykrywania i rozwiązywania konfliktów, które wynikają z wieloma użytkownikami zmian w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="7b1a4-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="7b1a4-104">Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="7b1a4-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b1a4-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b1a4-105">Example</span></span>  
 <span data-ttu-id="7b1a4-106">W poniższym przykładzie przedstawiono `try` / `catch` blok, który przechwytuje <xref:System.Data.Linq.ChangeConflictException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7b1a4-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="7b1a4-107">Informacje o wszystkich konfliktów jednostki i elementu członkowskiego jest wyświetlany w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7b1a4-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b1a4-108">Musi zawierać `using System.Reflection` — dyrektywa (`Imports System.Reflection` w języku Visual Basic) do obsługi pobierania informacji.</span><span class="sxs-lookup"><span data-stu-id="7b1a4-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="7b1a4-109">Aby uzyskać więcej informacji, zobacz <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="7b1a4-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7b1a4-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b1a4-110">See also</span></span>

- [<span data-ttu-id="7b1a4-111">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="7b1a4-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="7b1a4-112">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="7b1a4-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
