---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522655"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="f4dcb-101">Aplikacji jednostronicowych: SpaServices i NodeServices nie są już z powrotem do rejestratora konsoli</span><span class="sxs-lookup"><span data-stu-id="f4dcb-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="f4dcb-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> i <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> nie będą wyświetlane dzienniki konsoli, chyba że rejestrowanie jest skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="f4dcb-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f4dcb-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="f4dcb-103">Version introduced</span></span>

<span data-ttu-id="f4dcb-104">3.0</span><span class="sxs-lookup"><span data-stu-id="f4dcb-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f4dcb-105">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="f4dcb-105">Old behavior</span></span>

<span data-ttu-id="f4dcb-106">`Microsoft.AspNetCore.SpaServices` i `Microsoft.AspNetCore.NodeServices` używane do automatycznego tworzenia rejestratora konsoli, gdy rejestrowanie nie jest skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="f4dcb-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f4dcb-107">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="f4dcb-107">New behavior</span></span>

<span data-ttu-id="f4dcb-108">`Microsoft.AspNetCore.SpaServices` i `Microsoft.AspNetCore.NodeServices` nie będą wyświetlane dzienniki konsoli, chyba że rejestrowanie jest skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="f4dcb-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f4dcb-109">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="f4dcb-109">Reason for change</span></span>

<span data-ttu-id="f4dcb-110">Istnieje potrzeba dopasowania metody rejestrowania w innych pakietach ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4dcb-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f4dcb-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="f4dcb-111">Recommended action</span></span>

<span data-ttu-id="f4dcb-112">Jeśli jest wymagane stare zachowanie, aby skonfigurować rejestrowanie konsoli, Dodaj `services.AddLogging(builder => builder.AddConsole())` do metody `Setup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="f4dcb-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="f4dcb-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="f4dcb-113">Category</span></span>

<span data-ttu-id="f4dcb-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f4dcb-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f4dcb-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f4dcb-115">Affected APIs</span></span>

<span data-ttu-id="f4dcb-116">Brak</span><span class="sxs-lookup"><span data-stu-id="f4dcb-116">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
