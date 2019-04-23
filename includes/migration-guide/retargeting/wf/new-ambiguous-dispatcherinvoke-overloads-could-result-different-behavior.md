---
ms.openlocfilehash: 4529d8040fc08b5290ac46abd1ef752086ea3aeb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774493"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>Nowe przeciążenia Dispatcher.Invoke (niejednoznaczne) może spowodować inne zachowanie

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.5 dodaje nowe przeciążenia do <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> zawierające parametr typu <xref:System.Action>. Gdy istniejący kod jest ponownie kompilowany, kompilatory mogą rozpoznawać wywołania metod Dispatcher.Invoke, które mają <xref:System.Delegate> parametr jako wywołania metod Dispatcher.Invoke z <xref:System.Action> parametru. Jeśli wywołanie przeciążenia Dispatcher.Invoke, za pomocą <xref:System.Delegate> parametr jest rozpoznawane jako wywołanie przeciążenia Dispatcher.Invoke, za pomocą <xref:System.Action> parametru, mogą wystąpić następujące różnice w zachowaniu:<ul><li>Jeśli wystąpi wyjątek, <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> i <xref:System.Windows.Threading.Dispatcher.UnhandledException> zdarzenia nie są zgłaszane. Zamiast tego wyjątki są obsługiwane przez <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=name> zdarzeń.</li><li>Wywołania niektórych członków, takich jak <xref:System.Windows.Threading.DispatcherOperation.Result>, blokowane, aż operacja zostanie ukończona.</li></ul>|
|Sugestia|Aby uniknąć niejednoznaczności (i potencjalne różnice w wyjątków, obsługa lub blokuje zachowania), kod wywołujący Dispatcher.Invoke przekazać pusty obiekt [] jako drugi parametr do wywołania Invoke mieć pewność, że programu rozpoznawania przeciążenia metody .NET Framework 4.0.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType></li></ul>|
