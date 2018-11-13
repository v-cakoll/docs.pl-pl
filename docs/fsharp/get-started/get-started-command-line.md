---
title: Wprowadzenie do F# za pomocą narzędzia wiersza polecenia
description: Dowiedz się, jak tworzenie prostego rozwiązania wielu projektów F# za pomocą interfejsu wiersza polecenia platformy .NET Core w dowolnym systemie operacyjnym (Windows, macOs lub Linux).
ms.date: 03/26/2018
ms.openlocfilehash: 8a82970f33c8bbe1b8cdd8fb6499b59b16d3cbf3
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "45673912"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="9cd1b-103">Wprowadzenie do F# za pomocą interfejsu wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="9cd1b-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="9cd1b-104">W tym artykule opisano, jak możesz rozpocząć pracę z F# w dowolnym systemie operacyjnym (Windows, macOS lub Linux) przy użyciu interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9cd1b-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="9cd1b-105">Przechodzi on przez tworzenie rozwiązania wielu projektów za pomocą biblioteki klas, który jest wywoływany przez aplikację konsolową w języku.</span><span class="sxs-lookup"><span data-stu-id="9cd1b-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9cd1b-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9cd1b-106">Prerequisites</span></span>

<span data-ttu-id="9cd1b-107">Aby rozpocząć, należy zainstalować najnowsze [zestawu .NET Core SDK](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="9cd1b-107">To begin, you must install the latest [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

<span data-ttu-id="9cd1b-108">W tym artykule trzeba wiedzieć, jak za pomocą wiersza polecenia i tekst preferowanego edytora.</span><span class="sxs-lookup"><span data-stu-id="9cd1b-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="9cd1b-109">Jeśli już nie używasz go, [programu Visual Studio Code](get-started-vscode.md) jest świetnym rozwiązaniem jako edytora tekstu w języku F#.</span><span class="sxs-lookup"><span data-stu-id="9cd1b-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="9cd1b-110">Tworzenie prostego rozwiązania wielu projektów</span><span class="sxs-lookup"><span data-stu-id="9cd1b-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="9cd1b-111">Otwórz wiersz polecenia/terminal i użyj [dotnet nowe](../../core/tools/dotnet-new.md) polecenie, aby utworzyć nowy plik rozwiązania o nazwie `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="9cd1b-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```console
dotnet new sln -o FSNetCore
```

<span data-ttu-id="9cd1b-112">Następującą strukturę katalogów jest generowany po uruchomieniu w poprzednim poleceniu:</span><span class="sxs-lookup"><span data-stu-id="9cd1b-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="9cd1b-113">Zapis biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="9cd1b-113">Write a class library</span></span>

<span data-ttu-id="9cd1b-114">Zmień katalog na *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="9cd1b-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="9cd1b-115">Użyj `dotnet new` polecenia, Utwórz projekt biblioteki klas w **src** folder o nazwie biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9cd1b-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```console
dotnet new classlib -lang F# -o src/Library
```

<span data-ttu-id="9cd1b-116">Następującą strukturę katalogów jest generowany po uruchomieniu w poprzednim poleceniu:</span><span class="sxs-lookup"><span data-stu-id="9cd1b-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="9cd1b-117">Zastąp zawartość `Library.fs` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="9cd1b-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="9cd1b-118">Dodaj pakiet Newtonsoft.Json NuGet do projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9cd1b-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="9cd1b-119">Dodaj `Library` projekt `FSNetCore` rozwiązanie przy użyciu [Dodaj dotnet sln](../../core/tools/dotnet-sln.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="9cd1b-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```console
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="9cd1b-120">Uruchom `dotnet build` do skompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="9cd1b-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="9cd1b-121">Nierozwiązane zależności zostaną przywrócone, podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="9cd1b-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="9cd1b-122">Napisz aplikację konsolową, która używa biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="9cd1b-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="9cd1b-123">Użyj `dotnet new` polecenia, Utwórz aplikację konsolową w **src** folder o nazwie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cd1b-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```console
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="9cd1b-124">Następującą strukturę katalogów jest generowany po uruchomieniu w poprzednim poleceniu:</span><span class="sxs-lookup"><span data-stu-id="9cd1b-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="9cd1b-125">Zastąp zawartość `Program.fs` pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="9cd1b-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="9cd1b-126">Dodaj odwołanie do `Library` projektu za pomocą [dotnet Dodaj odwołanie](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="9cd1b-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="9cd1b-127">Dodaj `App` projekt `FSNetCore` rozwiązanie przy użyciu `dotnet sln add` polecenia:</span><span class="sxs-lookup"><span data-stu-id="9cd1b-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```console
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="9cd1b-128">Przywracanie zależności NuGet `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) i uruchom `dotnet build` do skompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="9cd1b-128">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="9cd1b-129">Zmień katalog na `src/App` konsoli projekt i uruchomić projekt, przekazując `Hello World` jako argumenty:</span><span class="sxs-lookup"><span data-stu-id="9cd1b-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```console
cd src/App
dotnet run Hello World
```

<span data-ttu-id="9cd1b-130">Powinny zostać wyświetlone następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9cd1b-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="9cd1b-131">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9cd1b-131">Next steps</span></span>

<span data-ttu-id="9cd1b-132">Następnie zapoznaj się z [samouczek programu F#](../tour.md) Aby dowiedzieć się więcej na temat różnych funkcji języka F#.</span><span class="sxs-lookup"><span data-stu-id="9cd1b-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
