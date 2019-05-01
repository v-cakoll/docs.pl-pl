---
ms.openlocfilehash: f814703e187726d3988787fac52e5049988fd4d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783264"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>Zmieniła się z SHA1 SHA256 symboli, sum kontrolnych XAML przepływu pracy

|   |   |
|---|---|
|Szczegóły|Aby zapewnić obsługę debugowania programu Visual Studio, środowiska wykonawczego przepływów pracy generuje sumy kontrolnej pliku XAML przepływu pracy przy użyciu algorytmu wyznaczania wartości skrótu. W .NET Framework 4.6.2 i wcześniejszych wersjach przepływ pracy sumy kontrolnej wyznaczania wartości skrótu używany algorytmu MD5, który spowodował problemów w systemach z obsługą standardu FIPS. Począwszy od programu .NET Framework 4.7, zmieniono domyślny algorytm SHA1. Począwszy od .NET Framework 4.8 zmieniono domyślny algorytm na SHA256.|
|Sugestia|Jeśli Twój kod nie może załadować wystąpienia przepływu pracy lub znalezienia odpowiednich symboli z powodu błędu sumy kontrolnej, spróbuj ustawienie <code>AppContext</code> Przełącz &quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot; na wartość true. W kodzie:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot;, true);&#13;&#10;</code></pre>Lub w konfiguracji:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.8|
|Typ|Przekierowanie|
