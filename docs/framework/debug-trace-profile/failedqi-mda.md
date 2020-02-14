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
ms.openlocfilehash: 4c36ec514645a38ef1228e76bdf6dbd06e886bae
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217505"
---
# <a name="failedqi-mda"></a><span data-ttu-id="caa1c-102">failedQI MDA</span><span class="sxs-lookup"><span data-stu-id="caa1c-102">failedQI MDA</span></span>
<span data-ttu-id="caa1c-103">Asystent debugowania zarządzanego `failedQI` (MDA) jest uaktywniany, gdy wywołania środowiska uruchomieniowego `QueryInterface` na wskaźniku interfejsu COM w imieniu otoki (RCW) środowiska uruchomieniowego, a wywołanie `QueryInterface` kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="caa1c-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="caa1c-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="caa1c-104">Symptoms</span></span>  
 <span data-ttu-id="caa1c-105">Rzutowanie otoki RCW kończy się niepowodzeniem lub wywołanie modelu COM z otoki RCW nieoczekiwanie zakończyło się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="caa1c-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="caa1c-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="caa1c-106">Cause</span></span>  
  
- <span data-ttu-id="caa1c-107">Wywołanie zostało wykonane z niewłaściwego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="caa1c-107">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="caa1c-108">Zarejestrowany serwer proxy kończy się niepowodzeniem wywołania `QueryInterface`, ponieważ próba wywołania była w nieprawidłowym kontekście.</span><span class="sxs-lookup"><span data-stu-id="caa1c-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="caa1c-109">Serwer proxy należący do OLE zwrócił błąd HRESULT.</span><span class="sxs-lookup"><span data-stu-id="caa1c-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="caa1c-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="caa1c-110">Resolution</span></span>  
 <span data-ttu-id="caa1c-111">Zapoznaj się z dokumentacją MSDN dotyczącą reguł COM.</span><span class="sxs-lookup"><span data-stu-id="caa1c-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="caa1c-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="caa1c-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="caa1c-113">Jeśli wywołanie `QueryInterface` nie powiedzie się, kontekst jest przełączany i próba wywołania `QueryInterface` zostanie ponowiona, aby sprawdzić, czy wystąpił błąd w nieprawidłowym kontekście.</span><span class="sxs-lookup"><span data-stu-id="caa1c-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="caa1c-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="caa1c-114">Output</span></span>  
 <span data-ttu-id="caa1c-115">Zarządzana nazwa interfejsu, identyfikator GUID interfejsu i HRESULT błędu.</span><span class="sxs-lookup"><span data-stu-id="caa1c-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="caa1c-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="caa1c-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="caa1c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="caa1c-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="caa1c-118">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="caa1c-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="caa1c-119">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="caa1c-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
