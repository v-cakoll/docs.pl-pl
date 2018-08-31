---
title: fatalExecutionEngineError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- corrupted CLR
- fatal execution error
- terminated processes
- unexpected terminations
- fatal errors
- MDAs (managed debugging assistants), fatal errors
- process termination
- FatalExecutionEngineError MDA
- managed debugging assistants (MDAs), fatal errors
ms.assetid: 8b559e44-2393-4e4e-8160-7558d37a4a89
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f12b94198b88111d559cfe372c28bdbf4b37e3fe
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257480"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="bb892-102">fatalExecutionEngineError MDA</span><span class="sxs-lookup"><span data-stu-id="bb892-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="bb892-103">`fatalExecutionEngineError` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy wykryto błąd krytyczny w środowisku uruchomieniowym języka (wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="bb892-103">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="bb892-104">Proces zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="bb892-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bb892-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="bb892-105">Symptoms</span></span>  
 <span data-ttu-id="bb892-106">Kończenie procesu nieoczekiwany.</span><span class="sxs-lookup"><span data-stu-id="bb892-106">Unexpected process termination.</span></span> <span data-ttu-id="bb892-107">Nie można określić inne objawy, ponieważ może wystąpić błąd CLR, z różnych powodów.</span><span class="sxs-lookup"><span data-stu-id="bb892-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bb892-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="bb892-108">Cause</span></span>  
 <span data-ttu-id="bb892-109">Środowisko CLR jest uszkodzony krytycznego.</span><span class="sxs-lookup"><span data-stu-id="bb892-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="bb892-110">W większości przypadków jest to spowodowane uszkodzeniem danych, która może wpływać wiele problemów, takich jak wywołania platformy źle sformułowane wywołania funkcji i przekazanie nieprawidłowe dane do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="bb892-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bb892-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="bb892-111">Resolution</span></span>  
 <span data-ttu-id="bb892-112">Włączanie dodatkowych MDA może ułatwić zidentyfikowanie problemu.</span><span class="sxs-lookup"><span data-stu-id="bb892-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="bb892-113">Następujące MDA może być szczególnie przydatne podczas diagnozowania problemu:</span><span class="sxs-lookup"><span data-stu-id="bb892-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
-   [<span data-ttu-id="bb892-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="bb892-114">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)  
  
-   [<span data-ttu-id="bb892-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="bb892-115">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)  
  
-   [<span data-ttu-id="bb892-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="bb892-116">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)  
  
-   [<span data-ttu-id="bb892-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="bb892-117">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)  
  
-   [<span data-ttu-id="bb892-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="bb892-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
  
-   [<span data-ttu-id="bb892-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="bb892-119">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)  
  
-   [<span data-ttu-id="bb892-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="bb892-120">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)  
  
-   [<span data-ttu-id="bb892-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="bb892-121">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)  
  
-   [<span data-ttu-id="bb892-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="bb892-122">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)  
  
-   [<span data-ttu-id="bb892-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="bb892-123">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)  
  
-   [<span data-ttu-id="bb892-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="bb892-124">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)  
  
-   [<span data-ttu-id="bb892-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="bb892-125">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bb892-126">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="bb892-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="bb892-127">To zdarzenie MDA nie ma wpływu na działanie w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="bb892-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bb892-128">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="bb892-128">Output</span></span>  
 <span data-ttu-id="bb892-129">Adres funkcji CLR, który spowodował błąd krytyczny, identyfikator wątku, w którym wystąpił błąd i kod błędu.</span><span class="sxs-lookup"><span data-stu-id="bb892-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="bb892-130">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="bb892-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb892-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb892-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution.Cer>  
 [<span data-ttu-id="bb892-132">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="bb892-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
