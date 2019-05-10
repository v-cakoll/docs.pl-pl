---
title: Jak zainstalować narzędzie strukturze ML.NET interfejsu wiersza polecenia (CLI)
description: Omówienie i instalacja narzędzia strukturze ML.NET interfejsu wiersza polecenia (CLI).
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 869c443d519557c9d3976676047e63a4a072d2d3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066236"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="10db9-103">Jak zainstalować narzędzie strukturze ML.NET interfejsu wiersza polecenia (CLI)</span><span class="sxs-lookup"><span data-stu-id="10db9-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="10db9-104">Strukturze ML.NET interfejsu wiersza polecenia (interfejsu wiersza polecenia) jest narzędziem, które można uruchomić na dowolnym wiersza polecenia (Windows, Mac lub Linux) generowania modeli strukturze ML.NET dobrej jakości i kodu źródłowego, w oparciu o zestawów danych szkoleniowych, których udzielasz.</span><span class="sxs-lookup"><span data-stu-id="10db9-104">The ML.NET CLI (command-line interface) is a tool you can run on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on training datasets you provide.</span></span>

> [!NOTE]
> <span data-ttu-id="10db9-105">W tym temacie odnosi się do interfejsu wiersza polecenia w strukturze ML.NET i strukturze ML.NET AutoML, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="10db9-105">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="10db9-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="10db9-106">Pre-requisites</span></span>

