---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901743"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC: JsonResult przeniesiony do microsoft.aspNetCore.Mvc.Core

`JsonResult`przesunął `Microsoft.AspNetCore.Mvc.Core` się do zespołu. Ten typ był definiowany w [pliku Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json). Na poziomie zestawu [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) atrybut `Microsoft.AspNetCore.Mvc.Formatters.Json` został dodany do rozwiązania tego problemu dla większości użytkowników. Aplikacje, które korzystają z bibliotek innych firm mogą napotkać problemy.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 6

#### <a name="old-behavior"></a>Stare zachowanie

Aplikacja korzystająca z biblioteki opartej na 2.2 tworzy pomyślnie.

#### <a name="new-behavior"></a>Nowe zachowanie

Kompilacja aplikacji korzystająca z biblioteki opartej na 2.2 kończy się niepowodzeniem. Występuje błąd zawierający odmianę następującego tekstu:

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

Przykład takiego problemu można znaleźć w części [dotnet/aspnetcore#7220](https://github.com/dotnet/aspnetcore/issues/7220).

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zmiany na poziomie platformy w składzie ASP.NET Core zgodnie z opisem w [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).

#### <a name="recommended-action"></a>Zalecana akcja

Biblioteki skompilowane w wersji 2.2 `Microsoft.AspNetCore.Mvc.Formatters.Json` może być konieczne ponowneskompilowanie w celu rozwiązania problemu dla wszystkich konsumentów. Jeśli problem dotyczy, skontaktuj się z autorem biblioteki. Zażądaj ponownej kompilacji biblioteki, aby ASP.NET Core 3.0.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
