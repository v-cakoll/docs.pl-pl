---
title: notMarshalable MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 489f0e2ff4dc1eeaa9721ec6cf59faad0bee2ca8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="db279-102">notMarshalable MDA</span><span class="sxs-lookup"><span data-stu-id="db279-102">notMarshalable MDA</span></span>
<span data-ttu-id="db279-103">`notMarshalable` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka wskaźnika interfejsu COM bez prawidłowy zarejestrowanego serwera proxy/stub lub niepoprawne `IMarshal` implementacja podczas próby interfejsu kierowanie interfejs między kontekstami.</span><span class="sxs-lookup"><span data-stu-id="db279-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="db279-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="db279-104">Symptoms</span></span>  
 <span data-ttu-id="db279-105">Wywołania nie są obsługiwane lub występować w nieprawidłowego kontekstu do wskaźników interfejsów COM. wywołań.</span><span class="sxs-lookup"><span data-stu-id="db279-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="db279-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="db279-106">Cause</span></span>  
 <span data-ttu-id="db279-107">Nie prawidłowy zarejestrowanego serwera proxy/stub lub niepoprawne `IMarshal` podczas próby kierować interfejs między kontekstami.</span><span class="sxs-lookup"><span data-stu-id="db279-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="db279-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="db279-108">Resolution</span></span>  
 <span data-ttu-id="db279-109">Upewnij się, że masz pełnomocnika namiastki zarejestrowany oraz czy `IMarshal` implementacja jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="db279-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="db279-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="db279-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="db279-111">To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="db279-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="db279-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="db279-112">Output</span></span>  
 <span data-ttu-id="db279-113">Komunikat opisujący problem.</span><span class="sxs-lookup"><span data-stu-id="db279-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="db279-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="db279-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="db279-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db279-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="db279-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="db279-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="db279-117">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="db279-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
