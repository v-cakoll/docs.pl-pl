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
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="5a8f0-103">Aplikacje gRPC hostowane samodzielnie</span><span class="sxs-lookup"><span data-stu-id="5a8f0-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="5a8f0-104">Chociaż ASP.NET aplikacje Core 3.0 mogą być hostowane w usługach IIS w systemie Windows Server, obecnie nie jest możliwe hosta aplikacji gRPC w usługach IIS, ponieważ niektóre funkcje HTTP/2 nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="5a8f0-105">Ta funkcja jest celem przyszłej aktualizacji systemu Windows Server.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="5a8f0-106">Aplikację można uruchomić jako usługę systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="5a8f0-107">Lub można go uruchomić jako usługę Linux kontrolowane przez [systemd](https://en.wikipedia.org/wiki/Systemd), ze względu na nowe funkcje w .NET Core 3.0 hosting rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="5a8f0-108">Uruchamianie aplikacji jako usługi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5a8f0-108">Run your app as a Windows service</span></span>

<span data-ttu-id="5a8f0-109">Aby skonfigurować aplikację ASP.NET Core do uruchamiania jako usługa systemu Windows, zainstaluj pakiet [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) z NuGet.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="5a8f0-110">Następnie dodaj wywołanie `UseWindowsService` `CreateHostBuilder` do `Program.cs`metody w pliku .</span><span class="sxs-lookup"><span data-stu-id="5a8f0-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="5a8f0-111">Jeśli aplikacja nie jest uruchomiona jako `UseWindowsService` usługa systemu Windows, metoda nic nie robi.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="5a8f0-112">Teraz opublikuj aplikację przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="5a8f0-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="5a8f0-113">W programie Visual Studio kliknij prawym przyciskiem myszy projekt i wybierając polecenie **Publikuj** w menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="5a8f0-114">Z .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-114">From the .NET Core CLI.</span></span>

