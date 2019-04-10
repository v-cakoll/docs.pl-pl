---
ms.openlocfilehash: e73fe48467ede501bae0ddd9362d9d55b3ca998b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234075"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a>Akcje upbutton i downbutton domeny firmy WinForm są teraz zsynchronizowane

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.7.1 i poprzednich wersjach <xref:System.Windows.Forms.DomainUpDown> kontrolki <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcji jest ignorowana, gdy tekst kontrolki jest obecny i dewelopera jest wymagana do używania <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> działanie sterowania przed użyciem <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcji. Począwszy od programu .NET Framework 4.7.2 zarówno <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> i <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akcje działać niezależnie, w tym scenariuszu i pozostają zsynchronizowane.|
|Sugestia|Aby dla aplikacji do korzystania z tych zmian, należy uruchomić w środowisku .NET Framework 4.7.2 lub nowszej. Aplikacji mogą korzystać z tych zmian w jednej z następujących sposobów:<ul><li>Jest ponownie kompilowana pod kątem programu .NET Framework 4.7.2. Ta zmiana jest włączona domyślnie w aplikacji Windows Forms, przeznaczonych dla środowiska .NET Framework 4.7.2 lub nowszej.</li><li>Jego oznacza brak zgody na starszej wersji przewijanie zachowanie przez dodanie poniższego [przełącznika AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do <code>&lt;runtime&gt;</code> części pliku konfiguracyjnego aplikacji i ustawieniem dla niego <code>false</code>, jak pokazano w poniższym przykładzie.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType></li><li><xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType></li></ul>|
