---
title: dotnet dodaj pakiet, polecenie
description: Polecenie 'dotnet add package' zapewnia wygodną opcję dodawania odwołania do pakietu NuGet do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 1d57aed59ccd45417c88f9b6a2f9dd768fda9b58
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102856"
---
# <a name="dotnet-add-package"></a>dotnet add package

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet add package`- Dodaje odwołanie do pakietu do pliku projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet add package` zapewnia wygodną opcję dodawania odwołania do pakietu do pliku projektu. Po uruchomieniu polecenia, istnieje sprawdzenie zgodności, aby upewnić się, że pakiet jest zgodny z platformami w projekcie. Jeśli sprawdzanie przejdzie, `<PackageReference>` element jest dodawany do pliku projektu i [dotnet restore](dotnet-restore.md) jest uruchamiany.

Na przykład `Newtonsoft.Json` dodanie do *pliku ToDo.csproj* tworzy dane wyjściowe podobne do następującego przykładu:

```console
Writing C:\Users\me\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

Plik *ToDo.csproj* zawiera [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) teraz element pakietu, do którego istnieje odwołanie.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a>Niejawne przywracanie

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Argumenty

- **`PROJECT`**

  Określa plik projektu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla jednego.

- **`PACKAGE_NAME`**

  Odwołanie do pakietu, aby dodać.

## <a name="options"></a>Opcje

- **`-f|--framework <FRAMEWORK>`**

  Dodaje odwołanie do pakietu tylko wtedy, gdy kierowanie określonej [struktury](../../standard/frameworks.md).

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania). Dostępne od .NET Core 2.1 SDK, wersja 2.1.400 lub nowsza.

- **`-n|--no-restore`**

  Dodaje odwołanie do pakietu bez wykonywania sprawdzania podglądu przywracania i zgodności.

- **`--package-directory <PACKAGE_DIRECTORY>`**

  Katalog, w którym można przywrócić pakiety. Domyślna lokalizacja przywracania pakietu jest `%userprofile%\.nuget\packages` w systemie Windows oraz `~/.nuget/packages` na komputerach macOS i Linux. Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowymi w nuget](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).

- **`-s|--source <SOURCE>`**

  Źródło pakietu NuGet do użycia podczas operacji przywracania.

- **`-v|--version <VERSION>`**

  Wersja pakietu. Zobacz [NuGet wersji pakietu](https://docs.microsoft.com/nuget/reference/package-versioning).

## <a name="examples"></a>Przykłady

- Dodaj `Newtonsoft.Json` pakiet NuGet do projektu:

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- Dodawanie określonej wersji pakietu do projektu:

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- Dodaj pakiet przy użyciu określonego źródła NuGet:

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a>Zobacz też

- [Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowymi w nuget](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [Przechowywanie wersji pakietu NuGet](https://docs.microsoft.com/nuget/reference/package-versioning)
