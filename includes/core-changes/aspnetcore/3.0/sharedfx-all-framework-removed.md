---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394440"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="f2da3-101">Udostępnione środowisko: Usunięto Microsoft. AspNetCore. All</span><span class="sxs-lookup"><span data-stu-id="f2da3-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="f2da3-102">Począwszy od ASP.NET Core 3,0, `Microsoft.AspNetCore.All` nie jest już tworzony pakiet i `Microsoft.AspNetCore.All` zgodna struktura współdzielona.</span><span class="sxs-lookup"><span data-stu-id="f2da3-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="f2da3-103">Ten pakiet jest dostępny w ASP.NET Core 2,2 i nadal będzie otrzymywać aktualizacje obsługi w programie ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="f2da3-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f2da3-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="f2da3-104">Version introduced</span></span>

<span data-ttu-id="f2da3-105">3.0</span><span class="sxs-lookup"><span data-stu-id="f2da3-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f2da3-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="f2da3-106">Old behavior</span></span>

<span data-ttu-id="f2da3-107">Aplikacje mogą używać `Microsoft.AspNetCore.All` pakietu dla platformy `Microsoft.AspNetCore.All` udostępnionej w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f2da3-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f2da3-108">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="f2da3-108">New behavior</span></span>

<span data-ttu-id="f2da3-109">Platforma .NET Core 3,0 nie obejmuje `Microsoft.AspNetCore.All` współdzielonej struktury.</span><span class="sxs-lookup"><span data-stu-id="f2da3-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f2da3-110">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="f2da3-110">Reason for change</span></span>

<span data-ttu-id="f2da3-111">`Microsoft.AspNetCore.All` Pakietbinding zawiera dużą liczbę zależności zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="f2da3-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f2da3-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="f2da3-112">Recommended action</span></span>

<span data-ttu-id="f2da3-113">Migruj projekt, aby użyć `Microsoft.AspNetCore.App` struktury.</span><span class="sxs-lookup"><span data-stu-id="f2da3-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="f2da3-114">Składniki, które wcześniej były dostępne `Microsoft.AspNetCore.All` w programie, są nadal dostępne w programie NuGet.</span><span class="sxs-lookup"><span data-stu-id="f2da3-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="f2da3-115">Te składniki są teraz wdrażane wraz z aplikacją, a nie uwzględniane w strukturze udostępnionej.</span><span class="sxs-lookup"><span data-stu-id="f2da3-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="f2da3-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="f2da3-116">Category</span></span>

<span data-ttu-id="f2da3-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f2da3-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f2da3-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f2da3-118">Affected APIs</span></span>

<span data-ttu-id="f2da3-119">Brak</span><span class="sxs-lookup"><span data-stu-id="f2da3-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
