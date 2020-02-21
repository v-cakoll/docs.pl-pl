---
title: Narzędzia .NET Core
description: Jak instalować, używać, aktualizować i usuwać narzędzia .NET Core. Obejmuje narzędzia globalne, narzędzia ścieżki narzędzi i narzędzia lokalne.
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: d8ee30df3fe063fd41a85072d145b1b5eec7d0d0
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543394"
---
# <a name="how-to-manage-net-core-tools"></a><span data-ttu-id="46511-104">Jak zarządzać narzędziami programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="46511-104">How to manage .NET Core tools</span></span>

<span data-ttu-id="46511-105">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="46511-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="46511-106">Narzędzie .NET Core jest specjalnym pakietem NuGet, który zawiera aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="46511-106">A .NET Core tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="46511-107">Narzędzie można zainstalować na maszynie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="46511-107">A tool can be installed on your machine in the following ways:</span></span>

* <span data-ttu-id="46511-108">Jako narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="46511-108">As a global tool.</span></span>

  <span data-ttu-id="46511-109">Pliki binarne narzędzia są instalowane w katalogu domyślnym, który jest dodawany do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="46511-109">The tool binaries are installed in a default directory that is added to the PATH environment variable.</span></span> <span data-ttu-id="46511-110">Można wywołać narzędzie z dowolnego katalogu na maszynie bez określania jego lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="46511-110">You can invoke the tool from any directory on the machine without specifying its location.</span></span> <span data-ttu-id="46511-111">Jedna wersja narzędzia jest używana dla wszystkich katalogów na komputerze.</span><span class="sxs-lookup"><span data-stu-id="46511-111">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="46511-112">Jako narzędzie globalne w niestandardowej lokalizacji (nazywanej również narzędziem ścieżki narzędzia).</span><span class="sxs-lookup"><span data-stu-id="46511-112">As a global tool in a custom location (also known as a tool-path tool).</span></span>

  <span data-ttu-id="46511-113">Pliki binarne narzędzia są instalowane w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="46511-113">The tool binaries are installed in a location that you specify.</span></span> <span data-ttu-id="46511-114">Możesz wywołać narzędzie z katalogu instalacyjnego lub podając katalog z nazwą polecenia lub dodając katalog do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="46511-114">You can invoke the tool from the installation directory or by providing the directory with the command name or by adding the directory to the PATH environment variable.</span></span> <span data-ttu-id="46511-115">Jedna wersja narzędzia jest używana dla wszystkich katalogów na komputerze.</span><span class="sxs-lookup"><span data-stu-id="46511-115">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="46511-116">Jako narzędzie lokalne (dotyczy zestaw .NET Core SDK 3,0 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="46511-116">As a local tool (applies to .NET Core SDK 3.0 and later).</span></span>

  <span data-ttu-id="46511-117">Pliki binarne narzędzia są instalowane w katalogu domyślnym.</span><span class="sxs-lookup"><span data-stu-id="46511-117">The tool binaries are installed in a default directory.</span></span> <span data-ttu-id="46511-118">Należy wywołać narzędzie z katalogu instalacyjnego lub któregokolwiek z jego podkatalogów.</span><span class="sxs-lookup"><span data-stu-id="46511-118">You invoke the tool from the installation directory or any of its subdirectories.</span></span> <span data-ttu-id="46511-119">Różne katalogi mogą korzystać z różnych wersji tego samego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="46511-119">Different directories can use different versions of the same tool.</span></span>
  
  <span data-ttu-id="46511-120">Interfejs wiersza polecenia platformy .NET używa plików manifestu do śledzenia, które narzędzia są instalowane jako lokalne w katalogu.</span><span class="sxs-lookup"><span data-stu-id="46511-120">The .NET CLI uses manifest files to keep track of which tools are installed as local to a directory.</span></span> <span data-ttu-id="46511-121">Gdy plik manifestu jest zapisywany w katalogu głównym repozytorium kodu źródłowego, współautor może sklonować repozytorium i wywoływać pojedyncze interfejs wiersza polecenia platformy .NET Core polecenie, które instaluje wszystkie narzędzia wymienione w plikach manifestu.</span><span class="sxs-lookup"><span data-stu-id="46511-121">When the manifest file is saved in the root directory of a source code repository, a contributor can clone the repository and invoke a single .NET Core CLI command that installs all of the tools listed in the manifest files.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="46511-122">Narzędzia .NET Core Tools działają w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="46511-122">.NET Core tools run in full trust.</span></span> <span data-ttu-id="46511-123">Nie instaluj narzędzia .NET Core, chyba że ufasz autorowi.</span><span class="sxs-lookup"><span data-stu-id="46511-123">Do not install a .NET Core tool unless you trust the author.</span></span>

## <a name="find-a-tool"></a><span data-ttu-id="46511-124">Znajdź narzędzie</span><span class="sxs-lookup"><span data-stu-id="46511-124">Find a tool</span></span>

<span data-ttu-id="46511-125">Obecnie platforma .NET Core nie ma funkcji wyszukiwania w narzędziu.</span><span class="sxs-lookup"><span data-stu-id="46511-125">Currently, .NET Core doesn't have a tool search feature.</span></span> <span data-ttu-id="46511-126">Oto kilka sposobów znajdowania narzędzi:</span><span class="sxs-lookup"><span data-stu-id="46511-126">Here are some ways to find tools:</span></span>

* <span data-ttu-id="46511-127">Zobacz listę narzędzi w repozytorium GitHub [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .</span><span class="sxs-lookup"><span data-stu-id="46511-127">See the list of tools in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>
* <span data-ttu-id="46511-128">Użyj [ToolGet](https://www.toolget.net/) , aby wyszukać narzędzia platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="46511-128">Use [ToolGet](https://www.toolget.net/) to search for .NET tools.</span></span>
* <span data-ttu-id="46511-129">Zobacz kod źródłowy narzędzi utworzonych przez zespół ASP.NET Core w [katalogu Tools w repozytorium GitHub/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span><span class="sxs-lookup"><span data-stu-id="46511-129">See the source code for the tools created by the ASP.NET Core team in the [Tools directory of the dotnet/aspnetcore GitHub repository](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span></span>
* <span data-ttu-id="46511-130">Informacje o narzędziach diagnostycznych w [programie .NET Core dotnet Diagnostic Tools](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span><span class="sxs-lookup"><span data-stu-id="46511-130">Learn about diagnostic tools at [.NET Core dotnet diagnostic tools](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span></span>
* <span data-ttu-id="46511-131">Przeszukaj witrynę sieci Web [NuGet](https://www.nuget.org) .</span><span class="sxs-lookup"><span data-stu-id="46511-131">Search the [NuGet](https://www.nuget.org) website.</span></span> <span data-ttu-id="46511-132">Jednak witryna NuGet nie ma jeszcze funkcji umożliwiającej wyszukiwanie tylko pakietów narzędzi.</span><span class="sxs-lookup"><span data-stu-id="46511-132">However, the NuGet site doesn't yet have a feature that lets you search only for tool packages.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="46511-133">Sprawdź autora i statystyki</span><span class="sxs-lookup"><span data-stu-id="46511-133">Check the author and statistics</span></span>

<span data-ttu-id="46511-134">Ponieważ narzędzia platformy .NET Core działają w trybie pełnego zaufania, a narzędzia globalne są dodawane do zmiennej środowiskowej PATH, mogą być bardzo wydajne.</span><span class="sxs-lookup"><span data-stu-id="46511-134">Since .NET Core tools run in full trust, and global tools are added to the PATH environment variable, they can be very powerful.</span></span> <span data-ttu-id="46511-135">Nie pobieraj narzędzi z osób, które nie są zaufane.</span><span class="sxs-lookup"><span data-stu-id="46511-135">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="46511-136">Jeśli narzędzie jest hostowane w usłudze NuGet, można sprawdzić autora i statystyk, wyszukując narzędzie.</span><span class="sxs-lookup"><span data-stu-id="46511-136">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="46511-137">Instalowanie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="46511-137">Install a global tool</span></span>

<span data-ttu-id="46511-138">Aby zainstalować narzędzie jako narzędzie globalne, użyj opcji `-g` lub `--global` [instalacji narzędzia dotnet](dotnet-tool-install.md), jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="46511-138">To install a tool as a global tool, use the `-g` or `--global` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="46511-139">Dane wyjściowe przedstawiają polecenie używane do wywołania narzędzia i zainstalowanej wersji, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="46511-139">The output shows the command used to invoke the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

<span data-ttu-id="46511-140">Domyślna lokalizacja plików binarnych narzędzia zależy od systemu operacyjnego:</span><span class="sxs-lookup"><span data-stu-id="46511-140">The default location for a tool's binaries depends on the operating system:</span></span>

| <span data-ttu-id="46511-141">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="46511-141">OS</span></span>          | <span data-ttu-id="46511-142">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="46511-142">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="46511-143">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="46511-143">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="46511-144">System Windows</span><span class="sxs-lookup"><span data-stu-id="46511-144">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="46511-145">Ta lokalizacja jest dodawana do ścieżki użytkownika podczas pierwszego uruchomienia zestawu SDK, dzięki czemu narzędzia globalne mogą być wywoływane z dowolnego katalogu bez określania lokalizacji narzędzia.</span><span class="sxs-lookup"><span data-stu-id="46511-145">This location is added to the user's path when the SDK is first run, so global tools can be invoked from any directory without specifying the tool location.</span></span>

<span data-ttu-id="46511-146">Dostęp do narzędzi to specyficzne dla użytkownika, a nie globalne maszyny.</span><span class="sxs-lookup"><span data-stu-id="46511-146">Tool access is user-specific, not machine global.</span></span> <span data-ttu-id="46511-147">Narzędzie globalne jest dostępne tylko dla użytkownika, który zainstalował narzędzie.</span><span class="sxs-lookup"><span data-stu-id="46511-147">A global tool is only available to the user that installed the tool.</span></span>

### <a name="install-a-global-tool-in-a-custom-location"></a><span data-ttu-id="46511-148">Instalowanie narzędzia globalnego w niestandardowej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="46511-148">Install a global tool in a custom location</span></span>

<span data-ttu-id="46511-149">Aby zainstalować narzędzie jako narzędzie globalne w niestandardowej lokalizacji, użyj opcji `--tool-path` [instalacji narzędzia dotnet](dotnet-tool-install.md), jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="46511-149">To install a tool as a global tool in a custom location, use the `--tool-path` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following examples.</span></span>

<span data-ttu-id="46511-150">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="46511-150">On Windows:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

<span data-ttu-id="46511-151">W systemie Linux lub macOS:</span><span class="sxs-lookup"><span data-stu-id="46511-151">On Linux or macOS:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

<span data-ttu-id="46511-152">Zestaw .NET Core SDK nie dodaje automatycznie tej lokalizacji do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="46511-152">The .NET Core SDK doesn't add this location automatically to the PATH environment variable.</span></span> <span data-ttu-id="46511-153">Aby [wywołać narzędzie ścieżki narzędzi](#invoke-a-tool-path-tool), należy upewnić się, że polecenie jest dostępne za pomocą jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="46511-153">To [invoke a tool-path tool](#invoke-a-tool-path-tool), you have to make sure the command is available by using one of the following methods:</span></span>

* <span data-ttu-id="46511-154">Dodaj katalog instalacyjny do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="46511-154">Add the installation directory to the PATH environment variable.</span></span>
* <span data-ttu-id="46511-155">Określ pełną ścieżkę do narzędzia podczas jego wywoływania.</span><span class="sxs-lookup"><span data-stu-id="46511-155">Specify the full path to the tool when you invoke it.</span></span>
* <span data-ttu-id="46511-156">Wywołaj narzędzie z katalogu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="46511-156">Invoke the tool from within the installation directory.</span></span>

## <a name="install-a-local-tool"></a><span data-ttu-id="46511-157">Instalowanie narzędzia lokalnego</span><span class="sxs-lookup"><span data-stu-id="46511-157">Install a local tool</span></span>

<span data-ttu-id="46511-158">**Dotyczy zestawu .NET Core 3,0 SDK i nowszych wersji.**</span><span class="sxs-lookup"><span data-stu-id="46511-158">**Applies to .NET Core 3.0 SDK and later.**</span></span>

<span data-ttu-id="46511-159">Aby zainstalować narzędzie tylko do dostępu lokalnego (dla bieżącego katalogu i podkatalogów), należy dodać je do pliku manifestu narzędzia.</span><span class="sxs-lookup"><span data-stu-id="46511-159">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a tool manifest file.</span></span> <span data-ttu-id="46511-160">Aby utworzyć plik manifestu narzędzia, uruchom polecenie `dotnet new tool-manifest`:</span><span class="sxs-lookup"><span data-stu-id="46511-160">To create a tool manifest file, run the `dotnet new tool-manifest` command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="46511-161">To polecenie tworzy plik manifestu o nazwie *dotnet-Tools. JSON* w katalogu *. config* .</span><span class="sxs-lookup"><span data-stu-id="46511-161">This command creates a manifest file named *dotnet-tools.json* under the *.config* directory.</span></span> <span data-ttu-id="46511-162">Aby dodać narzędzie lokalne do pliku manifestu, należy użyć polecenia [Narzędzia dotnet](dotnet-tool-install.md) i **pominąć** opcje `--global` i `--tool-path`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="46511-162">To add a local tool to the manifest file, use the [dotnet tool install](dotnet-tool-install.md) command and **omit** the `--global` and `--tool-path` options, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay
```

<span data-ttu-id="46511-163">Dane wyjściowe polecenia pokazują plik manifestu, w którym znajduje się nowo zainstalowane narzędzie, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="46511-163">The command output shows which manifest file the newly installed tool is in, similar to the following example:</span></span>

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

<span data-ttu-id="46511-164">W poniższym przykładzie przedstawiono plik manifestu z zainstalowanymi dwoma lokalnymi narzędziami:</span><span class="sxs-lookup"><span data-stu-id="46511-164">The following example shows a manifest file with two local tools installed:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    },
    "dotnetsay": {
      "version": "2.1.3",
      "commands": [
        "dotnetsay"
      ]
    }
  }
}
```

<span data-ttu-id="46511-165">Zazwyczaj można dodać lokalne narzędzie do katalogu głównego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="46511-165">You typically add a local tool to the root directory of the repository.</span></span> <span data-ttu-id="46511-166">Po zaewidencjonowaniu pliku manifestu do repozytorium, deweloperzy, którzy ewidencjonują kod z repozytorium, pobierają najnowszy plik manifestu.</span><span class="sxs-lookup"><span data-stu-id="46511-166">After you check in the manifest file to the repository, developers who check out code from the repository get the latest manifest file.</span></span> <span data-ttu-id="46511-167">Aby zainstalować wszystkie narzędzia wymienione w pliku manifestu, uruchom polecenie `dotnet tool restore`:</span><span class="sxs-lookup"><span data-stu-id="46511-167">To install all of the tools listed in the manifest file, they run the `dotnet tool restore` command:</span></span>

```dotnetcli
dotnet tool restore
```

<span data-ttu-id="46511-168">Dane wyjściowe wskazują, które narzędzia zostały przywrócone:</span><span class="sxs-lookup"><span data-stu-id="46511-168">The output indicates which tools were restored:</span></span>

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a><span data-ttu-id="46511-169">Zainstaluj określoną wersję narzędzia</span><span class="sxs-lookup"><span data-stu-id="46511-169">Install a specific tool version</span></span>

<span data-ttu-id="46511-170">Aby zainstalować wersję wstępną lub określoną wersję narzędzia, należy określić numer wersji przy użyciu opcji `--version`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="46511-170">To install a pre-release version or a specific version of a tool, specify the version number by using the `--version` option, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a><span data-ttu-id="46511-171">Korzystanie z narzędzia</span><span class="sxs-lookup"><span data-stu-id="46511-171">Use a tool</span></span>

<span data-ttu-id="46511-172">Polecenie używane do wywoływania narzędzia może różnić się od nazwy instalowanego pakietu.</span><span class="sxs-lookup"><span data-stu-id="46511-172">The command that you use to invoke a tool may be different from the name of the package that you install.</span></span> <span data-ttu-id="46511-173">Aby wyświetlić wszystkie narzędzia aktualnie zainstalowane na komputerze dla bieżącego użytkownika, użyj polecenia z [listy narzędzi dotnet](dotnet-tool-list.md) :</span><span class="sxs-lookup"><span data-stu-id="46511-173">To display all of the tools currently installed on the machine for the current user, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list
```

<span data-ttu-id="46511-174">Dane wyjściowe wyświetlają wersję i polecenie każdego narzędzia, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="46511-174">The output shows each tool's version and command, similar to the following example:</span></span>

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

<span data-ttu-id="46511-175">Jak pokazano w tym przykładzie, lista zawiera narzędzia lokalne.</span><span class="sxs-lookup"><span data-stu-id="46511-175">As shown in this example, the list shows local tools.</span></span> <span data-ttu-id="46511-176">Aby wyświetlić narzędzia globalne, użyj opcji `--global` i aby wyświetlić narzędzia ścieżki narzędzi, użyj opcji `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="46511-176">To see global tools, use the `--global` option, and to see tool-path tools, use the `--tool-path` option.</span></span>

### <a name="invoke-a-global-tool"></a><span data-ttu-id="46511-177">Wywołaj narzędzie globalne</span><span class="sxs-lookup"><span data-stu-id="46511-177">Invoke a global tool</span></span>

<span data-ttu-id="46511-178">W przypadku narzędzi globalnych Użyj narzędzia.</span><span class="sxs-lookup"><span data-stu-id="46511-178">For global tools, use the tool command by itself.</span></span> <span data-ttu-id="46511-179">Na przykład jeśli polecenie jest `dotnetsay` lub `dotnet-doc`, to jest używane do wywołania polecenia:</span><span class="sxs-lookup"><span data-stu-id="46511-179">For example, if the command is `dotnetsay` or `dotnet-doc`, that's what you use to invoke the command:</span></span>

```console
dotnetsay
dotnet-doc
```

<span data-ttu-id="46511-180">Jeśli polecenie zaczyna się od prefiksu `dotnet-`, alternatywnym sposobem wywołania narzędzia jest użycie polecenia `dotnet` i pominięcie prefiksu polecenia narzędzia.</span><span class="sxs-lookup"><span data-stu-id="46511-180">If the command begins with the prefix `dotnet-`, an alternative way to invoke the tool is to use the `dotnet` command and omit the tool command prefix.</span></span> <span data-ttu-id="46511-181">Na przykład jeśli polecenie jest `dotnet-doc`, następujące polecenie wywoła narzędzie:</span><span class="sxs-lookup"><span data-stu-id="46511-181">For example, if the command is `dotnet-doc`, the following command invokes the tool:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="46511-182">Jednak w poniższym scenariuszu nie można użyć `dotnet` polecenia do wywołania narzędzia globalnego:</span><span class="sxs-lookup"><span data-stu-id="46511-182">However, in the following scenario you can't use the `dotnet` command to invoke a global tool:</span></span>

* <span data-ttu-id="46511-183">Narzędzie globalne i narzędzie lokalne mają takie samo polecenie, które jest poprzedzone `dotnet-`.</span><span class="sxs-lookup"><span data-stu-id="46511-183">A global tool and a local tool have the same command prefixed by `dotnet-`.</span></span>
* <span data-ttu-id="46511-184">Chcesz wywołać narzędzie globalne z katalogu, który znajduje się w zakresie dla narzędzia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="46511-184">You want to invoke the global tool from a directory that is in scope for the local tool.</span></span>

<span data-ttu-id="46511-185">W tym scenariuszu `dotnet doc` i `dotnet dotnet-doc` wywoływania narzędzia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="46511-185">In this scenario, `dotnet doc` and `dotnet dotnet-doc` invoke the local tool.</span></span> <span data-ttu-id="46511-186">Aby wywołać narzędzie globalne, użyj polecenia przez samego siebie:</span><span class="sxs-lookup"><span data-stu-id="46511-186">To invoke the global tool, use the command by itself:</span></span>

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a><span data-ttu-id="46511-187">Wywołaj narzędzie ścieżki narzędziowej</span><span class="sxs-lookup"><span data-stu-id="46511-187">Invoke a tool-path tool</span></span>

<span data-ttu-id="46511-188">Aby wywołać narzędzie globalne, które jest instalowane przy użyciu opcji `tool-path`, upewnij się, że polecenie jest dostępne, zgodnie z opisem [we wcześniejszej części tego artykułu](#install-a-global-tool-in-a-custom-location).</span><span class="sxs-lookup"><span data-stu-id="46511-188">To invoke a global tool that is installed by using the `tool-path` option, make sure the command is available, as explained [earlier in this article](#install-a-global-tool-in-a-custom-location).</span></span>

### <a name="invoke-a-local-tool"></a><span data-ttu-id="46511-189">Wywoływanie narzędzia lokalnego</span><span class="sxs-lookup"><span data-stu-id="46511-189">Invoke a local tool</span></span>

<span data-ttu-id="46511-190">Aby wywołać narzędzie lokalne, należy użyć polecenia `dotnet` w katalogu instalacyjnym.</span><span class="sxs-lookup"><span data-stu-id="46511-190">To invoke a local tool, you have to use the `dotnet` command from within the installation directory.</span></span> <span data-ttu-id="46511-191">Możesz użyć długiej formy (`dotnet tool run <COMMAND_NAME>`) lub krótkiej formy (`dotnet <COMMAND_NAME>`), jak pokazano w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="46511-191">You can use the long form (`dotnet tool run <COMMAND_NAME>`) or the short form (`dotnet <COMMAND_NAME>`), as shown in the following examples:</span></span>

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

<span data-ttu-id="46511-192">Jeśli polecenie jest poprzedzone `dotnet-`, można dołączyć lub pominąć prefiks podczas wywoływania narzędzia.</span><span class="sxs-lookup"><span data-stu-id="46511-192">If the command is prefixed by `dotnet-`, you can include or omit the prefix when you invoke the tool.</span></span> <span data-ttu-id="46511-193">Na przykład jeśli polecenie jest `dotnet-doc`, każdy z poniższych przykładów wywoła narzędzie lokalne:</span><span class="sxs-lookup"><span data-stu-id="46511-193">For example, if the command is `dotnet-doc`, any of the following examples invokes the local tool:</span></span>

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a><span data-ttu-id="46511-194">Aktualizowanie narzędzia</span><span class="sxs-lookup"><span data-stu-id="46511-194">Update a tool</span></span>

<span data-ttu-id="46511-195">Aktualizacja narzędzia polega na odinstalowaniu i ponownym zainstalowaniu go z najnowszą stabilną wersją.</span><span class="sxs-lookup"><span data-stu-id="46511-195">Updating a tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="46511-196">Aby zaktualizować narzędzie, należy użyć polecenia " [Update" narzędzia dotnet](dotnet-tool-update.md) z tą samą opcją, która została użyta do zainstalowania narzędzia:</span><span class="sxs-lookup"><span data-stu-id="46511-196">To update a tool, use the [dotnet tool update](dotnet-tool-update.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

<span data-ttu-id="46511-197">W przypadku narzędzia lokalnego zestaw SDK znajduje pierwszy plik manifestu zawierający identyfikator pakietu, przeszukując bieżący katalog i katalogi nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="46511-197">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span> <span data-ttu-id="46511-198">Jeśli w pliku manifestu nie ma takiego identyfikatora pakietu, zestaw SDK dodaje nowy wpis do najbliższego pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="46511-198">If there is no such package ID in any manifest file, the SDK adds a new entry to the closest manifest file.</span></span>

## <a name="uninstall-a-tool"></a><span data-ttu-id="46511-199">Odinstalowywanie narzędzia</span><span class="sxs-lookup"><span data-stu-id="46511-199">Uninstall a tool</span></span>

<span data-ttu-id="46511-200">Usuń narzędzie za pomocą [Narzędzia dotnet Command Uninstall](dotnet-tool-uninstall.md) polecenie z tą samą opcją, która została użyta do zainstalowania narzędzia:</span><span class="sxs-lookup"><span data-stu-id="46511-200">Remove a tool by using the [dotnet tool uninstall](dotnet-tool-uninstall.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path<packagename>
dotnet tool uninstall <packagename>
```

<span data-ttu-id="46511-201">W przypadku narzędzia lokalnego zestaw SDK znajduje pierwszy plik manifestu zawierający identyfikator pakietu, przeszukując bieżący katalog i katalogi nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="46511-201">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span>

## <a name="get-help-and-troubleshoot"></a><span data-ttu-id="46511-202">Uzyskiwanie pomocy i rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="46511-202">Get help and troubleshoot</span></span>

<span data-ttu-id="46511-203">Aby uzyskać listę dostępnych poleceń `dotnet tool`, wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="46511-203">To get a list of available `dotnet tool` commands, enter the following command:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="46511-204">Aby uzyskać instrukcje dotyczące użycia narzędzia, wprowadź jedno z następujących poleceń lub zapoznaj się z witryną sieci Web narzędzia:</span><span class="sxs-lookup"><span data-stu-id="46511-204">To get tool usage instructions, enter one of the following commands or see the tool's website:</span></span>

```dotnetcli
<command> --help
dotnet <command> --help
```

<span data-ttu-id="46511-205">Jeśli instalacja lub uruchomienie narzędzia nie powiedzie się, zobacz [Rozwiązywanie problemów z użyciem narzędzia .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="46511-205">If a tool fails to install or run, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>
