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
ms.openlocfilehash: c5de75130acab30c4f73522728c00b69c1c3e8d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="a3122-102">notMarshalable MDA</span><span class="sxs-lookup"><span data-stu-id="a3122-102">notMarshalable MDA</span></span>
<span data-ttu-id="a3122-103">`notMarshalable` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka wskaźnika interfejsu COM bez prawidłowy zarejestrowanego serwera proxy/stub lub niepoprawne `IMarshal` implementacja podczas próby interfejsu kierowanie interfejs między kontekstami.</span><span class="sxs-lookup"><span data-stu-id="a3122-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a3122-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="a3122-104">Symptoms</span></span>  
 <span data-ttu-id="a3122-105">Wywołania nie są obsługiwane lub występować w nieprawidłowego kontekstu do wskaźników interfejsów COM. wywołań.</span><span class="sxs-lookup"><span data-stu-id="a3122-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a3122-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="a3122-106">Cause</span></span>  
 <span data-ttu-id="a3122-107">Nie prawidłowy zarejestrowanego serwera proxy/stub lub niepoprawne `IMarshal` podczas próby kierować interfejs między kontekstami.</span><span class="sxs-lookup"><span data-stu-id="a3122-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a3122-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="a3122-108">Resolution</span></span>  
 <span data-ttu-id="a3122-109">Upewnij się, że masz pełnomocnika namiastki zarejestrowany oraz czy `IMarshal` implementacja jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a3122-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a3122-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a3122-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="a3122-111">To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="a3122-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a3122-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="a3122-112">Output</span></span>  
 <span data-ttu-id="a3122-113">Komunikat opisujący problem.</span><span class="sxs-lookup"><span data-stu-id="a3122-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a3122-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a3122-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3122-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3122-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="a3122-116">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="a3122-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="a3122-117">Przekazywanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="a3122-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
