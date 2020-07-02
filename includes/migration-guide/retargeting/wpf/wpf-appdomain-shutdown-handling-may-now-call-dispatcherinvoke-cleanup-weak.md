---
ms.openlocfilehash: 8b804d23247b95381f3ff83bc12c32215a420fb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614959"
---
### <a name="wpf-appdomain-shutdown-handling-may-now-call-dispatcherinvoke-in-cleanup-of-weak-events"></a>Obsługa zamykania aplikacji WPF może teraz wywołać dyspozytora. Wywołaj w trakcie oczyszczania słabych zdarzeń

#### <a name="details"></a>Szczegóły

W .NET Framework 4.7.1 i starszych wersjach program WPF może utworzyć <xref:System.Windows.Threading.Dispatcher?displayProperty=nameWithType> na wątku platformy .NET finalizator podczas zamykania elementu AppDomain.  Zostało to rozwiązane w .NET Framework 4.7.2 i nowszych wersjach, co sprawia, że jest to oczyszczanie słabych zdarzeń z obsługą wątków.  Z tego powodu, WPF może wywołać, <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> Aby ukończyć proces oczyszczania. W niektórych aplikacjach ta zmiana w czasie wykonywania może potencjalnie spowodować wyjątki podczas zamykania elementu AppDomain lub procesu.  Jest to zwykle widoczne w aplikacjach, które nie zamykają prawidłowo odniesień działających w wątkach roboczych przed przetworzeniem lub zamknięciem elementu AppDomain.  Takie aplikacje powinny mieć na celu prawidłowe zarządzanie okresem istnienia dyspozytorów.

#### <a name="suggestion"></a>Sugestia

W .NET Framework 4.7.2 i nowszych wersjach deweloperzy mogą wyłączyć tę poprawkę, aby pomóc wyeliminować problemy związane z chronometrażem, które mogą wystąpić w wyniku zmiany. Aby wyłączyć zmianę w oczyszczaniu, użyj następującej flagi AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotInvokeInWeakEventTableShutdownListener=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.7.2       |
| Typ    | Przekierowanie |
