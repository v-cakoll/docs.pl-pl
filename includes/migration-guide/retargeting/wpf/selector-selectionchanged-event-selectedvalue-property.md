---
ms.openlocfilehash: 0ef39d67cd4335658658f5772b5bce49d827cad0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614936"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>Selektor SelectionChanged zdarzenie i Właściwość SelectedValue

#### <a name="details"></a>Szczegóły

Rozpoczynając od .NET Framework 4.7.1, <xref:System.Windows.Controls.Primitives.Selector> zawsze aktualizuje wartość <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> Właściwości przed podnoszeniem poziomu <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> zdarzenia, gdy zmieni się zaznaczenie. Dzięki temu Właściwość SelectedValue jest spójna z innymi właściwościami wyboru ( <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> i <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> ), które są aktualizowane przed podnoszeniem poziomu zdarzenia.<p/>W .NET Framework 4,7 i wcześniejszych wersjach aktualizacja SelectedValue miała miejsce przed zdarzeniem w większości przypadków, ale wystąpił po zdarzeniu, jeśli zmiana wyboru została spowodowana przez zmianę <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> właściwości.

#### <a name="suggestion"></a>Sugestia

Aplikacje przeznaczone dla .NET Framework 4.7.1 lub nowszych mogą zrezygnować z tej zmiany i zastosować starsze zachowanie, dodając do `<runtime>` sekcji pliku konfiguracyjnego aplikacji następujące czynności:

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

Aplikacje przeznaczone dla .NET Framework 4,7 lub wcześniejszych, ale działają na .NET Framework 4.7.1 lub nowszych mogą włączyć nowe zachowanie, dodając następujący wiersz do `<runtime>` sekcji pliku Application. Configuration:

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.7.1       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
