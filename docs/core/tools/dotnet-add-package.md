---
title: polecenia DotNet Dodaj polecenie pakietu — interfejs wiersza polecenia platformy .NET Core
description: Polecenie "dotnet Dodaj pakiet" zapewnia wygodny sposób, aby dodać odwołanie do pakietu NuGet do projektu.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 31dda9dbb101238b3a33d8b0d9a17765744480e0
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244396"
---
# <a name="dotnet-add-package"></a>polecenia DotNet Dodaj pakiet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet add package` -Dodaje odwołania do pakietu do pliku projektu.

## <a name="synopsis"></a>Streszczenie

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>Opis

`dotnet add package` Polecenia oferuje wygodne możliwość dodania odwołania do pakietu do pliku projektu. Po uruchomieniu polecenia, istnieje sprawdzania zgodności w celu zapewnienia, że pakiet jest zgodna ze strukturami w projekcie. Jeśli sprawdzenie zakończy się pomyślnie, `<PackageReference>` element zostanie dodany do pliku projektu i [dotnet restore](dotnet-restore.md) jest uruchamiany.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Na przykład dodanie `Newtonsoft.Json` do *ToDo.csproj* generuje dane wyjściowe podobne do poniższego przykładu:

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

*ToDo.csproj* plik zawiera teraz [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) element dla odpowiedniego pakietu.

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a>Argumenty

`PROJECT`

Określa plik projektu. Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.

`PACKAGE_NAME`

Odwołania pakietu do dodania.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-f|--framework <FRAMEWORK>`

Dodaje odwołanie do pakietu tylko wtedy, gdy przeznaczonych dla określonego [framework](../../standard/frameworks.md).

`-n|--no-restore`

Dodaje odwołanie do pakietu bez sprawdzanie przywracania (wersja zapoznawcza) i zgodności.

`--package-directory <PACKAGE_DIRECTORY>`

Przywraca pakietu w określonym katalogu.

`-s|--source <SOURCE>`

Używa określonego źródła pakietu NuGet podczas operacji przywracania.

`-v|--version <VERSION>`

Wersja pakietu.

## <a name="examples"></a>Przykłady

Dodaj `Newtonsoft.Json` pakiet NuGet do projektu:

`dotnet add package Newtonsoft.Json`

Dodaj określoną wersję pakietu do projektu:

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

Dodaj pakiet przy użyciu określonego źródła NuGet:

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
