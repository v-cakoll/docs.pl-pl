---
ms.openlocfilehash: 2aa424ff5e3308b730c22cb865993d4100f193cc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616302"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a><span data-ttu-id="306ca-101">Sumy kontrolne pliku XOML przepływu pracy zmieniono z MD5 na SHA256</span><span class="sxs-lookup"><span data-stu-id="306ca-101">Workflow XOML file checksums changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="306ca-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="306ca-102">Details</span></span>

<span data-ttu-id="306ca-103">W celu obsługi debugowania przepływów pracy opartych na plikach xoml przy użyciu programu Visual Studio, gdy projekty przepływu pracy zawierające pliki XOML są kompilowane, suma kontrolna zawartości pliku XOML jest uwzględniana w kodzie wygenerowanym jako <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> wartość.</span><span class="sxs-lookup"><span data-stu-id="306ca-103">To support debugging XOML-based workflows with Visual Studio, when workflow projects containing XOML files build, a checksum of the contents of the XOML file is included in the code generated as a <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="306ca-104">W .NET Framework 4.7.2 i starszych wersjach tego skrótu sumy kontrolnej używał algorytmu MD5, który spowodował problemy w systemach z obsługą FIPS.</span><span class="sxs-lookup"><span data-stu-id="306ca-104">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="306ca-105">Począwszy od .NET Framework 4,8, używany algorytm to SHA256.</span><span class="sxs-lookup"><span data-stu-id="306ca-105">Starting with the .NET Framework 4.8, the algorithm used is SHA256.</span></span> <span data-ttu-id="306ca-106">Aby można było uaktualniana z WorkflowMarkupSourceAttribute. MD5Digest, używane są tylko pierwsze 16 bajtów wygenerowanej sumy kontrolnej. Może to spowodować problemy podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="306ca-106">To be compatibile with the WorkflowMarkupSourceAttribute.MD5Digest, only the first 16 bytes of the generated checksum are used.This may cause problems during debugging.</span></span> <span data-ttu-id="306ca-107">Może być konieczne ponowne skompilowanie projektu.</span><span class="sxs-lookup"><span data-stu-id="306ca-107">You may need to re-build your project.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="306ca-108">Sugestia</span><span class="sxs-lookup"><span data-stu-id="306ca-108">Suggestion</span></span>

<span data-ttu-id="306ca-109">Jeśli ponowne skompilowanie projektu nie rozwiąże problemu, spróbuj ustawić `AppContext` przełącznik &quot;Switch.System. Workflow. ComponentModel. UseLegacyHashForXomlFileChecksum &quot; na true. W kodzie:</span><span class="sxs-lookup"><span data-stu-id="306ca-109">If re-building your project does not solve the problem, try setting the `AppContext` switch &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; to true.In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="306ca-110">Lub w pliku konfiguracyjnym (musi być w MSBuild.exe.config dla MSBuild.exe, którego używasz):</span><span class="sxs-lookup"><span data-stu-id="306ca-110">Or in a configuration file (this needs to be in MSBuild.exe.config for the MSBuild.exe that you are using):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="306ca-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="306ca-111">Name</span></span>    | <span data-ttu-id="306ca-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="306ca-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="306ca-113">Zakres</span><span class="sxs-lookup"><span data-stu-id="306ca-113">Scope</span></span>   | <span data-ttu-id="306ca-114">Mały</span><span class="sxs-lookup"><span data-stu-id="306ca-114">Minor</span></span>       |
| <span data-ttu-id="306ca-115">Wersja</span><span class="sxs-lookup"><span data-stu-id="306ca-115">Version</span></span> | <span data-ttu-id="306ca-116">4,8</span><span class="sxs-lookup"><span data-stu-id="306ca-116">4.8</span></span>         |
| <span data-ttu-id="306ca-117">Typ</span><span class="sxs-lookup"><span data-stu-id="306ca-117">Type</span></span>    | <span data-ttu-id="306ca-118">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="306ca-118">Retargeting</span></span> |
