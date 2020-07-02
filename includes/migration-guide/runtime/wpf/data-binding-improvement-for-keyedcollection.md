---
ms.openlocfilehash: beb869208e8d48d762d94b5989a558fa2f1aaf29
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622109"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="00edb-101">Poprawa powiązania danych dla elementu prebindingcollection</span><span class="sxs-lookup"><span data-stu-id="00edb-101">Data Binding improvement for KeyedCollection</span></span>

#### <a name="details"></a><span data-ttu-id="00edb-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="00edb-102">Details</span></span>

<span data-ttu-id="00edb-103">Naprawiono <xref:System.Windows.Data.Binding> nieprawidłowe użycie indeksatora IList, gdy obiekt źródłowy deklaruje niestandardowy indeksator o tym samym podpisie (na przykład, &lt; TItemcollection int, niestandardowa &gt; ).</span><span class="sxs-lookup"><span data-stu-id="00edb-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (for example, KeyedCollection&lt;int,TItem&gt;).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="00edb-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="00edb-104">Suggestion</span></span>

<span data-ttu-id="00edb-105">Aby można było korzystać z tej zmiany w aplikacji, która jest przeznaczona dla starszej wersji, należy ją uruchomić w .NET Framework 4,8 lub nowszej i musimy zadecydować o zmianie, dodając następujący [przełącznik AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do <code>&lt;runtime&gt;</code> sekcji pliku konfiguracyjnego aplikacji i ustawiając go na <code>false</code> :</span><span class="sxs-lookup"><span data-stu-id="00edb-105">In order for an application that targets an older version to benefit from this change, it must run on the .NET Framework 4.8 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="00edb-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="00edb-106">Name</span></span>    | <span data-ttu-id="00edb-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="00edb-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="00edb-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="00edb-108">Scope</span></span>   |<span data-ttu-id="00edb-109">Duży</span><span class="sxs-lookup"><span data-stu-id="00edb-109">Major</span></span>|
|<span data-ttu-id="00edb-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="00edb-110">Version</span></span>|<span data-ttu-id="00edb-111">4,8</span><span class="sxs-lookup"><span data-stu-id="00edb-111">4.8</span></span>|
|<span data-ttu-id="00edb-112">Typ</span><span class="sxs-lookup"><span data-stu-id="00edb-112">Type</span></span>|<span data-ttu-id="00edb-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="00edb-113">Runtime</span></span>|
