---
title: Konteneryzowanie aplikacji za pomocą samouczka platformy Docker
description: W tym samouczku dowiesz się, jak konteneryzować aplikację .NET Core za pomocą platformy Docker.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 8be12792e4a9e8511dba87e657f700cc4ec97a16
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546578"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="d328b-103">Samouczek: Konteneryzuj aplikację .NET Core</span><span class="sxs-lookup"><span data-stu-id="d328b-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="d328b-104">W tym samouczku dowiesz się, jak utworzyć obraz platformy Docker zawierający aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d328b-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="d328b-105">Obraz może służyć do tworzenia kontenerów dla lokalnego środowiska programistycznego, chmury prywatnej lub chmury publicznej.</span><span class="sxs-lookup"><span data-stu-id="d328b-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="d328b-106">Nauczysz się:</span><span class="sxs-lookup"><span data-stu-id="d328b-106">You'll learn to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="d328b-107">Tworzenie i publikowanie prostej aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="d328b-107">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="d328b-108">Tworzenie i konfigurowanie pliku dockerfile dla programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="d328b-108">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="d328b-109">Kompilowanie obrazu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="d328b-109">Build a Docker image</span></span>
> - <span data-ttu-id="d328b-110">Tworzenie i uruchamianie kontenera platformy Docker</span><span class="sxs-lookup"><span data-stu-id="d328b-110">Create and run a Docker container</span></span>

<span data-ttu-id="d328b-111">Zrozumiesz kompilację kontenera platformy Docker i wdrożyć zadania dla aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d328b-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="d328b-112">*Platforma Docker* używa *aparatu platformy Docker* do szybkiego tworzenia i pakowania aplikacji w *obrazach platformy Docker.*</span><span class="sxs-lookup"><span data-stu-id="d328b-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="d328b-113">Te obrazy są zapisywane w formacie *Dockerfile* do wdrożenia i uruchomienia w kontenerze warstwowym.</span><span class="sxs-lookup"><span data-stu-id="d328b-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!WARNING]
> <span data-ttu-id="d328b-114">**Ten samouczek nie jest przeznaczony dla aplikacji ASP.NET Core.**</span><span class="sxs-lookup"><span data-stu-id="d328b-114">**This tutorial isn't for ASP.NET Core apps.**</span></span> <span data-ttu-id="d328b-115">Jeśli używasz ASP.NET Core, przeczytaj [dowiedz się, jak konteneryzować samouczek aplikacji ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)</span><span class="sxs-lookup"><span data-stu-id="d328b-115">If you're using ASP.NET Core, read the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d328b-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d328b-116">Prerequisites</span></span>

<span data-ttu-id="d328b-117">Zainstaluj następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="d328b-117">Install the following prerequisites:</span></span>

- <span data-ttu-id="d328b-118">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="d328b-118">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="d328b-119">Jeśli masz zainstalowany program .NET `dotnet --info` Core, użyj polecenia, aby określić, którego sdk używasz.</span><span class="sxs-lookup"><span data-stu-id="d328b-119">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

