---
title: IdentityServer dla natywnych aplikacji w chmurze
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | IdentityServer
ms.date: 06/30/2019
ms.openlocfilehash: 536a4cbdbdaee47f3a5a0d9f93b2736270d9ea7a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394877"
---
# <a name="identityserver-for-cloud-native-applications"></a>IdentityServer dla aplikacji natywnych w chmurze

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

IdentityServer to serwer uwierzytelniania "open source", który implementuje standardy OpenID Connect Connect (OIDC) i OAuth 2,0 dla ASP.NET Core. Zaprojektowano w celu zapewnienia typowego sposobu uwierzytelniania żądań do wszystkich aplikacji, niezależnie od tego, czy są to punkty końcowe sieci Web, natywne, mobilne czy interfejsy API. IdentityServer może służyć do implementowania logowania jednokrotnego (SSO) dla wielu aplikacji i typów aplikacji. Może służyć do uwierzytelniania rzeczywistych użytkowników za pośrednictwem formularzy logowania i podobnych interfejsów użytkownika, a także uwierzytelniania opartego na usługach, który zazwyczaj obejmuje wystawianie, weryfikację i odnawianie tokenów bez żadnego interfejsu użytkownika. IdentityServer została zaprojektowana jako dostosowywalne rozwiązanie. Każde wystąpienie jest zwykle dostosowane do konkretnej organizacji i/lub zestawu potrzeb aplikacji.

## <a name="common-web-app-scenarios"></a>Typowe scenariusze aplikacji sieci Web

Zazwyczaj aplikacje muszą obsługiwać niektóre lub wszystkie z następujących scenariuszy:

- Użytkownicy ludzkich uzyskują dostęp do aplikacji sieci Web za pomocą przeglądarki.
- Użytkownicy ludzki uzyskują dostęp do interfejsów API sieci Web z aplikacji opartych na przeglądarce.
- Użytkownicy w przypadku klientów mobilnych/natywnych uzyskujących dostęp do interfejsów API sieci Web zaplecza.
- Inne aplikacje uzyskujące dostęp do interfejsów API sieci Web zaplecza (bez aktywnego użytkownika lub interfejsu użytkownika).
- Każda aplikacja może wymagać współdziałania z innymi interfejsami API sieci Web przy użyciu własnej tożsamości lub delegowania do tożsamości użytkownika.

![Typy aplikacji i scenariusze](./media/application-types.png)

**Rysunek 8-1**. Typy aplikacji i scenariusze.

W każdym z tych scenariuszy uwidocznione funkcje muszą być zabezpieczone przed nieautoryzowanym użyciem. Minimalnym wymaganiem jest zazwyczaj uwierzytelnianie użytkownika lub podmiotu zabezpieczeń wysyłającego żądanie dotyczące zasobu. Uwierzytelnianie może korzystać z jednego z kilku popularnych protokołów, takich jak SAML2p, WS-karmione lub OpenID Connect Connect. Komunikowanie się z interfejsami API zwykle używa protokołu OAuth2 oraz obsługi tokenów zabezpieczających. Oddzielenie tych krytycznych zagadnień związanych z bezpieczeństwem i ich implementacji z aplikacji zapewnia spójność i zwiększa bezpieczeństwo i łatwość utrzymania. Podniesieniu tych problemów do dedykowanego produktu, takiego jak IdentityServer, ułatwia wymagania dla każdej aplikacji, aby rozwiązać te problemy.

