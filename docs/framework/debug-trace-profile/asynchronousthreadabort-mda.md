---
title: asynchronousThreadAbort MDA
description: Sprawdź, w jaki sposób Asystent debugowania zarządzanego asynchronousThreadAbort (MDA) jest aktywowany, gdy wątek próbuje wykonać asynchroniczne przerywanie do innego wątku.
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
ms.openlocfilehash: 469372d57d9c21198353d171fec16458691eb25d
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415670"
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="82fbe-103">asynchronousThreadAbort MDA</span><span class="sxs-lookup"><span data-stu-id="82fbe-103">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="82fbe-104">`asynchronousThreadAbort`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy wątek próbuje wprowadzić asynchroniczne przerwanie do innego wątku.</span><span class="sxs-lookup"><span data-stu-id="82fbe-104">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="82fbe-105">Przerwania wątku synchronicznego nie uaktywniają operacji `asynchronousThreadAbort` MDA.</span><span class="sxs-lookup"><span data-stu-id="82fbe-105">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="82fbe-106">Objawy</span><span class="sxs-lookup"><span data-stu-id="82fbe-106">Symptoms</span></span>
 <span data-ttu-id="82fbe-107">Aplikacja uległa awarii z nieobsługiwanym <xref:System.Threading.ThreadAbortException> , gdy główny wątek aplikacji zostanie przerwany.</span><span class="sxs-lookup"><span data-stu-id="82fbe-107">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="82fbe-108">Jeśli aplikacja była nadal wykonywana, konsekwencje mogą być gorsze niż awaria aplikacji, co może spowodować dalsze uszkodzenie danych.</span><span class="sxs-lookup"><span data-stu-id="82fbe-108">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="82fbe-109">Operacje, które mają być niepodzielne, mogły zostać przerwane po częściowym zakończeniu, pozostawiając dane aplikacji w stanie nieprzewidywalnym.</span><span class="sxs-lookup"><span data-stu-id="82fbe-109">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="82fbe-110"><xref:System.Threading.ThreadAbortException>Można generować z pozornie losowych punktów w trakcie wykonywania kodu, często w miejscach, w których wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="82fbe-110">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="82fbe-111">Kod może nie być w stanie obsłużyć takiego wyjątku, co spowodowało uszkodzenie stanu.</span><span class="sxs-lookup"><span data-stu-id="82fbe-111">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="82fbe-112">Objawy mogą się znacznie różnić ze względu na losowość problemu.</span><span class="sxs-lookup"><span data-stu-id="82fbe-112">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="82fbe-113">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="82fbe-113">Cause</span></span>
 <span data-ttu-id="82fbe-114">Kod w jednym wątku nazywany <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metodą w wątku docelowym, aby wprowadzić asynchroniczne przerwanie wątku.</span><span class="sxs-lookup"><span data-stu-id="82fbe-114">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="82fbe-115">Przerywanie wątku jest asynchroniczne, ponieważ kod, który wywołuje wywołanie, <xref:System.Threading.Thread.Abort%2A> działa w innym wątku niż element docelowy operacji Abort.</span><span class="sxs-lookup"><span data-stu-id="82fbe-115">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="82fbe-116">Przerwania wątku synchronicznego nie należy wywoływać problemu, ponieważ wątek wykonujący tę <xref:System.Threading.Thread.Abort%2A> czynność powinien być wykonany tylko w bezpiecznym punkcie kontrolnym, w którym stan aplikacji jest spójny.</span><span class="sxs-lookup"><span data-stu-id="82fbe-116">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="82fbe-117">Asynchroniczny wątek przerywa problem, ponieważ są przetwarzane w nieprzewidywalne punkty w wykonaniu wątku docelowego.</span><span class="sxs-lookup"><span data-stu-id="82fbe-117">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="82fbe-118">Aby tego uniknąć, kod zapisany do uruchomienia w wątku, który może zostać przerwany w ten sposób, musi obsłużyć <xref:System.Threading.ThreadAbortException> niemal każdy wiersz kodu, zwracając szczególną uwagę na umieszczenie danych aplikacji w spójnym stanie.</span><span class="sxs-lookup"><span data-stu-id="82fbe-118">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="82fbe-119">Nie jest to realistyczne, aby oczekiwać, że kod jest napisany z tym problemem lub napisać kod chroniący przed wszystkimi możliwymi okolicznościami.</span><span class="sxs-lookup"><span data-stu-id="82fbe-119">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="82fbe-120">Wywołania w kodzie niezarządzanym i `finally` bloki nie będą przerywane asynchronicznie, ale natychmiast po zakończeniu z jednej z tych kategorii.</span><span class="sxs-lookup"><span data-stu-id="82fbe-120">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="82fbe-121">Przyczyny problemu mogą być trudne do ustalenia z powodu losowości.</span><span class="sxs-lookup"><span data-stu-id="82fbe-121">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="82fbe-122">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="82fbe-122">Resolution</span></span>
 <span data-ttu-id="82fbe-123">Unikaj projektowania kodu, który wymaga użycia asynchronicznych przerwań wątków.</span><span class="sxs-lookup"><span data-stu-id="82fbe-123">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="82fbe-124">Istnieje kilka metod, które są bardziej odpowiednie dla przerwy w wątku docelowym, które nie wymagają wywołania do <xref:System.Threading.Thread.Abort%2A> .</span><span class="sxs-lookup"><span data-stu-id="82fbe-124">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="82fbe-125">Najbezpieczniejszym jest wprowadzenie mechanizmu, takiego jak Właściwość wspólna, która sygnalizuje wątek docelowy, aby zażądać przerwania.</span><span class="sxs-lookup"><span data-stu-id="82fbe-125">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="82fbe-126">Wątek docelowy sprawdza sygnał z określonych bezpiecznych punktów kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="82fbe-126">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="82fbe-127">Jeśli zażądano przerwania, może ono zostać bezpiecznie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="82fbe-127">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="82fbe-128">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="82fbe-128">Effect on the Runtime</span></span>
 <span data-ttu-id="82fbe-129">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="82fbe-129">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="82fbe-130">Raportuje tylko dane dotyczące przerwań wątków asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="82fbe-130">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="82fbe-131">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="82fbe-131">Output</span></span>
 <span data-ttu-id="82fbe-132">Zdarzenie MDA raportuje identyfikator wątku wykonującego przerwanie i identyfikator wątku, który jest obiektem docelowym przerwania.</span><span class="sxs-lookup"><span data-stu-id="82fbe-132">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="82fbe-133">Te operacje nigdy nie będą takie same, ponieważ są ograniczone do asynchronicznych przerwań.</span><span class="sxs-lookup"><span data-stu-id="82fbe-133">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="82fbe-134">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="82fbe-134">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="82fbe-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="82fbe-135">Example</span></span>
 <span data-ttu-id="82fbe-136">Aktywowanie `asynchronousThreadAbort` MDA wymaga tylko wywołania do <xref:System.Threading.Thread.Abort%2A> oddzielnego działającego wątku.</span><span class="sxs-lookup"><span data-stu-id="82fbe-136">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="82fbe-137">Należy wziąć pod uwagę konsekwencje, jeśli zawartość funkcji uruchamiania wątku była zbiorem bardziej złożonych operacji, które mogą zostać przerwane w dowolnym dowolnym miejscu przez przerwanie.</span><span class="sxs-lookup"><span data-stu-id="82fbe-137">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="82fbe-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82fbe-138">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="82fbe-139">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="82fbe-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
