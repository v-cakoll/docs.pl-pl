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
# <a name="manage-net-project-and-item-templates"></a>Zarządzanie szablonami projektów i elementów programu .NET

Platforma .NET Core udostępnia system szablonów, który umożliwia użytkownikom instalowanie lub odinstalowywanie szablonów z programu NuGet, pliku pakietu NuGet lub katalogu systemu plików. W tym artykule opisano sposób zarządzania szablonami .NET Core za pomocą interfejsu wiersza polecenia zestaw .NET Core SDK.

Aby uzyskać więcej informacji na temat tworzenia szablonów, zobacz [Samouczek: Tworzenie szablonów](../tutorials/cli-templates-create-item-template.md).

## <a name="install-template"></a>Zainstaluj szablon

Szablony są instalowane za pomocą [nowego](../tools/dotnet-new.md) zestawu SDK dotnet polecenia z `-i` parametrem. Możesz podać identyfikator pakietu NuGet szablonu lub folder zawierający pliki szablonów.

### <a name="nuget-hosted-package"></a>Pakiet hostowany przez narzędzie NuGet

Szablony interfejsu wiersza polecenia platformy .NET są przekazywane do programu [NuGet](https://www.nuget.org/) w celu zapewnienia szerokiej dystrybucji. Szablony mogą być również instalowane z prywatnego źródła danych. Zamiast przekazywania szablonu do źródła danych NuGet, pliki szablonów *NUPKG* można rozpowszechniać i instalować ręcznie zgodnie z opisem w sekcji [lokalny pakiet NuGet](#local-nuget-package) .

Aby uzyskać więcej informacji o konfigurowaniu kanałów informacyjnych NuGet, zobacz [Dodawanie źródła przez program dotnet NuGet](../tools/dotnet-nuget-add-source.md).

Aby zainstalować pakiet szablonów z domyślnego źródła danych NuGet, użyj `dotnet new -i {package-id}` polecenia:

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates
```

Aby zainstalować pakiet szablonów z domyślnego kanału informacyjnego NuGet z określoną wersją, użyj `dotnet new -i {package-id}::{version}` polecenia:

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.2.6
```

### <a name="local-nuget-package"></a>Lokalny pakiet NuGet

Gdy tworzony jest pakiet szablonów, generowany jest plik *NUPKG* . Jeśli masz plik *NUPKG* zawierający szablony, możesz go zainstalować przy użyciu `dotnet new -i {path-to-package}` polecenia:

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

### <a name="folder"></a>Folder

Alternatywnie, aby zainstalować szablon z pliku *NUPKG* , można także zainstalować szablony z folderu bezpośrednio za pomocą `dotnet new -i {folder-path}` polecenia. Określony folder jest traktowany jako identyfikator pakietu szablonów dla dowolnego odnalezionego szablonu. Zostanie zainstalowany każdy szablon znaleziony w hierarchii określonego folderu.

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

`{folder-path}` Określone w poleceniu staną się identyfikatorem pakietu szablonów dla wszystkich znalezionych szablonów. Jak określono w sekcji [szablony list](#list-templates) , można uzyskać listę szablonów zainstalowanych za pomocą `dotnet new -u` polecenia. W tym przykładzie identyfikator pakietu szablonów jest pokazywany jako folder używany do instalacji:

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

## <a name="uninstall-template"></a>Odinstaluj szablon

Szablony są odinstalowywane za pomocą nowego zestawu SDK [dotnet](../tools/dotnet-new.md) polecenia `-u` z parametrem. Możesz podać identyfikator pakietu NuGet szablonu lub folder zawierający pliki szablonów.

### <a name="nuget-package"></a>Pakiet NuGet

Po zainstalowaniu pakietu szablonów NuGet z poziomu źródła danych NuGet lub pliku *NUPKG* można go odinstalować, odwołując się do identyfikatora pakietu NuGet.

Aby odinstalować pakiet szablonów, użyj `dotnet new -u {package-id}` polecenia:

```dotnetcli
dotnet new -u Microsoft.DotNet.Web.Spa.ProjectTemplates
```

### <a name="folder"></a>Folder

Gdy szablony są instalowane za pomocą [ścieżki folderu](#folder), ścieżka folderu zostanie do identyfikatora pakietu szablonu.

Aby odinstalować pakiet szablonów, użyj `dotnet new -u {package-folder-path}` polecenia:

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

## <a name="list-templates"></a>Szablony list

Przy użyciu standardowego polecenia Odinstaluj bez identyfikatora pakietu, można wyświetlić listę zainstalowanych szablonów wraz z poleceniem, które Odinstalowuje każdy szablon.

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

## <a name="install-templates-from-other-sdks"></a>Instalowanie szablonów z innych zestawów SDK

Jeśli każda wersja zestawu SDK została zainstalowana sekwencyjnie, na przykład w przypadku zainstalowania zestawu SDK 2,0, zestawu SDK 2,1 i tak dalej, zostaną zainstalowane wszystkie szablony zestawu SDK. Jeśli jednak zaczniesz od nowszej wersji zestawu SDK, na przykład 3,1, zostaną uwzględnione tylko szablony dla [wydań LTS (obsługa długoterminowa)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , które w momencie wydania zestawu SDK 3,1 to SDK 2,1 i SDK 3,1. Szablony innych wersji nie są uwzględniane.

Szablony .NET Core są dostępne w programie NuGet i można je zainstalować podobnie jak każdy inny szablon. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu NuGet Hosted](#nuget-hosted-package).

| SDK              | Identyfikator pakietu NuGet                                                                                                      |
|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| .NET Core 2.1    | [`Microsoft.DotNet.Common.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.1) |
| .NET Core 2.2    | [`Microsoft.DotNet.Common.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.2) |
| .NET Core 3.0    | [`Microsoft.DotNet.Common.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.0) |
| .NET Core 3,1    | [`Microsoft.DotNet.Common.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.1) |
| ASP.NET Core 2,1 | [`Microsoft.DotNet.Web.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.1)       |
| ASP.NET Core 2,2 | [`Microsoft.DotNet.Web.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.2)       |
| ASP.NET Core 3,0 | [`Microsoft.DotNet.Web.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.0)       |
| ASP.NET Core 3,1 | [`Microsoft.DotNet.Web.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.1)       |

Na przykład zestaw .NET Core SDK zawiera szablony dla aplikacji konsoli przeznaczonej dla platformy .NET Core 2,1 i .NET Core 3,1. Jeśli chcesz określić platformę .NET Core 3,0, musisz zainstalować szablony 3,0.

01. Spróbuj utworzyć aplikację, która jest przeznaczona dla platformy .NET Core 3,0.

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    Jeśli zostanie wyświetlony komunikat o błędzie, należy zainstalować szablony.

    > Nie można znaleźć zainstalowanego szablonu zgodnego z danymi wejściowymi, wyszukiwanie w trybie online dla jednego z nich...

01. Zainstaluj szablony projektów platformy .NET Core 3,0.

    ```dotnetcli
    dotnet new -i Microsoft.DotNet.Common.ProjectTemplates.3.0
    ```

01. Spróbuj utworzyć aplikację po raz drugi.

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    Powinien zostać wyświetlony komunikat informujący o tym, że projekt został utworzony.

    > Tworzenie szablonu "Aplikacja konsolowa" zakończyło się pomyślnie.
    >
    > Trwa przetwarzanie akcji po utworzeniu... Trwa uruchamianie "dotnet restore" w path-to-Project-File. csproj... Trwa Określanie projektów do przywrócenia... Ukończono przywracanie w 1,05 s dla Path-to-Project-File. csproj.
    >
    > Przywracanie powiodło się.

## <a name="see-also"></a>Zobacz także

- [Samouczek: Tworzenie szablonu elementu](../tutorials/cli-templates-create-item-template.md)
- [dotnet new](../tools/dotnet-new.md)
- [dotnet nuget add source](../tools/dotnet-nuget-add-source.md)
