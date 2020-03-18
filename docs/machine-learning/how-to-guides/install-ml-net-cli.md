---
title: Jak zainstalować narzędzie ML.NET Command-Line Interface (CLI)
description: Dowiedz się, jak zainstalować, uaktualnić, obniżyć i odinstalować narzędzie ML.NET interfejsu wiersza polecenia (CLI).
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 9f678c7117d32bf817139951db7eef2c3d0f5eb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848642"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="4aa1c-103">Jak zainstalować narzędzie ML.NET Command-Line Interface (CLI)</span><span class="sxs-lookup"><span data-stu-id="4aa1c-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="4aa1c-104">Dowiedz się, jak zainstalować ML.NET interfejsu wiersza polecenia (interfejsu wiersza polecenia) w systemie Windows, Mac lub Linux.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-104">Learn how to install the ML.NET CLI (command-line interface) on Windows, Mac, or Linux.</span></span>

<span data-ttu-id="4aa1c-105">ML.NET CLI generuje dobrej jakości modele ML.NET i kod źródłowy przy użyciu automatycznego uczenia maszynowego (AutoML) i zestawu danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-105">The ML.NET CLI generates good quality ML.NET models and source code using automated machine learning (AutoML) and a training dataset.</span></span>

> [!NOTE]
> <span data-ttu-id="4aa1c-106">Ten temat odnosi się do ML.NET cli i ML.NET AutoML, które są obecnie w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-106">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="4aa1c-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="4aa1c-107">Pre-requisites</span></span>

