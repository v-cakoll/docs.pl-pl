---
title: Instalowanie szablonów zestawu SDK i zarządzanie nimi — .NET Core
description: Dowiedz się, jak instalować szablony .NET Core w systemach Windows, Linux i macOS.
author: thraka
ms.author: adegeo
ms.date: 04/24/2020
zone_pivot_groups: operating-systems-set-one
no-loc:
- dotnet new
- dotnet nuget add source
ms.openlocfilehash: 0a3c8655d55bf63de1e91337ce3a2ac399b07d0f
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200616"
---
# <a name="manage-net-project-and-item-templates"></a><span data-ttu-id="0e6ba-103">Zarządzanie szablonami projektów i elementów programu .NET</span><span class="sxs-lookup"><span data-stu-id="0e6ba-103">Manage .NET project and item templates</span></span>

<span data-ttu-id="0e6ba-104">Platforma .NET Core udostępnia system szablonów, który umożliwia użytkownikom instalowanie lub odinstalowywanie szablonów z programu NuGet, pliku pakietu NuGet lub katalogu systemu plików.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-104">.NET Core provides a template system that enables users to install or uninstall templates from NuGet, a NuGet package file, or a file system directory.</span></span> <span data-ttu-id="0e6ba-105">W tym artykule opisano sposób zarządzania szablonami .NET Core za pomocą interfejsu wiersza polecenia zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-105">This article describes how to manage .NET Core templates through the .NET Core SDK CLI.</span></span>

<span data-ttu-id="0e6ba-106">Aby uzyskać więcej informacji na temat tworzenia szablonów, zobacz [Samouczek: Tworzenie szablonów](../tutorials/cli-templates-create-item-template.md).</span><span class="sxs-lookup"><span data-stu-id="0e6ba-106">For more information about creating templates, see [Tutorial: Create templates](../tutorials/cli-templates-create-item-template.md).</span></span>

## <a name="install-template"></a><span data-ttu-id="0e6ba-107">Zainstaluj szablon</span><span class="sxs-lookup"><span data-stu-id="0e6ba-107">Install template</span></span>

<span data-ttu-id="0e6ba-108">Szablony są instalowane za pomocą [nowego](../tools/dotnet-new.md) zestawu SDK dotnet polecenia z `-i` parametrem.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-108">Templates are installed through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-i` parameter.</span></span> <span data-ttu-id="0e6ba-109">Możesz podać identyfikator pakietu NuGet szablonu lub folder zawierający pliki szablonów.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-109">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-hosted-package"></a><span data-ttu-id="0e6ba-110">Pakiet hostowany przez narzędzie NuGet</span><span class="sxs-lookup"><span data-stu-id="0e6ba-110">NuGet hosted package</span></span>

