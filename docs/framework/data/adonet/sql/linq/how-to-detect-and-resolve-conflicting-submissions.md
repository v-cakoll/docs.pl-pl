---
title: 'Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: ff33196f83e2c0d8d759e4ffc3fb7442e8ba0e3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940096"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="8151d-102">Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań</span><span class="sxs-lookup"><span data-stu-id="8151d-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8151d-103">oferuje wiele zasobów do wykrywania i rozwiązywania konfliktów, które pochodzą od zmian wielu użytkowników w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="8151d-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="8151d-104">Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie konfliktami](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)zmian.</span><span class="sxs-lookup"><span data-stu-id="8151d-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8151d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="8151d-105">Example</span></span>  
 <span data-ttu-id="8151d-106">Poniższy `try` przykład pokazuje / <xref:System.Data.Linq.ChangeConflictException> blok, który przechwytuje wyjątek. `catch`</span><span class="sxs-lookup"><span data-stu-id="8151d-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="8151d-107">Informacje o jednostkach i elementach członkowskich dla każdego konfliktu są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="8151d-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8151d-108">Musisz dołączyć `using System.Reflection` dyrektywę (`Imports System.Reflection` w Visual Basic) do obsługi pobierania informacji.</span><span class="sxs-lookup"><span data-stu-id="8151d-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="8151d-109">Aby uzyskać więcej informacji, zobacz <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="8151d-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8151d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8151d-110">See also</span></span>

- [<span data-ttu-id="8151d-111">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="8151d-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="8151d-112">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="8151d-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
