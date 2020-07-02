---
ms.openlocfilehash: 7c2e80669d9ef27f87cde9442d8eeab0ee31a524
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614978"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>Element TextBox/PasswordBox tekstu WPF nie jest zgodny z kolorami systemu

#### <a name="details"></a>Szczegóły

W .NET Framework 4.7.1 i starszych wersjach, WPF `System.Windows.Controls.TextBox` i `System.Windows.Controls.PasswordBox` można renderować tylko zaznaczenie tekstu w warstwie modułu definiowania układu. W niektórych motywach systemu occlude tekstu, co trudno odczytać.  W .NET Framework 4.7.2 i nowszych deweloperzy mogą korzystać z opcji włączania schematu renderowania wyboru, który pozwala uniknąć tego problemu.

#### <a name="suggestion"></a>Sugestia

Deweloperzy, którzy chcą korzystać z tej zmiany, muszą odpowiednio ustawić następującą flagę AppContext.  Aby można było korzystać z tej funkcji, zainstalowana wersja .NET Framework musi być 4.7.2 lub nowsza. Aby włączyć wybór poza modułem definiowania układu, użyj następującej flagi AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.7.2       |
| Typ    | Przekierowanie |
