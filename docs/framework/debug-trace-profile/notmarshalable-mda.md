---
title: notMarshalable MDA
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30db07ddf935b5ce13b1fe4212f7f6a40270ae93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753702"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="ce624-102">notMarshalable MDA</span><span class="sxs-lookup"><span data-stu-id="ce624-102">notMarshalable MDA</span></span>
<span data-ttu-id="ce624-103">`notMarshalable` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka wskaźnika interfejsu COM bez prawidłowe zarejestrowanych proxy/zastępczego lub niepoprawne `IMarshal` implementacji podczas próby interfejsu Kieruj interfejsu w różnych kontekstach.</span><span class="sxs-lookup"><span data-stu-id="ce624-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ce624-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="ce624-104">Symptoms</span></span>  
 <span data-ttu-id="ce624-105">Wywołania nie są obsługiwane lub występować wywołań w nieprawidłowym kontekście dla wskaźników interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="ce624-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ce624-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="ce624-106">Cause</span></span>  
 <span data-ttu-id="ce624-107">Nie prawidłowe zarejestrowanych proxy/zastępczego lub niepoprawne `IMarshal` podczas próby kierować interfejsu w różnych kontekstach.</span><span class="sxs-lookup"><span data-stu-id="ce624-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ce624-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ce624-108">Resolution</span></span>  
 <span data-ttu-id="ce624-109">Upewnij się, pełnomocnika namiastki zarejestrowany oraz że `IMarshal` wdrożenia jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ce624-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ce624-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ce624-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="ce624-111">To zdarzenie MDA nie ma wpływu na środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ce624-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ce624-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="ce624-112">Output</span></span>  
 <span data-ttu-id="ce624-113">Komunikat opisujący problem.</span><span class="sxs-lookup"><span data-stu-id="ce624-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ce624-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ce624-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce624-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce624-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ce624-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="ce624-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ce624-117">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="ce624-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
