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
ms.openlocfilehash: cbb33d2cddab22ad2072354ba543d2cd6a60a668
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754573"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="50bb2-102">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="50bb2-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="50bb2-103">`invalidFunctionPointerInDelegate` Zarządzanego Asystenta debugowania (MDA) jest uaktywniany podczas nieprawidłowy wskaźnik funkcji jest przekazywany do utworzenia delegata przez wskaźnik natywnej funkcji.</span><span class="sxs-lookup"><span data-stu-id="50bb2-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="50bb2-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="50bb2-104">Symptoms</span></span>  
 <span data-ttu-id="50bb2-105">Naruszenia zasad dostępu ani uszkodzeń pamięci nieoczekiwany, używając delegata za pośrednictwem wskaźnika funkcji.</span><span class="sxs-lookup"><span data-stu-id="50bb2-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="50bb2-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="50bb2-106">Cause</span></span>  
 <span data-ttu-id="50bb2-107">Określono nieprawidłowy wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="50bb2-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="50bb2-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="50bb2-108">Resolution</span></span>  
 <span data-ttu-id="50bb2-109">Określ prawidłową funkcją wskaźnik</span><span class="sxs-lookup"><span data-stu-id="50bb2-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="50bb2-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="50bb2-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="50bb2-111">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="50bb2-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="50bb2-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="50bb2-112">Output</span></span>  
 <span data-ttu-id="50bb2-113">Nieprawidłowy wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="50bb2-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="50bb2-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="50bb2-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="50bb2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50bb2-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="50bb2-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="50bb2-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="50bb2-117">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="50bb2-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
