---
title: 'Wprowadzenie do języka F # z narzędzi wiersza polecenia'
description: 'Dowiedz się, jak rozbudowywać prostym rozwiązaniem wielu projektów F # za pomocą interfejsu wiersza polecenia platformy .NET Core w dowolnym systemie operacyjnym (Windows, system macOs lub Linux).'
ms.date: 03/26/2018
ms.openlocfilehash: 35ec2313742a0b14c92f3de2662a16aff389b214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Rozpoczynanie pracy z F # z poziomu interfejsu wiersza polecenia platformy .NET Core

W tym artykule opisano, jak możesz rozpocząć pracę z F # w dowolnym systemie operacyjnym (Windows, system macOS lub Linux) z poziomu interfejsu wiersza polecenia platformy .NET Core. Przechodzi ona przez tworzenie wielu projektów rozwiązania z biblioteki klas, który jest wywoływany przez aplikacji konsoli.

## <a name="prerequisites"></a>Wymagania wstępne

Aby rozpocząć, należy zainstalować [.NET Core SDK w wersji 1.0 lub nowszej](https://www.microsoft.com/net/download/). Ponieważ obsługuje on instalacji side-by-side jest niepotrzebna odinstalować poprzedniej wersji programu .NET Core SDK.

W tym artykule trzeba wiedzieć, jak za pomocą wiersza polecenia i preferowany tekst edytora. Jeśli nie używasz już, [Visual Studio Code](https://code.visualstudio.com) to doskonałe rozwiązanie edytorem tekstu w F #. Aby uzyskać atrakcyjne funkcje, takie jak IntelliSense, lepiej wyróżnianie składni i inne, możesz pobrać [Ionide rozszerzenia](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).

## <a name="build-a-simple-multi-project-solution"></a>Tworzenie prostego rozwiązania wielu projektów

Otwórz wiersz polecenia/terminal i użyj [dotnet nowe](../../core/tools/dotnet-new.md) polecenie, aby utworzyć nowy plik rozwiązania o nazwie `FSNetCore`:

```
dotnet new sln -o FSNetCore
```

Następującą strukturę katalogów jest generowany po użyciu poprzedniego polecenia:

```
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Zapis biblioteki klas

Przejdź do *FSNetCore*.

Użyj `dotnet new` polecenia, tworzenie projektu biblioteki klas w **src** folder o nazwie biblioteki.

```
dotnet new lib -lang F# -o src/Library
```

Następującą strukturę katalogów jest generowany po użyciu poprzedniego polecenia:

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Zastąp zawartość `Library.fs` z następującym kodem:

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

Dodaj pakiet Newtonsoft.Json NuGet do projektu biblioteki.

```
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Dodaj `Library` projektu do `FSNetCore` przy użyciu rozwiązania [dodać dotnet sln](../../core/tools/dotnet-sln.md) polecenia:

```
dotnet sln add src/Library/Library.fsproj
```

Przywróć zależności NuGet przy użyciu `dotnet restore` polecenia ([patrz Uwaga](#dotnet-restore-note)) i uruchom `dotnet build` Aby skompilować projekt.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Pisanie aplikacji konsoli, który wykorzystuje biblioteki klas

Użyj `dotnet new` polecenia, Utwórz aplikację konsoli w **src** folder o nazwie aplikacji.

```
dotnet new console -lang F# -o src/App
```

Następującą strukturę katalogów jest generowany po użyciu poprzedniego polecenia:

```
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

Zastąp zawartość `Program.fs` pliku następującym kodem:

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

Dodaj odwołanie do `Library` projektu za pomocą [dotnet Dodaj odwołanie](../../core/tools/dotnet-add-reference.md).

```
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Dodaj `App` projektu do `FSNetCore` przy użyciu rozwiązania `dotnet sln add` polecenia:

```
dotnet sln add src/App/App.fsproj
```

Przywróć zależności NuGet `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) i uruchom `dotnet build` Aby skompilować projekt.

Zmień katalog na `src/App` konsoli projekt i uruchomić projekt przekazywanie `Hello World` jako argumenty:

```
cd src/App
dotnet run Hello World
```

Powinny być widoczne następujące wyniki:

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]