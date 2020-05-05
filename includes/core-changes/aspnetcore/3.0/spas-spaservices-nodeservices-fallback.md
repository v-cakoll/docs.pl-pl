---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522655"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="3c458-101">Aplikacji jednostronicowych: SpaServices i NodeServices nie są już z powrotem do rejestratora konsoli</span><span class="sxs-lookup"><span data-stu-id="3c458-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="3c458-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType>nie <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> będą wyświetlane dzienniki konsoli, chyba że skonfigurowano rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="3c458-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3c458-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="3c458-103">Version introduced</span></span>

<span data-ttu-id="3c458-104">3.0</span><span class="sxs-lookup"><span data-stu-id="3c458-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3c458-105">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="3c458-105">Old behavior</span></span>

<span data-ttu-id="3c458-106">`Microsoft.AspNetCore.SpaServices`służy `Microsoft.AspNetCore.NodeServices` do automatycznego tworzenia rejestratora konsoli, gdy rejestrowanie nie jest skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="3c458-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3c458-107">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="3c458-107">New behavior</span></span>

<span data-ttu-id="3c458-108">`Microsoft.AspNetCore.SpaServices`nie `Microsoft.AspNetCore.NodeServices` będą wyświetlane dzienniki konsoli, chyba że skonfigurowano rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="3c458-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3c458-109">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="3c458-109">Reason for change</span></span>

<span data-ttu-id="3c458-110">Istnieje potrzeba dopasowania metody rejestrowania w innych pakietach ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3c458-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3c458-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="3c458-111">Recommended action</span></span>

<span data-ttu-id="3c458-112">Jeśli stare zachowanie jest wymagane, aby skonfigurować rejestrowanie konsoli, Dodaj `services.AddLogging(builder => builder.AddConsole())` do `Setup.ConfigureServices` metody.</span><span class="sxs-lookup"><span data-stu-id="3c458-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="3c458-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="3c458-113">Category</span></span>

<span data-ttu-id="3c458-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3c458-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3c458-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3c458-115">Affected APIs</span></span>

<span data-ttu-id="3c458-116">Brak</span><span class="sxs-lookup"><span data-stu-id="3c458-116">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
