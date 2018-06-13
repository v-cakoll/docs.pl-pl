---
title: Dowiedz się podstawy Docker z platformą .NET Core
description: Docker i .NET Core podstawowy samouczek
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 02b6b3fc9e149f5d1d5d78e310c7df257be983c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218547"
---
# <a name="learn-docker-basics-with-net-core"></a><span data-ttu-id="87708-103">Dowiedz się podstawy Docker z platformą .NET Core</span><span class="sxs-lookup"><span data-stu-id="87708-103">Learn Docker Basics with .NET Core</span></span>

<span data-ttu-id="87708-104">Ten samouczek zawiera Docker kontenera tworzenia i wdrażania zadania dla aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87708-104">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="87708-105">W trakcie tego samouczka dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="87708-105">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="87708-106">Jak utworzyć plik Dockerfile</span><span class="sxs-lookup"><span data-stu-id="87708-106">How to create a Dockerfile</span></span>
> * <span data-ttu-id="87708-107">Jak utworzyć aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87708-107">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="87708-108">Jak wdrożyć aplikację w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="87708-108">How to deploy your app into a Docker container.</span></span>

<span data-ttu-id="87708-109">[Platformy Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) używa [aparatem platformy Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) szybkie tworzenie i pakietu aplikacji jako [obrazy usługi Docker](https://docs.docker.com/glossary/?term=image).</span><span class="sxs-lookup"><span data-stu-id="87708-109">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="87708-110">Te obrazy są zapisywane [plik Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format, aby wdrożyć i uruchomić w [warstwie kontenera](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="87708-110">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="87708-111">Oprogramowanie .NET core: Najłatwiejszym sposobem na rozpoczęcie pracy</span><span class="sxs-lookup"><span data-stu-id="87708-111">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="87708-112">Przed utworzeniem obrazu Docker, należy containerize aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87708-112">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="87708-113">Można go utworzyć w systemie Linux, MacOS lub systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="87708-113">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="87708-114">Jest najszybszym i Najprostszym sposobem wykonania tego używać .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87708-114">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="87708-115">Jeśli znasz zestaw narzędzi interfejsu wiersza polecenia platformy .NET Core odczytu [Omówienie zestawu SDK programu .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="87708-115">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="87708-116">Można tworzyć kontenery w systemach Windows i Linux z [tagi na podstawie wielu arch](https://github.com/dotnet/announcements/issues/14).</span><span class="sxs-lookup"><span data-stu-id="87708-116">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="87708-117">Pierwszej aplikacji platformy .NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="87708-117">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="87708-118">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="87708-118">Prerequisites</span></span>

<span data-ttu-id="87708-119">Do ukończenia tego samouczka:</span><span class="sxs-lookup"><span data-stu-id="87708-119">To complete this tutorial:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="87708-120">.NET core 2.0 SDK</span><span class="sxs-lookup"><span data-stu-id="87708-120">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="87708-121">Zainstaluj [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="87708-121">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

<span data-ttu-id="87708-122">Zobacz [2.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) Pełna lista .NET Core 2.x obsługiwanych systemów operacyjnych, poza wersje obsługi systemu operacyjnego i łącza do zasad cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="87708-122">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="87708-123">Jeśli nie jest jeszcze, należy zainstalować w edytorze kodu ulubionych.</span><span class="sxs-lookup"><span data-stu-id="87708-123">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="87708-124">Należy zainstalować Edytor kodu?</span><span class="sxs-lookup"><span data-stu-id="87708-124">Need to install a code editor?</span></span> <span data-ttu-id="87708-125">Spróbuj [programu Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="87708-125">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="87708-126">Instalowanie klienta Docker</span><span class="sxs-lookup"><span data-stu-id="87708-126">Installing Docker Client</span></span>

<span data-ttu-id="87708-127">Zainstaluj [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) lub nowszego klienta Docker.</span><span class="sxs-lookup"><span data-stu-id="87708-127">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="87708-128">Klient Docker można zainstalować w:</span><span class="sxs-lookup"><span data-stu-id="87708-128">The Docker client can be installed in:</span></span>

* <span data-ttu-id="87708-129">Dystrybucje systemu Linux</span><span class="sxs-lookup"><span data-stu-id="87708-129">Linux distributions</span></span>

   * [<span data-ttu-id="87708-130">CentOS</span><span class="sxs-lookup"><span data-stu-id="87708-130">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="87708-131">Debian</span><span class="sxs-lookup"><span data-stu-id="87708-131">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="87708-132">Fedora</span><span class="sxs-lookup"><span data-stu-id="87708-132">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="87708-133">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="87708-133">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="87708-134">macOS</span><span class="sxs-lookup"><span data-stu-id="87708-134">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="87708-135">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="87708-135">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

### <a name="create-a-net-core-20-console-app-for-dockerization"></a><span data-ttu-id="87708-136">Tworzenie aplikacji konsoli .NET Core 2.0 dla Dockerization</span><span class="sxs-lookup"><span data-stu-id="87708-136">Create a .NET Core 2.0 console app for Dockerization</span></span>

<span data-ttu-id="87708-137">Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*.</span><span class="sxs-lookup"><span data-stu-id="87708-137">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="87708-138">Przejdź do folderu, który został utworzony i wpisz następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="87708-138">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="87708-139">Poznajmy Szybkie wskazówki:</span><span class="sxs-lookup"><span data-stu-id="87708-139">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="87708-140">[`dotnet new`](../tools/dotnet-new.md) Tworzy aktualne `Hello.csproj` pliku projektu z zależnościami, które są niezbędne do tworzenia aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="87708-140">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="87708-141">Tworzy również `Program.cs`, podstawowe plik zawierający punkt wejścia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87708-141">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="87708-142">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="87708-142">`Hello.csproj`:</span></span>

   <span data-ttu-id="87708-143">Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i kompilacji programu.</span><span class="sxs-lookup"><span data-stu-id="87708-143">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="87708-144">`OutputType` Określa tag tworzymy plik wykonywalny, innymi słowy aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="87708-144">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="87708-145">`TargetFramework` Tag Określa, jakie implementacji .NET możemy docelowych.</span><span class="sxs-lookup"><span data-stu-id="87708-145">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="87708-146">Realizując bardziej zaawansowany scenariusz można określić wiele platform docelowych i kompilacja — przejście do określonej struktury w ramach jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="87708-146">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="87708-147">W tym samouczku będziemy kompilacji dla programu .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="87708-147">In this tutorial, we build for .NET Core 2.0.</span></span>

   <span data-ttu-id="87708-148">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="87708-148">`Program.cs`:</span></span>

   <span data-ttu-id="87708-149">Program, który rozpoczyna się od `using System`.</span><span class="sxs-lookup"><span data-stu-id="87708-149">The program starts by `using System`.</span></span> <span data-ttu-id="87708-150">To zdanie oznacza, "Przenieś wszystko `System` przestrzeni nazw do zakresu dla tego pliku."</span><span class="sxs-lookup"><span data-stu-id="87708-150">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="87708-151">`System` Przestrzeń nazw zawiera podstawowe konstrukcji `string`, lub typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="87708-151">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="87708-152">Następnie definicję przestrzeni nazw o nazwie `Hello`.</span><span class="sxs-lookup"><span data-stu-id="87708-152">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="87708-153">Przestrzeń nazw, można zmienić na dowolnych znaków.</span><span class="sxs-lookup"><span data-stu-id="87708-153">You can change namespace to anything you want.</span></span> <span data-ttu-id="87708-154">Klasa o nazwie `Program` jest zdefiniowany w tej przestrzeni nazw z `Main` metody pobierającej tablicy ciągów jako jej argument.</span><span class="sxs-lookup"><span data-stu-id="87708-154">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="87708-155">Ta tablica zawiera listę argumentów przekazana wywołanego skompilowany program.</span><span class="sxs-lookup"><span data-stu-id="87708-155">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="87708-156">W naszym przykładzie program zapisuje tylko "Witaj świecie!"</span><span class="sxs-lookup"><span data-stu-id="87708-156">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="87708-157">w konsoli.</span><span class="sxs-lookup"><span data-stu-id="87708-157">to the console.</span></span>

2. `$ dotnet restore`

   <span data-ttu-id="87708-158">W .NET Core 2.x, **dotnet nowe** uruchamia [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="87708-158">In .NET Core 2.x, **dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="87708-159">**Przywracanie DotNet** przywraca drzewie zależności z [NuGet](https://www.nuget.org/)wywołania (.NET Menedżera pakietów).</span><span class="sxs-lookup"><span data-stu-id="87708-159">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="87708-160">NuGet wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="87708-160">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="87708-161">analizuje *Hello.csproj* pliku</span><span class="sxs-lookup"><span data-stu-id="87708-161">analyzes the *Hello.csproj* file</span></span> 
   * <span data-ttu-id="87708-162">pobiera plik zależności (lub chwyty z pamięci podręcznej komputera)</span><span class="sxs-lookup"><span data-stu-id="87708-162">downloads the file dependencies (or grabs from your machine cache)</span></span>
   * <span data-ttu-id="87708-163">zapisuje *obj/project.assets.json* pliku</span><span class="sxs-lookup"><span data-stu-id="87708-163">writes the *obj/project.assets.json* file</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   <span data-ttu-id="87708-164">*Project.assets.json* plików jest pełny zestaw wykres zależności NuGet rozwiązania powiązania i innych metadanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87708-164">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="87708-165">To wymagane, plik jest używany przez innych narzędzi, takich jak [ `dotnet build` ](../tools/dotnet-build.md) i [ `dotnet run` ](../tools/dotnet-run.md), aby poprawnie przetworzyć kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="87708-165">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="87708-166">[`dotnet run`](../tools/dotnet-run.md) wywołania [ `dotnet build` ](../tools/dotnet-build.md) o potwierdzenie pomyślnego utworzenia kompilacji, a następnie wywołania `dotnet <assembly.dll>` do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87708-166">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    <span data-ttu-id="87708-167">Dla zaawansowanych scenariuszy, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="87708-167">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="87708-168">Dockerize aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="87708-168">Dockerize the .NET Core application</span></span>

<span data-ttu-id="87708-169">Aplikacja konsoli Hello .NET Core pomyślnie działa lokalnie.</span><span class="sxs-lookup"><span data-stu-id="87708-169">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="87708-170">Teraz załóżmy zabrać krok dalsze i skompilować i uruchomić aplikację w Docker.</span><span class="sxs-lookup"><span data-stu-id="87708-170">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="87708-171">Twoje pierwszy plik Dockerfile</span><span class="sxs-lookup"><span data-stu-id="87708-171">Your first Dockerfile</span></span>

<span data-ttu-id="87708-172">Otwórz w edytorze tekstów i do dzieła!</span><span class="sxs-lookup"><span data-stu-id="87708-172">Open your text editor and let's get started!</span></span> <span data-ttu-id="87708-173">Nadal trwają prace z katalogu Hello możemy tworzone w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87708-173">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="87708-174">Dodaj następujące instrukcje Docker albo Linux lub [kontenery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) do nowego pliku.</span><span class="sxs-lookup"><span data-stu-id="87708-174">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="87708-175">Po zakończeniu zapisz go w folderze głównym katalogiem Hello jako **plik Dockerfile**, bez rozszerzenia (konieczne może być równa danego typu pliku `All types (*.*)` lub coś podobnego).</span><span class="sxs-lookup"><span data-stu-id="87708-175">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

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

<span data-ttu-id="87708-176">Plik Dockerfile zawiera instrukcje kompilacji Docker, które są wykonywane sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="87708-176">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="87708-177">Pierwsza instrukcja musi być [ **FROM**](https://docs.docker.com/engine/reference/builder/#from).</span><span class="sxs-lookup"><span data-stu-id="87708-177">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="87708-178">Ta instrukcja inicjuje nowy etap kompilacji i ustawia obraz podstawowy dla pozostałych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="87708-178">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="87708-179">Tagi wielu architektury ściągnięcia kontenery systemu Windows lub Linux, w zależności od platformy Docker dla systemu Windows [tryb kontenera](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span><span class="sxs-lookup"><span data-stu-id="87708-179">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="87708-180">Obraz podstawowy dla naszej próbki jest obrazem zestawu sdk 2.0 z repozytorium microsoft/dotnet</span><span class="sxs-lookup"><span data-stu-id="87708-180">The Base Image for our sample is the 2.0-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

<span data-ttu-id="87708-181">[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) instrukcji Ustawia katalog roboczy dla wszelkie pozostałe wykonywania, CMD, punktu wejścia, KOPIOWANIA i Dodaj plik Dockerfile instrukcje.</span><span class="sxs-lookup"><span data-stu-id="87708-181">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="87708-182">Jeśli katalog nie istnieje, zostanie on utworzony.</span><span class="sxs-lookup"><span data-stu-id="87708-182">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="87708-183">W takim przypadku WORKDIR ustawiono do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87708-183">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="87708-184">[ **KOPIOWANIA** ](https://docs.docker.com/engine/reference/builder/#copy) instrukcji kopiuje nowe pliki lub katalogi ze ścieżki źródłowej i dodaje je do plików kontenera docelowego.</span><span class="sxs-lookup"><span data-stu-id="87708-184">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="87708-185">Z tej instrukcji Trwa kopiowanie plików projektu C# do kontenera.</span><span class="sxs-lookup"><span data-stu-id="87708-185">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="87708-186">[ **Uruchom** ](https://docs.docker.com/engine/reference/builder/#run) instrukcji wykonuje żadnych poleceń w nową warstwę ponad bieżący obraz i zatwierdź wyniki.</span><span class="sxs-lookup"><span data-stu-id="87708-186">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="87708-187">Obraz wynikowy zatwierdzone służy do następnego kroku w plik Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="87708-187">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="87708-188">Uruchamiamy **przywracania dotnet** uzyskać wymagane zależności pliku projektu C#.</span><span class="sxs-lookup"><span data-stu-id="87708-188">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span> 

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="87708-189">To **KOPIOWANIA** instrukcji kopiuje pozostałych plików do naszej kontenera do nowych [warstwy](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span><span class="sxs-lookup"><span data-stu-id="87708-189">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="87708-190">Firma Microsoft publikowania aplikacji z tym **Uruchom** instrukcji.</span><span class="sxs-lookup"><span data-stu-id="87708-190">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="87708-191">[ **Publikowania dotnet** ](../tools/dotnet-publish.md) polecenie kompiluje aplikacji odczytuje za pośrednictwem jego zależności, określona w pliku projektu i publikuje Wynikowy zestaw plików w katalogu.</span><span class="sxs-lookup"><span data-stu-id="87708-191">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="87708-192">Naszej aplikacji jest publikowany razem **wersji** konfiguracji i dane wyjściowe do domyślnego katalogu.</span><span class="sxs-lookup"><span data-stu-id="87708-192">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="87708-193">[ **Punktu wejścia** ](https://docs.docker.com/engine/reference/builder/#entrypoint) instrukcji umożliwia kontener uruchamianie jako plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="87708-193">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="87708-194">Teraz masz plik Dockerfile który:</span><span class="sxs-lookup"><span data-stu-id="87708-194">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="87708-195">Kopiuje obraz aplikacji</span><span class="sxs-lookup"><span data-stu-id="87708-195">copies your app to the image</span></span>
* <span data-ttu-id="87708-196">zależności aplikacji do obrazu</span><span class="sxs-lookup"><span data-stu-id="87708-196">your app's dependencies to the image</span></span>
* <span data-ttu-id="87708-197">Tworzy aplikację do uruchamiania jako plik wykonywalny</span><span class="sxs-lookup"><span data-stu-id="87708-197">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-20-app"></a><span data-ttu-id="87708-198">Tworzenie i uruchamianie aplikacji Hello .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="87708-198">Build and run the Hello .NET Core 2.0 app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="87708-199">Niezbędne polecenia Docker</span><span class="sxs-lookup"><span data-stu-id="87708-199">Essential Docker commands</span></span>

<span data-ttu-id="87708-200">Te polecenia Docker są niezbędne:</span><span class="sxs-lookup"><span data-stu-id="87708-200">These Docker commands are essential:</span></span>

* [<span data-ttu-id="87708-201">docker kompilacji</span><span class="sxs-lookup"><span data-stu-id="87708-201">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="87708-202">Uruchom docker</span><span class="sxs-lookup"><span data-stu-id="87708-202">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="87708-203">docker ps</span><span class="sxs-lookup"><span data-stu-id="87708-203">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="87708-204">Zatrzymaj docker</span><span class="sxs-lookup"><span data-stu-id="87708-204">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="87708-205">docker rm</span><span class="sxs-lookup"><span data-stu-id="87708-205">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="87708-206">docker rmi</span><span class="sxs-lookup"><span data-stu-id="87708-206">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="87708-207">Obraz docker</span><span class="sxs-lookup"><span data-stu-id="87708-207">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="87708-208">Tworzenie i uruchamianie</span><span class="sxs-lookup"><span data-stu-id="87708-208">Build and run</span></span>

<span data-ttu-id="87708-209">Zapisano plik dockerfile; teraz Docker tworzy aplikację, a następnie uruchomi kontener.</span><span class="sxs-lookup"><span data-stu-id="87708-209">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="87708-210">Dane wyjściowe z `docker build` polecenia powinny być podobne do następujących danych wyjściowych konsoli:</span><span class="sxs-lookup"><span data-stu-id="87708-210">The output from the `docker build` command should be similar to the following console output:</span></span>

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

<span data-ttu-id="87708-211">Jak widać z danych wyjściowych, aparatem platformy Docker używane plik Dockerfile do budowania naszych kontenera.</span><span class="sxs-lookup"><span data-stu-id="87708-211">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="87708-212">Dane wyjściowe z `docker run` polecenia powinny być podobne do następujących danych wyjściowych konsoli:</span><span class="sxs-lookup"><span data-stu-id="87708-212">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="87708-213">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="87708-213">Congratulations!</span></span> <span data-ttu-id="87708-214">masz tylko:</span><span class="sxs-lookup"><span data-stu-id="87708-214">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="87708-215">Utworzyć lokalnej aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="87708-215">Created a local .NET Core app</span></span>
> * <span data-ttu-id="87708-216">Utworzony plik Dockerfile do kompilacji z pierwszego kontenera</span><span class="sxs-lookup"><span data-stu-id="87708-216">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="87708-217">Wbudowane i uruchomiono aplikację Dockerized</span><span class="sxs-lookup"><span data-stu-id="87708-217">Built and ran your Dockerized app</span></span>



## <a name="next-steps"></a><span data-ttu-id="87708-218">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="87708-218">Next Steps</span></span>

<span data-ttu-id="87708-219">Poniżej przedstawiono niektóre czynności, które można wykonać:</span><span class="sxs-lookup"><span data-stu-id="87708-219">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="87708-220">Wprowadzenie do platformy .NET Docker obrazów wideo</span><span class="sxs-lookup"><span data-stu-id="87708-220">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="87708-221">Visual Studio, Docker i wystąpień kontenera Azure lepsze razem!</span><span class="sxs-lookup"><span data-stu-id="87708-221">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [<span data-ttu-id="87708-222">Docker dla skrócone podręczniki platformy Azure</span><span class="sxs-lookup"><span data-stu-id="87708-222">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="87708-223">Wdrażanie aplikacji na Docker na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="87708-223">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> <span data-ttu-id="87708-224">Jeśli nie masz subskrypcji platformy Azure, [Zarejestruj się już dziś](https://azure.microsoft.com/free/?b=16.48) bezpłatnej 30-dniowe konto i 200 USD interweniować środków Azure wypróbowanie dowolną kombinację usługami Azure.</span><span class="sxs-lookup"><span data-stu-id="87708-224">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="87708-225">Używane w tym przykładzie obrazy usługi docker</span><span class="sxs-lookup"><span data-stu-id="87708-225">Docker Images used in this sample</span></span>

<span data-ttu-id="87708-226">Na poniższych ilustracjach Docker są używane w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="87708-226">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="87708-227">Powiązane zasoby</span><span class="sxs-lookup"><span data-stu-id="87708-227">Related Resources</span></span>

* [<span data-ttu-id="87708-228">Przykłady .NET core Docker</span><span class="sxs-lookup"><span data-stu-id="87708-228">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [<span data-ttu-id="87708-229">Plik Dockerfile kontenerów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="87708-229">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="87708-230">Przykłady programu .NET framework Docker</span><span class="sxs-lookup"><span data-stu-id="87708-230">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="87708-231">Platformy ASP.NET Core na DockerHub</span><span class="sxs-lookup"><span data-stu-id="87708-231">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="87708-232">Dockerize aplikację .NET Core — samouczek Docker</span><span class="sxs-lookup"><span data-stu-id="87708-232">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="87708-233">Praca z narzędzia Docker programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="87708-233">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="87708-234">Wdrażanie obrazów Docker z rejestru kontenera platformy Azure do wystąpień kontenera platformy Azure</span><span class="sxs-lookup"><span data-stu-id="87708-234">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)