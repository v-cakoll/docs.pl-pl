---
ms.openlocfilehash: 8e75c60126abc2670053eba2c01e1fb36d1a93e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762649"
---
### <a name="wpf-appdomain-shutdown-handling-may-now-call-dispatcherinvoke-in-cleanup-of-weak-events"></a>Obsługa zamykania domeny aplikacji WPF teraz może wywołać Dispatcher.Invoke w oczyszczania słabe zdarzeń

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.7.1 i wcześniejszymi wersjami, tworzy potencjalnie WPF <xref:System.Windows.Threading.Dispatcher?displayProperty=nameWithType> w wątku finalizatora .NET podczas zamykania domeny aplikacji.  Zostało to naprawione w .NET Framework 4.7.2 i nowszych wersjach, wprowadzając obsługujących wątku czyszczenia zdarzeń słabych.  Ze względu na to, może wywołać WPF <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> do ukończenia procesu czyszczenia. W niektórych aplikacjach ta zmiana w finalizator chronometrażu potencjalnie może spowodować, że wyjątki podczas AppDomain lub przetworzyć zamknięcia.  Jest to ogólnie widoczny w aplikacjach, które nie są poprawnie zamykane dyspozytorów systemem wątków roboczych przed procesu lub zamykania domeny aplikacji.  Do prawidłowego zarządzania okresem istnienia dyspozytorów takich aplikacji należy się zająć.|
|Sugestia|W .NET Framework 4.7.2 i nowszych wersjach deweloperów można wyłączyć tej poprawki, aby ułatwić złagodzenie (ale nie eliminuje) problemy dotyczące synchronizacji, które mogą wystąpić z powodu zmiany oczyszczania. Aby wyłączyć zmianę oczyszczania, należy użyć następujących flagi AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotInvokeInWeakEventTableShutdownListener=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|Przekierowanie|
