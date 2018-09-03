---
title: Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 192033348a779591a54860505d5d707a802c415a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464963"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="486ef-102">Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="486ef-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="486ef-103">Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="486ef-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="486ef-104">Może to być spowodowane przez usługę WMI nie istnieje na bieżącej maszynie.</span><span class="sxs-lookup"><span data-stu-id="486ef-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="486ef-105">Wywołanie `My.Computer.Info.OSFullName` właściwości nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="486ef-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="486ef-106">Możliwą przyczyną tego błędu jest, jeśli Instrumentacji zarządzania Windows (WMI) nie jest zainstalowany na bieżącym komputerze.</span><span class="sxs-lookup"><span data-stu-id="486ef-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="486ef-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="486ef-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="486ef-108">Dodaj `Try...Catch` bloku wokół wywołania `My.Computer.Info.OSFullName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="486ef-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="486ef-109">Aby uzyskać więcej informacji dotyczących usługi WMI i sposobach jego instalacji przejdź do i wyszukaj frazę "Podstawowy Instrumentacji zarządzania Windows".</span><span class="sxs-lookup"><span data-stu-id="486ef-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="486ef-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="486ef-110">See Also</span></span>  
 [<span data-ttu-id="486ef-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="486ef-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [<span data-ttu-id="486ef-112">Wyjątek i obsługa błędów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="486ef-112">Exception and Error Handling in Visual Basic</span></span>](https://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="486ef-113">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="486ef-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
