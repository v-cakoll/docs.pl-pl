---
title: Konteneryzowanie aplikacji przy użyciu samouczka platformy Docker
description: W tym samouczku dowiesz się, jak konteneryzowanie aplikację .NET Core z platformą Docker.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 17d3dfbe58770b19a75be1dad3ae03406584992c
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900110"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="ad5b7-103">Samouczek: Konteneryzowanie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="ad5b7-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="ad5b7-104">W tym samouczku przedstawiono sposób tworzenia obrazu platformy Docker, który zawiera aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="ad5b7-105">Obraz może służyć do tworzenia kontenerów dla lokalnego środowiska projektowego, chmury prywatnej lub chmury publicznej.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="ad5b7-106">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-106">You'll learn to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="ad5b7-107">Tworzenie i publikowanie prostej aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="ad5b7-107">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="ad5b7-108">Tworzenie i konfigurowanie pliku dockerfile dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ad5b7-108">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="ad5b7-109">Tworzenie obrazu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="ad5b7-109">Build a Docker image</span></span>
> - <span data-ttu-id="ad5b7-110">Tworzenie i uruchamianie kontenera platformy Docker</span><span class="sxs-lookup"><span data-stu-id="ad5b7-110">Create and run a Docker container</span></span>

<span data-ttu-id="ad5b7-111">Zapoznaj się z tematem tworzenie i wdrażanie kontenerów platformy Docker dla aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="ad5b7-112">*Platforma Docker* korzysta z *aparatu platformy Docker* , aby szybko kompilować i spakować aplikacje jako *obrazy platformy Docker*.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="ad5b7-113">Te obrazy są zapisywane w formacie *pliku dockerfile* , który ma zostać wdrożony i uruchomiony w kontenerze warstwowym.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!TIP]
> <span data-ttu-id="ad5b7-114">Jeśli pracujesz z istniejącą aplikacją ASP.NET Core, zapoznaj się z samouczkiem [uczenie się, jak konteneryzowanie aplikacji ASP.NET Core](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .</span><span class="sxs-lookup"><span data-stu-id="ad5b7-114">If you're working with an existing ASP.NET Core application, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ad5b7-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ad5b7-115">Prerequisites</span></span>

<span data-ttu-id="ad5b7-116">Zainstaluj następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-116">Install the following prerequisites:</span></span>

- <span data-ttu-id="ad5b7-117">[Zestaw SDK platformy .NET Core 3,1](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="ad5b7-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="ad5b7-118">Jeśli masz zainstalowany program .NET Core, użyj polecenia `dotnet --info`, aby określić, którego zestawu SDK używasz.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-118">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

- [<span data-ttu-id="ad5b7-119">Platforma Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="ad5b7-119">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

- <span data-ttu-id="ad5b7-120">Tymczasowy folder roboczy dla przykładowej aplikacji *pliku dockerfile* i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-120">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="ad5b7-121">W tym samouczku Nazwa programu *Docker Work* jest używana jako folder roboczy.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-121">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="ad5b7-122">Tworzenie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="ad5b7-122">Create .NET Core app</span></span>

<span data-ttu-id="ad5b7-123">Potrzebna jest aplikacja .NET Core, którą zostanie uruchomiony kontener platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-123">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="ad5b7-124">Otwórz Terminal, Utwórz folder roboczy, jeśli jeszcze tego nie zrobiono, a następnie wprowadź go.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-124">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="ad5b7-125">W folderze roboczym Uruchom następujące polecenie, aby utworzyć nowy projekt w podkatalogu o nazwie *App*:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-125">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o app -n myapp
```

<span data-ttu-id="ad5b7-126">Drzewo folderów będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-126">Your folder tree will look like the following:</span></span>

```
docker-working
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.dgspec.json
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

<span data-ttu-id="ad5b7-127">`dotnet new` polecenie tworzy nowy folder o nazwie *App* i generuje aplikację "Hello World".</span><span class="sxs-lookup"><span data-stu-id="ad5b7-127">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="ad5b7-128">Wprowadź folder *App* i uruchom polecenie `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-128">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="ad5b7-129">Zobaczysz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-129">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="ad5b7-130">Szablon domyślny tworzy aplikację, która drukuje do terminalu, a następnie kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-130">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="ad5b7-131">Na potrzeby tego samouczka będziesz używać aplikacji, która nieskończonie pętli.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-131">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="ad5b7-132">Otwórz plik *program.cs* w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-132">Open the *Program.cs* file in a text editor.</span></span> <span data-ttu-id="ad5b7-133">Powinien wyglądać podobnie do następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-133">It should currently look like the following code:</span></span>

```csharp
using System;

namespace myapp
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

<span data-ttu-id="ad5b7-134">Zastąp plik następującym kodem, który zlicza liczby w każdej sekundzie:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-134">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

<span data-ttu-id="ad5b7-135">Zapisz plik i ponownie przetestuj program przy użyciu `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-135">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="ad5b7-136">Należy pamiętać, że ta aplikacja jest uruchamiana w nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-136">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="ad5b7-137">Użyj polecenia Cancel <kbd>CTRL</kbd>+<kbd>C</kbd> , aby go zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-137">Use the cancel command <kbd>CTRL</kbd>+<kbd>C</kbd> to stop it.</span></span> <span data-ttu-id="ad5b7-138">Zobaczysz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-138">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="ad5b7-139">Jeśli przekażesz liczbę w wierszu polecenia do aplikacji, będzie ona liczyć tylko do tej wartości, a następnie zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-139">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="ad5b7-140">Wypróbuj `dotnet run -- 5`, aby liczyć do pięciu.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-140">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="ad5b7-141">Wszelkie parametry po `--` nie są przenoszone do polecenia `dotnet run` i zamiast tego są przesyłane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-141">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="ad5b7-142">Publikowanie aplikacji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ad5b7-142">Publish .NET Core app</span></span>

<span data-ttu-id="ad5b7-143">Przed dodaniem aplikacji .NET Core do obrazu platformy Docker należy opublikować ją.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-143">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="ad5b7-144">Upewnij się, że kontener uruchamia opublikowaną wersję aplikacji po jej uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-144">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="ad5b7-145">W folderze roboczym wprowadź folder *App* z przykładowym kodem źródłowym i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-145">From the working folder, enter the *app* folder with the example source code and run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="ad5b7-146">To polecenie kompiluje aplikację do folderu *Publikowanie* .</span><span class="sxs-lookup"><span data-stu-id="ad5b7-146">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="ad5b7-147">Ścieżka do folderu *publikowania* z folderu roboczego powinna być `.\app\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="ad5b7-147">The path to the *publish* folder from the working folder should be `.\app\bin\Release\netcoreapp3.1\publish\`</span></span>

<span data-ttu-id="ad5b7-148">Aby sprawdzić, czy plik *MojaApl. dll* został utworzony, w folderze *App* należy uzyskać listę katalogów folderu publikacji.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-148">From the *app* folder, get a directory listing of the publish folder to verify that the *myapp.dll* file was created.</span></span> 

```console
> dir bin\Release\netcoreapp3.1\publish

    Directory:  C:\docker-working\app\bin\Release\netcoreapp3.1\publish

01/09/2020  11:41 AM    <DIR>          .
01/09/2020  11:41 AM    <DIR>          ..
01/09/2020  11:41 AM               407 myapp.deps.json
01/09/2020  12:15 PM             4,608 myapp.dll
01/09/2020  12:15 PM           169,984 myapp.exe
01/09/2020  12:15 PM               736 myapp.pdb
01/09/2020  11:41 AM               154 myapp.runtimeconfig.json
```

<span data-ttu-id="ad5b7-149">Jeśli używasz systemu Linux lub macOS, użyj polecenia `ls`, aby uzyskać listę katalogów i sprawdzić, czy plik *MojaApl. dll* został utworzony.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-149">If you're using Linux or macOS, use the `ls` command to get a directory listing and verify that the *myapp.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="ad5b7-150">Tworzenie pliku dockerfile</span><span class="sxs-lookup"><span data-stu-id="ad5b7-150">Create the Dockerfile</span></span>

<span data-ttu-id="ad5b7-151">Plik *pliku dockerfile* jest używany przez polecenie `docker build`, aby utworzyć obraz kontenera.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-151">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="ad5b7-152">Ten plik jest plikiem tekstowym o nazwie *pliku dockerfile* , który nie ma rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-152">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="ad5b7-153">W terminalu przejdź do katalogu roboczego, który został utworzony na początku.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-153">In your terminal, navigate up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="ad5b7-154">Utwórz plik o nazwie *pliku dockerfile* w folderze roboczym i otwórz go w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-154">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="ad5b7-155">W zależności od typu aplikacji, która ma zostać konteneryzowanie, należy wybrać środowisko uruchomieniowe ASP.NET Core lub środowisko uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-155">Depending on the type of application you're going to containerize, you'll choose either the ASP.NET Core runtime or the .NET Core runtime.</span></span> <span data-ttu-id="ad5b7-156">W razie wątpliwości Wybierz środowisko uruchomieniowe ASP.NET Core, które obejmuje środowisko uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-156">When in doubt, choose the ASP.NET Core runtime, which includes the .NET Core runtime.</span></span> <span data-ttu-id="ad5b7-157">W tym samouczku zostanie użyty obraz środowiska uruchomieniowego ASP.NET Core, ale aplikacja utworzona w poprzednich sekcjach jest aplikacją platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-157">This tutorial will use the ASP.NET Core runtime image, but the application created in the previous sections is an .NET Core application.</span></span>

- <span data-ttu-id="ad5b7-158">Środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ad5b7-158">ASP.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- <span data-ttu-id="ad5b7-159">Środowisko uruchomieniowe programu .NET core</span><span class="sxs-lookup"><span data-stu-id="ad5b7-159">.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

<span data-ttu-id="ad5b7-160">Polecenie `FROM` instruuje platformę Docker, aby ściągnąć obraz oznaczony **3,1** z określonego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-160">The `FROM` command tells Docker to pull down the image tagged **3.1** from the specified repository.</span></span> <span data-ttu-id="ad5b7-161">Upewnij się, że korzystasz z wersji środowiska uruchomieniowego, która pasuje do środowiska uruchomieniowego wskazywanego przez zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-161">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="ad5b7-162">Na przykład aplikacja utworzona w poprzedniej sekcji używa zestawu .NET Core 3,1 SDK i obrazu podstawowego, do którego odwołuje się w *pliku dockerfile* , jest oznaczona jako **3,1**.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-162">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="ad5b7-163">Zapisz plik *pliku dockerfile* .</span><span class="sxs-lookup"><span data-stu-id="ad5b7-163">Save the *Dockerfile* file.</span></span> <span data-ttu-id="ad5b7-164">Struktura katalogów folderu roboczego powinna wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-164">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="ad5b7-165">Niektóre pliki i foldery z bardziej szczegółowymi poziomami zostały wycięte w celu zaoszczędzenia miejsca w artykule:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-165">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

```
docker-working
│   Dockerfile
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp3.1
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.exe
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

<span data-ttu-id="ad5b7-166">W terminalu uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-166">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="ad5b7-167">Platforma Docker będzie przetwarzać każdy wiersz w *pliku dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-167">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="ad5b7-168">`.` w poleceniu `docker build` instruuje platformę Docker, aby użyć bieżącego folderu do znalezienia *pliku dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-168">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="ad5b7-169">To polecenie kompiluje obraz i tworzy lokalne repozytorium o nazwie **obraz** , który wskazuje na ten obraz.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-169">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="ad5b7-170">Po zakończeniu tego polecenia Uruchom `docker images`, aby wyświetlić listę zainstalowanych obrazów:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-170">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="ad5b7-171">Zwróć uwagę, że te dwa obrazy mają tę samą wartość **identyfikatora obrazu** .</span><span class="sxs-lookup"><span data-stu-id="ad5b7-171">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="ad5b7-172">Wartość jest taka sama między obu obrazów, ponieważ jedyne polecenie w *pliku dockerfile* było podstawą nowego obrazu na istniejącym obrazie.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-172">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="ad5b7-173">Dodajmy dwa polecenia do *pliku dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-173">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="ad5b7-174">Każde polecenie tworzy nową warstwę obrazu z końcowym poleceniem reprezentującym obraz wskazujący na wpis repozytorium **obrazu** .</span><span class="sxs-lookup"><span data-stu-id="ad5b7-174">Each command creates a new image layer with the final command representing the image the **myimage** repository entry points to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="ad5b7-175">Polecenie `COPY` instruuje platformę Docker o skopiowanie określonego folderu na komputerze do folderu w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-175">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="ad5b7-176">W tym przykładzie folder *publikacji* jest kopiowany do folderu o nazwie *aplikacja* w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-176">In this example, the *publish* folder is copied to a folder named *app* in the container.</span></span>

<span data-ttu-id="ad5b7-177">Następne polecenie `ENTRYPOINT`, instruuje platformę Docker, aby skonfigurować kontener do uruchamiania jako plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-177">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="ad5b7-178">Po rozpoczęciu kontenera zostanie uruchomione polecenie `ENTRYPOINT`.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-178">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="ad5b7-179">Po zakończeniu tego polecenia kontener zostanie automatycznie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-179">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="ad5b7-180">W terminalu uruchom `docker build -t myimage -f Dockerfile .` i po zakończeniu tego polecenia Uruchom polecenie `docker images`.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-180">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  1.624MB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> 38db0eb8f648
Step 2/3 : COPY app/bin/Release/netcoreapp3.1/publish/ app/
 ---> 37873673e468
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in d8deb7b3aa9e
Removing intermediate container d8deb7b3aa9e
 ---> 0d602ca35c1d
Successfully built 0d602ca35c1d
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              0d602ca35c1d        4 seconds ago       346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="ad5b7-181">Każde polecenie w *pliku dockerfile* wygenerowało warstwę i utworzyła **Identyfikator obrazu**.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-181">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="ad5b7-182">Końcowy **Identyfikator obrazu** (będzie inny) to **ddcc6646461b** , a następnie utworzysz kontener oparty na tym obrazie.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-182">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="ad5b7-183">Tworzenie kontenera</span><span class="sxs-lookup"><span data-stu-id="ad5b7-183">Create a container</span></span>

<span data-ttu-id="ad5b7-184">Teraz, gdy masz obraz zawierający aplikację, możesz utworzyć kontener.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-184">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="ad5b7-185">Kontener można utworzyć na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-185">You can create a container in two ways.</span></span> <span data-ttu-id="ad5b7-186">Najpierw utwórz nowy kontener, który został zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-186">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

<span data-ttu-id="ad5b7-187">Polecenie `docker create` from powyżej utworzy kontener oparty na obrazie **obrazu** .</span><span class="sxs-lookup"><span data-stu-id="ad5b7-187">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="ad5b7-188">Dane wyjściowe tego polecenia pokazują, że **Identyfikator kontenera** (zostanie inaczej) utworzonego kontenera.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-188">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="ad5b7-189">Aby wyświetlić listę *wszystkich* kontenerów, użyj `docker ps -a` polecenia:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-189">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a><span data-ttu-id="ad5b7-190">Zarządzanie kontenerem</span><span class="sxs-lookup"><span data-stu-id="ad5b7-190">Manage the container</span></span>

<span data-ttu-id="ad5b7-191">Do każdego kontenera jest przypisywana nazwa Losowa, której można użyć do odwoływania się do tego wystąpienia kontenera.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-191">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="ad5b7-192">Na przykład kontener, który został utworzony automatycznie wybiera nazwę **gallant_lehmann** (będzie się różnić), a ta nazwa może być używana do uruchamiania kontenera.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-192">For example, the container that was created automatically chose the name **gallant_lehmann** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="ad5b7-193">Automatyczna nazwa zostanie zastąpiona określonym przez użycie parametru `docker create --name`.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-193">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="ad5b7-194">Poniższy przykład używa polecenia `docker start`, aby uruchomić kontener, a następnie używa polecenia `docker ps` do wyświetlania tylko kontenerów z systemem:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-194">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

<span data-ttu-id="ad5b7-195">Analogicznie, polecenie `docker stop` spowoduje zatrzymanie kontenera.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-195">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="ad5b7-196">Poniższy przykład używa polecenia `docker stop`, aby zatrzymać kontener, a następnie używa polecenia `docker ps`, aby pokazać, że żaden kontener nie jest uruchomiony:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-196">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="ad5b7-197">Nawiązywanie połączenia z kontenerem</span><span class="sxs-lookup"><span data-stu-id="ad5b7-197">Connect to a container</span></span>

<span data-ttu-id="ad5b7-198">Po uruchomieniu kontenera można nawiązać z nim połączenie, aby wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-198">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="ad5b7-199">Użyj poleceń `docker start` i `docker attach`, aby uruchomić kontener i uzyskać wgląd w strumieniu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-199">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="ad5b7-200">W tym przykładzie naciśnięcie klawiszy <kbd>Ctrl + C</kbd> jest używane do odłączenia od uruchomionego kontenera.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-200">In this example, the <kbd>CTRL + C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="ad5b7-201">To naciśnięcie klawisza może ostatecznie zakończyć proces w kontenerze, co spowoduje zatrzymanie kontenera.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-201">This keystroke may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="ad5b7-202">`--sig-proxy=false` parametr gwarantuje, że <kbd>naciśnięcie klawiszy CTRL + C</kbd> nie zatrzyma procesu w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-202">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="ad5b7-203">Po odłączeniu od kontenera ponownie Dołącz, aby upewnić się, że nadal działa i zlicza.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-203">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker attach --sig-proxy=false gallant_lehmann
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false gallant_lehmann
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="ad5b7-204">Usuwanie kontenera</span><span class="sxs-lookup"><span data-stu-id="ad5b7-204">Delete a container</span></span>

<span data-ttu-id="ad5b7-205">Na potrzeby tego artykułu nie ma potrzeby, aby kontenery zostały jedynie obsunięte.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-205">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="ad5b7-206">Usuń kontener, który został wcześniej utworzony.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-206">Delete the container you previously created.</span></span> <span data-ttu-id="ad5b7-207">Jeśli kontener jest uruchomiony, Zatrzymaj go.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-207">If the container is running, stop it.</span></span>

```console
> docker stop gallant_lehmann
```

<span data-ttu-id="ad5b7-208">Poniższy przykład wyświetla listę wszystkich kontenerów.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-208">The following example lists all containers.</span></span> <span data-ttu-id="ad5b7-209">Następnie używa polecenia `docker rm`, aby usunąć kontener, a następnie sprawdza drugi czas dla wszystkich uruchomionych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-209">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="ad5b7-210">Pojedynczy przebieg</span><span class="sxs-lookup"><span data-stu-id="ad5b7-210">Single run</span></span>

<span data-ttu-id="ad5b7-211">Platforma Docker udostępnia polecenie `docker run`, aby utworzyć i uruchomić kontener jako pojedyncze polecenie.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-211">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="ad5b7-212">To polecenie eliminuje konieczność uruchamiania `docker create` a następnie `docker start`.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-212">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="ad5b7-213">Możesz również ustawić to polecenie, aby automatycznie usuwać kontener po zatrzymaniu kontenera.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-213">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="ad5b7-214">Na przykład użyj `docker run -it --rm`, aby wykonać dwa czynności, w pierwszej kolejności automatycznie Użyj bieżącego terminalu do nawiązania połączenia z kontenerem, a następnie usuń go:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-214">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="ad5b7-215">Za pomocą `docker run -it`polecenie <kbd>Ctrl + C</kbd> przestanie działać w kontenerze, który z kolei zatrzymuje kontener.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-215">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="ad5b7-216">Ponieważ podano parametr `--rm`, kontener jest automatycznie usuwany, gdy proces zostanie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-216">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="ad5b7-217">Sprawdź, czy nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-217">Verify that it doesn't exist:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="ad5b7-218">Zmień punkt wejścia</span><span class="sxs-lookup"><span data-stu-id="ad5b7-218">Change the ENTRYPOINT</span></span>

<span data-ttu-id="ad5b7-219">`docker run` polecenie umożliwia również modyfikowanie polecenia `ENTRYPOINT` z *pliku dockerfile* i uruchamianie czegoś innego, ale tylko dla tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-219">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="ad5b7-220">Na przykład użyj następującego polecenia, aby uruchomić `bash` lub `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-220">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="ad5b7-221">W razie potrzeby zmodyfikuj polecenie.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-221">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="ad5b7-222">Windows</span><span class="sxs-lookup"><span data-stu-id="ad5b7-222">Windows</span></span>

<span data-ttu-id="ad5b7-223">W tym przykładzie `ENTRYPOINT` został zmieniony na `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-223">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="ad5b7-224"><kbd>Naciśnij klawisz CTRL</kbd>+<kbd>C</kbd> , aby zakończyć proces i zatrzymać kontener.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-224"><kbd>CTRL</kbd>+<kbd>C</kbd> is pressed to end the process and stop the container.</span></span>

```console
> docker run -it --rm --entrypoint "cmd.exe" myimage

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

#### <a name="linux"></a><span data-ttu-id="ad5b7-225">Linux</span><span class="sxs-lookup"><span data-stu-id="ad5b7-225">Linux</span></span>

<span data-ttu-id="ad5b7-226">W tym przykładzie `ENTRYPOINT` został zmieniony na `bash`.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-226">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="ad5b7-227">`quit` polecenie jest uruchamiane, które zakończy proces i Zatrzymaj kontener.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-227">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="ad5b7-228">Najważniejsze polecenia</span><span class="sxs-lookup"><span data-stu-id="ad5b7-228">Essential commands</span></span>

<span data-ttu-id="ad5b7-229">Platforma Docker ma wiele różnych poleceń, które obejmują, co chcesz zrobić z kontenerem i obrazami.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-229">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="ad5b7-230">Te polecenia platformy Docker mają kluczowe znaczenie dla zarządzania kontenerami:</span><span class="sxs-lookup"><span data-stu-id="ad5b7-230">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="ad5b7-231">Kompilacja platformy Docker</span><span class="sxs-lookup"><span data-stu-id="ad5b7-231">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="ad5b7-232">uruchomienie platformy Docker</span><span class="sxs-lookup"><span data-stu-id="ad5b7-232">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="ad5b7-233">Docker PS</span><span class="sxs-lookup"><span data-stu-id="ad5b7-233">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="ad5b7-234">zatrzymanie platformy Docker</span><span class="sxs-lookup"><span data-stu-id="ad5b7-234">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="ad5b7-235">Platforma Docker RM</span><span class="sxs-lookup"><span data-stu-id="ad5b7-235">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="ad5b7-236">Docker RMI</span><span class="sxs-lookup"><span data-stu-id="ad5b7-236">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="ad5b7-237">obraz platformy Docker</span><span class="sxs-lookup"><span data-stu-id="ad5b7-237">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="ad5b7-238">Oczyszczanie zasobów</span><span class="sxs-lookup"><span data-stu-id="ad5b7-238">Clean up resources</span></span>

<span data-ttu-id="ad5b7-239">W tym samouczku utworzono kontenery i obrazy.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-239">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="ad5b7-240">Jeśli chcesz, usuń te zasoby.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-240">If you want, delete these resources.</span></span> <span data-ttu-id="ad5b7-241">Użyj następujących poleceń, aby</span><span class="sxs-lookup"><span data-stu-id="ad5b7-241">Use the following commands to</span></span>

01. <span data-ttu-id="ad5b7-242">Wyświetl listę wszystkich kontenerów</span><span class="sxs-lookup"><span data-stu-id="ad5b7-242">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="ad5b7-243">Zatrzymaj uruchomione kontenery.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-243">Stop containers that are running.</span></span> <span data-ttu-id="ad5b7-244">`CONTAINER_NAME` reprezentuje nazwę, która jest automatycznie przypisywana do kontenera.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-244">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="ad5b7-245">Usuwanie kontenera</span><span class="sxs-lookup"><span data-stu-id="ad5b7-245">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="ad5b7-246">Następnie usuń wszystkie obrazy, które nie są już potrzebne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-246">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="ad5b7-247">Usuń obraz utworzony przez *pliku dockerfile* , a następnie Usuń obraz platformy .NET Core, na którym oparto *pliku dockerfile* .</span><span class="sxs-lookup"><span data-stu-id="ad5b7-247">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="ad5b7-248">Możesz użyć **identyfikatora obrazu** lub ciągu sformatowanego jako **tag** .</span><span class="sxs-lookup"><span data-stu-id="ad5b7-248">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="ad5b7-249">Użyj `docker images` polecenia, aby wyświetlić listę zainstalowanych obrazów.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-249">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="ad5b7-250">Pliki obrazów mogą być duże.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-250">Image files can be large.</span></span> <span data-ttu-id="ad5b7-251">Zazwyczaj można usunąć kontenery tymczasowe, które zostały utworzone podczas testowania i opracowywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-251">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="ad5b7-252">Obrazy podstawowe z zainstalowanym środowiskiem uruchomieniowym zwykle są zachowywane, jeśli planujesz tworzenie innych obrazów na podstawie tego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-252">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ad5b7-253">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ad5b7-253">Next steps</span></span>

- [<span data-ttu-id="ad5b7-254">Dowiedz się, jak konteneryzowanie aplikację ASP.NET Coreową.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-254">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="ad5b7-255">Wypróbuj ASP.NET Core samouczka mikrousług.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-255">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="ad5b7-256">Przejrzyj usługi platformy Azure, które obsługują kontenery.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-256">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="ad5b7-257">Przeczytaj o poleceniach pliku dockerfile.</span><span class="sxs-lookup"><span data-stu-id="ad5b7-257">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="ad5b7-258">Poznaj narzędzia kontenerów dla programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ad5b7-258">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
