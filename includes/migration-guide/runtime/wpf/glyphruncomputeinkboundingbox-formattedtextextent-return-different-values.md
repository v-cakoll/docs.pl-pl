---
ms.openlocfilehash: 00ffc782c9a15c0d88f797f52372b4658706b350
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620429"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a><span data-ttu-id="52e61-101">GlyphRun. ComputeInkBoundingBox () i FormattedText. zakres zwracają różne wartości zaczynające się na .NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="52e61-101">GlyphRun.ComputeInkBoundingBox() and FormattedText.Extent return different values beginning in .NET Framework 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="52e61-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="52e61-102">Details</span></span>

<span data-ttu-id="52e61-103">Wprowadzono ulepszenia <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> i <xref:System.Windows.Media.FormattedText.Extent> w .NET Framework 4,5 do rozwiązywania problemów, gdy pola są zbyt małe dla zawartych symboli w niektórych przypadkach w .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="52e61-103">Improvements were made to <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> and <xref:System.Windows.Media.FormattedText.Extent> in the .NET Framework 4.5 to address issues where the boxes were too small for the contained glyphs in some cases in the .NET Framework 4.0.</span></span> <span data-ttu-id="52e61-104">W wyniku tego niektóre pola ograniczające będą większe od początku .NET Framework 4,5, co spowodowało delikatne różnice w układzie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="52e61-104">As a result of this, some bounding boxes will be larger beginning in the .NET Framework 4.5, resulting in subtle differences in UI layout.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="52e61-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="52e61-105">Suggestion</span></span>

<span data-ttu-id="52e61-106">Należy pamiętać, że niektóre rozmiary pól ograniczających glify zostały powiększone.</span><span class="sxs-lookup"><span data-stu-id="52e61-106">Be aware that some glyph bounding box sizes have increased.</span></span> <span data-ttu-id="52e61-107">Te zmiany zwykle ulepszają testowanie i pole trafień, ale jeśli jest wymagane zachowanie starsze (pre-.NET 4,5), można je dodać, dodając następujący wpis do pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="52e61-107">These changes will usually improve presentation and hit box testing, but if the older (pre-.NET 4.5) behavior is desired, it can be opted into by adding the following entry to the app.config file:</span></span><pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="52e61-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="52e61-108">Name</span></span>    | <span data-ttu-id="52e61-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="52e61-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="52e61-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="52e61-110">Scope</span></span>   |<span data-ttu-id="52e61-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="52e61-111">Edge</span></span>|
|<span data-ttu-id="52e61-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="52e61-112">Version</span></span>|<span data-ttu-id="52e61-113">4.5</span><span class="sxs-lookup"><span data-stu-id="52e61-113">4.5</span></span>|
|<span data-ttu-id="52e61-114">Typ</span><span class="sxs-lookup"><span data-stu-id="52e61-114">Type</span></span>|<span data-ttu-id="52e61-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="52e61-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="52e61-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="52e61-116">Affected APIs</span></span>

-<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|
