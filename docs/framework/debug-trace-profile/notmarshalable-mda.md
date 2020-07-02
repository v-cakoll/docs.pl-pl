---
title: notMarshalable MDA
description: Zapoznaj się z asystentem debugowania zarządzanego notMarshalable, który może uaktywnić, jeśli wywołania nie są obsługiwane lub występują w nieprawidłowym kontekście wskaźników interfejsu COM.
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
ms.openlocfilehash: b464d914a8d83504daaf4cb276914da7798262dc
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803797"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="57d28-103">notMarshalable MDA</span><span class="sxs-lookup"><span data-stu-id="57d28-103">notMarshalable MDA</span></span>
<span data-ttu-id="57d28-104">`notMarshalable`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka wskaźnik interfejsu COM bez prawidłowego zarejestrowanego serwera proxy/zastępczego lub nieprawidłowej `IMarshal` implementacji interfejsu podczas próby zorganizowania interfejsu w wielu kontekstach.</span><span class="sxs-lookup"><span data-stu-id="57d28-104">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="57d28-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="57d28-105">Symptoms</span></span>  
 <span data-ttu-id="57d28-106">Wywołania nie są obsługiwane lub wywołania występują w nieprawidłowym kontekście wskaźników interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="57d28-106">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="57d28-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="57d28-107">Cause</span></span>  
 <span data-ttu-id="57d28-108">Brak prawidłowego zarejestrowanego serwera proxy/zastępczego lub nieprawidłowej `IMarshal` próby zorganizowania interfejsu w wielu kontekstach.</span><span class="sxs-lookup"><span data-stu-id="57d28-108">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="57d28-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="57d28-109">Resolution</span></span>  
 <span data-ttu-id="57d28-110">Upewnij się, że zarejestrowano procedurę pośredniczącą serwera proxy i że `IMarshal` implementacja jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="57d28-110">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="57d28-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="57d28-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="57d28-112">To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="57d28-112">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="57d28-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="57d28-113">Output</span></span>  
 <span data-ttu-id="57d28-114">Komunikat z opisem problemu.</span><span class="sxs-lookup"><span data-stu-id="57d28-114">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="57d28-115">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="57d28-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="57d28-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57d28-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="57d28-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="57d28-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="57d28-118">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="57d28-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
