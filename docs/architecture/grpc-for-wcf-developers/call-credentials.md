---
title: Wywołania poświadczeń — gRPC dla deweloperów WCF
description: Jak zaimplementować i używać poświadczeń wywołań gRPC w ASP.NET Core 3,0.
ms.date: 09/02/2019
ms.openlocfilehash: 2588fe3590a63ea6071b85ff29b3685efbfa25db
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967996"
---
# <a name="call-credentials"></a>Poświadczenia wywołań

Poświadczenia wywołań są wszystkie na podstawie pewnego rodzaju tokenu przekazaną w metadanych przy użyciu każdego żądania.

## <a name="ws-federation"></a>WS-Federation

ASP.NET Core obsługuje protokół WS-Federation przy użyciu pakietu NuGet [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) . Usługa WS-Federation to najbliższa dostępna alternatywa dla uwierzytelniania systemu Windows, która nie jest obsługiwana w przypadku protokołu HTTP/2. Użytkownicy są uwierzytelniani przy użyciu Active Directory Federation Services (AD FS), która zapewnia token, którego można użyć do uwierzytelniania za pomocą ASP.NET Core.

Aby uzyskać więcej informacji na temat rozpoczynania pracy z tą metodą uwierzytelniania, zobacz artykuł [uwierzytelnianie użytkowników za pomocą usługi WS-Federation w ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) artykule.

## <a name="jwt-bearer-tokens"></a>Tokeny okaziciela JWT

Standard [token internetowy JSON](https://jwt.io) umożliwia kodowanie informacji o użytkowniku i ich oświadczeniach w zakodowanym ciągu oraz podpisanie tego tokenu w taki sposób, aby konsument mógł zweryfikować integralność tokenu przy użyciu kryptografii klucza publicznego. Za pomocą różnych usług, takich jak usługi identityserver4, można uwierzytelniać użytkowników i generować tokeny połączenia OpenID Connect (OIDC) do użycia z interfejsami API gRPC i HTTP.

ASP.NET Core 3,0 może obsługiwać tokeny sieci Web JSON przy użyciu pakietu okaziciela JWT. Konfiguracja jest dokładnie taka sama dla aplikacji gRPC jako aplikacja MVC ASP.NET Core.

Ten rozdział koncentruje się na tokenach okaziciela JWT, ponieważ są one łatwiejsze do opracowania z użyciem usługi WS-Federation.

## <a name="adding-authentication-and-authorization-to-the-server"></a>Dodawanie uwierzytelniania i autoryzacji do serwera

Pakiet okaziciela JWT nie jest domyślnie zawarty w ASP.NET Core 3,0. Zainstaluj pakiet NuGet [Microsoft. AspNetCore. Authentication. JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) w aplikacji.

Dodaj usługę uwierzytelniania w klasie startowej i skonfiguruj procedurę obsługi okaziciela JWT.

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();

    var signingKey = ObtainSigningKeySomehow();

    services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
        .AddJwtBearer(options =>
        {
            options.TokenValidationParameters =
                new TokenValidationParameters
                {
                    ValidateAudience = false,
                    ValidateIssuer = false,
                    ValidateActor = false,
                    ValidateLifetime = true,
                    IssuerSigningKey = signingKey
                };
        });

}
```

Właściwość `IssuerSigningKey` wymaga implementacji `Microsoft.IdentityModels.Tokens.SecurityKey` z danymi kryptograficznymi niezbędnymi do zweryfikowania podpisanych tokenów. Ten token powinien być bezpiecznie przechowywany na *serwerze tajnym* , takim jak Magazyn kluczy platformy Azure.

Następnie Dodaj usługę autoryzacji, która kontroluje dostęp do systemu.

```csharp
    services.AddAuthorization(options =>
    {
        options.AddPolicy(JwtBearerDefaults.AuthenticationScheme, policy =>
        {
            policy.AddAuthenticationSchemes(JwtBearerDefaults.AuthenticationScheme);
            policy.RequireClaim(ClaimTypes.Name);
        });
    });

```

> [!TIP]
> Uwierzytelnianie i autoryzacja to dwa oddzielne kroki. Uwierzytelnianie służy do określenia tożsamości użytkownika. Autoryzacja decyduje, czy użytkownik może uzyskać dostęp do różnych części systemu.

Teraz Dodaj oprogramowanie pośredniczące uwierzytelniania i autoryzacji do potoku ASP.NET Core w metodzie `Configure`.

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    // Authenticate, then Authorize
    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

Na koniec zastosuj atrybut `[Authorize]` do dowolnych usług lub metod, które mają być zabezpieczone, i Użyj właściwości `User` z bazowego `HttpContext`, aby zweryfikować uprawnienia.

```csharp
[Authorize]
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!TryValidateUser(request.TraderId, context.GetHttpContext().User))
    {
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Denied."));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}
```

## <a name="providing-call-credentials-in-the-client-application"></a>Udostępnianie poświadczeń wywołań w aplikacji klienckiej

Po uzyskaniu tokenu JWT z serwera tożsamości można go użyć do uwierzytelnienia wywołań gRPC z klienta przez dodanie go jako nagłówka metadanych w wywołaniu w następujący sposób:

```csharp
public async Task ShowPortfolioAsync(int portfolioId)
{
    var headers = new Grpc.Core.Metadata
    {
        { "Authorization", $"Bearer {_userToken}" }
    };
    var request = new GetRequest
    {
        TraderId = _userId,
        PortfolioId = portfolioId
    };
    var response = await _portfoliosClient.GetAsync(request, headers);

    // Display portfolio
}
```

Teraz usługa gRPC została zabezpieczona przy użyciu tokenów okaziciela JWT jako poświadczeń wywołania. W serwisie GitHub znajduje się wersja [przykładowej portfolio, gRPC aplikację z uwierzytelnianiem i autoryzacją](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) .

>[!div class="step-by-step"]
>[Poprzedni](security.md)
>[Następny](channel-credentials.md)
