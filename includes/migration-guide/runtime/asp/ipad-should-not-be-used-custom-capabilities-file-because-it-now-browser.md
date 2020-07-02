---
ms.openlocfilehash: af10716fe5f4c07091e8605cdf620e4a499fb1e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620182"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a><span data-ttu-id="30cd6-101">Tabletu IPad nie należy używać w pliku możliwości niestandardowych, ponieważ jest teraz funkcją przeglądarki</span><span class="sxs-lookup"><span data-stu-id="30cd6-101">IPad should not be used in custom capabilities file because it is now a browser capability</span></span>

#### <a name="details"></a><span data-ttu-id="30cd6-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="30cd6-102">Details</span></span>

<span data-ttu-id="30cd6-103">Począwszy od .NET Framework 4,5, iPad jest identyfikatorem w domyślnym pliku możliwości przeglądarki ASP.NET, dlatego nie należy go używać w pliku możliwości niestandardowych</span><span class="sxs-lookup"><span data-stu-id="30cd6-103">Beginning in .NET Framework 4.5, iPad is an identifier in the default ASP.NET browser capabilities file, so it should not be used in a custom capabilities file</span></span>

#### <a name="suggestion"></a><span data-ttu-id="30cd6-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="30cd6-104">Suggestion</span></span>

<span data-ttu-id="30cd6-105">Jeśli są wymagane możliwości specyficzne dla tabletu iPad, należy zmodyfikować zachowanie urządzenia iPad przez ustawienie funkcji na wstępnie zdefiniowanej bramie iPad refID, &quot; &quot; zamiast wygenerowania nowego &quot; identyfikatora iPad &quot; przez dopasowanie agenta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="30cd6-105">If iPad-specific capabilities are required, it is necessary to modify iPad behavior by setting capabilities on the pre-defined gateway refID &quot;IPad&quot; instead of by generating a new &quot;IPad&quot; ID by user agent matching.</span></span>

| <span data-ttu-id="30cd6-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="30cd6-106">Name</span></span>    | <span data-ttu-id="30cd6-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="30cd6-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="30cd6-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="30cd6-108">Scope</span></span>   |<span data-ttu-id="30cd6-109">Brzeg</span><span class="sxs-lookup"><span data-stu-id="30cd6-109">Edge</span></span>|
|<span data-ttu-id="30cd6-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="30cd6-110">Version</span></span>|<span data-ttu-id="30cd6-111">4.5</span><span class="sxs-lookup"><span data-stu-id="30cd6-111">4.5</span></span>|
|<span data-ttu-id="30cd6-112">Typ</span><span class="sxs-lookup"><span data-stu-id="30cd6-112">Type</span></span>|<span data-ttu-id="30cd6-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="30cd6-113">Runtime</span></span>|
