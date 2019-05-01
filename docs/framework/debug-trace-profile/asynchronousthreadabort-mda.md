---
title: asynchronousThreadAbort MDA
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08f67ad363d0bd3efcc7a1eeedd1f48d3bae9407
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875709"
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="f1405-102">asynchronousThreadAbort MDA</span><span class="sxs-lookup"><span data-stu-id="f1405-102">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="f1405-103">`asynchronousThreadAbort` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy wątek próbuje wprowadzić asynchronicznego przerwania do innego wątku.</span><span class="sxs-lookup"><span data-stu-id="f1405-103">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="f1405-104">Przerwań synchroniczne wątek nie zostanie aktywowany `asynchronousThreadAbort` MDA.</span><span class="sxs-lookup"><span data-stu-id="f1405-104">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="f1405-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="f1405-105">Symptoms</span></span>
 <span data-ttu-id="f1405-106">Wystąpiła awaria aplikacji przy użyciu nieobsługiwanego <xref:System.Threading.ThreadAbortException> po wątku głównego aplikacji zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="f1405-106">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="f1405-107">Gdyby aplikacja aby kontynuować wykonywanie konsekwencje może być niższa niż aplikacja uległa awarii, przez co więcej uszkodzenie danych.</span><span class="sxs-lookup"><span data-stu-id="f1405-107">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="f1405-108">Należy traktować jako niepodzielne operacje prawdopodobnie zostać przerwane po zakończeniu częściowe, pozostawiając dane aplikacji w nieprzewidywalnym stanie.</span><span class="sxs-lookup"><span data-stu-id="f1405-108">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="f1405-109">Element <xref:System.Threading.ThreadAbortException> może zostać wygenerowany na podstawie pozornie losowe punkty podczas wykonywania kodu, często w miejscach, z których wyjątek nie powinna wystąpić.</span><span class="sxs-lookup"><span data-stu-id="f1405-109">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="f1405-110">Kod może nie być zdolne do obsługi takiego wyjątku, co w stanie uszkodzenia.</span><span class="sxs-lookup"><span data-stu-id="f1405-110">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="f1405-111">Objawy mogą się znacznie zmieniać z powodu losowości związane z problemem.</span><span class="sxs-lookup"><span data-stu-id="f1405-111">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="f1405-112">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="f1405-112">Cause</span></span>
 <span data-ttu-id="f1405-113">Kod w jeden wątek nazywane <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metodę na jeden wątek docelowy wprowadzenie przerwanie asynchronicznego wątku.</span><span class="sxs-lookup"><span data-stu-id="f1405-113">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="f1405-114">Przerwanie wątku jest asynchroniczne, ponieważ kod sprawia to, że wywołanie <xref:System.Threading.Thread.Abort%2A> jest uruchomiona w innym wątku niż obiekt docelowy operacji przerywania.</span><span class="sxs-lookup"><span data-stu-id="f1405-114">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="f1405-115">Przerwanie wątku synchroniczne nie powinno powodować problem, ponieważ wykonywanie wątku <xref:System.Threading.Thread.Abort%2A> powinna mieć wykonana tylko na bezpiecznego punktu kontrolnego, gdzie stan aplikacji jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="f1405-115">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="f1405-116">Przerwanie asynchronicznego wątku powodują problemu, ponieważ są przetwarzane w nieprzewidywalnych punktach wykonywania wątek docelowy.</span><span class="sxs-lookup"><span data-stu-id="f1405-116">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="f1405-117">Aby tego uniknąć, kod napisany do uruchamiania w wątku, który może być przerwana w ten sposób będzie konieczna Obsługa <xref:System.Threading.ThreadAbortException> w prawie każdym wierszu kodu, zwracając szczególną uwagę na odłożyć dane aplikacji do stanu spójności.</span><span class="sxs-lookup"><span data-stu-id="f1405-117">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="f1405-118">Nie jest realistyczne kodu ma zostać zapisany w rozwiązaniu tego problemu należy pamiętać, lub napisać kod, który chroni przed wszystkich możliwych okolicznościach.</span><span class="sxs-lookup"><span data-stu-id="f1405-118">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="f1405-119">Wywołania kodu niezarządzanego i `finally` bloki nie zostanie przerwane asynchronicznie, ale od razu po wyjściu z jednej z tych kategorii.</span><span class="sxs-lookup"><span data-stu-id="f1405-119">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="f1405-120">Przyczyną może być trudno określić, z powodu losowości związane z problemem.</span><span class="sxs-lookup"><span data-stu-id="f1405-120">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="f1405-121">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="f1405-121">Resolution</span></span>
 <span data-ttu-id="f1405-122">Należy unikać projekt kodu, który wymaga użycia przerwanie asynchronicznego wątku.</span><span class="sxs-lookup"><span data-stu-id="f1405-122">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="f1405-123">Istnieje kilka metod są bardziej odpowiednie dla przeszkód wątek docelowy, który nie wymaga wywołania <xref:System.Threading.Thread.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1405-123">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="f1405-124">Najbezpieczniejsze jest wprowadzenie mechanizmu, takiego jak wspólnej właściwości, który sygnalizuje wątek docelowy żądania przerwania.</span><span class="sxs-lookup"><span data-stu-id="f1405-124">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="f1405-125">Sprawdza, czy wątek docelowy sygnał niektórych bezpieczne punkty kontrolne.</span><span class="sxs-lookup"><span data-stu-id="f1405-125">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="f1405-126">Jeśli powiadomienia go, czy wysłano żądanie przerwania, może zostać zamknięty zostanie wyłączone poprawnie.</span><span class="sxs-lookup"><span data-stu-id="f1405-126">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="f1405-127">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f1405-127">Effect on the Runtime</span></span>
 <span data-ttu-id="f1405-128">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="f1405-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="f1405-129">Informuje jedynie dane o przerwanie asynchronicznego wątku.</span><span class="sxs-lookup"><span data-stu-id="f1405-129">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="f1405-130">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="f1405-130">Output</span></span>
 <span data-ttu-id="f1405-131">MDA raportów, identyfikator wątku wykonującego przerwania i identyfikator wątku, który jest elementem docelowym przerwanie.</span><span class="sxs-lookup"><span data-stu-id="f1405-131">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="f1405-132">Nigdy nie będą takie same, ponieważ jest ograniczona do asynchronicznego przerwania.</span><span class="sxs-lookup"><span data-stu-id="f1405-132">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="f1405-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="f1405-133">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="f1405-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1405-134">Example</span></span>
 <span data-ttu-id="f1405-135">Aktywowanie `asynchronousThreadAbort` MDA wymaga tylko wywołania <xref:System.Threading.Thread.Abort%2A> w oddzielnym wątku uruchomione.</span><span class="sxs-lookup"><span data-stu-id="f1405-135">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="f1405-136">Należy rozważyć konsekwencje, jeśli zawartość wątku Uruchom funkcję były zbiór bardziej złożonych operacji, które może zostać przerwane w dowolnym momencie dowolnego za przerwanie.</span><span class="sxs-lookup"><span data-stu-id="f1405-136">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f1405-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1405-137">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="f1405-138">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="f1405-138">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
