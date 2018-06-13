---
title: pInvokeLog MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 830a65a4490b1d084e3bb301e89293ccb9424b32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387006"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="2f6da-102">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="2f6da-102">pInvokeLog MDA</span></span>
<span data-ttu-id="2f6da-103">`pInvokeLog` Zarządzany Asystent debugowania (MDA) została aktywowana dla każdej platformy unikatowy wywołania podpisu używane podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2f6da-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2f6da-104">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="2f6da-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="2f6da-105">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="2f6da-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2f6da-106">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="2f6da-106">Output</span></span>  
 <span data-ttu-id="2f6da-107">Komunikat informujący o platformie wywołania podpisu używane podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2f6da-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2f6da-108">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="2f6da-108">Configuration</span></span>  
 <span data-ttu-id="2f6da-109">Każdy filtry element dopasowania plików dll na poszczególnych platformach wywołania wywołania zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="2f6da-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f6da-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f6da-110">See Also</span></span>  
 [<span data-ttu-id="2f6da-111">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="2f6da-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="2f6da-112">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="2f6da-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
