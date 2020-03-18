---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901759"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC: Sufiks asynchroniczne przycięte z nazw akcji kontrolera

W ramach adresowania [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC `Async` domyślnie przycina sufiks z nazw akcji. Począwszy od ASP.NET Core 3.0, ta zmiana ma wpływ zarówno na routing, jak i generowanie łączy.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Należy wziąć pod uwagę następujące ASP.NET kontrolera Core MVC:

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

Akcja jest routingu `Product/ListAsync`przez . Generowanie łączy wymaga `Async` określenia sufiksu. Przykład:

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>Nowe zachowanie

W ASP.NET Core 3.0 akcja jest `Product/List`routingu przez . Kod generowania łączy powinien `Async` pominąć sufiks. Przykład:

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

Ta zmiana nie ma wpływu na `[ActionName]` nazwy określone przy użyciu atrybutu. Nowe zachowanie można wyłączyć, `MvcOptions.SuppressAsyncSuffixInActionNames` ustawiając `Startup.ConfigureServices`w: `false`

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zgodnie z konwencją asynchroniczne metody .NET `Async`są sufiksowane z . Jednak gdy metoda definiuje akcję MVC, niepożądane jest użycie `Async` sufiksu.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli aplikacja zależy od akcji MVC zachowując `Async` sufiks nazwy, wybierz jedną z następujących czynników ograniczających zagrożenie:

- Użyj `[ActionName]` atrybutu, aby zachować oryginalną nazwę.
- Całkowicie wyłącz zmianę nazwy, `MvcOptions.SuppressAsyncSuffixInActionNames` `false` ustawiając `Startup.ConfigureServices`w:

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
