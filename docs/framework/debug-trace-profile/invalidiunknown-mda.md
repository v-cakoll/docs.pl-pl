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
ms.openlocfilehash: db360a3b7c5f70596d5d5855b8e38dae5d484c42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390178"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="c2bb1-102">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="c2bb1-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="c2bb1-103">`invalidIUnknown` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy nieprawidłową `IUnknown` wskaźnika są przekazywane do kodu zarządzanego z kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="c2bb1-104">`IUnknown` Zakończy się niepowodzeniem, zwraca sukces, gdy zapytanie dotyczące `IUnknown` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c2bb1-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="c2bb1-105">Symptoms</span></span>  
 <span data-ttu-id="c2bb1-106">Wystąpił nieoczekiwany błąd występuje, gdy organizowanie wskaźnika interfejsu COM podczas przekazywania międzyprocesowego argumentu.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c2bb1-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="c2bb1-107">Cause</span></span>  
 <span data-ttu-id="c2bb1-108">Niepoprawna `QueryInterface` implementacji interfejsu COM przekazany do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c2bb1-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="c2bb1-109">Resolution</span></span>  
 <span data-ttu-id="c2bb1-110">Popraw `QueryInterface` implementacji.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c2bb1-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c2bb1-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="c2bb1-112">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c2bb1-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="c2bb1-113">Output</span></span>  
 <span data-ttu-id="c2bb1-114">Opis błędu.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c2bb1-115">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c2bb1-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2bb1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2bb1-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="c2bb1-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="c2bb1-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="c2bb1-118">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="c2bb1-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
