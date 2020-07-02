---
ms.openlocfilehash: 4303b177ffe01328965c909a5a3809414fcead91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614931"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a><span data-ttu-id="50338-101">Domyślny algorytm wyznaczania wartości skrótu dla kompilatora znaczników języka WPF jest teraz SHA256</span><span class="sxs-lookup"><span data-stu-id="50338-101">The default hash algorithm for WPF's Markup Compiler is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="50338-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="50338-102">Details</span></span>

<span data-ttu-id="50338-103">Program WPF MarkupCompiler udostępnia usługi kompilacji dla plików znaczników XAML.</span><span class="sxs-lookup"><span data-stu-id="50338-103">The WPF MarkupCompiler provides compilation services for XAML markup files.</span></span>  <span data-ttu-id="50338-104">W .NET Framework 4.7.1 i starszych wersjach domyślny algorytm wyznaczania wartości skrótu używany dla sum kontrolnych to SHA1.</span><span class="sxs-lookup"><span data-stu-id="50338-104">In the .NET Framework 4.7.1 and earlier versions, the default hash algorithm used for checksums was SHA1.</span></span> <span data-ttu-id="50338-105">Z powodu niedawnych problemów z zabezpieczeniami algorytmem SHA1 ta wartość domyślna została zmieniona na SHA256, począwszy od .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="50338-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.2.</span></span>  <span data-ttu-id="50338-106">Ta zmiana ma wpływ na wszystkie generowanie sum kontrolnych dla plików znaczników podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="50338-106">This change affects all checksum generation for markup files during compilation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="50338-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="50338-107">Suggestion</span></span>

<span data-ttu-id="50338-108">Deweloper, który jest ukierunkowany na .NET Framework 4.7.2 lub nowszy i chce powrócić do zachowania skrótu SHA1, musi ustawić następującą flagę AppContext.</span><span class="sxs-lookup"><span data-stu-id="50338-108">A developer who targets .NET Framework 4.7.2 or greater and wants to revert to SHA1 hashing behavior must set the following AppContext flag.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="50338-109">Deweloper, który chce wykorzystać mieszanie SHA256 podczas określania wersji platformy pod kątem platformy .NET 4.7.2, musi ustawić poniżej flagę AppContext.</span><span class="sxs-lookup"><span data-stu-id="50338-109">A developer who wants to utilize SHA256 hashing while targeting a framework version below .NET 4.7.2 must set the below AppContext flag.</span></span>  <span data-ttu-id="50338-110">Należy pamiętać, że zainstalowana wersja .NET Framework musi być 4.7.2 lub nowsza.</span><span class="sxs-lookup"><span data-stu-id="50338-110">Note that the installed version of the .NET Framework must be 4.7.2 or greater.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="50338-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="50338-111">Name</span></span>    | <span data-ttu-id="50338-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="50338-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="50338-113">Zakres</span><span class="sxs-lookup"><span data-stu-id="50338-113">Scope</span></span>   | <span data-ttu-id="50338-114">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="50338-114">Transparent</span></span> |
| <span data-ttu-id="50338-115">Wersja</span><span class="sxs-lookup"><span data-stu-id="50338-115">Version</span></span> | <span data-ttu-id="50338-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="50338-116">4.7.2</span></span>       |
| <span data-ttu-id="50338-117">Typ</span><span class="sxs-lookup"><span data-stu-id="50338-117">Type</span></span>    | <span data-ttu-id="50338-118">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="50338-118">Retargeting</span></span> |
