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
ms.openlocfilehash: ddb6b0b5c2248d215245e0f881c8e7c91b13e480
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052427"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="3282c-102">notMarshalable MDA</span><span class="sxs-lookup"><span data-stu-id="3282c-102">notMarshalable MDA</span></span>
<span data-ttu-id="3282c-103">Asystent debugowania `IMarshal` zarządzanego (MDA) jest uaktywniany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotyka wskaźnik interfejsu COM bez prawidłowego zarejestrowanego serwera proxy/szczątkowego lub nieprawidłowej implementacji interfejsu podczas próby `notMarshalable` kierowanie interfejsu między kontekstami.</span><span class="sxs-lookup"><span data-stu-id="3282c-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3282c-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="3282c-104">Symptoms</span></span>  
 <span data-ttu-id="3282c-105">Wywołania nie są obsługiwane lub wywołania występują w nieprawidłowym kontekście wskaźników interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="3282c-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3282c-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="3282c-106">Cause</span></span>  
 <span data-ttu-id="3282c-107">Brak prawidłowego zarejestrowanego serwera proxy/zastępczego lub nieprawidłowej `IMarshal` próby zorganizowania interfejsu w wielu kontekstach.</span><span class="sxs-lookup"><span data-stu-id="3282c-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3282c-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="3282c-108">Resolution</span></span>  
 <span data-ttu-id="3282c-109">Upewnij się, że zarejestrowano procedurę pośredniczącą serwera `IMarshal` proxy i że implementacja jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="3282c-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3282c-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3282c-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="3282c-111">To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="3282c-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3282c-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="3282c-112">Output</span></span>  
 <span data-ttu-id="3282c-113">Komunikat z opisem problemu.</span><span class="sxs-lookup"><span data-stu-id="3282c-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3282c-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="3282c-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3282c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3282c-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="3282c-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="3282c-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="3282c-117">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="3282c-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