- [<span data-ttu-id="10db9-107">.NET core SDK 2,2</span><span class="sxs-lookup"><span data-stu-id="10db9-107">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="10db9-108">(Opcjonalnie) [Visual Studio 2017 lub 2019 r](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="10db9-108">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="10db9-109">Aplikację możesz uruchomić wygenerowany C# projekty z Visual Studio F5 lub kodu `dotnet run` (.NET Core interfejsu wiersza polecenia).</span><span class="sxs-lookup"><span data-stu-id="10db9-109">You can either run the generated C# code projects with Visual Studio F5 or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="10db9-110">Uwaga: Jeśli po zainstalowaniu [zestawu .NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` polecenie nie działa, wyloguj się z Windows i zalogować się ponownie.</span><span class="sxs-lookup"><span data-stu-id="10db9-110">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="10db9-111">Zainstaluj</span><span class="sxs-lookup"><span data-stu-id="10db9-111">Install</span></span>

<span data-ttu-id="10db9-112">Interfejs wiersza polecenia strukturze ML.NET zainstalowano podobnie jak wszystkie inne polecenia dotnet narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="10db9-112">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="10db9-113">Możesz użyć `dotnet tool install` polecenia interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10db9-113">You use the `dotnet tool install` .NET Core CLI command.</span></span> 

<span data-ttu-id="10db9-114">Poniższy przykład pokazuje, jak do zainstalowania interfejsu wiersza polecenia strukturze ML.NET w domyślnym, który NuGet kanału informacyjnego lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="10db9-114">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```console
> dotnet tool install -g mlnet
```

<span data-ttu-id="10db9-115">Jeśli nie można zainstalować narzędzia, (to znaczy, jeśli nie jest dostępny na domyślne, które NuGet źródła danych), zostaną wyświetlone komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="10db9-115">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="10db9-116">Sprawdź, że źródła danych, które miały są sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="10db9-116">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="10db9-117">Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat przedstawiający polecenia używane do wywoływania narzędzia i wersją zainstalowaną, podobny do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="10db9-117">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="10db9-118">Można potwierdzić, że instalacja zakończyła się pomyślnie, wpisując następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="10db9-118">You can confirm the installation was successful by typing the following command:</span></span>

```console
> mlnet
```

<span data-ttu-id="10db9-119">Pomoc dla dostępnych poleceń dla narzędzia mlnet, takie jak polecenie "auto-train" powinien być widoczny.</span><span class="sxs-lookup"><span data-stu-id="10db9-119">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="10db9-120">Instalowanie określonej wersji</span><span class="sxs-lookup"><span data-stu-id="10db9-120">Install a specific release version</span></span>

<span data-ttu-id="10db9-121">Jeśli próbujesz zainstalować wersję wstępną lub określoną wersję narzędzia, można określić numeru wersji w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="10db9-121">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```console
> dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="10db9-122">Możesz również sprawdzić, jeśli pakiet jest prawidłowo zainstalowany, wpisując następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="10db9-122">You can also check if the package is properly installed by typing the following command:</span></span>

```console
> dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="10db9-123">Odinstaluj pakiet interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="10db9-123">Uninstall the CLI package</span></span>

<span data-ttu-id="10db9-124">Wpisz następujące polecenie, aby odinstalować pakiet z komputera lokalnego:</span><span class="sxs-lookup"><span data-stu-id="10db9-124">Type the following command to uninstall the package from your local machine:</span></span>

```console
> dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="10db9-125">Aktualizuj pakiet interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="10db9-125">Update the CLI package</span></span>

<span data-ttu-id="10db9-126">Wpisz następujące polecenie, aby zaktualizować pakiet z komputera lokalnego:</span><span class="sxs-lookup"><span data-stu-id="10db9-126">Type the following command to update the package from your local machine:</span></span>

```console
> dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="10db9-127">Konfigurowanie interfejsu wiersza polecenia sugestie (oparte na karcie automatycznego uzupełniania)</span><span class="sxs-lookup"><span data-stu-id="10db9-127">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="10db9-128">Interfejs wiersza polecenia strukturze ML.NET jest tworzony na podstawie `System.CommandLine`, ma wbudowaną obsługę uzupełniania po naciśnięciu tabulatora.</span><span class="sxs-lookup"><span data-stu-id="10db9-128">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="10db9-129">Przykład sposobu działania uzupełniania po naciśnięciu tabulatora automatycznie jest pokazana w animacji następujące:</span><span class="sxs-lookup"><span data-stu-id="10db9-129">An example of how tab auto completion works is shown in the following animation:</span></span>

![obraz](./media/cli-tab-completion.gif)

<span data-ttu-id="10db9-131">"Oparte na karcie automatycznego uzupełniania" (parametr sugestie) działa na *programu Windows PowerShell* i *bash systemu macOS/Linux* , ale nie będzie działać na *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="10db9-131">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="10db9-132">Aby ją włączyć, w bieżącej wersji zapoznawczej, użytkownik końcowy musi wykonać kilka czynności, raz na shell w opisany poniżej.</span><span class="sxs-lookup"><span data-stu-id="10db9-132">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="10db9-133">Po zakończeniu tej operacji uzupełnienia będzie działać dla wszystkich aplikacji napisanych z użyciem `System.CommandLine` takich jak strukturze ML.NET interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="10db9-133">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="10db9-134">Na komputerze, na którym chcesz włączyć uzupełnianie należy wykonać dwie czynności.</span><span class="sxs-lookup"><span data-stu-id="10db9-134">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="10db9-135">Zainstaluj `dotnet-suggest` narzędzie globalne, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="10db9-135">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```console
    > dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="10db9-136">Dodaj skrypt podkładki odpowiednie do swojego profilu powłoki.</span><span class="sxs-lookup"><span data-stu-id="10db9-136">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="10db9-137">Użytkownik może być konieczne utworzenie pliku profilu powłoki.</span><span class="sxs-lookup"><span data-stu-id="10db9-137">You may have to create a shell profile file.</span></span> <span data-ttu-id="10db9-138">Skrypt podkładki przekaże żądania zakończenia z powłoki do `dotnet-suggest` narzędzia, który deleguje do odpowiedniego `System.CommandLine`— na podstawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="10db9-138">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    * <span data-ttu-id="10db9-139">W przypadku powłoki bash, należy dodać zawartość [dotnet zasugerować shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) do `~/.bash_profile`.</span><span class="sxs-lookup"><span data-stu-id="10db9-139">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    * <span data-ttu-id="10db9-140">W przypadku programu PowerShell, należy dodać zawartość [dotnet zasugerować shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) do Twojego profilu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="10db9-140">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="10db9-141">Oczekiwaną ścieżką do Twojego profilu programu PowerShell można znaleźć, uruchamiając następujące polecenie w konsoli:</span><span class="sxs-lookup"><span data-stu-id="10db9-141">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    > echo $profile
    ``` 

<span data-ttu-id="10db9-142">(Dla innych powłoki [poszukaj](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) lub Otwórz [problem](https://github.com/dotnet/System.CommandLine/issues).)</span><span class="sxs-lookup"><span data-stu-id="10db9-142">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="10db9-143">Katalog instalacyjny</span><span class="sxs-lookup"><span data-stu-id="10db9-143">Installation directory</span></span>

<span data-ttu-id="10db9-144">Strukturze ML.NET interfejsu wiersza polecenia można zainstalować w domyślnym katalogu lub w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="10db9-144">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="10db9-145">Domyślne katalogi są następujące:</span><span class="sxs-lookup"><span data-stu-id="10db9-145">The default directories are:</span></span>

| <span data-ttu-id="10db9-146">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="10db9-146">OS</span></span>          | <span data-ttu-id="10db9-147">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="10db9-147">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="10db9-148">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="10db9-148">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="10db9-149">Windows</span><span class="sxs-lookup"><span data-stu-id="10db9-149">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="10db9-150">Te lokalizacje są dodawane do ścieżki użytkownika podczas pierwszego uruchomienia zestaw SDK, więc globalnego narzędzia są zainstalowane, może być wywoływana bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="10db9-150">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="10db9-151">Uwaga: narzędzia globalne są specyficzne dla użytkownika, nie machine globalnego.</span><span class="sxs-lookup"><span data-stu-id="10db9-151">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="10db9-152">Są specyficzne dla użytkownika oznacza, że nie można zainstalować narzędzie globalne, która jest dostępna dla wszystkich użytkowników komputera.</span><span class="sxs-lookup"><span data-stu-id="10db9-152">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="10db9-153">Narzędzie jest dostępne tylko dla każdego profilu użytkownika którym zostało zainstalowane narzędzie.</span><span class="sxs-lookup"><span data-stu-id="10db9-153">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="10db9-154">Można również zainstalować narzędzia globalnej w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="10db9-154">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="10db9-155">Podczas instalowania w określonym katalogu, użytkownik musi upewnić się polecenie jest dostępne, umieszczając tego katalogu w ścieżce, wywołując polecenie z katalogu, który został określony, lub podczas wywoływania narzędzia z w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="10db9-155">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="10db9-156">W tym przypadku interfejsu wiersza polecenia platformy .NET Core nie powoduje dodania tej lokalizacji automatycznie do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="10db9-156">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="10db9-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10db9-157">See also</span></span>

- [<span data-ttu-id="10db9-158">Samouczek dotyczący "Wprowadzenie za pomocą narzędzia interfejsu wiersza polecenia w strukturze ML.NET"</span><span class="sxs-lookup"><span data-stu-id="10db9-158">Tutorial on 'Getting Started with ML.NET CLI tool'</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="10db9-159">Jak automatycznie uczenia modeli za pomocą narzędzia interfejsu wiersza polecenia w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="10db9-159">How to automatically train models with the ML.NET CLI tool</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="10db9-160">Podręcznik interfejsu wiersza polecenia w strukturze ML.NET train automatycznie poleceń</span><span class="sxs-lookup"><span data-stu-id="10db9-160">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="10db9-161">Dane telemetryczne w interfejsie wiersza polecenia w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="10db9-161">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
