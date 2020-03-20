---
ms.openlocfilehash: f59c9f048bb3cd3f425e36b931302258fcf693f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803481"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a>Zmieniono sumy kontrolne plików XOML przepływu pracy z MD5 na SHA256

|   |   |
|---|---|
|Szczegóły|Aby obsługiwać debugowanie przepływów pracy opartych na XOML w programie Visual Studio, gdy projekty przepływu pracy zawierające kompilację plików XOML <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> suma kontrolna zawartości pliku XOML jest uwzględniona w kodzie wygenerowanym jako wartość. W .NET Framework 4.7.2 i wcześniejszych wersjach to mieszanie sumy kontrolnej używane algorytm MD5, który spowodował problemy w systemach z obsługą FIPS. Począwszy od .NET Framework 4.8, algorytm używany jest SHA256. Aby być compatibile z WorkflowMarkupSourceAttribute.MD5Digest, tylko pierwsze 16 bajtów wygenerowanej sumy kontrolnej są używane. Może to spowodować problemy podczas debugowania. Może być konieczne ponowne zbudowanie projektu.|
|Sugestia|Jeśli ponowne zbudowanie projektu nie rozwiąże <code>AppContext</code> problemu, spróbuj zmienić switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum &quot;&quot; na true. W kodzie:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>Lub w pliku konfiguracyjnym (musi to być w pliku MSBuild.exe.config dla serwera MSBuild.exe, którego używasz):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.8|
|Typ|Przekierowanie|
