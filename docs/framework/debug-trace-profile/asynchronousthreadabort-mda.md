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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59114900"
---
# <a name="asynchronousthreadabort-mda"></a>asynchronousThreadAbort MDA
`asynchronousThreadAbort` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy wątek próbuje wprowadzić asynchronicznego przerwania do innego wątku. Przerwań synchroniczne wątek nie zostanie aktywowany `asynchronousThreadAbort` MDA.

## <a name="symptoms"></a>Symptomy
 Wystąpiła awaria aplikacji przy użyciu nieobsługiwanego <xref:System.Threading.ThreadAbortException> po wątku głównego aplikacji zostało przerwane. Gdyby aplikacja aby kontynuować wykonywanie konsekwencje może być niższa niż aplikacja uległa awarii, przez co więcej uszkodzenie danych.

 Należy traktować jako niepodzielne operacje prawdopodobnie zostać przerwane po zakończeniu częściowe, pozostawiając dane aplikacji w nieprzewidywalnym stanie. Element <xref:System.Threading.ThreadAbortException> może zostać wygenerowany na podstawie pozornie losowe punkty podczas wykonywania kodu, często w miejscach, z których wyjątek nie powinna wystąpić. Kod może nie być zdolne do obsługi takiego wyjątku, co w stanie uszkodzenia.

 Objawy mogą się znacznie zmieniać z powodu losowości związane z problemem.

## <a name="cause"></a>Przyczyna
 Kod w jeden wątek nazywane <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metodę na jeden wątek docelowy wprowadzenie przerwanie asynchronicznego wątku. Przerwanie wątku jest asynchroniczne, ponieważ kod sprawia to, że wywołanie <xref:System.Threading.Thread.Abort%2A> jest uruchomiona w innym wątku niż obiekt docelowy operacji przerywania. Przerwanie wątku synchroniczne nie powinno powodować problem, ponieważ wykonywanie wątku <xref:System.Threading.Thread.Abort%2A> powinna mieć wykonana tylko na bezpiecznego punktu kontrolnego, gdzie stan aplikacji jest zgodny.

 Przerwanie asynchronicznego wątku powodują problemu, ponieważ są przetwarzane w nieprzewidywalnych punktach wykonywania wątek docelowy. Aby tego uniknąć, kod napisany do uruchamiania w wątku, który może być przerwana w ten sposób będzie konieczna Obsługa <xref:System.Threading.ThreadAbortException> w prawie każdym wierszu kodu, zwracając szczególną uwagę na odłożyć dane aplikacji do stanu spójności. Nie jest realistyczne kodu ma zostać zapisany w rozwiązaniu tego problemu należy pamiętać, lub napisać kod, który chroni przed wszystkich możliwych okolicznościach.

 Wywołania kodu niezarządzanego i `finally` bloki nie zostanie przerwane asynchronicznie, ale od razu po wyjściu z jednej z tych kategorii.

 Przyczyną może być trudno określić, z powodu losowości związane z problemem.

## <a name="resolution"></a>Rozwiązanie
 Należy unikać projekt kodu, który wymaga użycia przerwanie asynchronicznego wątku. Istnieje kilka metod są bardziej odpowiednie dla przeszkód wątek docelowy, który nie wymaga wywołania <xref:System.Threading.Thread.Abort%2A>. Najbezpieczniejsze jest wprowadzenie mechanizmu, takiego jak wspólnej właściwości, który sygnalizuje wątek docelowy żądania przerwania. Sprawdza, czy wątek docelowy sygnał niektórych bezpieczne punkty kontrolne. Jeśli powiadomienia go, czy wysłano żądanie przerwania, może zostać zamknięty zostanie wyłączone poprawnie.

## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Informuje jedynie dane o przerwanie asynchronicznego wątku.

## <a name="output"></a>Dane wyjściowe
 MDA raportów, identyfikator wątku wykonującego przerwania i identyfikator wątku, który jest elementem docelowym przerwanie. Nigdy nie będą takie same, ponieważ jest ograniczona do asynchronicznego przerwania.

## <a name="configuration"></a>Konfiguracja

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Przykład
 Aktywowanie `asynchronousThreadAbort` MDA wymaga tylko wywołania <xref:System.Threading.Thread.Abort%2A> w oddzielnym wątku uruchomione. Należy rozważyć konsekwencje, jeśli zawartość wątku Uruchom funkcję były zbiór bardziej złożonych operacji, które może zostać przerwane w dowolnym momencie dowolnego za przerwanie.

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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