<span data-ttu-id="0e6ba-111">Szablony interfejsu wiersza polecenia platformy .NET są przekazywane do programu [NuGet](https://www.nuget.org/) w celu zapewnienia szerokiej dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-111">.NET CLI templates are uploaded to [NuGet](https://www.nuget.org/) for wide distribution.</span></span> <span data-ttu-id="0e6ba-112">Szablony mogą być również instalowane z prywatnego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-112">Templates can also be installed from a private feed.</span></span> <span data-ttu-id="0e6ba-113">Zamiast przekazywania szablonu do źródła danych NuGet, pliki szablonów *NUPKG* można rozpowszechniać i instalować ręcznie zgodnie z opisem w sekcji [lokalny pakiet NuGet](#local-nuget-package) .</span><span class="sxs-lookup"><span data-stu-id="0e6ba-113">Instead of uploading a template to a NuGet feed, *nupkg* template files can be distributed and manually installed, as described in the [Local NuGet package](#local-nuget-package) section.</span></span>

<span data-ttu-id="0e6ba-114">Aby uzyskać więcej informacji o konfigurowaniu kanałów informacyjnych NuGet, zobacz [Dodawanie źródła przez program dotnet NuGet](../tools/dotnet-nuget-add-source.md).</span><span class="sxs-lookup"><span data-stu-id="0e6ba-114">For more information about configuring NuGet feeds, see [dotnet nuget add source](../tools/dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="0e6ba-115">Aby zainstalować pakiet szablonów z domyślnego źródła danych NuGet, użyj `dotnet new -i {package-id}` polecenia:</span><span class="sxs-lookup"><span data-stu-id="0e6ba-115">To install a template pack from the default NuGet feed, use the `dotnet new -i {package-id}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates
```

<span data-ttu-id="0e6ba-116">Aby zainstalować pakiet szablonów z domyślnego kanału informacyjnego NuGet z określoną wersją, użyj `dotnet new -i {package-id}::{version}` polecenia:</span><span class="sxs-lookup"><span data-stu-id="0e6ba-116">To install a template pack from the default NuGet feed with a specific version, use the `dotnet new -i {package-id}::{version}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.2.6
```

### <a name="local-nuget-package"></a><span data-ttu-id="0e6ba-117">Lokalny pakiet NuGet</span><span class="sxs-lookup"><span data-stu-id="0e6ba-117">Local NuGet package</span></span>

<span data-ttu-id="0e6ba-118">Gdy tworzony jest pakiet szablonów, generowany jest plik *NUPKG* .</span><span class="sxs-lookup"><span data-stu-id="0e6ba-118">When a template pack is created, a *nupkg* file is generated.</span></span> <span data-ttu-id="0e6ba-119">Jeśli masz plik *NUPKG* zawierający szablony, możesz go zainstalować przy użyciu `dotnet new -i {path-to-package}` polecenia:</span><span class="sxs-lookup"><span data-stu-id="0e6ba-119">If you have a *nupkg* file containing templates, you can install it with the `dotnet new -i {path-to-package}` command:</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\Some.Templates.1.0.0.nupkg
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/Some.Templates.1.0.0.nupkg
```

::: zone-end

### <a name="folder"></a><span data-ttu-id="0e6ba-120">Folder</span><span class="sxs-lookup"><span data-stu-id="0e6ba-120">Folder</span></span>

<span data-ttu-id="0e6ba-121">Alternatywnie, aby zainstalować szablon z pliku *NUPKG* , można także zainstalować szablony z folderu bezpośrednio za pomocą `dotnet new -i {folder-path}` polecenia.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-121">As an alternative to installing template from a *nupkg* file, you can also install templates from a folder directly with the `dotnet new -i {folder-path}` command.</span></span> <span data-ttu-id="0e6ba-122">Określony folder jest traktowany jako identyfikator pakietu szablonów dla dowolnego odnalezionego szablonu.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-122">The folder specified is treated as the template pack identifier for any template found.</span></span> <span data-ttu-id="0e6ba-123">Zostanie zainstalowany każdy szablon znaleziony w hierarchii określonego folderu.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-123">Any template found in the specified folder's hierarchy is installed.</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\some-folder\
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/some-folder/
```

::: zone-end

<span data-ttu-id="0e6ba-124">`{folder-path}` Określone w poleceniu staną się identyfikatorem pakietu szablonów dla wszystkich znalezionych szablonów.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-124">The `{folder-path}` specified on the command becomes the template pack identifier for all templates found.</span></span> <span data-ttu-id="0e6ba-125">Jak określono w sekcji [szablony list](#list-templates) , można uzyskać listę szablonów zainstalowanych za pomocą `dotnet new -u` polecenia.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-125">As specified in the [List templates](#list-templates) section, you can get a list of templates installed with the `dotnet new -u` command.</span></span> <span data-ttu-id="0e6ba-126">W tym przykładzie identyfikator pakietu szablonów jest pokazywany jako folder używany do instalacji:</span><span class="sxs-lookup"><span data-stu-id="0e6ba-126">In this example, the template pack identifier is shown as the folder used for install:</span></span>

::: zone pivot="os-windows"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  /home/username/code/templates
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="uninstall-template"></a><span data-ttu-id="0e6ba-127">Odinstaluj szablon</span><span class="sxs-lookup"><span data-stu-id="0e6ba-127">Uninstall template</span></span>

<span data-ttu-id="0e6ba-128">Szablony są odinstalowywane za pomocą nowego zestawu SDK [dotnet](../tools/dotnet-new.md) polecenia `-u` z parametrem.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-128">Templates are uninstalled through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-u` parameter.</span></span> <span data-ttu-id="0e6ba-129">Możesz podać identyfikator pakietu NuGet szablonu lub folder zawierający pliki szablonów.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-129">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-package"></a><span data-ttu-id="0e6ba-130">Pakiet NuGet</span><span class="sxs-lookup"><span data-stu-id="0e6ba-130">NuGet package</span></span>

<span data-ttu-id="0e6ba-131">Po zainstalowaniu pakietu szablonów NuGet z poziomu źródła danych NuGet lub pliku *NUPKG* można go odinstalować, odwołując się do identyfikatora pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-131">After a NuGet template pack is installed, either from a NuGet feed or a *nupkg* file, you can uninstall it by referencing the NuGet package identifier.</span></span>

<span data-ttu-id="0e6ba-132">Aby odinstalować pakiet szablonów, użyj `dotnet new -u {package-id}` polecenia:</span><span class="sxs-lookup"><span data-stu-id="0e6ba-132">To uninstall a template pack, use the `dotnet new -u {package-id}` command:</span></span>

```dotnetcli
dotnet new -u Microsoft.DotNet.Web.Spa.ProjectTemplates
```

### <a name="folder"></a><span data-ttu-id="0e6ba-133">Folder</span><span class="sxs-lookup"><span data-stu-id="0e6ba-133">Folder</span></span>

<span data-ttu-id="0e6ba-134">Gdy szablony są instalowane za pomocą [ścieżki folderu](#folder), ścieżka folderu zostanie do identyfikatora pakietu szablonu.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-134">When templates are installed through a [folder path](#folder), the folder path becomes the template pack identifier.</span></span>

<span data-ttu-id="0e6ba-135">Aby odinstalować pakiet szablonów, użyj `dotnet new -u {package-folder-path}` polecenia:</span><span class="sxs-lookup"><span data-stu-id="0e6ba-135">To uninstall a template pack, use the `dotnet new -u {package-folder-path}` command:</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="list-templates"></a><span data-ttu-id="0e6ba-136">Szablony list</span><span class="sxs-lookup"><span data-stu-id="0e6ba-136">List templates</span></span>

<span data-ttu-id="0e6ba-137">Przy użyciu standardowego polecenia Odinstaluj bez identyfikatora pakietu, można wyświetlić listę zainstalowanych szablonów wraz z poleceniem, które Odinstalowuje każdy szablon.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-137">By using the standard uninstall command without a package identifier, you can see a list of installed templates along with the command that uninstalls each template.</span></span>

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

## <a name="install-templates-from-other-sdks"></a><span data-ttu-id="0e6ba-138">Instalowanie szablonów z innych zestawów SDK</span><span class="sxs-lookup"><span data-stu-id="0e6ba-138">Install templates from other SDKs</span></span>

<span data-ttu-id="0e6ba-139">Jeśli każda wersja zestawu SDK została zainstalowana sekwencyjnie, na przykład w przypadku zainstalowania zestawu SDK 2,0, zestawu SDK 2,1 i tak dalej, zostaną zainstalowane wszystkie szablony zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-139">If you've installed each version of the SDK sequentially, for example you installed SDK 2.0, then SDK 2.1, and so on, you'll have every SDK's templates installed.</span></span> <span data-ttu-id="0e6ba-140">Jeśli jednak zaczniesz od nowszej wersji zestawu SDK, na przykład 3,1, zostaną uwzględnione tylko szablony dla [wydań LTS (obsługa długoterminowa)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , które w momencie wydania zestawu SDK 3,1 to SDK 2,1 i SDK 3,1.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-140">However, if you start with a later SDK version, like 3.1, only the templates for [LTS (long term support) releases](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) are included, which at the time of the SDK 3.1 release is SDK 2.1 and SDK 3.1.</span></span> <span data-ttu-id="0e6ba-141">Szablony innych wersji nie są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-141">Templates for any other release aren't included.</span></span>

<span data-ttu-id="0e6ba-142">Szablony .NET Core są dostępne w programie NuGet i można je zainstalować podobnie jak każdy inny szablon.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-142">The .NET Core templates are available on NuGet, and you can install them like any other template.</span></span> <span data-ttu-id="0e6ba-143">Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu NuGet Hosted](#nuget-hosted-package).</span><span class="sxs-lookup"><span data-stu-id="0e6ba-143">For more information, see [Install NuGet hosted package](#nuget-hosted-package).</span></span>

| <span data-ttu-id="0e6ba-144">SDK</span><span class="sxs-lookup"><span data-stu-id="0e6ba-144">SDK</span></span>              | <span data-ttu-id="0e6ba-145">Identyfikator pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="0e6ba-145">NuGet Package Identifier</span></span>                                                                                                      |
|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0e6ba-146">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0e6ba-146">.NET Core 2.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.1) |
| <span data-ttu-id="0e6ba-147">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="0e6ba-147">.NET Core 2.2</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.2) |
| <span data-ttu-id="0e6ba-148">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0e6ba-148">.NET Core 3.0</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.0) |
| <span data-ttu-id="0e6ba-149">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="0e6ba-149">.NET Core 3.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.1) |
| <span data-ttu-id="0e6ba-150">ASP.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="0e6ba-150">ASP.NET Core 2.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.1)       |
| <span data-ttu-id="0e6ba-151">ASP.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="0e6ba-151">ASP.NET Core 2.2</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.2)       |
| <span data-ttu-id="0e6ba-152">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="0e6ba-152">ASP.NET Core 3.0</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.0)       |
| <span data-ttu-id="0e6ba-153">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="0e6ba-153">ASP.NET Core 3.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.1)       |

