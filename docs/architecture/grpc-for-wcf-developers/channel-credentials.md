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
# <a name="channel-credentials"></a>Poświadczenia kanałów

Jak wskazuje nazwa, poświadczenia kanału są dołączane do bazowego kanału gRPC. Standardowa forma poświadczeń kanału używa uwierzytelniania certyfikatu klienta. W tym procesie klient udostępnia certyfikat TLS, gdy nastąpi połączenie, a następnie serwer weryfikuje to przed zezwoleniem na wykonywanie jakichkolwiek wywołań.

Poświadczenia kanału można połączyć z poświadczeniami wywołania, aby zapewnić kompleksowe zabezpieczenia usługi gRPC. Poświadczenia kanału potwierdzają, że aplikacja kliencka może uzyskać dostęp do usługi, a poświadczenia wywołania zawierają informacje o osobie korzystającej z aplikacji klienckiej.

Uwierzytelnianie za pomocą certyfikatu klienta działa dla gRPC w taki sam sposób, w jaki działa ASP.NET Core. Aby uzyskać więcej informacji, zobacz [Konfigurowanie uwierzytelniania certyfikatów w ASP.NET Core](/aspnet/core/security/authentication/certauth).

W celach programistycznych można użyć certyfikatu z podpisem własnym, ale w przypadku produkcji należy użyć odpowiedniego certyfikatu HTTPS podpisanego przez zaufany urząd.

## <a name="add-certificate-authentication-to-the-server"></a>Dodawanie uwierzytelniania certyfikatu do serwera

Skonfiguruj uwierzytelnianie certyfikatu zarówno na poziomie hosta (na przykład na serwerze Kestrel), jak i w potoku ASP.NET Core.

### <a name="configure-certificate-validation-on-kestrel"></a>Konfigurowanie weryfikacji certyfikatu na Kestrel

Można skonfigurować Kestrel (serwer HTTP ASP.NET Core), aby wymagał certyfikatu klienta i opcjonalnie przeprowadzić weryfikację podanego certyfikatu przed zaakceptowaniem połączeń przychodzących. Należy to zrobić w metodzie `CreateWebHostBuilder` klasy `Program`, a nie w `Startup`.

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

Ustawienie `ClientCertificateMode.RequireCertificate` powoduje natychmiastowe odrzucanie wszystkich żądań połączenia, które nie zawierają certyfikatu klienta, ale to ustawienie nie będzie sprawdzać podanego certyfikatu. Dodaj wywołanie zwrotne `ClientCertificateValidation`, aby umożliwić programowi Kestrel zweryfikowanie certyfikatu klienta w momencie nawiązywania połączenia, zanim potoku ASP.NET Core zostanie włączone. (W tym przypadku wywołanie zwrotne zapewnia, że zostało wystawione przez ten sam *urząd certyfikacji* co certyfikat serwera). 

### <a name="add-aspnet-core-certificate-authentication"></a>Dodawanie ASP.NET Core uwierzytelniania certyfikatów

Pakiet NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) zapewnia uwierzytelnianie certyfikatu.

Dodaj usługę uwierzytelniania certyfikatów w metodzie `ConfigureServices` i Dodaj uwierzytelnianie i autoryzację do potoku ASP.NET Core w metodzie `Configure`.

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

## <a name="provide-channel-credentials-in-the-client-application"></a>Podaj poświadczenia kanału w aplikacji klienckiej

Korzystając z pakietu `Grpc.Net.Client`, można skonfigurować certyfikaty w wystąpieniu <xref:System.Net.Http.HttpClient>, które jest udostępniane `GrpcChannel` używanym do nawiązywania połączenia.

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

## <a name="combine-channelcredentials-and-callcredentials"></a>Łączenie ChannelCredentials i CallCredentials

Serwer można skonfigurować tak, aby korzystał z uwierzytelniania certyfikatu i tokenu. W tym celu należy zastosować zmiany certyfikatu na serwerze Kestrel i użyć oprogramowania pośredniczącego okaziciela JWT w ASP.NET Core.

Aby zapewnić zarówno `ChannelCredentials` i `CallCredentials` na kliencie, użyj metody `ChannelCredentials.Create`, aby zastosować poświadczenia wywołania. Nadal musisz zastosować uwierzytelnianie certyfikatu przy użyciu wystąpienia <xref:System.Net.Http.HttpClient>. W przypadku przekazania dowolnych argumentów do konstruktora `SslCredentials` wewnętrzny kod klienta zgłasza wyjątek. Parametr `SslCredentials` jest uwzględniany tylko w metodzie `Create` pakietu `Grpc.Net.Client`, aby zachować zgodność z pakietem `Grpc.Core`.

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
> Metody `ChannelCredentials.Create` można użyć dla klienta bez uwierzytelniania przy użyciu certyfikatu. Jest to przydatny sposób przekazywania poświadczeń tokenu przy każdym wywołaniu w kanale.

W serwisie GitHub została [dodana wersja przykładowej aplikacji GRPC FullStockTicker z uwierzytelnianiem przy użyciu certyfikatu](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) .

>[!div class="step-by-step"]
>[Poprzednie](call-credentials.md)
>[dalej](encryption.md)
