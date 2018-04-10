---
title: 'Wprowadzenie do języka F # z narzędzi wiersza polecenia'
description: 'Dowiedz się, jak rozbudowywać prostym rozwiązaniem wielu projektów F # za pomocą interfejsu wiersza polecenia platformy .NET Core w dowolnym systemie operacyjnym (Windows, system macOs lub Linux).'
author: cartermp
ms.author: phcart
ms.date: 03/26/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.openlocfilehash: e48e1291bbe91da0d9ca2adbb08662bd106c8fb4
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="7d35a-103">Rozpoczynanie pracy z F # z poziomu interfejsu wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="7d35a-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="7d35a-104">W tym artykule opisano, jak możesz rozpocząć pracę z F # w dowolnym systemie operacyjnym (Windows, system macOS lub Linux) z poziomu interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7d35a-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="7d35a-105">Przechodzi ona przez tworzenie wielu projektów rozwiązania z biblioteki klas, który jest wywoływany przez aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="7d35a-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7d35a-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7d35a-106">Prerequisites</span></span>

<span data-ttu-id="7d35a-107">Aby rozpocząć, należy zainstalować [.NET Core SDK w wersji 1.0 lub nowszej](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="7d35a-107">To begin, you must install the [.NET Core SDK 1.0 or later](https://www.microsoft.com/net/download/).</span></span> <span data-ttu-id="7d35a-108">Ponieważ obsługuje on instalacji side-by-side jest niepotrzebna odinstalować poprzedniej wersji programu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="7d35a-108">There is no need to uninstall a previous version of the .NET Core SDK, as it supports side-by-side installations.</span></span>

<span data-ttu-id="7d35a-109">W tym artykule trzeba wiedzieć, jak za pomocą wiersza polecenia i preferowany tekst edytora.</span><span class="sxs-lookup"><span data-stu-id="7d35a-109">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="7d35a-110">Jeśli nie używasz już, [Visual Studio Code](https://code.visualstudio.com) to doskonałe rozwiązanie edytorem tekstu w F #.</span><span class="sxs-lookup"><span data-stu-id="7d35a-110">If you don't already use it, [Visual Studio Code](https://code.visualstudio.com) is a great option as a text editor for F#.</span></span> <span data-ttu-id="7d35a-111">Aby uzyskać atrakcyjne funkcje, takie jak IntelliSense, lepiej wyróżnianie składni i inne, możesz pobrać [Ionide rozszerzenia](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="7d35a-111">To get awesome features like IntelliSense, better syntax highlighting, and more, you can download the [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="7d35a-112">Tworzenie prostego rozwiązania wielu projektów</span><span class="sxs-lookup"><span data-stu-id="7d35a-112">Build a simple multi-project solution</span></span>

<span data-ttu-id="7d35a-113">Otwórz wiersz polecenia/terminal i użyj [dotnet nowe](../../core/tools/dotnet-new.md) polecenie, aby utworzyć nowy plik rozwiązania o nazwie `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="7d35a-113">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```
dotnet new sln -o FSNetCore
```

<span data-ttu-id="7d35a-114">Następującą strukturę katalogów jest generowany po użyciu poprzedniego polecenia:</span><span class="sxs-lookup"><span data-stu-id="7d35a-114">The following directory structure is produced after running the previous command:</span></span>

```
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="7d35a-115">Zapis biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="7d35a-115">Write a class library</span></span>

<span data-ttu-id="7d35a-116">Przejdź do *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="7d35a-116">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="7d35a-117">Użyj `dotnet new` polecenia, tworzenie projektu biblioteki klas w **src** folder o nazwie biblioteki.</span><span class="sxs-lookup"><span data-stu-id="7d35a-117">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```
dotnet new lib -lang F# -o src/Library
```

<span data-ttu-id="7d35a-118">Następującą strukturę katalogów jest generowany po użyciu poprzedniego polecenia:</span><span class="sxs-lookup"><span data-stu-id="7d35a-118">The following directory structure is produced after running the previous command:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="7d35a-119">Zastąp zawartość `Library.fs` z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7d35a-119">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="7d35a-120">Dodaj pakiet Newtonsoft.Json NuGet do projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="7d35a-120">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="7d35a-121">Dodaj `Library` projektu do `FSNetCore` przy użyciu rozwiązania [dodać dotnet sln](../../core/tools/dotnet-sln.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="7d35a-121">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="7d35a-122">Przywróć zależności NuGet przy użyciu `dotnet restore` polecenia ([patrz Uwaga](#dotnet-restore-note)) i uruchom `dotnet build` Aby skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="7d35a-122">Restore the NuGet dependencies using the `dotnet restore` command ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="7d35a-123">Pisanie aplikacji konsoli, który wykorzystuje biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="7d35a-123">Write a console application that consumes the class library</span></span>

<span data-ttu-id="7d35a-124">Użyj `dotnet new` polecenia, Utwórz aplikację konsoli w **src** folder o nazwie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d35a-124">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="7d35a-125">Następującą strukturę katalogów jest generowany po użyciu poprzedniego polecenia:</span><span class="sxs-lookup"><span data-stu-id="7d35a-125">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="7d35a-126">Zastąp zawartość `Program.fs` pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7d35a-126">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="7d35a-127">Dodaj odwołanie do `Library` projektu za pomocą [dotnet Dodaj odwołanie](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="7d35a-127">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="7d35a-128">Dodaj `App` projektu do `FSNetCore` przy użyciu rozwiązania `dotnet sln add` polecenia:</span><span class="sxs-lookup"><span data-stu-id="7d35a-128">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="7d35a-129">Przywróć zależności NuGet `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) i uruchom `dotnet build` Aby skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="7d35a-129">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="7d35a-130">Zmień katalog na `src/App` konsoli projekt i uruchomić projekt przekazywanie `Hello World` jako argumenty:</span><span class="sxs-lookup"><span data-stu-id="7d35a-130">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```
cd src/App
dotnet run Hello World
```

<span data-ttu-id="7d35a-131">Powinny być widoczne następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7d35a-131">You should see the following results:</span></span>

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]