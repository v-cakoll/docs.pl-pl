---
ms.openlocfilehash: b1fb9647091cecb80b9c2f04ec9b6bb156eb39ba
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84466879"
---
### <a name="pubternal-apis-removed"></a><span data-ttu-id="cfcc2-101">Usunięte interfejsy API "Pubternal"</span><span class="sxs-lookup"><span data-stu-id="cfcc2-101">"Pubternal" APIs removed</span></span>

<span data-ttu-id="cfcc2-102">Aby lepiej zachować publiczną powierzchnię interfejsu API ASP.NET Core, większość typów w `*.Internal` przestrzeniach nazw (nazywanych :::no-loc text="\"pubternal\""::: interfejsami API) staje się naprawdę wewnętrzna.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-102">To better maintain the public API surface of ASP.NET Core, most of the types in `*.Internal` namespaces (referred to as :::no-loc text="\"pubternal\""::: APIs) have become truly internal.</span></span> <span data-ttu-id="cfcc2-103">Elementy członkowskie w tych przestrzeniach nazw nigdy nie były obsługiwane jako interfejsy API dostępne publicznie.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-103">Members in these namespaces were never meant to be supported as public-facing APIs.</span></span> <span data-ttu-id="cfcc2-104">Interfejsy API można przerwać w mniejszych wersjach i często zostały wykonane.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-104">The APIs could break in minor releases and often did.</span></span> <span data-ttu-id="cfcc2-105">Kod, który zależy od tych interfejsów API, jest dzielony podczas aktualizacji do ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-105">Code that depends on these APIs breaks when updating to ASP.NET Core 3.0.</span></span>

<span data-ttu-id="cfcc2-106">Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore # 4932](https://github.com/dotnet/aspnetcore/issues/4932) i [dotnet/aspnetcore # 11312](https://github.com/dotnet/aspnetcore/issues/11312).</span><span class="sxs-lookup"><span data-stu-id="cfcc2-106">For more information, see [dotnet/aspnetcore#4932](https://github.com/dotnet/aspnetcore/issues/4932) and [dotnet/aspnetcore#11312](https://github.com/dotnet/aspnetcore/issues/11312).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cfcc2-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="cfcc2-107">Version introduced</span></span>

<span data-ttu-id="cfcc2-108">3.0</span><span class="sxs-lookup"><span data-stu-id="cfcc2-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="cfcc2-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="cfcc2-109">Old behavior</span></span>

<span data-ttu-id="cfcc2-110">Narażone interfejsy API są oznaczone `public` modyfikatorem dostępu i istnieją w `*.Internal` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-110">The affected APIs are marked with the `public` access modifier and exist in `*.Internal` namespaces.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="cfcc2-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="cfcc2-111">New behavior</span></span>

<span data-ttu-id="cfcc2-112">Narażone interfejsy API są oznaczone modyfikatorem dostępu [wewnętrznego](/dotnet/csharp/language-reference/keywords/internal) i nie mogą być używane przez kod poza tym zestawem.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-112">The affected APIs are marked with the [internal](/dotnet/csharp/language-reference/keywords/internal) access modifier and can no longer be used by code outside that assembly.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cfcc2-113">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="cfcc2-113">Reason for change</span></span>

<span data-ttu-id="cfcc2-114">Wskazówki dotyczące tych :::no-loc text="\"pubternal\""::: interfejsów API to:</span><span class="sxs-lookup"><span data-stu-id="cfcc2-114">The guidance for these :::no-loc text="\"pubternal\""::: APIs was that they:</span></span>

* <span data-ttu-id="cfcc2-115">Może ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-115">Could change without notice.</span></span>
* <span data-ttu-id="cfcc2-116">Nie podlegają zasadom platformy .NET, aby zapobiec wprowadzeniu zmian.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-116">Weren't subject to .NET policies to prevent breaking changes.</span></span>

