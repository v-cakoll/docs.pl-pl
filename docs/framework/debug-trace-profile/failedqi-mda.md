---
title: failedQI MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc717f1500d202ae2590adb61b0376e93eba0944
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="failedqi-mda"></a><span data-ttu-id="d8490-102">failedQI MDA</span><span class="sxs-lookup"><span data-stu-id="d8490-102">failedQI MDA</span></span>
<span data-ttu-id="d8490-103">`failedQI` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy środowisko urchomieniowe wywołuje `QueryInterface` w imieniu wywoływana otoka środowiska uruchomieniowego (otoki RCW), wskaźnika interfejsu COM i `QueryInterface` wywołania kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d8490-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d8490-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="d8490-104">Symptoms</span></span>  
 <span data-ttu-id="d8490-105">Rzutowanie na otoki RCW nie powiedzie się lub wywołania modelu COM z otoki RCW nieoczekiwanie nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="d8490-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d8490-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="d8490-106">Cause</span></span>  
  
-   <span data-ttu-id="d8490-107">Połączenie jest nawiązywane z nieprawidłowego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="d8490-107">The call is made from the wrong context.</span></span>  
  
-   <span data-ttu-id="d8490-108">Kończy się niepowodzeniem zarejestrowanego serwera proxy `QueryInterface` wywołać, ponieważ podjęto próbę wywołania w nieprawidłowego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="d8490-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
-   <span data-ttu-id="d8490-109">Serwer proxy należące do OLE zwróciła błąd HRESULT.</span><span class="sxs-lookup"><span data-stu-id="d8490-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d8490-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="d8490-110">Resolution</span></span>  
 <span data-ttu-id="d8490-111">W regułach COM można znaleźć w dokumentacji MSDN.</span><span class="sxs-lookup"><span data-stu-id="d8490-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d8490-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d8490-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="d8490-113">Jeśli `QueryInterface` przełączono wywołanie się nie powiedzie, kontekst oraz `QueryInterface` wywołanie jest ponownie umieszczanie, aby zobaczyć, czy Nieprawidłowy kontekst został na pozycji błędu.</span><span class="sxs-lookup"><span data-stu-id="d8490-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d8490-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="d8490-114">Output</span></span>  
 <span data-ttu-id="d8490-115">Nazwa zarządzanego interfejsu, identyfikatora GUID interfejsu i HRESULT błędu.</span><span class="sxs-lookup"><span data-stu-id="d8490-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d8490-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d8490-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8490-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8490-117">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="d8490-118">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="d8490-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="d8490-119">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="d8490-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
