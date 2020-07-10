---
ms.openlocfilehash: ca369c4e3f78648c6e8e0bcb5d54711d3009a769
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174269"
---
### <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a><span data-ttu-id="29641-101">Blazor: nieznaczące odstępy są obcinane ze składników w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="29641-101">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>

<span data-ttu-id="29641-102">Począwszy od ASP.NET Core 5,0 w wersji zapoznawczej 7 kompilator Razor pomija nieznaczące odstępy w składnikach Blazor (pliki*Razor* ) w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="29641-102">Starting with ASP.NET Core 5.0 Preview 7, the Razor compiler omits insignificant whitespace in Blazor components (*.razor* files) at compile time.</span></span> <span data-ttu-id="29641-103">Aby zapoznać się z omówieniem, zobacz temat Issue [dotnet/aspnetcore # 23568](https://github.com/dotnet/aspnetcore/issues/23568).</span><span class="sxs-lookup"><span data-stu-id="29641-103">For discussion, see issue [dotnet/aspnetcore#23568](https://github.com/dotnet/aspnetcore/issues/23568).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="29641-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="29641-104">Version introduced</span></span>

<span data-ttu-id="29641-105">5,0 wersja zapoznawcza 7</span><span class="sxs-lookup"><span data-stu-id="29641-105">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="29641-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="29641-106">Old behavior</span></span>

<span data-ttu-id="29641-107">W 3. x wersjach Blazor Server i Blazor webassembly biały znak jest uznawany za kod źródłowy składnika.</span><span class="sxs-lookup"><span data-stu-id="29641-107">In 3.x versions of Blazor Server and Blazor WebAssembly, whitespace is honored in a component's source code.</span></span> <span data-ttu-id="29641-108">Odstępy — tylko węzły tekstowe są renderowane w Document Object Model przeglądarki (DOM), nawet jeśli nie ma efektów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="29641-108">Whitespace-only text nodes render in the browser's Document Object Model (DOM) even when there's no visual effect.</span></span>

<span data-ttu-id="29641-109">Rozważmy następujący kod składnika Blazor:</span><span class="sxs-lookup"><span data-stu-id="29641-109">Consider the following Blazor component code:</span></span>

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

<span data-ttu-id="29641-110">W poprzednim przykładzie renderowane są dwa węzły odstępu:</span><span class="sxs-lookup"><span data-stu-id="29641-110">The preceding example renders two whitespace nodes:</span></span>

* <span data-ttu-id="29641-111">Poza `@foreach` blokiem kodu.</span><span class="sxs-lookup"><span data-stu-id="29641-111">Outside of the `@foreach` code block.</span></span>
* <span data-ttu-id="29641-112">Wokół `<li>` elementu.</span><span class="sxs-lookup"><span data-stu-id="29641-112">Around the `<li>` element.</span></span>
* <span data-ttu-id="29641-113">Wokół `@item.Text` danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="29641-113">Around the `@item.Text` output.</span></span>

<span data-ttu-id="29641-114">Lista zawierająca 100 elementów skutkuje w węzłach o 402.</span><span class="sxs-lookup"><span data-stu-id="29641-114">A list containing 100 items results in 402 whitespace nodes.</span></span> <span data-ttu-id="29641-115">Jest to ponad połowę wszystkich wyrenderowanych węzłów, nawet jeśli żaden z węzłów odstępu nie ma wizualnie wpływu na renderowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="29641-115">That's over half of all nodes rendered, even though none of the whitespace nodes visually affect the rendered output.</span></span>

<span data-ttu-id="29641-116">Podczas renderowania statycznego kodu HTML dla składników, odstęp wewnątrz tagu nie został zachowany.</span><span class="sxs-lookup"><span data-stu-id="29641-116">When rendering static HTML for components, whitespace inside a tag wasn't preserved.</span></span> <span data-ttu-id="29641-117">Na przykład Wyświetl źródło następującego składnika:</span><span class="sxs-lookup"><span data-stu-id="29641-117">For example, view the source of the following component:</span></span>

```razor
<foo        bar="baz"     />
```

<span data-ttu-id="29641-118">Biały znak nie jest zachowywany.</span><span class="sxs-lookup"><span data-stu-id="29641-118">Whitespace isn't preserved.</span></span> <span data-ttu-id="29641-119">Wstępnie renderowane dane wyjściowe to:</span><span class="sxs-lookup"><span data-stu-id="29641-119">The pre-rendered output is:</span></span>

```razor
<foo bar="baz" />
```

#### <a name="new-behavior"></a><span data-ttu-id="29641-120">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="29641-120">New behavior</span></span>

<span data-ttu-id="29641-121">O ile `@preservewhitespace` dyrektywa nie jest używana z wartością `true` , węzły odstępu są usuwane, jeśli:</span><span class="sxs-lookup"><span data-stu-id="29641-121">Unless the `@preservewhitespace` directive is used with value `true`, whitespace nodes are removed if they:</span></span>

* <span data-ttu-id="29641-122">Są wiodące lub końcowe w obrębie elementu.</span><span class="sxs-lookup"><span data-stu-id="29641-122">Are leading or trailing within an element.</span></span>
* <span data-ttu-id="29641-123">Są wiodące lub końcowe w obrębie `RenderFragment` parametru.</span><span class="sxs-lookup"><span data-stu-id="29641-123">Are leading or trailing within a `RenderFragment` parameter.</span></span> <span data-ttu-id="29641-124">Na przykład zawartość podrzędna jest przesyłana do innego składnika.</span><span class="sxs-lookup"><span data-stu-id="29641-124">For example, child content being passed to another component.</span></span>
* <span data-ttu-id="29641-125">Należy użyć bloku kodu w języku C#, takiego jak `@if` i `@foreach` .</span><span class="sxs-lookup"><span data-stu-id="29641-125">Precede or follow a C# code block such as `@if` and `@foreach`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="29641-126">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="29641-126">Reason for change</span></span>

<span data-ttu-id="29641-127">Celem Blazor w ASP.NET Core 5,0 jest poprawa wydajności renderowania i różnicowania.</span><span class="sxs-lookup"><span data-stu-id="29641-127">A goal for Blazor in ASP.NET Core 5.0 is to improve the performance of rendering and diffing.</span></span> <span data-ttu-id="29641-128">Nieznaczące węzły drzewa odstępów zużywają do 40% czasu renderowania w testach porównawczych.</span><span class="sxs-lookup"><span data-stu-id="29641-128">Insignificant whitespace tree nodes consumed up to 40 percent of the rendering time in benchmarks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="29641-129">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="29641-129">Recommended action</span></span>

<span data-ttu-id="29641-130">W większości przypadków nie ma to żadnego oddziaływania na układ wizualizacji renderowanego składnika.</span><span class="sxs-lookup"><span data-stu-id="29641-130">In most cases, the visual layout of the rendered component is unaffected.</span></span> <span data-ttu-id="29641-131">Jednak usunięcie odstępu może mieć wpływ na renderowane dane wyjściowe w przypadku używania reguły CSS, takiej jak `white-space: pre` .</span><span class="sxs-lookup"><span data-stu-id="29641-131">However, the whitespace removal might affect the rendered output when using a CSS rule like `white-space: pre`.</span></span> <span data-ttu-id="29641-132">Aby wyłączyć tę optymalizację wydajności i zachować odstęp, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="29641-132">To disable this performance optimization and preserve the whitespace, take one of the following actions:</span></span>

* <span data-ttu-id="29641-133">Dodaj `@preservewhitespace true` dyrektywę w górnej części pliku *Razor* , aby zastosować preferencję do określonego składnika.</span><span class="sxs-lookup"><span data-stu-id="29641-133">Add the `@preservewhitespace true` directive at the top of the *.razor* file to apply the preference to a specific component.</span></span>
* <span data-ttu-id="29641-134">Dodaj `@preservewhitespace true` dyrektywę wewnątrz pliku *_Imports. Razor* , aby zastosować preferencję do całego podkatalogu lub całego projektu.</span><span class="sxs-lookup"><span data-stu-id="29641-134">Add the `@preservewhitespace true` directive inside an *_Imports.razor* file to apply the preference to an entire subdirectory or the entire project.</span></span>

<span data-ttu-id="29641-135">W większości przypadków żadna akcja nie jest wymagana, ponieważ aplikacje zwykle nadal zachowują się normalnie (ale szybciej).</span><span class="sxs-lookup"><span data-stu-id="29641-135">In most cases, no action is required, as applications will typically continue to behave normally (but faster).</span></span> <span data-ttu-id="29641-136">W przypadku wyłączania odstępów powoduje wszelkie problemy dotyczące określonego składnika, użyj `@preservewhitespace true` w tym składniku, aby wyłączyć tę optymalizację.</span><span class="sxs-lookup"><span data-stu-id="29641-136">If the whitespace stripping causes any problems for a particular component, use `@preservewhitespace true` in that component to disable this optimization.</span></span>

#### <a name="category"></a><span data-ttu-id="29641-137">Kategoria</span><span class="sxs-lookup"><span data-stu-id="29641-137">Category</span></span>

<span data-ttu-id="29641-138">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="29641-138">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="29641-139">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="29641-139">Affected APIs</span></span>

<span data-ttu-id="29641-140">Brak</span><span class="sxs-lookup"><span data-stu-id="29641-140">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
