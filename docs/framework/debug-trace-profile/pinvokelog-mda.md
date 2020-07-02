---
title: pInvokeLog MDA
description: Informacje o programie pInvokeLog Managed Debug Assistant (MDA), który jest uaktywniany dla każdego unikatowego podpisu wywołania platformy używanego podczas wykonywania w programie .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: 05af4e17a91f7c0d8f3576a86d3d784ef6666aed
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803693"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="466f9-103">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="466f9-103">pInvokeLog MDA</span></span>
<span data-ttu-id="466f9-104">`pInvokeLog`Asystent debugowania zarządzanego (MDA) jest uaktywniany dla każdego unikatowego podpisu wywołania platformy używanego podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="466f9-104">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="466f9-105">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="466f9-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="466f9-106">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="466f9-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="466f9-107">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="466f9-107">Output</span></span>  
 <span data-ttu-id="466f9-108">Komunikat wskazujący podpis wywołania platformy używany podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="466f9-108">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="466f9-109">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="466f9-109">Configuration</span></span>  
 <span data-ttu-id="466f9-110">Każdy element dopasowania filtruje pliki. dll, do których są tworzone wywołania wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="466f9-110">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="466f9-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="466f9-111">See also</span></span>

- [<span data-ttu-id="466f9-112">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="466f9-112">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="466f9-113">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="466f9-113">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
