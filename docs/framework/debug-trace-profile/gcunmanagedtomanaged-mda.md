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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66f662114868832f909d734a482e1dc9aefb841a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754482"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="e3058-102">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="e3058-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="e3058-103">`gcUnmanagedToManaged` Zarządzanego Asystenta debugowania (MDA) powoduje wyrzucania elementów bezużytecznych, zawsze wtedy, gdy wątku przechodzi z niezarządzane do zarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="e3058-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e3058-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="e3058-104">Symptoms</span></span>  
 <span data-ttu-id="e3058-105">Wywoływanie uruchomione składniki niezarządzane użytkownika za pomocą modelu COM i platformy aplikacji powoduje naruszenie zasad dostępu niedeterministyczne w CLR.</span><span class="sxs-lookup"><span data-stu-id="e3058-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e3058-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="e3058-106">Cause</span></span>  
 <span data-ttu-id="e3058-107">Jeśli aplikacja jest uruchomiona składniki niezarządzane użytkownika, następnie tych składników może mieć uszkodzony stosu odśmieconej pamięci.</span><span class="sxs-lookup"><span data-stu-id="e3058-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="e3058-108">Powoduje naruszenie zasad dostępu w CLR, gdy moduł zbierający elementy bezużyteczne próbuje zapoznaj się z wykresu obiektu.</span><span class="sxs-lookup"><span data-stu-id="e3058-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e3058-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="e3058-109">Resolution</span></span>  
 <span data-ttu-id="e3058-110">Włączenie tego Asystenta skraca czas między po niezarządzanych składnika wykonana spowoduje uszkodzenie stosu odśmieconej pamięci i kiedy naruszenie zasad dostępu ma miejsce wymuszenia wyrzucania elementów bezużytecznych występuje przed każdym Zarządzanie zmianami.</span><span class="sxs-lookup"><span data-stu-id="e3058-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e3058-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e3058-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="e3058-112">Powoduje, że wyrzucania elementów bezużytecznych zawsze wtedy, gdy przejścia wątków, z niezarządzanych w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="e3058-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e3058-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="e3058-113">Output</span></span>  
 <span data-ttu-id="e3058-114">To zdarzenie MDA nie daje żadnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e3058-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e3058-115">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="e3058-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3058-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3058-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e3058-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="e3058-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e3058-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="e3058-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="e3058-119">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="e3058-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
