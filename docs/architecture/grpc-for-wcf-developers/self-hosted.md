---
title: Własne hostowane aplikacje gRPC — gRPC dla deweloperów WCF
description: Wdrażanie aplikacji ASP.NET Core gRPC jako usług samoobsługowych.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1269137b58f4d25f407a6a04327c51bc9f069c1b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184107"
---
# <a name="self-hosted-grpc-applications"></a>Własne hostowane aplikacje gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Chociaż aplikacje ASP.NET Core 3,0 mogą być hostowane w usługach IIS w systemie Windows Server, obecnie nie jest możliwe hostowanie aplikacji gRPC w usługach IIS, ponieważ niektóre funkcje protokołu HTTP/2 nie są jeszcze obsługiwane. Ta funkcja jest oczekiwana w przyszłej aktualizacji systemu Windows Server.

Możesz uruchomić aplikację jako usługę systemu Windows lub jako usługę systemu Linux sterowaną przez [system](https://en.wikipedia.org/wiki/Systemd), korzystając z pewnych nowych funkcji w rozszerzeniach hostingu platformy .net Core 3,0.

## <a name="run-your-app-as-a-windows-service"></a>Uruchamianie aplikacji jako usługi systemu Windows

Aby skonfigurować aplikację ASP.NET Core tak, aby była uruchamiana jako usługa systemu Windows, zainstaluj pakiet [Microsoft. Extensions. hosting. WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) z narzędzia NuGet. Następnie Dodaj wywołanie `UseWindowsService` `CreateHostBuilder` do metody w `Program.cs`.

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseWindowsService() // Enable running as a Windows service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> Jeśli aplikacja nie działa jako usługa systemu Windows, `UseWindowsService` Metoda nie wykonuje żadnych działań.

Teraz Opublikuj aplikację, korzystając z programu Visual Studio, klikając prawym przyciskiem myszy projekt i wybierając pozycję *Publikuj* z menu kontekstowego lub z interfejs wiersza polecenia platformy .NET Core.

Podczas publikowania aplikacji .NET Core można utworzyć wdrożenie *zależne od platformy* lub wdrożenie *samodzielne* . Wdrożenia zależne od platformy wymagają zainstalowania wspólnego środowiska uruchomieniowego platformy .NET Core na hoście, na którym są uruchamiane. Wstępnie zawarte wdrożenia są publikowane z pełną kopią środowiska uruchomieniowego i platformy .NET Core i mogą być uruchamiane na dowolnym hoście. Aby uzyskać więcej informacji, w tym zalety i wady każdego podejścia, zapoznaj się z dokumentacją [wdrażania aplikacji .NET Core](https://docs.microsoft.com/dotnet/core/deploying/) .

Aby opublikować samodzielną kompilację aplikacji, która nie wymaga zainstalowania środowiska uruchomieniowego programu .NET Core 3,0 na hoście, określ środowisko uruchomieniowe, które ma zostać dołączone do aplikacji przy użyciu `-r` flagi (lub `--runtime`).

```console
dotnet publish -c Release -r win-x64 -o ./publish
```

Aby opublikować kompilację zależną od platformy, Pomiń `-r` flagę.

```console
dotnet publish -c Release -o ./publish
```

Skopiuj kompletną zawartość `publish` katalogu do folderu instalacyjnego i Użyj [narzędzia SC](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) , aby utworzyć usługę systemu Windows dla pliku wykonywalnego.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-windows-event-log"></a>Rejestruj w dzienniku zdarzeń systemu Windows

Metoda automatycznie dodaje dostawcę rejestrowania, który zapisuje komunikaty dziennika w dzienniku zdarzeń systemu Windows. [](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) `UseWindowsService` Rejestrowanie dla tego dostawcy można skonfigurować przez dodanie `EventLog` wpisu `Logging` do sekcji `appsettings.json` lub innego źródła konfiguracji. Nazwę źródła używaną w dzienniku zdarzeń można przesłonić, ustawiając `SourceName` właściwość w tych ustawieniach. Jeśli nie określisz nazwy, zostanie użyta domyślna nazwa aplikacji (zazwyczaj nazwa zestawu wykonywalnego).

Więcej informacji na temat rejestrowania znajduje się na końcu tego rozdziału.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Uruchamianie aplikacji jako usługi systemu Linux z systemem

Aby skonfigurować aplikację ASP.NET Core tak, aby była uruchamiana jako usługa systemu Linux (lub *demon* w systemie Linux sprzężeniem), zainstaluj pakiet [Microsoft. Extensions. hosting. systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) z narzędzia NuGet. Następnie Dodaj wywołanie `UseSystemd` `CreateHostBuilder` do metody w `Program.cs`.

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseSystemd() // Enable running as a Systemd service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> Jeśli aplikacja nie działa jako usługa systemu Linux, `UseSystemd` Metoda nie wykonuje żadnych działań.

Teraz Opublikuj aplikację (zależne od platformy lub samodzielne dla odpowiedniego środowiska uruchomieniowego systemu Linux, np. `linux-x64`), w programie Visual Studio, klikając prawym przyciskiem myszy projekt i wybierając pozycję *Publikuj* z menu kontekstowego lub z platformy .NET Rdzeń interfejsu wiersza polecenia przy użyciu poniższe polecenie.

```console
dotnet publish -c Release -r linux-x64 -o ./publish
```

Skopiuj kompletną zawartość `publish` katalogu do folderu instalacji na hoście z systemem Linux. Rejestracja usługi wymaga pliku specjalnego o nazwie "plik jednostkowy", który ma zostać dodany do `/etc/systemd/system` katalogu. Musisz mieć uprawnienia główne, aby utworzyć plik w tym folderze. Nazwij plik z identyfikatorem, którego chcesz `systemd` użyć `.service` , a rozszerzeniem. Na przykład `/etc/systemd/system/myapp.service`.

Plik usługi używa formatu INI, jak pokazano w tym przykładzie.

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

`Type=notify` Właściwość informuje`systemd` , że aplikacja powiadomi ją o uruchomieniu i zamknięciu. `WantedBy=multi-user.target` Ustawienie spowoduje uruchomienie usługi, gdy system Linux osiągnie wartość "runlevel 2", co oznacza, że powłoka wiele użytkowników nie jest aktywna.

Przed `systemd` rozpoznaniem usługi należy ponownie załadować jej konfigurację. Możesz kontrolować `systemd` `systemctl` przy użyciu polecenia. Po ponownym załadowaniu Użyj `status` podpolecenia, aby upewnić się, że aplikacja została pomyślnie zarejestrowana.

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

Jeśli usługa została prawidłowo skonfigurowana, zostaną wyświetlone następujące dane wyjściowe:

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

`start` Użyj polecenia, aby uruchomić usługę.

```console
sudo systemctl start myapp.service
```

> [!TIP]
> Rozszerzenie jest opcjonalne przy użyciu `systemctl start`. `.service`

Aby poinformować `systemd` o automatycznym uruchomieniu usługi przy uruchamianiu systemu, `enable` Użyj polecenia.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Rejestruj w dzienniku

System Linux odpowiadający dziennikowi zdarzeń systemu Windows `journald`to usługa systemu rejestrowania strukturalnego, która jest częścią programu. `systemd` Komunikaty dziennika zapisywane w standardowym wyniku przez demon systemu Linux są automatycznie zapisywane do `journald`, dlatego w celu skonfigurowania poziomów rejestrowania `Console` Użyj sekcji konfiguracji rejestrowania. Metoda `UseSystemd` konstruktora hosta automatycznie konfiguruje format danych wyjściowych konsoli w celu dostosowania go do dziennika.

Ponieważ `journald` jest standardem dla dzienników systemu Linux, istnieje wiele narzędzi, które integrują się z nim i można łatwo kierować dzienniki z `journald` do zewnętrznego systemu rejestrowania. Pracując lokalnie na hoście, można użyć `journalctl` polecenia, aby wyświetlić dzienniki z wiersza polecenia.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Jeśli na hoście jest dostępne środowisko graficznego interfejsu użytkownika, w systemie Linux dostępne są kilka graficznych przeglądarek dzienników, takich jak *QJournalctl* i *GNOME*.

Aby dowiedzieć się więcej o wysyłaniu zapytań do dziennika systemowego z wiersza `journalctl`polecenia za pomocą programu, zobacz [strony man](https://manpages.debian.org/buster/systemd/journalctl.1).

## <a name="https-certificates-for-self-hosted-applications"></a>Certyfikaty HTTPS dla aplikacji samodzielnych

Podczas uruchamiania aplikacji gRPC w środowisku produkcyjnym należy używać certyfikatu TLS z zaufanego urzędu certyfikacji (CA). Ten urząd certyfikacji może być publicznym urzędem certyfikacji lub wewnętrznym.

Na hostach z systemem Windows certyfikat może zostać załadowany z bezpiecznego [magazynu certyfikatów](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores) przy użyciu [klasy X509Store](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0). `X509Store` Klasy można również używać z magazynem kluczy OpenSSL na niektórych hostach z systemem Linux.

Certyfikaty mogą być również tworzone przy użyciu jednego z [konstruktorów X509Certificate2](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), z pliku (na przykład `.pfx` pliku chronionego za pomocą silnego hasła) lub z danych binarnych pobranych z usługi bezpiecznego magazynu, takiej jak [Azure Key Vault ](https://azure.microsoft.com/services/key-vault/).

Kestrel można skonfigurować do korzystania z certyfikatu na dwa sposoby: od konfiguracji lub w kodzie.

### <a name="set-https-certificates-using-configuration"></a>Ustawianie certyfikatów HTTPS przy użyciu konfiguracji

Podejście konfiguracyjne wymaga ustawienia ścieżki do pliku certyfikatu `.pfx` i hasła w sekcji konfiguracji Kestrel. W `appsettings.json` takim przypadku będzie to wyglądać następująco.

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "cert.pfx",
        "Password": "DO NOT STORE PLAINTEXT PASSWORDS IN APPSETTINGS FILES"
      }
    }
  }
}
```

Hasło należy zapewnić przy użyciu bezpiecznego źródła konfiguracji, takiego jak Magazyn kluczy platformy Azure lub magazyn Hashicorp.

NIE należy przechowywać nieszyfrowanych haseł w plikach konfiguracji.

### <a name="set-https-certificates-in-code"></a>Ustawianie certyfikatów HTTPS w kodzie

Aby skonfigurować protokół https na Kestrel w kodzie, należy `ConfigureKestrel` użyć `IWebHostBuilder` metody `Program` w klasie.

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
            webBuilder.ConfigureKestrel(kestrel =>
            {
                kestrel.ConfigureHttpsDefaults(https =>
                {
                    https.ServerCertificate = new X509Certificate2("mycert.pfx", "password");
                });
            });
        });
```

Ponownie hasło do `.pfx` pliku powinno być przechowywane i pobierane z bezpiecznego źródła konfiguracji.

>[!div class="step-by-step"]
>[Poprzedni](grpc-in-production.md)
>[Następny](docker.md)
