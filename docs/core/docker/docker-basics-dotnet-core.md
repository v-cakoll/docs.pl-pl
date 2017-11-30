---
title: "Dowiedz się podstawy Docker z platformą .NET Core"
description: Docker i .NET Core podstawowy samouczek
keywords: .NET, .NET core, Docker, samouczek
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.openlocfilehash: 5935f67d7e4ca9c9e8768373e2bcaa9febccfdc5
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2017
---
# <a name="learn-docker-basics-with-net-core"></a><span data-ttu-id="886f4-104">Dowiedz się podstawy Docker z platformą .NET Core</span><span class="sxs-lookup"><span data-stu-id="886f4-104">Learn Docker Basics with .NET Core</span></span>

<span data-ttu-id="886f4-105">Ten samouczek zawiera Docker kontenera tworzenia i wdrażania zadania dla aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="886f4-105">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="886f4-106">W trakcie tego samouczka dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="886f4-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="886f4-107">Jak utworzyć plik Dockerfile</span><span class="sxs-lookup"><span data-stu-id="886f4-107">How to create a Dockerfile</span></span>
> * <span data-ttu-id="886f4-108">Jak utworzyć aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="886f4-108">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="886f4-109">Jak wdrożyć aplikację w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="886f4-109">How to deploy your app into a Docker container.</span></span>

