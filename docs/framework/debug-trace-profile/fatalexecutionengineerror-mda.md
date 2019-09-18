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
ms.openlocfilehash: 3fd58ae8f73fd932df641ea96a44ff618dd139e2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052806"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="cccb8-102">fatalExecutionEngineError MDA</span><span class="sxs-lookup"><span data-stu-id="cccb8-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="cccb8-103">Asystent `fatalExecutionEngineError` debugowania zarządzanego (MDA) jest uaktywniany w przypadku wykrycia błędu krytycznego w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="cccb8-103">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="cccb8-104">Proces zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="cccb8-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="cccb8-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="cccb8-105">Symptoms</span></span>  
 <span data-ttu-id="cccb8-106">Nieoczekiwane zakończenie procesu.</span><span class="sxs-lookup"><span data-stu-id="cccb8-106">Unexpected process termination.</span></span> <span data-ttu-id="cccb8-107">Nie można ustalić innych objawów, ponieważ awaria środowiska CLR może wystąpić z różnych powodów.</span><span class="sxs-lookup"><span data-stu-id="cccb8-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="cccb8-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="cccb8-108">Cause</span></span>  
 <span data-ttu-id="cccb8-109">Środowisko CLR zostało uszkodzone w sposób krytyczny.</span><span class="sxs-lookup"><span data-stu-id="cccb8-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="cccb8-110">Jest to najczęściej spowodowane uszkodzeniem danych, które może być spowodowane przez wiele problemów, takich jak wywołania źle sformułowanej platformy wywołania funkcji i przekazywanie nieprawidłowych danych do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="cccb8-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="cccb8-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="cccb8-111">Resolution</span></span>  
 <span data-ttu-id="cccb8-112">Włączenie dodatkowych MDA może pomóc w zidentyfikowaniu problemu.</span><span class="sxs-lookup"><span data-stu-id="cccb8-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="cccb8-113">Następujący MDA może być szczególnie przydatny w diagnozowaniu problemu:</span><span class="sxs-lookup"><span data-stu-id="cccb8-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="cccb8-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="cccb8-114">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="cccb8-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="cccb8-115">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="cccb8-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="cccb8-116">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="cccb8-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="cccb8-117">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="cccb8-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="cccb8-118">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="cccb8-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="cccb8-119">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="cccb8-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="cccb8-120">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="cccb8-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="cccb8-121">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="cccb8-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="cccb8-122">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="cccb8-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="cccb8-123">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="cccb8-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="cccb8-124">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="cccb8-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="cccb8-125">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="cccb8-126">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="cccb8-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="cccb8-127">To zdarzenie MDA nie ma wpływu na zachowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="cccb8-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="cccb8-128">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="cccb8-128">Output</span></span>  
 <span data-ttu-id="cccb8-129">Adres funkcji CLR, która spowodowała błąd krytyczny, identyfikator wątku, w którym wystąpił błąd, oraz kod błędu.</span><span class="sxs-lookup"><span data-stu-id="cccb8-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="cccb8-130">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="cccb8-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cccb8-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cccb8-131">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="cccb8-132">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="cccb8-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
