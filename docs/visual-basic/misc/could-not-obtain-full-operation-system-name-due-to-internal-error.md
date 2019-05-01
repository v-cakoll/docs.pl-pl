---
title: Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: ecbed5b59d36b1984c0b0ae161821ea99d28e090
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970589"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="ea675-102">Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="ea675-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="ea675-103">Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="ea675-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="ea675-104">Może to być spowodowane przez usługę WMI nie istnieje na bieżącej maszynie.</span><span class="sxs-lookup"><span data-stu-id="ea675-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="ea675-105">Wywołanie `My.Computer.Info.OSFullName` właściwości nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="ea675-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="ea675-106">Możliwą przyczyną tego błędu jest, jeśli Instrumentacji zarządzania Windows (WMI) nie jest zainstalowany na bieżącym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ea675-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ea675-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="ea675-107">To correct this error</span></span>  
  
1. <span data-ttu-id="ea675-108">Dodaj `Try...Catch` bloku wokół wywołania `My.Computer.Info.OSFullName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="ea675-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2. <span data-ttu-id="ea675-109">Aby uzyskać więcej informacji dotyczących usługi WMI i sposobach jego instalacji przejdź do i wyszukaj frazę "Podstawowy Instrumentacji zarządzania Windows".</span><span class="sxs-lookup"><span data-stu-id="ea675-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea675-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea675-110">See also</span></span>

- [<span data-ttu-id="ea675-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="ea675-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="ea675-112">Obsługa i zgłaszanie wyjątków na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="ea675-112">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="ea675-113">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ea675-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
