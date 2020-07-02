---
ms.openlocfilehash: 7a7ecf052276fe8e62463498b83230d466630c79
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616297"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>Klucze XOML i SqlTrackingService pamięci podręcznej przepływu pracy zmieniły się z MD5 na SHA256

#### <a name="details"></a>Szczegóły

Środowisko uruchomieniowe przepływu pracy w programie przechowuje w pamięci podręcznej definicje przepływów pracy zdefiniowane w pliku XOML. SqlTrackingService przechowuje również pamięć podręczną, która jest określana przez ciągi. Te pamięci podręczne są oparte na wartościach, które zawierają wartość skrótu sumy kontrolnej. W .NET Framework 4.7.2 i starszych wersjach tego skrótu sumy kontrolnej używał algorytmu MD5, który spowodował problemy w systemach z obsługą FIPS. Począwszy od .NET Framework 4,8, używany algorytm to SHA256. Ta zmiana nie powinna być przyczyną problemu ze zgodnością, ponieważ wartości są ponownie obliczane przy każdym uruchomieniu środowiska uruchomieniowego przepływu pracy i SqlTrackingService. Jednak firma Microsoft udostępniła osobliwości, aby umożliwić klientom przywrócenie zgodności ze starszym algorytmem wyznaczania wartości skrótu, w razie potrzeby.

#### <a name="suggestion"></a>Sugestia

Jeśli ta zmiana spowoduje problem podczas wykonywania przepływów pracy, spróbuj ustawić jeden lub oba `AppContext` przełączniki:

- &quot;Switch.System Workflow. Runtime. UseLegacyHashForWorkflowDefinitionDispenserCacheKey &quot; to true.
- &quot;Switch.System Workflow. Runtime. UseLegacyHashForSqlTrackingCacheKey &quot; to true.
W kodzie:

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>

Lub w pliku konfiguracyjnym (musi być w pliku konfiguracji dla aplikacji, która tworzy <xref:System.Workflow.Runtime.WorkflowRuntime> obiekt):

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4,8         |
| Typ    | Przekierowanie |
