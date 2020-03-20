---
ms.openlocfilehash: 4254cceab0048341b32fe5babf53b5ea3e5a52d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "72846991"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>Definicja XOML przepływu pracy i klucze pamięci podręcznej SqlTrackingService zostały zmienione z MD5 na SHA256

|   |   |
|---|---|
|Szczegóły|Środowisko wykonawcze przepływu pracy w zachowuje pamięć podręczną definicji przepływu pracy zdefiniowanych w XOML. SqlTrackingService przechowuje również pamięć podręczną, która jest kluczem przez ciągi. Te pamięci podręczne są kluczem przez wartości, które zawierają wartość mieszania sumy kontrolnej. W .NET Framework 4.7.2 i wcześniejszych wersjach to mieszanie sumy kontrolnej używane algorytm MD5, który spowodował problemy w systemach z obsługą FIPS. Począwszy od .NET Framework 4.8, algorytm używany jest SHA256. Nie powinno być problemu ze zgodnością z tą zmianą, ponieważ wartości są ponownie obliczane przy każdym uruchomieniu środowiska wykonawczego przepływu pracy i usługi SqlTrackingService. Jednak dostarczyliśmy dziwactwa, aby umożliwić klientom powrót do korzystania ze starszego algorytmu mieszania, jeśli to konieczne.|
|Sugestia|Jeśli ta zmiana stwarza problem podczas wykonywania przepływów pracy, spróbuj <code>AppContext</code> użyć jednego lub obu przełączników:<ul><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; do true.</li><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; do true.</li></ul>W kodzie:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>Lub w pliku konfiguracyjnym (to musi być w pliku <xref:System.Workflow.Runtime.WorkflowRuntime> konfiguracyjnym dla aplikacji, która tworzy obiekt):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.8|
|Typ|Przekierowanie|
