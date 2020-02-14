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
ms.openlocfilehash: d0c78e6d52ae4a5b3a24e0bb4278b2e8a1b98751
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217580"
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="ce9c7-102">asynchronousThreadAbort MDA</span><span class="sxs-lookup"><span data-stu-id="ce9c7-102">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="ce9c7-103">Asystent debugowania zarządzanego `asynchronousThreadAbort` (MDA) jest uaktywniany, gdy wątek próbuje wprowadzić asynchroniczne przerwanie do innego wątku.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-103">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="ce9c7-104">Przerwania wątku synchronicznego nie aktywuje `asynchronousThreadAbort` MDA.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-104">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="ce9c7-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="ce9c7-105">Symptoms</span></span>
 <span data-ttu-id="ce9c7-106">Aplikacja ulega awarii z nieobsługiwanym <xref:System.Threading.ThreadAbortException>, gdy główny wątek aplikacji zostanie przerwany.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-106">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="ce9c7-107">Jeśli aplikacja była nadal wykonywana, konsekwencje mogą być gorsze niż awaria aplikacji, co może spowodować dalsze uszkodzenie danych.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-107">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="ce9c7-108">Operacje, które mają być niepodzielne, mogły zostać przerwane po częściowym zakończeniu, pozostawiając dane aplikacji w stanie nieprzewidywalnym.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-108">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="ce9c7-109"><xref:System.Threading.ThreadAbortException> można generować od pozornie losowych punktów w trakcie wykonywania kodu, często w miejscach, w których wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-109">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="ce9c7-110">Kod może nie być w stanie obsłużyć takiego wyjątku, co spowodowało uszkodzenie stanu.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-110">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="ce9c7-111">Objawy mogą się znacznie różnić ze względu na losowość problemu.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-111">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="ce9c7-112">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="ce9c7-112">Cause</span></span>
 <span data-ttu-id="ce9c7-113">Kod w jednym wątku nazywany metodą <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> w wątku docelowym, aby wprowadzić asynchroniczne przerwanie wątku.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-113">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="ce9c7-114">Przerywanie wątku jest asynchroniczne, ponieważ kod, który wywołuje wywołanie <xref:System.Threading.Thread.Abort%2A>, działa w innym wątku niż element docelowy operacji przerwania.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-114">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="ce9c7-115">Przerwania wątku synchronicznego nie należy wywoływać problemu, ponieważ wątek wykonujący <xref:System.Threading.Thread.Abort%2A> powinien wykonać tę czynność tylko w bezpiecznym punkcie kontrolnym, w którym stan aplikacji jest spójny.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-115">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="ce9c7-116">Asynchroniczny wątek przerywa problem, ponieważ są przetwarzane w nieprzewidywalne punkty w wykonaniu wątku docelowego.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-116">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="ce9c7-117">Aby tego uniknąć, kod zapisany do uruchomienia w wątku, który może zostać przerwany w ten sposób, musi obsłużyć <xref:System.Threading.ThreadAbortException> niemal każdy wiersz kodu, zwracając szczególną uwagę na umieszczenie danych aplikacji w spójnym stanie.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-117">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="ce9c7-118">Nie jest to realistyczne, aby oczekiwać, że kod jest napisany z tym problemem lub napisać kod chroniący przed wszystkimi możliwymi okolicznościami.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-118">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="ce9c7-119">Wywołania w kodzie niezarządzanym i bloków `finally` nie będą przerywane asynchronicznie, ale natychmiast po zakończeniu z jednej z tych kategorii.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-119">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="ce9c7-120">Przyczyny problemu mogą być trudne do ustalenia z powodu losowości.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-120">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="ce9c7-121">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ce9c7-121">Resolution</span></span>
 <span data-ttu-id="ce9c7-122">Unikaj projektowania kodu, który wymaga użycia asynchronicznych przerwań wątków.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-122">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="ce9c7-123">Istnieje kilka metod, które są bardziej odpowiednie dla przerwania wątku docelowego, które nie wymagają wywołania do <xref:System.Threading.Thread.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-123">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="ce9c7-124">Najbezpieczniejszym jest wprowadzenie mechanizmu, takiego jak Właściwość wspólna, która sygnalizuje wątek docelowy, aby zażądać przerwania.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-124">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="ce9c7-125">Wątek docelowy sprawdza sygnał z określonych bezpiecznych punktów kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-125">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="ce9c7-126">Jeśli zażądano przerwania, może ono zostać bezpiecznie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-126">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="ce9c7-127">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ce9c7-127">Effect on the Runtime</span></span>
 <span data-ttu-id="ce9c7-128">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="ce9c7-129">Raportuje tylko dane dotyczące przerwań wątków asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-129">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="ce9c7-130">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="ce9c7-130">Output</span></span>
 <span data-ttu-id="ce9c7-131">Zdarzenie MDA raportuje identyfikator wątku wykonującego przerwanie i identyfikator wątku, który jest obiektem docelowym przerwania.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-131">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="ce9c7-132">Te operacje nigdy nie będą takie same, ponieważ są ograniczone do asynchronicznych przerwań.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-132">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="ce9c7-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ce9c7-133">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="ce9c7-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce9c7-134">Example</span></span>
 <span data-ttu-id="ce9c7-135">Aktywowanie `asynchronousThreadAbort` MDA wymaga tylko wywołania do <xref:System.Threading.Thread.Abort%2A> w oddzielnym działaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-135">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="ce9c7-136">Należy wziąć pod uwagę konsekwencje, jeśli zawartość funkcji uruchamiania wątku była zbiorem bardziej złożonych operacji, które mogą zostać przerwane w dowolnym dowolnym miejscu przez przerwanie.</span><span class="sxs-lookup"><span data-stu-id="ce9c7-136">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ce9c7-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce9c7-137">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="ce9c7-138">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="ce9c7-138">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
