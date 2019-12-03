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
# <a name="call-credentials"></a><span data-ttu-id="44b66-103">Poświadczenia wywołań</span><span class="sxs-lookup"><span data-stu-id="44b66-103">Call credentials</span></span>

<span data-ttu-id="44b66-104">Poświadczenia wywołań są wszystkie na podstawie tokenu przesłanego w metadanych przy każdym żądaniu.</span><span class="sxs-lookup"><span data-stu-id="44b66-104">Call credentials are all based on a token passed in metadata with each request.</span></span>

## <a name="ws-federation"></a><span data-ttu-id="44b66-105">Usługa WS-Federation</span><span class="sxs-lookup"><span data-stu-id="44b66-105">WS-Federation</span></span>

<span data-ttu-id="44b66-106">ASP.NET Core obsługuje protokół WS-Federation przy użyciu pakietu NuGet [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) .</span><span class="sxs-lookup"><span data-stu-id="44b66-106">ASP.NET Core supports WS-Federation using the [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet package.</span></span> <span data-ttu-id="44b66-107">Usługa WS-Federation jest najbliższą dostępną alternatywą dla uwierzytelniania systemu Windows, która nie jest obsługiwana w przypadku protokołu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="44b66-107">WS-Federation is the closest available alternative to Windows Authentication, which isn't supported over HTTP/2.</span></span> <span data-ttu-id="44b66-108">Użytkownicy są uwierzytelniani przy użyciu Active Directory Federation Services (AD FS), który zapewnia token, którego można użyć do uwierzytelniania za pomocą ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="44b66-108">Users are authenticated by using Active Directory Federation Services (AD FS), which provides a token that can be used to authenticate with ASP.NET Core.</span></span>

<span data-ttu-id="44b66-109">Aby uzyskać więcej informacji na temat rozpoczynania pracy z tą metodą uwierzytelniania, zobacz [uwierzytelnianie użytkowników przy użyciu usługi WS-Federation w ASP.NET Core](/aspnet/core/security/authentication/ws-federation).</span><span class="sxs-lookup"><span data-stu-id="44b66-109">For more information on how to get started with this authentication method, see [Authenticate users with WS-Federation in ASP.NET Core](/aspnet/core/security/authentication/ws-federation).</span></span>

## <a name="jwt-bearer-tokens"></a><span data-ttu-id="44b66-110">Tokeny okaziciela JWT</span><span class="sxs-lookup"><span data-stu-id="44b66-110">JWT Bearer tokens</span></span>

<span data-ttu-id="44b66-111">Standard [token sieci Web JSON](https://jwt.io) (JWT) zapewnia sposób kodowania informacji o użytkowniku i ich oświadczeniach w zakodowanym ciągu.</span><span class="sxs-lookup"><span data-stu-id="44b66-111">The [JSON Web Token](https://jwt.io) (JWT) standard provides a way to encode information about a user and their claims in an encoded string.</span></span> <span data-ttu-id="44b66-112">Umożliwia także podpisanie tego tokenu, dzięki czemu konsument może zweryfikować integralność tokenu przy użyciu kryptografii klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="44b66-112">It also provides a way to sign that token, so that the consumer can verify the integrity of the token by using public key cryptography.</span></span> <span data-ttu-id="44b66-113">Za pomocą różnych usług, takich jak usługi identityserver4, można uwierzytelniać użytkowników i generować tokeny połączenia OpenID Connect (OIDC) do użycia z interfejsami API gRPC i HTTP.</span><span class="sxs-lookup"><span data-stu-id="44b66-113">You can use various services, such as IdentityServer4, to authenticate users and generate OpenID Connect (OIDC) tokens to use with gRPC and HTTP APIs.</span></span>

<span data-ttu-id="44b66-114">ASP.NET Core 3,0 może obsłużyć JWTs przy użyciu pakietu okaziciela JWT.</span><span class="sxs-lookup"><span data-stu-id="44b66-114">ASP.NET Core 3.0 can handle JWTs by using the JWT Bearer package.</span></span> <span data-ttu-id="44b66-115">Konfiguracja jest dokładnie taka sama dla aplikacji gRPC, jak dla aplikacji ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="44b66-115">The configuration is exactly the same for a gRPC application as it is for an ASP.NET Core MVC application.</span></span> <span data-ttu-id="44b66-116">W tym miejscu będziemy skupić się na tokenach okaziciela JWT, ponieważ są one łatwiejsze do opracowania z użyciem usługi WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="44b66-116">Here, we'll focus on JWT Bearer tokens, because they're easier to develop with than WS-Federation.</span></span>

## <a name="add-authentication-and-authorization-to-the-server"></a><span data-ttu-id="44b66-117">Dodawanie uwierzytelniania i autoryzacji do serwera</span><span class="sxs-lookup"><span data-stu-id="44b66-117">Add authentication and authorization to the server</span></span>

<span data-ttu-id="44b66-118">Pakiet okaziciela JWT nie jest domyślnie zawarty w ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="44b66-118">The JWT Bearer package isn't included in ASP.NET Core 3.0 by default.</span></span> <span data-ttu-id="44b66-119">Zainstaluj pakiet NuGet [Microsoft. AspNetCore. Authentication. JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="44b66-119">Install the [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet package in your app.</span></span>

<span data-ttu-id="44b66-120">Dodaj usługę uwierzytelniania w klasie startowej i skonfiguruj procedurę obsługi okaziciela JWT:</span><span class="sxs-lookup"><span data-stu-id="44b66-120">Add the Authentication service in the Startup class, and configure the JWT Bearer handler:</span></span>

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

<span data-ttu-id="44b66-121">Właściwość `IssuerSigningKey` wymaga implementacji `Microsoft.IdentityModels.Tokens.SecurityKey` z danymi kryptograficznymi niezbędnymi do zweryfikowania podpisanych tokenów.</span><span class="sxs-lookup"><span data-stu-id="44b66-121">The `IssuerSigningKey` property requires an implementation of `Microsoft.IdentityModels.Tokens.SecurityKey` with the cryptographic data necessary to validate the signed tokens.</span></span> <span data-ttu-id="44b66-122">Bezpiecznie przechowuj ten token na *serwerze tajnym*, takim jak Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="44b66-122">Store this token securely in a *secrets server*, like Azure Key Vault.</span></span>

<span data-ttu-id="44b66-123">Następnie Dodaj usługę autoryzacji, która kontroluje dostęp do systemu:</span><span class="sxs-lookup"><span data-stu-id="44b66-123">Next, add the Authorization service, which controls access to the system:</span></span>

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
> <span data-ttu-id="44b66-124">Uwierzytelnianie i autoryzacja to dwa oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="44b66-124">Authentication and authorization are two separate steps.</span></span> <span data-ttu-id="44b66-125">Aby określić tożsamość użytkownika, należy użyć uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="44b66-125">You use authentication to determine the user's identity.</span></span> <span data-ttu-id="44b66-126">Autoryzacja jest używana do decydowania, czy użytkownik może uzyskać dostęp do różnych części systemu.</span><span class="sxs-lookup"><span data-stu-id="44b66-126">You use authorization to decide whether that user is allowed to access various parts of the system.</span></span>

<span data-ttu-id="44b66-127">Teraz Dodaj oprogramowanie pośredniczące uwierzytelniania i autoryzacji do potoku ASP.NET Core w metodzie `Configure`:</span><span class="sxs-lookup"><span data-stu-id="44b66-127">Now add the authentication and authorization middleware to the ASP.NET Core pipeline in the `Configure` method:</span></span>

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

<span data-ttu-id="44b66-128">Na koniec zastosuj atrybut `[Authorize]` do dowolnych usług lub metod, które mają być zabezpieczone, i Użyj właściwości `User` z bazowego `HttpContext`, aby zweryfikować uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="44b66-128">Finally, apply the `[Authorize]` attribute to any services or methods to be secured, and use the `User` property from the underlying `HttpContext` to verify permissions.</span></span>

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

## <a name="provide-call-credentials-in-the-client-application"></a><span data-ttu-id="44b66-129">Podaj poświadczenia wywołania w aplikacji klienckiej</span><span class="sxs-lookup"><span data-stu-id="44b66-129">Provide call credentials in the client application</span></span>

<span data-ttu-id="44b66-130">Po uzyskaniu tokenu JWT z serwera tożsamości można go użyć do uwierzytelnienia wywołań gRPC z klienta przez dodanie go jako nagłówka metadanych w wywołaniu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="44b66-130">After you've obtained a JWT token from an identity server, you can use it to authenticate gRPC calls from the client by adding it as a metadata header on the call, as follows:</span></span>

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

<span data-ttu-id="44b66-131">Teraz usługa gRPC została zabezpieczona przy użyciu tokenów okaziciela JWT jako poświadczeń wywołania.</span><span class="sxs-lookup"><span data-stu-id="44b66-131">Now you've secured your gRPC service by using JWT bearer tokens as call credentials.</span></span> <span data-ttu-id="44b66-132">W serwisie GitHub znajduje się wersja [przykładowej portfolio, gRPC aplikację z uwierzytelnianiem i autoryzacją](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) .</span><span class="sxs-lookup"><span data-stu-id="44b66-132">A version of the [portfolios sample gRPC application with authentication and authorization added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="44b66-133">[Poprzednie](security.md)
>[dalej](channel-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="44b66-133">[Previous](security.md)
[Next](channel-credentials.md)</span></span>
