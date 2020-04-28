---
title: Konteneryzowanie aplikacji przy użyciu samouczka platformy Docker
description: W tym samouczku dowiesz się, jak konteneryzowanie aplikację .NET Core z platformą Docker.
ms.date: 04/27/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5e6648539af45f3ce615bfc183e6f95a62b085a
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200031"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="6f3e8-103">Samouczek: Konteneryzowanie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="6f3e8-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="6f3e8-104">W tym samouczku dowiesz się, jak konteneryzowanie aplikację .NET Core z platformą Docker.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-104">In this tutorial, you'll learn how to containerize a .NET Core application with Docker.</span></span> <span data-ttu-id="6f3e8-105">Kontenery mają wiele funkcji i korzyści, takie jak niezmienne infrastruktury, zapewniające przenośną architekturę i umożliwiające skalowalność.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-105">Containers have many features and benefits, such as being an immutable infrastructure, providing a portable architecture, and enabling scalability.</span></span> <span data-ttu-id="6f3e8-106">Obraz może służyć do tworzenia kontenerów dla lokalnego środowiska projektowego, chmury prywatnej lub chmury publicznej.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-106">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="6f3e8-107">W tym samouczku zostały wykonane następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-107">In this tutorial, you:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="6f3e8-108">Tworzenie i publikowanie prostej aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="6f3e8-108">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="6f3e8-109">Tworzenie i konfigurowanie pliku dockerfile dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="6f3e8-109">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="6f3e8-110">Kompilowanie obrazu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="6f3e8-110">Build a Docker image</span></span>
> - <span data-ttu-id="6f3e8-111">Tworzenie i uruchamianie kontenera platformy Docker</span><span class="sxs-lookup"><span data-stu-id="6f3e8-111">Create and run a Docker container</span></span>

<span data-ttu-id="6f3e8-112">Zapoznaj się z tematem tworzenie i wdrażanie kontenerów platformy Docker dla aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-112">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="6f3e8-113">*Platforma Docker* korzysta z *aparatu platformy Docker* , aby szybko kompilować i spakować aplikacje jako *obrazy platformy Docker*.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-113">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="6f3e8-114">Te obrazy są zapisywane w formacie *pliku dockerfile* , który ma zostać wdrożony i uruchomiony w kontenerze warstwowym.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-114">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!NOTE]
> <span data-ttu-id="6f3e8-115">Ten samouczek **nie dotyczy** aplikacji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-115">This tutorial **is not** for ASP.NET Core apps.</span></span> <span data-ttu-id="6f3e8-116">Jeśli używasz ASP.NET Core, zapoznaj się z samouczkiem [uczenie się, jak konteneryzowanie aplikacji ASP.NET Core](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .</span><span class="sxs-lookup"><span data-stu-id="6f3e8-116">If you're using ASP.NET Core, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6f3e8-117">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="6f3e8-117">Prerequisites</span></span>

<span data-ttu-id="6f3e8-118">Zainstaluj następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-118">Install the following prerequisites:</span></span>

