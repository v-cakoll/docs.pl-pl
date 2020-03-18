---
title: Poświadczenia kanału - gRPC dla programistów WCF
description: Jak zaimplementować i używać poświadczeń kanału gRPC w ASP.NET Core 3.0.
ms.date: 09/02/2019
ms.openlocfilehash: 9ebe0aecb517e4cc2fe280632c4ecb593da9871c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148208"
---
# <a name="channel-credentials"></a><span data-ttu-id="2d1ec-103">Poświadczenia kanałów</span><span class="sxs-lookup"><span data-stu-id="2d1ec-103">Channel credentials</span></span>

<span data-ttu-id="2d1ec-104">Jak sama nazwa wskazuje, poświadczenia kanału są dołączone do podstawowego kanału gRPC.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="2d1ec-105">Standardowa forma poświadczeń kanału używa uwierzytelniania certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="2d1ec-106">W tym procesie klient udostępnia certyfikat TLS podczas nawiązywania połączenia, a następnie serwer sprawdza to przed zezwoleniem na wszelkie wywołania do nawiązywania.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this before allowing any calls to be made.</span></span>

<span data-ttu-id="2d1ec-107">Można połączyć poświadczenia kanału z poświadczeniami wywołania, aby zapewnić kompleksowe zabezpieczenia usługi gRPC.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="2d1ec-108">Poświadczenia kanału udowodnić, że aplikacja kliencka może uzyskać dostęp do usługi, a poświadczenia wywołania zawierają informacje o osobie, która korzysta z aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="2d1ec-109">Uwierzytelnianie certyfikatów klienta działa dla gRPC w taki sam sposób, jak działa dla ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="2d1ec-110">Aby uzyskać więcej informacji, zobacz [Konfigurowanie uwierzytelniania certyfikatów w ASP.NET core](/aspnet/core/security/authentication/certauth).</span><span class="sxs-lookup"><span data-stu-id="2d1ec-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="2d1ec-111">Do celów deweloperskich można użyć certyfikatu z podpisem własnym, ale do produkcji należy użyć odpowiedniego certyfikatu HTTPS podpisanego przez zaufany urząd.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="2d1ec-112">Dodawanie uwierzytelniania certyfikatów do serwera</span><span class="sxs-lookup"><span data-stu-id="2d1ec-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="2d1ec-113">Konfigurowanie uwierzytelniania certyfikatów zarówno na poziomie hosta (na przykład na serwerze Kestrel), jak i w potoku ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="2d1ec-114">Konfigurowanie sprawdzania poprawności certyfikatów w pustułku</span><span class="sxs-lookup"><span data-stu-id="2d1ec-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="2d1ec-115">Kestrel (ASP.NET core http) można skonfigurować do wymagania certyfikatu klienta i opcjonalnie do przeprowadzenia weryfikacji dostarczonego certyfikatu przed zaakceptowaniem połączeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="2d1ec-116">Można to zrobić `CreateWebHostBuilder` w `Program` metodzie klasy, `Startup`a nie w .</span><span class="sxs-lookup"><span data-stu-id="2d1ec-116">You do this in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="2d1ec-117">To `ClientCertificateMode.RequireCertificate` ustawienie powoduje, że kestrel natychmiast odrzuca żądanie połączenia, które nie udostępnia certyfikatu klienta, ale to ustawienie samo w sobie nie sprawdza poprawność certyfikatu, który jest dostarczany.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="2d1ec-118">Dodaj `ClientCertificateValidation` wywołanie odgłosowe, aby umożliwić kestrel do sprawdzania poprawności certyfikatu klienta w punkcie nawiązywanie połączenia, przed ASP.NET Core potoku jest włączony.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="2d1ec-119">(W takim przypadku wywołanie wsteczne zapewnia, że został wystawiony przez ten sam *urząd certyfikacji* co certyfikat serwera).</span><span class="sxs-lookup"><span data-stu-id="2d1ec-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span>

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="2d1ec-120">Dodawanie uwierzytelniania certyfikatu ASP.NET core</span><span class="sxs-lookup"><span data-stu-id="2d1ec-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="2d1ec-121">Pakiet [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet zapewnia uwierzytelnianie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="2d1ec-122">Dodaj usługę uwierzytelniania certyfikatów w metodzie `ConfigureServices` i dodaj uwierzytelnianie `Configure` i autoryzację do potoku ASP.NET Core w metodzie.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="2d1ec-123">Podaj poświadczenia kanału w aplikacji klienckiej</span><span class="sxs-lookup"><span data-stu-id="2d1ec-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="2d1ec-124">Za `Grpc.Net.Client` pomocą pakietu można skonfigurować <xref:System.Net.Http.HttpClient> certyfikaty w wystąpieniu, które jest dostarczane do `GrpcChannel` używanego dla połączenia.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="2d1ec-125">Łączenie poświadczeń kanału i poświadczeń wywołań</span><span class="sxs-lookup"><span data-stu-id="2d1ec-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="2d1ec-126">Serwer można skonfigurować tak, aby używał uwierzytelniania certyfikatów i tokenów.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="2d1ec-127">Należy to zrobić, stosując zmiany certyfikatu do serwera Kestrel i używając pośredniczonego pośredniczynicy JWT w ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-127">Do this by applying the certificate changes to the Kestrel server, and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="2d1ec-128">Aby podać `ChannelCredentials` `CallCredentials` zarówno i na `ChannelCredentials.Create` kliencie, należy użyć metody, aby zastosować poświadczenia wywołania.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="2d1ec-129">Nadal należy zastosować uwierzytelnianie <xref:System.Net.Http.HttpClient> certyfikatów przy użyciu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="2d1ec-130">Jeśli przekażesz żadnych `SslCredentials` argumentów do konstruktora, wewnętrzny kod klienta zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="2d1ec-131">Parametr `SslCredentials` jest tylko zawarte `Grpc.Net.Client` w `Create` metodzie pakietu, `Grpc.Core` aby zachować zgodność z pakietem.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="2d1ec-132">Można użyć `ChannelCredentials.Create` metody dla klienta bez uwierzytelniania certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="2d1ec-133">Jest to przydatny sposób przekazywania poświadczeń tokenu z każdym wywołaniem nakanale.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="2d1ec-134">Wersja [przykładowej aplikacji gRPC firmy FullStockTicker z dodanym uwierzytelnianiem certyfikatów](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) znajduje się w usyłku GitHub.</span><span class="sxs-lookup"><span data-stu-id="2d1ec-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2d1ec-135">[Poprzedni](call-credentials.md)
>[następny](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="2d1ec-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
