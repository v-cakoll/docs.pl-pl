---
title: Własne hostowane aplikacje gRPC — gRPC dla deweloperów WCF
description: Wdrażanie aplikacji ASP.NET Core gRPC jako usług samoobsługowych.
ms.date: 09/02/2019
ms.openlocfilehash: 2244f161ad4b5d60138ae0f7b4d6a9c8c8829aa8
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503401"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="835bc-103">Własne hostowane aplikacje gRPC</span><span class="sxs-lookup"><span data-stu-id="835bc-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="835bc-104">Chociaż aplikacje ASP.NET Core 3,0 mogą być hostowane w usługach IIS w systemie Windows Server, obecnie nie jest możliwe hostowanie aplikacji gRPC w usługach IIS, ponieważ niektóre funkcje protokołu HTTP/2 nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="835bc-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="835bc-105">Ta funkcja jest celem przyszłej aktualizacji systemu Windows Server.</span><span class="sxs-lookup"><span data-stu-id="835bc-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="835bc-106">Aplikację można uruchomić jako usługę systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="835bc-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="835bc-107">Można też uruchomić ją jako usługę systemu Linux sterowaną przez [system](https://en.wikipedia.org/wiki/Systemd), ze względu na nowe funkcje w rozszerzeniach hostingu platformy .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="835bc-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="835bc-108">Uruchamianie aplikacji jako usługi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="835bc-108">Run your app as a Windows service</span></span>

<span data-ttu-id="835bc-109">Aby skonfigurować aplikację ASP.NET Core tak, aby była uruchamiana jako usługa systemu Windows, zainstaluj pakiet [Microsoft. Extensions. hosting. WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) z narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="835bc-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="835bc-110">Następnie Dodaj wywołanie do `UseWindowsService` do metody `CreateHostBuilder` w `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="835bc-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="835bc-111">Jeśli aplikacja nie działa jako usługa systemu Windows, Metoda `UseWindowsService` nie wykonuje żadnego działania.</span><span class="sxs-lookup"><span data-stu-id="835bc-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="835bc-112">Teraz Opublikuj swoją aplikację za pomocą jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="835bc-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="835bc-113">W programie Visual Studio, klikając prawym przyciskiem myszy projekt, a następnie wybierając pozycję **Publikuj** w menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="835bc-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="835bc-114">Z interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="835bc-114">From the .NET Core CLI.</span></span>

