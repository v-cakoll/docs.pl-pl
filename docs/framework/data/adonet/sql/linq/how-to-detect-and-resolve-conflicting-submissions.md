---
title: 'Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 2de0182cc0b87768a9cff553b7ec6e77f8ccc7b8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793777"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="6a7cf-102">Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań</span><span class="sxs-lookup"><span data-stu-id="6a7cf-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6a7cf-103">oferuje wiele zasobów do wykrywania i rozwiązywania konfliktów, które pochodzą od zmian wielu użytkowników w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="6a7cf-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="6a7cf-104">Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie konfliktami](how-to-manage-change-conflicts.md)zmian.</span><span class="sxs-lookup"><span data-stu-id="6a7cf-104">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a7cf-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6a7cf-105">Example</span></span>  
 <span data-ttu-id="6a7cf-106">Poniższy `try` przykład pokazuje / <xref:System.Data.Linq.ChangeConflictException> blok, który przechwytuje wyjątek. `catch`</span><span class="sxs-lookup"><span data-stu-id="6a7cf-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="6a7cf-107">Informacje o jednostkach i elementach członkowskich dla każdego konfliktu są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="6a7cf-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a7cf-108">Musisz dołączyć `using System.Reflection` dyrektywę (`Imports System.Reflection` w Visual Basic) do obsługi pobierania informacji.</span><span class="sxs-lookup"><span data-stu-id="6a7cf-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="6a7cf-109">Aby uzyskać więcej informacji, zobacz <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="6a7cf-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6a7cf-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a7cf-110">See also</span></span>

- [<span data-ttu-id="6a7cf-111">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="6a7cf-111">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="6a7cf-112">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="6a7cf-112">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
