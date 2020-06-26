---
title: fatalExecutionEngineError MDA
description: Zapoznaj się z asystentem debugowania zarządzanego fatalExecutionEngineError (MDA) w programie .NET, który może zostać aktywowany z powodu nieoczekiwanego zakończenia procesu.
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
ms.openlocfilehash: 0806d2eaa1752c88bebd03304fbe5c8094416a48
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415930"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="f7777-103">fatalExecutionEngineError MDA</span><span class="sxs-lookup"><span data-stu-id="f7777-103">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="f7777-104">`fatalExecutionEngineError`Asystent debugowania zarządzanego (MDA) jest uaktywniany w przypadku wykrycia błędu krytycznego w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f7777-104">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="f7777-105">Proces zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="f7777-105">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f7777-106">Objawy</span><span class="sxs-lookup"><span data-stu-id="f7777-106">Symptoms</span></span>  
 <span data-ttu-id="f7777-107">Nieoczekiwane zakończenie procesu.</span><span class="sxs-lookup"><span data-stu-id="f7777-107">Unexpected process termination.</span></span> <span data-ttu-id="f7777-108">Nie można ustalić innych objawów, ponieważ awaria środowiska CLR może wystąpić z różnych powodów.</span><span class="sxs-lookup"><span data-stu-id="f7777-108">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f7777-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="f7777-109">Cause</span></span>  
 <span data-ttu-id="f7777-110">Środowisko CLR zostało uszkodzone w sposób krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f7777-110">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="f7777-111">Jest to najczęściej spowodowane uszkodzeniem danych, które może być spowodowane przez wiele problemów, takich jak wywołania źle sformułowanej platformy wywołania funkcji i przekazywanie nieprawidłowych danych do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="f7777-111">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f7777-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="f7777-112">Resolution</span></span>  
 <span data-ttu-id="f7777-113">Włączenie dodatkowych MDA może pomóc w zidentyfikowaniu problemu.</span><span class="sxs-lookup"><span data-stu-id="f7777-113">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="f7777-114">Następujący MDA może być szczególnie przydatny w diagnozowaniu problemu:</span><span class="sxs-lookup"><span data-stu-id="f7777-114">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="f7777-115">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="f7777-115">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="f7777-116">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="f7777-116">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="f7777-117">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="f7777-117">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="f7777-118">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="f7777-118">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="f7777-119">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="f7777-119">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="f7777-120">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="f7777-120">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="f7777-121">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="f7777-121">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="f7777-122">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="f7777-122">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="f7777-123">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="f7777-123">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="f7777-124">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="f7777-124">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="f7777-125">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="f7777-125">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="f7777-126">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="f7777-126">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f7777-127">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f7777-127">Effect on the Runtime</span></span>  
 <span data-ttu-id="f7777-128">To zdarzenie MDA nie ma wpływu na zachowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f7777-128">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f7777-129">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="f7777-129">Output</span></span>  
 <span data-ttu-id="f7777-130">Adres funkcji CLR, która spowodowała błąd krytyczny, identyfikator wątku, w którym wystąpił błąd, oraz kod błędu.</span><span class="sxs-lookup"><span data-stu-id="f7777-130">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f7777-131">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="f7777-131">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7777-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7777-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="f7777-133">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="f7777-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
