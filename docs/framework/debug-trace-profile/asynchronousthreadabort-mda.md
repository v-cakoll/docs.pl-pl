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
ms.openlocfilehash: 9bde6f6e625476712c5af516491ab9dd29b7dea3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052962"
---
# <a name="asynchronousthreadabort-mda"></a>asynchronousThreadAbort MDA
Asystent `asynchronousThreadAbort` debugowania zarządzanego (MDA) jest uaktywniany, gdy wątek próbuje wprowadzić asynchroniczne przerwanie do innego wątku. Przerwania wątku synchronicznego nie uaktywniają `asynchronousThreadAbort` operacji MDA.

## <a name="symptoms"></a>Symptomy
 Aplikacja uległa awarii z nieobsługiwanym <xref:System.Threading.ThreadAbortException> , gdy główny wątek aplikacji zostanie przerwany. Jeśli aplikacja była nadal wykonywana, konsekwencje mogą być gorsze niż awaria aplikacji, co może spowodować dalsze uszkodzenie danych.

 Operacje, które mają być niepodzielne, mogły zostać przerwane po częściowym zakończeniu, pozostawiając dane aplikacji w stanie nieprzewidywalnym. <xref:System.Threading.ThreadAbortException> Można generować z pozornie losowych punktów w trakcie wykonywania kodu, często w miejscach, w których wystąpił wyjątek. Kod może nie być w stanie obsłużyć takiego wyjątku, co spowodowało uszkodzenie stanu.

 Objawy mogą się znacznie różnić ze względu na losowość problemu.

## <a name="cause"></a>Przyczyna
 Kod w jednym wątku nazywany <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metodą w wątku docelowym, aby wprowadzić asynchroniczne przerwanie wątku. Przerywanie wątku jest asynchroniczne, ponieważ kod, który wywołuje wywołanie <xref:System.Threading.Thread.Abort%2A> , działa w innym wątku niż element docelowy operacji Abort. Przerwania wątku synchronicznego nie należy wywoływać problemu, ponieważ wątek wykonujący tę <xref:System.Threading.Thread.Abort%2A> czynność powinien być wykonany tylko w bezpiecznym punkcie kontrolnym, w którym stan aplikacji jest spójny.

 Asynchroniczny wątek przerywa problem, ponieważ są przetwarzane w nieprzewidywalne punkty w wykonaniu wątku docelowego. Aby tego uniknąć, kod zapisany do uruchomienia w wątku, który może zostać przerwany w ten sposób, musi obsłużyć <xref:System.Threading.ThreadAbortException> niemal każdy wiersz kodu, zwracając szczególną uwagę na umieszczenie danych aplikacji w spójnym stanie. Nie jest to realistyczne, aby oczekiwać, że kod jest napisany z tym problemem lub napisać kod chroniący przed wszystkimi możliwymi okolicznościami.

 Wywołania w kodzie niezarządzanym i bloki nie będą przerywane asynchronicznie, `finally` ale natychmiast po zakończeniu z jednej z tych kategorii.

 Przyczyny problemu mogą być trudne do ustalenia z powodu losowości.

## <a name="resolution"></a>Rozwiązanie
 Unikaj projektowania kodu, który wymaga użycia asynchronicznych przerwań wątków. Istnieje kilka metod, które są bardziej odpowiednie dla przerwy w wątku docelowym, które nie wymagają wywołania do <xref:System.Threading.Thread.Abort%2A>. Najbezpieczniejszym jest wprowadzenie mechanizmu, takiego jak Właściwość wspólna, która sygnalizuje wątek docelowy, aby zażądać przerwania. Wątek docelowy sprawdza sygnał z określonych bezpiecznych punktów kontrolnych. Jeśli zażądano przerwania, może ono zostać bezpiecznie zamknięte.

## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Raportuje tylko dane dotyczące przerwań wątków asynchronicznych.

## <a name="output"></a>Dane wyjściowe
 Zdarzenie MDA raportuje identyfikator wątku wykonującego przerwanie i identyfikator wątku, który jest obiektem docelowym przerwania. Te operacje nigdy nie będą takie same, ponieważ są ograniczone do asynchronicznych przerwań.

## <a name="configuration"></a>Konfiguracja

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Przykład
 Aktywowanie <xref:System.Threading.Thread.Abort%2A> MDA wymaga tylko wywołania do oddzielnego działającego wątku. `asynchronousThreadAbort` Należy wziąć pod uwagę konsekwencje, jeśli zawartość funkcji uruchamiania wątku była zbiorem bardziej złożonych operacji, które mogą zostać przerwane w dowolnym dowolnym miejscu przez przerwanie.

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

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