<span data-ttu-id="0e6ba-154">Na przykład zestaw .NET Core SDK zawiera szablony dla aplikacji konsoli przeznaczonej dla platformy .NET Core 2,1 i .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-154">For example, the .NET Core SDK includes templates for a console app targeting .NET Core 2.1 and .NET Core 3.1.</span></span> <span data-ttu-id="0e6ba-155">Jeśli chcesz określić platformę .NET Core 3,0, musisz zainstalować szablony 3,0.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-155">If you wanted to target .NET Core 3.0, you would need to install the 3.0 templates.</span></span>

01. <span data-ttu-id="0e6ba-156">Spróbuj utworzyć aplikację, która jest przeznaczona dla platformy .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-156">Try creating an app that targets .NET Core 3.0.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="0e6ba-157">Jeśli zostanie wyświetlony komunikat o błędzie, należy zainstalować szablony.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-157">If you see an error message, you need to install the templates.</span></span>

    > <span data-ttu-id="0e6ba-158">Nie można znaleźć zainstalowanego szablonu zgodnego z danymi wejściowymi, wyszukiwanie w trybie online dla jednego z nich...</span><span class="sxs-lookup"><span data-stu-id="0e6ba-158">Couldn't find an installed template that matches the input, searching online for one that does...</span></span>

