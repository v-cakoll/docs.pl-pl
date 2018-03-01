---
title: "Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6e90de5a2fd0699a449e05b9c32e7450b8bdc991
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="43e6e-102">Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="43e6e-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="43e6e-103">Nie można uzyskać pełnej nazwy systemu operacyjnego z powodu błędu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="43e6e-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="43e6e-104">Może to być spowodowane WMI nie istniejący na bieżącym komputerze.</span><span class="sxs-lookup"><span data-stu-id="43e6e-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="43e6e-105">Wywołanie `My.Computer.Info.OSFullName` właściwości nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="43e6e-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="43e6e-106">Możliwą przyczyną tego błędu jest to, czy Instrumentacja zarządzania Windows (WMI) nie jest zainstalowany na bieżącym komputerze.</span><span class="sxs-lookup"><span data-stu-id="43e6e-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="43e6e-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="43e6e-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="43e6e-108">Dodaj `Try...Catch` bloku wokół wywołanie `My.Computer.Info.OSFullName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="43e6e-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="43e6e-109">Aby uzyskać więcej informacji na temat usługi WMI i sposobu instalacji, przejdź do i wyszukaj "Windows Management Instrumentation Core".</span><span class="sxs-lookup"><span data-stu-id="43e6e-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e6e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43e6e-110">See Also</span></span>  
 [<span data-ttu-id="43e6e-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="43e6e-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [<span data-ttu-id="43e6e-112">Wyjątek i obsługa błędów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43e6e-112">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="43e6e-113">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="43e6e-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
