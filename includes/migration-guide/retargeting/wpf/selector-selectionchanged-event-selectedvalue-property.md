---
ms.openlocfilehash: a4054ee893ba8b8c290a447689d3aa58dcc84cbe
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "52742363"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>Selektor SelectionChanged zdarzeń i właściwości SelectedValue

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7.1, <xref:System.Windows.Controls.Primitives.Selector> zawsze aktualizuje wartość jego <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> właściwości przed zgłoszeniem <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> zdarzenie, gdy zmieni się jego zaznaczenie. To sprawia, że właściwości SelectedValue zgodne z innymi właściwościami wyboru (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> i <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), które zostaną zaktualizowane przed zgłoszeniem zdarzenia.<p/>W .NET Framework 4.7 i wcześniejszych wersjach, aktualizacja SelectedValue miały miejsce przed wystąpieniem zdarzenia w większości przypadków, ale wystąpiły po wystąpieniu zdarzenia, jeśli zmiana zaznaczenia zostało spowodowane przez zmianę <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> właściwości.|
|Sugestia|Aplikacje, które obsługują program .NET Framework 4.7.1 lub nowszej można zrezygnować z tego zmienić i użyć starsze zachowanie, dodając następujące polecenie, aby <code>&lt;runtime&gt;</code> sekcję pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikacje przeznaczone dla .NET Framework 4.7 lub wcześniej, ale są uruchomione w środowisku .NET Framework 4.7.1 lub później włączyć nowe zachowanie, dodając następujący wiersz do <code>&lt;runtime&gt;</code> części pliku .configuration aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|

