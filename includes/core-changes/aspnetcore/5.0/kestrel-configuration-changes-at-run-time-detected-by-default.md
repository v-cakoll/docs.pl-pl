---
ms.openlocfilehash: d00b8ecaa61b358e062d85a2b68ca8a95cada442
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803268"
---
### <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a>Kestrel: domyślnie wykryto zmiany konfiguracji w czasie wykonywania

Kestrel teraz reaguje na zmiany wprowadzone w `Kestrel` sekcji `IConfiguration` wystąpienia projektu (na przykład *appsettings.json*) w czasie wykonywania. Aby dowiedzieć się więcej o konfigurowaniu Kestrel przy użyciu *appsettings.json*, zobacz *appsettings.jsna* przykład w [konfiguracji punktu końcowego](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).

Kestrel będzie powiązać, usunąć powiązania i ponownie powiązać punkty końcowe w celu reagowania na te zmiany konfiguracji.

Aby zapoznać się z omówieniem, zobacz temat Issue [dotnet/aspnetcore # 22807](https://github.com/dotnet/aspnetcore/issues/22807).

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 7

#### <a name="old-behavior"></a>Stare zachowanie

Przed ASP.NET Core 5,0 wersji zapoznawczej 6 Kestrel nie obsługiwał zmiany konfiguracji w czasie wykonywania.

W ASP.NET Core 5,0 w wersji zapoznawczej 6 można przystąpić do domyślnego zachowania, które odbędzie się do zmian konfiguracji w czasie wykonywania. Ręczne wyKestrelnie wymaganej konfiguracji powiązanego powiązania:

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.Hosting;

public class Program
{
    public static void Main(string[] args) =>
        CreateHostBuilder(args).Build().Run();

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                {
                    kestrelOptions.Configure(
                        builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: true);
                });

                webBuilder.UseStartup<Startup>();
            });
}
```

#### <a name="new-behavior"></a>Nowe zachowanie

Kestrel domyślnie reaguje na zmiany konfiguracji w czasie wykonywania. W celu obsługi tej zmiany <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> program `KestrelServerOptions.Configure(IConfiguration, bool)` Domyślnie wywołuje program `reloadOnChange: true` .

#### <a name="reason-for-change"></a>Przyczyna zmiany

Wprowadzono zmiany w celu obsługi ponownej konfiguracji punktu końcowego w czasie wykonywania bez całkowitego ponownego uruchomienia serwera. W przeciwieństwie do pełnego ponownego uruchomienia serwera, niezmienione punkty końcowe nie są nawet tymczasowo niepowiązane.

#### <a name="recommended-action"></a>Zalecana akcja

* W przypadku większości scenariuszy, w których domyślna sekcja konfiguracji Kestrel nie zmienia się w czasie wykonywania, ta zmiana nie ma wpływu i nie jest wymagana żadna akcja.
* W przypadku scenariuszy, w których domyślna sekcja konfiguracji Kestrel zmienia się w czasie wykonywania, a Kestrel powinna reagować na nie, jest to teraz zachowanie domyślne.
* W przypadku scenariuszy, w których domyślna sekcja konfiguracji Kestrel jest zmieniana w czasie wykonywania, a Kestrel nie powinna reagować na nią, można zrezygnować z następujących metod:

    ```csharp
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                    {
                        kestrelOptions.Configure(
                            builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: false);
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

**Uwagi:**

Ta zmiana nie modyfikuje zachowania `KestrelServerOptions.Configure(IConfiguration)` przeciążenia, które nadal jest `reloadOnChange: false` zachowaniem domyślnym.

Ważne jest również, aby upewnić się, że źródło konfiguracji obsługuje ponowne ładowanie. W przypadku źródeł JSON ponowne ładowanie jest konfigurowane przez wywołanie metody `AddJsonFile(path, reloadOnChange: true)` . Ponowne ładowanie jest już skonfigurowane domyślnie dla *appsettings.jsw* i *appSettings. { Environment}. JSON*.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
