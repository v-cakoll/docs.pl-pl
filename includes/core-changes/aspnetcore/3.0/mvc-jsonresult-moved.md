---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901743"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC: JsonResult przeniesiony do Microsoft. AspNetCore. MVC. Core

`JsonResult` przeniesiono do zestawu `Microsoft.AspNetCore.Mvc.Core`. Ten typ jest używany do zdefiniowania w pliku [Microsoft. AspNetCore. MVC. formatującegos. JSON](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json). Atrybut na poziomie zestawu [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) został dodany do `Microsoft.AspNetCore.Mvc.Formatters.Json`, aby rozwiązać ten problem w przypadku większości użytkowników. Aplikacje korzystające z bibliotek innych firm mogą napotkać problemy.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 6

#### <a name="old-behavior"></a>Stare zachowanie

Aplikacja używająca pomyślnie utworzonych bibliotek opartych na 2,2.

#### <a name="new-behavior"></a>Nowe zachowanie

Kompilacja nie powiedzie się w aplikacji korzystającej z biblioteki opartej na 2,2. Wystąpił błąd zawierający odmianę następującego tekstu:

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

Przykład takiego problemu można znaleźć w temacie [dotnet/aspnetcore # 7220](https://github.com/dotnet/aspnetcore/issues/7220).

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zmiany na poziomie platformy do kompozycji ASP.NET Core zgodnie z opisem w polu [ASPNET/anonse # 325](https://github.com/aspnet/Announcements/issues/325).

#### <a name="recommended-action"></a>Zalecane działanie

Biblioteki skompilowane pod kątem 2,2 wersji `Microsoft.AspNetCore.Mvc.Formatters.Json` mogą wymagać ponownego skompilowania w celu rozwiązania problemu dla wszystkich klientów. Jeśli to dotyczy, skontaktuj się z autorem biblioteki. Poproś o ponowną kompilację biblioteki do celu ASP.NET Core 3,0.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
