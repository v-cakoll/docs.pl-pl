---
title: Poświadczenia kanału — gRPC dla deweloperów WCF
description: Jak zaimplementować i używać poświadczeń kanału gRPC w ASP.NET Core 3,0.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 61305ee47a2c09a0b2a0fd866beb9b7c102ffeaa
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184583"
---
# <a name="channel-credentials"></a>Poświadczenia kanału

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jak wskazuje nazwa, poświadczenia kanału są dołączane do bazowego kanału gRPC. Standardowa forma poświadczeń kanału używa uwierzytelniania certyfikatu klienta, gdy klient udostępnia certyfikat TLS, gdy nastąpi połączenie, które jest weryfikowane przez serwer przed zezwoleniem na wykonywanie jakichkolwiek wywołań.

Poświadczenia kanału można łączyć z poświadczeniami wywołania, aby zapewnić kompleksowe zabezpieczenia usługi gRPC. Poświadczenia kanału potwierdzają, że aplikacja kliencka może uzyskać dostęp do usługi, a poświadczenia wywołania zawierają informacje o osobie korzystającej z aplikacji klienckiej.

Uwierzytelnianie za pomocą certyfikatu klienta działa dla gRPC w taki sam sposób, w jaki działa ASP.NET Core. Ten proces konfiguracji zostanie podsumowany w tym miejscu, ale więcej informacji można znaleźć w artykule [Konfigurowanie uwierzytelniania certyfikatu w ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) .

W celach programistycznych można użyć certyfikatu z podpisem własnym, ale w przypadku produkcji należy użyć odpowiedniego certyfikatu HTTPS podpisanego przez zaufany urząd.

## <a name="adding-certificate-authentication-to-the-server"></a>Dodawanie uwierzytelniania certyfikatu do serwera

Należy skonfigurować uwierzytelnianie certyfikatu zarówno na poziomie hosta, na przykład na serwerze Kestrel, jak i w potoku ASP.NET Core.

### <a name="configuring-certificate-validation-on-kestrel"></a>Konfigurowanie weryfikacji certyfikatu na Kestrel

Można skonfigurować Kestrel (serwer HTTP ASP.NET Core), aby wymagał certyfikatu klienta i opcjonalnie przeprowadzić weryfikację podanego certyfikatu przed zaakceptowaniem połączeń przychodzących. Ta konfiguracja jest wykonywana w `CreateWebHostBuilder` metodzie `Program` klasy, a nie w `Startup`.

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

To `ClientCertificateMode.RequireCertificate` ustawienie spowoduje natychmiastowe odrzucanie wszystkich żądań połączenia, które nie zawierają certyfikatu klienta, ale nie sprawdza poprawności certyfikatu. Dodanie wywołania zwrotnego umożliwia Kestrel Weryfikowanie certyfikatu klienta (w tym przypadku, aby upewnić się, że został wystawiony przez ten sam *urząd certyfikacji* co certyfikat serwera) w momencie nawiązywania połączenia przed ASP.NET Core `ClientCertificateValidation` potok jest zajęty.

### <a name="adding-aspnet-core-certificate-authentication"></a>Dodawanie ASP.NET Core uwierzytelniania certyfikatów

Uwierzytelnianie przy użyciu certyfikatu jest dostarczane przez pakiet NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) .

Dodaj usługę uwierzytelniania certyfikatów w `ConfigureServices` metodzie i Dodaj uwierzytelnianie i autoryzację do potoku ASP.NET Core `Configure` w metodzie.

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

## <a name="providing-channel-credentials-in-the-client-application"></a>Dostarczanie poświadczeń kanału w aplikacji klienckiej

W pakiecie certyfikaty są konfigurowane <xref:System.Net.Http.HttpClient> w wystąpieniu, `GrpcChannel` które jest dostarczane do użytego połączenia. `Grpc.Net.Client`

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

## <a name="combining-channelcredentials-and-callcredentials"></a>Łączenie ChannelCredentials i CallCredentials

Serwer można skonfigurować tak, aby korzystał z uwierzytelniania certyfikatów i tokenów, stosując zmiany certyfikatu na serwerze Kestrel i używając oprogramowania pośredniczącego okaziciela JWT w ASP.NET Core.

Aby zapewnić zarówno ChannelCredentials, jak i CallCredentials na kliencie, użyj `ChannelCredentials.Create` metody, aby zastosować poświadczenia wywołania. Nadal należy zastosować uwierzytelnianie certyfikatu przy użyciu <xref:System.Net.Http.HttpClient> wystąpienia: w przypadku przekazania jakichkolwiek argumentów `SslCredentials` do konstruktora wewnętrzny kod klienta zgłasza wyjątek. Parametr jest uwzględniany tylko `Grpc.Net.Client` w `Create` metodzie pakietu, aby zachować zgodność z `Grpc.Core` pakietem. `SslCredentials`

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
> Możesz użyć `ChannelCredentials.Create` metody dla klienta bez uwierzytelniania przy użyciu certyfikatu, ponieważ jest to przydatny sposób przekazywania poświadczeń tokenu przy każdym wywołaniu w kanale.

W serwisie GitHub została [dodana wersja przykładowej aplikacji GRPC FullStockTicker z uwierzytelnianiem przy użyciu certyfikatu](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) .

>[!div class="step-by-step"]
>[Poprzedni](call-credentials.md)
>[Następny](encryption.md)
