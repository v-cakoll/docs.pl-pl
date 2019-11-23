---
title: Poświadczenia kanału — gRPC dla deweloperów WCF
description: Jak zaimplementować i używać poświadczeń kanału gRPC w ASP.NET Core 3,0.
ms.date: 09/02/2019
ms.openlocfilehash: b424db49337a2dc6e3d0245d36349e3f408cdf6c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967963"
---
# <a name="channel-credentials"></a><span data-ttu-id="0a8fc-103">Poświadczenia kanałów</span><span class="sxs-lookup"><span data-stu-id="0a8fc-103">Channel credentials</span></span>

<span data-ttu-id="0a8fc-104">Jak wskazuje nazwa, poświadczenia kanału są dołączane do bazowego kanału gRPC.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="0a8fc-105">Standardowa forma poświadczeń kanału używa uwierzytelniania certyfikatu klienta, gdy klient udostępnia certyfikat TLS, gdy nastąpi połączenie, które jest weryfikowane przez serwer przed zezwoleniem na wykonywanie jakichkolwiek wywołań.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-105">The standard form of channel credentials uses Client Certificate authentication, where the client provides a TLS certificate when it's making the connection, which is verified by the server before allowing any calls to be made.</span></span>

<span data-ttu-id="0a8fc-106">Poświadczenia kanału można łączyć z poświadczeniami wywołania, aby zapewnić kompleksowe zabezpieczenia usługi gRPC.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-106">Channel credentials can be combined with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="0a8fc-107">Poświadczenia kanału potwierdzają, że aplikacja kliencka może uzyskać dostęp do usługi, a poświadczenia wywołania zawierają informacje o osobie korzystającej z aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-107">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person using the client application.</span></span>

<span data-ttu-id="0a8fc-108">Uwierzytelnianie za pomocą certyfikatu klienta działa dla gRPC w taki sam sposób, w jaki działa ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-108">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="0a8fc-109">Ten proces konfiguracji zostanie podsumowany w tym miejscu, ale więcej informacji można znaleźć w artykule [Konfigurowanie uwierzytelniania certyfikatu w ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) .</span><span class="sxs-lookup"><span data-stu-id="0a8fc-109">The configuration process will be summarized here, but more information is available in the [Configure certificate authentication in ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) article.</span></span>

<span data-ttu-id="0a8fc-110">W celach programistycznych można użyć certyfikatu z podpisem własnym, ale w przypadku produkcji należy użyć odpowiedniego certyfikatu HTTPS podpisanego przez zaufany urząd.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-110">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="adding-certificate-authentication-to-the-server"></a><span data-ttu-id="0a8fc-111">Dodawanie uwierzytelniania certyfikatu do serwera</span><span class="sxs-lookup"><span data-stu-id="0a8fc-111">Adding certificate authentication to the server</span></span>

<span data-ttu-id="0a8fc-112">Należy skonfigurować uwierzytelnianie certyfikatu zarówno na poziomie hosta, na przykład na serwerze Kestrel, jak i w potoku ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-112">You need to configure certificate authentication both at the host level, for example on the Kestrel server, and in the ASP.NET Core pipeline.</span></span>

### <a name="configuring-certificate-validation-on-kestrel"></a><span data-ttu-id="0a8fc-113">Konfigurowanie weryfikacji certyfikatu na Kestrel</span><span class="sxs-lookup"><span data-stu-id="0a8fc-113">Configuring certificate validation on Kestrel</span></span>

<span data-ttu-id="0a8fc-114">Można skonfigurować Kestrel (serwer HTTP ASP.NET Core), aby wymagał certyfikatu klienta i opcjonalnie przeprowadzić weryfikację podanego certyfikatu przed zaakceptowaniem połączeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-114">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate before accepting incoming connections.</span></span> <span data-ttu-id="0a8fc-115">Ta konfiguracja jest wykonywana w metodzie `CreateWebHostBuilder` klasy `Program`, a nie w `Startup`.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-115">This configuration is done in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            var serverCert = ObtainServerCertificate();
            webBuilder.UseStartup<Startup>()
                .ConfigureKestrel(kestrelServerOptions => {
                    kestrelServerOptions.ConfigureHttpsDefaults(opt =>
                    {
                        opt.ClientCertificateMode = ClientCertificateMode.RequireCertificate;

                        // Verify that client certificate was issued by same CA as server certificate
                        opt.ClientCertificateValidation = (certificate, chain, errors) =>
                            certificate.Issuer == serverCert.Issuer;
                    });
                });
        });

```

<span data-ttu-id="0a8fc-116">Ustawienie `ClientCertificateMode.RequireCertificate` spowoduje natychmiastowe odrzucanie wszystkich żądań połączenia, które nie zawierają certyfikatu klienta, ale nie sprawdza poprawności certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-116">The `ClientCertificateMode.RequireCertificate` setting will cause Kestrel to immediately reject any connection request that doesn't provide a client certificate, but it won't validate the certificate.</span></span> <span data-ttu-id="0a8fc-117">Dodanie wywołania zwrotnego `ClientCertificateValidation` umożliwia Kestrel Weryfikowanie certyfikatu klienta (w tym przypadku, aby upewnić się, że został wystawiony przez ten sam *urząd certyfikacji* co certyfikat serwera) w momencie nawiązywania połączenia, przed przeprowadzeniem potoku ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-117">Adding the `ClientCertificateValidation` callback enables Kestrel to validate the client certificate (in this case, ensuring that it was issued by the same *Certificate Authority* as the server certificate) at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span>

### <a name="adding-aspnet-core-certificate-authentication"></a><span data-ttu-id="0a8fc-118">Dodawanie ASP.NET Core uwierzytelniania certyfikatów</span><span class="sxs-lookup"><span data-stu-id="0a8fc-118">Adding ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="0a8fc-119">Uwierzytelnianie przy użyciu certyfikatu jest dostarczane przez pakiet NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) .</span><span class="sxs-lookup"><span data-stu-id="0a8fc-119">Certificate authentication is provided by the [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package.</span></span>

<span data-ttu-id="0a8fc-120">Dodaj usługę uwierzytelniania certyfikatów w metodzie `ConfigureServices` i Dodaj uwierzytelnianie i autoryzację do potoku ASP.NET Core w metodzie `Configure`.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-120">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

```csharp
public class Startup
{
    private readonly bool _isDevelopment;

