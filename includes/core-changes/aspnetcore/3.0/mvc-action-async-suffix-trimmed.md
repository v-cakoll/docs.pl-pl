---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901759"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC: sufiks Async został przycięty z nazw akcji kontrolera

W ramach adresowania [dotnet/aspnetcore # 4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC domyślnie przycina sufiks `Async` z nazw akcji. Począwszy od ASP.NET Core 3,0, ta zmiana ma wpływ na generowanie routingu i linków.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Rozważmy następujący kontroler ASP.NET Core MVC:

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

Akcja obsługuje routing za pośrednictwem `Product/ListAsync`. Generowanie linku wymaga określenia `Async` sufiksu. Przykład:

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>Nowe zachowanie

W ASP.NET Core 3,0 akcja jest w trakcie routingu za `Product/List`pośrednictwem. Kod generacji łącza powinien pominąć `Async` sufiks. Przykład:

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

Ta zmiana nie ma wpływu na nazwy określone `[ActionName]` przy użyciu atrybutu. Nowe zachowanie można wyłączyć, ustawiając wartość `MvcOptions.SuppressAsyncSuffixInActionNames` `false` w: `Startup.ConfigureServices`

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>Przyczyna zmiany

Przy użyciu konwencji asynchroniczne metody .NET są sufiksem `Async`. Jednak jeśli metoda definiuje akcję MVC, nie można użyć `Async` sufiksu.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli aplikacja zależy od akcji MVC z zachowaniem `Async` sufiksu nazwy, wybierz jedno z następujących środków zaradczych:

- Użyj atrybutu `[ActionName]` , aby zachować oryginalną nazwę.
- Wyłącz zmianę nazwy poprzez ustawienie na `MvcOptions.SuppressAsyncSuffixInActionNames` `false` wartość w: `Startup.ConfigureServices`

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