- <span data-ttu-id="6f3e8-119">[Zestaw SDK platformy .NET Core 3,1](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="6f3e8-119">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="6f3e8-120">Jeśli masz zainstalowany program .NET Core, użyj polecenia `dotnet --info` , aby określić, którego zestawu SDK używasz.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-120">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>
- [<span data-ttu-id="6f3e8-121">Platforma Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="6f3e8-121">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)
- <span data-ttu-id="6f3e8-122">Tymczasowy folder roboczy dla przykładowej aplikacji *pliku dockerfile* i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-122">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="6f3e8-123">W tym samouczku Nazwa programu *Docker Work* jest używana jako folder roboczy.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-123">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="6f3e8-124">Tworzenie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="6f3e8-124">Create .NET Core app</span></span>

<span data-ttu-id="6f3e8-125">Potrzebna jest aplikacja .NET Core, którą zostanie uruchomiony kontener platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-125">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="6f3e8-126">Otwórz Terminal, Utwórz folder roboczy, jeśli jeszcze tego nie zrobiono, a następnie wprowadź go.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-126">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="6f3e8-127">W folderze roboczym Uruchom następujące polecenie, aby utworzyć nowy projekt w podkatalogu o nazwie *App*:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-127">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

<span data-ttu-id="6f3e8-128">Drzewo folderów będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-128">Your folder tree will look like the following:</span></span>

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

<span data-ttu-id="6f3e8-129">`dotnet new` Polecenie tworzy nowy folder o nazwie *App* i generuje aplikację konsolową "Hello World".</span><span class="sxs-lookup"><span data-stu-id="6f3e8-129">The `dotnet new` command creates a new folder named *App* and generates a "Hello World" console application.</span></span> <span data-ttu-id="6f3e8-130">Zmień katalogi i przejdź do folderu *aplikacji* z sesji terminala.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-130">Change directories and navigate into the *App* folder, from your terminal session.</span></span> <span data-ttu-id="6f3e8-131">Użyj `dotnet run` polecenia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-131">Use the `dotnet run` command to start the app.</span></span> <span data-ttu-id="6f3e8-132">Aplikacja zostanie uruchomiona i wydrukowana `Hello World!` poniżej polecenia:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-132">The application will run, and print `Hello World!` below the command:</span></span>

```dotnetcli
dotnet run
Hello World!
```

<span data-ttu-id="6f3e8-133">Szablon domyślny tworzy aplikację, która drukuje do terminalu, a następnie natychmiast kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-133">The default template creates an app that prints to the terminal and then immediately terminates.</span></span> <span data-ttu-id="6f3e8-134">Na potrzeby tego samouczka będziesz używać aplikacji, która nieskończonie pętli.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-134">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="6f3e8-135">Otwórz plik *program.cs* w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-135">Open the *Program.cs* file in a text editor.</span></span>

> [!TIP]
> <span data-ttu-id="6f3e8-136">Jeśli używasz Visual Studio Code, w poprzedniej sesji terminala wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-136">If you're using Visual Studio Code, from the previous terminal session type the following command:</span></span>
>
> ```
> code .
> ```
>
> <span data-ttu-id="6f3e8-137">Spowoduje to otwarcie folderu *aplikacji* zawierającego projekt w Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-137">This will open the *App* folder that contains the project in Visual Studio Code.</span></span>

<span data-ttu-id="6f3e8-138">*Program.cs* powinien wyglądać podobnie do następującego kodu w języku C#:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-138">The *Program.cs* should look like the following C# code:</span></span>

```csharp
using System;

namespace NetCore.Docker
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="6f3e8-139">Zastąp plik następującym kodem, który zlicza liczby w każdej sekundzie:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-139">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

<span data-ttu-id="6f3e8-140">Zapisz plik i ponownie przetestuj program przy użyciu `dotnet run`programu.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-140">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="6f3e8-141">Należy pamiętać, że ta aplikacja jest uruchamiana w nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-141">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="6f3e8-142">Aby zatrzymać, użyj polecenia Cancel <kbd>Ctrl + C</kbd> .</span><span class="sxs-lookup"><span data-stu-id="6f3e8-142">Use the cancel command <kbd>Ctrl+C</kbd> to stop it.</span></span> <span data-ttu-id="6f3e8-143">Oto przykładowe dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-143">The following is an example output:</span></span>

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="6f3e8-144">Jeśli przekażesz liczbę w wierszu polecenia do aplikacji, będzie ona liczyć tylko do tej wartości, a następnie zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-144">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="6f3e8-145">Wypróbuj go, `dotnet run -- 5` aby liczyć do pięciu.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-145">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6f3e8-146">Wszystkie parametry po `--` nie są przenoszone do `dotnet run` polecenia i zamiast tego są przesyłane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-146">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="6f3e8-147">Publikowanie aplikacji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="6f3e8-147">Publish .NET Core app</span></span>

<span data-ttu-id="6f3e8-148">Przed dodaniem aplikacji .NET Core do obrazu platformy Docker należy najpierw ją opublikować.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-148">Before adding the .NET Core app to the Docker image, first it must be published.</span></span> <span data-ttu-id="6f3e8-149">Najlepszym rozwiązaniem jest uruchomienie przez kontener opublikowanej wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-149">It is best to have the container run the published version of the app.</span></span> <span data-ttu-id="6f3e8-150">Aby opublikować aplikację, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-150">To publish the app, run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="6f3e8-151">To polecenie kompiluje aplikację do folderu *Publikowanie* .</span><span class="sxs-lookup"><span data-stu-id="6f3e8-151">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="6f3e8-152">Ścieżka do folderu *publikowania* z folderu roboczego powinna być`.\App\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="6f3e8-152">The path to the *publish* folder from the working folder should be `.\App\bin\Release\netcoreapp3.1\publish\`</span></span>

#### <a name="windows"></a>[<span data-ttu-id="6f3e8-153">Windows</span><span class="sxs-lookup"><span data-stu-id="6f3e8-153">Windows</span></span>](#tab/windows)

<span data-ttu-id="6f3e8-154">W folderze *App (aplikacja* ) Pobierz listę katalogów folderu publikowania, aby sprawdzić, czy został utworzony plik z systemem. *Docker. dll* .</span><span class="sxs-lookup"><span data-stu-id="6f3e8-154">From the *App* folder, get a directory listing of the publish folder to verify that the *NetCore.Docker.dll* file was created.</span></span>

```powershell
dir .\bin\Release\netcoreapp3.1\publish\

    Directory: C:\Users\dapine\App\bin\Release\netcoreapp3.1\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[<span data-ttu-id="6f3e8-155">Linux</span><span class="sxs-lookup"><span data-stu-id="6f3e8-155">Linux</span></span>](#tab/linux)

<span data-ttu-id="6f3e8-156">Użyj `ls` polecenia, aby uzyskać listę katalogów i sprawdzić, czy plik. *Docker. dll* został utworzony.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-156">Use the `ls` command to get a directory listing and verify that the *NetCore.Docker.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a><span data-ttu-id="6f3e8-157">Tworzenie pliku dockerfile</span><span class="sxs-lookup"><span data-stu-id="6f3e8-157">Create the Dockerfile</span></span>

<span data-ttu-id="6f3e8-158">Plik *pliku dockerfile* jest używany przez `docker build` polecenie do tworzenia obrazu kontenera.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-158">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="6f3e8-159">Ten plik jest plikiem tekstowym o nazwie *pliku dockerfile* , który nie ma rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-159">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="6f3e8-160">Utwórz plik o nazwie *pliku dockerfile* w katalogu zawierającym element *. csproj* i otwórz go w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-160">Create a file named *Dockerfile* in directory containing the *.csproj* and open it in a text editor.</span></span> <span data-ttu-id="6f3e8-161">W tym samouczku zostanie użyty obraz środowiska uruchomieniowego ASP.NET Core (zawierający obraz środowiska uruchomieniowego programu .NET Core), który odpowiada aplikacji konsolowej programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-161">This tutorial will use the ASP.NET Core runtime image (which contains the .NET Core runtime image) and corresponds with the .NET Core console application.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
```

> [!NOTE]
> <span data-ttu-id="6f3e8-162">Obraz środowiska uruchomieniowego ASP.NET Core jest używany w sposób celowy, `mcr.microsoft.com/dotnet/core/runtime:3.1` chociaż można było użyć obrazu.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-162">The ASP.NET Core runtime image is used intentionally here, although the `mcr.microsoft.com/dotnet/core/runtime:3.1` image could have been used.</span></span>

<span data-ttu-id="6f3e8-163">`FROM` Słowo kluczowe wymaga w pełni kwalifikowanej nazwy obrazu kontenera Docker.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-163">The `FROM` keyword requires a fully qualified Docker container image name.</span></span> <span data-ttu-id="6f3e8-164">Microsoft Container Registry (MCR, mcr.microsoft.com) to zespolone centrum Docker, które hostuje dostępne publicznie kontenery.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-164">The Microsoft Container Registry (MCR, mcr.microsoft.com) is a syndicate of Docker Hub - which hosts publicly accessible containers.</span></span> <span data-ttu-id="6f3e8-165">`dotnet/core` Segment jest repozytorium kontenera, gdzie jako `aspnet` segment jest nazwą obrazu kontenera.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-165">The `dotnet/core` segment is the container repository, where as the `aspnet` segment is the container image name.</span></span> <span data-ttu-id="6f3e8-166">Obraz jest otagowany przy `3.1`użyciu, który jest używany do przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-166">The image is tagged with `3.1`, which is used for versioning.</span></span> <span data-ttu-id="6f3e8-167">`mcr.microsoft.com/dotnet/core/aspnet:3.1` W tym przypadku środowisko uruchomieniowe programu .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-167">Thus, `mcr.microsoft.com/dotnet/core/aspnet:3.1` is the .NET Core 3.1 runtime.</span></span> <span data-ttu-id="6f3e8-168">Upewnij się, że korzystasz z wersji środowiska uruchomieniowego, która pasuje do środowiska uruchomieniowego wskazywanego przez zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-168">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="6f3e8-169">Na przykład aplikacja utworzona w poprzedniej sekcji używa zestawu .NET Core 3,1 SDK i obrazu podstawowego, do którego odwołuje się w *pliku dockerfile* , jest oznaczona jako **3,1**.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-169">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="6f3e8-170">Zapisz plik *pliku dockerfile* .</span><span class="sxs-lookup"><span data-stu-id="6f3e8-170">Save the *Dockerfile* file.</span></span> <span data-ttu-id="6f3e8-171">Struktura katalogów folderu roboczego powinna wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-171">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="6f3e8-172">Niektóre pliki i foldery bardziej szczegółowe zostały pominięte w celu zaoszczędzenia miejsca w artykule:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-172">Some of the deeper-level files and folders have been omitted to save space in the article:</span></span>

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──netcoreapp3.1
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

<span data-ttu-id="6f3e8-173">W terminalu uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-173">From your terminal, run the following command:</span></span>

```Docker
docker build -t counter-image -f Dockerfile .
```

<span data-ttu-id="6f3e8-174">Platforma Docker będzie przetwarzać każdy wiersz w *pliku dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-174">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="6f3e8-175">W poleceniu polecenie instruuje platformę Docker, aby użyć bieżącego folderu do znalezienia *pliku dockerfile.* `.` `docker build`</span><span class="sxs-lookup"><span data-stu-id="6f3e8-175">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="6f3e8-176">To polecenie kompiluje obraz i tworzy lokalne repozytorium o nazwie **Counter-Image** , które wskazuje na ten obraz.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-176">This command builds the image and creates a local repository named **counter-image** that points to that image.</span></span> <span data-ttu-id="6f3e8-177">Po zakończeniu tego polecenia Uruchom `docker images` polecenie, aby wyświetlić listę zainstalowanych obrazów:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-177">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```Docker
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="6f3e8-178">Zwróć uwagę, że te dwa obrazy mają tę samą wartość **identyfikatora obrazu** .</span><span class="sxs-lookup"><span data-stu-id="6f3e8-178">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="6f3e8-179">Wartość jest taka sama między obu obrazów, ponieważ jedyne polecenie w *pliku dockerfile* było podstawą nowego obrazu na istniejącym obrazie.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-179">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="6f3e8-180">Dodajmy trzy polecenia do *pliku dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-180">Let's add three commands to the *Dockerfile*.</span></span> <span data-ttu-id="6f3e8-181">Każde polecenie tworzy nową warstwę obrazu z końcowym poleceniem reprezentującym punkty wejścia repozytorium **obrazu licznika** do.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-181">Each command creates a new image layer with the final command representing the **counter-image** repository entry points to.</span></span>

```dockerfile
COPY bin/Release/netcoreapp3.1/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

<span data-ttu-id="6f3e8-182">`COPY` Polecenie instruuje platformę Docker, aby skopiował określony folder na komputerze do folderu w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-182">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="6f3e8-183">W tym przykładzie folder *publikacji* jest kopiowany do folderu o nazwie *aplikacja* w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-183">In this example, the *publish* folder is copied to a folder named *App* in the container.</span></span>

<span data-ttu-id="6f3e8-184">`WORKDIR` Polecenie zmienia **bieżący katalog** wewnątrz kontenera na *aplikację*.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-184">The `WORKDIR` command changes the **current directory** inside of the container to *App*.</span></span>

<span data-ttu-id="6f3e8-185">Następne polecenie,, `ENTRYPOINT`instruuje platformę Docker, aby skonfigurować kontener do uruchamiania jako plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-185">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="6f3e8-186">Po uruchomieniu kontenera `ENTRYPOINT` polecenie zostanie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-186">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="6f3e8-187">Po zakończeniu tego polecenia kontener zostanie automatycznie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-187">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="6f3e8-188">W terminalu uruchom `docker build -t counter-image -f Dockerfile .` polecenie i po zakończeniu wykonywania `docker images`polecenia.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-188">From your terminal, run `docker build -t counter-image -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```Docker
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> e6780479db63
Step 2/4 : COPY bin/Release/netcoreapp3.1/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="6f3e8-189">Każde polecenie w *pliku dockerfile* wygenerowało warstwę i utworzyła **Identyfikator obrazu**.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-189">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="6f3e8-190">Końcowy **Identyfikator obrazu** (będzie inny) to **cd11c3df9b19** , a następnie utworzysz kontener oparty na tym obrazie.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-190">The final **IMAGE ID** (yours will be different) is **cd11c3df9b19** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="6f3e8-191">Tworzenie kontenera</span><span class="sxs-lookup"><span data-stu-id="6f3e8-191">Create a container</span></span>

<span data-ttu-id="6f3e8-192">Teraz, gdy masz obraz zawierający aplikację, możesz utworzyć kontener.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-192">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="6f3e8-193">Kontener można utworzyć na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-193">You can create a container in two ways.</span></span> <span data-ttu-id="6f3e8-194">Najpierw utwórz nowy kontener, który został zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-194">First, create a new container that is stopped.</span></span>

```Docker
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

<span data-ttu-id="6f3e8-195">Powyższe `docker create` polecenie spowoduje utworzenie kontenera na podstawie obrazu **licznika** .</span><span class="sxs-lookup"><span data-stu-id="6f3e8-195">The `docker create` command from above will create a container based on the **counter-image** image.</span></span> <span data-ttu-id="6f3e8-196">Dane wyjściowe tego polecenia pokazują, że **Identyfikator kontenera** (zostanie inaczej) utworzonego kontenera.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-196">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="6f3e8-197">Aby wyświetlić listę *wszystkich* kontenerów, użyj `docker ps -a` polecenia:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-197">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a><span data-ttu-id="6f3e8-198">Zarządzanie kontenerem</span><span class="sxs-lookup"><span data-stu-id="6f3e8-198">Manage the container</span></span>

<span data-ttu-id="6f3e8-199">Kontener został utworzony z określoną nazwą `core-counter`. Ta nazwa jest używana do zarządzania kontenerem.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-199">The container was created with a specific name `core-counter`, this name is used to manage the container.</span></span> <span data-ttu-id="6f3e8-200">Poniższy przykład używa `docker start` polecenia do uruchomienia kontenera, a następnie używa `docker ps` polecenia do wyświetlania tylko kontenerów, które są uruchomione:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-200">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```Docker
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

<span data-ttu-id="6f3e8-201">Podobnie `docker stop` polecenie spowoduje zatrzymanie kontenera.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-201">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="6f3e8-202">Poniższy przykład używa `docker stop` polecenia do zatrzymania kontenera, a następnie używa `docker ps` polecenia, aby pokazać, że żaden kontener nie jest uruchomiony:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-202">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```Docker
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="6f3e8-203">Nawiązywanie połączenia z kontenerem</span><span class="sxs-lookup"><span data-stu-id="6f3e8-203">Connect to a container</span></span>

<span data-ttu-id="6f3e8-204">Po uruchomieniu kontenera można nawiązać z nim połączenie, aby wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-204">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="6f3e8-205">Użyj poleceń `docker start` i `docker attach` , aby uruchomić kontener i wgląd do strumienia wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-205">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="6f3e8-206">W tym przykładzie naciśnięcie klawiszy <kbd>Ctrl + C</kbd> jest używane do odłączenia od uruchomionego kontenera.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-206">In this example, the <kbd>Ctrl+C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="6f3e8-207">Naciśnięcie klawisza spowoduje zakończenie procesu w kontenerze, o ile nie określono inaczej, co spowodowałoby zatrzymanie kontenera.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-207">This keystroke will end the process in the container unless otherwise specified, which would stop the container.</span></span> <span data-ttu-id="6f3e8-208">`--sig-proxy=false` Parametr zapewnia, że <kbd>naciśnięcie klawiszy CTRL + C</kbd> nie spowoduje zatrzymania procesu w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-208">The `--sig-proxy=false` parameter ensures that <kbd>Ctrl+C</kbd> will not stop the process in the container.</span></span>

<span data-ttu-id="6f3e8-209">Po odłączeniu od kontenera ponownie Dołącz, aby upewnić się, że nadal działa i zlicza.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-209">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```Docker
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="6f3e8-210">Usuwanie kontenera</span><span class="sxs-lookup"><span data-stu-id="6f3e8-210">Delete a container</span></span>

<span data-ttu-id="6f3e8-211">Na potrzeby tego artykułu nie ma potrzeby, aby kontenery zostały jedynie obsunięte.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-211">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="6f3e8-212">Usuń kontener, który został wcześniej utworzony.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-212">Delete the container you previously created.</span></span> <span data-ttu-id="6f3e8-213">Jeśli kontener jest uruchomiony, Zatrzymaj go.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-213">If the container is running, stop it.</span></span>

```Docker
docker stop core-counter
```

<span data-ttu-id="6f3e8-214">Poniższy przykład wyświetla listę wszystkich kontenerów.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-214">The following example lists all containers.</span></span> <span data-ttu-id="6f3e8-215">Następnie używa `docker rm` polecenia do usuwania kontenera, a następnie sprawdza drugi czas dla wszystkich uruchomionych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-215">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="6f3e8-216">Pojedynczy przebieg</span><span class="sxs-lookup"><span data-stu-id="6f3e8-216">Single run</span></span>

<span data-ttu-id="6f3e8-217">Docker udostępnia `docker run` polecenie do tworzenia i uruchamiania kontenera jako pojedyncze polecenie.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-217">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="6f3e8-218">To polecenie eliminuje konieczność uruchomienia `docker create` , a następnie `docker start`.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-218">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="6f3e8-219">Możesz również ustawić to polecenie, aby automatycznie usuwać kontener po zatrzymaniu kontenera.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-219">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="6f3e8-220">Na przykład użyj `docker run -it --rm` do dwóch rzeczy, najpierw automatycznie Użyj bieżącego terminalu do łączenia się z kontenerem, a następnie usuń go:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-220">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```Docker
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="6f3e8-221">Kontener przekazuje również parametry do wykonywania aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-221">The container also passes parameters into the execution of the .NET Core app.</span></span> <span data-ttu-id="6f3e8-222">Aby nakazać aplikacji .NET Core zliczanie tylko do 3 przebiegów 3.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-222">To instruct the .NET Core app to count only to 3 pass in 3.</span></span>

```Docker
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

<span data-ttu-id="6f3e8-223">W `docker run -it`programie <kbd>naciśnięcie polecenia CTRL + C</kbd> spowoduje zatrzymanie procesu, który jest uruchomiony w kontenerze, co z kolei powoduje zatrzymanie kontenera.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-223">With `docker run -it`, the <kbd>Ctrl+C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="6f3e8-224">Ponieważ `--rm` parametr został dostarczony, kontener jest automatycznie usuwany, gdy proces zostanie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-224">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="6f3e8-225">Sprawdź, czy nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-225">Verify that it doesn't exist:</span></span>

```Docker
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="6f3e8-226">Zmień punkt wejścia</span><span class="sxs-lookup"><span data-stu-id="6f3e8-226">Change the ENTRYPOINT</span></span>

<span data-ttu-id="6f3e8-227">`docker run` Polecenie umożliwia również modyfikowanie `ENTRYPOINT` polecenia z *pliku dockerfile* i uruchamianie czegoś innego, ale tylko dla tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-227">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="6f3e8-228">Na przykład użyj poniższego polecenia, aby uruchomić `bash` polecenie `cmd.exe`lub.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-228">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="6f3e8-229">W razie potrzeby zmodyfikuj polecenie.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-229">Edit the command as necessary.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="6f3e8-230">Windows</span><span class="sxs-lookup"><span data-stu-id="6f3e8-230">Windows</span></span>](#tab/windows)

<span data-ttu-id="6f3e8-231">W tym przykładzie `ENTRYPOINT` został zmieniony na `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-231">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="6f3e8-232"><kbd>Ctrl + C</kbd> jest wciśnięty, aby zakończyć proces i zatrzymać kontener.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-232"><kbd>Ctrl+C</kbd> is pressed to end the process and stop the container.</span></span>

```Docker
docker run -it --rm --entrypoint "cmd.exe" counter-image

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>[<span data-ttu-id="6f3e8-233">Linux</span><span class="sxs-lookup"><span data-stu-id="6f3e8-233">Linux</span></span>](#tab/linux)

<span data-ttu-id="6f3e8-234">W tym przykładzie `ENTRYPOINT` został zmieniony na `bash`.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-234">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="6f3e8-235">`exit` Polecenie jest uruchamiane, które zakończy proces i Zatrzymaj kontener.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-235">The `exit` command is run which ends the process and stop the container.</span></span>

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a><span data-ttu-id="6f3e8-236">Najważniejsze polecenia</span><span class="sxs-lookup"><span data-stu-id="6f3e8-236">Essential commands</span></span>

<span data-ttu-id="6f3e8-237">Platforma Docker ma wiele różnych poleceń, które tworzą i obsługują kontenery i obrazy oraz zarządzają nimi.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-237">Docker has many different commands that create, manage, and interact with containers and images.</span></span> <span data-ttu-id="6f3e8-238">Te polecenia platformy Docker mają kluczowe znaczenie dla zarządzania kontenerami:</span><span class="sxs-lookup"><span data-stu-id="6f3e8-238">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="6f3e8-239">docker build</span><span class="sxs-lookup"><span data-stu-id="6f3e8-239">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="6f3e8-240">uruchomienie platformy Docker</span><span class="sxs-lookup"><span data-stu-id="6f3e8-240">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="6f3e8-241">docker ps</span><span class="sxs-lookup"><span data-stu-id="6f3e8-241">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="6f3e8-242">zatrzymanie platformy Docker</span><span class="sxs-lookup"><span data-stu-id="6f3e8-242">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="6f3e8-243">Platforma Docker RM</span><span class="sxs-lookup"><span data-stu-id="6f3e8-243">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="6f3e8-244">Docker RMI</span><span class="sxs-lookup"><span data-stu-id="6f3e8-244">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="6f3e8-245">obraz platformy Docker</span><span class="sxs-lookup"><span data-stu-id="6f3e8-245">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="6f3e8-246">Oczyszczanie zasobów</span><span class="sxs-lookup"><span data-stu-id="6f3e8-246">Clean up resources</span></span>

<span data-ttu-id="6f3e8-247">W tym samouczku utworzono kontenery i obrazy.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-247">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="6f3e8-248">Jeśli chcesz, usuń te zasoby.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-248">If you want, delete these resources.</span></span> <span data-ttu-id="6f3e8-249">Użyj następujących poleceń, aby</span><span class="sxs-lookup"><span data-stu-id="6f3e8-249">Use the following commands to</span></span>

01. <span data-ttu-id="6f3e8-250">Wyświetl listę wszystkich kontenerów</span><span class="sxs-lookup"><span data-stu-id="6f3e8-250">List all containers</span></span>

    ```Docker
    docker ps -a
    ```

02. <span data-ttu-id="6f3e8-251">Zatrzymaj kontenery uruchomione przez ich nazwę.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-251">Stop containers that are running by their name.</span></span>

    ```Docker
    docker stop counter-image
    ```

03. <span data-ttu-id="6f3e8-252">Usuwanie kontenera</span><span class="sxs-lookup"><span data-stu-id="6f3e8-252">Delete the container</span></span>

    ```Docker
    docker rm counter-image
    ```

<span data-ttu-id="6f3e8-253">Następnie usuń wszystkie obrazy, które nie są już potrzebne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-253">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="6f3e8-254">Usuń obraz utworzony przez *pliku dockerfile* , a następnie Usuń obraz platformy .NET Core, na którym oparto *pliku dockerfile* .</span><span class="sxs-lookup"><span data-stu-id="6f3e8-254">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="6f3e8-255">Możesz użyć **identyfikatora obrazu** lub ciągu sformatowanego jako **tag** .</span><span class="sxs-lookup"><span data-stu-id="6f3e8-255">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```Docker
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="6f3e8-256">Użyj polecenia `docker images` , aby wyświetlić listę zainstalowanych obrazów.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-256">Use the `docker images` command to see a list of images installed.</span></span>

> [!TIP]
> <span data-ttu-id="6f3e8-257">Pliki obrazów mogą być duże.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-257">Image files can be large.</span></span> <span data-ttu-id="6f3e8-258">Zazwyczaj można usunąć kontenery tymczasowe, które zostały utworzone podczas testowania i opracowywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-258">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="6f3e8-259">Obrazy podstawowe z zainstalowanym środowiskiem uruchomieniowym zwykle są zachowywane, jeśli planujesz tworzenie innych obrazów na podstawie tego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-259">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6f3e8-260">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="6f3e8-260">Next steps</span></span>

- [<span data-ttu-id="6f3e8-261">Dowiedz się, jak konteneryzowanie aplikację ASP.NET Coreową.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-261">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="6f3e8-262">Wypróbuj ASP.NET Core samouczka mikrousług.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-262">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="6f3e8-263">Przejrzyj usługi platformy Azure, które obsługują kontenery.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-263">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="6f3e8-264">Przeczytaj o poleceniach pliku dockerfile.</span><span class="sxs-lookup"><span data-stu-id="6f3e8-264">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="6f3e8-265">Poznaj narzędzia kontenerów dla programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6f3e8-265">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
