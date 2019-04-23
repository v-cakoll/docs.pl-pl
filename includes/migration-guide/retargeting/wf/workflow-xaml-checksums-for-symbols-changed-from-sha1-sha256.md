---
ms.openlocfilehash: f814703e187726d3988787fac52e5049988fd4d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982170"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a><span data-ttu-id="a35c1-101">Zmieniła się z SHA1 SHA256 symboli, sum kontrolnych XAML przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a35c1-101">Workflow XAML checksums for symbols changed from SHA1 to SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a35c1-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a35c1-102">Details</span></span>|<span data-ttu-id="a35c1-103">Aby zapewnić obsługę debugowania programu Visual Studio, środowiska wykonawczego przepływów pracy generuje sumy kontrolnej pliku XAML przepływu pracy przy użyciu algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="a35c1-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow XAML file using a hashing algorithm.</span></span> <span data-ttu-id="a35c1-104">W .NET Framework 4.6.2 i wcześniejszych wersjach przepływ pracy sumy kontrolnej wyznaczania wartości skrótu używany algorytmu MD5, który spowodował problemów w systemach z obsługą standardu FIPS.</span><span class="sxs-lookup"><span data-stu-id="a35c1-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="a35c1-105">Począwszy od programu .NET Framework 4.7, zmieniono domyślny algorytm SHA1.</span><span class="sxs-lookup"><span data-stu-id="a35c1-105">Starting with the .NET Framework 4.7, the default algorithm was changed to SHA1.</span></span> <span data-ttu-id="a35c1-106">Począwszy od .NET Framework 4.8 zmieniono domyślny algorytm na SHA256.</span><span class="sxs-lookup"><span data-stu-id="a35c1-106">Starting with the .NET Framework 4.8, the default algorithm was changed to SHA256.</span></span>|
|<span data-ttu-id="a35c1-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="a35c1-107">Suggestion</span></span>|<span data-ttu-id="a35c1-108">Jeśli Twój kod nie może załadować wystąpienia przepływu pracy lub znalezienia odpowiednich symboli z powodu błędu sumy kontrolnej, spróbuj ustawienie <code>AppContext</code> Przełącz &quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot; na wartość true. W kodzie:</span><span class="sxs-lookup"><span data-stu-id="a35c1-108">If your code is unable to load workflow instances or to find appropriate symbols due to a checksum failure, try setting the <code>AppContext</code> switch &quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot; to true.In code:</span></span><pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot;, true);&#13;&#10;</code></pre><span data-ttu-id="a35c1-109">Lub w konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="a35c1-109">Or in configuration:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="a35c1-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="a35c1-110">Scope</span></span>|<span data-ttu-id="a35c1-111">Mały</span><span class="sxs-lookup"><span data-stu-id="a35c1-111">Minor</span></span>|
|<span data-ttu-id="a35c1-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="a35c1-112">Version</span></span>|<span data-ttu-id="a35c1-113">4.8</span><span class="sxs-lookup"><span data-stu-id="a35c1-113">4.8</span></span>|
|<span data-ttu-id="a35c1-114">Typ</span><span class="sxs-lookup"><span data-stu-id="a35c1-114">Type</span></span>|<span data-ttu-id="a35c1-115">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="a35c1-115">Retargeting</span></span>|