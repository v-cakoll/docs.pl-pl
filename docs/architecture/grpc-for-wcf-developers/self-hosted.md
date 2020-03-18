---
title: Aplikacje gRPC hostowane samodzielnie - gRPC dla programistów WCF
description: Wdrażanie ASP.NET aplikacji Core gRPC jako usług hostowanych samodzielnie.
ms.date: 09/02/2019
ms.openlocfilehash: 00fb1453e19a02469f80af79672e0c1f72c7280f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147805"
---
# <a name="self-hosted-grpc-applications"></a>Aplikacje gRPC hostowane samodzielnie

Chociaż ASP.NET aplikacje Core 3.0 mogą być hostowane w usługach IIS w systemie Windows Server, obecnie nie jest możliwe hosta aplikacji gRPC w usługach IIS, ponieważ niektóre funkcje HTTP/2 nie są obsługiwane. Ta funkcja jest celem przyszłej aktualizacji systemu Windows Server.

Aplikację można uruchomić jako usługę systemu Windows. Lub można go uruchomić jako usługę Linux kontrolowane przez [systemd](https://en.wikipedia.org/wiki/Systemd), ze względu na nowe funkcje w .NET Core 3.0 hosting rozszerzeń.

## <a name="run-your-app-as-a-windows-service"></a>Uruchamianie aplikacji jako usługi systemu Windows

Aby skonfigurować aplikację ASP.NET Core do uruchamiania jako usługa systemu Windows, zainstaluj pakiet [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) z NuGet. Następnie dodaj wywołanie `UseWindowsService` `CreateHostBuilder` do `Program.cs`metody w pliku .

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
> Jeśli aplikacja nie jest uruchomiona jako `UseWindowsService` usługa systemu Windows, metoda nic nie robi.

Teraz opublikuj aplikację przy użyciu jednej z następujących metod:

* W programie Visual Studio kliknij prawym przyciskiem myszy projekt i wybierając polecenie **Publikuj** w menu skrótów.
* Z .NET Core CLI.

Podczas publikowania aplikacji .NET Core można utworzyć wdrożenie *zależne od struktury* lub wdrożenie *niezależne.* Wdrożenia zależne od struktury wymagają zainstalowania udostępnionego serwera .NET Core na hoście, na którym są uruchamiane. Niezależne wdrożenia są publikowane z pełną kopią programu runtime i struktury programu .NET Core i można je uruchamiać na dowolnym hoście. Aby uzyskać więcej informacji, w tym zalety i wady każdego podejścia, zobacz .NET Core dokumentacji [wdrażania aplikacji.](../../core/deploying/index.md)

Aby opublikować niezależną kompilację aplikacji, która nie wymaga zainstalowania programu .NET Core 3.0 na hoście, należy określić czas uruchomieniowy, który ma zostać dołączony do aplikacji. Użyj `-r` flagi `--runtime`(lub ) .

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

Aby opublikować kompilacji zależnej `-r` od struktury, pominąć flagę.

```dotnetcli
dotnet publish -c Release -o ./publish
```

Skopiuj pełną `publish` zawartość katalogu do folderu instalacyjnego. Następnie użyj [narzędzia sc,](/windows/desktop/services/controlling-a-service-using-sc) aby utworzyć usługę systemu Windows dla pliku wykonywalnego.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>Rejestrowanie w dzienniku zdarzeń systemu Windows

Metoda `UseWindowsService` automatycznie dodaje dostawcę [rejestrowania,](/aspnet/core/fundamentals/logging/) który zapisuje komunikaty dziennika do dziennika zdarzeń systemu Windows. Rejestrowanie dla tego dostawcy można `EventLog` skonfigurować, `Logging` dodając `appsettings.json` wpis do sekcji lub innego źródła konfiguracji.

Można zastąpić nazwę źródłową używaną w dzienniku zdarzeń, ustawiając `SourceName` właściwość w tych ustawieniach. Jeśli nie określisz nazwy, zostanie użyta domyślna nazwa aplikacji (zwykle nazwa zestawu wykonywalnego).

Więcej informacji na temat rejestrowania znajduje się na końcu tego rozdziału.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Uruchom aplikację jako usługę Linux z systememd

Aby skonfigurować aplikację ASP.NET Core do uruchamiania jako usługa Systemu Linux (lub *daemon* w żargonie systemu Linux), zainstaluj pakiet [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) z NuGet. Następnie dodaj wywołanie `UseSystemd` `CreateHostBuilder` do `Program.cs`metody w pliku .

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
> Jeśli aplikacja nie jest uruchomiona jako `UseSystemd` usługa Systemu Linux, metoda nic nie robi.

Teraz opublikuj aplikację. Aplikacja może być zależna od struktury lub niezależna dla odpowiedniego uruchomienia `linux-x64`systemu Linux (na przykład). Można opublikować przy użyciu jednej z następujących metod:

* W programie Visual Studio kliknij prawym przyciskiem myszy projekt i wybierając polecenie **Publikuj** w menu skrótów.
* Z polecenia CLI .NET Core przy użyciu następującego polecenia:

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
Skopiuj pełną `publish` zawartość katalogu do folderu instalacyjnego na hoście systemu Linux. Rejestracja usługi wymaga specjalnego pliku, zwanego *plikiem jednostki,* który ma zostać dodany do `/etc/systemd/system` katalogu. Do utworzenia pliku w tym folderze potrzebne jest uprawnienie administratora. Nazwij plik identyfikatorem, `systemd` którego chcesz `.service` użyć, i rozszerzeniem. Użyj na przykład nazwy `/etc/systemd/system/myapp.service`.

Plik usługi używa formatu INI, jak pokazano w tym przykładzie:

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

Właściwość `Type=notify` informuje, `systemd` że aplikacja powiadomi go podczas uruchamiania i zamykania. Ustawienie `WantedBy=multi-user.target` spowoduje uruchomienie usługi, gdy system Linux osiągnie "poziom uruchamiania 2", co oznacza, że niegraficzna powłoka dla wielu użytkowników jest aktywna.

Zanim `systemd` rozpozna usługę, musi ponownie załadować jej konfigurację. Kontroluj `systemd` za `systemctl` pomocą polecenia. Po ponownym załadowaniu `status` użyj podpolecenia, aby potwierdzić, że aplikacja została pomyślnie zarejestrowana.

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

Jeśli usługa została poprawnie skonfigurowana, otrzymasz następujące dane wyjściowe:

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

Użyj `start` polecenia, aby uruchomić usługę.

```console
sudo systemctl start myapp.service
```

> [!TIP]
> Rozszerzenie `.service` jest opcjonalne, gdy `systemctl start`używasz .

Aby `systemd` poinformować, aby uruchomić usługę automatycznie `enable` podczas uruchamiania systemu, użyj polecenia.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Rejestrowanie do dziennika

Linux odpowiednik dziennika zdarzeń `journald`systemu Windows jest , ustrukturyzowanej usługi systemu rejestrowania, który jest częścią `systemd`. Wiadomości dziennika zapisane do standardowego wyjścia przez daemon `journald`Linux są automatycznie zapisywane do . Aby skonfigurować poziomy rejestrowania, należy użyć `Console` sekcji konfiguracji rejestrowania. Metoda `UseSystemd` konstruktora hostów automatycznie konfiguruje format wyjściowy konsoli do obsługi arkusza.

Ponieważ `journald` jest to standard dla dzienników Linuksa, różne narzędzia integrują się z nim. Dzienniki można łatwo `journald` kierować z ewnętrznego systemu rejestrowania. Pracując lokalnie na hoście, `journalctl` można użyć polecenia do wyświetlania dzienników z wiersza polecenia.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Jeśli masz środowisko graficzne dostępne na hoście, dla systemu Linux dostępnych jest kilka graficznych dzienników, takich jak *QJournalctl* i *gnome-logi.*

Aby dowiedzieć się więcej `systemd` o śledzeniu `journalctl`dziennika z wiersza polecenia za pomocą , zobacz [strony osoby .](https://manpages.debian.org/buster/systemd/journalctl.1)

## <a name="https-certificates-for-self-hosted-applications"></a>Certyfikaty HTTPS dla aplikacji hostowanych samodzielnie

Podczas uruchamiania aplikacji gRPC w środowisku produkcyjnym należy użyć certyfikatu TLS z zaufanego urzędu certyfikacji (CA). Ten urząd certyfikacji może być publicznym urządem certyfikacji lub wewnętrznym urządem certyfikacji organizacji.

Na hostach systemu Windows certyfikat można załadować z <xref:System.Security.Cryptography.X509Certificates.X509Store> bezpiecznego [magazynu certyfikatów](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) przy użyciu tej klasy. Można również użyć `X509Store` klasy z magazynu kluczy OpenSSL na niektórych hostach systemu Linux.

Certyfikaty można również tworzyć przy użyciu jednego z [konstruktorów X509Certificate2,](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)z jednego z:

* Plik, taki jak `.pfx` plik chroniony silnym hasłem
* Dane binarne pobrane z bezpiecznej usługi magazynu, takiej jak [Usługa Azure Key Vault](https://azure.microsoft.com/services/key-vault/)

Kestrel można skonfigurować tak, aby używał certyfikatu na dwa sposoby: od konfiguracji lub w kodzie.

### <a name="set-https-certificates-by-using-configuration"></a>Ustawianie certyfikatów HTTPS przy użyciu konfiguracji

Podejście konfiguracyjne wymaga ustawienia `.pfx` ścieżki do pliku certyfikatu i hasła w sekcji konfiguracji kestrel. W `appsettings.json`, że będzie wyglądać tak:

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

Podaj hasło przy użyciu bezpiecznego źródła konfiguracji, takiego jak Usługa Azure Key Vault lub Hashicorp Vault.

> [!IMPORTANT]
> Nie przechowuj niezaszyfrowanych haseł w plikach konfiguracyjnych.

### <a name="set-https-certificates-in-code"></a>Ustawianie certyfikatów HTTPS w kodzie

Aby skonfigurować protokół HTTPS na kestrel `IWebHostBuilder` w `Program` kodzie, należy użyć `ConfigureKestrel` metody w klasie.

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

Ponownie pamiętaj, aby zapisać hasło `.pfx` do pliku i pobrać go z bezpiecznego źródła konfiguracji.

>[!div class="step-by-step"]
>[Poprzedni](grpc-in-production.md)
>[następny](docker.md)
