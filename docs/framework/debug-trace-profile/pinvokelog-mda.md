---
title: pInvokeLog MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9c4842d838fd5b4fee29187f118c784c55e0eb13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="2aa27-102">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="2aa27-102">pInvokeLog MDA</span></span>
<span data-ttu-id="2aa27-103">`pInvokeLog` Zarządzany Asystent debugowania (MDA) została aktywowana dla każdej platformy unikatowy wywołania podpisu używane podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2aa27-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2aa27-104">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="2aa27-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="2aa27-105">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="2aa27-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2aa27-106">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="2aa27-106">Output</span></span>  
 <span data-ttu-id="2aa27-107">Komunikat informujący o platformie wywołania podpisu używane podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2aa27-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2aa27-108">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="2aa27-108">Configuration</span></span>  
 <span data-ttu-id="2aa27-109">Każdy filtry element dopasowania plików dll na poszczególnych platformach wywołania wywołania zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="2aa27-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2aa27-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2aa27-110">See Also</span></span>  
 [<span data-ttu-id="2aa27-111">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="2aa27-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="2aa27-112">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="2aa27-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
