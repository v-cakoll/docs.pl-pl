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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 847ec4d861136b46383ce7d3801764f3d962049e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="5e7c3-102">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="5e7c3-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="5e7c3-103">`invalidFunctionPointerInDelegate` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy nieprawidłowy wskaźnik funkcji jest przekazany w celu utworzenia delegata za pośrednictwem wskaźnika funkcji macierzystej.</span><span class="sxs-lookup"><span data-stu-id="5e7c3-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5e7c3-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="5e7c3-104">Symptoms</span></span>  
 <span data-ttu-id="5e7c3-105">Naruszenia zasad dostępu lub uszkodzenie pamięci nieoczekiwany, używając delegata przez wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="5e7c3-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5e7c3-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="5e7c3-106">Cause</span></span>  
 <span data-ttu-id="5e7c3-107">Określono nieprawidłowy wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="5e7c3-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5e7c3-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="5e7c3-108">Resolution</span></span>  
 <span data-ttu-id="5e7c3-109">Określ prawidłową funkcją wskaźnik</span><span class="sxs-lookup"><span data-stu-id="5e7c3-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5e7c3-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="5e7c3-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="5e7c3-111">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="5e7c3-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5e7c3-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="5e7c3-112">Output</span></span>  
 <span data-ttu-id="5e7c3-113">Nieprawidłowy wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="5e7c3-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5e7c3-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5e7c3-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e7c3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e7c3-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="5e7c3-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="5e7c3-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="5e7c3-117">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="5e7c3-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
