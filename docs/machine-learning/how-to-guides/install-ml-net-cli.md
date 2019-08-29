---
title: Jak zainstalować narzędzie ML.NET interfejsu wiersza polecenia (CLI)
description: Omówienie i instalacja narzędzia ML.NET interfejsu wiersza polecenia (CLI).
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 8b6de466a6cf72b44a16c80fc024671bc4e975e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106901"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="f9bfb-103">Jak zainstalować narzędzie ML.NET interfejsu wiersza polecenia (CLI)</span><span class="sxs-lookup"><span data-stu-id="f9bfb-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="f9bfb-104">Interfejs wiersza polecenia ML.NET — narzędzie, które można uruchomić w dowolnym wierszu polecenia (Windows, Mac lub Linux) w celu wygenerowania dobrej jakości modeli ML.NET i kodu źródłowego na podstawie podanych szkoleń.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-104">The ML.NET CLI (command-line interface) is a tool you can run on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on training datasets you provide.</span></span>

> [!NOTE]
> <span data-ttu-id="f9bfb-105">Ten temat dotyczy ML.NET interfejsu wiersza polecenia i ML.NET AutoML, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-105">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="f9bfb-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f9bfb-106">Pre-requisites</span></span>

- [<span data-ttu-id="f9bfb-107">Zestaw SDK platformy .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="f9bfb-107">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="f9bfb-108">Obowiązkowe [Visual Studio 2017 lub 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="f9bfb-108">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="f9bfb-109">Można uruchomić wygenerowane C# projekty kodu za pomocą programu Visual Studio F5 lub z `dotnet run` (interfejs wiersza polecenia platformy .NET Core).</span><span class="sxs-lookup"><span data-stu-id="f9bfb-109">You can either run the generated C# code projects with Visual Studio F5 or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="f9bfb-110">Uwaga: Jeśli po zainstalowaniu [zestawu .NET Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` polecenie nie działa, Wyloguj się z systemu Windows i zaloguj się ponownie.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-110">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="f9bfb-111">Zainstaluj</span><span class="sxs-lookup"><span data-stu-id="f9bfb-111">Install</span></span>

<span data-ttu-id="f9bfb-112">Interfejs wiersza polecenia ML.NET jest instalowany jak każdy inny narzędzie globalne dotnet.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-112">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="f9bfb-113">Używasz polecenia interfejs wiersza polecenia platformy .NET Core `dotnet tool install` .</span><span class="sxs-lookup"><span data-stu-id="f9bfb-113">You use the `dotnet tool install` .NET Core CLI command.</span></span> 

<span data-ttu-id="f9bfb-114">Poniższy przykład pokazuje, jak zainstalować interfejs wiersza polecenia ML.NET w domyślnej lokalizacji źródła danych NuGet:</span><span class="sxs-lookup"><span data-stu-id="f9bfb-114">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```console
dotnet tool install -g mlnet
```

<span data-ttu-id="f9bfb-115">Jeśli nie można zainstalować narzędzia (czyli jeśli nie jest ono dostępne w domyślnym źródle danych NuGet), wyświetlane są komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-115">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="f9bfb-116">Sprawdź, czy wybrane źródła danych są sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-116">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="f9bfb-117">Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat z poleceniem, które służy do wywoływania narzędzia i zainstalowanej wersji, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f9bfb-117">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="f9bfb-118">Można potwierdzić, że instalacja zakończyła się pomyślnie, wpisując następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f9bfb-118">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="f9bfb-119">Powinna zostać wyświetlona Pomoc dotycząca dostępnych poleceń dla narzędzia mlnet, takiego jak polecenie "autouczenie".</span><span class="sxs-lookup"><span data-stu-id="f9bfb-119">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="f9bfb-120">Zainstaluj określoną wersję wydania</span><span class="sxs-lookup"><span data-stu-id="f9bfb-120">Install a specific release version</span></span>

<span data-ttu-id="f9bfb-121">Jeśli próbujesz zainstalować wersję wstępną lub określoną wersję narzędzia, możesz określić [strukturę](../../standard/frameworks.md) przy użyciu następującego formatu:</span><span class="sxs-lookup"><span data-stu-id="f9bfb-121">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```console
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="f9bfb-122">Możesz również sprawdzić, czy pakiet jest prawidłowo zainstalowany, wpisując następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f9bfb-122">You can also check if the package is properly installed by typing the following command:</span></span>

```console
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="f9bfb-123">Odinstalowywanie pakietu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="f9bfb-123">Uninstall the CLI package</span></span>

<span data-ttu-id="f9bfb-124">Wpisz następujące polecenie, aby odinstalować pakiet z komputera lokalnego:</span><span class="sxs-lookup"><span data-stu-id="f9bfb-124">Type the following command to uninstall the package from your local machine:</span></span>

```console
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="f9bfb-125">Aktualizowanie pakietu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="f9bfb-125">Update the CLI package</span></span>

<span data-ttu-id="f9bfb-126">Wpisz następujące polecenie, aby zaktualizować pakiet z komputera lokalnego:</span><span class="sxs-lookup"><span data-stu-id="f9bfb-126">Type the following command to update the package from your local machine:</span></span>

```console
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="f9bfb-127">Konfigurowanie sugestii interfejsu wiersza polecenia (funkcja automatycznego uzupełniania oparta na kartach)</span><span class="sxs-lookup"><span data-stu-id="f9bfb-127">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="f9bfb-128">Ponieważ interfejs wiersza polecenia ml.NET jest oparty `System.CommandLine`na systemie, ma wbudowaną obsługę uzupełniania kart.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-128">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="f9bfb-129">Przykład sposobu, w jaki działa funkcja automatycznego uzupełniania kart, jest pokazana w następującej animacji:</span><span class="sxs-lookup"><span data-stu-id="f9bfb-129">An example of how tab auto completion works is shown in the following animation:</span></span>

![obraz](./media/cli-tab-completion.gif)

<span data-ttu-id="f9bfb-131">"Autouzupełnianie oparte na kartach" (sugestie dotyczące parametrów) działają w programie *Windows PowerShell* i *macOS/Linux bash* , ale nie będzie działać w programie *Windows cmd*.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-131">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="f9bfb-132">Aby włączyć tę funkcję, w bieżącej wersji zapoznawczej użytkownik końcowy musi wykonać kilka kroków raz na powłokę poniżej.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-132">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="f9bfb-133">Po wykonaniu tych czynności uzupełnianie będzie działało dla wszystkich aplikacji, które `System.CommandLine` zostały utworzone przy użyciu takiego interfejsu wiersza polecenia ml.NET.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-133">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="f9bfb-134">Na komputerze, na którym chcesz włączyć uzupełnianie, musisz wykonać dwie czynności.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-134">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="f9bfb-135">Zainstaluj narzędzie `dotnet-suggest` globalne, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f9bfb-135">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```console
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="f9bfb-136">Dodaj odpowiedni skrypt podkładki do profilu powłoki.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-136">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="f9bfb-137">Może być konieczne utworzenie pliku profilu powłoki.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-137">You may have to create a shell profile file.</span></span> <span data-ttu-id="f9bfb-138">Skrypt podkładki przekaże żądania ukończenia z powłoki do `dotnet-suggest` narzędzia, które deleguje do odpowiedniej `System.CommandLine`aplikacji opartej na usłudze.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-138">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="f9bfb-139">W przypadku bash Dodaj zawartość elementu [dotnet-sugerował-podkładkę. bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) do `~/.bash_profile`.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-139">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="f9bfb-140">W przypadku programu PowerShell Dodaj zawartość [dotnet-Suggest-Shim. ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) do profilu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-140">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="f9bfb-141">Oczekiwaną ścieżkę do profilu programu PowerShell można znaleźć, uruchamiając następujące polecenie w konsoli programu:</span><span class="sxs-lookup"><span data-stu-id="f9bfb-141">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ``` 

<span data-ttu-id="f9bfb-142">(W przypadku innych powłok należy [](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) poszukać lub otworzyć [problem](https://github.com/dotnet/System.CommandLine/issues)).</span><span class="sxs-lookup"><span data-stu-id="f9bfb-142">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="f9bfb-143">Katalog instalacji</span><span class="sxs-lookup"><span data-stu-id="f9bfb-143">Installation directory</span></span>

<span data-ttu-id="f9bfb-144">Interfejs wiersza polecenia ML.NET można zainstalować w katalogu domyślnym lub w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-144">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="f9bfb-145">Domyślne katalogi są następujące:</span><span class="sxs-lookup"><span data-stu-id="f9bfb-145">The default directories are:</span></span>

| <span data-ttu-id="f9bfb-146">OS</span><span class="sxs-lookup"><span data-stu-id="f9bfb-146">OS</span></span>          | <span data-ttu-id="f9bfb-147">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="f9bfb-147">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="f9bfb-148">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="f9bfb-148">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="f9bfb-149">Windows</span><span class="sxs-lookup"><span data-stu-id="f9bfb-149">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="f9bfb-150">Te lokalizacje są dodawane do ścieżki użytkownika podczas pierwszego uruchomienia zestawu SDK, dzięki czemu globalne narzędzia mogą być wywoływane bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-150">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="f9bfb-151">Uwaga: globalne narzędzia to specyficzne dla użytkownika, a nie globalne maszyny.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-151">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="f9bfb-152">Specyficzne dla użytkownika oznacza, że nie można zainstalować narzędzia globalnego, które jest dostępne dla wszystkich użytkowników komputera.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-152">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="f9bfb-153">Narzędzie jest dostępne tylko dla każdego profilu użytkownika, w którym zainstalowano narzędzie.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-153">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="f9bfb-154">Narzędzia globalne można także zainstalować w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-154">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="f9bfb-155">Po zainstalowaniu w określonym katalogu użytkownik musi upewnić się, że polecenie jest dostępne, dołączając ten katalog w ścieżce, wywołując polecenie z określonym katalogiem lub wywołując narzędzie z w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-155">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="f9bfb-156">W takim przypadku interfejs wiersza polecenia platformy .NET Core nie dodaje automatycznie tej lokalizacji do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="f9bfb-156">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9bfb-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9bfb-157">See also</span></span>

- [<span data-ttu-id="f9bfb-158">Samouczek dotyczący "Wprowadzenie za pomocą narzędzia interfejsu wiersza polecenia ML.NET"</span><span class="sxs-lookup"><span data-stu-id="f9bfb-158">Tutorial on 'Getting Started with ML.NET CLI tool'</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="f9bfb-159">Jak automatycznie uczenie modeli za pomocą narzędzia interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="f9bfb-159">How to automatically train models with the ML.NET CLI tool</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="f9bfb-160">Przewodnik dotyczący poleceń autouczenia interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="f9bfb-160">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="f9bfb-161">Dane telemetryczne w interfejsie wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="f9bfb-161">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
