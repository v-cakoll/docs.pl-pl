---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344319"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="2a5de-101">Brzytwa: Kompilacja runtime przeniesiona do pakietu</span><span class="sxs-lookup"><span data-stu-id="2a5de-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="2a5de-102">Obsługa kompilacji w czasie wykonywania widoków Razor i Stron Razor została przeniesiona do oddzielnego pakietu.</span><span class="sxs-lookup"><span data-stu-id="2a5de-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2a5de-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2a5de-103">Version introduced</span></span>

<span data-ttu-id="2a5de-104">3.0</span><span class="sxs-lookup"><span data-stu-id="2a5de-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2a5de-105">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="2a5de-105">Old behavior</span></span>

<span data-ttu-id="2a5de-106">Kompilacja w czasie wykonywania jest dostępna bez konieczności dodatkowych pakietów.</span><span class="sxs-lookup"><span data-stu-id="2a5de-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2a5de-107">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="2a5de-107">New behavior</span></span>

<span data-ttu-id="2a5de-108">Funkcja została przeniesiona do pakietu [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)</span><span class="sxs-lookup"><span data-stu-id="2a5de-108">The functionality has been moved to the [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) package.</span></span>

<span data-ttu-id="2a5de-109">Następujące interfejsy API `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` były wcześniej dostępne w celu obsługi kompilacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2a5de-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="2a5de-110">Interfejsy API są `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`teraz dostępne za pośrednictwem .</span><span class="sxs-lookup"><span data-stu-id="2a5de-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- <span data-ttu-id="2a5de-111">`RazorViewEngineOptions.FileProviders`jest teraz`MvcRazorRuntimeCompilationOptions.FileProviders`</span><span class="sxs-lookup"><span data-stu-id="2a5de-111">`RazorViewEngineOptions.FileProviders` is now `MvcRazorRuntimeCompilationOptions.FileProviders`</span></span>
- <span data-ttu-id="2a5de-112">`RazorViewEngineOptions.AdditionalCompilationReferences`jest teraz`MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span><span class="sxs-lookup"><span data-stu-id="2a5de-112">`RazorViewEngineOptions.AdditionalCompilationReferences` is now `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span></span>

<span data-ttu-id="2a5de-113">Ponadto `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` został usunięty.</span><span class="sxs-lookup"><span data-stu-id="2a5de-113">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="2a5de-114">Ponowna kompilacja zmian plików jest domyślnie `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` włączona, odwołując się do pakietu.</span><span class="sxs-lookup"><span data-stu-id="2a5de-114">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2a5de-115">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="2a5de-115">Reason for change</span></span>

<span data-ttu-id="2a5de-116">Ta zmiana była konieczna, aby usunąć zależność ASP.NET core współużytkowane struktury na Roslyn.</span><span class="sxs-lookup"><span data-stu-id="2a5de-116">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2a5de-117">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="2a5de-117">Recommended action</span></span>

<span data-ttu-id="2a5de-118">Aplikacje, które wymagają kompilacji w czasie wykonywania lub ponownej kompilacji plików Razor powinny wykonać następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="2a5de-118">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="2a5de-119">Dodaj odwołanie do `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` pakietu.</span><span class="sxs-lookup"><span data-stu-id="2a5de-119">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="2a5de-120">Zaktualizuj `Startup.ConfigureServices` metodę projektu, aby uwzględnić `AddRazorRuntimeCompilation`wywołanie .</span><span class="sxs-lookup"><span data-stu-id="2a5de-120">Update the project's `Startup.ConfigureServices` method to include a call to `AddRazorRuntimeCompilation`.</span></span> <span data-ttu-id="2a5de-121">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2a5de-121">For example:</span></span>

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="2a5de-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="2a5de-122">Category</span></span>

<span data-ttu-id="2a5de-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2a5de-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2a5de-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="2a5de-124">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
