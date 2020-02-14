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
ms.openlocfilehash: 8acafcc2fba9a7d30cc77f25f06adaca7c79db32
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217417"
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="532bc-102">invalidApartmentStateChange MDA</span><span class="sxs-lookup"><span data-stu-id="532bc-102">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="532bc-103">Asystent debugowania zarządzanego `invalidApartmentStateChange` (MDS) jest uaktywniany z jednego z dwóch problemów:</span><span class="sxs-lookup"><span data-stu-id="532bc-103">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
- <span data-ttu-id="532bc-104">Podjęto próbę zmiany stanu apartamentu COM wątku, który został już zainicjowany przez COM do innego stanu apartamentu.</span><span class="sxs-lookup"><span data-stu-id="532bc-104">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
- <span data-ttu-id="532bc-105">Stan apartamentu COM wątku zmienia się nieoczekiwanie.</span><span class="sxs-lookup"><span data-stu-id="532bc-105">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="532bc-106">Objawy</span><span class="sxs-lookup"><span data-stu-id="532bc-106">Symptoms</span></span>  
  
- <span data-ttu-id="532bc-107">Stan apartamentu COM wątku nie jest żądaniem.</span><span class="sxs-lookup"><span data-stu-id="532bc-107">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="532bc-108">Może to spowodować, że serwery proxy mają być używane dla składników COM, które mają model wątkowości inny niż bieżący.</span><span class="sxs-lookup"><span data-stu-id="532bc-108">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="532bc-109">To z kolei może spowodować, że <xref:System.InvalidCastException> być zgłaszane podczas wywoływania obiektu COM za pomocą interfejsów, które nie są skonfigurowane do organizowania między komórkami.</span><span class="sxs-lookup"><span data-stu-id="532bc-109">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
- <span data-ttu-id="532bc-110">Stan apartamentu COM wątku jest inny niż oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="532bc-110">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="532bc-111">Może to spowodować <xref:System.Runtime.InteropServices.COMException> z wartością HRESULT RPC_E_WRONG_THREAD, a także <xref:System.InvalidCastException> podczas wykonywania wywołań dla otoki wywołującej (otoka) [środowiska uruchomieniowego](../../standard/native-interop/runtime-callable-wrapper.md) .</span><span class="sxs-lookup"><span data-stu-id="532bc-111">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="532bc-112">Może to spowodować, że pewne składniki COM jednowątkowego są dostępne jednocześnie przez wiele wątków, co może prowadzić do uszkodzenia lub utraty danych.</span><span class="sxs-lookup"><span data-stu-id="532bc-112">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="532bc-113">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="532bc-113">Cause</span></span>  
  
- <span data-ttu-id="532bc-114">Wątek został wcześniej zainicjowany do innego stanu apartamentu COM.</span><span class="sxs-lookup"><span data-stu-id="532bc-114">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="532bc-115">Należy zauważyć, że stan Apartment wątku może być ustawiony jawnie lub niejawnie.</span><span class="sxs-lookup"><span data-stu-id="532bc-115">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="532bc-116">Operacje jawne obejmują Właściwość <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> i metody <xref:System.Threading.Thread.SetApartmentState%2A> i <xref:System.Threading.Thread.TrySetApartmentState%2A>.</span><span class="sxs-lookup"><span data-stu-id="532bc-116">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="532bc-117">Wątek utworzony przy użyciu metody <xref:System.Threading.Thread.Start%2A> jest niejawnie ustawiany na <xref:System.Threading.ApartmentState.MTA>, chyba że <xref:System.Threading.Thread.SetApartmentState%2A> jest wywoływana przed uruchomieniem wątku.</span><span class="sxs-lookup"><span data-stu-id="532bc-117">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="532bc-118">Główny wątek aplikacji jest również niejawnie zainicjowany do <xref:System.Threading.ApartmentState.MTA>, chyba że atrybut <xref:System.STAThreadAttribute> jest określony w metodzie Main.</span><span class="sxs-lookup"><span data-stu-id="532bc-118">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
- <span data-ttu-id="532bc-119">Metoda `CoUninitialize` (lub metoda `CoInitializeEx`) z innym modelem współbieżności jest wywoływana w wątku.</span><span class="sxs-lookup"><span data-stu-id="532bc-119">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="532bc-120">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="532bc-120">Resolution</span></span>  
 <span data-ttu-id="532bc-121">Ustaw stan apartamentu wątku przed rozpoczęciem jego wykonywania lub zastosuj atrybut <xref:System.STAThreadAttribute> lub atrybut <xref:System.MTAThreadAttribute> do głównej metody aplikacji.</span><span class="sxs-lookup"><span data-stu-id="532bc-121">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="532bc-122">W przypadku drugiej przyczyny, najlepiej, kod wywołujący metodę `CoUninitialize` należy zmodyfikować, aby opóźnić wywołanie do momentu zakończenia wątku i nie RCW i ich bazowe składniki COM nadal są używane przez wątek.</span><span class="sxs-lookup"><span data-stu-id="532bc-122">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="532bc-123">Jednakże jeśli nie można zmodyfikować kodu wywołującego metodę `CoUninitialize`, nie należy używać RCW z wątków, które nie zostały zainicjowane w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="532bc-123">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="532bc-124">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="532bc-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="532bc-125">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="532bc-125">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="532bc-126">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="532bc-126">Output</span></span>  
 <span data-ttu-id="532bc-127">Stan apartamentu modelu COM bieżącego wątku oraz stan, który próbuje zastosować kod.</span><span class="sxs-lookup"><span data-stu-id="532bc-127">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="532bc-128">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="532bc-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="532bc-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="532bc-129">Example</span></span>  
 <span data-ttu-id="532bc-130">Poniższy przykład kodu demonstruje sytuację, w której można aktywować to MDA.</span><span class="sxs-lookup"><span data-stu-id="532bc-130">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="532bc-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="532bc-131">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="532bc-132">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="532bc-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="532bc-133">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="532bc-133">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
