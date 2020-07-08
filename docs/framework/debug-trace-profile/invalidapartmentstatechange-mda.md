---
title: invalidApartmentStateChange MDA
description: Dowiedz się więcej o programie invalidApartmentStateChange Managed Debug Assistant (MDA) w programie .NET, który jest aktywowany w przypadku problemów ze stanem apartamentu COM.
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
ms.openlocfilehash: c6f7b6a5e450d4167946d22b2ada268ea2b0135f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051830"
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="632cd-103">invalidApartmentStateChange MDA</span><span class="sxs-lookup"><span data-stu-id="632cd-103">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="632cd-104">`invalidApartmentStateChange`Asystent debugowania zarządzanego (MDS) jest uaktywniany z jednego z dwóch problemów:</span><span class="sxs-lookup"><span data-stu-id="632cd-104">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
- <span data-ttu-id="632cd-105">Podjęto próbę zmiany stanu apartamentu COM wątku, który został już zainicjowany przez COM do innego stanu apartamentu.</span><span class="sxs-lookup"><span data-stu-id="632cd-105">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
- <span data-ttu-id="632cd-106">Stan apartamentu COM wątku zmienia się nieoczekiwanie.</span><span class="sxs-lookup"><span data-stu-id="632cd-106">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="632cd-107">Objawy</span><span class="sxs-lookup"><span data-stu-id="632cd-107">Symptoms</span></span>  
  
- <span data-ttu-id="632cd-108">Stan apartamentu COM wątku nie jest żądaniem.</span><span class="sxs-lookup"><span data-stu-id="632cd-108">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="632cd-109">Może to spowodować, że serwery proxy mają być używane dla składników COM, które mają model wątkowości inny niż bieżący.</span><span class="sxs-lookup"><span data-stu-id="632cd-109">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="632cd-110">To z kolei może spowodować, <xref:System.InvalidCastException> że w przypadku wywoływania obiektu com za pomocą interfejsów, które nie są skonfigurowane do organizowania między różnymi komórkami.</span><span class="sxs-lookup"><span data-stu-id="632cd-110">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
- <span data-ttu-id="632cd-111">Stan apartamentu COM wątku jest inny niż oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="632cd-111">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="632cd-112">Może to spowodować, że <xref:System.Runtime.InteropServices.COMException> wynik HRESULT RPC_E_WRONG_THREAD, a także podczas wykonywania <xref:System.InvalidCastException> wywołań dla otoki (RCW) [środowiska uruchomieniowego](../../standard/native-interop/runtime-callable-wrapper.md) .</span><span class="sxs-lookup"><span data-stu-id="632cd-112">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="632cd-113">Może to spowodować, że pewne składniki COM jednowątkowego są dostępne jednocześnie przez wiele wątków, co może prowadzić do uszkodzenia lub utraty danych.</span><span class="sxs-lookup"><span data-stu-id="632cd-113">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="632cd-114">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="632cd-114">Cause</span></span>  
  
- <span data-ttu-id="632cd-115">Wątek został wcześniej zainicjowany do innego stanu apartamentu COM.</span><span class="sxs-lookup"><span data-stu-id="632cd-115">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="632cd-116">Należy zauważyć, że stan Apartment wątku może być ustawiony jawnie lub niejawnie.</span><span class="sxs-lookup"><span data-stu-id="632cd-116">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="632cd-117">Operacje jawne obejmują <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> Właściwość oraz <xref:System.Threading.Thread.SetApartmentState%2A> <xref:System.Threading.Thread.TrySetApartmentState%2A> metody i.</span><span class="sxs-lookup"><span data-stu-id="632cd-117">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="632cd-118">Wątek utworzony przy użyciu <xref:System.Threading.Thread.Start%2A> metody jest niejawnie ustawiony na, <xref:System.Threading.ApartmentState.MTA> chyba że <xref:System.Threading.Thread.SetApartmentState%2A> jest wywoływana przed uruchomieniem wątku.</span><span class="sxs-lookup"><span data-stu-id="632cd-118">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="632cd-119">Główny wątek aplikacji jest również niejawnie zainicjowany, <xref:System.Threading.ApartmentState.MTA> chyba że <xref:System.STAThreadAttribute> atrybut jest określony w metodzie Main.</span><span class="sxs-lookup"><span data-stu-id="632cd-119">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
- <span data-ttu-id="632cd-120">`CoUninitialize`Metoda (lub `CoInitializeEx` Metoda) z innym modelem współbieżności jest wywoływana w wątku.</span><span class="sxs-lookup"><span data-stu-id="632cd-120">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="632cd-121">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="632cd-121">Resolution</span></span>  
 <span data-ttu-id="632cd-122">Ustaw stan apartamentu wątku przed rozpoczęciem jego wykonywania lub Zastosuj <xref:System.STAThreadAttribute> atrybut lub <xref:System.MTAThreadAttribute> atrybut do metody Main aplikacji.</span><span class="sxs-lookup"><span data-stu-id="632cd-122">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="632cd-123">Dla drugiej przyczyny, najlepiej, kod wywołujący `CoUninitialize` metodę należy zmodyfikować tak, aby opóźnić wywołanie do momentu zakończenia wątku, i nie RCW i ich bazowe składniki com nadal są używane przez wątek.</span><span class="sxs-lookup"><span data-stu-id="632cd-123">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="632cd-124">Jednakże jeśli nie można zmodyfikować kodu wywołującego `CoUninitialize` metodę, nie należy używać RCW z wątków, które nie zostały zainicjowane w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="632cd-124">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="632cd-125">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="632cd-125">Effect on the Runtime</span></span>  
 <span data-ttu-id="632cd-126">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="632cd-126">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="632cd-127">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="632cd-127">Output</span></span>  
 <span data-ttu-id="632cd-128">Stan apartamentu modelu COM bieżącego wątku oraz stan, który próbuje zastosować kod.</span><span class="sxs-lookup"><span data-stu-id="632cd-128">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="632cd-129">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="632cd-129">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="632cd-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="632cd-130">Example</span></span>  
 <span data-ttu-id="632cd-131">Poniższy przykład kodu demonstruje sytuację, w której można aktywować to MDA.</span><span class="sxs-lookup"><span data-stu-id="632cd-131">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="632cd-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="632cd-132">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="632cd-133">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="632cd-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="632cd-134">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="632cd-134">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
