---
title: gcUnmanagedToManaged MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bc02f12a49ef65614114a056f9263f9ef7f5322
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="f7bcb-102">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="f7bcb-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="f7bcb-103">`gcUnmanagedToManaged` Zarządzany Asystent debugowania (MDA) powoduje wyrzucania elementów bezużytecznych zawsze, gdy wątek przejścia z niezarządzanych do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f7bcb-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f7bcb-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="f7bcb-104">Symptoms</span></span>  
 <span data-ttu-id="f7bcb-105">Aplikacji uruchomionej składniki niezarządzane użytkownika przy użyciu platformy i modelu COM. wywołania powoduje naruszenie dostępu niedeterministyczne w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="f7bcb-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f7bcb-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="f7bcb-106">Cause</span></span>  
 <span data-ttu-id="f7bcb-107">Jeśli aplikacja działa składniki niezarządzane użytkownika, następnie te składniki mógł uszkodzony stosu zebranego przez pamięci.</span><span class="sxs-lookup"><span data-stu-id="f7bcb-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="f7bcb-108">Powoduje to naruszenie zasad dostępu w środowisku CLR, gdy moduł garbage collector spróbuje przeprowadzić wykres obiektu.</span><span class="sxs-lookup"><span data-stu-id="f7bcb-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f7bcb-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="f7bcb-109">Resolution</span></span>  
 <span data-ttu-id="f7bcb-110">Włączenie tego Asystenta skraca czas między gdy niezarządzany składnika uszkodzi stosu zebranego przez pamięci i gdy naruszenia zasad dostępu się stanie, wymuszając wyrzucania elementów bezużytecznych występuje przed każdym Zarządzanie zmianami.</span><span class="sxs-lookup"><span data-stu-id="f7bcb-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f7bcb-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f7bcb-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="f7bcb-112">Powoduje, że wyrzucania elementów bezużytecznych zawsze, gdy wątek przejścia z niezarządzanych w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="f7bcb-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f7bcb-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="f7bcb-113">Output</span></span>  
 <span data-ttu-id="f7bcb-114">To zdarzenie MDA tworzy żadnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f7bcb-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f7bcb-115">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="f7bcb-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7bcb-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7bcb-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="f7bcb-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="f7bcb-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="f7bcb-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="f7bcb-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
 [<span data-ttu-id="f7bcb-119">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="f7bcb-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
