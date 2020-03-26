---
title: Samodzielne aplikacje gRPC - gRPC dla programistów WCF
description: Wdrażanie ASP.NET podstawowych aplikacji gRPC jako usług hostowanych samodzielnie.
ms.date: 09/02/2019
ms.openlocfilehash: 69f70e4077247fd07eba7abeee82f257dd1f4f90
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110909"
---
# <a name="self-hosted-grpc-applications"></a>Samodzielne aplikacje gRPC

Chociaż aplikacje ASP.NET Core 3.0 mogą być hostowane w usługach IIS w systemie Windows Server, obecnie nie można hostować aplikacji gRPC w usługach IIS, ponieważ niektóre funkcje HTTP/2 nie są obsługiwane. Ta funkcja jest celem przyszłej aktualizacji systemu Windows Server.

Aplikację można uruchomić jako usługę systemu Windows. Możesz też uruchomić go jako usługę Linux kontrolowaną przez [systemd](https://en.wikipedia.org/wiki/Systemd), ze względu na nowe funkcje w rozszerzeniach hostingu .NET Core 3.0.

## <a name="run-your-app-as-a-windows-service"></a>Uruchamianie aplikacji jako usługi systemu Windows

Aby skonfigurować aplikację ASP.NET Core do uruchamiania jako usługa systemu Windows, zainstaluj pakiet [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) z nuget. Następnie dodaj wywołanie `UseWindowsService` `CreateHostBuilder` do `Program.cs`metody w pliku .

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
> Jeśli aplikacja nie jest uruchomiona jako usługa `UseWindowsService` systemu Windows, metoda nie robi nic.

Teraz opublikuj aplikację przy użyciu jednej z następujących metod:

* W programie Visual Studio, klikając prawym przyciskiem myszy projekt i wybierając **polecenie Publikuj** w menu skrótów.
* Z interfejsu wiersza polecenia .NET Core.

Podczas publikowania aplikacji .NET Core można utworzyć wdrożenie *zależne od struktury* lub *samodzielne* wdrożenie. Wdrożenia zależne od struktury wymagają instalowany współdzielony czas wykonywania .NET Core na hoście, na którym są uruchamiane. Samodzielne wdrożenia są publikowane z pełną kopią środowiska uruchomieniowego i struktury .NET Core i mogą być uruchamiane na dowolnym hoście. Aby uzyskać więcej informacji, w tym zalety i wady każdego podejścia, zobacz dokumentację [wdrażania aplikacji .NET Core.](../../core/deploying/index.md)

Aby opublikować niezależną kompilację aplikacji, która nie wymaga zainstalowania środowiska uruchomieniowego .NET Core 3.0 na hoście, należy określić środowisko wykonawcze, które ma zostać dołączone do aplikacji. Użyj `-r` flagi `--runtime`(lub).

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

Aby opublikować kompilację zależną `-r` od struktury, pomiń flagę.

```dotnetcli
dotnet publish -c Release -o ./publish
```

Skopiuj `publish` pełną zawartość katalogu do folderu instalacyjnego. Następnie użyj [narzędzia sc,](/windows/desktop/services/controlling-a-service-using-sc) aby utworzyć usługę systemu Windows dla pliku wykonywalnego.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>Logowanie do dziennika zdarzeń systemu Windows

Metoda `UseWindowsService` automatycznie dodaje dostawcę [rejestrowania,](/aspnet/core/fundamentals/logging/) który zapisuje komunikaty dziennika do dziennika zdarzeń systemu Windows. Rejestrowanie dla tego dostawcy można skonfigurować, dodając `EventLog` wpis do `Logging` sekcji `appsettings.json` lub innego źródła konfiguracji.

Nazwę źródła używaną w dzienniku zdarzeń można `SourceName` zastąpić, ustawiając właściwość w tych ustawieniach. Jeśli nie określisz nazwy, zostanie użyta domyślna nazwa aplikacji (zwykle nazwa zestawu wykonywalnego).

Więcej informacji na temat rejestrowania znajduje się na końcu tego rozdziału.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Uruchamianie aplikacji jako usługi Linux za pomocą systemu

Aby skonfigurować aplikację ASP.NET Core do uruchamiania jako usługa Linux (lub *demona* w żargonie systemu Linux), zainstaluj pakiet [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) z NuGet. Następnie dodaj wywołanie `UseSystemd` `CreateHostBuilder` do `Program.cs`metody w pliku .

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
> Jeśli aplikacja nie jest uruchomiona jako usługa `UseSystemd` Linux, metoda nie robi nic.

Teraz opublikuj aplikację. Aplikacja może być zależna od struktury lub niezależna dla odpowiedniego środowiska `linux-x64`wykonawczego systemu Linux (na przykład ). Można publikować przy użyciu jednej z następujących metod:

* W programie Visual Studio, klikając prawym przyciskiem myszy projekt i wybierając **polecenie Publikuj** w menu skrótów.
* Z interfejsu wiersza polecenia .NET Core, za pomocą następującego polecenia:

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
Skopiuj `publish` pełną zawartość katalogu do folderu instalacyjnego na hoście systemu Linux. Rejestracja usługi wymaga specjalnego pliku, zwanego *plikiem jednostkowym,* który ma zostać dodany do `/etc/systemd/system` katalogu. Aby utworzyć plik w tym folderze, musisz mieć uprawnienia administratora. Nazwij plik identyfikatorem, `systemd` którego chcesz `.service` użyć, i rozszerzeniem. Użyj na przykład nazwy `/etc/systemd/system/myapp.service`.

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

Właściwość `Type=notify` `systemd` informuje, że aplikacja powiadomi go podczas uruchamiania i zamykania. Ustawienie `WantedBy=multi-user.target` spowoduje uruchomienie usługi, gdy system Linux osiągnie "runlevel 2", co oznacza, że aktywna jest powłoka niegraficzną, wielouchwytowa.

Zanim `systemd` rozpozna usługę, musi ponownie załadować jej konfigurację. Można `systemd` kontrolować za `systemctl` pomocą polecenia. Po ponownym załadowaniu `status` użyj podpokazu, aby potwierdzić, że aplikacja została pomyślnie zarejestrowana.

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
> Rozszerzenie `.service` jest opcjonalne podczas `systemctl start`korzystania z programu .

Aby `systemd` poinformować o automatycznym uruchomieniu usługi `enable` podczas uruchamiania systemu, użyj polecenia.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Zaloguj się do dziennika

Linux odpowiednik dziennika zdarzeń systemu `journald`Windows jest, ustrukturyzowała usługa `systemd`systemu rejestrowania, który jest częścią . Komunikaty dziennika zapisane na standardowym wyjściu przez demona `journald`Linuksa są automatycznie zapisywane na . Aby skonfigurować poziomy rejestrowania, należy użyć `Console` sekcji konfiguracji rejestrowania. Metoda `UseSystemd` konstruktora hostów automatycznie konfiguruje format wyjściowy konsoli do arkusza.

Ponieważ `journald` jest to standard dla dzienników Linuksa, wiele narzędzi integruje się z nim. Dzienniki można łatwo `journald` rozsyłać z zewnętrznego systemu rejestrowania. Pracując lokalnie na hoście, `journalctl` można użyć polecenia do wyświetlania dzienników z wiersza polecenia.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Jeśli masz środowisko GUI dostępne na swoim hoście, kilka graficznych widzów dziennika są dostępne dla Linuksa, takich jak *QJournalctl* i *gnome-logs*.

Aby dowiedzieć się `systemd` więcej na temat wykonywania `journalctl`zapytań do arkusza z wiersza polecenia za pomocą programu , zobacz [strony manpages](https://manpages.debian.org/buster/systemd/journalctl.1).

## <a name="https-certificates-for-self-hosted-applications"></a>Certyfikaty HTTPS dla aplikacji hostowanych samodzielnie

Podczas uruchamiania aplikacji gRPC w produkcji należy użyć certyfikatu TLS z zaufanego urzędu certyfikacji (CA). Ten urząd certyfikacji może być urzędem certyfikacji lub wewnętrznym urzędem certyfikacji dla organizacji.

Na hostach systemu Windows można załadować certyfikat z <xref:System.Security.Cryptography.X509Certificates.X509Store> bezpiecznego magazynu [certyfikatów](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) przy użyciu klasy. Można również użyć `X509Store` klasy z magazynu kluczy OpenSSL na niektórych hostach systemu Linux.

Certyfikaty można również tworzyć przy użyciu jednego z [konstruktorów X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), z:

* Plik, taki jak `.pfx` plik chroniony silnym hasłem
* Dane binarne pobrane z bezpiecznej usługi pamięci masowej, takiej jak [Usługa Azure Key Vault](https://azure.microsoft.com/services/key-vault/)

Kestrel można skonfigurować tak, aby używała certyfikatu na dwa sposoby: z konfiguracji lub kodu.

### <a name="set-https-certificates-by-using-configuration"></a>Ustawianie certyfikatów HTTPS przy użyciu konfiguracji

Podejście konfiguracji wymaga ustawienia ścieżki `.pfx` do pliku certyfikatu i hasła w sekcji konfiguracji Pustułka. W `appsettings.json`, które wyglądają tak:

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

Podaj hasło przy użyciu bezpiecznego źródła konfiguracji, takiego jak Azure Key Vault lub Hashicorp Vault.

> [!IMPORTANT]
> Nie przechowuj niezaszyfrowanych haseł w plikach konfiguracyjnych.

### <a name="set-https-certificates-in-code"></a>Ustawianie certyfikatów HTTPS w kodzie

Aby skonfigurować https na Kestrel `ConfigureKestrel` w `IWebHostBuilder` kodzie, należy użyć metody w `Program` klasie.

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

Ponownie należy zapisać hasło `.pfx` do pliku i pobrać je z bezpiecznego źródła konfiguracji.

>[!div class="step-by-step"]
>[Poprzedni](grpc-in-production.md)
>[następny](docker.md)