<span data-ttu-id="886f4-110">[Platformy Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) używa [aparatem platformy Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) szybkie tworzenie i pakietu aplikacji jako [obrazy usługi Docker](https://docs.docker.com/glossary/?term=image).</span><span class="sxs-lookup"><span data-stu-id="886f4-110">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="886f4-111">Te obrazy są zapisywane [plik Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format, aby wdrożyć i uruchomić w [warstwie kontenera](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="886f4-111">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="886f4-112">Oprogramowanie .NET core: Najłatwiejszym sposobem na rozpoczęcie pracy</span><span class="sxs-lookup"><span data-stu-id="886f4-112">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="886f4-113">Przed utworzeniem obrazu Docker, należy containerize aplikacji.</span><span class="sxs-lookup"><span data-stu-id="886f4-113">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="886f4-114">Można go utworzyć w systemie Linux, MacOS lub systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="886f4-114">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="886f4-115">Jest najszybszym i Najprostszym sposobem wykonania tego używać .NET Core.</span><span class="sxs-lookup"><span data-stu-id="886f4-115">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="886f4-116">Jeśli znasz zestaw narzędzi interfejsu wiersza polecenia platformy .NET Core odczytu [Omówienie zestawu SDK programu .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="886f4-116">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="886f4-117">Można tworzyć kontenery w systemach Windows i Linux z [tagi na podstawie wielu arch](https://github.com/dotnet/announcements/issues/14).</span><span class="sxs-lookup"><span data-stu-id="886f4-117">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="886f4-118">Pierwszej aplikacji platformy .NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="886f4-118">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="886f4-119">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="886f4-119">Prerequisites</span></span>

<span data-ttu-id="886f4-120">Do ukończenia tego samouczka:</span><span class="sxs-lookup"><span data-stu-id="886f4-120">To complete this tutorial:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="886f4-121">.NET core 2.0 SDK</span><span class="sxs-lookup"><span data-stu-id="886f4-121">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="886f4-122">Zainstaluj [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="886f4-122">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

<span data-ttu-id="886f4-123">Zobacz [2.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) Pełna lista .NET Core 2.x obsługiwanych systemów operacyjnych, poza wersje obsługi systemu operacyjnego i łącza do zasad cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="886f4-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="886f4-124">Jeśli nie jest jeszcze, należy zainstalować w edytorze kodu ulubionych.</span><span class="sxs-lookup"><span data-stu-id="886f4-124">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="886f4-125">Należy zainstalować Edytor kodu?</span><span class="sxs-lookup"><span data-stu-id="886f4-125">Need to install a code editor?</span></span> <span data-ttu-id="886f4-126">Spróbuj [programu Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="886f4-126">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="886f4-127">Instalowanie klienta Docker</span><span class="sxs-lookup"><span data-stu-id="886f4-127">Installing Docker Client</span></span>

<span data-ttu-id="886f4-128">Zainstaluj [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) lub nowszego klienta Docker.</span><span class="sxs-lookup"><span data-stu-id="886f4-128">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="886f4-129">Klient Docker można zainstalować w:</span><span class="sxs-lookup"><span data-stu-id="886f4-129">The Docker client can be installed in:</span></span>

* <span data-ttu-id="886f4-130">Dystrybucje systemu Linux</span><span class="sxs-lookup"><span data-stu-id="886f4-130">Linux distributions</span></span>

   * [<span data-ttu-id="886f4-131">CentOS</span><span class="sxs-lookup"><span data-stu-id="886f4-131">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="886f4-132">Debian</span><span class="sxs-lookup"><span data-stu-id="886f4-132">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="886f4-133">Fedora</span><span class="sxs-lookup"><span data-stu-id="886f4-133">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="886f4-134">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="886f4-134">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="886f4-135">System macOS</span><span class="sxs-lookup"><span data-stu-id="886f4-135">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="886f4-136">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="886f4-136">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

### <a name="create-a-net-core-20-console-app-for-dockerization"></a><span data-ttu-id="886f4-137">Tworzenie aplikacji konsoli .NET Core 2.0 dla Dockerization</span><span class="sxs-lookup"><span data-stu-id="886f4-137">Create a .NET Core 2.0 console app for Dockerization</span></span>

<span data-ttu-id="886f4-138">Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*.</span><span class="sxs-lookup"><span data-stu-id="886f4-138">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="886f4-139">Przejdź do folderu, który został utworzony i wpisz następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="886f4-139">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="886f4-140">Poznajmy Szybkie wskazówki:</span><span class="sxs-lookup"><span data-stu-id="886f4-140">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="886f4-141">[`dotnet new`](../tools/dotnet-new.md)Tworzy aktualne `Hello.csproj` pliku projektu z zależnościami, które są niezbędne do tworzenia aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="886f4-141">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="886f4-142">Tworzy również `Program.cs`, podstawowe plik zawierający punkt wejścia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="886f4-142">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="886f4-143">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="886f4-143">`Hello.csproj`:</span></span>

   <span data-ttu-id="886f4-144">Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i kompilacji programu.</span><span class="sxs-lookup"><span data-stu-id="886f4-144">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="886f4-145">`OutputType` Określa tag tworzymy plik wykonywalny, innymi słowy aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="886f4-145">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="886f4-146">`TargetFramework` Tag Określa, jakie implementacji .NET możemy docelowych.</span><span class="sxs-lookup"><span data-stu-id="886f4-146">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="886f4-147">Realizując bardziej zaawansowany scenariusz można określić wiele platform docelowych i kompilacja — przejście do określonej struktury w ramach jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="886f4-147">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="886f4-148">W tym samouczku będziemy kompilacji dla programu .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="886f4-148">In this tutorial, we build for .NET Core 2.0.</span></span>

   <span data-ttu-id="886f4-149">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="886f4-149">`Program.cs`:</span></span>

   <span data-ttu-id="886f4-150">Program, który rozpoczyna się od `using System`.</span><span class="sxs-lookup"><span data-stu-id="886f4-150">The program starts by `using System`.</span></span> <span data-ttu-id="886f4-151">To zdanie oznacza, "Przenieś wszystko `System` przestrzeni nazw do zakresu dla tego pliku."</span><span class="sxs-lookup"><span data-stu-id="886f4-151">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="886f4-152">`System` Przestrzeń nazw zawiera podstawowe konstrukcji `string`, lub typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="886f4-152">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="886f4-153">Następnie definicję przestrzeni nazw o nazwie `Hello`.</span><span class="sxs-lookup"><span data-stu-id="886f4-153">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="886f4-154">Przestrzeń nazw, można zmienić na dowolnych znaków.</span><span class="sxs-lookup"><span data-stu-id="886f4-154">You can change namespace to anything you want.</span></span> <span data-ttu-id="886f4-155">Klasa o nazwie `Program` jest zdefiniowany w tej przestrzeni nazw z `Main` metody pobierającej tablicy ciągów jako jej argument.</span><span class="sxs-lookup"><span data-stu-id="886f4-155">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="886f4-156">Ta tablica zawiera listę argumentów przekazana wywołanego skompilowany program.</span><span class="sxs-lookup"><span data-stu-id="886f4-156">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="886f4-157">W naszym przykładzie program zapisuje tylko "Witaj świecie!"</span><span class="sxs-lookup"><span data-stu-id="886f4-157">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="886f4-158">w konsoli.</span><span class="sxs-lookup"><span data-stu-id="886f4-158">to the console.</span></span>

2. `$ dotnet restore`

   <span data-ttu-id="886f4-159">W .NET Core 2.x, **dotnet nowe** uruchamia [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="886f4-159">In .NET Core 2.x, **dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="886f4-160">**Przywracanie DotNet** przywraca drzewie zależności z [NuGet](https://www.nuget.org/)wywołania (.NET Menedżera pakietów).</span><span class="sxs-lookup"><span data-stu-id="886f4-160">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="886f4-161">NuGet wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="886f4-161">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="886f4-162">analizuje *Hello.csproj* pliku</span><span class="sxs-lookup"><span data-stu-id="886f4-162">analyzes the *Hello.csproj* file</span></span> 
   * <span data-ttu-id="886f4-163">pobiera plik zależności (lub chwyty z pamięci podręcznej komputera)</span><span class="sxs-lookup"><span data-stu-id="886f4-163">downloads the file dependencies (or grabs from your machine cache)</span></span>
   * <span data-ttu-id="886f4-164">zapisuje *obj/project.assets.json* pliku</span><span class="sxs-lookup"><span data-stu-id="886f4-164">writes the *obj/project.assets.json* file</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   <span data-ttu-id="886f4-165">*Project.assets.json* plików jest pełny zestaw wykres zależności NuGet rozwiązania powiązania i innych metadanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="886f4-165">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="886f4-166">To wymagane, plik jest używany przez innych narzędzi, takich jak [ `dotnet build` ](../tools/dotnet-build.md) i [ `dotnet run` ](../tools/dotnet-run.md), aby poprawnie przetworzyć kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="886f4-166">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="886f4-167">[`dotnet run`](../tools/dotnet-run.md)wywołania [ `dotnet build` ](../tools/dotnet-build.md) o potwierdzenie pomyślnego utworzenia kompilacji, a następnie wywołania `dotnet <assembly.dll>` do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="886f4-167">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    <span data-ttu-id="886f4-168">Dla zaawansowanych scenariuszy, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="886f4-168">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="886f4-169">Dockerize aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="886f4-169">Dockerize the .NET Core application</span></span>

<span data-ttu-id="886f4-170">Aplikacja konsoli Hello .NET Core pomyślnie działa lokalnie.</span><span class="sxs-lookup"><span data-stu-id="886f4-170">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="886f4-171">Teraz załóżmy zabrać krok dalsze i skompilować i uruchomić aplikację w Docker.</span><span class="sxs-lookup"><span data-stu-id="886f4-171">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="886f4-172">Twoje pierwszy plik Dockerfile</span><span class="sxs-lookup"><span data-stu-id="886f4-172">Your first Dockerfile</span></span>

<span data-ttu-id="886f4-173">Otwórz w edytorze tekstów i do dzieła!</span><span class="sxs-lookup"><span data-stu-id="886f4-173">Open your text editor and let's get started!</span></span> <span data-ttu-id="886f4-174">Nadal trwają prace z katalogu Hello możemy tworzone w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="886f4-174">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="886f4-175">Dodaj następujące instrukcje Docker albo Linux lub [kontenery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) do nowego pliku.</span><span class="sxs-lookup"><span data-stu-id="886f4-175">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="886f4-176">Po zakończeniu zapisz go w folderze głównym katalogiem Hello jako **plik Dockerfile**, bez rozszerzenia (konieczne może być równa danego typu pliku `All types (*.*)` lub coś podobnego).</span><span class="sxs-lookup"><span data-stu-id="886f4-176">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="886f4-177">Plik Dockerfile zawiera instrukcje kompilacji Docker, które są wykonywane sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="886f4-177">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="886f4-178">Pierwsza instrukcja musi być [ **FROM**](https://docs.docker.com/engine/reference/builder/#from).</span><span class="sxs-lookup"><span data-stu-id="886f4-178">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="886f4-179">Ta instrukcja inicjuje nowy etap kompilacji i ustawia obraz podstawowy dla pozostałych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="886f4-179">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="886f4-180">Tagi wielu architektury ściągnięcia kontenery systemu Windows lub Linux, w zależności od platformy Docker dla systemu Windows [tryb kontenera](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span><span class="sxs-lookup"><span data-stu-id="886f4-180">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="886f4-181">Obraz podstawowy dla naszej próbki jest obrazem zestawu sdk 2.0 z repozytorium microsoft/dotnet</span><span class="sxs-lookup"><span data-stu-id="886f4-181">The Base Image for our sample is the 2.0-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

<span data-ttu-id="886f4-182">[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) instrukcji Ustawia katalog roboczy dla wszelkie pozostałe wykonywania, CMD, punktu wejścia, KOPIOWANIA i Dodaj plik Dockerfile instrukcje.</span><span class="sxs-lookup"><span data-stu-id="886f4-182">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="886f4-183">Jeśli katalog nie istnieje, zostanie on utworzony.</span><span class="sxs-lookup"><span data-stu-id="886f4-183">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="886f4-184">W takim przypadku WORKDIR ustawiono do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="886f4-184">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="886f4-185">[ **KOPIOWANIA** ](https://docs.docker.com/engine/reference/builder/#copy) instrukcji kopiuje nowe pliki lub katalogi ze ścieżki źródłowej i dodaje je do plików kontenera docelowego.</span><span class="sxs-lookup"><span data-stu-id="886f4-185">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="886f4-186">Z tej instrukcji Trwa kopiowanie plików projektu C# do kontenera.</span><span class="sxs-lookup"><span data-stu-id="886f4-186">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="886f4-187">[ **Uruchom** ](https://docs.docker.com/engine/reference/builder/#run) instrukcji wykonuje żadnych poleceń w nową warstwę ponad bieżący obraz i zatwierdź wyniki.</span><span class="sxs-lookup"><span data-stu-id="886f4-187">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="886f4-188">Obraz wynikowy zatwierdzone służy do następnego kroku w plik Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="886f4-188">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="886f4-189">Uruchamiamy **przywracania dotnet** uzyskać wymagane zależności pliku projektu C#.</span><span class="sxs-lookup"><span data-stu-id="886f4-189">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span> 

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="886f4-190">To **KOPIOWANIA** instrukcji kopiuje pozostałych plików do naszej kontenera do nowych [warstwy](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span><span class="sxs-lookup"><span data-stu-id="886f4-190">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="886f4-191">Firma Microsoft publikowania aplikacji z tym **Uruchom** instrukcji.</span><span class="sxs-lookup"><span data-stu-id="886f4-191">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="886f4-192">[ **Publikowania dotnet** ](../tools/dotnet-publish.md) polecenie kompiluje aplikacji odczytuje za pośrednictwem jego zależności, określona w pliku projektu i publikuje Wynikowy zestaw plików w katalogu.</span><span class="sxs-lookup"><span data-stu-id="886f4-192">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="886f4-193">Naszej aplikacji jest publikowany razem **wersji** konfiguracji i dane wyjściowe do domyślnego katalogu.</span><span class="sxs-lookup"><span data-stu-id="886f4-193">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="886f4-194">[ **Punktu wejścia** ](https://docs.docker.com/engine/reference/builder/#entrypoint) instrukcji umożliwia kontener uruchamianie jako plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="886f4-194">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="886f4-195">Teraz masz plik Dockerfile który:</span><span class="sxs-lookup"><span data-stu-id="886f4-195">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="886f4-196">Kopiuje obraz aplikacji</span><span class="sxs-lookup"><span data-stu-id="886f4-196">copies your app to the image</span></span>
* <span data-ttu-id="886f4-197">zależności aplikacji do obrazu</span><span class="sxs-lookup"><span data-stu-id="886f4-197">your app's dependencies to the image</span></span>
* <span data-ttu-id="886f4-198">Tworzy aplikację do uruchamiania jako plik wykonywalny</span><span class="sxs-lookup"><span data-stu-id="886f4-198">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-20-app"></a><span data-ttu-id="886f4-199">Tworzenie i uruchamianie aplikacji Hello .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="886f4-199">Build and run the Hello .NET Core 2.0 app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="886f4-200">Niezbędne polecenia Docker</span><span class="sxs-lookup"><span data-stu-id="886f4-200">Essential Docker commands</span></span>

<span data-ttu-id="886f4-201">Te polecenia Docker są niezbędne:</span><span class="sxs-lookup"><span data-stu-id="886f4-201">These Docker commands are essential:</span></span>

* [<span data-ttu-id="886f4-202">docker kompilacji</span><span class="sxs-lookup"><span data-stu-id="886f4-202">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="886f4-203">Uruchom docker</span><span class="sxs-lookup"><span data-stu-id="886f4-203">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="886f4-204">docker ps</span><span class="sxs-lookup"><span data-stu-id="886f4-204">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="886f4-205">Zatrzymaj docker</span><span class="sxs-lookup"><span data-stu-id="886f4-205">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="886f4-206">docker rm</span><span class="sxs-lookup"><span data-stu-id="886f4-206">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="886f4-207">docker rmi</span><span class="sxs-lookup"><span data-stu-id="886f4-207">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="886f4-208">Obraz docker</span><span class="sxs-lookup"><span data-stu-id="886f4-208">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="886f4-209">Tworzenie i uruchamianie</span><span class="sxs-lookup"><span data-stu-id="886f4-209">Build and run</span></span>

<span data-ttu-id="886f4-210">Zapisano plik dockerfile; teraz Docker tworzy aplikację, a następnie uruchomi kontener.</span><span class="sxs-lookup"><span data-stu-id="886f4-210">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="886f4-211">Dane wyjściowe z `docker build` polecenia powinny być podobne do następujących danych wyjściowych konsoli:</span><span class="sxs-lookup"><span data-stu-id="886f4-211">The output from the `docker build` command should be similar to the following console output:</span></span>

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

<span data-ttu-id="886f4-212">Jak widać z danych wyjściowych, aparatem platformy Docker używane plik Dockerfile do budowania naszych kontenera.</span><span class="sxs-lookup"><span data-stu-id="886f4-212">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="886f4-213">Dane wyjściowe z `docker run` polecenia powinny być podobne do następujących danych wyjściowych konsoli:</span><span class="sxs-lookup"><span data-stu-id="886f4-213">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="886f4-214">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="886f4-214">Congratulations!</span></span> <span data-ttu-id="886f4-215">masz tylko:</span><span class="sxs-lookup"><span data-stu-id="886f4-215">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="886f4-216">Utworzyć lokalnej aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="886f4-216">Created a local .NET Core app</span></span>
> * <span data-ttu-id="886f4-217">Utworzony plik Dockerfile do kompilacji z pierwszego kontenera</span><span class="sxs-lookup"><span data-stu-id="886f4-217">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="886f4-218">Wbudowane i uruchomiono aplikację Dockerized</span><span class="sxs-lookup"><span data-stu-id="886f4-218">Built and ran your Dockerized app</span></span>



## <a name="next-steps"></a><span data-ttu-id="886f4-219">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="886f4-219">Next Steps</span></span>

<span data-ttu-id="886f4-220">Poniżej przedstawiono niektóre czynności, które można wykonać:</span><span class="sxs-lookup"><span data-stu-id="886f4-220">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="886f4-221">Wprowadzenie do platformy .NET Docker obrazów wideo</span><span class="sxs-lookup"><span data-stu-id="886f4-221">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="886f4-222">Visual Studio, Docker i wystąpień kontenera Azure lepsze razem!</span><span class="sxs-lookup"><span data-stu-id="886f4-222">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [<span data-ttu-id="886f4-223">Docker dla skrócone podręczniki platformy Azure</span><span class="sxs-lookup"><span data-stu-id="886f4-223">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="886f4-224">Wdrażanie aplikacji na Docker na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="886f4-224">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> <span data-ttu-id="886f4-225">Jeśli nie masz subskrypcji platformy Azure, [Zarejestruj się już dziś](https://azure.microsoft.com/free/?b=16.48) bezpłatnej 30-dniowe konto i 200 USD interweniować środków Azure wypróbowanie dowolną kombinację usługami Azure.</span><span class="sxs-lookup"><span data-stu-id="886f4-225">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="886f4-226">Używane w tym przykładzie obrazy usługi docker</span><span class="sxs-lookup"><span data-stu-id="886f4-226">Docker Images used in this sample</span></span>

<span data-ttu-id="886f4-227">Na poniższych ilustracjach Docker są używane w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="886f4-227">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="886f4-228">Powiązane zasoby</span><span class="sxs-lookup"><span data-stu-id="886f4-228">Related Resources</span></span>

* [<span data-ttu-id="886f4-229">Przykłady .NET core Docker</span><span class="sxs-lookup"><span data-stu-id="886f4-229">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [<span data-ttu-id="886f4-230">Plik Dockerfile kontenerów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="886f4-230">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="886f4-231">Przykłady programu .NET framework Docker</span><span class="sxs-lookup"><span data-stu-id="886f4-231">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="886f4-232">Platformy ASP.NET Core na DockerHub</span><span class="sxs-lookup"><span data-stu-id="886f4-232">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="886f4-233">Dockerize aplikację .NET Core — samouczek Docker</span><span class="sxs-lookup"><span data-stu-id="886f4-233">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="886f4-234">Praca z narzędzia Docker programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="886f4-234">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="886f4-235">Wdrażanie obrazów Docker z rejestru kontenera platformy Azure do wystąpień kontenera platformy Azure</span><span class="sxs-lookup"><span data-stu-id="886f4-235">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)