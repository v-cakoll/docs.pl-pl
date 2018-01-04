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
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="31d19-104">Rozpoczynanie pracy z F # z poziomu interfejsu wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="31d19-104">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="31d19-105">W tym artykule opisano, jak możesz rozpocząć pracę na systemie operacyjnym (Windows, system macOS lub Linux) przy użyciu języka F # z interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="31d19-105">This article covers how you can get started on any OS (Windows, macOS, or Linux) by using F# with the .NET Core CLI.</span></span> <span data-ttu-id="31d19-106">Będzie ona przejść przez tworzenie wielu projektów rozwiązania z biblioteki klas, który jest wywoływany przez aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="31d19-106">It will go through building a multi-project solution with a Class Library that is called by a Console Application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="31d19-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="31d19-107">Prerequisites</span></span>

<span data-ttu-id="31d19-108">Aby rozpocząć, należy zainstalować [.NET Core SDK w wersji 1.0 lub nowszej](https://dot.net/core).</span><span class="sxs-lookup"><span data-stu-id="31d19-108">To begin, you must install the [.NET Core SDK 1.0 or later](https://dot.net/core).</span></span> <span data-ttu-id="31d19-109">Ponieważ obsługuje on instalacji side-by-side jest niepotrzebna odinstalować poprzedniej wersji programu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="31d19-109">There is no need to uninstall a previous version of the .NET Core SDK, as it supports side-by-side installations.</span></span>

<span data-ttu-id="31d19-110">W tym artykule trzeba wiedzieć, jak za pomocą wiersza polecenia i preferowany tekst edytora.</span><span class="sxs-lookup"><span data-stu-id="31d19-110">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="31d19-111">Jeśli nie używasz już, [Visual Studio Code](https://code.visualstudio.com) to doskonałe rozwiązanie edytorem tekstu w F #.</span><span class="sxs-lookup"><span data-stu-id="31d19-111">If you don't already use it, [Visual Studio Code](https://code.visualstudio.com) is a great option as a text editor for F#.</span></span> <span data-ttu-id="31d19-112">Aby uzyskać atrakcyjne funkcje, takie jak IntelliSense, lepiej wyróżnianie składni i inne, możesz pobrać [Ionide rozszerzenia](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="31d19-112">To get awesome features like IntelliSense, better syntax highlighting, and more, you can download the [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>

## <a name="building-a-simple-multi-project-solution"></a><span data-ttu-id="31d19-113">Tworzenie prostego rozwiązania wielu projektów</span><span class="sxs-lookup"><span data-stu-id="31d19-113">Building a Simple Multi-project Solution</span></span>

<span data-ttu-id="31d19-114">Otwórz wiersz polecenia/terminal i użyj `dotnet new` polecenie, aby utworzyć nowy plik rozwiązania o nazwie `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="31d19-114">Open a command prompt/terminal and use the `dotnet new` command to create new solution file called `FSNetCore`:</span></span>

```
dotnet new sln -o FSNetCore
```

<span data-ttu-id="31d19-115">Następującą strukturę katalogów jest tworzony w wyniku wykonanie polecenia:</span><span class="sxs-lookup"><span data-stu-id="31d19-115">The folowing directory structure is produced as a result of the command completing:</span></span>

```
FSNetCore
    ├── FSNetCore.sln
```

<span data-ttu-id="31d19-116">Przejdź do *FSNetCore* i rozpocząć dodawanie projektów do folderu rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="31d19-116">Change directories to *FSNetCore* and start adding projects to the solution folder.</span></span>
 
### <a name="writing-a-class-library"></a><span data-ttu-id="31d19-117">Pisanie biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="31d19-117">Writing a Class library</span></span>

<span data-ttu-id="31d19-118">Użyj `dotnet new` polecenia, tworzenie projektu biblioteki klas w **src** folder o nazwie biblioteki.</span><span class="sxs-lookup"><span data-stu-id="31d19-118">Use the `dotnet new` command, create a Class Library project in the **src** folder named Library.</span></span> 

```bash
dotnet new lib -lang F# -o src/Library 
```

<span data-ttu-id="31d19-119">Następującą strukturę katalogów jest tworzony w wyniku wykonanie polecenia:</span><span class="sxs-lookup"><span data-stu-id="31d19-119">The following directory structure is produced as a result of the command completing:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="31d19-120">Zastąp zawartość `Library.fs` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="31d19-120">Replace the contents of `Library.fs` with the following:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value = 
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value  (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="31d19-121">Dodaj pakiet Newtonsoft.Json NuGet do projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="31d19-121">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```bash
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="31d19-122">Dodaj `Library` projektu do `FSNetCore` przy użyciu rozwiązania `dotnet sln add` polecenia:</span><span class="sxs-lookup"><span data-stu-id="31d19-122">Add the `Library` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="31d19-123">Przywróć zależności NuGet `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) i uruchom `dotnet build` Aby skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="31d19-123">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

### <a name="writing-a-console-application-which-consumes-the-class-library"></a><span data-ttu-id="31d19-124">Pisanie aplikacji konsoli, która korzysta z biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="31d19-124">Writing a Console Application which Consumes the Class Library</span></span>

<span data-ttu-id="31d19-125">Użyj `dotnet new` poleceń, Utwórz aplikację konsoli w **src** folder o nazwie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="31d19-125">Use the `dotnet new` command, create a Console app in the **src** folder named App.</span></span> 

```bash
dotnet new console -lang F# -o src/App 
```

<span data-ttu-id="31d19-126">Następującą strukturę katalogów jest tworzony w wyniku wykonanie polecenia:</span><span class="sxs-lookup"><span data-stu-id="31d19-126">The following directory structure is produced as a result of the command completing:</span></span>

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

<span data-ttu-id="31d19-127">Zmień `Program.fs` do:</span><span class="sxs-lookup"><span data-stu-id="31d19-127">Change `Program.fs` to:</span></span>

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

<span data-ttu-id="31d19-128">Dodaj odwołanie do `Library` projektu przy użyciu `dotnet add reference`.</span><span class="sxs-lookup"><span data-stu-id="31d19-128">Add a reference to the `Library` project using `dotnet add reference`.</span></span>

```bash
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="31d19-129">Dodaj `App` projektu do `FSNetCore` przy użyciu rozwiązania `dotnet sln add` polecenia:</span><span class="sxs-lookup"><span data-stu-id="31d19-129">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="31d19-130">Przywróć zależności NuGet `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) i uruchom `dotnet build` Aby skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="31d19-130">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="31d19-131">Zmień katalog na `src/App` konsoli projekt i uruchomić projekt przekazywanie `Hello World` jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="31d19-131">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments.</span></span>

```bash
cd src/App
dotnet run Hello World
``` 

<span data-ttu-id="31d19-132">Powinny być widoczne następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="31d19-132">You should see the following results:</span></span>

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
