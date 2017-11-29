---
title: invalidApartmentStateChange MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71634018e42ad66fdd2d03d0b0d496394cde801e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="9afd2-102">invalidApartmentStateChange MDA</span><span class="sxs-lookup"><span data-stu-id="9afd2-102">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="9afd2-103">`invalidApartmentStateChange` Asystent debugowania zarządzanego (MDS) jest aktywowany przy użyciu jednej z dwóch problemów:</span><span class="sxs-lookup"><span data-stu-id="9afd2-103">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
-   <span data-ttu-id="9afd2-104">Aby zmienić stan apartamentu COM wątku, który został już zainicjowany przez model COM do stanu apartamentu różnych podejmowana jest próba.</span><span class="sxs-lookup"><span data-stu-id="9afd2-104">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
-   <span data-ttu-id="9afd2-105">Nieoczekiwana zmiana stanu apartamentu com. wątku.</span><span class="sxs-lookup"><span data-stu-id="9afd2-105">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9afd2-106">Symptomy</span><span class="sxs-lookup"><span data-stu-id="9afd2-106">Symptoms</span></span>  
  
-   <span data-ttu-id="9afd2-107">Stanem apartamentu COM wątku jest nie żądano.</span><span class="sxs-lookup"><span data-stu-id="9afd2-107">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="9afd2-108">Może to spowodować, że serwery proxy do użycia dla składników COM, które ma inny niż bieżący model wątkowości.</span><span class="sxs-lookup"><span data-stu-id="9afd2-108">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="9afd2-109">To z kolei może spowodować <xref:System.InvalidCastException> zostanie wygenerowany podczas wywoływania obiektu COM za pomocą interfejsów, które nie są skonfigurowane dla typu apartment między przekazywanie.</span><span class="sxs-lookup"><span data-stu-id="9afd2-109">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
-   <span data-ttu-id="9afd2-110">Stanem apartamentu COM wątku jest inny niż oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="9afd2-110">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="9afd2-111">Może to spowodować <xref:System.Runtime.InteropServices.COMException> z HRESULT RPC_E_WRONG_THREAD, jak również <xref:System.InvalidCastException> podczas wprowadzania wywołuje w [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (otoki RCW).</span><span class="sxs-lookup"><span data-stu-id="9afd2-111">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="9afd2-112">Może to spowodować także niektóre jednowątkowe składniki COM można uzyskać dostęp przez wiele wątków jednocześnie, co może prowadzić do uszkodzenia lub utraty danych.</span><span class="sxs-lookup"><span data-stu-id="9afd2-112">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9afd2-113">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="9afd2-113">Cause</span></span>  
  
-   <span data-ttu-id="9afd2-114">Wątek był poprzednio inicjowany do innego stanu apartamentu COM.</span><span class="sxs-lookup"><span data-stu-id="9afd2-114">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="9afd2-115">Należy pamiętać, że można ustawić stanu apartamentu wątku jawnie lub niejawnie.</span><span class="sxs-lookup"><span data-stu-id="9afd2-115">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="9afd2-116">Jawne operacji zalicza się <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> właściwości i <xref:System.Threading.Thread.SetApartmentState%2A> i <xref:System.Threading.Thread.TrySetApartmentState%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9afd2-116">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="9afd2-117">Wątek, który został utworzony przy użyciu <xref:System.Threading.Thread.Start%2A> niejawnie ustawiono metodę <xref:System.Threading.ApartmentState.MTA> chyba że <xref:System.Threading.Thread.SetApartmentState%2A> jest wywoływana przed wątek jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="9afd2-117">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="9afd2-118">Można również niejawnie zainicjowano wątku głównego aplikacji <xref:System.Threading.ApartmentState.MTA> chyba że <xref:System.STAThreadAttribute> atrybut został określony dla metody main.</span><span class="sxs-lookup"><span data-stu-id="9afd2-118">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
-   <span data-ttu-id="9afd2-119">`CoUninitialize` — Metoda (lub `CoInitializeEx` metody) z różnych współbieżności modelu jest wywoływana w wątku.</span><span class="sxs-lookup"><span data-stu-id="9afd2-119">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9afd2-120">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="9afd2-120">Resolution</span></span>  
 <span data-ttu-id="9afd2-121">Ustawienie stanu apartamentu wątku, przed rozpoczęciem wykonywania lub zastosować jedną <xref:System.STAThreadAttribute> atrybutu lub <xref:System.MTAThreadAttribute> atrybut do metody głównej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9afd2-121">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="9afd2-122">Drugi Przyczyna najlepiej, jeśli kod, który odwołuje się `CoUninitialize` metody powinien zostać zmodyfikowany opóźnienia wywołanie, dopóki nie ma zakończenie wątku i nie ma żadnych RCWs i komponentów COM nadal używany przez wątek.</span><span class="sxs-lookup"><span data-stu-id="9afd2-122">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="9afd2-123">Jednak jeśli nie jest możliwe zmodyfikować kod, który wywołuje `CoUninitialize` metody, a następnie RCWs nie powinien być używany z wątków, które są odinicjowany w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="9afd2-123">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9afd2-124">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="9afd2-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="9afd2-125">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="9afd2-125">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9afd2-126">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="9afd2-126">Output</span></span>  
 <span data-ttu-id="9afd2-127">Stanem apartamentu COM bieżącego wątku i próbował wprowadzić kod stanu.</span><span class="sxs-lookup"><span data-stu-id="9afd2-127">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9afd2-128">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="9afd2-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9afd2-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="9afd2-129">Example</span></span>  
 <span data-ttu-id="9afd2-130">W poniższym przykładzie kodu pokazano sytuację, której można uaktywnić to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="9afd2-130">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="9afd2-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9afd2-131">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="9afd2-132">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="9afd2-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="9afd2-133">Przekazywanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="9afd2-133">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