<span data-ttu-id="835bc-115">Podczas publikowania aplikacji .NET Core można utworzyć wdrożenie *zależne od platformy* lub wdrożenie *samodzielne* .</span><span class="sxs-lookup"><span data-stu-id="835bc-115">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="835bc-116">Wdrożenia zależne od platformy wymagają zainstalowania wspólnego środowiska uruchomieniowego platformy .NET Core na hoście, na którym są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="835bc-116">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="835bc-117">Wstępnie zawarte wdrożenia są publikowane z pełną kopią środowiska uruchomieniowego i platformy .NET Core i mogą być uruchamiane na dowolnym hoście.</span><span class="sxs-lookup"><span data-stu-id="835bc-117">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="835bc-118">Aby uzyskać więcej informacji, w tym zalety i wady każdego podejścia, zapoznaj się z dokumentacją dotyczącą [wdrażania aplikacji .NET Core](../../core/deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="835bc-118">For more information, including the advantages and disadvantages of each approach, see the [.NET Core application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="835bc-119">Aby opublikować samodzielną kompilację aplikacji, która nie wymaga zainstalowania środowiska uruchomieniowego programu .NET Core 3,0 na hoście, określ środowisko uruchomieniowe, które ma zostać dołączone do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="835bc-119">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="835bc-120">Użyj flagi `-r` (lub `--runtime`).</span><span class="sxs-lookup"><span data-stu-id="835bc-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="835bc-121">Aby opublikować kompilację zależną od platformy, Pomiń flagę `-r`.</span><span class="sxs-lookup"><span data-stu-id="835bc-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="835bc-122">Skopiuj kompletną zawartość katalogu `publish` do folderu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="835bc-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="835bc-123">Następnie użyj [narzędzia SC](/windows/desktop/services/controlling-a-service-using-sc) , aby utworzyć usługę systemu Windows dla pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="835bc-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="835bc-124">Rejestruj w dzienniku zdarzeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="835bc-124">Log to the Windows event log</span></span>

<span data-ttu-id="835bc-125">Metoda `UseWindowsService` automatycznie dodaje dostawcę [rejestrowania](/aspnet/core/fundamentals/logging/) , który zapisuje komunikaty dziennika w dzienniku zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="835bc-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="835bc-126">Można skonfigurować rejestrowanie dla tego dostawcy, dodając wpis `EventLog` do sekcji `Logging` `appsettings.json` lub innego źródła konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="835bc-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span> 

<span data-ttu-id="835bc-127">Można zastąpić nazwę źródła używaną w dzienniku zdarzeń, ustawiając właściwość `SourceName` w tych ustawieniach.</span><span class="sxs-lookup"><span data-stu-id="835bc-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="835bc-128">Jeśli nazwa nie zostanie określona, zostanie użyta domyślna nazwa aplikacji (zazwyczaj nazwa zestawu wykonywalnego).</span><span class="sxs-lookup"><span data-stu-id="835bc-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="835bc-129">Więcej informacji na temat rejestrowania znajduje się na końcu tego rozdziału.</span><span class="sxs-lookup"><span data-stu-id="835bc-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="835bc-130">Uruchamianie aplikacji jako usługi systemu Linux z systemem</span><span class="sxs-lookup"><span data-stu-id="835bc-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="835bc-131">Aby skonfigurować aplikację ASP.NET Core tak, aby była uruchamiana jako usługa systemu Linux (lub *demon* w systemie Linux sprzężeniem), zainstaluj pakiet [Microsoft. Extensions. hosting. systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) z narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="835bc-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="835bc-132">Następnie Dodaj wywołanie do `UseSystemd` do metody `CreateHostBuilder` w `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="835bc-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="835bc-133">Jeśli aplikacja nie działa jako usługa systemu Linux, Metoda `UseSystemd` nie wykonuje żadnego działania.</span><span class="sxs-lookup"><span data-stu-id="835bc-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="835bc-134">Teraz Opublikuj aplikację.</span><span class="sxs-lookup"><span data-stu-id="835bc-134">Now publish your application.</span></span> <span data-ttu-id="835bc-135">Aplikacja może być zależna od platformy lub samodzielna dla odpowiedniego środowiska uruchomieniowego systemu Linux (na przykład `linux-x64`).</span><span class="sxs-lookup"><span data-stu-id="835bc-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="835bc-136">Można opublikować za pomocą jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="835bc-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="835bc-137">W programie Visual Studio, klikając prawym przyciskiem myszy projekt, a następnie wybierając pozycję **Publikuj** w menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="835bc-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span> 
* <span data-ttu-id="835bc-138">W interfejs wiersza polecenia platformy .NET Core przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="835bc-138">From the .NET Core CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
<span data-ttu-id="835bc-139">Skopiuj kompletną zawartość katalogu `publish` do folderu instalacji na hoście z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="835bc-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="835bc-140">Rejestracja usługi wymaga pliku specjalnego o nazwie *Unit*, który ma zostać dodany do katalogu `/etc/systemd/system`.</span><span class="sxs-lookup"><span data-stu-id="835bc-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="835bc-141">Musisz mieć uprawnienia główne, aby utworzyć plik w tym folderze.</span><span class="sxs-lookup"><span data-stu-id="835bc-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="835bc-142">Nazwij plik z identyfikatorem, który ma być używany `systemd` i `.service` rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="835bc-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="835bc-143">Użyj na przykład nazwy `/etc/systemd/system/myapp.service`.</span><span class="sxs-lookup"><span data-stu-id="835bc-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="835bc-144">Plik usługi używa formatu INI, jak pokazano w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="835bc-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="835bc-145">Właściwość `Type=notify` informuje `systemd`, że aplikacja będzie powiadamiać ją przy uruchamianiu i zamykaniu.</span><span class="sxs-lookup"><span data-stu-id="835bc-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="835bc-146">Ustawienie `WantedBy=multi-user.target` spowoduje uruchomienie usługi, gdy system Linux osiągnie wartość "runlevel 2", co oznacza, że powłoka wiele użytkowników nie jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="835bc-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical multi-user shell is active.</span></span>

<span data-ttu-id="835bc-147">Aby program `systemd` rozpoznał usługę, musi ponownie załadować jej konfigurację.</span><span class="sxs-lookup"><span data-stu-id="835bc-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="835bc-148">`systemd` można kontrolować za pomocą polecenia `systemctl`.</span><span class="sxs-lookup"><span data-stu-id="835bc-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="835bc-149">Po ponownym załadowaniu Użyj podpolecenia `status`, aby upewnić się, że aplikacja została pomyślnie zarejestrowana.</span><span class="sxs-lookup"><span data-stu-id="835bc-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="835bc-150">Jeśli usługa została prawidłowo skonfigurowana, uzyskasz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="835bc-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="835bc-151">Użyj polecenia `start`, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="835bc-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="835bc-152">Rozszerzenie `.service` jest opcjonalne w przypadku korzystania z `systemctl start`.</span><span class="sxs-lookup"><span data-stu-id="835bc-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="835bc-153">Aby poinformować `systemd` o automatycznym uruchomieniu usługi przy uruchamianiu systemu, użyj polecenia `enable`.</span><span class="sxs-lookup"><span data-stu-id="835bc-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="835bc-154">Rejestruj w dzienniku</span><span class="sxs-lookup"><span data-stu-id="835bc-154">Log to journald</span></span>

<span data-ttu-id="835bc-155">System Linux odpowiadający dziennikowi zdarzeń systemu Windows jest `journald`, usługa systemu rejestrowania strukturalnego, która jest częścią `systemd`.</span><span class="sxs-lookup"><span data-stu-id="835bc-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="835bc-156">Komunikaty dziennika zapisywane w standardowym wyniku przez demon systemu Linux są automatycznie zapisywane w `journald`.</span><span class="sxs-lookup"><span data-stu-id="835bc-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="835bc-157">Aby skonfigurować poziomy rejestrowania, użyj sekcji `Console` konfiguracji rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="835bc-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="835bc-158">Metoda `UseSystemd` konstruktora hosta automatycznie konfiguruje format danych wyjściowych konsoli w celu dostosowania go do dziennika.</span><span class="sxs-lookup"><span data-stu-id="835bc-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="835bc-159">Ponieważ `journald` jest standardem dla dzienników systemu Linux, wiele narzędzi integruje się z nim.</span><span class="sxs-lookup"><span data-stu-id="835bc-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="835bc-160">Dzienniki można łatwo kierować z `journald` do zewnętrznego systemu rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="835bc-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="835bc-161">Pracując lokalnie na hoście, można użyć `journalctl` polecenie, aby wyświetlić dzienniki z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="835bc-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="835bc-162">Jeśli na hoście jest dostępne środowisko graficznego interfejsu użytkownika, w systemie Linux dostępne są kilka graficznych przeglądarek dzienników, takich jak *QJournalctl* i *GNOME*.</span><span class="sxs-lookup"><span data-stu-id="835bc-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="835bc-163">Aby dowiedzieć się więcej o wysyłaniu zapytań do dziennika `systemd` z wiersza polecenia przy użyciu `journalctl`, zobacz [strony man](https://manpages.debian.org/buster/systemd/journalctl.1).</span><span class="sxs-lookup"><span data-stu-id="835bc-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the man pages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="835bc-164">Certyfikaty HTTPS dla aplikacji samodzielnych</span><span class="sxs-lookup"><span data-stu-id="835bc-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="835bc-165">Gdy uruchamiasz aplikację gRPC w środowisku produkcyjnym, należy używać certyfikatu TLS z zaufanego urzędu certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="835bc-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="835bc-166">Ten urząd certyfikacji może być publicznym urzędem certyfikacji lub wewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="835bc-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="835bc-167">Na hostach z systemem Windows można załadować certyfikat z bezpiecznego [magazynu certyfikatów](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) przy użyciu klasy <xref:System.Security.Cryptography.X509Certificates.X509Store>.</span><span class="sxs-lookup"><span data-stu-id="835bc-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="835bc-168">Klasy `X509Store` można również użyć z magazynem kluczy OpenSSL na niektórych hostach z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="835bc-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="835bc-169">Można również tworzyć certyfikaty przy użyciu jednego z [konstruktorów X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A):</span><span class="sxs-lookup"><span data-stu-id="835bc-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="835bc-170">Plik, taki jak plik `.pfx` chroniony za pomocą silnego hasła</span><span class="sxs-lookup"><span data-stu-id="835bc-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="835bc-171">Dane binarne pobrane z usługi bezpiecznego magazynu, takie jak [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span><span class="sxs-lookup"><span data-stu-id="835bc-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="835bc-172">Kestrel można skonfigurować tak, aby używał certyfikatu na dwa sposoby: od konfiguracji lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="835bc-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="835bc-173">Ustawianie certyfikatów HTTPS przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="835bc-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="835bc-174">Podejście konfiguracyjne wymaga ustawienia ścieżki do pliku `.pfx` certyfikatu i hasła w sekcji konfiguracji Kestrel.</span><span class="sxs-lookup"><span data-stu-id="835bc-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="835bc-175">W `appsettings.json`, który będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="835bc-175">In `appsettings.json`, that would look like this:</span></span>

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

<span data-ttu-id="835bc-176">Podaj hasło przy użyciu bezpiecznego źródła konfiguracji, takiego jak Azure Key Vault lub magazyn Hashicorp.</span><span class="sxs-lookup"><span data-stu-id="835bc-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="835bc-177">Nie przechowuj nieszyfrowanych haseł w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="835bc-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="835bc-178">Ustawianie certyfikatów HTTPS w kodzie</span><span class="sxs-lookup"><span data-stu-id="835bc-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="835bc-179">Aby skonfigurować protokół HTTPS na Kestrel w kodzie, należy użyć metody `ConfigureKestrel` na `IWebHostBuilder` w klasie `Program`.</span><span class="sxs-lookup"><span data-stu-id="835bc-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="835bc-180">Ponownie Zapisz hasło do pliku `.pfx` w programie, a następnie pobierz go ze źródła konfiguracji bezpiecznego.</span><span class="sxs-lookup"><span data-stu-id="835bc-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="835bc-181">[Poprzednie](grpc-in-production.md)
>[dalej](docker.md)</span><span class="sxs-lookup"><span data-stu-id="835bc-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
