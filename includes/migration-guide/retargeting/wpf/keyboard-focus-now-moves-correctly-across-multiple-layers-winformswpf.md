---
ms.openlocfilehash: a82b720fd4e771481ea1142a88a095443afa0d5b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614945"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a>Fokus klawiatury jest teraz przenoszony prawidłowo między wieloma warstwami WinForms/hostingu WPF

#### <a name="details"></a>Szczegóły

Rozważmy aplikację WPF hostującym kontrolkę WinForms, która z kolei umożliwia hostowanie formantów WPF. Użytkownicy mogą nie być w stanie wystawić karty z warstwy WinForms, jeśli pierwszy lub ostatni formant w tej warstwie jest WPF `System.Windows.Forms.Integration.ElementHost` . Ta zmiana rozwiązuje ten problem, a użytkownicy mogą teraz wystawić kartę z warstwy WinForms. Zautomatyzowane aplikacje, które opierają się na koncentracji, nigdy nie ucieczką warstwy WinForms, mogą przestać działać zgodnie z oczekiwaniami.

#### <a name="suggestion"></a>Sugestia

Deweloperzy, którzy chcą korzystać z tej zmiany podczas określania wersji platformy pod kątem platformy .NET 4.7.2, mogą ustawić dla następujących zestawów flag AppContext wartość false, aby zmiana została włączona.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Aplikacje WPF muszą wyrazić zgodę na wszystkie ulepszenia wczesnego dostępu, aby uzyskać dalsze ulepszenia. Innymi słowy, zarówno, `Switch.UseLegacyAccessibilityFeatures` jak i `Switch.UseLegacyAccessibilityFeatures.2` przełączników musi być setA Deweloper, który wymaga powyższej funkcjonalności, podczas gdy przeznaczony dla programu .NET 4.7.2 lub nowszego można ustawić dla następującej flagi AppContext wartość true, aby zmiana została wyłączona.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.7.2       |
| Typ    | Przekierowanie |
