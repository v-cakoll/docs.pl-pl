---
ms.openlocfilehash: 4254cceab0048341b32fe5babf53b5ea3e5a52d6
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "72846991"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>Klucze XOML i SqlTrackingService pamięci podręcznej przepływu pracy zmieniły się z MD5 na SHA256

|   |   |
|---|---|
|Szczegóły|Środowisko uruchomieniowe przepływu pracy w programie przechowuje w pamięci podręcznej definicje przepływów pracy zdefiniowane w pliku XOML. SqlTrackingService przechowuje również pamięć podręczną, która jest określana przez ciągi. Te pamięci podręczne są oparte na wartościach, które zawierają wartość skrótu sumy kontrolnej. W .NET Framework 4.7.2 i starszych wersjach tego skrótu sumy kontrolnej używał algorytmu MD5, który spowodował problemy w systemach z obsługą FIPS. Począwszy od .NET Framework 4,8, używany algorytm to SHA256. Ta zmiana nie powinna być przyczyną problemu ze zgodnością, ponieważ wartości są ponownie obliczane przy każdym uruchomieniu środowiska uruchomieniowego przepływu pracy i SqlTrackingService. Jednak firma Microsoft udostępniła osobliwości, aby umożliwić klientom przywrócenie zgodności ze starszym algorytmem wyznaczania wartości skrótu, w razie potrzeby.|
|Sugestia|Jeśli ta zmiana spowoduje problem podczas wykonywania przepływów pracy, spróbuj ustawić jeden lub oba przełączniki <code>AppContext</code>:<ul><li>&quot;Switch. System. Workflow. Runtime. UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; na wartość true.</li><li>&quot;Switch. System. Workflow. Runtime. UseLegacyHashForSqlTrackingCacheKey&quot; na wartość true.</li></ul>W kodzie:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>Lub w pliku konfiguracyjnym (musi być w pliku konfiguracji dla aplikacji, która tworzy obiekt <xref:System.Workflow.Runtime.WorkflowRuntime>):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4,8|
|Typ|Przekierowanie|
