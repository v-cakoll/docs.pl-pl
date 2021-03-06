---
title: polecenie dotnet Add Package
description: Polecenie "dotnet Add Package" udostępnia wygodną opcję dodawania odwołania do pakietu NuGet do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: bc79fe8adf5f775ddce62f3877a8de945c6a18ab
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840900"
---
# <a name="dotnet-add-package"></a>dotnet add package

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet add package`-Dodaje odwołanie do pakietu do pliku projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a>Opis

`dotnet add package`Polecenie udostępnia wygodną opcję dodawania odwołania do pakietu do pliku projektu. Po uruchomieniu polecenia jest sprawdzanie zgodności, aby upewnić się, że pakiet jest zgodny z strukturami w projekcie. Jeśli sprawdzanie przebiega, `<PackageReference>` element jest dodawany do pliku projektu i [dotnet Restore](dotnet-restore.md) jest uruchamiany.

Na przykład dodanie `Newtonsoft.Json` do zadania do *zrobienia. csproj* generuje dane wyjściowe podobne do następującego przykładu:

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

Plik do *zrobienia. csproj* zawiera teraz [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element dla przywoływanego pakietu.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a>Przywracanie niejawne

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Argumenty

- **`PROJECT`**

  Określa plik projektu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.

- **`PACKAGE_NAME`**

  Odwołanie do pakietu do dodania.

## <a name="options"></a>Opcje

- **`-f|--framework <FRAMEWORK>`**

  Dodaje odwołanie do pakietu tylko w przypadku określania konkretnej [struktury](../../standard/frameworks.md).

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład w celu ukończenia uwierzytelniania). Dostępne od wersji .NET Core 2,1 SDK, wersja 2.1.400 lub nowsza.

- **`-n|--no-restore`**

  Dodaje odwołanie do pakietu bez wykonywania podglądu przywracania i sprawdzania zgodności.

- **`--package-directory <PACKAGE_DIRECTORY>`**

  Katalog, w którym mają zostać przywrócone pakiety. Domyślna lokalizacja przywracania pakietu znajduje się `%userprofile%\.nuget\packages` w systemach Windows i `~/.nuget/packages` Linux. Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowymi w pakiecie NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).

- **`-s|--source <SOURCE>`**

  Identyfikator URI źródła pakietu NuGet do użycia podczas operacji przywracania.

- **`-v|--version <VERSION>`**

  Wersja pakietu. Zobacz [przechowywanie wersji pakietów NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).

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

## <a name="see-also"></a>Zobacz także

- [Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowymi w pakiecie NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [Przechowywanie wersji pakietów NuGet](https://docs.microsoft.com/nuget/reference/package-versioning)
