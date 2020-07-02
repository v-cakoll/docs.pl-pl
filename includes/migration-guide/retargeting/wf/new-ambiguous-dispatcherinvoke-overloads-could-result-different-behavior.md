---
ms.openlocfilehash: 80e61d4dd5b8d4754a39e95e37475fefff57fcbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617169"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>Nowe (niejednoznaczne) Dyspozytor. Wywołaj przeciążenia mogą spowodować inne zachowanie

#### <a name="details"></a>Szczegóły

.NET Framework 4,5 dodaje nowe przeciążenia do <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> , które zawierają parametr typu <xref:System.Action> . Gdy istniejący kod jest ponownie kompilowany, kompilatory mogą rozpoznać wywołania do dyspozytora. Wywołaj metody, które mają <xref:System.Delegate> parametr jako wywołania dyspozytora. Wywołaj metody z <xref:System.Action> parametrem. W przypadku wywołania dyspozytora. Wywołaj Przeciążenie z <xref:System.Delegate> parametrem, który jest rozpoznawany jako wywołanie dyspozytora. Wywołaj Przeciążenie z <xref:System.Action> parametrem, mogą wystąpić następujące różnice w zachowaniu:

- Jeśli wystąpi wyjątek, <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> <xref:System.Windows.Threading.Dispatcher.UnhandledException> zdarzenia i nie są zgłaszane. Zamiast tego wyjątki są obsługiwane przez <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> zdarzenie.
- Wywołania do niektórych elementów członkowskich, takie jak <xref:System.Windows.Threading.DispatcherOperation.Result> , bloku do momentu ukończenia operacji.

#### <a name="suggestion"></a>Sugestia

Aby uniknąć niejednoznaczności (i potencjalnych różnic w obsłudze wyjątków lub zachowania blokowania), kod wywołujący wywołania. Invoke może przekazać pusty obiekt [] jako drugi parametr do wywołania wywołania, aby upewnić się, że rozwiązanie do przeciążenia metody .NET Framework 4,0.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.5         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
