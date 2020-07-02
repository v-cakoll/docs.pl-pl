---
ms.openlocfilehash: dfdb62e8dd6db67d4fd12aba93928f4615e3f284
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614950"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a>Właściwość TabControl zdarzenia SelectionChanged i SelectedContent

#### <a name="details"></a>Szczegóły

Rozpoczynając od .NET Framework 4.7.1, <xref:System.Windows.Controls.TabControl> aktualizuje wartość <xref:System.Windows.Controls.TabControl.SelectedContent> Właściwości przed podnoszeniem poziomu <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> zdarzenia, gdy zmieni się zaznaczenie. W .NET Framework 4,7 i wcześniejszych wersjach aktualizacja SelectedContent miała miejsce po zdarzeniu.

#### <a name="suggestion"></a>Sugestia

Aplikacje przeznaczone dla .NET Framework 4.7.1 lub nowszych mogą zrezygnować z tej zmiany i zastosować starsze zachowanie, dodając do `<runtime>` sekcji pliku konfiguracyjnego aplikacji następujące czynności:

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

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
