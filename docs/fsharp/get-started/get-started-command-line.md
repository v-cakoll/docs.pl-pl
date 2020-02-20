---
title: Wprowadzenie do F# narzędzia wiersza polecenia
description: Dowiedz się, jak utworzyć proste rozwiązanie z obsługą F# kilku projektów przy użyciu interfejs wiersza polecenia platformy .NET Core w dowolnym systemie operacyjnym (Windows, MacOS lub Linux).
ms.date: 03/26/2018
ms.openlocfilehash: 6f67314f49150e20b18734f21f24daa3ce856922
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504146"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Wprowadzenie do programu F# z interfejs wiersza polecenia platformy .NET Core

W tym artykule opisano, jak rozpocząć pracę z F# dowolnym systemem operacyjnym (Windows, MacOS lub Linux) przy użyciu interfejs wiersza polecenia platformy .NET Core. Odbywa się to przez utworzenie rozwiązania obejmującego wiele projektów z biblioteką klas, która jest wywoływana przez aplikację konsolową.

## <a name="prerequisites"></a>Wymagania wstępne

Aby rozpocząć, należy zainstalować najnowszą [zestaw .NET Core SDK](https://dotnet.microsoft.com/download).

W tym artykule przyjęto założenie, że wiesz, jak używać wiersza polecenia i mieć preferowany Edytor tekstu. Jeśli nie jest już używany, [Visual Studio Code](get-started-vscode.md) jest doskonałym rozwiązaniem jako edytor tekstu dla F#.

## <a name="build-a-simple-multi-project-solution"></a>Tworzenie prostego rozwiązania z obsługą kilku projektów

Otwórz wiersz polecenia/Terminal i użyj polecenia [dotnet New](../../core/tools/dotnet-new.md) , aby utworzyć nowy plik rozwiązania o nazwie `FSNetCore`:

```dotnetcli
dotnet new sln -o FSNetCore
```

Następująca struktura katalogów jest generowana po uruchomieniu poprzedniego polecenia:

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Napisz bibliotekę klas

Zmień katalogi na *FSNetCore*.

Użyj `dotnet new` polecenie, Utwórz projekt biblioteki klas w folderze **src** o nazwie Library.

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
```

Następująca struktura katalogów jest generowana po uruchomieniu poprzedniego polecenia:

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Zastąp zawartość `Library.fs` następującym kodem:

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

Dodaj pakiet NuGet Newtonsoft. JSON do projektu biblioteki.

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Dodaj projekt `Library` do rozwiązania `FSNetCore` za pomocą polecenia [dotnet sln Add](../../core/tools/dotnet-sln.md) :

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

Uruchom `dotnet build`, aby skompilować projekt. Nierozwiązane zależności zostaną przywrócone podczas kompilowania.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Napisz aplikację konsolową, która używa biblioteki klas

Użyj `dotnet new` polecenie, Utwórz aplikację konsolową w folderze **src** o nazwie App.

```dotnetcli
dotnet new console -lang "F#" -o src/App
```

Następująca struktura katalogów jest generowana po uruchomieniu poprzedniego polecenia:

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        ├── App
        │   ├── App.fsproj
        │   ├── Program.fs
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Zastąp zawartość pliku `Program.fs` następującym kodem:

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    argv
    |> Array.map getJsonNetJson
    |> Array.iter (printfn "%s")

    0 // return an integer exit code
```

Dodaj odwołanie do projektu `Library` przy użyciu [dodatku dotnet Dodaj odwołanie](../../core/tools/dotnet-add-reference.md).

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Dodaj projekt `App` do rozwiązania `FSNetCore` za pomocą polecenia `dotnet sln add`:

```dotnetcli
dotnet sln add src/App/App.fsproj
```

Przywróć zależności NuGet, `dotnet restore` i uruchom `dotnet build` w celu skompilowania projektu.

Zmień katalog na projekt konsoli `src/App` i Uruchom projekt przekazywać `Hello World` jako argumenty:

```dotnetcli
cd src/App
dotnet run Hello World
```

Powinny zostać wyświetlone następujące wyniki:

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a>Następne kroki

Następnie zapoznaj się z [przewodnikiem F# ](../tour.md) , aby dowiedzieć się F# więcej o różnych funkcjach.
