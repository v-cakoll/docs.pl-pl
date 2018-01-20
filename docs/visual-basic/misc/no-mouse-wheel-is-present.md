---
title: "Nie ma kółka myszy obecne"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrMouse_NoWheelIsPresent
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7caf2e24bcbd86ad2b6175d593bd218a9bb4689d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="no-mouse-wheel-is-present"></a><span data-ttu-id="a1dff-102">Nie ma kółka myszy obecne</span><span class="sxs-lookup"><span data-stu-id="a1dff-102">No mouse wheel is present</span></span>
<span data-ttu-id="a1dff-103">`My.Computer.Mouse.WheelScrollLines` Właściwość została wywołana, ale nie kółko przewijania myszy ma myszy.</span><span class="sxs-lookup"><span data-stu-id="a1dff-103">The `My.Computer.Mouse.WheelScrollLines` property was called, but the mouse has no scroll wheel.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a1dff-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a1dff-104">To correct this error</span></span>  
  
-   <span data-ttu-id="a1dff-105">Sprawdź `My.Computer.Mouse.WheelExists` właściwość, aby sprawdzić, czy wskaźnik myszy ma kółka przewijania przed wywołaniem `My.Computer.Mouse.WheelScrollLines` właściwości.</span><span class="sxs-lookup"><span data-stu-id="a1dff-105">Check the `My.Computer.Mouse.WheelExists` property to see if the mouse has a scroll wheel before calling the `My.Computer.Mouse.WheelScrollLines` property.</span></span>  
  
     <span data-ttu-id="a1dff-106">—lub—</span><span class="sxs-lookup"><span data-stu-id="a1dff-106">-or-</span></span>  
  
-   <span data-ttu-id="a1dff-107">Zainstaluj myszy w kółko przewijania na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a1dff-107">Install a mouse with a scroll wheel on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1dff-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1dff-108">See Also</span></span>  
 [<span data-ttu-id="a1dff-109">My.Computer.Mouse.WheelScrollLines</span><span class="sxs-lookup"><span data-stu-id="a1dff-109">My.Computer.Mouse.WheelScrollLines</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelScrollLines)  
 [<span data-ttu-id="a1dff-110">My.Computer.Mouse.WheelExists</span><span class="sxs-lookup"><span data-stu-id="a1dff-110">My.Computer.Mouse.WheelExists</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelExists)  
 [<span data-ttu-id="a1dff-111">Wyjątek i obsługa błędów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1dff-111">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)
