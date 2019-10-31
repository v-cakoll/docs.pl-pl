---
ms.openlocfilehash: 3f702febc78488b9413ec9303ded211493650f02
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198532"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="12ef6-101">MVC: Narzędzie wstępnej kompilacji zostało zaniechane</span><span class="sxs-lookup"><span data-stu-id="12ef6-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="12ef6-102">W ASP.NET Core 1,1 został wprowadzony pakiet `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (Narzędzie wstępnej kompilacji MVC) w celu dodania obsługi kompilacji plików Razor ( *. cshtml* ) w czasie publikowania.</span><span class="sxs-lookup"><span data-stu-id="12ef6-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="12ef6-103">W ASP.NET Core 2,1 został wprowadzony [zestaw SDK Razor](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) do rozwinięcia przy użyciu funkcji narzędzia prekompilacji.</span><span class="sxs-lookup"><span data-stu-id="12ef6-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="12ef6-104">Zestaw SDK Razor dodaliśmy obsługę kompilacji i kompilowania plików Razor w czasie kompilowania i publikowania.</span><span class="sxs-lookup"><span data-stu-id="12ef6-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="12ef6-105">Zestaw SDK sprawdza poprawność plików *. cshtml* w czasie kompilacji podczas poprawiania czasu uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="12ef6-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="12ef6-106">Zestaw SDK Razor jest domyślnie włączony i żaden gest nie jest wymagany do rozpoczęcia korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="12ef6-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="12ef6-107">W ASP.NET Core 3,0 zostało usunięte narzędzie wstępnej kompilacji MVC ASP.NET Core 1,1.</span><span class="sxs-lookup"><span data-stu-id="12ef6-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="12ef6-108">Wcześniejsze wersje pakietu będą nadal otrzymywać ważne poprawki błędów i zabezpieczeń w wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="12ef6-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="12ef6-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12ef6-109">Version introduced</span></span>

<span data-ttu-id="12ef6-110">3.0</span><span class="sxs-lookup"><span data-stu-id="12ef6-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="12ef6-111">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="12ef6-111">Old behavior</span></span>

<span data-ttu-id="12ef6-112">Pakiet `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` został użyty do wstępnego skompilowania widoków Razor MVC.</span><span class="sxs-lookup"><span data-stu-id="12ef6-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="12ef6-113">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="12ef6-113">New behavior</span></span>

<span data-ttu-id="12ef6-114">Zestaw Razor SDK natywnie obsługuje tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="12ef6-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="12ef6-115">Pakiet `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` nie jest już aktualizowany.</span><span class="sxs-lookup"><span data-stu-id="12ef6-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="12ef6-116">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="12ef6-116">Reason for change</span></span>

<span data-ttu-id="12ef6-117">Zestaw SDK Razor oferuje większą funkcjonalność i sprawdza poprawność plików *. cshtml* w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="12ef6-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="12ef6-118">Zestaw SDK poprawia również czas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="12ef6-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="12ef6-119">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="12ef6-119">Recommended action</span></span>

<span data-ttu-id="12ef6-120">W przypadku użytkowników ASP.NET Core 2,1 lub nowszych należy zaktualizować do korzystania z natywnej obsługi wstępnej kompilacji w [zestawie Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="12ef6-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="12ef6-121">Jeśli błędy lub brakujące funkcje uniemożliwiają migrację do zestawu Razor SDK, Otwórz problem na [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span><span class="sxs-lookup"><span data-stu-id="12ef6-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="12ef6-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="12ef6-122">Category</span></span>

<span data-ttu-id="12ef6-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="12ef6-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="12ef6-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="12ef6-124">Affected APIs</span></span>

<span data-ttu-id="12ef6-125">Brak</span><span class="sxs-lookup"><span data-stu-id="12ef6-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
