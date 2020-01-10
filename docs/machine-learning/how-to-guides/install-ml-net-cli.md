---
title: Jak zainstalować narzędzie ML.NET interfejsu wiersza polecenia (CLI)
description: Dowiedz się, jak zainstalować, uaktualnić, obniżyć i odinstalować narzędzie ML.NET interfejsu wiersza polecenia (CLI).
ms.date: 12/18/2019
ms.openlocfilehash: 350122f2d2d2f03484ab6e272b482adf2094495c
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75739965"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="fc9d9-103">Jak zainstalować narzędzie ML.NET interfejsu wiersza polecenia (CLI)</span><span class="sxs-lookup"><span data-stu-id="fc9d9-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="fc9d9-104">Dowiedz się, jak zainstalować interfejs wiersza polecenia ML.NET w systemie Windows, Mac lub Linux.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-104">Learn how to install the ML.NET CLI (command-line interface) on Windows, Mac, or Linux.</span></span>

<span data-ttu-id="fc9d9-105">Interfejs wiersza polecenia ML.NET generuje dobrą jakość modeli ML.NET i kod źródłowy przy użyciu zautomatyzowanego uczenia maszynowego (AutoML) i zestawu danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-105">The ML.NET CLI generates good quality ML.NET models and source code using automated machine learning (AutoML) and a training dataset.</span></span>

> [!NOTE]
> <span data-ttu-id="fc9d9-106">Ten temat dotyczy ML.NET interfejsu wiersza polecenia i ML.NET AutoML, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-106">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="fc9d9-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="fc9d9-107">Pre-requisites</span></span>

