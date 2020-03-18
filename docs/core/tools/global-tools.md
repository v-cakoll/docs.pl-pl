---
title: Narzędzia .NET Core
description: Jak zainstalować, używać, aktualizować i usuwać narzędzia programu .NET Core. Obejmuje narzędzia globalne, narzędzia ścieżki narzędzii i narzędzia lokalne.
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: 2f0101c6385c41eda49bcb2458428c1f14552617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847793"
---
# <a name="how-to-manage-net-core-tools"></a><span data-ttu-id="c888a-104">Jak zarządzać narzędziami programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="c888a-104">How to manage .NET Core tools</span></span>

<span data-ttu-id="c888a-105">**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="c888a-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="c888a-106">Narzędzie .NET Core to specjalny pakiet NuGet zawierający aplikację konsoli.</span><span class="sxs-lookup"><span data-stu-id="c888a-106">A .NET Core tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="c888a-107">Narzędzie można zainstalować na komputerze w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c888a-107">A tool can be installed on your machine in the following ways:</span></span>

* <span data-ttu-id="c888a-108">Jako narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="c888a-108">As a global tool.</span></span>

  <span data-ttu-id="c888a-109">Pliki binarne narzędzi są instalowane w katalogu domyślnym dodanym do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="c888a-109">The tool binaries are installed in a default directory that is added to the PATH environment variable.</span></span> <span data-ttu-id="c888a-110">Narzędzie można wywołać z dowolnego katalogu na komputerze bez określania jego lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="c888a-110">You can invoke the tool from any directory on the machine without specifying its location.</span></span> <span data-ttu-id="c888a-111">Jedna wersja narzędzia jest używana dla wszystkich katalogów na maszynie.</span><span class="sxs-lookup"><span data-stu-id="c888a-111">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="c888a-112">Jako narzędzie globalne w lokalizacji niestandardowej (nazywane również narzędziem ścieżki narzędzia).</span><span class="sxs-lookup"><span data-stu-id="c888a-112">As a global tool in a custom location (also known as a tool-path tool).</span></span>

  <span data-ttu-id="c888a-113">Pliki binarne narzędzi są instalowane w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="c888a-113">The tool binaries are installed in a location that you specify.</span></span> <span data-ttu-id="c888a-114">Narzędzie można wywołać z katalogu instalacyjnego lub podając katalog z nazwą polecenia lub dodając katalog do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="c888a-114">You can invoke the tool from the installation directory or by providing the directory with the command name or by adding the directory to the PATH environment variable.</span></span> <span data-ttu-id="c888a-115">Jedna wersja narzędzia jest używana dla wszystkich katalogów na maszynie.</span><span class="sxs-lookup"><span data-stu-id="c888a-115">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="c888a-116">Jako narzędzie lokalne (dotyczy zestawu .NET Core SDK 3.0 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="c888a-116">As a local tool (applies to .NET Core SDK 3.0 and later).</span></span>

  <span data-ttu-id="c888a-117">Pliki binarne narzędzi są instalowane w katalogu domyślnym.</span><span class="sxs-lookup"><span data-stu-id="c888a-117">The tool binaries are installed in a default directory.</span></span> <span data-ttu-id="c888a-118">Narzędzie wywołujesz z katalogu instalacyjnego lub dowolnego z jego podkatalogów.</span><span class="sxs-lookup"><span data-stu-id="c888a-118">You invoke the tool from the installation directory or any of its subdirectories.</span></span> <span data-ttu-id="c888a-119">Różne katalogi mogą używać różnych wersji tego samego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c888a-119">Different directories can use different versions of the same tool.</span></span>
  
  <span data-ttu-id="c888a-120">Polecenie CLI programu .NET używa plików manifestu do śledzenia, które narzędzia są instalowane jako lokalne w katalogu.</span><span class="sxs-lookup"><span data-stu-id="c888a-120">The .NET CLI uses manifest files to keep track of which tools are installed as local to a directory.</span></span> <span data-ttu-id="c888a-121">Gdy plik manifestu jest zapisywany w katalogu głównym repozytorium kodu źródłowego, współautor może sklonować repozytorium i wywołać pojedyncze polecenie CLI .NET Core, które instaluje wszystkie narzędzia wymienione w plikach manifestu.</span><span class="sxs-lookup"><span data-stu-id="c888a-121">When the manifest file is saved in the root directory of a source code repository, a contributor can clone the repository and invoke a single .NET Core CLI command that installs all of the tools listed in the manifest files.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c888a-122">Narzędzia .NET Core działają w pełnym zaufaniu.</span><span class="sxs-lookup"><span data-stu-id="c888a-122">.NET Core tools run in full trust.</span></span> <span data-ttu-id="c888a-123">Nie instaluj narzędzia .NET Core, chyba że ufasz autorowi.</span><span class="sxs-lookup"><span data-stu-id="c888a-123">Do not install a .NET Core tool unless you trust the author.</span></span>

## <a name="find-a-tool"></a><span data-ttu-id="c888a-124">Znajdowanie narzędzia</span><span class="sxs-lookup"><span data-stu-id="c888a-124">Find a tool</span></span>

<span data-ttu-id="c888a-125">Obecnie program .NET Core nie ma funkcji wyszukiwania narzędzi.</span><span class="sxs-lookup"><span data-stu-id="c888a-125">Currently, .NET Core doesn't have a tool search feature.</span></span> <span data-ttu-id="c888a-126">Oto kilka sposobów znajdowania narzędzi:</span><span class="sxs-lookup"><span data-stu-id="c888a-126">Here are some ways to find tools:</span></span>

* <span data-ttu-id="c888a-127">Zobacz listę narzędzi w repozytorium GitHub [natemcmaster/dotnet-tools.](https://github.com/natemcmaster/dotnet-tools)</span><span class="sxs-lookup"><span data-stu-id="c888a-127">See the list of tools in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>
* <span data-ttu-id="c888a-128">Użyj [NarzędziaPobierz](https://www.toolget.net/) do wyszukiwania narzędzi .NET.</span><span class="sxs-lookup"><span data-stu-id="c888a-128">Use [ToolGet](https://www.toolget.net/) to search for .NET tools.</span></span>
* <span data-ttu-id="c888a-129">Zobacz kod źródłowy narzędzi utworzonych przez zespół ASP.NET Core w [katalogu Narzędzia repozytorium GitHub dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span><span class="sxs-lookup"><span data-stu-id="c888a-129">See the source code for the tools created by the ASP.NET Core team in the [Tools directory of the dotnet/aspnetcore GitHub repository](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span></span>
* <span data-ttu-id="c888a-130">Dowiedz się więcej o narzędziach diagnostycznych w [narzędziach diagnostycznych .NET Core dotnet](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span><span class="sxs-lookup"><span data-stu-id="c888a-130">Learn about diagnostic tools at [.NET Core dotnet diagnostic tools](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span></span>
* <span data-ttu-id="c888a-131">Przeszukaj witrynę [NuGet.](https://www.nuget.org)</span><span class="sxs-lookup"><span data-stu-id="c888a-131">Search the [NuGet](https://www.nuget.org) website.</span></span> <span data-ttu-id="c888a-132">Jednak nuget witryny nie ma jeszcze funkcji, która pozwala wyszukiwać tylko pakiety narzędzi.</span><span class="sxs-lookup"><span data-stu-id="c888a-132">However, the NuGet site doesn't yet have a feature that lets you search only for tool packages.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="c888a-133">Sprawdź autora i statystyki</span><span class="sxs-lookup"><span data-stu-id="c888a-133">Check the author and statistics</span></span>

<span data-ttu-id="c888a-134">Ponieważ narzędzia .NET Core działają w pełnym zaufaniu, a narzędzia globalne są dodawane do zmiennej środowiskowej PATH, mogą być bardzo wydajne.</span><span class="sxs-lookup"><span data-stu-id="c888a-134">Since .NET Core tools run in full trust, and global tools are added to the PATH environment variable, they can be very powerful.</span></span> <span data-ttu-id="c888a-135">Nie pobieraj narzędzi od osób, którym nie ufasz.</span><span class="sxs-lookup"><span data-stu-id="c888a-135">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="c888a-136">Jeśli narzędzie jest hostowane na NuGet, można sprawdzić autora i statystyki, wyszukując narzędzie.</span><span class="sxs-lookup"><span data-stu-id="c888a-136">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="c888a-137">Instalowanie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="c888a-137">Install a global tool</span></span>

<span data-ttu-id="c888a-138">Aby zainstalować narzędzie jako narzędzie `-g` globalne, należy użyć lub `--global` opcji [instalacji narzędzia dotnet](dotnet-tool-install.md), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c888a-138">To install a tool as a global tool, use the `-g` or `--global` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="c888a-139">Dane wyjściowe pokazuje polecenie używane do wywołania narzędzia i zainstalowanej wersji, podobne do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="c888a-139">The output shows the command used to invoke the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

<span data-ttu-id="c888a-140">Domyślna lokalizacja plików binarnych narzędzia zależy od systemu operacyjnego:</span><span class="sxs-lookup"><span data-stu-id="c888a-140">The default location for a tool's binaries depends on the operating system:</span></span>

| <span data-ttu-id="c888a-141">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="c888a-141">OS</span></span>          | <span data-ttu-id="c888a-142">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="c888a-142">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="c888a-143">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="c888a-143">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="c888a-144">Windows</span><span class="sxs-lookup"><span data-stu-id="c888a-144">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="c888a-145">Ta lokalizacja jest dodawana do ścieżki użytkownika po pierwszym uruchomieniu zestawu SDK, dzięki czemu można wywołać narzędzia globalne z dowolnego katalogu bez określania lokalizacji narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c888a-145">This location is added to the user's path when the SDK is first run, so global tools can be invoked from any directory without specifying the tool location.</span></span>

<span data-ttu-id="c888a-146">Dostęp do narzędzi jest specyficzny dla użytkownika, a nie globalny.</span><span class="sxs-lookup"><span data-stu-id="c888a-146">Tool access is user-specific, not machine global.</span></span> <span data-ttu-id="c888a-147">Narzędzie globalne jest dostępne tylko dla użytkownika, który zainstalował narzędzie.</span><span class="sxs-lookup"><span data-stu-id="c888a-147">A global tool is only available to the user that installed the tool.</span></span>

### <a name="install-a-global-tool-in-a-custom-location"></a><span data-ttu-id="c888a-148">Instalowanie narzędzia globalnego w lokalizacji niestandardowej</span><span class="sxs-lookup"><span data-stu-id="c888a-148">Install a global tool in a custom location</span></span>

<span data-ttu-id="c888a-149">Aby zainstalować narzędzie jako narzędzie globalne w `--tool-path` lokalizacji niestandardowej, należy użyć opcji [instalacji narzędzia dotnet](dotnet-tool-install.md), jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="c888a-149">To install a tool as a global tool in a custom location, use the `--tool-path` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following examples.</span></span>

<span data-ttu-id="c888a-150">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="c888a-150">On Windows:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

<span data-ttu-id="c888a-151">W systemie Linux lub macOS:</span><span class="sxs-lookup"><span data-stu-id="c888a-151">On Linux or macOS:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

<span data-ttu-id="c888a-152">Zestaw SDK .NET Core nie powoduje automatycznego dodania tej lokalizacji do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="c888a-152">The .NET Core SDK doesn't add this location automatically to the PATH environment variable.</span></span> <span data-ttu-id="c888a-153">Aby [wywołać narzędzie ścieżki narzędzia,](#invoke-a-tool-path-tool)należy upewnić się, że polecenie jest dostępne przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="c888a-153">To [invoke a tool-path tool](#invoke-a-tool-path-tool), you have to make sure the command is available by using one of the following methods:</span></span>

* <span data-ttu-id="c888a-154">Dodaj katalog instalacyjny do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="c888a-154">Add the installation directory to the PATH environment variable.</span></span>
* <span data-ttu-id="c888a-155">Określ pełną ścieżkę do narzędzia podczas wywoływania go.</span><span class="sxs-lookup"><span data-stu-id="c888a-155">Specify the full path to the tool when you invoke it.</span></span>
* <span data-ttu-id="c888a-156">Wywołaj narzędzie z poziomu katalogu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c888a-156">Invoke the tool from within the installation directory.</span></span>

## <a name="install-a-local-tool"></a><span data-ttu-id="c888a-157">Instalowanie narzędzia lokalnego</span><span class="sxs-lookup"><span data-stu-id="c888a-157">Install a local tool</span></span>

<span data-ttu-id="c888a-158">**Dotyczy sdk .NET Core 3.0 i nowszych.**</span><span class="sxs-lookup"><span data-stu-id="c888a-158">**Applies to .NET Core 3.0 SDK and later.**</span></span>

<span data-ttu-id="c888a-159">Aby zainstalować narzędzie tylko dla dostępu lokalnego (dla bieżącego katalogu i podkatalogów), należy je dodać do pliku manifestu narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c888a-159">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a tool manifest file.</span></span> <span data-ttu-id="c888a-160">Aby utworzyć plik manifestu `dotnet new tool-manifest` narzędzia, uruchom polecenie:</span><span class="sxs-lookup"><span data-stu-id="c888a-160">To create a tool manifest file, run the `dotnet new tool-manifest` command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="c888a-161">To polecenie tworzy plik manifestu o nazwie *dotnet-tools.json* w katalogu *.config.*</span><span class="sxs-lookup"><span data-stu-id="c888a-161">This command creates a manifest file named *dotnet-tools.json* under the *.config* directory.</span></span> <span data-ttu-id="c888a-162">Aby dodać narzędzie lokalne do pliku manifestu, użyj polecenia install `--global` tool `--tool-path` [dotnet](dotnet-tool-install.md) i **pomiń** opcje i opcje, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c888a-162">To add a local tool to the manifest file, use the [dotnet tool install](dotnet-tool-install.md) command and **omit** the `--global` and `--tool-path` options, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay
```

<span data-ttu-id="c888a-163">Dane wyjściowe polecenia pokazuje, w którym pliku manifestu znajduje się nowo zainstalowane narzędzie, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c888a-163">The command output shows which manifest file the newly installed tool is in, similar to the following example:</span></span>

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

<span data-ttu-id="c888a-164">W poniższym przykładzie przedstawiono plik manifestu z zainstalowanymi dwoma narzędziami lokalnymi:</span><span class="sxs-lookup"><span data-stu-id="c888a-164">The following example shows a manifest file with two local tools installed:</span></span>

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

<span data-ttu-id="c888a-165">Zazwyczaj dodaje się narzędzie lokalne do katalogu głównego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="c888a-165">You typically add a local tool to the root directory of the repository.</span></span> <span data-ttu-id="c888a-166">Po zaewidencjonowanie w pliku manifestu do repozytorium deweloperzy, którzy wyewidencjonują kod z repozytorium, otrzymują najnowszy plik manifestu.</span><span class="sxs-lookup"><span data-stu-id="c888a-166">After you check in the manifest file to the repository, developers who check out code from the repository get the latest manifest file.</span></span> <span data-ttu-id="c888a-167">Aby zainstalować wszystkie narzędzia wymienione w pliku manifestu, uruchomią `dotnet tool restore` polecenie:</span><span class="sxs-lookup"><span data-stu-id="c888a-167">To install all of the tools listed in the manifest file, they run the `dotnet tool restore` command:</span></span>

```dotnetcli
dotnet tool restore
```

<span data-ttu-id="c888a-168">Dane wyjściowe wskazują, które narzędzia zostały przywrócone:</span><span class="sxs-lookup"><span data-stu-id="c888a-168">The output indicates which tools were restored:</span></span>

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a><span data-ttu-id="c888a-169">Instalowanie określonej wersji narzędzia</span><span class="sxs-lookup"><span data-stu-id="c888a-169">Install a specific tool version</span></span>

<span data-ttu-id="c888a-170">Aby zainstalować wersję wstępną lub określoną wersję narzędzia, określ `--version` numer wersji przy użyciu tej opcji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c888a-170">To install a pre-release version or a specific version of a tool, specify the version number by using the `--version` option, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a><span data-ttu-id="c888a-171">Korzystanie z narzędzia</span><span class="sxs-lookup"><span data-stu-id="c888a-171">Use a tool</span></span>

<span data-ttu-id="c888a-172">Polecenie, którego używasz do wywoływania narzędzia, może się różnić od nazwy instalowany pakiet.</span><span class="sxs-lookup"><span data-stu-id="c888a-172">The command that you use to invoke a tool may be different from the name of the package that you install.</span></span> <span data-ttu-id="c888a-173">Aby wyświetlić wszystkie narzędzia aktualnie zainstalowane na komputerze dla bieżącego użytkownika, użyj polecenia [listy narzędzi dotnet:](dotnet-tool-list.md)</span><span class="sxs-lookup"><span data-stu-id="c888a-173">To display all of the tools currently installed on the machine for the current user, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list
```

<span data-ttu-id="c888a-174">Dane wyjściowe pokazują wersję i polecenie każdego narzędzia, podobne do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="c888a-174">The output shows each tool's version and command, similar to the following example:</span></span>

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

<span data-ttu-id="c888a-175">Jak pokazano w tym przykładzie, na liście są wyświetlane narzędzia lokalne.</span><span class="sxs-lookup"><span data-stu-id="c888a-175">As shown in this example, the list shows local tools.</span></span> <span data-ttu-id="c888a-176">Aby wyświetlić narzędzia globalne, użyj `--global` tej opcji i zobacz `--tool-path` narzędzia ścieżki narzędzia, użyj tej opcji.</span><span class="sxs-lookup"><span data-stu-id="c888a-176">To see global tools, use the `--global` option, and to see tool-path tools, use the `--tool-path` option.</span></span>

### <a name="invoke-a-global-tool"></a><span data-ttu-id="c888a-177">Wywoływanie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="c888a-177">Invoke a global tool</span></span>

<span data-ttu-id="c888a-178">W przypadku narzędzi globalnych użyj polecenia narzędzia samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="c888a-178">For global tools, use the tool command by itself.</span></span> <span data-ttu-id="c888a-179">Na przykład, jeśli `dotnetsay` polecenie `dotnet-doc`jest lub , to jest to, co można użyć do wywołania polecenia:</span><span class="sxs-lookup"><span data-stu-id="c888a-179">For example, if the command is `dotnetsay` or `dotnet-doc`, that's what you use to invoke the command:</span></span>

```console
dotnetsay
dotnet-doc
```

<span data-ttu-id="c888a-180">Jeśli polecenie zaczyna się `dotnet-`od prefiksu, alternatywnym sposobem `dotnet` wywołania narzędzia jest użycie polecenia i pominięcie prefiksu polecenia narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c888a-180">If the command begins with the prefix `dotnet-`, an alternative way to invoke the tool is to use the `dotnet` command and omit the tool command prefix.</span></span> <span data-ttu-id="c888a-181">Na przykład, jeśli `dotnet-doc`polecenie jest , następujące polecenie wywołuje narzędzie:</span><span class="sxs-lookup"><span data-stu-id="c888a-181">For example, if the command is `dotnet-doc`, the following command invokes the tool:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="c888a-182">Jednak w poniższym scenariuszu `dotnet` nie można użyć polecenia do wywołania narzędzia globalnego:</span><span class="sxs-lookup"><span data-stu-id="c888a-182">However, in the following scenario you can't use the `dotnet` command to invoke a global tool:</span></span>

* <span data-ttu-id="c888a-183">Narzędzie globalne i narzędzie lokalne mają to `dotnet-`samo polecenie poprzedzone .</span><span class="sxs-lookup"><span data-stu-id="c888a-183">A global tool and a local tool have the same command prefixed by `dotnet-`.</span></span>
* <span data-ttu-id="c888a-184">Chcesz wywołać narzędzie globalne z katalogu, który jest w zakresie narzędzia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="c888a-184">You want to invoke the global tool from a directory that is in scope for the local tool.</span></span>

<span data-ttu-id="c888a-185">W tym `dotnet doc` scenariuszu i `dotnet dotnet-doc` wywołać narzędzie lokalne.</span><span class="sxs-lookup"><span data-stu-id="c888a-185">In this scenario, `dotnet doc` and `dotnet dotnet-doc` invoke the local tool.</span></span> <span data-ttu-id="c888a-186">Aby wywołać narzędzie globalne, użyj polecenia samodzielnie:</span><span class="sxs-lookup"><span data-stu-id="c888a-186">To invoke the global tool, use the command by itself:</span></span>

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a><span data-ttu-id="c888a-187">Wywoływanie narzędzia ścieżki narzędzia</span><span class="sxs-lookup"><span data-stu-id="c888a-187">Invoke a tool-path tool</span></span>

<span data-ttu-id="c888a-188">Aby wywołać narzędzie globalne, które `tool-path` jest zainstalowane przy użyciu tej opcji, upewnij się, że polecenie jest dostępne, jak wyjaśniono [wcześniej w tym artykule](#install-a-global-tool-in-a-custom-location).</span><span class="sxs-lookup"><span data-stu-id="c888a-188">To invoke a global tool that is installed by using the `tool-path` option, make sure the command is available, as explained [earlier in this article](#install-a-global-tool-in-a-custom-location).</span></span>

### <a name="invoke-a-local-tool"></a><span data-ttu-id="c888a-189">Wywoływanie narzędzia lokalnego</span><span class="sxs-lookup"><span data-stu-id="c888a-189">Invoke a local tool</span></span>

<span data-ttu-id="c888a-190">Aby wywołać narzędzie lokalne, należy `dotnet` użyć polecenia z poziomu katalogu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c888a-190">To invoke a local tool, you have to use the `dotnet` command from within the installation directory.</span></span> <span data-ttu-id="c888a-191">Można użyć formularza długiego (`dotnet tool run <COMMAND_NAME>`)`dotnet <COMMAND_NAME>`lub krótkiego formularza ( ), jak pokazano w poniższych przykładach:</span><span class="sxs-lookup"><span data-stu-id="c888a-191">You can use the long form (`dotnet tool run <COMMAND_NAME>`) or the short form (`dotnet <COMMAND_NAME>`), as shown in the following examples:</span></span>

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

<span data-ttu-id="c888a-192">Jeśli polecenie jest poprzedzone przez `dotnet-`, można dołączyć lub pominąć prefiks podczas wywoływania narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c888a-192">If the command is prefixed by `dotnet-`, you can include or omit the prefix when you invoke the tool.</span></span> <span data-ttu-id="c888a-193">Na przykład jeśli polecenie `dotnet-doc`jest , każdy z poniższych przykładów wywołuje narzędzie lokalne:</span><span class="sxs-lookup"><span data-stu-id="c888a-193">For example, if the command is `dotnet-doc`, any of the following examples invokes the local tool:</span></span>

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a><span data-ttu-id="c888a-194">Aktualizowanie narzędzia</span><span class="sxs-lookup"><span data-stu-id="c888a-194">Update a tool</span></span>

<span data-ttu-id="c888a-195">Aktualizacja narzędzia polega na odinstalowaniu i ponownym zainstalowaniu go za pomocą najnowszej stabilnej wersji.</span><span class="sxs-lookup"><span data-stu-id="c888a-195">Updating a tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="c888a-196">Aby zaktualizować narzędzie, użyj polecenia [aktualizacji narzędzia dotnet](dotnet-tool-update.md) z tą samą opcją, która została użyta do zainstalowania narzędzia:</span><span class="sxs-lookup"><span data-stu-id="c888a-196">To update a tool, use the [dotnet tool update](dotnet-tool-update.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

<span data-ttu-id="c888a-197">W przypadku narzędzia lokalnego zestaw SDK znajduje pierwszy plik manifestu zawierający identyfikator pakietu, patrząc w bieżącym katalogu i katalogach nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c888a-197">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span> <span data-ttu-id="c888a-198">Jeśli w żadnym pliku manifestu nie ma takiego identyfikatora pakietu, zestaw SDK dodaje nowy wpis do najbliższego pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="c888a-198">If there is no such package ID in any manifest file, the SDK adds a new entry to the closest manifest file.</span></span>

## <a name="uninstall-a-tool"></a><span data-ttu-id="c888a-199">Odinstalowywanie narzędzia</span><span class="sxs-lookup"><span data-stu-id="c888a-199">Uninstall a tool</span></span>

<span data-ttu-id="c888a-200">Usuń narzędzie za pomocą polecenia [odinstalowywania narzędzia dotnet](dotnet-tool-uninstall.md) z tą samą opcją, która została użyta do zainstalowania narzędzia:</span><span class="sxs-lookup"><span data-stu-id="c888a-200">Remove a tool by using the [dotnet tool uninstall](dotnet-tool-uninstall.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path<packagename>
dotnet tool uninstall <packagename>
```

<span data-ttu-id="c888a-201">W przypadku narzędzia lokalnego zestaw SDK znajduje pierwszy plik manifestu zawierający identyfikator pakietu, patrząc w bieżącym katalogu i katalogach nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c888a-201">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span>

## <a name="get-help-and-troubleshoot"></a><span data-ttu-id="c888a-202">Uzyskiwanie pomocy i rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="c888a-202">Get help and troubleshoot</span></span>

<span data-ttu-id="c888a-203">Aby uzyskać listę `dotnet tool` dostępnych poleceń, wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c888a-203">To get a list of available `dotnet tool` commands, enter the following command:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="c888a-204">Aby uzyskać instrukcje użycia narzędzia, wprowadź jedno z następujących poleceń lub zobacz witrynę sieci Web narzędzia:</span><span class="sxs-lookup"><span data-stu-id="c888a-204">To get tool usage instructions, enter one of the following commands or see the tool's website:</span></span>

```dotnetcli
<command> --help
dotnet <command> --help
```

<span data-ttu-id="c888a-205">Jeśli narzędzie nie może zostać zainstalowane lub uruchomione, zobacz [Rozwiązywanie problemów z używaniem narzędzia .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="c888a-205">If a tool fails to install or run, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c888a-206">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c888a-206">See also</span></span>

- [<span data-ttu-id="c888a-207">Samouczek: Tworzenie narzędzia .NET Core przy użyciu procesora CLI programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="c888a-207">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>](global-tools-how-to-create.md)
- [<span data-ttu-id="c888a-208">Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="c888a-208">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="c888a-209">Samouczek: Instalowanie i używanie lokalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="c888a-209">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
