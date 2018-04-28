---
title: DotNet Dodaj polecenie pakietu - .NET Core interfejsu wiersza polecenia
description: Polecenie "dotnet Dodawanie pakietu" zapewnia to wygodny sposób, aby dodać odwołanie pakiet NuGet do projektu.
author: mairaw
ms.author: mairaw
ms.date: 08/11/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 3a8752ff83e069d21ebbda346efef34b17360e3b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-add-package"></a>DotNet Dodaj pakiet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet add package` -Dodaje pakiet odwołanie do pliku projektu.

## <a name="synopsis"></a>Streszczenie

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]`

## <a name="description"></a>Opis

`dotnet add package` Polecenie zapewnia to wygodny sposób, aby dodać pakiet odwołanie do pliku projektu. Po uruchomieniu polecenia jest sprawdzenie zgodności, aby upewnić się, że pakiet jest zgodny z platform w projekcie. Jeśli sprawdzenie zakończy się pomyślnie, `<PackageReference>` element zostanie dodany do pliku projektu i [przywracania dotnet](dotnet-restore.md) jest uruchamiany.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Na przykład dodać `Newtonsoft.Json` do *ToDo.csproj* generuje dane wyjściowe podobne do poniższego przykładu:

```
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

*ToDo.csproj* plik zawiera teraz [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) elementu dla odpowiedniego pakietu.

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

Drukuje krótkich pomocy dla polecenia.

`-v|--version <VERSION>`

Wersja pakietu.

`-f|--framework <FRAMEWORK>`

Dodaje odwołanie do pakietu, tylko gdy jest określony [framework](../../standard/frameworks.md).

`-n|--no-restore`

Dodaje odwołanie do pakietu bez sprawdzanie przywracania Podgląd i zgodności.

`-s|--source <SOURCE>`

Korzysta z określonego źródła pakietu NuGet podczas operacji przywracania.

`--package-directory <PACKAGE_DIRECTORY>`

Przywraca pakietu do określonego katalogu.

## <a name="examples"></a>Przykłady

Dodaj `Newtonsoft.Json` pakiet NuGet do projektu:

`dotnet add package Newtonsoft.Json`

Dodawanie określonej wersji pakietu do projektu:

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

Dodaj pakiet przy użyciu określonego źródła NuGet:

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