- [<span data-ttu-id="fc9d9-108">Zestaw SDK platformy .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="fc9d9-108">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="fc9d9-109">Obowiązkowe [Visual Studio 2017 lub 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="fc9d9-109">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="fc9d9-110">Możesz uruchomić wygenerowane C# projekty kodu w programie Visual Studio, naciskając klawisz `F5` lub `dotnet run` (interfejs wiersza polecenia platformy .NET Core).</span><span class="sxs-lookup"><span data-stu-id="fc9d9-110">You can run the generated C# code projects with Visual Studio by pressing the `F5` key or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="fc9d9-111">Uwaga: Jeśli po zainstalowaniu [zestawu .NET Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) polecenie `dotnet tool` nie działa, Wyloguj się z systemu Windows i zaloguj się ponownie.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-111">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="fc9d9-112">Instalacja programu</span><span class="sxs-lookup"><span data-stu-id="fc9d9-112">Install</span></span>

<span data-ttu-id="fc9d9-113">Interfejs wiersza polecenia ML.NET jest instalowany jak każdy inny narzędzie globalne dotnet.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-113">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="fc9d9-114">Używasz interfejs wiersza polecenia platformy .NET Core `dotnet tool install` polecenia.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-114">You use the `dotnet tool install` .NET Core CLI command.</span></span>

<span data-ttu-id="fc9d9-115">Poniższy przykład pokazuje, jak zainstalować interfejs wiersza polecenia ML.NET w domyślnej lokalizacji źródła danych NuGet:</span><span class="sxs-lookup"><span data-stu-id="fc9d9-115">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="fc9d9-116">Jeśli nie można zainstalować narzędzia (czyli jeśli nie jest ono dostępne w domyślnym źródle danych NuGet), wyświetlane są komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-116">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="fc9d9-117">Sprawdź, czy wybrane źródła danych są sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-117">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="fc9d9-118">Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat z poleceniem, które służy do wywoływania narzędzia i zainstalowanej wersji, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fc9d9-118">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="fc9d9-119">Można potwierdzić, że instalacja zakończyła się pomyślnie, wpisując następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="fc9d9-119">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="fc9d9-120">Powinna zostać wyświetlona Pomoc dotycząca dostępnych poleceń dla narzędzia mlnet, takiego jak polecenie "autouczenie".</span><span class="sxs-lookup"><span data-stu-id="fc9d9-120">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="fc9d9-121">Zainstaluj określoną wersję wydania</span><span class="sxs-lookup"><span data-stu-id="fc9d9-121">Install a specific release version</span></span>

<span data-ttu-id="fc9d9-122">Jeśli próbujesz zainstalować wersję wstępną lub określoną wersję narzędzia, możesz określić [strukturę](../../standard/frameworks.md) przy użyciu następującego formatu:</span><span class="sxs-lookup"><span data-stu-id="fc9d9-122">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="fc9d9-123">Możesz również sprawdzić, czy pakiet jest prawidłowo zainstalowany, wpisując następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="fc9d9-123">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="fc9d9-124">Odinstalowywanie pakietu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="fc9d9-124">Uninstall the CLI package</span></span>

<span data-ttu-id="fc9d9-125">Wpisz następujące polecenie, aby odinstalować pakiet z komputera lokalnego:</span><span class="sxs-lookup"><span data-stu-id="fc9d9-125">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="fc9d9-126">Aktualizowanie pakietu interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="fc9d9-126">Update the CLI package</span></span>

<span data-ttu-id="fc9d9-127">Wpisz następujące polecenie, aby zaktualizować pakiet z komputera lokalnego:</span><span class="sxs-lookup"><span data-stu-id="fc9d9-127">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="fc9d9-128">Konfigurowanie sugestii interfejsu wiersza polecenia (funkcja automatycznego uzupełniania oparta na kartach)</span><span class="sxs-lookup"><span data-stu-id="fc9d9-128">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="fc9d9-129">Ponieważ interfejs wiersza polecenia ML.NET jest oparty na `System.CommandLine`, ma wbudowaną obsługę uzupełniania kart.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-129">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="fc9d9-130">Przykład sposobu, w jaki działa funkcja automatycznego uzupełniania kart, jest pokazana w następującej animacji:</span><span class="sxs-lookup"><span data-stu-id="fc9d9-130">An example of how tab auto completion works is shown in the following animation:</span></span>

![obraz](./media/cli-tab-completion.gif)

<span data-ttu-id="fc9d9-132">"Autouzupełnianie oparte na kartach" (sugestie dotyczące parametrów) działają w programie *Windows PowerShell* i *macOS/Linux bash* , ale nie będzie działać w programie *Windows cmd*.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-132">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="fc9d9-133">Aby włączyć tę funkcję, w bieżącej wersji zapoznawczej użytkownik końcowy musi wykonać kilka kroków raz na powłokę poniżej.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-133">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="fc9d9-134">Po wykonaniu tej czynności uzupełnianie będzie działało dla wszystkich aplikacji pisanych przy użyciu `System.CommandLine`, takich jak interfejs wiersza polecenia ML.NET.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-134">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="fc9d9-135">Na komputerze, na którym chcesz włączyć uzupełnianie, musisz wykonać dwie czynności.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-135">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="fc9d9-136">Zainstaluj `dotnet-suggest` narzędzie globalne, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="fc9d9-136">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="fc9d9-137">Dodaj odpowiedni skrypt podkładki do profilu powłoki.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-137">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="fc9d9-138">Może być konieczne utworzenie pliku profilu powłoki.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-138">You may have to create a shell profile file.</span></span> <span data-ttu-id="fc9d9-139">Skrypt podkładki przekaże żądania ukończenia z powłoki do narzędzia `dotnet-suggest`, które deleguje do odpowiedniej aplikacji opartej na `System.CommandLine`.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-139">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="fc9d9-140">W przypadku bash Dodaj zawartość elementu [dotnet-sugerował-podkładkę. bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) do `~/.bash_profile`.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-140">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="fc9d9-141">W przypadku programu PowerShell Dodaj zawartość [dotnet-Suggest-Shim. ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) do profilu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-141">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="fc9d9-142">Oczekiwaną ścieżkę do profilu programu PowerShell można znaleźć, uruchamiając następujące polecenie w konsoli programu:</span><span class="sxs-lookup"><span data-stu-id="fc9d9-142">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ```

<span data-ttu-id="fc9d9-143">(W przypadku innych powłok należy [poszukać](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) lub otworzyć [problem](https://github.com/dotnet/System.CommandLine/issues)).</span><span class="sxs-lookup"><span data-stu-id="fc9d9-143">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="fc9d9-144">Katalog instalacji</span><span class="sxs-lookup"><span data-stu-id="fc9d9-144">Installation directory</span></span>

<span data-ttu-id="fc9d9-145">Interfejs wiersza polecenia ML.NET można zainstalować w katalogu domyślnym lub w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-145">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="fc9d9-146">Domyślne katalogi są następujące:</span><span class="sxs-lookup"><span data-stu-id="fc9d9-146">The default directories are:</span></span>

| <span data-ttu-id="fc9d9-147">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="fc9d9-147">OS</span></span>          | <span data-ttu-id="fc9d9-148">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="fc9d9-148">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="fc9d9-149">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="fc9d9-149">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="fc9d9-150">Windows</span><span class="sxs-lookup"><span data-stu-id="fc9d9-150">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="fc9d9-151">Te lokalizacje są dodawane do ścieżki użytkownika podczas pierwszego uruchomienia zestawu SDK, dzięki czemu globalne narzędzia mogą być wywoływane bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-151">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="fc9d9-152">Uwaga: globalne narzędzia to specyficzne dla użytkownika, a nie globalne maszyny.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-152">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="fc9d9-153">Specyficzne dla użytkownika oznacza, że nie można zainstalować narzędzia globalnego, które jest dostępne dla wszystkich użytkowników komputera.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-153">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="fc9d9-154">Narzędzie jest dostępne tylko dla każdego profilu użytkownika, w którym zainstalowano narzędzie.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-154">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="fc9d9-155">Narzędzia globalne można także zainstalować w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-155">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="fc9d9-156">Po zainstalowaniu w określonym katalogu użytkownik musi upewnić się, że polecenie jest dostępne, dołączając ten katalog w ścieżce, wywołując polecenie z określonym katalogiem lub wywołując narzędzie z w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-156">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="fc9d9-157">W takim przypadku interfejs wiersza polecenia platformy .NET Core nie dodaje automatycznie tej lokalizacji do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="fc9d9-157">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc9d9-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc9d9-158">See also</span></span>

- [<span data-ttu-id="fc9d9-159">Przegląd interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="fc9d9-159">ML.NET CLI overview</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="fc9d9-160">Samouczek: analizowanie tonacji za pomocą interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="fc9d9-160">Tutorial: Analyze sentiment with the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="fc9d9-161">Przewodnik dotyczący poleceń autouczenia interfejsu wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="fc9d9-161">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="fc9d9-162">Dane telemetryczne w interfejsie wiersza polecenia ML.NET</span><span class="sxs-lookup"><span data-stu-id="fc9d9-162">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
