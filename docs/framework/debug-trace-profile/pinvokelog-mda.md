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
ms.openlocfilehash: 0883849eee12922601e50c2337bb0048d77cab68
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052376"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="fdae1-102">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="fdae1-102">pInvokeLog MDA</span></span>
<span data-ttu-id="fdae1-103">Asystent `pInvokeLog` debugowania zarządzanego (MDA) jest uaktywniany dla każdego unikatowego podpisu wywołania platformy używanego podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fdae1-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fdae1-104">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="fdae1-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="fdae1-105">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="fdae1-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fdae1-106">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="fdae1-106">Output</span></span>  
 <span data-ttu-id="fdae1-107">Komunikat wskazujący podpis wywołania platformy używany podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fdae1-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="fdae1-108">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="fdae1-108">Configuration</span></span>  
 <span data-ttu-id="fdae1-109">Każdy element dopasowania filtruje pliki. dll, do których są tworzone wywołania wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="fdae1-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fdae1-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdae1-110">See also</span></span>

- [<span data-ttu-id="fdae1-111">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="fdae1-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="fdae1-112">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="fdae1-112">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
