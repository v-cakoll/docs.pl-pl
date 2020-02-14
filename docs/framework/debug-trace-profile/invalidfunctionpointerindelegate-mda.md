---
title: invalidFunctionPointerInDelegate MDA
ms.date: 03/30/2017
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
ms.openlocfilehash: 723f51e14c314bde40c34d629ba7fc4f6276c633
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217379"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="d9740-102">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="d9740-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="d9740-103">Asystent debugowania zarządzanego `invalidFunctionPointerInDelegate` (MDA) jest uaktywniany po przekazaniu nieprawidłowego wskaźnika funkcji do konstruowania delegata przez wskaźnik funkcji natywnej.</span><span class="sxs-lookup"><span data-stu-id="d9740-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d9740-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="d9740-104">Symptoms</span></span>  
 <span data-ttu-id="d9740-105">Naruszenia zasad dostępu lub nieoczekiwane uszkodzenie pamięci podczas używania delegata na wskaźniku funkcji.</span><span class="sxs-lookup"><span data-stu-id="d9740-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d9740-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="d9740-106">Cause</span></span>  
 <span data-ttu-id="d9740-107">Określono nieprawidłowy wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="d9740-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d9740-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="d9740-108">Resolution</span></span>  
 <span data-ttu-id="d9740-109">Określ prawidłowy wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="d9740-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d9740-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d9740-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="d9740-111">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="d9740-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d9740-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="d9740-112">Output</span></span>  
 <span data-ttu-id="d9740-113">Nieprawidłowy wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="d9740-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d9740-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d9740-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9740-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9740-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d9740-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="d9740-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d9740-117">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="d9740-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
