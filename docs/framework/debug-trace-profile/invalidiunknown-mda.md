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
ms.openlocfilehash: 35560b966d5fba60ac35b2eb1e559e196fc868f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223358"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="19896-102">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="19896-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="19896-103">`invalidIUnknown` Zarządzanego Asystenta debugowania (MDA) jest uaktywniany podczas nieprawidłową `IUnknown` wskaźnik jest przekazywany do kodu zarządzanego z kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="19896-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="19896-104">`IUnknown` Nie zwraca Powodzenie po otrzymaniu kwerendy dla `IUnknown` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="19896-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="19896-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="19896-105">Symptoms</span></span>  
 <span data-ttu-id="19896-106">Wystąpił nieoczekiwany błąd występuje, gdy marshaling wskaźnika interfejsu COM podczas przekazywania międzyprocesowego argumentu.</span><span class="sxs-lookup"><span data-stu-id="19896-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="19896-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="19896-107">Cause</span></span>  
 <span data-ttu-id="19896-108">Nieprawidłowe `QueryInterface` implementacji interfejsu COM jest przekazywany do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="19896-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="19896-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="19896-109">Resolution</span></span>  
 <span data-ttu-id="19896-110">Popraw `QueryInterface` implementacji.</span><span class="sxs-lookup"><span data-stu-id="19896-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="19896-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="19896-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="19896-112">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="19896-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="19896-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="19896-113">Output</span></span>  
 <span data-ttu-id="19896-114">Opis błędu.</span><span class="sxs-lookup"><span data-stu-id="19896-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="19896-115">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="19896-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="19896-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19896-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="19896-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="19896-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="19896-118">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="19896-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
