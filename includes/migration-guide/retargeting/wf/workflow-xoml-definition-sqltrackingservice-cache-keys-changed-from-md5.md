---
ms.openlocfilehash: 82e2794f262548105f9b7cb12204eaa8138e0630
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783244"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>Definicji XOML przepływu pracy i kluczy pamięci podręcznej użyciu usługi SqlTrackingService zmieniła się z MD5 SHA256

|   |   |
|---|---|
|Szczegóły|Środowisko wykonawcze przepływów pracy w zachowuje pamięć podręczna definicji przepływu pracy w pliku XOML. Użyciu usługi SqlTrackingService przechowuje także pamięć podręczna, która jest kluczach ciągów. Te pamięci podręczne są dostosowane przy wartości, które zawierają sumy kontrolnej wartość skrótu. W .NET Framework 4.7.2 i starszych wersji tej sumy kontrolnej mieszania używany algorytmu MD5, który spowodował problemów w systemach z obsługą standardu FIPS. Począwszy od .NET Framework 4.8 algorytm używany jest algorytm SHA256. Nie powinny istnieć problem ze zgodnością z tą zmianą, ponieważ wartości są ponownie obliczane każdym uruchomieniu środowiska wykonawczego przepływów pracy i użyciu usługi SqlTrackingService. Jednak udostępniliśmy Osobliwości, aby umożliwić klientom powrócić do użycia, starszego algorytmu wyznaczania wartości skrótu, jeśli to konieczne.|
|Sugestia|Jeżeli ta zmiana stanowi problem podczas wykonywania przepływów pracy, spróbuj ustawić jedną lub obie <code>AppContext</code> przełączników:<ul><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; na wartość true.</li><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; na wartość true.</li></ul>W kodzie:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>Lub w pliku konfiguracji (musi to być w pliku konfiguracji dla aplikacji, która tworzy <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.8|
|Typ|Przekierowanie|
