---
title: Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: df7a91ea5763c0fe4b7a1993bec29f1b1bb43fcc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723298"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="70d0f-102">Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="70d0f-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="70d0f-103">Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="70d0f-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="70d0f-104">Może to być spowodowane przez usługę WMI nie istnieje na bieżącej maszynie.</span><span class="sxs-lookup"><span data-stu-id="70d0f-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="70d0f-105">Wywołanie `My.Computer.Info.OSFullName` właściwości nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="70d0f-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="70d0f-106">Możliwą przyczyną tego błędu jest, jeśli Instrumentacji zarządzania Windows (WMI) nie jest zainstalowany na bieżącym komputerze.</span><span class="sxs-lookup"><span data-stu-id="70d0f-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="70d0f-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="70d0f-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="70d0f-108">Dodaj `Try...Catch` bloku wokół wywołania `My.Computer.Info.OSFullName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="70d0f-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="70d0f-109">Aby uzyskać więcej informacji dotyczących usługi WMI i sposobach jego instalacji przejdź do i wyszukaj frazę "Podstawowy Instrumentacji zarządzania Windows".</span><span class="sxs-lookup"><span data-stu-id="70d0f-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70d0f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70d0f-110">See also</span></span>
- [<span data-ttu-id="70d0f-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="70d0f-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="70d0f-112">Wyjątek i obsługa błędów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70d0f-112">Exception and Error Handling in Visual Basic</span></span>](https://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)
- [<span data-ttu-id="70d0f-113">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="70d0f-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
