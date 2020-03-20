---
ms.openlocfilehash: b92086c8ccf7592ce70b75bd31d4ea255c35b543
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803449"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a>HwndHost teraz poprawnie zmienia rozmiar dziecka-HWND podczas zmian DPI

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.7.2 i wcześniejszych wersjach, gdy WPF WPF został uruchomiony w trybie per-monitor aware, formanty hostowane w ramach <xref:System.Windows.Interop.HwndHost> nie zostały odpowiednio dobrane po zmianach DPI, na przykład podczas przenoszenia aplikacji z jednego monitora do drugiego. Ta poprawka gwarantuje, że hostowane formanty są odpowiednio dopasowywalane.|
|Sugestia|Aby aplikacja korzystać z tych zmian, musi działać na .NET Framework 4.7.2 lub nowszej i musi wyrazić zgodę <code>&lt;runtime&gt;</code> na to zachowanie, <code>false</code>ustawiając następujące [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) w sekcji pliku konfiguracji aplikacji do , jak pokazano w poniższym przykładzie.<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Duży|
|Wersja|4.8|
|Typ|Przekierowanie|
