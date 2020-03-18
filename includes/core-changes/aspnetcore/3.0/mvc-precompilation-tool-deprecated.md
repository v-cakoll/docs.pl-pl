---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901832"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="6000e-101">MVC: Przestarzałe narzędzie kompilacji wstępnej</span><span class="sxs-lookup"><span data-stu-id="6000e-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="6000e-102">W ASP.NET Core 1.1 wprowadzono pakiet `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (narzędzie do wstępnej kompilacji MVC), aby dodać obsługę kompilacji plików Razor w czasie publikacji (plików*cshtml).*</span><span class="sxs-lookup"><span data-stu-id="6000e-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="6000e-103">W ASP.NET Core 2.1, [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) został wprowadzony w celu rozszerzenia na funkcje narzędzia wstępnej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6000e-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="6000e-104">Zestaw Razor SDK dodał obsługę kompilacji i publikowania w czasie kompilacji plików Razor.</span><span class="sxs-lookup"><span data-stu-id="6000e-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="6000e-105">Zestaw SDK sprawdza poprawność plików *cshtml w* czasie kompilacji, jednocześnie poprawiając czas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6000e-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="6000e-106">Zestaw SDK razor jest domyślnie włączony i nie jest wymagany gest, aby zacząć go używać.</span><span class="sxs-lookup"><span data-stu-id="6000e-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="6000e-107">W ASP.NET Core 3.0 usunięto narzędzie ASP.NET Core 1.1-era MVC prekompilacji.</span><span class="sxs-lookup"><span data-stu-id="6000e-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="6000e-108">Wcześniejsze wersje pakietów będą nadal otrzymywać ważne poprawki błędów i zabezpieczeń w wydaniu poprawki.</span><span class="sxs-lookup"><span data-stu-id="6000e-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6000e-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="6000e-109">Version introduced</span></span>

<span data-ttu-id="6000e-110">3.0</span><span class="sxs-lookup"><span data-stu-id="6000e-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6000e-111">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="6000e-111">Old behavior</span></span>

<span data-ttu-id="6000e-112">Pakiet `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` został użyty do wstępnej kompilacji widoków MVC Razor.</span><span class="sxs-lookup"><span data-stu-id="6000e-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6000e-113">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="6000e-113">New behavior</span></span>

<span data-ttu-id="6000e-114">Zestaw SDK Razor natywnie obsługuje tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="6000e-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="6000e-115">Pakiet `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` nie jest już aktualizowany.</span><span class="sxs-lookup"><span data-stu-id="6000e-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6000e-116">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="6000e-116">Reason for change</span></span>

<span data-ttu-id="6000e-117">Zestaw SDK Razor zapewnia więcej funkcjonalności i weryfikuje poprawność plików *cshtml* w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6000e-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="6000e-118">Zestaw SDK poprawia również czas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6000e-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6000e-119">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="6000e-119">Recommended action</span></span>

<span data-ttu-id="6000e-120">Dla użytkowników ASP.NET Core 2.1 lub nowszej, zaktualizuj, aby użyć natywnej obsługi wstępnej kompilacji w [zestawie Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="6000e-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="6000e-121">Jeśli błędy lub brakujące funkcje uniemożliwiają migrację do zestaw SDK Razor, otwórz problem w [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="6000e-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="6000e-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="6000e-122">Category</span></span>

<span data-ttu-id="6000e-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6000e-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6000e-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6000e-124">Affected APIs</span></span>

<span data-ttu-id="6000e-125">Brak</span><span class="sxs-lookup"><span data-stu-id="6000e-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
