---
ms.openlocfilehash: 52406f1e4ea4eda417909e52cf6529631cb0ae33
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620218"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>Zmiana zachowania metod Task. WaitAll z argumentami limitu czasu

#### <a name="details"></a>Szczegóły

<xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>zachowanie zostało bardziej spójne w .NET Framework 4.5.In .NET Framework 4. te metody zadziałały niespójnie. Po upływie limitu czasu, jeśli co najmniej jedno zadanie zostało ukończone lub anulowane przed wywołaniem metody, Metoda zgłosiła <xref:System.AggregateException?displayProperty=fullName> wyjątek. Po upływie limitu czasu, jeśli żadne zadania nie zostały ukończone lub anulowane przed wywołaniem metody, ale co najmniej jedno zadanie zostało wprowadzone po wywołaniu metody, Metoda zwróciła wartość false.<br/><br/>W .NET Framework 4,5 te przeciążenia metody teraz zwracają wartość false, jeśli jakieś zadania są nadal uruchomione, gdy upłynął limit czasu, i zgłasza wyjątek tylko wtedy, <xref:System.AggregateException?displayProperty=fullName> gdy zadanie wejściowe zostało anulowane (bez względu na to, czy przed lub po wywołaniu metody) i nie będzie nadal działać.

#### <a name="suggestion"></a>Sugestia

Jeśli <xref:System.AggregateException?displayProperty=fullName> został przechwycony jako środek wykrywania zadania, które zostało anulowane przed <xref:System.Threading.Tasks.Task.WaitAll%2A> wywoływaniem wywołania, ten kod powinien zamiast tego przeprowadzić wykrywanie za pośrednictwem <xref:System.Threading.Tasks.Task.IsCanceled%2A> właściwości (na przykład:. Dowolny (t = &gt; t. Iscanceld)) ponieważ .NET Framework 4,6 będzie zgłaszany w tym przypadku tylko wtedy, gdy wszystkie oczekujące zadania zostaną zakończone przed upływem limitu czasu.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType></li></ul>|
