---
title: invalidApartmentStateChange MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0540b10f2480c173dde1f72759e7f30a65bc382
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626579"
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="92472-102">invalidApartmentStateChange MDA</span><span class="sxs-lookup"><span data-stu-id="92472-102">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="92472-103">`invalidApartmentStateChange` Zarządzanego Asystenta debugowania (MDS) została aktywowana przy użyciu jednej z dwa problemy:</span><span class="sxs-lookup"><span data-stu-id="92472-103">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
-   <span data-ttu-id="92472-104">Aby zmienić stan apartamentu COM wątku, który został już zainicjowany przez model COM do stanu różnych apartamentu zostanie podjęta próba.</span><span class="sxs-lookup"><span data-stu-id="92472-104">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
-   <span data-ttu-id="92472-105">Stan apartamentu COM wątek nieoczekiwanie ulega zmianie.</span><span class="sxs-lookup"><span data-stu-id="92472-105">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="92472-106">Symptomy</span><span class="sxs-lookup"><span data-stu-id="92472-106">Symptoms</span></span>  
  
-   <span data-ttu-id="92472-107">Stan apartamentu COM wątku jest nie żądano.</span><span class="sxs-lookup"><span data-stu-id="92472-107">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="92472-108">Może to spowodować, że serwery proxy ma być używany dla składników modelu COM, które mają inny niż bieżący model wątkowości.</span><span class="sxs-lookup"><span data-stu-id="92472-108">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="92472-109">To z kolei może spowodować, że <xref:System.InvalidCastException> zostanie wygenerowany podczas wywoływania obiektu COM za pomocą interfejsów, które nie są skonfigurowane do szeregowanie między apartamentu.</span><span class="sxs-lookup"><span data-stu-id="92472-109">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
-   <span data-ttu-id="92472-110">Stan apartamentu COM wątku jest inny niż oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="92472-110">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="92472-111">Może to spowodować <xref:System.Runtime.InteropServices.COMException> z HRESULT RPC_E_WRONG_THREAD, a także <xref:System.InvalidCastException> podczas wprowadzania wzywa [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="92472-111">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="92472-112">Może to również spowodować niektóre jednowątkowe składniki COM można uzyskać dostęp przez wiele wątków, w tym samym czasie, co może prowadzić do uszkodzenia lub utraty danych.</span><span class="sxs-lookup"><span data-stu-id="92472-112">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="92472-113">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="92472-113">Cause</span></span>  
  
-   <span data-ttu-id="92472-114">Wątek był poprzednio inicjowany do innego stanu apartamentu COM.</span><span class="sxs-lookup"><span data-stu-id="92472-114">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="92472-115">Należy pamiętać, że stan apartamentu wątku można ustawić jawnie lub niejawnie.</span><span class="sxs-lookup"><span data-stu-id="92472-115">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="92472-116">Jawne operacje obejmują <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> właściwości i <xref:System.Threading.Thread.SetApartmentState%2A> i <xref:System.Threading.Thread.TrySetApartmentState%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="92472-116">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="92472-117">Wątek utworzone za pomocą <xref:System.Threading.Thread.Start%2A> niejawnie ustawiono metodę <xref:System.Threading.ApartmentState.MTA> chyba że <xref:System.Threading.Thread.SetApartmentState%2A> jest wywoływana przed wątek jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="92472-117">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="92472-118">Dodatkowo niejawnie zainicjowaniu wątku głównego aplikacji <xref:System.Threading.ApartmentState.MTA> chyba że <xref:System.STAThreadAttribute> atrybut jest określony w metodzie głównej.</span><span class="sxs-lookup"><span data-stu-id="92472-118">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
-   <span data-ttu-id="92472-119">`CoUninitialize` — Metoda (lub `CoInitializeEx` metoda) ze współbieżnością inny model jest wywoływana w wątku.</span><span class="sxs-lookup"><span data-stu-id="92472-119">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="92472-120">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="92472-120">Resolution</span></span>  
 <span data-ttu-id="92472-121">Ustaw stan apartamentu wątku, przed rozpoczęciem, wykonania lub zastosować jedną <xref:System.STAThreadAttribute> atrybutu lub <xref:System.MTAThreadAttribute> atrybutu do metody głównej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="92472-121">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="92472-122">Drugi przyczynę najlepiej, jeśli kod wywołująca `CoUninitialize` metody należy zmodyfikować, aby opóźnić wywołanie, aż wątek się zakończyć i nie ma żadnych RCW i komponentów COM nadal używany przez wątek.</span><span class="sxs-lookup"><span data-stu-id="92472-122">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="92472-123">Jednakże jeśli nie jest możliwe zmodyfikować kod, który wywołuje `CoUninitialize` metody, a następnie RCW nie powinny być używane z wątków, które są niezainicjowana w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="92472-123">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="92472-124">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="92472-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="92472-125">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="92472-125">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="92472-126">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="92472-126">Output</span></span>  
 <span data-ttu-id="92472-127">Stan apartamentu COM bieżącego wątku, a stan, który próbowano zastosować kodu.</span><span class="sxs-lookup"><span data-stu-id="92472-127">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="92472-128">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="92472-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="92472-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="92472-129">Example</span></span>  
 <span data-ttu-id="92472-130">W poniższym przykładzie kodu pokazano sytuację, która może aktywować to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="92472-130">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
```csharp
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="92472-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92472-131">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="92472-132">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="92472-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="92472-133">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="92472-133">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
