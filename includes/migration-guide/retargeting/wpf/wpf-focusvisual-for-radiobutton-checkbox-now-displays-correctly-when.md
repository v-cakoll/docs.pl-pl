---
ms.openlocfilehash: 9e70bcd95393a7ff24de43577d26869ce674067b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614964"
---
### <a name="wpf-focusvisual-for-radiobutton-and-checkbox-now-displays-correctly-when-the-controls-have-no-content"></a>Funkcja WPF FocusVisual dla RadioButton i CheckBox jest teraz wyświetlana prawidłowo, gdy kontrolki nie mają zawartości

#### <a name="details"></a>Szczegóły

W .NET Framework 4.7.1 i starszych wersjach WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWithType> i <xref:System.Windows.Controls.RadioButton?displayProperty=nameWithType> mają niespójne i, w klasyczny i duży kontrast motywy, wizualizacje fokusu są nieprawidłowe.  Te problemy występują w przypadkach, gdy kontrolki nie mają żadnego zestawu zawartości.  Może to spowodować, że przejście między motywami jest mylące i wizualizacja fokusu będzie widoczna. W .NET Framework 4.7.2 te wizualizacje są teraz bardziej spójne w różnych motywach i łatwiej widoczne w klasycznych i duży kontrast motywach.

#### <a name="suggestion"></a>Sugestia

Ukierunkowany dla deweloperów .NET Framework 4.7.2, które chcą powrócić do zachowania w programie .NET 4.7.1, muszą mieć ustawioną następującą flagę AppContext.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Deweloperzy, którzy chcą korzystać z tej zmiany, gdy celem jest wersja platformy .NET 4.7.2, musi ustawić następujące flagi AppContext. Należy pamiętać, że wszystkie flagi muszą być odpowiednio ustawione, a zainstalowana wersja .NET Framework musi być 4.7.2 lub większa. Aplikacje WPF są wymagane do zarejestrowania wszystkich wcześniejszych ulepszeń ułatwień dostępu w celu uzyskania najnowszych ulepszeń. W tym celu należy się upewnić, że oba przełączniki AppContext "switch. UseLegacyAccessibilityFeatures" i "switch. UseLegacyAccessibilityFeatures. 2" są ustawione na wartość false.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.7.2       |
| Typ    | Przekierowanie |
