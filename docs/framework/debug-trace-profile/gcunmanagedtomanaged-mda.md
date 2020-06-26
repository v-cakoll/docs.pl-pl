---
title: gcUnmanagedToManaged MDA
description: Zapoznaj się z asystentem debugowania zarządzanego przez gcManagedToUnmanaged w programie .NET. To zdarzenie MDA może zostać aktywowane ze względu na uszkodzenie sterty pamięci podczas przejścia do kodu zarządzanego.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
ms.openlocfilehash: 320d55224e6a204d330447d6c68eabe0fa6cf892
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415904"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="8157a-104">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="8157a-104">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="8157a-105">`gcUnmanagedToManaged`Asystent debugowania zarządzanego (MDA) powoduje wyrzucanie elementów bezużytecznych za każdym razem, gdy wątek przechodzi z niezarządzanych do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8157a-105">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8157a-106">Objawy</span><span class="sxs-lookup"><span data-stu-id="8157a-106">Symptoms</span></span>  
 <span data-ttu-id="8157a-107">Aplikacja, która uruchamia niezarządzane składniki użytkownika przy użyciu modelu COM i wywołania platformy, powoduje niedeterministyczne naruszenie dostępu w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="8157a-107">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8157a-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="8157a-108">Cause</span></span>  
 <span data-ttu-id="8157a-109">Jeśli aplikacja działa w niezarządzanych składnikach użytkownika, wówczas te składniki mogły spowodować uszkodzenie sterty zebranej przez elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="8157a-109">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="8157a-110">Powoduje to naruszenie zasad dostępu w środowisku CLR, gdy moduł zbierający elementy bezużyteczne podejmie próbę wykonania grafu obiektów.</span><span class="sxs-lookup"><span data-stu-id="8157a-110">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8157a-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="8157a-111">Resolution</span></span>  
 <span data-ttu-id="8157a-112">Włączenie tego asystenta skraca czas od momentu, gdy składnik niezarządzany uszkadza stertę zebraną przez elementy bezużyteczne i gdy występuje naruszenie zasad dostępu, wymuszając wyrzucanie elementów bezużytecznych przed każdym zarządzanym przejściem.</span><span class="sxs-lookup"><span data-stu-id="8157a-112">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8157a-113">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="8157a-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="8157a-114">Powoduje wyrzucanie elementów bezużytecznych przy każdym przejścia wątku z niezarządzanego do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8157a-114">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8157a-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="8157a-115">Output</span></span>  
 <span data-ttu-id="8157a-116">To zdarzenie MDA nie generuje danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="8157a-116">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8157a-117">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="8157a-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8157a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8157a-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="8157a-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="8157a-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="8157a-120">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="8157a-120">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="8157a-121">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="8157a-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
