---
title: gcManagedToUnmanaged MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: add5ba59f8f59fc013f8c04a186b34e711c1490c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537936"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="52a7d-102">gcManagedToUnmanaged MDA</span><span class="sxs-lookup"><span data-stu-id="52a7d-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="52a7d-103">`gcManagedToUnmanaged` Zarządzanego Asystenta debugowania (MDA) powoduje wyrzucania elementów bezużytecznych, zawsze wtedy, gdy wątku przechodzi z kodu zarządzanego do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="52a7d-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="52a7d-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="52a7d-104">Symptoms</span></span>  
 <span data-ttu-id="52a7d-105">Składnik użytkownika niezarządzanego zgłasza naruszenie zasad dostępu podczas próby użycia obiektu zarządzanego, który ma być narażone na model COM.</span><span class="sxs-lookup"><span data-stu-id="52a7d-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="52a7d-106">Obiekt COM, prawdopodobnie zostały zwolnione.</span><span class="sxs-lookup"><span data-stu-id="52a7d-106">The COM object appears to have been released.</span></span> <span data-ttu-id="52a7d-107">Naruszenie zasad dostępu jest niedeterministyczny.</span><span class="sxs-lookup"><span data-stu-id="52a7d-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="52a7d-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="52a7d-108">Cause</span></span>  
 <span data-ttu-id="52a7d-109">Jeśli niezarządzane składnika nie jest zliczanie zarządzanego obiektu COM poprawnie, środowisko uruchomieniowe można zebrać uwidaczniany w modelu COM, gdy składnik niezarządzanych nadal zawiera odwołanie do obiektu zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="52a7d-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="52a7d-110">Środowisko uruchomieniowe wywołuje <xref:System.Runtime.InteropServices.Marshal.Release%2A> podczas wyrzucania elementów bezużytecznych, więc jeśli użytkownik składnik używa obiektu, zanim wystąpi wyrzucania elementów bezużytecznych, następnie go będzie nie jeszcze zostać zebrane.</span><span class="sxs-lookup"><span data-stu-id="52a7d-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="52a7d-111">To źródło nondeterminism.</span><span class="sxs-lookup"><span data-stu-id="52a7d-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="52a7d-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="52a7d-112">Resolution</span></span>  
 <span data-ttu-id="52a7d-113">Włączenie tego Asystenta skraca czas między po obiekcie kwalifikuje się do kolekcji i <xref:System.Runtime.InteropServices.Marshal.Release%2A> jest wywoływana, pomaga śledzić określają składnik niezarządzanych po raz pierwszy próbuje uzyskać dostępu do obiektu zebrane.</span><span class="sxs-lookup"><span data-stu-id="52a7d-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="52a7d-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="52a7d-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="52a7d-115">Powoduje, że wyrzucania elementów bezużytecznych zawsze wtedy, gdy przejścia wątków, z kodu zarządzanego do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="52a7d-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="52a7d-116">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="52a7d-116">Output</span></span>  
 <span data-ttu-id="52a7d-117">To zdarzenie MDA nie daje żadnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="52a7d-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="52a7d-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="52a7d-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="52a7d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52a7d-119">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="52a7d-120">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="52a7d-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="52a7d-121">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="52a7d-121">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
- [<span data-ttu-id="52a7d-122">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="52a7d-122">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
