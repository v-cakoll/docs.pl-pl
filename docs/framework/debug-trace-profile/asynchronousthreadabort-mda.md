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
ms.workload: dotnet
ms.openlocfilehash: ecd99b098a619d4ad132432f4fd163d32598c2ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="asynchronousthreadabort-mda"></a>asynchronousThreadAbort MDA
`asynchronousThreadAbort` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy wątek podejmuje próbę wprowadzenia asynchronicznego przerwania do innego wątku. Przerywa synchroniczne wątek nie zostanie aktywowany `asynchronousThreadAbort` MDA.

## <a name="symptoms"></a>Symptomy
 Wystąpiła awaria aplikacji z nieobsługiwanym <xref:System.Threading.ThreadAbortException> po wątku głównego aplikacji zostało przerwane. Jeżeli aplikacja kontynuować jego wykonywanie, konsekwencje może być gorsza niż aplikacja awarii, co prawdopodobnie spowoduje dalsze uszkodzenia danych.

 Operacje przeznaczone do niepodzielnych prawdopodobnie zostać przerwane po zakończeniu częściowe, pozostawiając dane aplikacji w nieprzewidywalnym stanie. A <xref:System.Threading.ThreadAbortException> mogą być generowane z pozornie losowe punktów podczas wykonywania kodu, często w miejscach, z których wyjątek nie powinno wystąpić. Kod może nie być może obsługiwać takiego wyjątku, co w stanie uszkodzenia.

 Objawy różnią może z powodu problemu związanego z używaniem losowości.

## <a name="cause"></a>Przyczyna
 Kod w jeden wątek o nazwie <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody na wątek docelowy wprowadzenie przerwanie asynchronicznego wątku. Przerwij wątku jest asynchroniczne, ponieważ kod, który wykonuje wywołanie do <xref:System.Threading.Thread.Abort%2A> jest uruchomiona w innym wątku niż docelowy operacji przerwania. Przerywa wątku synchroniczne nie powinny powodować problem, ponieważ wykonywanie wątku <xref:System.Threading.Thread.Abort%2A> powinna mieć wykonana tylko na bezpiecznych punkt kontrolny, gdzie stan aplikacji jest zgodny.

 Przerwanie asynchronicznego wątku powodują problemu, ponieważ zostały one przetworzone w punktach nieprzewidywalne podczas wykonywania wątku docelowej. Aby tego uniknąć, należy obsługiwać kodu napisanego w celu uruchamiania w wątku, który może zostać przerwane w ten sposób <xref:System.Threading.ThreadAbortException> w niemal każdego wiersza kodu, zwracając szczególną uwagę na odłożyć dane aplikacji do stanu spójności. Nie jest realistyczne kodu ma zostać zapisany z tym problemem, pamiętając, lub do pisania kodu, która chroni przed wszystkich możliwych okolicznościach.

 Wywołania do kodu niezarządzanego i `finally` bloków nie zostanie przerwana asynchronicznie, ale natychmiast po wyjściu z jednej z tych kategorii.

 Przyczyną może być trudne do ustalenia, z powodu problemu związanego z używaniem losowości.

## <a name="resolution"></a>Rozwiązanie
 Unikaj projekt kodu, który wymaga użycia przerwanie asynchronicznego wątku. Istnieje kilka rozwiązań bardziej odpowiednie dla przerwom w wykonywaniu wątku docelowego, który nie wymaga wywołania <xref:System.Threading.Thread.Abort%2A>. Najbezpieczniejsze jest wprowadzenie mechanizmu, takiego jak wspólnej właściwości, która sygnalizuje wątek docelowy żądanie przerwania. Wątek docelowy sprawdza sygnał niektórych bezpieczne punkty kontrolne. Jeśli powiadomienia go, że zażądano przerwania, może zostać zamknięty bezpiecznie zamknąć.

## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Zwraca tylko dane o przerwanie asynchronicznego wątku.

## <a name="output"></a>Dane wyjściowe
 MDA zgłasza identyfikator wątku, przerwanie i identyfikator wątku, który jest elementem docelowym przerwanie. Nigdy nie będą takie same, ponieważ jest ograniczone do asynchronicznego przerwania.

## <a name="configuration"></a>Konfiguracja

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Przykład
 Aktywowanie `asynchronousThreadAbort` MDA wymaga tylko wywołania <xref:System.Threading.Thread.Abort%2A> na oddzielnych uruchomiony wątek. Jeśli zawartość wątku uruchomienia funkcji zostały zbiór bardziej złożonych czynności, które może zostać przerwane w dowolnym momencie dowolnego przez przerwanie, należy wziąć pod uwagę skutki.

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

## <a name="see-also"></a>Zobacz też
 <xref:System.Threading.Thread>[Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
