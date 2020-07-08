---
title: invalidFunctionPointerInDelegate MDA
description: Przejrzyj invalidFunctionPointerInDelegate Managed Debug Assistant (MDA), który jest wywoływany w przypadku przekazania nieprawidłowego wskaźnika funkcji do obiektu delegowanego.
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
ms.openlocfilehash: a17427d117c62ba782af3c9549c84623a3013b06
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051743"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="3225c-103">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="3225c-103">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="3225c-104">`invalidFunctionPointerInDelegate`Asystent debugowania zarządzanego (MDA) jest uaktywniany po przekazaniu nieprawidłowego wskaźnika funkcji do konstruowania delegata przez wskaźnik funkcji natywnej.</span><span class="sxs-lookup"><span data-stu-id="3225c-104">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3225c-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="3225c-105">Symptoms</span></span>  
 <span data-ttu-id="3225c-106">Naruszenia zasad dostępu lub nieoczekiwane uszkodzenie pamięci podczas używania delegata na wskaźniku funkcji.</span><span class="sxs-lookup"><span data-stu-id="3225c-106">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3225c-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="3225c-107">Cause</span></span>  
 <span data-ttu-id="3225c-108">Określono nieprawidłowy wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="3225c-108">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3225c-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="3225c-109">Resolution</span></span>  
 <span data-ttu-id="3225c-110">Określ prawidłowy wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="3225c-110">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3225c-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3225c-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="3225c-112">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="3225c-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3225c-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="3225c-113">Output</span></span>  
 <span data-ttu-id="3225c-114">Nieprawidłowy wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="3225c-114">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3225c-115">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="3225c-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3225c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3225c-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="3225c-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="3225c-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="3225c-118">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="3225c-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
