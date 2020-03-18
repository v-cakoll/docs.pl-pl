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
# <a name="channel-credentials"></a>Poświadczenia kanałów

Jak sama nazwa wskazuje, poświadczenia kanału są dołączone do podstawowego kanału gRPC. Standardowa forma poświadczeń kanału używa uwierzytelniania certyfikatu klienta. W tym procesie klient udostępnia certyfikat TLS podczas nawiązywania połączenia, a następnie serwer sprawdza to przed zezwoleniem na wszelkie wywołania do nawiązywania.

Można połączyć poświadczenia kanału z poświadczeniami wywołania, aby zapewnić kompleksowe zabezpieczenia usługi gRPC. Poświadczenia kanału udowodnić, że aplikacja kliencka może uzyskać dostęp do usługi, a poświadczenia wywołania zawierają informacje o osobie, która korzysta z aplikacji klienckiej.

Uwierzytelnianie certyfikatów klienta działa dla gRPC w taki sam sposób, jak działa dla ASP.NET Core. Aby uzyskać więcej informacji, zobacz [Konfigurowanie uwierzytelniania certyfikatów w ASP.NET core](/aspnet/core/security/authentication/certauth).

Do celów deweloperskich można użyć certyfikatu z podpisem własnym, ale do produkcji należy użyć odpowiedniego certyfikatu HTTPS podpisanego przez zaufany urząd.

## <a name="add-certificate-authentication-to-the-server"></a>Dodawanie uwierzytelniania certyfikatów do serwera

Konfigurowanie uwierzytelniania certyfikatów zarówno na poziomie hosta (na przykład na serwerze Kestrel), jak i w potoku ASP.NET Core.

### <a name="configure-certificate-validation-on-kestrel"></a>Konfigurowanie sprawdzania poprawności certyfikatów w pustułku

Kestrel (ASP.NET core http) można skonfigurować do wymagania certyfikatu klienta i opcjonalnie do przeprowadzenia weryfikacji dostarczonego certyfikatu przed zaakceptowaniem połączeń przychodzących. Można to zrobić `CreateWebHostBuilder` w `Program` metodzie klasy, `Startup`a nie w .

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

To `ClientCertificateMode.RequireCertificate` ustawienie powoduje, że kestrel natychmiast odrzuca żądanie połączenia, które nie udostępnia certyfikatu klienta, ale to ustawienie samo w sobie nie sprawdza poprawność certyfikatu, który jest dostarczany. Dodaj `ClientCertificateValidation` wywołanie odgłosowe, aby umożliwić kestrel do sprawdzania poprawności certyfikatu klienta w punkcie nawiązywanie połączenia, przed ASP.NET Core potoku jest włączony. (W takim przypadku wywołanie wsteczne zapewnia, że został wystawiony przez ten sam *urząd certyfikacji* co certyfikat serwera).

### <a name="add-aspnet-core-certificate-authentication"></a>Dodawanie uwierzytelniania certyfikatu ASP.NET core

Pakiet [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet zapewnia uwierzytelnianie certyfikatów.

Dodaj usługę uwierzytelniania certyfikatów w metodzie `ConfigureServices` i dodaj uwierzytelnianie `Configure` i autoryzację do potoku ASP.NET Core w metodzie.

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

Za `Grpc.Net.Client` pomocą pakietu można skonfigurować <xref:System.Net.Http.HttpClient> certyfikaty w wystąpieniu, które jest dostarczane do `GrpcChannel` używanego dla połączenia.

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

## <a name="combine-channelcredentials-and-callcredentials"></a>Łączenie poświadczeń kanału i poświadczeń wywołań

Serwer można skonfigurować tak, aby używał uwierzytelniania certyfikatów i tokenów. Należy to zrobić, stosując zmiany certyfikatu do serwera Kestrel i używając pośredniczonego pośredniczynicy JWT w ASP.NET Core.

Aby podać `ChannelCredentials` `CallCredentials` zarówno i na `ChannelCredentials.Create` kliencie, należy użyć metody, aby zastosować poświadczenia wywołania. Nadal należy zastosować uwierzytelnianie <xref:System.Net.Http.HttpClient> certyfikatów przy użyciu wystąpienia. Jeśli przekażesz żadnych `SslCredentials` argumentów do konstruktora, wewnętrzny kod klienta zgłasza wyjątek. Parametr `SslCredentials` jest tylko zawarte `Grpc.Net.Client` w `Create` metodzie pakietu, `Grpc.Core` aby zachować zgodność z pakietem.

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
> Można użyć `ChannelCredentials.Create` metody dla klienta bez uwierzytelniania certyfikatu. Jest to przydatny sposób przekazywania poświadczeń tokenu z każdym wywołaniem nakanale.

Wersja [przykładowej aplikacji gRPC firmy FullStockTicker z dodanym uwierzytelnianiem certyfikatów](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) znajduje się w usyłku GitHub.

>[!div class="step-by-step"]
>[Poprzedni](call-credentials.md)
>[następny](encryption.md)
