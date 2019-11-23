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
# <a name="call-credentials"></a><span data-ttu-id="b9d22-103">Poświadczenia wywołań</span><span class="sxs-lookup"><span data-stu-id="b9d22-103">Call credentials</span></span>

<span data-ttu-id="b9d22-104">Poświadczenia wywołań są wszystkie na podstawie pewnego rodzaju tokenu przekazaną w metadanych przy użyciu każdego żądania.</span><span class="sxs-lookup"><span data-stu-id="b9d22-104">Call credentials are all based on some kind of token passed in metadata with each request.</span></span>

## <a name="ws-federation"></a><span data-ttu-id="b9d22-105">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="b9d22-105">WS-Federation</span></span>

<span data-ttu-id="b9d22-106">ASP.NET Core obsługuje protokół WS-Federation przy użyciu pakietu NuGet [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) .</span><span class="sxs-lookup"><span data-stu-id="b9d22-106">ASP.NET Core supports WS-Federation using the [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet package.</span></span> <span data-ttu-id="b9d22-107">Usługa WS-Federation to najbliższa dostępna alternatywa dla uwierzytelniania systemu Windows, która nie jest obsługiwana w przypadku protokołu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="b9d22-107">WS-Federation is the closest available alternative to Windows Authentication, which is not supported over HTTP/2.</span></span> <span data-ttu-id="b9d22-108">Użytkownicy są uwierzytelniani przy użyciu Active Directory Federation Services (AD FS), która zapewnia token, którego można użyć do uwierzytelniania za pomocą ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9d22-108">Users are authenticated using Active Directory Federation Services (ADFS), which provides a token that can be used to authenticate with ASP.NET Core.</span></span>

<span data-ttu-id="b9d22-109">Aby uzyskać więcej informacji na temat rozpoczynania pracy z tą metodą uwierzytelniania, zobacz artykuł [uwierzytelnianie użytkowników za pomocą usługi WS-Federation w ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) artykule.</span><span class="sxs-lookup"><span data-stu-id="b9d22-109">For more information on how to get started with this authentication method, see the [Authenticate users with WS-Federation in ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) article.</span></span>

## <a name="jwt-bearer-tokens"></a><span data-ttu-id="b9d22-110">Tokeny okaziciela JWT</span><span class="sxs-lookup"><span data-stu-id="b9d22-110">JWT Bearer tokens</span></span>

<span data-ttu-id="b9d22-111">Standard [token internetowy JSON](https://jwt.io) umożliwia kodowanie informacji o użytkowniku i ich oświadczeniach w zakodowanym ciągu oraz podpisanie tego tokenu w taki sposób, aby konsument mógł zweryfikować integralność tokenu przy użyciu kryptografii klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="b9d22-111">The [JSON Web Token](https://jwt.io) standard provides a way to encode information about a user and their claims in an encoded string, and to sign that token in such a way that the consumer can verify the integrity of the token using public key cryptography.</span></span> <span data-ttu-id="b9d22-112">Za pomocą różnych usług, takich jak usługi identityserver4, można uwierzytelniać użytkowników i generować tokeny połączenia OpenID Connect (OIDC) do użycia z interfejsami API gRPC i HTTP.</span><span class="sxs-lookup"><span data-stu-id="b9d22-112">You can use various services, such as IdentityServer4, to authenticate users and generate OpenID Connect (OIDC) tokens to use with gRPC and HTTP APIs.</span></span>

<span data-ttu-id="b9d22-113">ASP.NET Core 3,0 może obsługiwać tokeny sieci Web JSON przy użyciu pakietu okaziciela JWT.</span><span class="sxs-lookup"><span data-stu-id="b9d22-113">ASP.NET Core 3.0 can handle JSON Web Tokens using the JWT Bearer package.</span></span> <span data-ttu-id="b9d22-114">Konfiguracja jest dokładnie taka sama dla aplikacji gRPC jako aplikacja MVC ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9d22-114">The configuration is exactly the same for a gRPC application as an ASP.NET Core MVC application.</span></span>

<span data-ttu-id="b9d22-115">Ten rozdział koncentruje się na tokenach okaziciela JWT, ponieważ są one łatwiejsze do opracowania z użyciem usługi WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="b9d22-115">This chapter will focus on JWT Bearer tokens as they're easier to develop with than WS-Federation.</span></span>

## <a name="adding-authentication-and-authorization-to-the-server"></a><span data-ttu-id="b9d22-116">Dodawanie uwierzytelniania i autoryzacji do serwera</span><span class="sxs-lookup"><span data-stu-id="b9d22-116">Adding authentication and authorization to the server</span></span>

<span data-ttu-id="b9d22-117">Pakiet okaziciela JWT nie jest domyślnie zawarty w ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="b9d22-117">The JWT Bearer package isn't included in ASP.NET Core 3.0 by default.</span></span> <span data-ttu-id="b9d22-118">Zainstaluj pakiet NuGet [Microsoft. AspNetCore. Authentication. JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9d22-118">Install the [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet package in your app.</span></span>

<span data-ttu-id="b9d22-119">Dodaj usługę uwierzytelniania w klasie startowej i skonfiguruj procedurę obsługi okaziciela JWT.</span><span class="sxs-lookup"><span data-stu-id="b9d22-119">Add the Authentication service in the Startup class and configure the JWT Bearer handler.</span></span>

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

<span data-ttu-id="b9d22-120">Właściwość `IssuerSigningKey` wymaga implementacji `Microsoft.IdentityModels.Tokens.SecurityKey` z danymi kryptograficznymi niezbędnymi do zweryfikowania podpisanych tokenów.</span><span class="sxs-lookup"><span data-stu-id="b9d22-120">The `IssuerSigningKey` property requires an implementation of `Microsoft.IdentityModels.Tokens.SecurityKey` with the cryptographic data necessary to validate the signed tokens.</span></span> <span data-ttu-id="b9d22-121">Ten token powinien być bezpiecznie przechowywany na *serwerze tajnym* , takim jak Magazyn kluczy platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b9d22-121">This token should be stored securely in a *secrets server* like Azure KeyVault.</span></span>

<span data-ttu-id="b9d22-122">Następnie Dodaj usługę autoryzacji, która kontroluje dostęp do systemu.</span><span class="sxs-lookup"><span data-stu-id="b9d22-122">Next add the Authorization service, which controls access to the system.</span></span>

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
> <span data-ttu-id="b9d22-123">Uwierzytelnianie i autoryzacja to dwa oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="b9d22-123">Authentication and Authorization are two separate steps.</span></span> <span data-ttu-id="b9d22-124">Uwierzytelnianie służy do określenia tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b9d22-124">Authentication is used to determine the user's identity.</span></span> <span data-ttu-id="b9d22-125">Autoryzacja decyduje, czy użytkownik może uzyskać dostęp do różnych części systemu.</span><span class="sxs-lookup"><span data-stu-id="b9d22-125">Authorization decides whether that user is allowed to access various parts of the system.</span></span>

<span data-ttu-id="b9d22-126">Teraz Dodaj oprogramowanie pośredniczące uwierzytelniania i autoryzacji do potoku ASP.NET Core w metodzie `Configure`.</span><span class="sxs-lookup"><span data-stu-id="b9d22-126">Now add the Authentication and Authorization middleware to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

<span data-ttu-id="b9d22-127">Na koniec zastosuj atrybut `[Authorize]` do dowolnych usług lub metod, które mają być zabezpieczone, i Użyj właściwości `User` z bazowego `HttpContext`, aby zweryfikować uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="b9d22-127">Finally, apply the `[Authorize]` attribute to any services or methods to be secured, and use the `User` property from the underlying `HttpContext` to verify permissions.</span></span>

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

## <a name="providing-call-credentials-in-the-client-application"></a><span data-ttu-id="b9d22-128">Udostępnianie poświadczeń wywołań w aplikacji klienckiej</span><span class="sxs-lookup"><span data-stu-id="b9d22-128">Providing call credentials in the client application</span></span>

<span data-ttu-id="b9d22-129">Po uzyskaniu tokenu JWT z serwera tożsamości można go użyć do uwierzytelnienia wywołań gRPC z klienta przez dodanie go jako nagłówka metadanych w wywołaniu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b9d22-129">Once you've obtained a JWT token from an identity server, you can use it to authenticate gRPC calls from the client by adding it as a metadata header on the call, as follows:</span></span>

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

<span data-ttu-id="b9d22-130">Teraz usługa gRPC została zabezpieczona przy użyciu tokenów okaziciela JWT jako poświadczeń wywołania.</span><span class="sxs-lookup"><span data-stu-id="b9d22-130">Now, you've secured your gRPC service using JWT bearer tokens as call credentials.</span></span> <span data-ttu-id="b9d22-131">W serwisie GitHub znajduje się wersja [przykładowej portfolio, gRPC aplikację z uwierzytelnianiem i autoryzacją](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) .</span><span class="sxs-lookup"><span data-stu-id="b9d22-131">A version of the [Portfolios sample gRPC application with authentication and authorization added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b9d22-132">[Poprzedni](security.md)
>[Następny](channel-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="b9d22-132">[Previous](security.md)
[Next](channel-credentials.md)</span></span>
