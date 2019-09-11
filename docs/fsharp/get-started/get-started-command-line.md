---
title: Wprowadzenie do F# narzędzia wiersza polecenia
description: Dowiedz się, jak utworzyć proste rozwiązanie z obsługą F# kilku projektów przy użyciu interfejs wiersza polecenia platformy .NET Core w dowolnym systemie operacyjnym (Windows, MacOS lub Linux).
ms.date: 03/26/2018
ms.openlocfilehash: 1376b6b5384f380c06a96cdc568ad108de8a6e5f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855821"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="9aa39-103">Wprowadzenie do programu F# z interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="9aa39-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="9aa39-104">W tym artykule opisano, jak rozpocząć pracę z F# dowolnym systemem operacyjnym (Windows, MacOS lub Linux) przy użyciu interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9aa39-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="9aa39-105">Odbywa się to przez utworzenie rozwiązania obejmującego wiele projektów z biblioteką klas, która jest wywoływana przez aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="9aa39-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9aa39-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9aa39-106">Prerequisites</span></span>

<span data-ttu-id="9aa39-107">Aby rozpocząć, należy zainstalować najnowszą [zestaw .NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="9aa39-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="9aa39-108">W tym artykule przyjęto założenie, że wiesz, jak używać wiersza polecenia i mieć preferowany Edytor tekstu.</span><span class="sxs-lookup"><span data-stu-id="9aa39-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="9aa39-109">Jeśli nie jest już używany, [Visual Studio Code](get-started-vscode.md) jest doskonałym rozwiązaniem jako edytor tekstu dla F#.</span><span class="sxs-lookup"><span data-stu-id="9aa39-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="9aa39-110">Tworzenie prostego rozwiązania z obsługą kilku projektów</span><span class="sxs-lookup"><span data-stu-id="9aa39-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="9aa39-111">Otwórz wiersz polecenia/Terminal i użyj polecenia [dotnet New](../../core/tools/dotnet-new.md) , aby utworzyć nowy plik rozwiązania o nazwie `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="9aa39-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```console
dotnet new sln -o FSNetCore
```

<span data-ttu-id="9aa39-112">Następująca struktura katalogów jest generowana po uruchomieniu poprzedniego polecenia:</span><span class="sxs-lookup"><span data-stu-id="9aa39-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="9aa39-113">Napisz bibliotekę klas</span><span class="sxs-lookup"><span data-stu-id="9aa39-113">Write a class library</span></span>

<span data-ttu-id="9aa39-114">Zmień katalogi na *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="9aa39-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="9aa39-115">Za pomocą polecenia Utwórz projekt biblioteki klas w folderze src o nazwie Library. `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="9aa39-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```console
dotnet new classlib -lang F# -o src/Library
```

<span data-ttu-id="9aa39-116">Następująca struktura katalogów jest generowana po uruchomieniu poprzedniego polecenia:</span><span class="sxs-lookup"><span data-stu-id="9aa39-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="9aa39-117">Zastąp zawartość `Library.fs` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="9aa39-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="9aa39-118">Dodaj pakiet NuGet Newtonsoft. JSON do projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9aa39-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="9aa39-119">Dodaj projekt do rozwiązania przy użyciu polecenia [dotnet sln Add:](../../core/tools/dotnet-sln.md) `FSNetCore` `Library`</span><span class="sxs-lookup"><span data-stu-id="9aa39-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```console
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="9aa39-120">Uruchom `dotnet build` , aby skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="9aa39-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="9aa39-121">Nierozwiązane zależności zostaną przywrócone podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="9aa39-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="9aa39-122">Napisz aplikację konsolową, która używa biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="9aa39-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="9aa39-123">Za pomocą polecenia Utwórz aplikację konsolową w folderze src o nazwie App. `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="9aa39-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```console
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="9aa39-124">Następująca struktura katalogów jest generowana po uruchomieniu poprzedniego polecenia:</span><span class="sxs-lookup"><span data-stu-id="9aa39-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="9aa39-125">Zastąp zawartość `Program.fs` pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="9aa39-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="9aa39-126">Dodaj odwołanie do `Library` projektu przy użyciu [dodatku dotnet Dodaj odwołanie](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="9aa39-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="9aa39-127">Dodaj projekt do rozwiązania przy użyciu `dotnet sln add` polecenia: `FSNetCore` `App`</span><span class="sxs-lookup"><span data-stu-id="9aa39-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```console
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="9aa39-128">Przywróć zależności NuGet i uruchom `dotnet restore` `dotnet build` polecenie, aby skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="9aa39-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="9aa39-129">Zmień katalog na `src/App` projekt konsoli i uruchom przekazywanie `Hello World` projektu jako argumenty:</span><span class="sxs-lookup"><span data-stu-id="9aa39-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```console
cd src/App
dotnet run Hello World
```

<span data-ttu-id="9aa39-130">Powinny być widoczne następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9aa39-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="9aa39-131">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9aa39-131">Next steps</span></span>

<span data-ttu-id="9aa39-132">Następnie zapoznaj się z [przewodnikiem F# ](../tour.md) , aby dowiedzieć się F# więcej o różnych funkcjach.</span><span class="sxs-lookup"><span data-stu-id="9aa39-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
