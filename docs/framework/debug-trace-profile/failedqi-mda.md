---
title: failedQI MDA
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ac478644561d2aab13d10811987d8d02c8d7608
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217630"
---
# <a name="failedqi-mda"></a><span data-ttu-id="b2217-102">failedQI MDA</span><span class="sxs-lookup"><span data-stu-id="b2217-102">failedQI MDA</span></span>
<span data-ttu-id="b2217-103">`failedQI` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy środowisko wykonawcze wywołuje `QueryInterface` na wskaźnik interfejsu COM w imieniu wywoływana otoka środowiska uruchomieniowego (RCW), a `QueryInterface` wywołanie zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="b2217-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b2217-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="b2217-104">Symptoms</span></span>  
 <span data-ttu-id="b2217-105">Rzutowanie na RCW zakończy się niepowodzeniem lub wywołania dla modelu COM z RCW nieoczekiwanie zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="b2217-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b2217-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="b2217-106">Cause</span></span>  
  
-   <span data-ttu-id="b2217-107">Wykonano wywołanie z nieprawidłowym kontekście.</span><span class="sxs-lookup"><span data-stu-id="b2217-107">The call is made from the wrong context.</span></span>  
  
-   <span data-ttu-id="b2217-108">Zarejestrowany serwer proxy, kończy się niepowodzeniem `QueryInterface` wywołania, ponieważ podjęto próbę wywołania w nieprawidłowym kontekście.</span><span class="sxs-lookup"><span data-stu-id="b2217-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
-   <span data-ttu-id="b2217-109">Serwer proxy należące do OLE zwróciła błąd HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b2217-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b2217-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="b2217-110">Resolution</span></span>  
 <span data-ttu-id="b2217-111">Na karcie reguły COM można znaleźć w dokumentacji MSDN.</span><span class="sxs-lookup"><span data-stu-id="b2217-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b2217-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b2217-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="b2217-113">Jeśli `QueryInterface` wywołanie zakończy się niepowodzeniem, kontekst jest włączane i `QueryInterface` wywołanie podejmowana jest próba ponownie zobaczyć był nieprawidłowy kontekst na pozycji błędu.</span><span class="sxs-lookup"><span data-stu-id="b2217-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b2217-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="b2217-114">Output</span></span>  
 <span data-ttu-id="b2217-115">Zarządzane nazwy interfejsu, identyfikator GUID interfejsu i HRESULT błędu.</span><span class="sxs-lookup"><span data-stu-id="b2217-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b2217-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="b2217-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2217-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2217-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="b2217-118">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="b2217-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="b2217-119">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="b2217-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
