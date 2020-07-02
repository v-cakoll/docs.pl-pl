---
ms.openlocfilehash: 7a7ecf052276fe8e62463498b83230d466630c79
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616297"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a><span data-ttu-id="37eb1-101">Klucze XOML i SqlTrackingService pamięci podręcznej przepływu pracy zmieniły się z MD5 na SHA256</span><span class="sxs-lookup"><span data-stu-id="37eb1-101">Workflow XOML definition and SqlTrackingService cache keys changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="37eb1-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="37eb1-102">Details</span></span>

<span data-ttu-id="37eb1-103">Środowisko uruchomieniowe przepływu pracy w programie przechowuje w pamięci podręcznej definicje przepływów pracy zdefiniowane w pliku XOML.</span><span class="sxs-lookup"><span data-stu-id="37eb1-103">The Workflow Runtime in keeps a cache of workflow definitions defined in XOML.</span></span> <span data-ttu-id="37eb1-104">SqlTrackingService przechowuje również pamięć podręczną, która jest określana przez ciągi.</span><span class="sxs-lookup"><span data-stu-id="37eb1-104">The SqlTrackingService also keeps a cache that is keyed by strings.</span></span> <span data-ttu-id="37eb1-105">Te pamięci podręczne są oparte na wartościach, które zawierają wartość skrótu sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="37eb1-105">These caches are keyed by values that include checksum hash value.</span></span> <span data-ttu-id="37eb1-106">W .NET Framework 4.7.2 i starszych wersjach tego skrótu sumy kontrolnej używał algorytmu MD5, który spowodował problemy w systemach z obsługą FIPS.</span><span class="sxs-lookup"><span data-stu-id="37eb1-106">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="37eb1-107">Począwszy od .NET Framework 4,8, używany algorytm to SHA256. Ta zmiana nie powinna być przyczyną problemu ze zgodnością, ponieważ wartości są ponownie obliczane przy każdym uruchomieniu środowiska uruchomieniowego przepływu pracy i SqlTrackingService.</span><span class="sxs-lookup"><span data-stu-id="37eb1-107">Starting with the .NET Framework 4.8, the algorithm used is SHA256.There shouldn't be a compatibility issue with this change because the values are recalculated each time the Workflow Runtime and SqlTrackingService is started.</span></span> <span data-ttu-id="37eb1-108">Jednak firma Microsoft udostępniła osobliwości, aby umożliwić klientom przywrócenie zgodności ze starszym algorytmem wyznaczania wartości skrótu, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="37eb1-108">However, we have provided quirks to allow customers to revert back to usage of the legacy hashing algorithm, if necessary.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="37eb1-109">Sugestia</span><span class="sxs-lookup"><span data-stu-id="37eb1-109">Suggestion</span></span>

<span data-ttu-id="37eb1-110">Jeśli ta zmiana spowoduje problem podczas wykonywania przepływów pracy, spróbuj ustawić jeden lub oba `AppContext` przełączniki:</span><span class="sxs-lookup"><span data-stu-id="37eb1-110">If this change presents a problem when executing workflows, try setting one or both of the `AppContext` switches:</span></span>

- <span data-ttu-id="37eb1-111">&quot;Switch.System Workflow. Runtime. UseLegacyHashForWorkflowDefinitionDispenserCacheKey &quot; to true.</span><span class="sxs-lookup"><span data-stu-id="37eb1-111">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; to true.</span></span>
- <span data-ttu-id="37eb1-112">&quot;Switch.System Workflow. Runtime. UseLegacyHashForSqlTrackingCacheKey &quot; to true.</span><span class="sxs-lookup"><span data-stu-id="37eb1-112">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; to true.</span></span>
<span data-ttu-id="37eb1-113">W kodzie:</span><span class="sxs-lookup"><span data-stu-id="37eb1-113">In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="37eb1-114">Lub w pliku konfiguracyjnym (musi być w pliku konfiguracji dla aplikacji, która tworzy <xref:System.Workflow.Runtime.WorkflowRuntime> obiekt):</span><span class="sxs-lookup"><span data-stu-id="37eb1-114">Or in the configuration file (this needs to be in the config file for the application that is creating the <xref:System.Workflow.Runtime.WorkflowRuntime> object):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="37eb1-115">Nazwa</span><span class="sxs-lookup"><span data-stu-id="37eb1-115">Name</span></span>    | <span data-ttu-id="37eb1-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="37eb1-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="37eb1-117">Zakres</span><span class="sxs-lookup"><span data-stu-id="37eb1-117">Scope</span></span>   | <span data-ttu-id="37eb1-118">Mały</span><span class="sxs-lookup"><span data-stu-id="37eb1-118">Minor</span></span>       |
| <span data-ttu-id="37eb1-119">Wersja</span><span class="sxs-lookup"><span data-stu-id="37eb1-119">Version</span></span> | <span data-ttu-id="37eb1-120">4,8</span><span class="sxs-lookup"><span data-stu-id="37eb1-120">4.8</span></span>         |
| <span data-ttu-id="37eb1-121">Typ</span><span class="sxs-lookup"><span data-stu-id="37eb1-121">Type</span></span>    | <span data-ttu-id="37eb1-122">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="37eb1-122">Retargeting</span></span> |
