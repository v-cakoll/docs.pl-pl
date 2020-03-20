---
ms.openlocfilehash: f814703e187726d3988787fac52e5049988fd4d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803547"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>Sumy kontrolne XAML przepływu pracy dla symboli zmienionych z SHA1 na SHA256

|   |   |
|---|---|
|Szczegóły|Aby obsługiwać debugowanie za pomocą programu Visual Studio, środowisko wykonawcze przepływu pracy generuje sumę kontrolną dla pliku XAML przepływu pracy przy użyciu algorytmu mieszania. W .NET Framework 4.6.2 i wcześniejszych wersjach mieszanie sumy kontrolnej przepływu pracy używało algorytmu MD5, który powodował problemy w systemach obsługujących FIPS. Począwszy od programu .NET Framework 4.7, domyślny algorytm został zmieniony na SHA1. Począwszy od programu .NET Framework 4.8, domyślny algorytm został zmieniony na SHA256.|
|Sugestia|Jeśli kod nie może załadować wystąpień przepływu pracy lub znaleźć odpowiednie symbole <code>AppContext</code> z &quot;powodu błędu sumy kontrolnej, spróbuj zmienić switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot; na true. W kodzie:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot;, true);&#13;&#10;</code></pre>Lub w konfiguracji:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.8|
|Typ|Przekierowanie|
