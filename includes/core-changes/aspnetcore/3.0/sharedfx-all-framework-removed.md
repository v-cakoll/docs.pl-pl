---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394440"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="3c2ba-101">Udostępnione środowisko: Usunięto Microsoft. AspNetCore. All</span><span class="sxs-lookup"><span data-stu-id="3c2ba-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="3c2ba-102">Począwszy od ASP.NET Core 3,0, pakiet "`Microsoft.AspNetCore.All`" oraz zgodna struktura współdzielona `Microsoft.AspNetCore.All` nie są już generowane.</span><span class="sxs-lookup"><span data-stu-id="3c2ba-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="3c2ba-103">Ten pakiet jest dostępny w ASP.NET Core 2,2 i nadal będzie otrzymywać aktualizacje obsługi w programie ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="3c2ba-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3c2ba-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="3c2ba-104">Version introduced</span></span>

<span data-ttu-id="3c2ba-105">3.0</span><span class="sxs-lookup"><span data-stu-id="3c2ba-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3c2ba-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="3c2ba-106">Old behavior</span></span>

<span data-ttu-id="3c2ba-107">Aplikacje mogą korzystać z pakietu "`Microsoft.AspNetCore.All`" jako docelowej platformy współdzielonej `Microsoft.AspNetCore.All` na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3c2ba-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3c2ba-108">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="3c2ba-108">New behavior</span></span>

<span data-ttu-id="3c2ba-109">Platforma .NET Core 3,0 nie obejmuje współdzielonej platformy `Microsoft.AspNetCore.All`.</span><span class="sxs-lookup"><span data-stu-id="3c2ba-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3c2ba-110">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="3c2ba-110">Reason for change</span></span>

<span data-ttu-id="3c2ba-111">Pakiet "`Microsoft.AspNetCore.All`" zawiera dużą liczbę zależności zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="3c2ba-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3c2ba-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="3c2ba-112">Recommended action</span></span>

<span data-ttu-id="3c2ba-113">Migruj projekt, aby użyć platformy `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="3c2ba-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="3c2ba-114">Składniki, które wcześniej były dostępne w `Microsoft.AspNetCore.All`, są nadal dostępne w programie NuGet.</span><span class="sxs-lookup"><span data-stu-id="3c2ba-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="3c2ba-115">Te składniki są teraz wdrażane wraz z aplikacją, a nie uwzględniane w strukturze udostępnionej.</span><span class="sxs-lookup"><span data-stu-id="3c2ba-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="3c2ba-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="3c2ba-116">Category</span></span>

<span data-ttu-id="3c2ba-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3c2ba-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3c2ba-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3c2ba-118">Affected APIs</span></span>

<span data-ttu-id="3c2ba-119">Brak</span><span class="sxs-lookup"><span data-stu-id="3c2ba-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
