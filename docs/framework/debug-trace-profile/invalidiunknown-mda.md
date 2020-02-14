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
ms.openlocfilehash: 5df9a3f506d8c2de6f1a3125459adc2d59d510bf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217366"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="209a0-102">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="209a0-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="209a0-103">Asystent debugowania zarządzanego `invalidIUnknown` (MDA) jest uaktywniany po przekazaniu nieprawidłowego wskaźnika `IUnknown` do kodu zarządzanego z kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="209a0-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="209a0-104">`IUnknown` nie może zwrócić sukcesu w przypadku zapytania o interfejs `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="209a0-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="209a0-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="209a0-105">Symptoms</span></span>  
 <span data-ttu-id="209a0-106">Wystąpił nieoczekiwany błąd podczas organizowania wskaźnika interfejsu COM podczas organizowania argumentów.</span><span class="sxs-lookup"><span data-stu-id="209a0-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="209a0-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="209a0-107">Cause</span></span>  
 <span data-ttu-id="209a0-108">Niepoprawna implementacja `QueryInterface` w interfejsie COM przeniesiona do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="209a0-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="209a0-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="209a0-109">Resolution</span></span>  
 <span data-ttu-id="209a0-110">Popraw implementację `QueryInterface`.</span><span class="sxs-lookup"><span data-stu-id="209a0-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="209a0-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="209a0-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="209a0-112">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="209a0-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="209a0-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="209a0-113">Output</span></span>  
 <span data-ttu-id="209a0-114">Opis błędu.</span><span class="sxs-lookup"><span data-stu-id="209a0-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="209a0-115">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="209a0-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="209a0-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="209a0-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="209a0-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="209a0-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="209a0-118">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="209a0-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
