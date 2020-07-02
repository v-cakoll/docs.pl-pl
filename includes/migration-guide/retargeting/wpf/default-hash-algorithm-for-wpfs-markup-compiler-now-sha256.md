---
ms.openlocfilehash: 4303b177ffe01328965c909a5a3809414fcead91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614931"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>Domyślny algorytm wyznaczania wartości skrótu dla kompilatora znaczników języka WPF jest teraz SHA256

#### <a name="details"></a>Szczegóły

Program WPF MarkupCompiler udostępnia usługi kompilacji dla plików znaczników XAML.  W .NET Framework 4.7.1 i starszych wersjach domyślny algorytm wyznaczania wartości skrótu używany dla sum kontrolnych to SHA1. Z powodu niedawnych problemów z zabezpieczeniami algorytmem SHA1 ta wartość domyślna została zmieniona na SHA256, począwszy od .NET Framework 4.7.2.  Ta zmiana ma wpływ na wszystkie generowanie sum kontrolnych dla plików znaczników podczas kompilacji.

#### <a name="suggestion"></a>Sugestia

Deweloper, który jest ukierunkowany na .NET Framework 4.7.2 lub nowszy i chce powrócić do zachowania skrótu SHA1, musi ustawić następującą flagę AppContext.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Deweloper, który chce wykorzystać mieszanie SHA256 podczas określania wersji platformy pod kątem platformy .NET 4.7.2, musi ustawić poniżej flagę AppContext.  Należy pamiętać, że zainstalowana wersja .NET Framework musi być 4.7.2 lub nowsza.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Przezroczyste |
| Wersja | 4.7.2       |
| Typ    | Przekierowanie |