<span data-ttu-id="cfcc2-117">Pozostawienie interfejsów API `public` (nawet w `*.Internal` przestrzeniach nazw) zostało mylące dla klientów.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-117">Leaving the APIs `public` (even in the `*.Internal` namespaces) was confusing to customers.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cfcc2-118">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="cfcc2-118">Recommended action</span></span>

<span data-ttu-id="cfcc2-119">Zatrzymaj korzystanie z tych :::no-loc text="\"pubternal\""::: interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-119">Stop using these :::no-loc text="\"pubternal\""::: APIs.</span></span> <span data-ttu-id="cfcc2-120">Jeśli masz pytania dotyczące alternatywnych interfejsów API, Otwórz problem w repozytorium [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) .</span><span class="sxs-lookup"><span data-stu-id="cfcc2-120">If you have questions about alternate APIs, open an issue in the [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) repository.</span></span>

<span data-ttu-id="cfcc2-121">Rozważmy na przykład następujący kod buforowania żądania HTTP w projekcie ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-121">For example, consider the following HTTP request buffering code in an ASP.NET Core 2.2 project.</span></span> <span data-ttu-id="cfcc2-122">`EnableRewind`Metoda rozszerzenia istnieje w `Microsoft.AspNetCore.Http.Internal` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-122">The `EnableRewind` extension method exists in the `Microsoft.AspNetCore.Http.Internal` namespace.</span></span>

```csharp
HttpContext.Request.EnableRewind();
```

<span data-ttu-id="cfcc2-123">W projekcie ASP.NET Core 3,0 Zastąp wywołanie wywołaniu `EnableRewind` `EnableBuffering` metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-123">In an ASP.NET Core 3.0 project, replace the `EnableRewind` call with a call to the `EnableBuffering` extension method.</span></span> <span data-ttu-id="cfcc2-124">Funkcja buforowania żądań działa tak, jak w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-124">The request buffering feature works as it did in the past.</span></span> <span data-ttu-id="cfcc2-125">`EnableBuffering`wywołuje `internal` interfejs API teraz.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-125">`EnableBuffering` calls the now `internal` API.</span></span>

```csharp
HttpContext.Request.EnableBuffering();
```

#### <a name="category"></a><span data-ttu-id="cfcc2-126">Kategoria</span><span class="sxs-lookup"><span data-stu-id="cfcc2-126">Category</span></span>

<span data-ttu-id="cfcc2-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cfcc2-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cfcc2-128">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="cfcc2-128">Affected APIs</span></span>

<span data-ttu-id="cfcc2-129">Wszystkie interfejsy API w `Microsoft.AspNetCore.*` `Microsoft.Extensions.*` przestrzeni nazw i, które mają `Internal` segment w nazwie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cfcc2-129">All APIs in the `Microsoft.AspNetCore.*` and `Microsoft.Extensions.*` namespaces that have an `Internal` segment in the namespace name.</span></span> <span data-ttu-id="cfcc2-130">Przykład:</span><span class="sxs-lookup"><span data-stu-id="cfcc2-130">For example:</span></span>

- `Microsoft.AspNetCore.Authentication.Internal`
- `Microsoft.AspNetCore.Builder.Internal`
- `Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `Microsoft.AspNetCore.DataProtection.Internal`
- `Microsoft.AspNetCore.Hosting.Internal`
- `Microsoft.AspNetCore.Http.Internal`
- `Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `Microsoft.AspNetCore.Mvc.Core.Internal`
- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `Microsoft.AspNetCore.Rewrite.Internal`
- `Microsoft.AspNetCore.Routing.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Internal`
- `N:Microsoft.AspNetCore.Builder.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Internal`
- `N:Microsoft.AspNetCore.Hosting.Internal`
- `N:Microsoft.AspNetCore.Http.Internal`
- `N:Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `N:Microsoft.AspNetCore.Mvc.Core.Internal`
- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `N:Microsoft.AspNetCore.Rewrite.Internal`
- `N:Microsoft.AspNetCore.Routing.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `N:Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

-->
