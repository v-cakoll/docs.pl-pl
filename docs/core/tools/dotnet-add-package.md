---
title: polecenie dotnet add package
description: Polecenie "dotnet add package" zapewnia wygodną opcję dodawania odwołania do pakietu NuGet do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 8121539a50d2ac2837693ccc35581f7fde1d1fc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146609"
---
# <a name="dotnet-add-package"></a>dotnet add package

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet add package`- Dodaje odwołanie do pakietu do pliku projektu.

## <a name="synopsis"></a>Streszczenie

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>Opis

Polecenie `dotnet add package` zapewnia wygodną opcję dodawania odwołania do pakietu do pliku projektu. Po uruchomieniu polecenia, jest sprawdzenie zgodności, aby upewnić się, że pakiet jest zgodny z ramach w projekcie. Jeśli sprawdzanie przejdzie `<PackageReference>` pomyślnie, element jest dodawany do pliku projektu i uruchamiane jest [przywracanie dotnet.](dotnet-restore.md)

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

Na przykład `Newtonsoft.Json` dodanie do *ToDo.csproj* daje dane wyjściowe podobne do następującego przykładu:

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

Plik *ToDo.csproj* zawiera [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) teraz element pakietu, do którego się odwołuje.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a>Argumenty

- **`PROJECT`**

  Określa plik projektu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu jednego.

- **`PACKAGE_NAME`**

  Odwołanie do pakietu, aby dodać.

## <a name="options"></a>Opcje

- **`-f|--framework <FRAMEWORK>`**

  Dodaje odwołanie do pakietu tylko podczas określania określonej [struktury](../../standard/frameworks.md).

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Umożliwia polecenie, aby zatrzymać i czekać na dane wejściowe użytkownika lub akcji (na przykład, aby zakończyć uwierzytelnianie). Dostępne od sdk .NET Core 2.1, wersja 2.1.400 lub nowsza.

- **`-n|--no-restore`**

  Dodaje odwołanie do pakietu bez wykonywania podglądu przywracania i sprawdzania zgodności.

- **`--package-directory <PACKAGE_DIRECTORY>`**

  Katalog, w którym należy przywrócić pakiety. Domyślna lokalizacja przywracania pakietów znajduje się `%userprofile%\.nuget\packages` w systemie Windows oraz `~/.nuget/packages` w systemach macOS i Linux. Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowych w nuget](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).

- **`-s|--source <SOURCE>`**

  Źródło pakietu NuGet do użycia podczas operacji przywracania.

- **`-v|--version <VERSION>`**

  Wersja pakietu. Zobacz [NuGet przechowywanie wersji pakietu](https://docs.microsoft.com/nuget/reference/package-versioning).

## <a name="examples"></a>Przykłady

- Dodaj `Newtonsoft.Json` pakiet NuGet do projektu:

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- Dodaj określoną wersję pakietu do projektu:

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- Dodaj pakiet przy użyciu określonego źródła NuGet:

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a>Zobacz też

- [Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowych w NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [Przechowywanie wersji pakietu NuGet](https://docs.microsoft.com/nuget/reference/package-versioning)
