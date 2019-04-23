---
ms.openlocfilehash: b92086c8ccf7592ce70b75bd31d4ea255c35b543
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982161"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a>HwndHost teraz poprawnie zmienia rozmiar HWND podrzędnych podczas zmiany wartości DPI

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.7.2 i wcześniejszych wersji WPF uruchomieniu w trybie monitora pamiętać formantów hostowanych na platformie <xref:System.Windows.Interop.HwndHost> zostały nie użyłeś pojemników po zmianie wartości DPI, takich jak podczas przenoszenia aplikacji z jednego monitora do innego. Ta poprawka gwarantuje, że formanty hostowanej są rozmiary.|
|Sugestia|Aby dla aplikacji do korzystania z tych zmian, należy uruchomić w środowisku .NET Framework 4.7.2 lub nowszym, i jego musi wyrazić zgodę na to zachowanie przez ustawienie następujących [przełącznika AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) w <code>&lt;runtime&gt;</code> sekcji konfiguracji aplikacji plik <code>false</code>, jak pokazano w poniższym przykładzie.<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Duży|
|Wersja|4.8|
|Typ|Przekierowanie|
