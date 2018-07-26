---
title: Dowiedz się, podstawy platformy Docker z platformą .NET Core
description: Platforma Docker i platformy .NET Core podstawowego samouczka
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 02b6b3fc9e149f5d1d5d78e310c7df257be983c1
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961550"
---
# <a name="learn-docker-basics-with-net-core"></a><span data-ttu-id="8c70e-103">Dowiedz się, podstawy platformy Docker z platformą .NET Core</span><span class="sxs-lookup"><span data-stu-id="8c70e-103">Learn Docker Basics with .NET Core</span></span>

<span data-ttu-id="8c70e-104">W tym samouczku pokazano Docker kontenera, twórz i wdrażaj zadania dla aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c70e-104">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="8c70e-105">W trakcie tego samouczka dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="8c70e-105">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="8c70e-106">Jak utworzyć plik Dockerfile</span><span class="sxs-lookup"><span data-stu-id="8c70e-106">How to create a Dockerfile</span></span>
> * <span data-ttu-id="8c70e-107">Jak utworzyć aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c70e-107">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="8c70e-108">Jak wdrożyć aplikację w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="8c70e-108">How to deploy your app into a Docker container.</span></span>

<span data-ttu-id="8c70e-109">[Platforma Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) używa [aparat platformy Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) umożliwiają szybkie tworzenie i pakowanie aplikacji jako [obrazów platformy Docker](https://docs.docker.com/glossary/?term=image).</span><span class="sxs-lookup"><span data-stu-id="8c70e-109">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="8c70e-110">Te obrazy są zapisywane [pliku Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format zostaną wdrożone i uruchomione [warstwie kontenerów](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="8c70e-110">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="8c70e-111">.NET core: Najłatwiejszym sposobem na rozpoczęcie pracy</span><span class="sxs-lookup"><span data-stu-id="8c70e-111">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="8c70e-112">Przed utworzeniem obrazu platformy Docker, należy konteneryzowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c70e-112">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="8c70e-113">Można je utworzyć w systemie Linux, MacOS lub Windows.</span><span class="sxs-lookup"><span data-stu-id="8c70e-113">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="8c70e-114">Najszybszym i najłatwiejszym sposobem wykonania tego zadania jest korzystanie z platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c70e-114">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="8c70e-115">Jeśli jesteś zaznajomiony z zestawu narzędzi interfejsu wiersza polecenia platformy .NET Core, zapoznaj się z [Omówienie zestawu .NET Core SDK](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="8c70e-115">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="8c70e-116">Możesz tworzyć kontenery systemów Windows i Linux za pomocą [wielu arch na podstawie tagów](https://github.com/dotnet/announcements/issues/14).</span><span class="sxs-lookup"><span data-stu-id="8c70e-116">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="8c70e-117">Twoja pierwsza aplikacja platformy .NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="8c70e-117">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="8c70e-118">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8c70e-118">Prerequisites</span></span>

<span data-ttu-id="8c70e-119">Do ukończenia tego samouczka:</span><span class="sxs-lookup"><span data-stu-id="8c70e-119">To complete this tutorial:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="8c70e-120">.NET core 2.0 SDK</span><span class="sxs-lookup"><span data-stu-id="8c70e-120">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="8c70e-121">Zainstaluj [platformy .NET Core SDK 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="8c70e-121">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

<span data-ttu-id="8c70e-122">Zobacz [obsługiwanych wersjach systemu operacyjnego programu .NET Core 2.x](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) kompletną listę platformy .NET Core 2.x obsługiwane systemy operacyjne, poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="8c70e-122">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="8c70e-123">Wybrany edytor kodu, należy zainstalować, jeśli jeszcze go.</span><span class="sxs-lookup"><span data-stu-id="8c70e-123">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="8c70e-124">Należy zainstalować Edytor kodu?</span><span class="sxs-lookup"><span data-stu-id="8c70e-124">Need to install a code editor?</span></span> <span data-ttu-id="8c70e-125">Spróbuj [programu Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="8c70e-125">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="8c70e-126">Instalowanie klienta platformy Docker</span><span class="sxs-lookup"><span data-stu-id="8c70e-126">Installing Docker Client</span></span>

<span data-ttu-id="8c70e-127">Zainstaluj [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) lub nowszego klienta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="8c70e-127">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="8c70e-128">Klient platformy Docker można zainstalować w:</span><span class="sxs-lookup"><span data-stu-id="8c70e-128">The Docker client can be installed in:</span></span>

* <span data-ttu-id="8c70e-129">Dystrybucje systemu Linux</span><span class="sxs-lookup"><span data-stu-id="8c70e-129">Linux distributions</span></span>

   * [<span data-ttu-id="8c70e-130">CentOS</span><span class="sxs-lookup"><span data-stu-id="8c70e-130">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="8c70e-131">Debian</span><span class="sxs-lookup"><span data-stu-id="8c70e-131">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="8c70e-132">Fedora</span><span class="sxs-lookup"><span data-stu-id="8c70e-132">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="8c70e-133">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="8c70e-133">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="8c70e-134">macOS</span><span class="sxs-lookup"><span data-stu-id="8c70e-134">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="8c70e-135">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="8c70e-135">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

### <a name="create-a-net-core-20-console-app-for-dockerization"></a><span data-ttu-id="8c70e-136">Tworzenie aplikacji konsolowej .NET Core 2.0 dla Dockerization</span><span class="sxs-lookup"><span data-stu-id="8c70e-136">Create a .NET Core 2.0 console app for Dockerization</span></span>

<span data-ttu-id="8c70e-137">Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*.</span><span class="sxs-lookup"><span data-stu-id="8c70e-137">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="8c70e-138">Przejdź do folderu, który został utworzony, a następnie wpisz następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="8c70e-138">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="8c70e-139">Zróbmy szybkiego przewodnika:</span><span class="sxs-lookup"><span data-stu-id="8c70e-139">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="8c70e-140">[`dotnet new`](../tools/dotnet-new.md) Tworzy aktualnej `Hello.csproj` pliku projektu z zależnościami, które są niezbędne do tworzenia aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="8c70e-140">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="8c70e-141">Tworzy również `Program.cs`, podstawowy plik zawierający punkt wejścia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c70e-141">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="8c70e-142">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="8c70e-142">`Hello.csproj`:</span></span>

   <span data-ttu-id="8c70e-143">Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i kompilacji programu.</span><span class="sxs-lookup"><span data-stu-id="8c70e-143">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="8c70e-144">`OutputType` Tag Określa, czy tworzymy plik wykonywalny, innymi słowy aplikację konsolową w języku.</span><span class="sxs-lookup"><span data-stu-id="8c70e-144">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="8c70e-145">`TargetFramework` Tagów Określa, jakie firma Microsoft objęci implementacja programu .NET.</span><span class="sxs-lookup"><span data-stu-id="8c70e-145">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="8c70e-146">W zaawansowanym scenariuszu można określić wielu platform docelowych i kompilacja — przejście do określonej struktury, w ramach jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="8c70e-146">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="8c70e-147">W tym samouczku, firma Microsoft tworzy dla platformy .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="8c70e-147">In this tutorial, we build for .NET Core 2.0.</span></span>

   <span data-ttu-id="8c70e-148">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="8c70e-148">`Program.cs`:</span></span>

   <span data-ttu-id="8c70e-149">Program, który rozpoczyna się od `using System`.</span><span class="sxs-lookup"><span data-stu-id="8c70e-149">The program starts by `using System`.</span></span> <span data-ttu-id="8c70e-150">To zdanie oznacza, "Przenieś wszystko `System` przestrzeni nazw do zakresu dla tego pliku."</span><span class="sxs-lookup"><span data-stu-id="8c70e-150">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="8c70e-151">`System` Przestrzeń nazw zawiera podstawowymi konstrukcjami `string`, lub typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="8c70e-151">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="8c70e-152">Następnie definiujemy przestrzeń nazwy wywołaną `Hello`.</span><span class="sxs-lookup"><span data-stu-id="8c70e-152">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="8c70e-153">Można zmienić nazw, do żadnego elementu, który ma.</span><span class="sxs-lookup"><span data-stu-id="8c70e-153">You can change namespace to anything you want.</span></span> <span data-ttu-id="8c70e-154">Klasa o nazwie `Program` jest zdefiniowana w ramach tej przestrzeni nazw za pomocą `Main` metody, która przyjmuje tablicę ciągów, jako argumentem.</span><span class="sxs-lookup"><span data-stu-id="8c70e-154">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="8c70e-155">Ta tablica zawiera listę argumentów przekazywanych do wywołanego skompilowanego programu.</span><span class="sxs-lookup"><span data-stu-id="8c70e-155">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="8c70e-156">W tym przykładzie program zapisuje tylko "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="8c70e-156">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="8c70e-157">w konsoli.</span><span class="sxs-lookup"><span data-stu-id="8c70e-157">to the console.</span></span>

2. `$ dotnet restore`

   <span data-ttu-id="8c70e-158">W .NET Core 2.x, **dotnet nowe** uruchamia [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="8c70e-158">In .NET Core 2.x, **dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="8c70e-159">**DotNet restore** przywraca drzewo zależności za pomocą [NuGet](https://www.nuget.org/)wywołania (Menedżer pakietów dla platformy .NET).</span><span class="sxs-lookup"><span data-stu-id="8c70e-159">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="8c70e-160">NuGet wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="8c70e-160">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="8c70e-161">analizuje *Hello.csproj* pliku</span><span class="sxs-lookup"><span data-stu-id="8c70e-161">analyzes the *Hello.csproj* file</span></span> 
   * <span data-ttu-id="8c70e-162">pobiera plik zależności (lub chwyty z pamięci podręcznej komputera)</span><span class="sxs-lookup"><span data-stu-id="8c70e-162">downloads the file dependencies (or grabs from your machine cache)</span></span>
   * <span data-ttu-id="8c70e-163">zapisuje *obj/project.assets.json* pliku</span><span class="sxs-lookup"><span data-stu-id="8c70e-163">writes the *obj/project.assets.json* file</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   <span data-ttu-id="8c70e-164">*Project.assets.json* plik jest kompletny zestaw wykres zależności NuGet, powiązania rozwiązania i innych metadanych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c70e-164">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="8c70e-165">To wymagane, plik jest używany przez innych narzędzi, takich jak [ `dotnet build` ](../tools/dotnet-build.md) i [ `dotnet run` ](../tools/dotnet-run.md), aby poprawnie przetworzyć kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="8c70e-165">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="8c70e-166">[`dotnet run`](../tools/dotnet-run.md) wywołania [ `dotnet build` ](../tools/dotnet-build.md) celu potwierdzenia pomyślnej kompilacji, a następnie wywołania `dotnet <assembly.dll>` do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c70e-166">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    <span data-ttu-id="8c70e-167">W przypadku zaawansowanych scenariuszy, zobacz [wdrożenie aplikacji programu .NET Core](../deploying/index.md) Aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="8c70e-167">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="8c70e-168">Przekształcać aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="8c70e-168">Dockerize the .NET Core application</span></span>

<span data-ttu-id="8c70e-169">Aplikację konsoli Hello platformy .NET Core pomyślnie działa lokalnie.</span><span class="sxs-lookup"><span data-stu-id="8c70e-169">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="8c70e-170">Teraz sklonujemy zabrać krok dalej i kompilowanie i uruchamianie aplikacji na platformie Docker.</span><span class="sxs-lookup"><span data-stu-id="8c70e-170">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="8c70e-171">Z pierwszego pliku Dockerfile</span><span class="sxs-lookup"><span data-stu-id="8c70e-171">Your first Dockerfile</span></span>

<span data-ttu-id="8c70e-172">Otwórz Edytor tekstu i zaczynajmy!</span><span class="sxs-lookup"><span data-stu-id="8c70e-172">Open your text editor and let's get started!</span></span> <span data-ttu-id="8c70e-173">Wciąż pracujemy z katalogu Witaj, którą utworzyliśmy aplikację w.</span><span class="sxs-lookup"><span data-stu-id="8c70e-173">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="8c70e-174">Dodaj następujące instrukcje dotyczące platformy Docker dla dowolnego systemu Linux lub [kontenery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) do nowego pliku.</span><span class="sxs-lookup"><span data-stu-id="8c70e-174">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="8c70e-175">Gdy skończysz, zapisz go w katalogu głównym katalogiem Hello jako **pliku Dockerfile**, bez rozszerzenia (może być konieczne ustawienie typu Twojego pliku `All types (*.*)` lub innego ogranicznika).</span><span class="sxs-lookup"><span data-stu-id="8c70e-175">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

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

<span data-ttu-id="8c70e-176">Plik Dockerfile zawiera instrukcje dotyczące kompilacji platformy Docker, które uruchamiają się po kolei.</span><span class="sxs-lookup"><span data-stu-id="8c70e-176">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="8c70e-177">Pierwsza instrukcja musi być [ **FROM**](https://docs.docker.com/engine/reference/builder/#from).</span><span class="sxs-lookup"><span data-stu-id="8c70e-177">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="8c70e-178">Ta instrukcja inicjuje nowy etap kompilacji i ustawiania obrazu podstawowego dla pozostałych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8c70e-178">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="8c70e-179">Tagi wielu architektury ściągnięcia kontenery Windows lub Linux, w zależności od platformy Docker for Windows [tryb kontenera](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span><span class="sxs-lookup"><span data-stu-id="8c70e-179">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="8c70e-180">Obrazu podstawowego w przypadku naszej próbki jest styl obrazowy zestawu sdk w wersji 2.0 z repozytorium dotnet/firmy microsoft</span><span class="sxs-lookup"><span data-stu-id="8c70e-180">The Base Image for our sample is the 2.0-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

<span data-ttu-id="8c70e-181">[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) instrukcja Ustawia katalog roboczy dla wszelkie pozostałe przebiegu, CMD, ENTRYPOINT, KOPIOWANIA i Dodaj plik Dockerfile instrukcje.</span><span class="sxs-lookup"><span data-stu-id="8c70e-181">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="8c70e-182">Jeśli katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="8c70e-182">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="8c70e-183">W tym przypadku WORKDIR ustawiono katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c70e-183">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="8c70e-184">[ **KOPIOWANIA** ](https://docs.docker.com/engine/reference/builder/#copy) instrukcji kopiowania nowych plików lub katalogów ze ścieżki źródłowej i dodaje je do systemu plików kontenera docelowego.</span><span class="sxs-lookup"><span data-stu-id="8c70e-184">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="8c70e-185">Za pomocą tej instrukcji Trwa kopiowanie pliku projektu C# do kontenera.</span><span class="sxs-lookup"><span data-stu-id="8c70e-185">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="8c70e-186">[ **Uruchom** ](https://docs.docker.com/engine/reference/builder/#run) instrukcji wykonuje wszystkie polecenia w nowej warstwie na podstawie bieżącego obrazu i zatwierdź wyniki.</span><span class="sxs-lookup"><span data-stu-id="8c70e-186">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="8c70e-187">Zatwierdzony obraz wynikowy jest używana do następnego kroku w pliku Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="8c70e-187">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="8c70e-188">Będziemy działają **dotnet restore** można pobrać wymagane zależności pliku projektu C#.</span><span class="sxs-lookup"><span data-stu-id="8c70e-188">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span> 

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="8c70e-189">To **KOPIOWANIA** instrukcji kopiuje pozostałą część plików do nasz kontener do nowego [warstwy](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span><span class="sxs-lookup"><span data-stu-id="8c70e-189">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="8c70e-190">Obecnie publikujemy aplikację z tym **Uruchom** instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8c70e-190">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="8c70e-191">[ **Publikowania dotnet** ](../tools/dotnet-publish.md) polecenie kompiluje aplikację, czyta za pośrednictwem jego zależności, które określono w pliku projektu i publikuje Wynikowy zestaw plików w katalogu.</span><span class="sxs-lookup"><span data-stu-id="8c70e-191">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="8c70e-192">Nasza aplikacja jest publikowana z **wersji** konfiguracji i dane wyjściowe do domyślnego katalogu.</span><span class="sxs-lookup"><span data-stu-id="8c70e-192">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="8c70e-193">[ **Punktu wejścia** ](https://docs.docker.com/engine/reference/builder/#entrypoint) instrukcji umożliwia kontener, aby działał jako plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="8c70e-193">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="8c70e-194">Teraz masz plik Dockerfile który:</span><span class="sxs-lookup"><span data-stu-id="8c70e-194">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="8c70e-195">Kopiuje obraz aplikacji</span><span class="sxs-lookup"><span data-stu-id="8c70e-195">copies your app to the image</span></span>
* <span data-ttu-id="8c70e-196">zależności aplikacji do obrazu</span><span class="sxs-lookup"><span data-stu-id="8c70e-196">your app's dependencies to the image</span></span>
* <span data-ttu-id="8c70e-197">Tworzy aplikację, aby działał jako plik wykonywalny</span><span class="sxs-lookup"><span data-stu-id="8c70e-197">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-20-app"></a><span data-ttu-id="8c70e-198">Kompilowanie i uruchamianie aplikacji Hello .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8c70e-198">Build and run the Hello .NET Core 2.0 app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="8c70e-199">Podstawowe polecenia platformy Docker</span><span class="sxs-lookup"><span data-stu-id="8c70e-199">Essential Docker commands</span></span>

<span data-ttu-id="8c70e-200">Te polecenia Docker są istotne:</span><span class="sxs-lookup"><span data-stu-id="8c70e-200">These Docker commands are essential:</span></span>

* [<span data-ttu-id="8c70e-201">kompilacji platformy docker</span><span class="sxs-lookup"><span data-stu-id="8c70e-201">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="8c70e-202">Uruchamianie platformy docker</span><span class="sxs-lookup"><span data-stu-id="8c70e-202">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="8c70e-203">docker ps</span><span class="sxs-lookup"><span data-stu-id="8c70e-203">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="8c70e-204">Zatrzymaj platformy docker</span><span class="sxs-lookup"><span data-stu-id="8c70e-204">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="8c70e-205">Menedżer zasobów platformy docker</span><span class="sxs-lookup"><span data-stu-id="8c70e-205">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="8c70e-206">rmi platformy docker</span><span class="sxs-lookup"><span data-stu-id="8c70e-206">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="8c70e-207">Obraz platformy docker</span><span class="sxs-lookup"><span data-stu-id="8c70e-207">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="8c70e-208">Kompilowanie i uruchamianie</span><span class="sxs-lookup"><span data-stu-id="8c70e-208">Build and run</span></span>

<span data-ttu-id="8c70e-209">Zapisano plik dockerfile; teraz Docker tworzy aplikację, a następnie uruchamia kontener.</span><span class="sxs-lookup"><span data-stu-id="8c70e-209">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="8c70e-210">Dane wyjściowe z `docker build` polecenia powinny być podobne do następujących danych wyjściowych konsoli:</span><span class="sxs-lookup"><span data-stu-id="8c70e-210">The output from the `docker build` command should be similar to the following console output:</span></span>

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

<span data-ttu-id="8c70e-211">Jak widać z danych wyjściowych, aparat platformy Docker umożliwiających tworzenie nasz kontener pliku Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="8c70e-211">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="8c70e-212">Dane wyjściowe z `docker run` polecenia powinny być podobne do następujących danych wyjściowych konsoli:</span><span class="sxs-lookup"><span data-stu-id="8c70e-212">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="8c70e-213">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="8c70e-213">Congratulations!</span></span> <span data-ttu-id="8c70e-214">masz tylko:</span><span class="sxs-lookup"><span data-stu-id="8c70e-214">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8c70e-215">Utworzone lokalnej aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="8c70e-215">Created a local .NET Core app</span></span>
> * <span data-ttu-id="8c70e-216">Utworzony plik Dockerfile, aby utworzyć swój pierwszy kontener</span><span class="sxs-lookup"><span data-stu-id="8c70e-216">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="8c70e-217">Wbudowane i uruchomiono aplikację Dockerized</span><span class="sxs-lookup"><span data-stu-id="8c70e-217">Built and ran your Dockerized app</span></span>



## <a name="next-steps"></a><span data-ttu-id="8c70e-218">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8c70e-218">Next Steps</span></span>

<span data-ttu-id="8c70e-219">Poniżej przedstawiono niektóre kolejne kroki, które należy wykonać:</span><span class="sxs-lookup"><span data-stu-id="8c70e-219">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="8c70e-220">Wprowadzenie do platformy Docker .NET obrazów, wideo</span><span class="sxs-lookup"><span data-stu-id="8c70e-220">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="8c70e-221">Visual Studio, platformy Docker i Azure Container Instances razem lepiej!</span><span class="sxs-lookup"><span data-stu-id="8c70e-221">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [<span data-ttu-id="8c70e-222">Docker for pakiety Azure Quickstarts</span><span class="sxs-lookup"><span data-stu-id="8c70e-222">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="8c70e-223">Wdrażanie aplikacji na platformy Docker na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="8c70e-223">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> <span data-ttu-id="8c70e-224">Jeśli nie masz subskrypcji platformy Azure, [Zarejestruj się dzisiaj](https://azure.microsoft.com/free/?b=16.48) bezpłatne konto 30-dniowej i Odbierz 200 USD środków na korzystanie z platformy Azure możesz wypróbować dowolną kombinację usług platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="8c70e-224">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="8c70e-225">Obrazy platformy docker, używane w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="8c70e-225">Docker Images used in this sample</span></span>

<span data-ttu-id="8c70e-226">Następujące obrazy platformy Docker są używane w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="8c70e-226">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="8c70e-227">Powiązane zasoby</span><span class="sxs-lookup"><span data-stu-id="8c70e-227">Related Resources</span></span>

* [<span data-ttu-id="8c70e-228">Przykłady Docker w programie .NET core</span><span class="sxs-lookup"><span data-stu-id="8c70e-228">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [<span data-ttu-id="8c70e-229">Plik Dockerfile kontenerów Windows</span><span class="sxs-lookup"><span data-stu-id="8c70e-229">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="8c70e-230">Przykłady Docker w programie .NET framework</span><span class="sxs-lookup"><span data-stu-id="8c70e-230">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="8c70e-231">Platforma ASP.NET Core w witrynie DockerHub</span><span class="sxs-lookup"><span data-stu-id="8c70e-231">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="8c70e-232">Przekształcać aplikacji .NET Core — samouczek platformy Docker</span><span class="sxs-lookup"><span data-stu-id="8c70e-232">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="8c70e-233">Praca z narzędzia Docker programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8c70e-233">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="8c70e-234">Wdrażanie obrazów platformy Docker z rejestru kontenerów platformy Azure w usłudze Azure Container Instances</span><span class="sxs-lookup"><span data-stu-id="8c70e-234">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)