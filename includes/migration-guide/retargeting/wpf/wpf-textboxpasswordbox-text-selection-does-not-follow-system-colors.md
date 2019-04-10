---
ms.openlocfilehash: 3f88c8b80518aa65c082dc3da2d75b5221dd00f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234033"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>Zaznaczanie tekstu w polu tekstowym/PasswordBox WPF nie jest zgodna z kolory systemowe

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.7.1 i wcześniejszych wersjach, WPF <code>System.Windows.Controls.TextBox</code> i <code>System.Windows.Controls.PasswordBox</code> można renderować obraz tylko zaznaczonego tekstu w warstwie moduł definiowania układu kodu. W niektórych kompozycje systemu to będzie occlude tekstu, dzięki czemu jest trudny do odczytania.  W programie .NET Framework 4.7.2 i później, deweloperzy mają możliwość włączania schematu renderowania wybór podstawie moduł definiowania układu kodu, który pozwala uniknąć tego problemu.|
|Sugestia|Deweloper, który chce korzystać z tej zmiany należy odpowiednio ustawione następujące flagi AppContext.  Aby korzystać z tej funkcji, zainstalowanej wersji .NET Framework musi być 4.7.2 lub nowszej. Włączony wybór podstawie moduł definiowania układu kodu, należy użyć następujących flagi AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|Przekierowanie|
