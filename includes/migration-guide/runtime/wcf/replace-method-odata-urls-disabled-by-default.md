---
ms.openlocfilehash: b2fcacdb02c411c4dcb12051bf0c6759faccdea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620388"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="cf40f-101">Metoda replace w adresach URL usługi OData jest domyślnie wyłączona</span><span class="sxs-lookup"><span data-stu-id="cf40f-101">The Replace method in OData URLs is disabled by default</span></span>

#### <a name="details"></a><span data-ttu-id="cf40f-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cf40f-102">Details</span></span>

<span data-ttu-id="cf40f-103">Począwszy od .NET Framework 4,5, Metoda replace w adresach URL usługi OData jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="cf40f-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="cf40f-104">Gdy funkcja zamiany OData jest wyłączona (teraz domyślnie), wszelkie żądania użytkowników, w tym funkcje Replace (rzadko występujące), zakończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="cf40f-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cf40f-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="cf40f-105">Suggestion</span></span>

<span data-ttu-id="cf40f-106">Jeśli Metoda replace jest wymagana (co jest nietypowe), można ją zmienić za pomocą ustawień konfiguracji ( <xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="cf40f-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>).</span></span> <span data-ttu-id="cf40f-107">Jednak włączona Metoda replace może otwierać luki w zabezpieczeniach i być używana tylko po dokładnym przeglądzie.</span><span class="sxs-lookup"><span data-stu-id="cf40f-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>

| <span data-ttu-id="cf40f-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cf40f-108">Name</span></span>    | <span data-ttu-id="cf40f-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="cf40f-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cf40f-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="cf40f-110">Scope</span></span>   |<span data-ttu-id="cf40f-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="cf40f-111">Edge</span></span>|
|<span data-ttu-id="cf40f-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="cf40f-112">Version</span></span>|<span data-ttu-id="cf40f-113">4.5</span><span class="sxs-lookup"><span data-stu-id="cf40f-113">4.5</span></span>|
|<span data-ttu-id="cf40f-114">Typ</span><span class="sxs-lookup"><span data-stu-id="cf40f-114">Type</span></span>|<span data-ttu-id="cf40f-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="cf40f-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cf40f-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="cf40f-116">Affected APIs</span></span>

-<xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
