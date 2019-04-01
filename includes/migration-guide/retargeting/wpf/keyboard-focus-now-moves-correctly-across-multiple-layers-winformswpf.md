---
ms.openlocfilehash: ae110d915241fe85453667e895ab54288302c20d
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760898"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a>Fokus klawiatury porusza się teraz prawidłowo między wieloma warstwami obsługi WinForms/WPF

|   |   |
|---|---|
|Szczegóły|Należy wziąć pod uwagę aplikacji WPF hostingu formant programu WinForms, który z kolei hostuje kontrolek WPF. Użytkownicy mogą nie mieć możliwość karcie poza warstwy WinForms, jeśli pierwszy lub ostatni kontroli w tej warstwie jest WPF <code>System.Windows.Forms.Integration.ElementHost</code>. Ta zmiana rozwiązuje ten problem, a użytkownicy mogą teraz kartę z warstwy WinForms. Zautomatyzowane aplikacje, które zależą od fokus nigdy nie anulowania zapewnianego element warstwy WinForms może przestać działać zgodnie z oczekiwaniami.|
|Sugestia|Dla deweloperów, który chce korzystać z tej zmiany podczas określania wartości docelowej framework w wersji starszej niż .NET 4.7.2 można ustawić następujący zestaw flag AppContext na wartość false, aby zmiana zaczęła być włączone.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Aplikacje WPF musi zgadzaj się na wszystkie wcześniejsze ulepszenia ułatwień dostępu, aby uzyskać nowsze ulepszenia. Innymi słowy, zarówno <code>Switch.UseLegacyAccessibilityFeatures</code> i <code>Switch.UseLegacyAccessibilityFeatures.2</code> przełączniki muszą być Deweloper setA, który wymaga poprzedniej funkcji podczas określania wartości docelowej platformy .NET 4.7.2 lub większą może ustawić następujące flagi AppContext na wartość true, aby zmiana zaczęła być wyłączone.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|Przekierowanie|

