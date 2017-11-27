---
title: asynchronousThreadAbort MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6f7bfee4375a14a4456493333e65a953d406c732
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="4d546-102">asynchronousThreadAbort MDA</span><span class="sxs-lookup"><span data-stu-id="4d546-102">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="4d546-103">`asynchronousThreadAbort` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy wątek podejmuje próbę wprowadzenia asynchronicznego przerwania do innego wątku.</span><span class="sxs-lookup"><span data-stu-id="4d546-103">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="4d546-104">Przerywa synchroniczne wątek nie zostanie aktywowany `asynchronousThreadAbort` MDA.</span><span class="sxs-lookup"><span data-stu-id="4d546-104">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="4d546-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="4d546-105">Symptoms</span></span>
 <span data-ttu-id="4d546-106">Wystąpiła awaria aplikacji z nieobsługiwanym <xref:System.Threading.ThreadAbortException> po wątku głównego aplikacji zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="4d546-106">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="4d546-107">Jeżeli aplikacja kontynuować jego wykonywanie, konsekwencje może być gorsza niż aplikacja awarii, co prawdopodobnie spowoduje dalsze uszkodzenia danych.</span><span class="sxs-lookup"><span data-stu-id="4d546-107">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="4d546-108">Operacje przeznaczone do niepodzielnych prawdopodobnie zostać przerwane po zakończeniu częściowe, pozostawiając dane aplikacji w nieprzewidywalnym stanie.</span><span class="sxs-lookup"><span data-stu-id="4d546-108">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="4d546-109">A <xref:System.Threading.ThreadAbortException> mogą być generowane z pozornie losowe punktów podczas wykonywania kodu, często w miejscach, z których wyjątek nie powinno wystąpić.</span><span class="sxs-lookup"><span data-stu-id="4d546-109">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="4d546-110">Kod może nie być może obsługiwać takiego wyjątku, co w stanie uszkodzenia.</span><span class="sxs-lookup"><span data-stu-id="4d546-110">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="4d546-111">Objawy różnią może z powodu problemu związanego z używaniem losowości.</span><span class="sxs-lookup"><span data-stu-id="4d546-111">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="4d546-112">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="4d546-112">Cause</span></span>
 <span data-ttu-id="4d546-113">Kod w jeden wątek o nazwie <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody na wątek docelowy wprowadzenie przerwanie asynchronicznego wątku.</span><span class="sxs-lookup"><span data-stu-id="4d546-113">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="4d546-114">Przerwij wątku jest asynchroniczne, ponieważ kod, który wykonuje wywołanie do <xref:System.Threading.Thread.Abort%2A> jest uruchomiona w innym wątku niż docelowy operacji przerwania.</span><span class="sxs-lookup"><span data-stu-id="4d546-114">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="4d546-115">Przerywa wątku synchroniczne nie powinny powodować problem, ponieważ wykonywanie wątku <xref:System.Threading.Thread.Abort%2A> powinna mieć wykonana tylko na bezpiecznych punkt kontrolny, gdzie stan aplikacji jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="4d546-115">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="4d546-116">Przerwanie asynchronicznego wątku powodują problemu, ponieważ zostały one przetworzone w punktach nieprzewidywalne podczas wykonywania wątku docelowej.</span><span class="sxs-lookup"><span data-stu-id="4d546-116">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="4d546-117">Aby tego uniknąć, należy obsługiwać kodu napisanego w celu uruchamiania w wątku, który może zostać przerwane w ten sposób <xref:System.Threading.ThreadAbortException> w niemal każdego wiersza kodu, zwracając szczególną uwagę na odłożyć dane aplikacji do stanu spójności.</span><span class="sxs-lookup"><span data-stu-id="4d546-117">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="4d546-118">Nie jest realistyczne kodu ma zostać zapisany z tym problemem, pamiętając, lub do pisania kodu, która chroni przed wszystkich możliwych okolicznościach.</span><span class="sxs-lookup"><span data-stu-id="4d546-118">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="4d546-119">Wywołania do kodu niezarządzanego i `finally` bloków nie zostanie przerwana asynchronicznie, ale natychmiast po wyjściu z jednej z tych kategorii.</span><span class="sxs-lookup"><span data-stu-id="4d546-119">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="4d546-120">Przyczyną może być trudne do ustalenia, z powodu problemu związanego z używaniem losowości.</span><span class="sxs-lookup"><span data-stu-id="4d546-120">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="4d546-121">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="4d546-121">Resolution</span></span>
 <span data-ttu-id="4d546-122">Unikaj projekt kodu, który wymaga użycia przerwanie asynchronicznego wątku.</span><span class="sxs-lookup"><span data-stu-id="4d546-122">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="4d546-123">Istnieje kilka rozwiązań bardziej odpowiednie dla przerwom w wykonywaniu wątku docelowego, który nie wymaga wywołania <xref:System.Threading.Thread.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d546-123">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="4d546-124">Najbezpieczniejsze jest wprowadzenie mechanizmu, takiego jak wspólnej właściwości, która sygnalizuje wątek docelowy żądanie przerwania.</span><span class="sxs-lookup"><span data-stu-id="4d546-124">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="4d546-125">Wątek docelowy sprawdza sygnał niektórych bezpieczne punkty kontrolne.</span><span class="sxs-lookup"><span data-stu-id="4d546-125">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="4d546-126">Jeśli powiadomienia go, że zażądano przerwania, może zostać zamknięty bezpiecznie zamknąć.</span><span class="sxs-lookup"><span data-stu-id="4d546-126">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="4d546-127">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="4d546-127">Effect on the Runtime</span></span>
 <span data-ttu-id="4d546-128">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="4d546-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="4d546-129">Zwraca tylko dane o przerwanie asynchronicznego wątku.</span><span class="sxs-lookup"><span data-stu-id="4d546-129">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="4d546-130">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="4d546-130">Output</span></span>
 <span data-ttu-id="4d546-131">MDA zgłasza identyfikator wątku, przerwanie i identyfikator wątku, który jest elementem docelowym przerwanie.</span><span class="sxs-lookup"><span data-stu-id="4d546-131">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="4d546-132">Nigdy nie będą takie same, ponieważ jest ograniczone do asynchronicznego przerwania.</span><span class="sxs-lookup"><span data-stu-id="4d546-132">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="4d546-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="4d546-133">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="4d546-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d546-134">Example</span></span>
 <span data-ttu-id="4d546-135">Aktywowanie `asynchronousThreadAbort` MDA wymaga tylko wywołania <xref:System.Threading.Thread.Abort%2A> na oddzielnych uruchomiony wątek.</span><span class="sxs-lookup"><span data-stu-id="4d546-135">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="4d546-136">Jeśli zawartość wątku uruchomienia funkcji zostały zbiór bardziej złożonych czynności, które może zostać przerwane w dowolnym momencie dowolnego przez przerwanie, należy wziąć pod uwagę skutki.</span><span class="sxs-lookup"><span data-stu-id="4d546-136">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

```csharp
using System.Threading;
void FireMda()
{
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });
    t.Start();
    // The following line activates the MDA.
    t.Abort();
    t.Join();
}
```

## <a name="see-also"></a><span data-ttu-id="4d546-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d546-137">See Also</span></span>
 <span data-ttu-id="4d546-138"><xref:System.Threading.Thread>[Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)</span><span class="sxs-lookup"><span data-stu-id="4d546-138"><xref:System.Threading.Thread> [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)</span></span>
