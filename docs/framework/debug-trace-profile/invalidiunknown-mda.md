---
title: invalidIUnknown MDA
description: Przejrzyj invalidIUnknown Managed Debug Assistant (MDA), który jest uaktywniany po przekazaniu nieprawidłowego wskaźnika IUnknown do kodu zarządzanego z kodu natywnego.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 65d704463ed746390ff1710b590bf080013bf53d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051730"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="d36b0-103">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="d36b0-103">invalidIUnknown MDA</span></span>
<span data-ttu-id="d36b0-104">`invalidIUnknown`Asystent debugowania zarządzanego (MDA) jest uaktywniany podczas przekazywania nieprawidłowego `IUnknown` wskaźnika do kodu zarządzanego z kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="d36b0-104">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="d36b0-105">`IUnknown`Nie można zwrócić sukcesu, gdy zapytanie dotyczące `IUnknown` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d36b0-105">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d36b0-106">Objawy</span><span class="sxs-lookup"><span data-stu-id="d36b0-106">Symptoms</span></span>  
 <span data-ttu-id="d36b0-107">Wystąpił nieoczekiwany błąd podczas organizowania wskaźnika interfejsu COM podczas organizowania argumentów.</span><span class="sxs-lookup"><span data-stu-id="d36b0-107">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d36b0-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="d36b0-108">Cause</span></span>  
 <span data-ttu-id="d36b0-109">Niepoprawna `QueryInterface` Implementacja interfejsu com przeniesiona do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d36b0-109">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d36b0-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="d36b0-110">Resolution</span></span>  
 <span data-ttu-id="d36b0-111">Popraw `QueryInterface` implementację.</span><span class="sxs-lookup"><span data-stu-id="d36b0-111">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d36b0-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d36b0-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="d36b0-113">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="d36b0-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d36b0-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="d36b0-114">Output</span></span>  
 <span data-ttu-id="d36b0-115">Opis błędu.</span><span class="sxs-lookup"><span data-stu-id="d36b0-115">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d36b0-116">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="d36b0-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d36b0-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d36b0-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d36b0-118">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="d36b0-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d36b0-119">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="d36b0-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