- [<span data-ttu-id="4aa1c-108">Zestaw SDK .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="4aa1c-108">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="4aa1c-109">(Opcjonalnie) [Visual Studio 2017 lub 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="4aa1c-109">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="4aa1c-110">Wygenerowane projekty kodu C# można uruchomić za `F5` pomocą programu `dotnet run` Visual Studio, naciskając klawisz lub za pomocą (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="4aa1c-110">You can run the generated C# code projects with Visual Studio by pressing the `F5` key or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="4aa1c-111">Uwaga: Jeśli po zainstalowaniu [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` polecenie nie działa, wyloguj się z systemu Windows i zaloguj się ponownie.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-111">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="4aa1c-112">Instalowanie</span><span class="sxs-lookup"><span data-stu-id="4aa1c-112">Install</span></span>

<span data-ttu-id="4aa1c-113">ML.NET CLI jest zainstalowany jak każde inne narzędzie globalne dotnet.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-113">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="4aa1c-114">Używasz polecenia `dotnet tool install` .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-114">You use the `dotnet tool install` .NET Core CLI command.</span></span>

<span data-ttu-id="4aa1c-115">W poniższym przykładzie pokazano, jak zainstalować ML.NET cli w domyślnej lokalizacji kanału danych NuGet:</span><span class="sxs-lookup"><span data-stu-id="4aa1c-115">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="4aa1c-116">Jeśli nie można zainstalować narzędzia (oznacza to, że nie jest dostępne w domyślnym kanale NuGet), wyświetlane są komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-116">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="4aa1c-117">Sprawdź, czy oczekiwane kanały są sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-117">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="4aa1c-118">Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat z poleceniem użytym do wywołania narzędzia i zainstalowaną wersją, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4aa1c-118">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="4aa1c-119">Można potwierdzić, że instalacja zakończyła się pomyślnie, wpisując następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4aa1c-119">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="4aa1c-120">Powinna zostać wyświetlona pomoc dotycząca dostępnych poleceń dla narzędzia mlnet, takiego jak polecenie "auto-train".</span><span class="sxs-lookup"><span data-stu-id="4aa1c-120">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="4aa1c-121">Instalowanie określonej wersji</span><span class="sxs-lookup"><span data-stu-id="4aa1c-121">Install a specific release version</span></span>

<span data-ttu-id="4aa1c-122">Jeśli próbujesz zainstalować wersję w wersji wstępnej lub określoną wersję narzędzia, możesz określić [strukturę](../../standard/frameworks.md) w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="4aa1c-122">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="4aa1c-123">Można również sprawdzić, czy pakiet jest poprawnie zainstalowany, wpisując następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4aa1c-123">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="4aa1c-124">Odinstalowywanie pakietu CLI</span><span class="sxs-lookup"><span data-stu-id="4aa1c-124">Uninstall the CLI package</span></span>

<span data-ttu-id="4aa1c-125">Wpisz następujące polecenie, aby odinstalować pakiet z komputera lokalnego:</span><span class="sxs-lookup"><span data-stu-id="4aa1c-125">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="4aa1c-126">Aktualizowanie pakietu CLI</span><span class="sxs-lookup"><span data-stu-id="4aa1c-126">Update the CLI package</span></span>

<span data-ttu-id="4aa1c-127">Wpisz następujące polecenie, aby zaktualizować pakiet z komputera lokalnego:</span><span class="sxs-lookup"><span data-stu-id="4aa1c-127">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="4aa1c-128">Konfigurowanie sugestii cli (automatyczne uzupełnianie oparte na karcie)</span><span class="sxs-lookup"><span data-stu-id="4aa1c-128">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="4aa1c-129">Ponieważ ML.NET CLI jest `System.CommandLine`oparty na , ma wbudowaną obsługę uzupełniania kart.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-129">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="4aa1c-130">Przykład działania automatycznego uzupełniania kart jest wyświetlany w następującej animacji:</span><span class="sxs-lookup"><span data-stu-id="4aa1c-130">An example of how tab auto completion works is shown in the following animation:</span></span>

![image](./media/cli-tab-completion.gif)

<span data-ttu-id="4aa1c-132">"Automatyczne uzupełnianie oparte na kartach" (sugestie parametrów) działa na *windows PowerShell* i *macOS /Linux bash,* ale nie będzie działać na *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-132">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="4aa1c-133">Aby go włączyć, w bieżącej wersji zapoznawczej użytkownik końcowy musi wykonać kilka kroków raz na powłokę, opisane poniżej.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-133">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="4aa1c-134">Gdy to zrobisz, zakończenia będą działać `System.CommandLine` dla wszystkich aplikacji napisanych przy użyciu takich jak ML.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-134">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="4aa1c-135">Na komputerze, na którym chcesz włączyć ukończenie, musisz wykonać dwie czynności.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-135">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="4aa1c-136">Zainstaluj `dotnet-suggest` narzędzie globalne, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4aa1c-136">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="4aa1c-137">Dodaj odpowiedni skrypt podkładki do profilu powłoki.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-137">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="4aa1c-138">Może być trzeba utworzyć plik profilu powłoki.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-138">You may have to create a shell profile file.</span></span> <span data-ttu-id="4aa1c-139">Skrypt składki przekaże żądania ukończenia `dotnet-suggest` z powłoki do `System.CommandLine`narzędzia, które przekazuje do odpowiedniej aplikacji opartej.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-139">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="4aa1c-140">Dla bash, dodaj zawartość [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) do `~/.bash_profile`.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-140">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="4aa1c-141">W przypadku programu PowerShell dodaj zawartość pliku [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) do profilu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-141">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="4aa1c-142">Oczekiwaną ścieżkę do profilu programu PowerShell można znaleźć, uruchamiając w konsoli następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4aa1c-142">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ```

<span data-ttu-id="4aa1c-143">(W przypadku innych pocisków [poszukaj](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) lub otwórz [problem).](https://github.com/dotnet/System.CommandLine/issues)</span><span class="sxs-lookup"><span data-stu-id="4aa1c-143">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="4aa1c-144">Katalog instalacji</span><span class="sxs-lookup"><span data-stu-id="4aa1c-144">Installation directory</span></span>

<span data-ttu-id="4aa1c-145">ML.NET CLI można zainstalować w katalogu domyślnym lub w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-145">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="4aa1c-146">Katalogi domyślne to:</span><span class="sxs-lookup"><span data-stu-id="4aa1c-146">The default directories are:</span></span>

| <span data-ttu-id="4aa1c-147">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="4aa1c-147">OS</span></span>          | <span data-ttu-id="4aa1c-148">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="4aa1c-148">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="4aa1c-149">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="4aa1c-149">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="4aa1c-150">Windows</span><span class="sxs-lookup"><span data-stu-id="4aa1c-150">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="4aa1c-151">Te lokalizacje są dodawane do ścieżki użytkownika po pierwszym uruchomieniu sdk, więc narzędzia globalne zainstalowane tam mogą być wywoływane bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-151">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="4aa1c-152">Uwaga: Narzędzia globalne są specyficzne dla użytkownika, a nie globalne maszyny.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-152">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="4aa1c-153">Bycie specyficznym dla użytkownika oznacza, że nie można zainstalować narzędzia globalnego, które jest dostępne dla wszystkich użytkowników urządzenia.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-153">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="4aa1c-154">Narzędzie jest dostępne tylko dla każdego profilu użytkownika, w którym narzędzie zostało zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-154">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="4aa1c-155">Narzędzia globalne można również zainstalować w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-155">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="4aa1c-156">Po zainstalowaniu w określonym katalogu użytkownik musi upewnić się, że polecenie jest dostępne, dołączając ten katalog do ścieżki, wywołując polecenie z określonym katalogiem lub wywołując narzędzie z określonego katalogu.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-156">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="4aa1c-157">W takim przypadku .NET Core CLI nie dodaje tej lokalizacji automatycznie do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-157">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="4aa1c-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4aa1c-158">See also</span></span>

- [<span data-ttu-id="4aa1c-159">ML.NET przegląd cli</span><span class="sxs-lookup"><span data-stu-id="4aa1c-159">ML.NET CLI overview</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="4aa1c-160">Samouczek: Analizowanie nastrojów za pomocą ML.NET interfejsu i ujścia interfejsu i odpowiedzialności</span><span class="sxs-lookup"><span data-stu-id="4aa1c-160">Tutorial: Analyze sentiment with the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="4aa1c-161">ML.NET przewodnik po polecenia automatycznego pociągu cli</span><span class="sxs-lookup"><span data-stu-id="4aa1c-161">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="4aa1c-162">Telemetria w ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="4aa1c-162">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
