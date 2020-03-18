---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394251"
---
### <a name="authentication-google-deprecated-and-replaced"></a>Uwierzytelnianie: Google+ przestarzałe i zastąpione

Google zaczyna [wyłączać](https://developers.google.com/+/api-shutdown) google+ Logowanie do aplikacji już 28 stycznia 2019.

#### <a name="change-description"></a>Zmień opis

ASP.NET 4.x i ASP.NET Core używają interfejsów API logowania Google+ do uwierzytelniania użytkowników kont Google w aplikacjach internetowych. Pakiety NuGet, których dotyczy problem, to [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) dla ASP.NET `Microsoft.Owin` Core i [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) z ASP.NET formularzami internetowymi i MVC.

Zastępcze interfejsy API Google używają innego źródła i formatu danych. Środki zaradcze i rozwiązania przedstawione poniżej uwzględniają zmiany strukturalne. Aplikacje powinny sprawdzać, czy same dane nadal spełniają ich wymagania. Na przykład nazwy, adresy e-mail, linki do profilu i zdjęcia profilowe mogą zawierać subtelnie inne wartości niż wcześniej.

#### <a name="version-introduced"></a>Wprowadzona wersja

Wszystkie wersje. Ta zmiana jest zewnętrzna dla ASP.NET Core.

#### <a name="recommended-action"></a>Zalecana akcja

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a>Owin z ASP.NET formularzami internetowymi i MVC

W `Microsoft.Owin` przypadku 3.1.0 i nowszych w [tym miejscu](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)przedstawiono tymczasowe środki zaradcze . Aplikacje powinny zakończyć testowanie z łagodzenia, aby sprawdzić zmiany w formacie danych. Istnieją plany wydania `Microsoft.Owin` 4.0.1 z poprawką. Aplikacje korzystające z dowolnej wcześniejszej wersji powinny zostać zaktualizowane do wersji 4.0.1.

##### <a name="aspnet-core-1x"></a>ASP.NET Core 1.x

Środki zaradcze w [Owin z ASP.NET web forms i MVC](#owin-with-aspnet-web-forms-and-mvc) mogą być dostosowane do ASP.NET Core 1.x. Poprawki pakietu NuGet nie są planowane, ponieważ 1.x osiągnął stan [końca życia.](https://dotnet.microsoft.com/platform/support-policy)

##### <a name="aspnet-core-2x"></a>ASP.NET Rdzeń 2.x

W `Microsoft.AspNetCore.Authentication.Google` przypadku wersji 2.x zastąp istniejące wywołanie `AddGoogle` `Startup.ConfigureServices` w następującym kodzie:

```csharp
.AddGoogle(o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.UserInformationEndpoint = "https://www.googleapis.com/oauth2/v2/userinfo";
    o.ClaimActions.Clear();
    o.ClaimActions.MapJsonKey(ClaimTypes.NameIdentifier, "id");
    o.ClaimActions.MapJsonKey(ClaimTypes.Name, "name");
    o.ClaimActions.MapJsonKey(ClaimTypes.GivenName, "given_name");
    o.ClaimActions.MapJsonKey(ClaimTypes.Surname, "family_name");
    o.ClaimActions.MapJsonKey("urn:google:profile", "link");
    o.ClaimActions.MapJsonKey(ClaimTypes.Email, "email");
});
```

Poprawki 2.1 i 2.2 z lutego zawierały poprzednią rekonfigurację jako nową wartość domyślną. Nie ma poprawki dla ASP.NET Core 2.0, ponieważ osiągnął [koniec życia](https://dotnet.microsoft.com/platform/support-policy).

##### <a name="aspnet-core-30"></a>ASP.NET Rdzeń 3.0

Środki zaradcze podane dla ASP.NET Core 2.x mogą być również używane do ASP.NET Core 3.0. W przyszłych wersjach zapoznawczych 3.0 `Microsoft.AspNetCore.Authentication.Google` pakiet może zostać usunięty. Użytkownicy będą kierowane `Microsoft.AspNetCore.Authentication.OpenIdConnect` do zamiast tego. Poniższy kod pokazuje, `AddGoogle` jak `AddOpenIdConnect` `Startup.ConfigureServices`zastąpić w . Ta wymiana może być używana z ASP.NET Core 2.0 i nowszym i może być dostosowana do ASP.NET Core 1.x w razie potrzeby.

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/sigin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
