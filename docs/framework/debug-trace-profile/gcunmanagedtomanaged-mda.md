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
ms.openlocfilehash: c99ae7d222db2e44de471eb9a41fed614362e300
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614383"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="887a8-102">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="887a8-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="887a8-103">`gcUnmanagedToManaged` Zarządzanego Asystenta debugowania (MDA) powoduje wyrzucania elementów bezużytecznych, zawsze wtedy, gdy wątku przechodzi z niezarządzane do zarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="887a8-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="887a8-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="887a8-104">Symptoms</span></span>  
 <span data-ttu-id="887a8-105">Wywoływanie uruchomione składniki niezarządzane użytkownika za pomocą modelu COM i platformy aplikacji powoduje naruszenie zasad dostępu niedeterministyczne w CLR.</span><span class="sxs-lookup"><span data-stu-id="887a8-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="887a8-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="887a8-106">Cause</span></span>  
 <span data-ttu-id="887a8-107">Jeśli aplikacja jest uruchomiona składniki niezarządzane użytkownika, następnie tych składników może mieć uszkodzony stosu odśmieconej pamięci.</span><span class="sxs-lookup"><span data-stu-id="887a8-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="887a8-108">Powoduje naruszenie zasad dostępu w CLR, gdy moduł zbierający elementy bezużyteczne próbuje zapoznaj się z wykresu obiektu.</span><span class="sxs-lookup"><span data-stu-id="887a8-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="887a8-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="887a8-109">Resolution</span></span>  
 <span data-ttu-id="887a8-110">Włączenie tego Asystenta skraca czas między po niezarządzanych składnika wykonana spowoduje uszkodzenie stosu odśmieconej pamięci i kiedy naruszenie zasad dostępu ma miejsce wymuszenia wyrzucania elementów bezużytecznych występuje przed każdym Zarządzanie zmianami.</span><span class="sxs-lookup"><span data-stu-id="887a8-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="887a8-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="887a8-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="887a8-112">Powoduje, że wyrzucania elementów bezużytecznych zawsze wtedy, gdy przejścia wątków, z niezarządzanych w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="887a8-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="887a8-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="887a8-113">Output</span></span>  
 <span data-ttu-id="887a8-114">To zdarzenie MDA nie daje żadnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="887a8-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="887a8-115">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="887a8-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="887a8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="887a8-116">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="887a8-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="887a8-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="887a8-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="887a8-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="887a8-119">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="887a8-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
