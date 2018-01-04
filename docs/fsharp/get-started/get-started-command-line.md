---
title: "Wprowadzenie do języka F # z narzędzi wiersza polecenia"
description: "Dowiedz się, jak używać F # na systemie operacyjnym (Windows, System MacOS, Linux) z wielu platform .NET Core interfejsu wiersza polecenia."
keywords: "Visual f #, f #, funkcjonalności programowania .NET, .NET Core"
author: cartermp
ms.author: phcart
ms.date: 06/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 615db1ec-6ef3-4de2-bae6-4586affa9771
ms.openlocfilehash: 4820a8a306bd478429b497a8b7c70ff170c1c655
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2017
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Rozpoczynanie pracy z F # z poziomu interfejsu wiersza polecenia platformy .NET Core

W tym artykule opisano, jak możesz rozpocząć pracę na systemie operacyjnym (Windows, system macOS lub Linux) przy użyciu języka F # z interfejsu wiersza polecenia platformy .NET Core. Będzie ona przejść przez tworzenie wielu projektów rozwiązania z biblioteki klas, który jest wywoływany przez aplikacji konsoli.

## <a name="prerequisites"></a>Wymagania wstępne

Aby rozpocząć, należy zainstalować [.NET Core SDK w wersji 1.0 lub nowszej](https://dot.net/core). Ponieważ obsługuje on instalacji side-by-side jest niepotrzebna odinstalować poprzedniej wersji programu .NET Core SDK.

W tym artykule trzeba wiedzieć, jak za pomocą wiersza polecenia i preferowany tekst edytora. Jeśli nie używasz już, [Visual Studio Code](https://code.visualstudio.com) to doskonałe rozwiązanie edytorem tekstu w F #. Aby uzyskać atrakcyjne funkcje, takie jak IntelliSense, lepiej wyróżnianie składni i inne, możesz pobrać [Ionide rozszerzenia](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).

## <a name="building-a-simple-multi-project-solution"></a>Tworzenie prostego rozwiązania wielu projektów

Otwórz wiersz polecenia/terminal i użyj `dotnet new` polecenie, aby utworzyć nowy plik rozwiązania o nazwie `FSNetCore`:

```
dotnet new sln -o FSNetCore
```

Następującą strukturę katalogów jest tworzony w wyniku wykonanie polecenia:

```
FSNetCore
    ├── FSNetCore.sln
```

Przejdź do *FSNetCore* i rozpocząć dodawanie projektów do folderu rozwiązania.
 
### <a name="writing-a-class-library"></a>Pisanie biblioteki klas

Użyj `dotnet new` polecenia, tworzenie projektu biblioteki klas w **src** folder o nazwie biblioteki. 

```bash
dotnet new lib -lang F# -o src/Library 
```

Następującą strukturę katalogów jest tworzony w wyniku wykonanie polecenia:

```
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
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value  (JsonConvert.SerializeObject(value))
```

Dodaj pakiet Newtonsoft.Json NuGet do projektu biblioteki.

```bash
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Dodaj `Library` projektu do `FSNetCore` przy użyciu rozwiązania `dotnet sln add` polecenia:

```bash
dotnet sln add src/Library/Library.fsproj
```

Przywróć zależności NuGet `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) i uruchom `dotnet build` Aby skompilować projekt.

### <a name="writing-a-console-application-which-consumes-the-class-library"></a>Pisanie aplikacji konsoli, która korzysta z biblioteki klas

Użyj `dotnet new` poleceń, Utwórz aplikację konsoli w **src** folder o nazwie aplikacji. 

```bash
dotnet new console -lang F# -o src/App 
```

Następującą strukturę katalogów jest tworzony w wyniku wykonanie polecenia:

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

Zmień `Program.fs` do:

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

Dodaj odwołanie do `Library` projektu przy użyciu `dotnet add reference`.

```bash
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Dodaj `App` projektu do `FSNetCore` przy użyciu rozwiązania `dotnet sln add` polecenia:

```bash
dotnet sln add src/App/App.fsproj
```

Przywróć zależności NuGet `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) i uruchom `dotnet build` Aby skompilować projekt.

Zmień katalog na `src/App` konsoli projekt i uruchomić projekt przekazywanie `Hello World` jako argumenty.

```bash
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
