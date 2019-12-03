---
title: Poświadczenia kanału — gRPC dla deweloperów WCF
description: Jak zaimplementować i używać poświadczeń kanału gRPC w ASP.NET Core 3,0.
ms.date: 09/02/2019
ms.openlocfilehash: 133de2c732e72844f249f11bfe22b5980b828b89
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711494"
---
# <a name="channel-credentials"></a><span data-ttu-id="7d2cd-103">Poświadczenia kanałów</span><span class="sxs-lookup"><span data-stu-id="7d2cd-103">Channel credentials</span></span>

<span data-ttu-id="7d2cd-104">Jak wskazuje nazwa, poświadczenia kanału są dołączane do bazowego kanału gRPC.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="7d2cd-105">Standardowa forma poświadczeń kanału używa uwierzytelniania certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="7d2cd-106">W tym procesie klient udostępnia certyfikat TLS, gdy nastąpi połączenie, a następnie serwer weryfikuje to przed zezwoleniem na wykonywanie jakichkolwiek wywołań.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this before allowing any calls to be made.</span></span>

<span data-ttu-id="7d2cd-107">Poświadczenia kanału można połączyć z poświadczeniami wywołania, aby zapewnić kompleksowe zabezpieczenia usługi gRPC.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="7d2cd-108">Poświadczenia kanału potwierdzają, że aplikacja kliencka może uzyskać dostęp do usługi, a poświadczenia wywołania zawierają informacje o osobie korzystającej z aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="7d2cd-109">Uwierzytelnianie za pomocą certyfikatu klienta działa dla gRPC w taki sam sposób, w jaki działa ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="7d2cd-110">Aby uzyskać więcej informacji, zobacz [Konfigurowanie uwierzytelniania certyfikatów w ASP.NET Core](/aspnet/core/security/authentication/certauth).</span><span class="sxs-lookup"><span data-stu-id="7d2cd-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="7d2cd-111">W celach programistycznych można użyć certyfikatu z podpisem własnym, ale w przypadku produkcji należy użyć odpowiedniego certyfikatu HTTPS podpisanego przez zaufany urząd.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="7d2cd-112">Dodawanie uwierzytelniania certyfikatu do serwera</span><span class="sxs-lookup"><span data-stu-id="7d2cd-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="7d2cd-113">Skonfiguruj uwierzytelnianie certyfikatu zarówno na poziomie hosta (na przykład na serwerze Kestrel), jak i w potoku ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="7d2cd-114">Konfigurowanie weryfikacji certyfikatu na Kestrel</span><span class="sxs-lookup"><span data-stu-id="7d2cd-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="7d2cd-115">Można skonfigurować Kestrel (serwer HTTP ASP.NET Core), aby wymagał certyfikatu klienta i opcjonalnie przeprowadzić weryfikację podanego certyfikatu przed zaakceptowaniem połączeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="7d2cd-116">Należy to zrobić w metodzie `CreateWebHostBuilder` klasy `Program`, a nie w `Startup`.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-116">You do this in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="7d2cd-117">Ustawienie `ClientCertificateMode.RequireCertificate` powoduje natychmiastowe odrzucanie wszystkich żądań połączenia, które nie zawierają certyfikatu klienta, ale to ustawienie nie będzie sprawdzać podanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="7d2cd-118">Dodaj wywołanie zwrotne `ClientCertificateValidation`, aby umożliwić programowi Kestrel zweryfikowanie certyfikatu klienta w momencie nawiązywania połączenia, zanim potoku ASP.NET Core zostanie włączone.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="7d2cd-119">(W tym przypadku wywołanie zwrotne zapewnia, że zostało wystawione przez ten sam *urząd certyfikacji* co certyfikat serwera).</span><span class="sxs-lookup"><span data-stu-id="7d2cd-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span> 

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="7d2cd-120">Dodawanie ASP.NET Core uwierzytelniania certyfikatów</span><span class="sxs-lookup"><span data-stu-id="7d2cd-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="7d2cd-121">Pakiet NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) zapewnia uwierzytelnianie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="7d2cd-122">Dodaj usługę uwierzytelniania certyfikatów w metodzie `ConfigureServices` i Dodaj uwierzytelnianie i autoryzację do potoku ASP.NET Core w metodzie `Configure`.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="7d2cd-123">Podaj poświadczenia kanału w aplikacji klienckiej</span><span class="sxs-lookup"><span data-stu-id="7d2cd-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="7d2cd-124">Korzystając z pakietu `Grpc.Net.Client`, można skonfigurować certyfikaty w wystąpieniu <xref:System.Net.Http.HttpClient>, które jest udostępniane `GrpcChannel` używanym do nawiązywania połączenia.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="7d2cd-125">Łączenie ChannelCredentials i CallCredentials</span><span class="sxs-lookup"><span data-stu-id="7d2cd-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="7d2cd-126">Serwer można skonfigurować tak, aby korzystał z uwierzytelniania certyfikatu i tokenu.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="7d2cd-127">W tym celu należy zastosować zmiany certyfikatu na serwerze Kestrel i użyć oprogramowania pośredniczącego okaziciela JWT w ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-127">Do this by applying the certificate changes to the Kestrel server, and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="7d2cd-128">Aby zapewnić zarówno `ChannelCredentials` i `CallCredentials` na kliencie, użyj metody `ChannelCredentials.Create`, aby zastosować poświadczenia wywołania.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="7d2cd-129">Nadal musisz zastosować uwierzytelnianie certyfikatu przy użyciu wystąpienia <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="7d2cd-130">W przypadku przekazania dowolnych argumentów do konstruktora `SslCredentials` wewnętrzny kod klienta zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="7d2cd-131">Parametr `SslCredentials` jest uwzględniany tylko w metodzie `Create` pakietu `Grpc.Net.Client`, aby zachować zgodność z pakietem `Grpc.Core`.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="7d2cd-132">Metody `ChannelCredentials.Create` można użyć dla klienta bez uwierzytelniania przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="7d2cd-133">Jest to przydatny sposób przekazywania poświadczeń tokenu przy każdym wywołaniu w kanale.</span><span class="sxs-lookup"><span data-stu-id="7d2cd-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="7d2cd-134">W serwisie GitHub została [dodana wersja przykładowej aplikacji GRPC FullStockTicker z uwierzytelnianiem przy użyciu certyfikatu](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) .</span><span class="sxs-lookup"><span data-stu-id="7d2cd-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7d2cd-135">[Poprzednie](call-credentials.md)
>[dalej](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="7d2cd-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
