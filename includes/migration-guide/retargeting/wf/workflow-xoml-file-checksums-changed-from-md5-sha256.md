---
ms.openlocfilehash: c44971dfd65ee31657279daec2d34b8cfa8d4860
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410398"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a>Przepływ pracy XOML plik sum kontrolnych zmieniła się z MD5 SHA256

|   |   |
|---|---|
|Szczegóły|Aby obsłużyć debugowanie przepływów pracy opartych na pliku XOML z programem Visual Studio, gdy przepływ pracy projektów zawierających kompilacji pliki XOML, sumy kontrolnej zawartość pliku XOML znajduje się w kodzie, który został wygenerowany jako <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> wartość. W .NET Framework 4.7.2 i starszych wersji tej sumy kontrolnej mieszania używany algorytmu MD5, który spowodował problemów w systemach z obsługą standardu FIPS. Począwszy od .NET Framework 4.8 algorytm używany jest algorytm SHA256. Aby był zgodny z WorkflowMarkupSourceAttribute.MD5Digest, używane są tylko pierwsze 16 bajtów wygenerowanego sumy kontrolnej. Może to spowodować problemy podczas debugowania. Może być konieczne ponowne skompilowanie projektu.|
|Sugestia|Jeśli ponowne kompilowanie projektu nie rozwiąże problemu, spróbuj ustawienie <code>AppContext</code> Przełącz &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; na wartość true. W kodzie:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>Lub w pliku konfiguracji (musi to być w pliku MSBuild.exe.config dla MSBuild.exe, którego używasz):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Scope|Mały|
|Wersja|4.8|
|Typ|Przekierowanie|
