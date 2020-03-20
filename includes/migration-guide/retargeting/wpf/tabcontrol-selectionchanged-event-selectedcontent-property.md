---
ms.openlocfilehash: 923105114c9e8da02c61c842cc02bed1ead3eddc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858963"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a>Zdarzenie TabControl SelectionChanged i SelectedContent, właściwość

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.7.1, <xref:System.Windows.Controls.TabControl> aktualizuje wartość jego <xref:System.Windows.Controls.TabControl.SelectedContent> właściwości przed podniesieniem <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> zdarzenia, gdy jego wybór ulegnie zmianie. W .NET Framework 4.7 i wcześniejszych wersjach aktualizacja do SelectedContent wystąpiła po zdarzeniu.|
|Sugestia|Aplikacje przeznaczone dla programu .NET Framework 4.7.1 lub nowszego mogą zrezygnować z <code>&lt;runtime&gt;</code> tej zmiany i używać starszego zachowania, dodając następujące elementy do sekcji pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikacje przeznaczone dla programu .NET Framework 4.7 lub starsze, ale uruchomione w programie .NET Framework 4.7.1 lub nowszym, mogą włączyć nowe zachowanie, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|