<span data-ttu-id="5a8f0-115">Podczas publikowania aplikacji .NET Core można utworzyć wdrożenie *zależne od struktury* lub wdrożenie *niezależne.*</span><span class="sxs-lookup"><span data-stu-id="5a8f0-115">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="5a8f0-116">Wdrożenia zależne od struktury wymagają zainstalowania udostępnionego serwera .NET Core na hoście, na którym są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-116">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="5a8f0-117">Niezależne wdrożenia są publikowane z pełną kopią programu runtime i struktury programu .NET Core i można je uruchamiać na dowolnym hoście.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-117">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="5a8f0-118">Aby uzyskać więcej informacji, w tym zalety i wady każdego podejścia, zobacz .NET Core dokumentacji [wdrażania aplikacji.](../../core/deploying/index.md)</span><span class="sxs-lookup"><span data-stu-id="5a8f0-118">For more information, including the advantages and disadvantages of each approach, see the [.NET Core application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="5a8f0-119">Aby opublikować niezależną kompilację aplikacji, która nie wymaga zainstalowania programu .NET Core 3.0 na hoście, należy określić czas uruchomieniowy, który ma zostać dołączony do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-119">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="5a8f0-120">Użyj `-r` flagi `--runtime`(lub ) .</span><span class="sxs-lookup"><span data-stu-id="5a8f0-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="5a8f0-121">Aby opublikować kompilacji zależnej `-r` od struktury, pominąć flagę.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="5a8f0-122">Skopiuj pełną `publish` zawartość katalogu do folderu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="5a8f0-123">Następnie użyj [narzędzia sc,](/windows/desktop/services/controlling-a-service-using-sc) aby utworzyć usługę systemu Windows dla pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="5a8f0-124">Rejestrowanie w dzienniku zdarzeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5a8f0-124">Log to the Windows event log</span></span>

<span data-ttu-id="5a8f0-125">Metoda `UseWindowsService` automatycznie dodaje dostawcę [rejestrowania,](/aspnet/core/fundamentals/logging/) który zapisuje komunikaty dziennika do dziennika zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="5a8f0-126">Rejestrowanie dla tego dostawcy można `EventLog` skonfigurować, `Logging` dodając `appsettings.json` wpis do sekcji lub innego źródła konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span>

<span data-ttu-id="5a8f0-127">Można zastąpić nazwę źródłową używaną w dzienniku zdarzeń, ustawiając `SourceName` właściwość w tych ustawieniach.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="5a8f0-128">Jeśli nie określisz nazwy, zostanie użyta domyślna nazwa aplikacji (zwykle nazwa zestawu wykonywalnego).</span><span class="sxs-lookup"><span data-stu-id="5a8f0-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="5a8f0-129">Więcej informacji na temat rejestrowania znajduje się na końcu tego rozdziału.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="5a8f0-130">Uruchom aplikację jako usługę Linux z systememd</span><span class="sxs-lookup"><span data-stu-id="5a8f0-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="5a8f0-131">Aby skonfigurować aplikację ASP.NET Core do uruchamiania jako usługa Systemu Linux (lub *daemon* w żargonie systemu Linux), zainstaluj pakiet [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) z NuGet.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="5a8f0-132">Następnie dodaj wywołanie `UseSystemd` `CreateHostBuilder` do `Program.cs`metody w pliku .</span><span class="sxs-lookup"><span data-stu-id="5a8f0-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="5a8f0-133">Jeśli aplikacja nie jest uruchomiona jako `UseSystemd` usługa Systemu Linux, metoda nic nie robi.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="5a8f0-134">Teraz opublikuj aplikację.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-134">Now publish your application.</span></span> <span data-ttu-id="5a8f0-135">Aplikacja może być zależna od struktury lub niezależna dla odpowiedniego uruchomienia `linux-x64`systemu Linux (na przykład).</span><span class="sxs-lookup"><span data-stu-id="5a8f0-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="5a8f0-136">Można opublikować przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="5a8f0-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="5a8f0-137">W programie Visual Studio kliknij prawym przyciskiem myszy projekt i wybierając polecenie **Publikuj** w menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="5a8f0-138">Z polecenia CLI .NET Core przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="5a8f0-138">From the .NET Core CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
<span data-ttu-id="5a8f0-139">Skopiuj pełną `publish` zawartość katalogu do folderu instalacyjnego na hoście systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="5a8f0-140">Rejestracja usługi wymaga specjalnego pliku, zwanego *plikiem jednostki,* który ma zostać dodany do `/etc/systemd/system` katalogu.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="5a8f0-141">Do utworzenia pliku w tym folderze potrzebne jest uprawnienie administratora.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="5a8f0-142">Nazwij plik identyfikatorem, `systemd` którego chcesz `.service` użyć, i rozszerzeniem.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="5a8f0-143">Użyj na przykład nazwy `/etc/systemd/system/myapp.service`.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="5a8f0-144">Plik usługi używa formatu INI, jak pokazano w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5a8f0-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="5a8f0-145">Właściwość `Type=notify` informuje, `systemd` że aplikacja powiadomi go podczas uruchamiania i zamykania.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="5a8f0-146">Ustawienie `WantedBy=multi-user.target` spowoduje uruchomienie usługi, gdy system Linux osiągnie "poziom uruchamiania 2", co oznacza, że niegraficzna powłoka dla wielu użytkowników jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical multi-user shell is active.</span></span>

<span data-ttu-id="5a8f0-147">Zanim `systemd` rozpozna usługę, musi ponownie załadować jej konfigurację.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="5a8f0-148">Kontroluj `systemd` za `systemctl` pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="5a8f0-149">Po ponownym załadowaniu `status` użyj podpolecenia, aby potwierdzić, że aplikacja została pomyślnie zarejestrowana.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="5a8f0-150">Jeśli usługa została poprawnie skonfigurowana, otrzymasz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="5a8f0-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="5a8f0-151">Użyj `start` polecenia, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="5a8f0-152">Rozszerzenie `.service` jest opcjonalne, gdy `systemctl start`używasz .</span><span class="sxs-lookup"><span data-stu-id="5a8f0-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="5a8f0-153">Aby `systemd` poinformować, aby uruchomić usługę automatycznie `enable` podczas uruchamiania systemu, użyj polecenia.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="5a8f0-154">Rejestrowanie do dziennika</span><span class="sxs-lookup"><span data-stu-id="5a8f0-154">Log to journald</span></span>

<span data-ttu-id="5a8f0-155">Linux odpowiednik dziennika zdarzeń `journald`systemu Windows jest , ustrukturyzowanej usługi systemu rejestrowania, który jest częścią `systemd`.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="5a8f0-156">Wiadomości dziennika zapisane do standardowego wyjścia przez daemon `journald`Linux są automatycznie zapisywane do .</span><span class="sxs-lookup"><span data-stu-id="5a8f0-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="5a8f0-157">Aby skonfigurować poziomy rejestrowania, należy użyć `Console` sekcji konfiguracji rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="5a8f0-158">Metoda `UseSystemd` konstruktora hostów automatycznie konfiguruje format wyjściowy konsoli do obsługi arkusza.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="5a8f0-159">Ponieważ `journald` jest to standard dla dzienników Linuksa, różne narzędzia integrują się z nim.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="5a8f0-160">Dzienniki można łatwo `journald` kierować z ewnętrznego systemu rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="5a8f0-161">Pracując lokalnie na hoście, `journalctl` można użyć polecenia do wyświetlania dzienników z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="5a8f0-162">Jeśli masz środowisko graficzne dostępne na hoście, dla systemu Linux dostępnych jest kilka graficznych dzienników, takich jak *QJournalctl* i *gnome-logi.*</span><span class="sxs-lookup"><span data-stu-id="5a8f0-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="5a8f0-163">Aby dowiedzieć się więcej `systemd` o śledzeniu `journalctl`dziennika z wiersza polecenia za pomocą , zobacz [strony osoby .](https://manpages.debian.org/buster/systemd/journalctl.1)</span><span class="sxs-lookup"><span data-stu-id="5a8f0-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the man pages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="5a8f0-164">Certyfikaty HTTPS dla aplikacji hostowanych samodzielnie</span><span class="sxs-lookup"><span data-stu-id="5a8f0-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="5a8f0-165">Podczas uruchamiania aplikacji gRPC w środowisku produkcyjnym należy użyć certyfikatu TLS z zaufanego urzędu certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="5a8f0-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="5a8f0-166">Ten urząd certyfikacji może być publicznym urządem certyfikacji lub wewnętrznym urządem certyfikacji organizacji.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="5a8f0-167">Na hostach systemu Windows certyfikat można załadować z <xref:System.Security.Cryptography.X509Certificates.X509Store> bezpiecznego [magazynu certyfikatów](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) przy użyciu tej klasy.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="5a8f0-168">Można również użyć `X509Store` klasy z magazynu kluczy OpenSSL na niektórych hostach systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="5a8f0-169">Certyfikaty można również tworzyć przy użyciu jednego z [konstruktorów X509Certificate2,](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)z jednego z:</span><span class="sxs-lookup"><span data-stu-id="5a8f0-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="5a8f0-170">Plik, taki jak `.pfx` plik chroniony silnym hasłem</span><span class="sxs-lookup"><span data-stu-id="5a8f0-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="5a8f0-171">Dane binarne pobrane z bezpiecznej usługi magazynu, takiej jak [Usługa Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span><span class="sxs-lookup"><span data-stu-id="5a8f0-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="5a8f0-172">Kestrel można skonfigurować tak, aby używał certyfikatu na dwa sposoby: od konfiguracji lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="5a8f0-173">Ustawianie certyfikatów HTTPS przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5a8f0-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="5a8f0-174">Podejście konfiguracyjne wymaga ustawienia `.pfx` ścieżki do pliku certyfikatu i hasła w sekcji konfiguracji kestrel.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="5a8f0-175">W `appsettings.json`, że będzie wyglądać tak:</span><span class="sxs-lookup"><span data-stu-id="5a8f0-175">In `appsettings.json`, that would look like this:</span></span>

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

<span data-ttu-id="5a8f0-176">Podaj hasło przy użyciu bezpiecznego źródła konfiguracji, takiego jak Usługa Azure Key Vault lub Hashicorp Vault.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a8f0-177">Nie przechowuj niezaszyfrowanych haseł w plikach konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="5a8f0-178">Ustawianie certyfikatów HTTPS w kodzie</span><span class="sxs-lookup"><span data-stu-id="5a8f0-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="5a8f0-179">Aby skonfigurować protokół HTTPS na kestrel `IWebHostBuilder` w `Program` kodzie, należy użyć `ConfigureKestrel` metody w klasie.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="5a8f0-180">Ponownie pamiętaj, aby zapisać hasło `.pfx` do pliku i pobrać go z bezpiecznego źródła konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5a8f0-181">[Poprzedni](grpc-in-production.md)
>[następny](docker.md)</span><span class="sxs-lookup"><span data-stu-id="5a8f0-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
