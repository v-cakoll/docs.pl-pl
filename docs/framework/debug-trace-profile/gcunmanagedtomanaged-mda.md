---
title: gcUnmanagedToManaged MDA
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
ms.openlocfilehash: dd4080870ae88da8d4e2055369cd36f3981f2eac
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216455"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="a0ea3-102">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="a0ea3-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="a0ea3-103">Asystent debugowania zarządzanego `gcUnmanagedToManaged` (MDA) powoduje wyrzucanie elementów bezużytecznych za każdym razem, gdy wątek przechodzi z niezarządzanych do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a0ea3-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a0ea3-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="a0ea3-104">Symptoms</span></span>  
 <span data-ttu-id="a0ea3-105">Aplikacja, która uruchamia niezarządzane składniki użytkownika przy użyciu modelu COM i wywołania platformy, powoduje niedeterministyczne naruszenie dostępu w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="a0ea3-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a0ea3-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="a0ea3-106">Cause</span></span>  
 <span data-ttu-id="a0ea3-107">Jeśli aplikacja działa w niezarządzanych składnikach użytkownika, wówczas te składniki mogły spowodować uszkodzenie sterty zebranej przez elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="a0ea3-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="a0ea3-108">Powoduje to naruszenie zasad dostępu w środowisku CLR, gdy moduł zbierający elementy bezużyteczne podejmie próbę wykonania grafu obiektów.</span><span class="sxs-lookup"><span data-stu-id="a0ea3-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a0ea3-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="a0ea3-109">Resolution</span></span>  
 <span data-ttu-id="a0ea3-110">Włączenie tego asystenta skraca czas od momentu, gdy składnik niezarządzany uszkadza stertę zebraną przez elementy bezużyteczne i gdy występuje naruszenie zasad dostępu, wymuszając wyrzucanie elementów bezużytecznych przed każdym zarządzanym przejściem.</span><span class="sxs-lookup"><span data-stu-id="a0ea3-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a0ea3-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a0ea3-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="a0ea3-112">Powoduje wyrzucanie elementów bezużytecznych przy każdym przejścia wątku z niezarządzanego do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a0ea3-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a0ea3-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="a0ea3-113">Output</span></span>  
 <span data-ttu-id="a0ea3-114">To zdarzenie MDA nie generuje danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a0ea3-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a0ea3-115">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a0ea3-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0ea3-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0ea3-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a0ea3-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="a0ea3-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a0ea3-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="a0ea3-118">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="a0ea3-119">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="a0ea3-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
