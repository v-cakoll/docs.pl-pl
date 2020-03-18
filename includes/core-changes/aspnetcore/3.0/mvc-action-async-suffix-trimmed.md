---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901759"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="2631b-101">MVC: Sufiks asynchroniczne przycięte z nazw akcji kontrolera</span><span class="sxs-lookup"><span data-stu-id="2631b-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="2631b-102">W ramach adresowania [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC `Async` domyślnie przycina sufiks z nazw akcji.</span><span class="sxs-lookup"><span data-stu-id="2631b-102">As part of addressing [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="2631b-103">Począwszy od ASP.NET Core 3.0, ta zmiana ma wpływ zarówno na routing, jak i generowanie łączy.</span><span class="sxs-lookup"><span data-stu-id="2631b-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2631b-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2631b-104">Version introduced</span></span>

<span data-ttu-id="2631b-105">3.0</span><span class="sxs-lookup"><span data-stu-id="2631b-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2631b-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="2631b-106">Old behavior</span></span>

<span data-ttu-id="2631b-107">Należy wziąć pod uwagę następujące ASP.NET kontrolera Core MVC:</span><span class="sxs-lookup"><span data-stu-id="2631b-107">Consider the following ASP.NET Core MVC controller:</span></span>

```csharp
public class ProductController : Controller
{
    public async IActionResult ListAsync()
    {
        var model = await DbContext.Products.ToListAsync();
        return View(model);
    }
}
```

<span data-ttu-id="2631b-108">Akcja jest routingu `Product/ListAsync`przez .</span><span class="sxs-lookup"><span data-stu-id="2631b-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="2631b-109">Generowanie łączy wymaga `Async` określenia sufiksu.</span><span class="sxs-lookup"><span data-stu-id="2631b-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="2631b-110">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2631b-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="2631b-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="2631b-111">New behavior</span></span>

<span data-ttu-id="2631b-112">W ASP.NET Core 3.0 akcja jest `Product/List`routingu przez .</span><span class="sxs-lookup"><span data-stu-id="2631b-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="2631b-113">Kod generowania łączy powinien `Async` pominąć sufiks.</span><span class="sxs-lookup"><span data-stu-id="2631b-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="2631b-114">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2631b-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="2631b-115">Ta zmiana nie ma wpływu na `[ActionName]` nazwy określone przy użyciu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2631b-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="2631b-116">Nowe zachowanie można wyłączyć, `MvcOptions.SuppressAsyncSuffixInActionNames` ustawiając `Startup.ConfigureServices`w: `false`</span><span class="sxs-lookup"><span data-stu-id="2631b-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="2631b-117">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="2631b-117">Reason for change</span></span>

<span data-ttu-id="2631b-118">Zgodnie z konwencją asynchroniczne metody .NET `Async`są sufiksowane z .</span><span class="sxs-lookup"><span data-stu-id="2631b-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="2631b-119">Jednak gdy metoda definiuje akcję MVC, niepożądane jest użycie `Async` sufiksu.</span><span class="sxs-lookup"><span data-stu-id="2631b-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2631b-120">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="2631b-120">Recommended action</span></span>

<span data-ttu-id="2631b-121">Jeśli aplikacja zależy od akcji MVC zachowując `Async` sufiks nazwy, wybierz jedną z następujących czynników ograniczających zagrożenie:</span><span class="sxs-lookup"><span data-stu-id="2631b-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="2631b-122">Użyj `[ActionName]` atrybutu, aby zachować oryginalną nazwę.</span><span class="sxs-lookup"><span data-stu-id="2631b-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="2631b-123">Całkowicie wyłącz zmianę nazwy, `MvcOptions.SuppressAsyncSuffixInActionNames` `false` ustawiając `Startup.ConfigureServices`w:</span><span class="sxs-lookup"><span data-stu-id="2631b-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a><span data-ttu-id="2631b-124">Kategoria</span><span class="sxs-lookup"><span data-stu-id="2631b-124">Category</span></span>

<span data-ttu-id="2631b-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2631b-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2631b-126">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="2631b-126">Affected APIs</span></span>

<span data-ttu-id="2631b-127">Brak</span><span class="sxs-lookup"><span data-stu-id="2631b-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
