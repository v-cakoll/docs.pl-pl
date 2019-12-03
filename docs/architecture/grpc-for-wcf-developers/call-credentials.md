---
title: Wywołania poświadczeń — gRPC dla deweloperów WCF
description: Jak zaimplementować i używać poświadczeń wywołań gRPC w ASP.NET Core 3,0.
ms.date: 09/02/2019
ms.openlocfilehash: 01f21f58ed4235f45509c948c84653cd99d35618
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711535"
---
# <a name="call-credentials"></a>Poświadczenia wywołań

Poświadczenia wywołań są wszystkie na podstawie tokenu przesłanego w metadanych przy każdym żądaniu.

## <a name="ws-federation"></a>Usługa WS-Federation

ASP.NET Core obsługuje protokół WS-Federation przy użyciu pakietu NuGet [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) . Usługa WS-Federation jest najbliższą dostępną alternatywą dla uwierzytelniania systemu Windows, która nie jest obsługiwana w przypadku protokołu HTTP/2. Użytkownicy są uwierzytelniani przy użyciu Active Directory Federation Services (AD FS), który zapewnia token, którego można użyć do uwierzytelniania za pomocą ASP.NET Core.

Aby uzyskać więcej informacji na temat rozpoczynania pracy z tą metodą uwierzytelniania, zobacz [uwierzytelnianie użytkowników przy użyciu usługi WS-Federation w ASP.NET Core](/aspnet/core/security/authentication/ws-federation).

## <a name="jwt-bearer-tokens"></a>Tokeny okaziciela JWT

Standard [token sieci Web JSON](https://jwt.io) (JWT) zapewnia sposób kodowania informacji o użytkowniku i ich oświadczeniach w zakodowanym ciągu. Umożliwia także podpisanie tego tokenu, dzięki czemu konsument może zweryfikować integralność tokenu przy użyciu kryptografii klucza publicznego. Za pomocą różnych usług, takich jak usługi identityserver4, można uwierzytelniać użytkowników i generować tokeny połączenia OpenID Connect (OIDC) do użycia z interfejsami API gRPC i HTTP.

ASP.NET Core 3,0 może obsłużyć JWTs przy użyciu pakietu okaziciela JWT. Konfiguracja jest dokładnie taka sama dla aplikacji gRPC, jak dla aplikacji ASP.NET Core MVC. W tym miejscu będziemy skupić się na tokenach okaziciela JWT, ponieważ są one łatwiejsze do opracowania z użyciem usługi WS-Federation.

## <a name="add-authentication-and-authorization-to-the-server"></a>Dodawanie uwierzytelniania i autoryzacji do serwera

Pakiet okaziciela JWT nie jest domyślnie zawarty w ASP.NET Core 3,0. Zainstaluj pakiet NuGet [Microsoft. AspNetCore. Authentication. JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) w aplikacji.

Dodaj usługę uwierzytelniania w klasie startowej i skonfiguruj procedurę obsługi okaziciela JWT:

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

Właściwość `IssuerSigningKey` wymaga implementacji `Microsoft.IdentityModels.Tokens.SecurityKey` z danymi kryptograficznymi niezbędnymi do zweryfikowania podpisanych tokenów. Bezpiecznie przechowuj ten token na *serwerze tajnym*, takim jak Azure Key Vault.

Następnie Dodaj usługę autoryzacji, która kontroluje dostęp do systemu:

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
> Uwierzytelnianie i autoryzacja to dwa oddzielne kroki. Aby określić tożsamość użytkownika, należy użyć uwierzytelniania. Autoryzacja jest używana do decydowania, czy użytkownik może uzyskać dostęp do różnych części systemu.

Teraz Dodaj oprogramowanie pośredniczące uwierzytelniania i autoryzacji do potoku ASP.NET Core w metodzie `Configure`:

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

## <a name="provide-call-credentials-in-the-client-application"></a>Podaj poświadczenia wywołania w aplikacji klienckiej

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
>[Poprzednie](security.md)
>[dalej](channel-credentials.md)
