---
title: polecenia DotNet Dodaj pakiet — polecenie
description: Polecenie "dotnet Dodaj pakiet" zapewnia wygodny sposób, aby dodać odwołanie do pakietu NuGet do projektu.
ms.date: 04/24/2019
ms.openlocfilehash: 79059e062368fc9c4b6b8cb31740fdf13ea2b9ca
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751411"
---
# <a name="dotnet-add-package"></a>polecenia DotNet Dodaj pakiet

**Ten artykuł dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet add package` -Dodaje odwołania do pakietu do pliku projektu.

## <a name="synopsis"></a>Streszczenie

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>Opis

`dotnet add package` Polecenia oferuje wygodne możliwość dodania odwołania do pakietu do pliku projektu. Po uruchomieniu polecenia, istnieje sprawdzania zgodności w celu zapewnienia, że pakiet jest zgodna ze strukturami w projekcie. Jeśli sprawdzenie zakończy się pomyślnie, `<PackageReference>` element zostanie dodany do pliku projektu i [dotnet restore](dotnet-restore.md) jest uruchamiany.

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

Na przykład dodanie `Newtonsoft.Json` do *ToDo.csproj* generuje dane wyjściowe podobne do poniższego przykładu:

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
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

*ToDo.csproj* plik zawiera teraz [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) element dla odpowiedniego pakietu.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a>Argumenty

* **`PROJECT`**

  Określa plik projektu. Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.

* **`PACKAGE_NAME`**

  Odwołania pakietu do dodania.

## <a name="options"></a>Opcje

* **`-f|--framework <FRAMEWORK>`**

  Dodaje odwołanie do pakietu tylko wtedy, gdy przeznaczonych dla określonego [framework](../../standard/frameworks.md).

* **`-h|--help`**

  Drukuje krótki pomoc dotyczącą polecenia.

* **`--interactive`**

  Umożliwia polecenie, aby zatrzymać i czeka na dane wejściowe użytkownika lub akcji (na przykład w celu ukończenia uwierzytelniania). Dostępne od .NET Core SDK 2.1, wersja 2.1.400 lub nowszej.

* **`-n|--no-restore`**

  Dodaje odwołanie do pakietu bez sprawdzanie przywracania (wersja zapoznawcza) i zgodności.

* **`--package-directory <PACKAGE_DIRECTORY>`**

  Katalog miejsca w celu przywrócenia pakietów.

* **`-s|--source <SOURCE>`**

  Źródło pakietu NuGet, która ma być używany podczas operacji przywracania.

* **`-v|--version <VERSION>`**

  Wersja pakietu.

## <a name="examples"></a>Przykłady

* Dodaj `Newtonsoft.Json` pakiet NuGet do projektu:

  ```console
  dotnet add package Newtonsoft.Json
  ```

* Dodaj określoną wersję pakietu do projektu:

  ```console
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

* Dodaj pakiet przy użyciu określonego źródła NuGet:

  ```console
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```