---
title: invalidIUnknown MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea7f48ab61c16cb0430717074f1b1feab4827763
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052595"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="86bdb-102">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="86bdb-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="86bdb-103">Asystent debugowania `IUnknown` zarządzanego (MDA) jest uaktywniany podczas przekazywania nieprawidłowego wskaźnika do kodu zarządzanego z kodu natywnego. `invalidIUnknown`</span><span class="sxs-lookup"><span data-stu-id="86bdb-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="86bdb-104">Nie `IUnknown` można zwrócić sukcesu, gdy zapytanie `IUnknown` dotyczące interfejsu.</span><span class="sxs-lookup"><span data-stu-id="86bdb-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="86bdb-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="86bdb-105">Symptoms</span></span>  
 <span data-ttu-id="86bdb-106">Wystąpił nieoczekiwany błąd podczas organizowania wskaźnika interfejsu COM podczas organizowania argumentów.</span><span class="sxs-lookup"><span data-stu-id="86bdb-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="86bdb-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="86bdb-107">Cause</span></span>  
 <span data-ttu-id="86bdb-108">Niepoprawna `QueryInterface` implementacja interfejsu com przeniesiona do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="86bdb-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="86bdb-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="86bdb-109">Resolution</span></span>  
 <span data-ttu-id="86bdb-110">`QueryInterface` Popraw implementację.</span><span class="sxs-lookup"><span data-stu-id="86bdb-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="86bdb-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="86bdb-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="86bdb-112">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="86bdb-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="86bdb-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="86bdb-113">Output</span></span>  
 <span data-ttu-id="86bdb-114">Opis błędu.</span><span class="sxs-lookup"><span data-stu-id="86bdb-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="86bdb-115">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="86bdb-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86bdb-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86bdb-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="86bdb-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="86bdb-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="86bdb-118">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="86bdb-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
