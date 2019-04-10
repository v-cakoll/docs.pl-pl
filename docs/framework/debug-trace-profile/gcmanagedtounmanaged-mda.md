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
ms.openlocfilehash: 7bb4779e300df71a5d075a322bcac8398ce42f34
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204279"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="f22c1-102">gcManagedToUnmanaged MDA</span><span class="sxs-lookup"><span data-stu-id="f22c1-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="f22c1-103">`gcManagedToUnmanaged` Zarządzanego Asystenta debugowania (MDA) powoduje wyrzucania elementów bezużytecznych, zawsze wtedy, gdy wątku przechodzi z kodu zarządzanego do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f22c1-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f22c1-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="f22c1-104">Symptoms</span></span>  
 <span data-ttu-id="f22c1-105">Składnik użytkownika niezarządzanego zgłasza naruszenie zasad dostępu podczas próby użycia obiektu zarządzanego, który ma być narażone na model COM.</span><span class="sxs-lookup"><span data-stu-id="f22c1-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="f22c1-106">Obiekt COM, prawdopodobnie zostały zwolnione.</span><span class="sxs-lookup"><span data-stu-id="f22c1-106">The COM object appears to have been released.</span></span> <span data-ttu-id="f22c1-107">Naruszenie zasad dostępu jest niedeterministyczny.</span><span class="sxs-lookup"><span data-stu-id="f22c1-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f22c1-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="f22c1-108">Cause</span></span>  
 <span data-ttu-id="f22c1-109">Jeśli niezarządzane składnika nie jest zliczanie zarządzanego obiektu COM poprawnie, środowisko uruchomieniowe można zebrać uwidaczniany w modelu COM, gdy składnik niezarządzanych nadal zawiera odwołanie do obiektu zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f22c1-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="f22c1-110">Środowisko uruchomieniowe wywołuje <xref:System.Runtime.InteropServices.Marshal.Release%2A> podczas wyrzucania elementów bezużytecznych, więc jeśli użytkownik składnik używa obiektu, zanim wystąpi wyrzucania elementów bezużytecznych, następnie go będzie nie jeszcze zostać zebrane.</span><span class="sxs-lookup"><span data-stu-id="f22c1-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="f22c1-111">To źródło nondeterminism.</span><span class="sxs-lookup"><span data-stu-id="f22c1-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f22c1-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="f22c1-112">Resolution</span></span>  
 <span data-ttu-id="f22c1-113">Włączenie tego Asystenta skraca czas między po obiekcie kwalifikuje się do kolekcji i <xref:System.Runtime.InteropServices.Marshal.Release%2A> jest wywoływana, pomaga śledzić określają składnik niezarządzanych po raz pierwszy próbuje uzyskać dostępu do obiektu zebrane.</span><span class="sxs-lookup"><span data-stu-id="f22c1-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f22c1-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f22c1-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="f22c1-115">Powoduje, że wyrzucania elementów bezużytecznych zawsze wtedy, gdy przejścia wątków, z kodu zarządzanego do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f22c1-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f22c1-116">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="f22c1-116">Output</span></span>  
 <span data-ttu-id="f22c1-117">To zdarzenie MDA nie daje żadnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f22c1-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f22c1-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="f22c1-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f22c1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f22c1-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f22c1-120">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="f22c1-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f22c1-121">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="f22c1-121">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
- [<span data-ttu-id="f22c1-122">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="f22c1-122">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
