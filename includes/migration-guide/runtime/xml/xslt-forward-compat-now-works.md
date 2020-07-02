---
ms.openlocfilehash: e3b9711ac66901d69838de4c9f309d086b06fd4d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620514"
---
### <a name="xslt-forward-compat-now-works"></a><span data-ttu-id="431e6-101">Teraz działa progresywne przekształcenie XSLT</span><span class="sxs-lookup"><span data-stu-id="431e6-101">XSLT forward compat now works</span></span>

#### <a name="details"></a><span data-ttu-id="431e6-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="431e6-102">Details</span></span>

<span data-ttu-id="431e6-103">W .NET Framework 4, przexslt 1,0 do przodu ma następujące problemy:</span><span class="sxs-lookup"><span data-stu-id="431e6-103">In the .NET Framework 4, XSLT 1.0 forward compatibility had the following issues:</span></span><ul><li><span data-ttu-id="431e6-104">Ładowanie arkusza stylów kończyło się niepowodzeniem, jeśli jego wersja miała wartość 2.0, a analizator napotkał nierozpoznaną konstrukcję specyfikacji XSLT 1.0.</span><span class="sxs-lookup"><span data-stu-id="431e6-104">Loading a style sheet failed if its version was set to 2.0 and the parser encountered an unrecognized XSLT 1.0 construct.</span></span></li><li><span data-ttu-id="431e6-105"><code>xsl:sort</code>Konstrukcja nie może sortować danych, jeśli ustawiono wersję arkusza stylów na 1,1.</span><span class="sxs-lookup"><span data-stu-id="431e6-105">The <code>xsl:sort</code> construct failed to sort data if the style sheet version was set to 1.1.</span></span></li></ul><span data-ttu-id="431e6-106">W .NET Framework 4,5 te problemy zostały rozwiązane, a tryb zgodności z przekazywaniem do przodu XSLT 1,0 działa prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="431e6-106">In the .NET Framework 4.5, these issues have been fixed, and XSLT 1.0 forward compatibility mode works properly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="431e6-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="431e6-107">Suggestion</span></span>

<span data-ttu-id="431e6-108">W przypadku większości aplikacji nie ma to żadnego oddziaływania, jednak w niektórych przypadkach dane będą sortowane w różny sposób, gdy jest to kod XSL: sort.</span><span class="sxs-lookup"><span data-stu-id="431e6-108">Most apps should be unaffected, however data will be sorted differently in some cases now that xsl:sort is respected.</span></span> <span data-ttu-id="431e6-109">Jeśli <code>xsl:sort</code> jest używany w arkuszach stylów 1,1, potwierdź, że aplikacje nie były w zależności od kolejności danych.</span><span class="sxs-lookup"><span data-stu-id="431e6-109">If <code>xsl:sort</code> is used in 1.1 style sheets, confirm that apps were not depending on the unsorted order of data.</span></span> <span data-ttu-id="431e6-110">Jeśli aplikacje są zależne od zachowania sortowania 4,0, Usuń <code>xsl:sort</code> z arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="431e6-110">If apps rely on the 4.0 sorting behavior, remove <code>xsl:sort</code> from the style sheet.</span></span>

| <span data-ttu-id="431e6-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="431e6-111">Name</span></span>    | <span data-ttu-id="431e6-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="431e6-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="431e6-113">Zakres</span><span class="sxs-lookup"><span data-stu-id="431e6-113">Scope</span></span>   |<span data-ttu-id="431e6-114">Brzeg</span><span class="sxs-lookup"><span data-stu-id="431e6-114">Edge</span></span>|
|<span data-ttu-id="431e6-115">Wersja</span><span class="sxs-lookup"><span data-stu-id="431e6-115">Version</span></span>|<span data-ttu-id="431e6-116">4.5</span><span class="sxs-lookup"><span data-stu-id="431e6-116">4.5</span></span>|
|<span data-ttu-id="431e6-117">Typ</span><span class="sxs-lookup"><span data-stu-id="431e6-117">Type</span></span>|<span data-ttu-id="431e6-118">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="431e6-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="431e6-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="431e6-119">Affected APIs</span></span>

-<xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|
