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
ms.openlocfilehash: 6e3e64a720d12426fb066619b46c73402d1113e0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052625"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="55bed-102">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="55bed-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="55bed-103">Asystent `invalidFunctionPointerInDelegate` debugowania zarządzanego (MDA) jest uaktywniany po przekazaniu nieprawidłowego wskaźnika funkcji do konstruowania delegata przez wskaźnik funkcji natywnej.</span><span class="sxs-lookup"><span data-stu-id="55bed-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="55bed-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="55bed-104">Symptoms</span></span>  
 <span data-ttu-id="55bed-105">Naruszenia zasad dostępu lub nieoczekiwane uszkodzenie pamięci podczas używania delegata na wskaźniku funkcji.</span><span class="sxs-lookup"><span data-stu-id="55bed-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="55bed-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="55bed-106">Cause</span></span>  
 <span data-ttu-id="55bed-107">Określono nieprawidłowy wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="55bed-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="55bed-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="55bed-108">Resolution</span></span>  
 <span data-ttu-id="55bed-109">Określ prawidłowy wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="55bed-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="55bed-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="55bed-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="55bed-111">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="55bed-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="55bed-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="55bed-112">Output</span></span>  
 <span data-ttu-id="55bed-113">Nieprawidłowy wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="55bed-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="55bed-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="55bed-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="55bed-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55bed-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="55bed-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="55bed-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="55bed-117">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="55bed-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
