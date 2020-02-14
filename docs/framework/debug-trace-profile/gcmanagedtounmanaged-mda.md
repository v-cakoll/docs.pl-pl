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
ms.openlocfilehash: f7e6334e20a6e0db1d52307a833de0ecd0d74cc4
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217476"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="a358d-102">gcManagedToUnmanaged MDA</span><span class="sxs-lookup"><span data-stu-id="a358d-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="a358d-103">Asystent debugowania zarządzanego `gcManagedToUnmanaged` (MDA) powoduje wyrzucanie elementów bezużytecznych za każdym razem, gdy wątek przechodzi z zarządzanego do niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="a358d-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a358d-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="a358d-104">Symptoms</span></span>  
 <span data-ttu-id="a358d-105">Niezarządzany składnik użytkownika zgłasza naruszenie zasad dostępu podczas próby użycia zarządzanego obiektu, który został ujawniony w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="a358d-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="a358d-106">Obiekt COM wydaje się być wystawiony.</span><span class="sxs-lookup"><span data-stu-id="a358d-106">The COM object appears to have been released.</span></span> <span data-ttu-id="a358d-107">Naruszenie zasad dostępu jest niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="a358d-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a358d-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="a358d-108">Cause</span></span>  
 <span data-ttu-id="a358d-109">Jeśli składnik niezarządzany nie odwołuje się prawidłowo do prawidłowego zliczania zarządzanego obiektu COM, środowisko uruchomieniowe może zebrać obiekt zarządzany uwidoczniony do modelu COM, gdy składnik niezarządzany nadal utrzymuje odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="a358d-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="a358d-110">Wywołania środowiska uruchomieniowego <xref:System.Runtime.InteropServices.Marshal.Release%2A> podczas wyrzucania elementów bezużytecznych, więc jeśli składnik użytkownika używa obiektu przed wystąpieniem wyrzucania elementów bezużytecznych, nie został jeszcze zebrany.</span><span class="sxs-lookup"><span data-stu-id="a358d-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="a358d-111">To jest źródło nieustalenia.</span><span class="sxs-lookup"><span data-stu-id="a358d-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a358d-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="a358d-112">Resolution</span></span>  
 <span data-ttu-id="a358d-113">Włączenie tego asystenta skraca czas od momentu, gdy obiekt kwalifikuje się do kolekcji, a <xref:System.Runtime.InteropServices.Marshal.Release%2A> jest wywoływana, pomagając śledzić, który składnik niezarządzany najpierw próbuje uzyskać dostęp do zebranego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a358d-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a358d-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a358d-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="a358d-115">Powoduje wyrzucanie elementów bezużytecznych po każdym przejścia wątku z zarządzanego do niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="a358d-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a358d-116">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="a358d-116">Output</span></span>  
 <span data-ttu-id="a358d-117">To zdarzenie MDA nie generuje danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a358d-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a358d-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a358d-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a358d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a358d-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a358d-120">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="a358d-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a358d-121">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="a358d-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="a358d-122">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="a358d-122">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