01. <span data-ttu-id="0e6ba-159">Zainstaluj szablony projektów platformy .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-159">Install the .NET Core 3.0 project templates.</span></span>

    ```dotnetcli
    dotnet new -i Microsoft.DotNet.Common.ProjectTemplates.3.0
    ```

01. <span data-ttu-id="0e6ba-160">Spróbuj utworzyć aplikację po raz drugi.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-160">Try creating the app a second time.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="0e6ba-161">Powinien zostać wyświetlony komunikat informujący o tym, że projekt został utworzony.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-161">And you should see a message indicating the project was created.</span></span>

    > <span data-ttu-id="0e6ba-162">Tworzenie szablonu "Aplikacja konsolowa" zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-162">The template "Console Application" was created successfully.</span></span>
    >
    > <span data-ttu-id="0e6ba-163">Trwa przetwarzanie akcji po utworzeniu... Trwa uruchamianie "dotnet restore" w path-to-Project-File. csproj... Trwa Określanie projektów do przywrócenia... Ukończono przywracanie w 1,05 s dla Path-to-Project-File. csproj.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-163">Processing post-creation actions... Running 'dotnet restore' on path-to-project-file.csproj... Determining projects to restore... Restore completed in 1.05 sec for path-to-project-file.csproj.</span></span>
    >
    > <span data-ttu-id="0e6ba-164">Przywracanie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="0e6ba-164">Restore succeeded.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e6ba-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e6ba-165">See also</span></span>

- [<span data-ttu-id="0e6ba-166">Samouczek: Tworzenie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="0e6ba-166">Tutorial: Create an item template</span></span>](../tutorials/cli-templates-create-item-template.md)
- [dotnet new](../tools/dotnet-new.md)
- [dotnet nuget add source](../tools/dotnet-nuget-add-source.md)