IdentityServer zapewnia oprogramowanie pośredniczące działające w ramach aplikacji ASP.NET Core i dodaje obsługę OpenID Connect Connect i OAuth2 (patrz [obsługiwane specyfikacje](http://docs.identityserver.io/en/latest/intro/specs.html)). Organizacje tworzą własne aplikacje ASP.NET Core przy użyciu oprogramowania pośredniczącego IdentityServer, aby działały jako usługa STS dla wszystkich protokołów zabezpieczeń opartych na tokenach. Oprogramowanie pośredniczące IdentityServer uwidacznia punkty końcowe do obsługi standardowych funkcji, w tym:

- Autoryzuj (uwierzytelniaj użytkownika końcowego)
- Token (żądanie tokenu programowo)
- Odnajdywanie (metadane dotyczące serwera)
- Informacje o użytkowniku (Uzyskiwanie informacji o użytkowniku z prawidłowym tokenem dostępu)
- Autoryzacja urządzenia (używana do uruchamiania autoryzacji przepływu urządzeń)
- Introspekcji (Walidacja tokenu)
- Odwołanie (odwołanie tokenu)
- Zakończ sesję (Wyzwalaj Logowanie jednokrotne we wszystkich aplikacjach)

## <a name="getting-started"></a>Wprowadzenie

Usługi identityserver4 to "open source" i bezpłatna do użycia. Możesz dodać go do aplikacji przy użyciu swoich pakietów NuGet. Pakiet główny to [usługi identityserver4](https://www.nuget.org/packages/IdentityServer4/) , który został pobrany ponad 4 000 000 razy. Pakiet podstawowy nie zawiera żadnego kodu interfejsu użytkownika i obsługuje tylko w konfiguracji pamięci. Aby używać jej z bazą danych, należy również użyć dostawcy danych, takiego jak [usługi identityserver4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) , który używa Entity Framework Core do przechowywania danych konfiguracyjnych i operacyjnych dla IdentityServer. W przypadku interfejsu użytkownika można skopiować pliki z [repozytorium szybkiego interfejsu użytkownika](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) do aplikacji ASP.NET Core MVC, aby dodać obsługę logowania i wylogować się przy użyciu oprogramowania pośredniczącego IdentityServer.

## <a name="configuration"></a>Konfigurowanie

Program IdentityServer obsługuje różne rodzaje protokołów i dostawców uwierzytelniania społecznościowego, które można skonfigurować w ramach każdej instalacji niestandardowej. Jest to zazwyczaj wykonywane w klasie aplikacji ASP.NET Core `Startup` w `ConfigureServices` metodzie. Konfiguracja obejmuje określenie obsługiwanych protokołów i ścieżek do serwerów i punktów końcowych, które będą używane. Na rysunku 8-2 przedstawiono przykładową konfigurację wykonywaną w projekcie interfejsu użytkownika szybkiego startu usługi identityserver4:

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();

        // some details omitted
        services.AddIdentityServer();

          services.AddAuthentication()
            .AddGoogle("Google", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;

                options.ClientId = "<insert here>";
                options.ClientSecret = "<insert here>";
            })
            .AddOpenIdConnect("demoidsrv", "IdentityServer", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;
                options.SignOutScheme = IdentityServerConstants.SignoutScheme;

                options.Authority = "https://demo.identityserver.io/";
                options.ClientId = "implicit";
                options.ResponseType = "id_token";
                options.SaveTokens = true;
                options.CallbackPath = new PathString("/signin-idsrv");
                options.SignedOutCallbackPath = new PathString("/signout-callback-idsrv");
                options.RemoteSignOutPath = new PathString("/signout-idsrv");

                options.TokenValidationParameters = new TokenValidationParameters
                {
                    NameClaimType = "name",
                    RoleClaimType = "role"
                };
            });
    }
}
```

**Rysunek 8-2**. Konfigurowanie IdentityServer.

IdentityServer również udostępnia publiczną witrynę demonstracyjną, która może służyć do testowania różnych protokołów i konfiguracji. Znajduje się on w [https://demo.identityserver.io/](https://demo.identityserver.io/) systemie i zawiera informacje dotyczące sposobu konfigurowania jego zachowania na podstawie `client_id` dostarczonego do niego działania.

## <a name="javascript-clients"></a>Klienci języka JavaScript

Wiele aplikacji natywnych w chmurze korzysta z interfejsów API po stronie serwera i rozbudowanych aplikacji jednostronicowych klienta (aplikacji jednostronicowych) na frontonie. IdentityServer dostarcza [klient JavaScript](http://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) ( `oidc-client.js` ) za pośrednictwem npm, który można dodać do aplikacji jednostronicowych, aby umożliwić im używanie IdentityServer do logowania, wylogowywania i uwierzytelniania opartych na tokenach interfejsów API sieci Web.

## <a name="references"></a>Odwołania

- [Dokumentacja IdentityServer](http://docs.identityserver.io/en/latest/)
- [Typy aplikacji](https://docs.microsoft.com/azure/active-directory/develop/app-types)
- [Klient JavaScript OIDC](http://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html)

>[!div class="step-by-step"]
>[Poprzedni](azure-active-directory.md) 
> [Dalej](security.md)
