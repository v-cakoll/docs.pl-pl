---
ms.openlocfilehash: 4eac93d5cfea19cb83c66cd3fe35c1b0703c0cc0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234040"
---
### <a name="wpf-focusvisual-for-radiobutton-and-checkbox-now-displays-correctly-when-the-controls-have-no-content"></a>WPF FocusVisual RadioButton i teraz pole wyboru jest wyświetlane prawidłowo, gdy formanty nie ma zawartości

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.7.1 i wcześniejszymi wersjami, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> i <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> mają niespójne i, w modelu klasycznym oraz wysokiego kontrastu motywy niepoprawne koncentracji uwagi wizualizacji.  Te problemy występują w przypadkach, gdy formanty nie mają żadnych zestawu zawartości.  Dzięki temu może być przejście pomiędzy motywów mylące i element wizualny fokusu trudne do zobaczenia. W programie .NET Framework 4.7.2 te wizualizacje są teraz bardziej spójny między motywy i widoczność w klasycznej sieci wirtualnej i wysokiego kontrastu motywów.|
|Sugestia|Deweloper przeznaczonych dla platformy .NET Framework 4.7.2 chce, aby przywrócić działanie na platformie .NET 4.7.1 należy ustawić następujące flagi AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Dla deweloperów, który chce korzystać z tej zmiany podczas określania wartości docelowej framework w wersji starszej niż .NET 4.7.2 należy ustawić następujące flagi AppContext. Pamiętaj, że wszystkie flagi muszą być odpowiednio ustawione, a zainstalowana wersja programu .NET Framework, musi być 4.7.2 lub nowszej. Aplikacje WPF są wymagane do zgadzaj się na wszystkie wcześniej ulepszenia ułatwień dostępu, aby uzyskać najnowsze ulepszenia. Aby to zrobić, upewnij się, że oba AppContext serwerów, które "Switch.UseLegacyAccessibilityFeatures" i "Switch.UseLegacyAccessibilityFeatures.2" są ustawione na wartość false.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|Przekierowanie|