    public Startup(IWebHostEnvironment env)
    {
        _isDevelopment = env.IsDevelopment();
    }

    public void ConfigureServices(IServiceCollection services)
    {
        services.AddAuthentication(CertificateAuthenticationDefaults.AuthenticationScheme)
            .AddCertificate(options =>
            {
                if (_isDevelopment)
                {
                    // DO NOT DO THIS IN PRODUCTION!
                    options.RevocationMode = X509RevocationMode.NoCheck;
                }
            });
        services.AddAuthorization();
        services.AddGrpc();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        app.UseRouting();

        app.UseAuthentication();
        app.UseAuthorization();

        app.UseEndpoints(endpoints => { endpoints.MapGrpcService<GreeterService>(); });
    }
}
```

## <a name="providing-channel-credentials-in-the-client-application"></a><span data-ttu-id="0a8fc-121">Dostarczanie poświadczeń kanału w aplikacji klienckiej</span><span class="sxs-lookup"><span data-stu-id="0a8fc-121">Providing channel credentials in the client application</span></span>

<span data-ttu-id="0a8fc-122">W pakiecie `Grpc.Net.Client` certyfikaty są konfigurowane w wystąpieniu <xref:System.Net.Http.HttpClient>, który jest dostarczany `GrpcChannel` używanym do nawiązywania połączenia.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-122">With the `Grpc.Net.Client` package, certificates are configured on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        // Assume path to a client .pfx file and password are passed from command line
        // On Windows this would probably be a reference to the Certificate Store
        var cert = new X509Certificate2(args[0], args[1]);

        var handler = new HttpClientHandler();
        handler.ClientCertificates.Add(cert);
        var httpClient = new HttpClient(handler);

        var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
        {
            HttpClient = httpClient
        });

        var grpc = new Greeter.GreeterClient(channel);
        var response = await grpc.SayHelloAsync(new HelloRequest { Name = "Bob" });
        System.Console.WriteLine(response.Message);
    }
}
```

## <a name="combining-channelcredentials-and-callcredentials"></a><span data-ttu-id="0a8fc-123">Łączenie ChannelCredentials i CallCredentials</span><span class="sxs-lookup"><span data-stu-id="0a8fc-123">Combining ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="0a8fc-124">Serwer można skonfigurować tak, aby korzystał z uwierzytelniania certyfikatów i tokenów, stosując zmiany certyfikatu na serwerze Kestrel i używając oprogramowania pośredniczącego okaziciela JWT w ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-124">You can configure your server to use both certificate and token authentication by applying the certificate changes to the Kestrel server and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="0a8fc-125">Aby zapewnić zarówno ChannelCredentials, jak i CallCredentials na kliencie, użyj metody `ChannelCredentials.Create`, aby zastosować poświadczenia wywołania.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-125">To provide both ChannelCredentials and CallCredentials on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="0a8fc-126">Nadal należy zastosować uwierzytelnianie certyfikatu przy użyciu wystąpienia <xref:System.Net.Http.HttpClient>: w przypadku przekazania jakichkolwiek argumentów do konstruktora `SslCredentials` wewnętrzny kod klienta zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-126">Certificate authentication still needs to be applied using the <xref:System.Net.Http.HttpClient> instance: if you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="0a8fc-127">Parametr `SslCredentials` jest uwzględniany tylko w metodzie `Create` pakietu `Grpc.Net.Client`, aby zachować zgodność z pakietem `Grpc.Core`.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-127">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

```csharp
var handler = new HttpClientHandler();
handler.ClientCertificates.Add(cert);

var httpClient = new HttpClient(handler);

var callCredentials = CallCredentials.FromInterceptor(((context, metadata) =>
    {
        metadata.Add("Authorization", $"Bearer {_token}");
    }));

var channelCredentials = ChannelCredentials.Create(new SslCredentials(), callCredentials);

var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
{
    HttpClient = httpClient,
    Credentials = channelCredentials
});

var grpc = new Portfolios.PortfoliosClient(channel);
```

> [!TIP]
> <span data-ttu-id="0a8fc-128">Metody `ChannelCredentials.Create` można użyć dla klienta bez uwierzytelniania przy użyciu certyfikatu, ponieważ jest to przydatny sposób przekazywania poświadczeń tokenu przy każdym wywołaniu w kanale.</span><span class="sxs-lookup"><span data-stu-id="0a8fc-128">You can use the `ChannelCredentials.Create` method for a client without certificate authentication, as a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="0a8fc-129">W serwisie GitHub została [dodana wersja przykładowej aplikacji GRPC FullStockTicker z uwierzytelnianiem przy użyciu certyfikatu](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) .</span><span class="sxs-lookup"><span data-stu-id="0a8fc-129">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0a8fc-130">[Poprzedni](call-credentials.md)
>[Następny](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="0a8fc-130">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