- [<span data-ttu-id="d328b-120">Wersja społeczności platformy Docker</span><span class="sxs-lookup"><span data-stu-id="d328b-120">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

- <span data-ttu-id="d328b-121">Tymczasowy folder roboczy dla przykładowej aplikacji *Dockerfile* i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d328b-121">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="d328b-122">W tym samouczku nazwa *docker-working* jest używana jako folder roboczy.</span><span class="sxs-lookup"><span data-stu-id="d328b-122">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="d328b-123">Tworzenie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="d328b-123">Create .NET Core app</span></span>

<span data-ttu-id="d328b-124">Potrzebujesz aplikacji .NET Core, która będzie uruchamiana przez kontener platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="d328b-124">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="d328b-125">Otwórz terminal, utwórz folder roboczy, jeśli jeszcze tego nie zrobiłeś, i wprowadź go.</span><span class="sxs-lookup"><span data-stu-id="d328b-125">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="d328b-126">W folderze roboczym uruchom następujące polecenie, aby utworzyć nowy projekt w podkatalogu o nazwie *aplikacji:*</span><span class="sxs-lookup"><span data-stu-id="d328b-126">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o app -n myapp
```

<span data-ttu-id="d328b-127">Drzewo folderów będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="d328b-127">Your folder tree will look like the following:</span></span>

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

<span data-ttu-id="d328b-128">Polecenie `dotnet new` tworzy nowy folder o nazwie *aplikacji* i generuje "Hello World" aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d328b-128">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="d328b-129">Wprowadź folder *aplikacji* i `dotnet run`uruchom polecenie .</span><span class="sxs-lookup"><span data-stu-id="d328b-129">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="d328b-130">Zobaczysz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d328b-130">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="d328b-131">Szablon domyślny tworzy aplikację, która drukuje do terminala, a następnie kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="d328b-131">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="d328b-132">W tym samouczku użyjesz aplikacji, która zapętla się przez czas nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="d328b-132">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="d328b-133">Otwórz plik *Program.cs* w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="d328b-133">Open the *Program.cs* file in a text editor.</span></span> <span data-ttu-id="d328b-134">Obecnie powinien wyglądać jak następujący kod:</span><span class="sxs-lookup"><span data-stu-id="d328b-134">It should currently look like the following code:</span></span>

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

<span data-ttu-id="d328b-135">Zastąp plik następującym kodem, który zlicza liczby co sekundę:</span><span class="sxs-lookup"><span data-stu-id="d328b-135">Replace the file with the following code that counts numbers every second:</span></span>

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

<span data-ttu-id="d328b-136">Zapisz plik i ponownie przetestuj program za pomocą pliku `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="d328b-136">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="d328b-137">Pamiętaj, że ta aplikacja działa przez czas nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="d328b-137">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="d328b-138">Użyj polecenia anuluj <kbd>CTRL</kbd>+<kbd>C,</kbd> aby go zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="d328b-138">Use the cancel command <kbd>CTRL</kbd>+<kbd>C</kbd> to stop it.</span></span> <span data-ttu-id="d328b-139">Zobaczysz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d328b-139">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="d328b-140">Jeśli przekażesz numer w wierszu polecenia do aplikacji, będzie on liczony tylko do tej kwoty, a następnie zakończyć.</span><span class="sxs-lookup"><span data-stu-id="d328b-140">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="d328b-141">Spróbuj z `dotnet run -- 5` liczyć do pięciu.</span><span class="sxs-lookup"><span data-stu-id="d328b-141">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="d328b-142">Wszelkie parametry `--` po nie `dotnet run` są przekazywane do polecenia i zamiast tego są przekazywane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d328b-142">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="d328b-143">Publikowanie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="d328b-143">Publish .NET Core app</span></span>

<span data-ttu-id="d328b-144">Przed dodaniem aplikacji .NET Core do obrazu platformy Docker należy ją opublikować.</span><span class="sxs-lookup"><span data-stu-id="d328b-144">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="d328b-145">Chcesz upewnić się, że kontener uruchamia opublikowaną wersję aplikacji po jej uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="d328b-145">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="d328b-146">W folderze roboczym wprowadź folder *aplikacji* z przykładowym kodem źródłowym i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d328b-146">From the working folder, enter the *app* folder with the example source code and run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="d328b-147">To polecenie kompiluje aplikację do folderu *publikowania.*</span><span class="sxs-lookup"><span data-stu-id="d328b-147">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="d328b-148">Ścieżka do folderu *publikowania* z folderu roboczego powinna być`.\app\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="d328b-148">The path to the *publish* folder from the working folder should be `.\app\bin\Release\netcoreapp3.1\publish\`</span></span>

<span data-ttu-id="d328b-149">Z folderu *aplikacji* pobierz listę katalogów folderu publikowania, aby sprawdzić, czy plik *myapp.dll* został utworzony.</span><span class="sxs-lookup"><span data-stu-id="d328b-149">From the *app* folder, get a directory listing of the publish folder to verify that the *myapp.dll* file was created.</span></span>

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

<span data-ttu-id="d328b-150">Jeśli używasz systemu Linux lub macOS, użyj `ls` tego polecenia, aby uzyskać listę katalogów i sprawdzić, czy plik *myapp.dll* został utworzony.</span><span class="sxs-lookup"><span data-stu-id="d328b-150">If you're using Linux or macOS, use the `ls` command to get a directory listing and verify that the *myapp.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="d328b-151">Tworzenie pliku dockerfile</span><span class="sxs-lookup"><span data-stu-id="d328b-151">Create the Dockerfile</span></span>

<span data-ttu-id="d328b-152">Plik *Dockerfile* jest używany `docker build` przez polecenie do tworzenia obrazu kontenera.</span><span class="sxs-lookup"><span data-stu-id="d328b-152">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="d328b-153">Ten plik jest plikiem tekstowym o nazwie *Dockerfile,* który nie ma rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d328b-153">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="d328b-154">W terminalu przejdź w górę katalogu do folderu roboczego utworzonego na początku.</span><span class="sxs-lookup"><span data-stu-id="d328b-154">In your terminal, navigate up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="d328b-155">Utwórz plik o nazwie *Dockerfile* w folderze roboczym i otwórz go w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="d328b-155">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="d328b-156">W zależności od typu aplikacji, który zamierzasz konteneryzować, wybierzesz ASP.NET core runtime lub .NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="d328b-156">Depending on the type of application you're going to containerize, you'll choose either the ASP.NET Core runtime or the .NET Core runtime.</span></span> <span data-ttu-id="d328b-157">W razie wątpliwości wybierz ASP.NET core runtime, który obejmuje środowisko uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d328b-157">When in doubt, choose the ASP.NET Core runtime, which includes the .NET Core runtime.</span></span> <span data-ttu-id="d328b-158">W tym samouczku użyje się ASP.NET core obrazu środowiska uruchomieniowego, ale aplikacja utworzona w poprzednich sekcjach jest aplikacją .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d328b-158">This tutorial will use the ASP.NET Core runtime image, but the application created in the previous sections is an .NET Core application.</span></span>

- <span data-ttu-id="d328b-159">ASP.NET Podstawowy czas pracy</span><span class="sxs-lookup"><span data-stu-id="d328b-159">ASP.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- <span data-ttu-id="d328b-160">Core .NET środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d328b-160">.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

<span data-ttu-id="d328b-161">Polecenie `FROM` nakazuje docker, aby ściągnąć w dół obraz oznaczony **3.1** z określonego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="d328b-161">The `FROM` command tells Docker to pull down the image tagged **3.1** from the specified repository.</span></span> <span data-ttu-id="d328b-162">Upewnij się, że ściągasz wersję środowiska wykonawczego, która odpowiada środowiska uruchomieniowego docelowego przez sdk.</span><span class="sxs-lookup"><span data-stu-id="d328b-162">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="d328b-163">Na przykład aplikacja utworzona w poprzedniej sekcji używała SDK .NET Core 3.1, a obraz podstawowy, o którym mowa w *pliku Dockerfile,* jest oznaczony tagiem **3.1**.</span><span class="sxs-lookup"><span data-stu-id="d328b-163">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="d328b-164">Zapisz plik *Dockerfile.*</span><span class="sxs-lookup"><span data-stu-id="d328b-164">Save the *Dockerfile* file.</span></span> <span data-ttu-id="d328b-165">Struktura katalogów folderu roboczego powinna wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="d328b-165">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="d328b-166">Niektóre pliki i foldery na głębszym poziomie zostały wycięte, aby zaoszczędzić miejsce w artykule:</span><span class="sxs-lookup"><span data-stu-id="d328b-166">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

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

<span data-ttu-id="d328b-167">Z terminala uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d328b-167">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="d328b-168">Docker będzie przetwarzać każdy wiersz w *pliku Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="d328b-168">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="d328b-169">W `.` poleceniu nakazuje programowi `docker build` Docker użycie bieżącego folderu w celu znalezienia pliku *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="d328b-169">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="d328b-170">To polecenie tworzy obraz i tworzy lokalne repozytorium o nazwie **myimage,** który wskazuje na ten obraz.</span><span class="sxs-lookup"><span data-stu-id="d328b-170">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="d328b-171">Po zakończeniu tego polecenia `docker images` uruchom, aby wyświetlić listę zainstalowanych obrazów:</span><span class="sxs-lookup"><span data-stu-id="d328b-171">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="d328b-172">Należy zauważyć, że dwa obrazy mają tę samą wartość **identyfikatora OBRAZU.**</span><span class="sxs-lookup"><span data-stu-id="d328b-172">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="d328b-173">Wartość jest taka sama między obu obrazów, ponieważ jedynym poleceniem w *Dockerfile* było oprzeć nowy obraz na istniejącym obrazie.</span><span class="sxs-lookup"><span data-stu-id="d328b-173">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="d328b-174">Dodajmy dwa polecenia do pliku *dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="d328b-174">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="d328b-175">Każde polecenie tworzy nową warstwę obrazu z poleceniem końcowym reprezentującym obraz, do których wskazuje wejście repozytorium **myimage.**</span><span class="sxs-lookup"><span data-stu-id="d328b-175">Each command creates a new image layer with the final command representing the image the **myimage** repository entry points to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="d328b-176">Polecenie `COPY` nakazuje programowi Docker skopiowanie określonego folderu na komputerze do folderu w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="d328b-176">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="d328b-177">W tym przykładzie folder *publikowania* jest kopiowany do folderu o nazwie *aplikacji* w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="d328b-177">In this example, the *publish* folder is copied to a folder named *app* in the container.</span></span>

<span data-ttu-id="d328b-178">Następne polecenie `ENTRYPOINT`, mówi docker skonfigurować kontener do uruchomienia jako plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="d328b-178">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="d328b-179">Po uruchomieniu kontenera `ENTRYPOINT` jest uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="d328b-179">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="d328b-180">Po zakończeniu tego polecenia kontener zostanie automatycznie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="d328b-180">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="d328b-181">Z terminala `docker build -t myimage -f Dockerfile .` uruchom i po zakończeniu `docker images`tego polecenia uruchom polecenie .</span><span class="sxs-lookup"><span data-stu-id="d328b-181">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

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

<span data-ttu-id="d328b-182">Każde polecenie w pliku *Dockerfile wygenerowało* warstwę i utworzyło **identyfikator OBRAZU**.</span><span class="sxs-lookup"><span data-stu-id="d328b-182">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="d328b-183">Ostateczny **identyfikator OBRAZU** (twój będzie inny) to **ddcc6646461b,** a następnie utworzysz kontener na podstawie tego obrazu.</span><span class="sxs-lookup"><span data-stu-id="d328b-183">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="d328b-184">Tworzenie kontenera</span><span class="sxs-lookup"><span data-stu-id="d328b-184">Create a container</span></span>

<span data-ttu-id="d328b-185">Teraz, gdy masz obraz, który zawiera aplikację, można utworzyć kontener.</span><span class="sxs-lookup"><span data-stu-id="d328b-185">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="d328b-186">Kontener można utworzyć na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="d328b-186">You can create a container in two ways.</span></span> <span data-ttu-id="d328b-187">Najpierw utwórz nowy kontener, który jest zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="d328b-187">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

<span data-ttu-id="d328b-188">Polecenie `docker create` z góry utworzy kontener na podstawie obrazu **myimage.**</span><span class="sxs-lookup"><span data-stu-id="d328b-188">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="d328b-189">Dane wyjściowe tego polecenia pokazuje **identyfikator kontenera** (twój będzie inny) utworzonego kontenera.</span><span class="sxs-lookup"><span data-stu-id="d328b-189">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="d328b-190">Aby wyświetlić listę *wszystkich* kontenerów, użyj `docker ps -a` polecenia:</span><span class="sxs-lookup"><span data-stu-id="d328b-190">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a><span data-ttu-id="d328b-191">Zarządzanie kontenerem</span><span class="sxs-lookup"><span data-stu-id="d328b-191">Manage the container</span></span>

<span data-ttu-id="d328b-192">Każdemu kontenerowi jest przypisywana losowa nazwa, której można użyć do odwoływania się do tego wystąpienia kontenera.</span><span class="sxs-lookup"><span data-stu-id="d328b-192">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="d328b-193">Na przykład kontener, który został utworzony automatycznie wybrał nazwę **gallant_lehmann** (twoja będzie inna) i tej nazwy może służyć do uruchamiania kontenera.</span><span class="sxs-lookup"><span data-stu-id="d328b-193">For example, the container that was created automatically chose the name **gallant_lehmann** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="d328b-194">Zastąpisz nazwę automatyczną określoną przy użyciu `docker create --name` parametru.</span><span class="sxs-lookup"><span data-stu-id="d328b-194">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="d328b-195">Poniższy przykład używa `docker start` polecenia do uruchomienia kontenera, `docker ps` a następnie używa polecenia, aby wyświetlić tylko kontenery, które są uruchomione:</span><span class="sxs-lookup"><span data-stu-id="d328b-195">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

<span data-ttu-id="d328b-196">Podobnie `docker stop` polecenie zatrzyma kontener.</span><span class="sxs-lookup"><span data-stu-id="d328b-196">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="d328b-197">Poniższy przykład używa `docker stop` polecenia, aby zatrzymać kontener, `docker ps` a następnie używa polecenia, aby pokazać, że żadne kontenery nie są uruchomione:</span><span class="sxs-lookup"><span data-stu-id="d328b-197">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="d328b-198">Łączenie się z kontenerem</span><span class="sxs-lookup"><span data-stu-id="d328b-198">Connect to a container</span></span>

<span data-ttu-id="d328b-199">Po uruchomieniu kontenera można połączyć się z nim, aby wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="d328b-199">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="d328b-200">Użyj `docker start` i `docker attach` polecenia, aby uruchomić kontener i zajrzeć do strumienia wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d328b-200">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="d328b-201">W tym przykładzie naciśnięcie klawisza <kbd>CTRL + C</kbd> jest używane do odłączyć od uruchomionego kontenera.</span><span class="sxs-lookup"><span data-stu-id="d328b-201">In this example, the <kbd>CTRL + C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="d328b-202">To naciśnięcie klawisza może faktycznie zakończyć proces w kontenerze, który zatrzyma kontenera.</span><span class="sxs-lookup"><span data-stu-id="d328b-202">This keystroke may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="d328b-203">Parametr `--sig-proxy=false` zapewnia, że <kbd>CTRL + C</kbd> nie zatrzyma proces w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="d328b-203">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="d328b-204">Po odłączeniu od kontenera, ponownie dołączyć, aby sprawdzić, czy jest nadal uruchomiony i zliczanie.</span><span class="sxs-lookup"><span data-stu-id="d328b-204">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

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

### <a name="delete-a-container"></a><span data-ttu-id="d328b-205">Usuwanie kontenera</span><span class="sxs-lookup"><span data-stu-id="d328b-205">Delete a container</span></span>

<span data-ttu-id="d328b-206">Na potrzeby tego artykułu nie chcesz, aby kontenery po prostu nie robiły nic.</span><span class="sxs-lookup"><span data-stu-id="d328b-206">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="d328b-207">Usuń poprzednio utworzony kontener.</span><span class="sxs-lookup"><span data-stu-id="d328b-207">Delete the container you previously created.</span></span> <span data-ttu-id="d328b-208">Jeśli kontener jest uruchomiony, zatrzymaj go.</span><span class="sxs-lookup"><span data-stu-id="d328b-208">If the container is running, stop it.</span></span>

```console
> docker stop gallant_lehmann
```

<span data-ttu-id="d328b-209">Poniższy przykład zawiera listę wszystkich kontenerów.</span><span class="sxs-lookup"><span data-stu-id="d328b-209">The following example lists all containers.</span></span> <span data-ttu-id="d328b-210">Następnie używa `docker rm` polecenia, aby usunąć kontener, a następnie sprawdza po raz drugi dla wszystkich uruchomionych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="d328b-210">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="d328b-211">Pojedynczy bieg</span><span class="sxs-lookup"><span data-stu-id="d328b-211">Single run</span></span>

<span data-ttu-id="d328b-212">Docker udostępnia `docker run` polecenie tworzenia i uruchamiania kontenera jako pojedynczego polecenia.</span><span class="sxs-lookup"><span data-stu-id="d328b-212">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="d328b-213">To polecenie eliminuje konieczność `docker create` uruchamiania, a następnie `docker start`.</span><span class="sxs-lookup"><span data-stu-id="d328b-213">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="d328b-214">Można również ustawić to polecenie, aby automatycznie usuwać kontener po zatrzymaniu kontenera.</span><span class="sxs-lookup"><span data-stu-id="d328b-214">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="d328b-215">Na przykład `docker run -it --rm` użyj do wykonania dwóch czynności, najpierw automatycznie użyj bieżącego terminala do połączenia z kontenerem, a następnie po zakończeniu kontenera usuń go:</span><span class="sxs-lookup"><span data-stu-id="d328b-215">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="d328b-216">Za `docker run -it`pomocą polecenia <kbd>CTRL + C</kbd> zatrzyma proces uruchomiony w kontenerze, który z kolei zatrzymuje kontener.</span><span class="sxs-lookup"><span data-stu-id="d328b-216">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="d328b-217">Ponieważ `--rm` parametr został dostarczony, kontener jest automatycznie usuwany po zatrzymaniu procesu.</span><span class="sxs-lookup"><span data-stu-id="d328b-217">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="d328b-218">Sprawdź, czy nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="d328b-218">Verify that it doesn't exist:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="d328b-219">Zmienianie PUNKTU WEJŚCIA</span><span class="sxs-lookup"><span data-stu-id="d328b-219">Change the ENTRYPOINT</span></span>

<span data-ttu-id="d328b-220">Polecenie `docker run` umożliwia również modyfikowanie `ENTRYPOINT` polecenia z pliku *Dockerfile* i uruchamianie czegoś innego, ale tylko dla tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="d328b-220">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="d328b-221">Na przykład użyj następującego `bash` polecenia, aby uruchomić lub `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="d328b-221">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="d328b-222">W razie potrzeby edytuj polecenie.</span><span class="sxs-lookup"><span data-stu-id="d328b-222">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="d328b-223">Windows</span><span class="sxs-lookup"><span data-stu-id="d328b-223">Windows</span></span>

<span data-ttu-id="d328b-224">W tym `ENTRYPOINT` przykładzie `cmd.exe`zostanie zmieniona na .</span><span class="sxs-lookup"><span data-stu-id="d328b-224">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="d328b-225"><kbd>Ctrl</kbd>+<kbd>C</kbd> jest wciśnięty, aby zakończyć proces i zatrzymać pojemnik.</span><span class="sxs-lookup"><span data-stu-id="d328b-225"><kbd>CTRL</kbd>+<kbd>C</kbd> is pressed to end the process and stop the container.</span></span>

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

#### <a name="linux"></a><span data-ttu-id="d328b-226">Linux</span><span class="sxs-lookup"><span data-stu-id="d328b-226">Linux</span></span>

<span data-ttu-id="d328b-227">W tym `ENTRYPOINT` przykładzie `bash`zostanie zmieniona na .</span><span class="sxs-lookup"><span data-stu-id="d328b-227">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="d328b-228">Polecenie `quit` jest uruchamiane, co kończy proces i zatrzymuje kontener.</span><span class="sxs-lookup"><span data-stu-id="d328b-228">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="d328b-229">Niezbędne polecenia</span><span class="sxs-lookup"><span data-stu-id="d328b-229">Essential commands</span></span>

<span data-ttu-id="d328b-230">Docker ma wiele różnych poleceń, które obejmują, co chcesz zrobić z kontenera i obrazów.</span><span class="sxs-lookup"><span data-stu-id="d328b-230">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="d328b-231">Te polecenia platformy Docker są niezbędne do zarządzania kontenerami:</span><span class="sxs-lookup"><span data-stu-id="d328b-231">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="d328b-232">docker build</span><span class="sxs-lookup"><span data-stu-id="d328b-232">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="d328b-233">uruchamianie platformy docker</span><span class="sxs-lookup"><span data-stu-id="d328b-233">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="d328b-234">docker ps</span><span class="sxs-lookup"><span data-stu-id="d328b-234">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="d328b-235">zatrzymanie platformy docker</span><span class="sxs-lookup"><span data-stu-id="d328b-235">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="d328b-236">rm docker</span><span class="sxs-lookup"><span data-stu-id="d328b-236">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="d328b-237">rmi platformy docker</span><span class="sxs-lookup"><span data-stu-id="d328b-237">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="d328b-238">obraz platformy docker</span><span class="sxs-lookup"><span data-stu-id="d328b-238">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="d328b-239">Oczyszczanie zasobów</span><span class="sxs-lookup"><span data-stu-id="d328b-239">Clean up resources</span></span>

<span data-ttu-id="d328b-240">Podczas tego samouczka utworzono kontenery i obrazy.</span><span class="sxs-lookup"><span data-stu-id="d328b-240">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="d328b-241">Jeśli chcesz, usuń te zasoby.</span><span class="sxs-lookup"><span data-stu-id="d328b-241">If you want, delete these resources.</span></span> <span data-ttu-id="d328b-242">Użyj następujących poleceń, aby</span><span class="sxs-lookup"><span data-stu-id="d328b-242">Use the following commands to</span></span>

01. <span data-ttu-id="d328b-243">Lista wszystkich kontenerów</span><span class="sxs-lookup"><span data-stu-id="d328b-243">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="d328b-244">Zatrzymaj uruchomione kontenery.</span><span class="sxs-lookup"><span data-stu-id="d328b-244">Stop containers that are running.</span></span> <span data-ttu-id="d328b-245">Reprezentuje `CONTAINER_NAME` nazwę automatycznie przypisane do kontenera.</span><span class="sxs-lookup"><span data-stu-id="d328b-245">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="d328b-246">Usuwanie kontenera</span><span class="sxs-lookup"><span data-stu-id="d328b-246">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="d328b-247">Następnie usuń wszystkie obrazy, których nie chcesz już na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d328b-247">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="d328b-248">Usuń obraz utworzony przez plik *Dockerfile,* a następnie usuń obraz .NET Core, na podstawie na podstawie pliku *Dockerfile.*</span><span class="sxs-lookup"><span data-stu-id="d328b-248">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="d328b-249">Można użyć **identyfikatora OBRAZU** lub **ciągu sformatowanego w formacie REPOZYTORIUM:TAG.**</span><span class="sxs-lookup"><span data-stu-id="d328b-249">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="d328b-250">Użyj `docker images` polecenia, aby wyświetlić listę zainstalowanych obrazów.</span><span class="sxs-lookup"><span data-stu-id="d328b-250">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="d328b-251">Pliki obrazów mogą być duże.</span><span class="sxs-lookup"><span data-stu-id="d328b-251">Image files can be large.</span></span> <span data-ttu-id="d328b-252">Zazwyczaj należy usunąć tymczasowe kontenery utworzone podczas testowania i tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d328b-252">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="d328b-253">Zazwyczaj zachować obrazy podstawowe z zainstalowanym czasem wykonywania, jeśli planujesz na tworzenie innych obrazów na podstawie tego środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="d328b-253">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d328b-254">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d328b-254">Next steps</span></span>

- [<span data-ttu-id="d328b-255">Dowiedz się, jak konteneryzować aplikację ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d328b-255">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="d328b-256">Wypróbuj ASP.NET Core Microservice Tutorial.</span><span class="sxs-lookup"><span data-stu-id="d328b-256">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="d328b-257">Przejrzyj usługi platformy Azure, które obsługują kontenery.</span><span class="sxs-lookup"><span data-stu-id="d328b-257">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="d328b-258">Przeczytaj o poleceniach dockerfile.</span><span class="sxs-lookup"><span data-stu-id="d328b-258">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="d328b-259">Zapoznaj się z narzędziami kontenerów dla programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d328b-259">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
