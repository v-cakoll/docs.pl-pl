---
ms.openlocfilehash: dc9f37ae0cd6eef2c67e62421571290bba1c2233
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393983"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="1715f-101">MVC: sufiks Async został przycięty z nazw akcji kontrolera</span><span class="sxs-lookup"><span data-stu-id="1715f-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="1715f-102">W ramach adresowania [ASPNET/AspNetCore # 4849](https://github.com/aspnet/AspNetCore/issues/4849), ASP.NET Core MVC domyślnie przycina sufiks `Async` z nazw akcji.</span><span class="sxs-lookup"><span data-stu-id="1715f-102">As part of addressing [aspnet/AspNetCore#4849](https://github.com/aspnet/AspNetCore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="1715f-103">Począwszy od ASP.NET Core 3,0, ta zmiana ma wpływ na generowanie routingu i linków.</span><span class="sxs-lookup"><span data-stu-id="1715f-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1715f-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="1715f-104">Version introduced</span></span>

<span data-ttu-id="1715f-105">3.0</span><span class="sxs-lookup"><span data-stu-id="1715f-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1715f-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="1715f-106">Old behavior</span></span>

<span data-ttu-id="1715f-107">Rozważmy następujący kontroler ASP.NET Core MVC:</span><span class="sxs-lookup"><span data-stu-id="1715f-107">Consider the following ASP.NET Core MVC controller:</span></span>

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

<span data-ttu-id="1715f-108">Akcja polega na włączeniu routingu za pośrednictwem `Product/ListAsync`.</span><span class="sxs-lookup"><span data-stu-id="1715f-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="1715f-109">Generowanie linku wymaga określenia sufiksu `Async`.</span><span class="sxs-lookup"><span data-stu-id="1715f-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="1715f-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1715f-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="1715f-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="1715f-111">New behavior</span></span>

<span data-ttu-id="1715f-112">W ASP.NET Core 3,0 akcja polega na włączeniu routingu za pośrednictwem `Product/List`.</span><span class="sxs-lookup"><span data-stu-id="1715f-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="1715f-113">Kod generacji łącza powinien pominąć sufiks `Async`.</span><span class="sxs-lookup"><span data-stu-id="1715f-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="1715f-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1715f-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="1715f-115">Ta zmiana nie ma wpływu na nazwy określone przy użyciu atrybutu `[ActionName]`.</span><span class="sxs-lookup"><span data-stu-id="1715f-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="1715f-116">Nowe zachowanie można wyłączyć, ustawiając `MvcOptions.SuppressAsyncSuffixInActionNames` do `false` w `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="1715f-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false; 
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="1715f-117">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="1715f-117">Reason for change</span></span>

<span data-ttu-id="1715f-118">Zgodnie z Konwencją asynchroniczne metody .NET są sufiksem z `Async`.</span><span class="sxs-lookup"><span data-stu-id="1715f-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="1715f-119">Jednak jeśli metoda definiuje akcję MVC, nie można użyć sufiksu `Async`.</span><span class="sxs-lookup"><span data-stu-id="1715f-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1715f-120">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="1715f-120">Recommended action</span></span>

<span data-ttu-id="1715f-121">Jeśli aplikacja zależy od akcji MVC z zachowaniem sufiksu `Async`, wybierz jedno z następujących środków zaradczych:</span><span class="sxs-lookup"><span data-stu-id="1715f-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="1715f-122">Użyj atrybutu `[ActionName]`, aby zachować oryginalną nazwę.</span><span class="sxs-lookup"><span data-stu-id="1715f-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="1715f-123">Wyłącz zmianę nazwy poprzez ustawienie `MvcOptions.SuppressAsyncSuffixInActionNames` na `false` w `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="1715f-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false; 
});
```

#### <a name="category"></a><span data-ttu-id="1715f-124">Kategoria</span><span class="sxs-lookup"><span data-stu-id="1715f-124">Category</span></span>

<span data-ttu-id="1715f-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1715f-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1715f-126">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="1715f-126">Affected APIs</span></span>

<span data-ttu-id="1715f-127">Brak</span><span class="sxs-lookup"><span data-stu-id="1715f-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
