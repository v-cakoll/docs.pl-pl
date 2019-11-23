---
title: Własne hostowane aplikacje gRPC — gRPC dla deweloperów WCF
description: Wdrażanie aplikacji ASP.NET Core gRPC jako usług samoobsługowych.
ms.date: 09/02/2019
ms.openlocfilehash: 59f6275dbf85442bca3a98a1521597ef40e9675b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967212"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="5f8f3-103">Własne hostowane aplikacje gRPC</span><span class="sxs-lookup"><span data-stu-id="5f8f3-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="5f8f3-104">Chociaż aplikacje ASP.NET Core 3,0 mogą być hostowane w usługach IIS w systemie Windows Server, obecnie nie jest możliwe hostowanie aplikacji gRPC w usługach IIS, ponieważ niektóre funkcje protokołu HTTP/2 nie są jeszcze obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't yet supported.</span></span> <span data-ttu-id="5f8f3-105">Ta funkcja jest oczekiwana w przyszłej aktualizacji systemu Windows Server.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-105">This functionality is expected in a future update to Windows Server.</span></span>

<span data-ttu-id="5f8f3-106">Możesz uruchomić aplikację jako usługę systemu Windows lub jako usługę systemu Linux sterowaną przez [system](https://en.wikipedia.org/wiki/Systemd), korzystając z pewnych nowych funkcji w rozszerzeniach hostingu platformy .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-106">You can run your application as a Windows Service, or as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), thanks to some new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="5f8f3-107">Uruchamianie aplikacji jako usługi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5f8f3-107">Run your app as a Windows service</span></span>

<span data-ttu-id="5f8f3-108">Aby skonfigurować aplikację ASP.NET Core tak, aby była uruchamiana jako usługa systemu Windows, zainstaluj pakiet [Microsoft. Extensions. hosting. WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) z narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-108">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="5f8f3-109">Następnie Dodaj wywołanie do `UseWindowsService` do metody `CreateHostBuilder` w `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-109">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="5f8f3-110">Jeśli aplikacja nie działa jako usługa systemu Windows, Metoda `UseWindowsService` nie wykonuje żadnego działania.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-110">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="5f8f3-111">Teraz Opublikuj aplikację, korzystając z programu Visual Studio, klikając prawym przyciskiem myszy projekt i wybierając pozycję *Publikuj* z menu kontekstowego lub z interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-111">Now publish your application, either from Visual Studio by right-clicking the project and choosing *Publish* from the context menu, or from the .NET Core CLI.</span></span>

<span data-ttu-id="5f8f3-112">Podczas publikowania aplikacji .NET Core można utworzyć wdrożenie *zależne od platformy* lub wdrożenie *samodzielne* .</span><span class="sxs-lookup"><span data-stu-id="5f8f3-112">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="5f8f3-113">Wdrożenia zależne od platformy wymagają zainstalowania wspólnego środowiska uruchomieniowego platformy .NET Core na hoście, na którym są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-113">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="5f8f3-114">Wstępnie zawarte wdrożenia są publikowane z pełną kopią środowiska uruchomieniowego i platformy .NET Core i mogą być uruchamiane na dowolnym hoście.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-114">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="5f8f3-115">Aby uzyskać więcej informacji, w tym zalety i wady każdego podejścia, zapoznaj się z dokumentacją [wdrażania aplikacji .NET Core](https://docs.microsoft.com/dotnet/core/deploying/) .</span><span class="sxs-lookup"><span data-stu-id="5f8f3-115">For more information, including the advantages and disadvantages of each approach, refer to the [.NET Core application deployment](https://docs.microsoft.com/dotnet/core/deploying/) documentation.</span></span>

<span data-ttu-id="5f8f3-116">Aby opublikować samodzielną kompilację aplikacji, która nie wymaga zainstalowania środowiska uruchomieniowego programu .NET Core 3,0 na hoście, określ środowisko uruchomieniowe, które ma zostać dołączone do aplikacji przy użyciu flagi `-r` (lub `--runtime`).</span><span class="sxs-lookup"><span data-stu-id="5f8f3-116">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application using the `-r` (or `--runtime`) flag.</span></span>

```console
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="5f8f3-117">Aby opublikować kompilację zależną od platformy, Pomiń flagę `-r`.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-117">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```console
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="5f8f3-118">Skopiuj kompletną zawartość katalogu `publish` do folderu instalacyjnego i Użyj [narzędzia SC](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) , aby utworzyć usługę systemu Windows dla pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-118">Copy the complete contents of the `publish` directory to an installation folder, and use the [sc utility](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-windows-event-log"></a><span data-ttu-id="5f8f3-119">Rejestruj w dzienniku zdarzeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5f8f3-119">Log to Windows Event Log</span></span>

<span data-ttu-id="5f8f3-120">Metoda `UseWindowsService` automatycznie dodaje dostawcę [rejestrowania](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) , który zapisuje komunikaty dziennika w dzienniku zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-120">The `UseWindowsService` method automatically adds a [Logging](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) provider that writes log messages to the Windows Event Log.</span></span> <span data-ttu-id="5f8f3-121">Można skonfigurować rejestrowanie dla tego dostawcy, dodając wpis `EventLog` do sekcji `Logging` `appsettings.json` lub innego źródła konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-121">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or other configuration source.</span></span> <span data-ttu-id="5f8f3-122">Nazwę źródła używaną w dzienniku zdarzeń można przesłonić, ustawiając właściwość `SourceName` w tych ustawieniach; Jeśli nazwa nie zostanie określona, zostanie użyta domyślna nazwa aplikacji (zazwyczaj nazwa zestawu wykonywalnego).</span><span class="sxs-lookup"><span data-stu-id="5f8f3-122">The source name used in Event Log can be overridden by setting a `SourceName` property in these settings; if you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="5f8f3-123">Więcej informacji na temat rejestrowania znajduje się na końcu tego rozdziału.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-123">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="5f8f3-124">Uruchamianie aplikacji jako usługi systemu Linux z systemem</span><span class="sxs-lookup"><span data-stu-id="5f8f3-124">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="5f8f3-125">Aby skonfigurować aplikację ASP.NET Core tak, aby była uruchamiana jako usługa systemu Linux (lub *demon* w systemie Linux sprzężeniem), zainstaluj pakiet [Microsoft. Extensions. hosting. systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) z narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-125">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="5f8f3-126">Następnie Dodaj wywołanie do `UseSystemd` do metody `CreateHostBuilder` w `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-126">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="5f8f3-127">Jeśli aplikacja nie działa jako usługa systemu Linux, Metoda `UseSystemd` nie wykonuje żadnego działania.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-127">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="5f8f3-128">Teraz Opublikuj aplikację (zależną od platformy lub autonomiczną dla odpowiedniego środowiska uruchomieniowego systemu Linux, np. `linux-x64`), z poziomu programu Visual Studio, klikając prawym przyciskiem myszy projekt i wybierając pozycję *Publikuj* z menu kontekstowego lub z interfejs wiersza polecenia platformy .NET Core przy użyciu poniższego polecenia.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-128">Now publish your application (either framework-dependent, or self-contained for the relevant Linux runtime, e.g. `linux-x64`), either from Visual Studio by right-clicking the project and choosing *Publish* from the context menu, or from the .NET Core CLI using the following command.</span></span>

```console
dotnet publish -c Release -r linux-x64 -o ./publish
```

<span data-ttu-id="5f8f3-129">Skopiuj kompletną zawartość katalogu `publish` do folderu instalacji na hoście z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-129">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="5f8f3-130">Rejestracja usługi wymaga pliku specjalnego o nazwie "plik jednostkowy", który ma zostać dodany do katalogu `/etc/systemd/system`.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-130">Registering the service requires a special file, called a "unit file", to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="5f8f3-131">Musisz mieć uprawnienia główne, aby utworzyć plik w tym folderze.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-131">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="5f8f3-132">Nazwij plik z identyfikatorem, który ma być używany `systemd` i `.service` rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-132">Name the file with the identifier you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="5f8f3-133">Na przykład `/etc/systemd/system/myapp.service`.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-133">For example, `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="5f8f3-134">Plik usługi używa formatu INI, jak pokazano w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-134">The service file uses INI format, as shown in this example.</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="5f8f3-135">Właściwość `Type=notify` informuje `systemd`, że aplikacja będzie powiadamiać ją przy uruchamianiu i zamykaniu.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-135">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="5f8f3-136">Ustawienie `WantedBy=multi-user.target` spowoduje uruchomienie usługi, gdy system Linux osiągnie wartość "runlevel 2", co oznacza, że niegraficzna powłoka z wieloużytkownika jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-136">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2", meaning a non-graphical multi-user shell is active.</span></span>

<span data-ttu-id="5f8f3-137">Aby program `systemd` rozpoznał usługę, musi ponownie załadować jej konfigurację.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-137">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="5f8f3-138">Użytkownik kontroluje `systemd` przy użyciu polecenia `systemctl`.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-138">You control `systemd` using the `systemctl` command.</span></span> <span data-ttu-id="5f8f3-139">Po ponownym załadowaniu Użyj podpolecenia `status`, aby potwierdzić, że aplikacja została pomyślnie zarejestrowana.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-139">After reloading, use the `status` subcommand to confirm the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="5f8f3-140">Jeśli usługa została prawidłowo skonfigurowana, zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="5f8f3-140">If you've configured the service correctly, the following output will be shown:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="5f8f3-141">Użyj polecenia `start`, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-141">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="5f8f3-142">Rozszerzenie `.service` jest opcjonalne w przypadku korzystania z `systemctl start`.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-142">The `.service` extension is optional when using `systemctl start`.</span></span>

<span data-ttu-id="5f8f3-143">Aby poinformować `systemd` o automatycznym uruchomieniu usługi przy uruchamianiu systemu, użyj polecenia `enable`.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-143">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="5f8f3-144">Rejestruj w dzienniku</span><span class="sxs-lookup"><span data-stu-id="5f8f3-144">Log to journald</span></span>

<span data-ttu-id="5f8f3-145">System Linux odpowiadający dziennikowi zdarzeń systemu Windows jest `journald`, usługa systemu rejestrowania strukturalnego, która jest częścią `systemd`.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-145">The Linux equivalent of the Windows Event Log is `journald`, a structured logging system service that is part of `systemd`.</span></span> <span data-ttu-id="5f8f3-146">Komunikaty dziennika zapisywane w standardowym wyniku przez demon systemu Linux są automatycznie zapisywane do `journald`, więc aby skonfigurować poziomy rejestrowania, użyj sekcji `Console` w konfiguracji rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-146">Log messages written to the standard output by a Linux daemon are automatically written to `journald`, so to configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="5f8f3-147">Metoda `UseSystemd` konstruktora hosta automatycznie konfiguruje format danych wyjściowych konsoli w celu dostosowania go do dziennika.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-147">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="5f8f3-148">Ponieważ `journald` jest standardem dla dzienników systemu Linux, istnieje wiele narzędzi, które integrują się z nim i można łatwo kierować dzienniki z `journald` do zewnętrznego systemu rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-148">Because `journald` is the standard for Linux logs, there are a variety of tools that integrate with it, and you can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="5f8f3-149">Pracując lokalnie na hoście, można użyć `journalctl` polecenie, aby wyświetlić dzienniki z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-149">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="5f8f3-150">Jeśli na hoście jest dostępne środowisko graficznego interfejsu użytkownika, w systemie Linux dostępne są kilka graficznych przeglądarek dzienników, takich jak *QJournalctl* i *GNOME*.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-150">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="5f8f3-151">Aby dowiedzieć się więcej o wysyłaniu zapytań do dziennika systemowego z wiersza polecenia z `journalctl`, zobacz [strony man](https://manpages.debian.org/buster/systemd/journalctl.1).</span><span class="sxs-lookup"><span data-stu-id="5f8f3-151">To learn more about querying the systemd journal from the command line with `journalctl`, see [the man pages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="5f8f3-152">Certyfikaty HTTPS dla aplikacji samodzielnych</span><span class="sxs-lookup"><span data-stu-id="5f8f3-152">HTTPS Certificates for self-hosted applications</span></span>

<span data-ttu-id="5f8f3-153">Podczas uruchamiania aplikacji gRPC w środowisku produkcyjnym należy używać certyfikatu TLS z zaufanego urzędu certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="5f8f3-153">When running a gRPC application in production, you should use a TLS certificate from a trusted Certificate Authority (CA).</span></span> <span data-ttu-id="5f8f3-154">Ten urząd certyfikacji może być publicznym urzędem certyfikacji lub wewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-154">This CA could be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="5f8f3-155">Na hostach z systemem Windows certyfikat może zostać załadowany z bezpiecznego [magazynu certyfikatów](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores) przy użyciu [klasy X509Store](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="5f8f3-155">On Windows hosts, the certificate may be loaded from a secure [Certificate Store](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores) using the [X509Store class](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0).</span></span> <span data-ttu-id="5f8f3-156">Klasy `X509Store` można również używać z magazynem kluczy OpenSSL na niektórych hostach z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-156">The `X509Store` class can also be used with the OpenSSL key-store on some Linux hosts.</span></span>

<span data-ttu-id="5f8f3-157">Certyfikaty mogą być również tworzone przy użyciu jednego z [konstruktorów X509Certificate2](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), z pliku (na przykład pliku `.pfx` chronionego za pomocą silnego hasła) lub z danych binarnych pobranych z usługi bezpiecznego magazynu, takich jak [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span><span class="sxs-lookup"><span data-stu-id="5f8f3-157">Certificates may also be created using one of the [X509Certificate2 constructors](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), either from a file (for example a `.pfx` file protected by a strong password), or from binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="5f8f3-158">Kestrel można skonfigurować do korzystania z certyfikatu na dwa sposoby: od konfiguracji lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-158">Kestrel can be configured to use a certificate in two ways: from configuration, or in code.</span></span>

### <a name="set-https-certificates-using-configuration"></a><span data-ttu-id="5f8f3-159">Ustawianie certyfikatów HTTPS przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5f8f3-159">Set HTTPS certificates using configuration</span></span>

<span data-ttu-id="5f8f3-160">Podejście konfiguracyjne wymaga ustawienia ścieżki do pliku `.pfx` certyfikatu i hasła w sekcji konfiguracji Kestrel.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-160">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="5f8f3-161">W `appsettings.json`, który będzie wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-161">In `appsettings.json` that would look like this.</span></span>

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

<span data-ttu-id="5f8f3-162">Hasło należy zapewnić przy użyciu bezpiecznego źródła konfiguracji, takiego jak Magazyn kluczy platformy Azure lub magazyn Hashicorp.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-162">The password should be provided using a secure configuration source such as Azure KeyVault or Hashicorp Vault.</span></span>

<span data-ttu-id="5f8f3-163">NIE należy przechowywać nieszyfrowanych haseł w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-163">You SHOULD NOT store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="5f8f3-164">Ustawianie certyfikatów HTTPS w kodzie</span><span class="sxs-lookup"><span data-stu-id="5f8f3-164">Set HTTPS certificates in code</span></span>

<span data-ttu-id="5f8f3-165">Aby skonfigurować protokół HTTPS na Kestrel w kodzie, należy użyć metody `ConfigureKestrel` na `IWebHostBuilder` w klasie `Program`.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-165">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="5f8f3-166">Ponownie hasło do pliku `.pfx` powinno być przechowywane w i pobierane z bezpiecznego źródła konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5f8f3-166">Again, the password for the `.pfx` file should be stored in and retrieved from a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5f8f3-167">[Poprzedni](grpc-in-production.md)
>[Następny](docker.md)</span><span class="sxs-lookup"><span data-stu-id="5f8f3-167">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
