---
title: Konteneryzowanie aplikacji przy użyciu samouczka platformy Docker
description: W tym samouczku dowiesz się, jak konteneryzowanie aplikację .NET Core z platformą Docker.
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e012fcf78c88e7f64f6ee205cd69b69683bed9c3
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740758"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="fe78f-103">Samouczek: Konteneryzowanie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="fe78f-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="fe78f-104">W tym samouczku przedstawiono sposób tworzenia obrazu platformy Docker, który zawiera aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe78f-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="fe78f-105">Obraz może służyć do tworzenia kontenerów dla lokalnego środowiska projektowego, chmury prywatnej lub chmury publicznej.</span><span class="sxs-lookup"><span data-stu-id="fe78f-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="fe78f-106">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="fe78f-106">You'll learn to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="fe78f-107">Tworzenie i publikowanie prostej aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="fe78f-107">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="fe78f-108">Tworzenie i konfigurowanie pliku dockerfile dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="fe78f-108">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="fe78f-109">Tworzenie obrazu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fe78f-109">Build a Docker image</span></span>
> - <span data-ttu-id="fe78f-110">Tworzenie i uruchamianie kontenera platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fe78f-110">Create and run a Docker container</span></span>

<span data-ttu-id="fe78f-111">Zapoznaj się z tematem tworzenie i wdrażanie kontenerów platformy Docker dla aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe78f-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="fe78f-112">*Platforma Docker* korzysta z *aparatu platformy Docker* , aby szybko kompilować i spakować aplikacje jako *obrazy platformy Docker*.</span><span class="sxs-lookup"><span data-stu-id="fe78f-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="fe78f-113">Te obrazy są zapisywane w formacie *pliku dockerfile* , który ma zostać wdrożony i uruchomiony w kontenerze warstwowym.</span><span class="sxs-lookup"><span data-stu-id="fe78f-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fe78f-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="fe78f-114">Prerequisites</span></span>

<span data-ttu-id="fe78f-115">Zainstaluj następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="fe78f-115">Install the following prerequisites:</span></span>

- <span data-ttu-id="fe78f-116">[Zestaw SDK platformy .NET Core 2,2](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="fe78f-116">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="fe78f-117">Jeśli masz zainstalowany program .NET Core, użyj polecenia `dotnet --info`, aby określić, którego zestawu SDK używasz.</span><span class="sxs-lookup"><span data-stu-id="fe78f-117">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

- [<span data-ttu-id="fe78f-118">Platforma Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="fe78f-118">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

- <span data-ttu-id="fe78f-119">Tymczasowy folder roboczy dla przykładowej aplikacji *pliku dockerfile* i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe78f-119">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="fe78f-120">W tym samouczku nazwa `docker-working` jest używana jako folder roboczy.</span><span class="sxs-lookup"><span data-stu-id="fe78f-120">In this tutorial, the name `docker-working` is used as the working folder.</span></span>

### <a name="use-sdk-version-22"></a><span data-ttu-id="fe78f-121">Użyj zestawu SDK 2,2</span><span class="sxs-lookup"><span data-stu-id="fe78f-121">Use SDK version 2.2</span></span>

<span data-ttu-id="fe78f-122">Jeśli używasz zestawu SDK, który jest nowszy, na przykład 3,0, upewnij się, że aplikacja ma wymuszone użycie zestawu 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="fe78f-122">If you're using an SDK that is newer, like 3.0, make sure that your app is forced to use the 2.2 SDK.</span></span> <span data-ttu-id="fe78f-123">Utwórz plik o nazwie *Global. JSON* w folderze roboczym i wklej go w następującym kodzie JSON:</span><span class="sxs-lookup"><span data-stu-id="fe78f-123">Create a file named *global.json* in your working folder and paste in the following JSON code:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

<span data-ttu-id="fe78f-124">Zapisz ten plik.</span><span class="sxs-lookup"><span data-stu-id="fe78f-124">Save this file.</span></span> <span data-ttu-id="fe78f-125">Obecność pliku spowoduje wymuszenie użycia przez program .NET Core wersji 2,2 dla każdego polecenia `dotnet` wywołana z tego folderu i poniżej.</span><span class="sxs-lookup"><span data-stu-id="fe78f-125">The presence of file will force .NET Core to use version 2.2 for any `dotnet` command called from this folder and below.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="fe78f-126">Tworzenie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="fe78f-126">Create .NET Core app</span></span>

<span data-ttu-id="fe78f-127">Potrzebna jest aplikacja .NET Core, którą zostanie uruchomiony kontener platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="fe78f-127">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="fe78f-128">Otwórz Terminal, Utwórz folder roboczy, jeśli jeszcze tego nie zrobiono, a następnie wprowadź go.</span><span class="sxs-lookup"><span data-stu-id="fe78f-128">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="fe78f-129">W folderze roboczym Uruchom następujące polecenie, aby utworzyć nowy projekt w podkatalogu o nazwie *App*:</span><span class="sxs-lookup"><span data-stu-id="fe78f-129">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o app -n myapp
```

<span data-ttu-id="fe78f-130">Drzewo folderów będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="fe78f-130">Your folder tree will look like the following:</span></span>

```
docker-working
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

<span data-ttu-id="fe78f-131">`dotnet new` polecenie tworzy nowy folder o nazwie *App* i generuje aplikację "Hello World".</span><span class="sxs-lookup"><span data-stu-id="fe78f-131">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="fe78f-132">Wprowadź folder *App* i uruchom polecenie `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="fe78f-132">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="fe78f-133">Zobaczysz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="fe78f-133">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="fe78f-134">Szablon domyślny tworzy aplikację, która drukuje do terminalu, a następnie kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="fe78f-134">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="fe78f-135">Na potrzeby tego samouczka będziesz używać aplikacji, która nieskończonie pętli.</span><span class="sxs-lookup"><span data-stu-id="fe78f-135">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="fe78f-136">Otwórz plik *program.cs* w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="fe78f-136">Open the *Program.cs* file in a text editor.</span></span> <span data-ttu-id="fe78f-137">Powinien wyglądać podobnie do następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="fe78f-137">It should currently look like the following code:</span></span>

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

<span data-ttu-id="fe78f-138">Zastąp plik następującym kodem, który zlicza liczby w każdej sekundzie:</span><span class="sxs-lookup"><span data-stu-id="fe78f-138">Replace the file with the following code that counts numbers every second:</span></span>

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

<span data-ttu-id="fe78f-139">Zapisz plik i ponownie przetestuj program przy użyciu `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="fe78f-139">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="fe78f-140">Należy pamiętać, że ta aplikacja jest uruchamiana w nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="fe78f-140">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="fe78f-141">Użyj polecenia Cancel <kbd>CTRL</kbd>+<kbd>C</kbd> , aby go zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="fe78f-141">Use the cancel command <kbd>CTRL</kbd>+<kbd>C</kbd> to stop it.</span></span> <span data-ttu-id="fe78f-142">Zobaczysz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="fe78f-142">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="fe78f-143">Jeśli przekażesz liczbę w wierszu polecenia do aplikacji, będzie ona liczyć tylko do tej wartości, a następnie zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="fe78f-143">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="fe78f-144">Wypróbuj `dotnet run -- 5`, aby liczyć do pięciu.</span><span class="sxs-lookup"><span data-stu-id="fe78f-144">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="fe78f-145">Wszelkie parametry po `--` nie są przenoszone do polecenia `dotnet run` i zamiast tego są przesyłane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe78f-145">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="fe78f-146">Publikowanie aplikacji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="fe78f-146">Publish .NET Core app</span></span>

<span data-ttu-id="fe78f-147">Przed dodaniem aplikacji .NET Core do obrazu platformy Docker należy opublikować ją.</span><span class="sxs-lookup"><span data-stu-id="fe78f-147">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="fe78f-148">Upewnij się, że kontener uruchamia opublikowaną wersję aplikacji po jej uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="fe78f-148">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="fe78f-149">W folderze roboczym wprowadź folder *App* z przykładowym kodem źródłowym i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="fe78f-149">From the working folder, enter the *app* folder with the example source code and run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="fe78f-150">To polecenie kompiluje aplikację do folderu *Publikowanie* .</span><span class="sxs-lookup"><span data-stu-id="fe78f-150">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="fe78f-151">Ścieżka do folderu *publikowania* z folderu roboczego powinna być `.\app\bin\Release\netcoreapp2.2\publish\`</span><span class="sxs-lookup"><span data-stu-id="fe78f-151">The path to the *publish* folder from the working folder should be `.\app\bin\Release\netcoreapp2.2\publish\`</span></span>

<span data-ttu-id="fe78f-152">Pobierz listę katalogów folderu publikowania, aby sprawdzić, czy *plik MojaApl. dll* został utworzony.</span><span class="sxs-lookup"><span data-stu-id="fe78f-152">Get a directory listing of the publish folder to verify that the *myapp.dll* was created.</span></span> <span data-ttu-id="fe78f-153">W folderze *aplikacja* Uruchom jedno z następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="fe78f-153">From the *app* folder, run one of the following commands:</span></span>

```console
> dir bin\Release\netcoreapp2.2\publish
 Directory of C:\docker-working\app\bin\Release\netcoreapp2.2\publish

04/05/2019  11:00 AM    <DIR>          .
04/05/2019  11:00 AM    <DIR>          ..
04/05/2019  11:00 AM               447 myapp.deps.json
04/05/2019  11:00 AM             4,608 myapp.dll
04/05/2019  11:00 AM               448 myapp.pdb
04/05/2019  11:00 AM               154 myapp.runtimeconfig.json
```

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp2.2/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="fe78f-154">Tworzenie pliku dockerfile</span><span class="sxs-lookup"><span data-stu-id="fe78f-154">Create the Dockerfile</span></span>

<span data-ttu-id="fe78f-155">Plik *pliku dockerfile* jest używany przez polecenie `docker build`, aby utworzyć obraz kontenera.</span><span class="sxs-lookup"><span data-stu-id="fe78f-155">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="fe78f-156">Ten plik jest plikiem w postaci zwykłego tekstu o nazwie *pliku dockerfile* , który nie ma rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="fe78f-156">This file is a plaintext file named *Dockerfile* that does not have an extension.</span></span>

<span data-ttu-id="fe78f-157">W terminalu przejdź do katalogu roboczego, który został utworzony na początku.</span><span class="sxs-lookup"><span data-stu-id="fe78f-157">In your terminal, navigate up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="fe78f-158">Utwórz plik o nazwie *pliku dockerfile* w folderze roboczym i otwórz go w edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="fe78f-158">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="fe78f-159">Dodaj następujące polecenie jako pierwszy wiersz pliku:</span><span class="sxs-lookup"><span data-stu-id="fe78f-159">Add the following command as the first line of the file:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="fe78f-160">Polecenie `FROM` informuje platformę Docker o konieczności ściągnięcia obrazu oznaczonego jako **2,2** z repozytorium **MCR.Microsoft.com/dotnet/Core/Runtime** .</span><span class="sxs-lookup"><span data-stu-id="fe78f-160">The `FROM` command tells Docker to pull down the image tagged **2.2** from the **mcr.microsoft.com/dotnet/core/runtime** repository.</span></span> <span data-ttu-id="fe78f-161">Upewnij się, że używasz środowiska uruchomieniowego programu .NET Core, które pasuje do środowiska uruchomieniowego wskazywanego przez zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="fe78f-161">Make sure that you pull the .NET Core runtime that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="fe78f-162">Na przykład aplikacja utworzona w poprzedniej sekcji używa zestawu .NET Core 2,2 SDK i utworzyła aplikację, która jest przeznaczona dla platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="fe78f-162">For example, the app created in the previous section used the .NET Core 2.2 SDK and created an app that targeted .NET Core 2.2.</span></span> <span data-ttu-id="fe78f-163">Dlatego obraz podstawowy, do którego odwołuje się *pliku dockerfile* , jest oznaczony **2,2**.</span><span class="sxs-lookup"><span data-stu-id="fe78f-163">So the base image referred to in the *Dockerfile* is tagged with **2.2**.</span></span>

<span data-ttu-id="fe78f-164">Zapisz plik *pliku dockerfile* .</span><span class="sxs-lookup"><span data-stu-id="fe78f-164">Save the *Dockerfile* file.</span></span> <span data-ttu-id="fe78f-165">Struktura katalogów folderu roboczego powinna wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="fe78f-165">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="fe78f-166">Niektóre pliki i foldery z bardziej szczegółowymi poziomami zostały wycięte w celu zaoszczędzenia miejsca w artykule:</span><span class="sxs-lookup"><span data-stu-id="fe78f-166">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

```
docker-working
│   Dockerfile
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp2.2
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

<span data-ttu-id="fe78f-167">W terminalu uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="fe78f-167">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="fe78f-168">Platforma Docker będzie przetwarzać każdy wiersz w *pliku dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="fe78f-168">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="fe78f-169">`.` w poleceniu `docker build` instruuje platformę Docker, aby użyć bieżącego folderu do znalezienia *pliku dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="fe78f-169">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="fe78f-170">To polecenie kompiluje obraz i tworzy lokalne repozytorium o nazwie **obraz** , który wskazuje na ten obraz.</span><span class="sxs-lookup"><span data-stu-id="fe78f-170">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="fe78f-171">Po zakończeniu tego polecenia Uruchom `docker images`, aby wyświetlić listę zainstalowanych obrazów:</span><span class="sxs-lookup"><span data-stu-id="fe78f-171">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="fe78f-172">Zwróć uwagę, że te dwa obrazy mają tę samą wartość **identyfikatora obrazu** .</span><span class="sxs-lookup"><span data-stu-id="fe78f-172">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="fe78f-173">Wartość jest taka sama między obu obrazów, ponieważ jedyne polecenie w *pliku dockerfile* było podstawą nowego obrazu na istniejącym obrazie.</span><span class="sxs-lookup"><span data-stu-id="fe78f-173">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="fe78f-174">Dodajmy dwa polecenia do *pliku dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="fe78f-174">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="fe78f-175">Każde polecenie tworzy nową warstwę obrazu z końcowym poleceniem reprezentującym obraz, do którego będzie **wskazywał repozytorium.**</span><span class="sxs-lookup"><span data-stu-id="fe78f-175">Each command creates a new image layer with the final command representing the image the **myimage** repository will point to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="fe78f-176">Polecenie `COPY` instruuje platformę Docker o skopiowanie określonego folderu na komputerze do folderu w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="fe78f-176">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="fe78f-177">W tym przykładzie folder *publikacji* jest kopiowany do folderu o nazwie *aplikacja* w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="fe78f-177">In this example, the *publish* folder is copied to a folder named *app* in the container.</span></span>

<span data-ttu-id="fe78f-178">Następne polecenie `ENTRYPOINT`, instruuje platformę Docker, aby skonfigurować kontener do uruchamiania jako plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="fe78f-178">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="fe78f-179">Po rozpoczęciu kontenera zostanie uruchomione polecenie `ENTRYPOINT`.</span><span class="sxs-lookup"><span data-stu-id="fe78f-179">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="fe78f-180">Po zakończeniu tego polecenia kontener zostanie automatycznie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="fe78f-180">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="fe78f-181">W terminalu uruchom `docker build -t myimage -f Dockerfile .` i po zakończeniu tego polecenia Uruchom polecenie `docker images`.</span><span class="sxs-lookup"><span data-stu-id="fe78f-181">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  819.7kB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/runtime:2.2
 ---> d51bb4452469
Step 2/3 : COPY app/bin/Release/netcoreapp2.2/publish/ app/
 ---> a1e98ac62017
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in f34da5c18e7c
Removing intermediate container f34da5c18e7c
 ---> ddcc6646461b
Successfully built ddcc6646461b
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              ddcc6646461b        10 seconds ago      314MB
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="fe78f-182">Każde polecenie w *pliku dockerfile* wygenerowało warstwę i utworzyła **Identyfikator obrazu**.</span><span class="sxs-lookup"><span data-stu-id="fe78f-182">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="fe78f-183">Końcowy **Identyfikator obrazu** (będzie inny) to **ddcc6646461b** , a następnie utworzysz kontener oparty na tym obrazie.</span><span class="sxs-lookup"><span data-stu-id="fe78f-183">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="fe78f-184">Tworzenie kontenera</span><span class="sxs-lookup"><span data-stu-id="fe78f-184">Create a container</span></span>

<span data-ttu-id="fe78f-185">Teraz, gdy masz obraz zawierający aplikację, możesz utworzyć kontener.</span><span class="sxs-lookup"><span data-stu-id="fe78f-185">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="fe78f-186">Kontener można utworzyć na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="fe78f-186">You can create a container in two ways.</span></span> <span data-ttu-id="fe78f-187">Najpierw utwórz nowy kontener, który został zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="fe78f-187">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

<span data-ttu-id="fe78f-188">Polecenie `docker create` from powyżej utworzy kontener oparty na obrazie **obrazu** .</span><span class="sxs-lookup"><span data-stu-id="fe78f-188">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="fe78f-189">Dane wyjściowe tego polecenia pokazują, że **Identyfikator kontenera** (zostanie inaczej) utworzonego kontenera.</span><span class="sxs-lookup"><span data-stu-id="fe78f-189">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="fe78f-190">Aby wyświetlić listę *wszystkich* kontenerów, użyj `docker ps -a` polecenia:</span><span class="sxs-lookup"><span data-stu-id="fe78f-190">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a><span data-ttu-id="fe78f-191">Zarządzanie kontenerem</span><span class="sxs-lookup"><span data-stu-id="fe78f-191">Manage the container</span></span>

<span data-ttu-id="fe78f-192">Do każdego kontenera jest przypisywana nazwa Losowa, której można użyć do odwoływania się do tego wystąpienia kontenera.</span><span class="sxs-lookup"><span data-stu-id="fe78f-192">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="fe78f-193">Na przykład kontener, który został utworzony automatycznie wybiera nazwę **boring_matsumoto** (będzie się różnić), a ta nazwa może być używana do uruchamiania kontenera.</span><span class="sxs-lookup"><span data-stu-id="fe78f-193">For example, the container that was created automatically chose the name **boring_matsumoto** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="fe78f-194">Automatyczna nazwa zostanie zastąpiona określonym przez użycie parametru `docker create --name`.</span><span class="sxs-lookup"><span data-stu-id="fe78f-194">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="fe78f-195">Poniższy przykład używa polecenia `docker start`, aby uruchomić kontener, a następnie używa polecenia `docker ps` do wyświetlania tylko kontenerów z systemem:</span><span class="sxs-lookup"><span data-stu-id="fe78f-195">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

<span data-ttu-id="fe78f-196">Analogicznie, polecenie `docker stop` spowoduje zatrzymanie kontenera.</span><span class="sxs-lookup"><span data-stu-id="fe78f-196">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="fe78f-197">Poniższy przykład używa polecenia `docker stop`, aby zatrzymać kontener, a następnie używa polecenia `docker ps`, aby pokazać, że żaden kontener nie jest uruchomiony:</span><span class="sxs-lookup"><span data-stu-id="fe78f-197">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="fe78f-198">Nawiązywanie połączenia z kontenerem</span><span class="sxs-lookup"><span data-stu-id="fe78f-198">Connect to a container</span></span>

<span data-ttu-id="fe78f-199">Po uruchomieniu kontenera można nawiązać z nim połączenie, aby wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="fe78f-199">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="fe78f-200">Użyj poleceń `docker start` i `docker attach`, aby uruchomić kontener i uzyskać wgląd w strumieniu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fe78f-200">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="fe78f-201">W tym przykładzie polecenie <kbd>Ctrl + C</kbd> służy do odłączenia od uruchomionego kontenera.</span><span class="sxs-lookup"><span data-stu-id="fe78f-201">In this example, the <kbd>CTRL + C</kbd> command is used to detach from the running container.</span></span> <span data-ttu-id="fe78f-202">Może to ostatecznie zakończyć proces w kontenerze, co spowoduje zatrzymanie kontenera.</span><span class="sxs-lookup"><span data-stu-id="fe78f-202">This may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="fe78f-203">`--sig-proxy=false` parametr gwarantuje, że <kbd>naciśnięcie klawiszy CTRL + C</kbd> nie zatrzyma procesu w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="fe78f-203">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="fe78f-204">Po odłączeniu od kontenera ponownie Dołącz, aby upewnić się, że nadal działa i zlicza.</span><span class="sxs-lookup"><span data-stu-id="fe78f-204">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker attach --sig-proxy=false boring_matsumoto
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false boring_matsumoto
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="fe78f-205">Usuwanie kontenera</span><span class="sxs-lookup"><span data-stu-id="fe78f-205">Delete a container</span></span>

<span data-ttu-id="fe78f-206">Na potrzeby tego artykułu nie ma potrzeby, aby kontenery zostały jedynie obsunięte.</span><span class="sxs-lookup"><span data-stu-id="fe78f-206">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="fe78f-207">Usuń kontener, który został wcześniej utworzony.</span><span class="sxs-lookup"><span data-stu-id="fe78f-207">Delete the container you previously created.</span></span> <span data-ttu-id="fe78f-208">Jeśli kontener jest uruchomiony, Zatrzymaj go.</span><span class="sxs-lookup"><span data-stu-id="fe78f-208">If the container is running, stop it.</span></span>

```console
> docker stop boring_matsumoto
```

<span data-ttu-id="fe78f-209">Poniższy przykład wyświetla listę wszystkich kontenerów.</span><span class="sxs-lookup"><span data-stu-id="fe78f-209">The following example lists all containers.</span></span> <span data-ttu-id="fe78f-210">Następnie używa polecenia `docker rm`, aby usunąć kontener, a następnie sprawdza drugi czas dla wszystkich uruchomionych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="fe78f-210">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="fe78f-211">Pojedynczy przebieg</span><span class="sxs-lookup"><span data-stu-id="fe78f-211">Single run</span></span>

<span data-ttu-id="fe78f-212">Platforma Docker udostępnia polecenie `docker run`, aby utworzyć i uruchomić kontener jako pojedyncze polecenie.</span><span class="sxs-lookup"><span data-stu-id="fe78f-212">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="fe78f-213">To polecenie eliminuje konieczność uruchamiania `docker create` a następnie `docker start`.</span><span class="sxs-lookup"><span data-stu-id="fe78f-213">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="fe78f-214">Możesz również ustawić to polecenie, aby automatycznie usuwać kontener po zatrzymaniu kontenera.</span><span class="sxs-lookup"><span data-stu-id="fe78f-214">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="fe78f-215">Na przykład użyj `docker run -it --rm`, aby wykonać dwa czynności, w pierwszej kolejności automatycznie Użyj bieżącego terminalu do nawiązania połączenia z kontenerem, a następnie usuń go:</span><span class="sxs-lookup"><span data-stu-id="fe78f-215">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="fe78f-216">Za pomocą `docker run -it`polecenie <kbd>Ctrl + C</kbd> przestanie działać w kontenerze, który z kolei zatrzymuje kontener.</span><span class="sxs-lookup"><span data-stu-id="fe78f-216">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="fe78f-217">Ponieważ podano parametr `--rm`, kontener jest automatycznie usuwany, gdy proces zostanie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="fe78f-217">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="fe78f-218">Sprawdź, czy nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="fe78f-218">Verify that it does not exist:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="fe78f-219">Zmień punkt wejścia</span><span class="sxs-lookup"><span data-stu-id="fe78f-219">Change the ENTRYPOINT</span></span>

<span data-ttu-id="fe78f-220">`docker run` polecenie umożliwia również modyfikowanie polecenia `ENTRYPOINT` z *pliku dockerfile* i uruchamianie czegoś innego, ale tylko dla tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="fe78f-220">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="fe78f-221">Na przykład użyj następującego polecenia, aby uruchomić `bash` lub `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="fe78f-221">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="fe78f-222">W razie potrzeby zmodyfikuj polecenie.</span><span class="sxs-lookup"><span data-stu-id="fe78f-222">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="fe78f-223">Windows</span><span class="sxs-lookup"><span data-stu-id="fe78f-223">Windows</span></span>

<span data-ttu-id="fe78f-224">W tym przykładzie `ENTRYPOINT` został zmieniony na `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="fe78f-224">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="fe78f-225"><kbd>Naciśnij klawisz CTRL</kbd>+<kbd>C</kbd> , aby zakończyć proces i zatrzymać kontener.</span><span class="sxs-lookup"><span data-stu-id="fe78f-225"><kbd>CTRL</kbd>+<kbd>C</kbd> is pressed to end the process and stop the container.</span></span>

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

#### <a name="linux"></a><span data-ttu-id="fe78f-226">Linux</span><span class="sxs-lookup"><span data-stu-id="fe78f-226">Linux</span></span>

<span data-ttu-id="fe78f-227">W tym przykładzie `ENTRYPOINT` został zmieniony na `bash`.</span><span class="sxs-lookup"><span data-stu-id="fe78f-227">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="fe78f-228">`quit` polecenie jest uruchamiane, które zakończy proces i Zatrzymaj kontener.</span><span class="sxs-lookup"><span data-stu-id="fe78f-228">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="fe78f-229">Najważniejsze polecenia</span><span class="sxs-lookup"><span data-stu-id="fe78f-229">Essential commands</span></span>

<span data-ttu-id="fe78f-230">Platforma Docker ma wiele różnych poleceń, które obejmują, co chcesz zrobić z kontenerem i obrazami.</span><span class="sxs-lookup"><span data-stu-id="fe78f-230">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="fe78f-231">Te polecenia platformy Docker mają kluczowe znaczenie dla zarządzania kontenerami:</span><span class="sxs-lookup"><span data-stu-id="fe78f-231">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="fe78f-232">Kompilacja platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fe78f-232">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="fe78f-233">uruchomienie platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fe78f-233">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="fe78f-234">Docker PS</span><span class="sxs-lookup"><span data-stu-id="fe78f-234">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="fe78f-235">zatrzymanie platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fe78f-235">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="fe78f-236">Platforma Docker RM</span><span class="sxs-lookup"><span data-stu-id="fe78f-236">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="fe78f-237">Docker RMI</span><span class="sxs-lookup"><span data-stu-id="fe78f-237">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="fe78f-238">obraz platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fe78f-238">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="fe78f-239">Oczyszczanie zasobów</span><span class="sxs-lookup"><span data-stu-id="fe78f-239">Clean up resources</span></span>

<span data-ttu-id="fe78f-240">W tym samouczku utworzono kontenery i obrazy.</span><span class="sxs-lookup"><span data-stu-id="fe78f-240">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="fe78f-241">Jeśli chcesz, usuń te zasoby.</span><span class="sxs-lookup"><span data-stu-id="fe78f-241">If you want, delete these resources.</span></span> <span data-ttu-id="fe78f-242">Użyj następujących poleceń, aby</span><span class="sxs-lookup"><span data-stu-id="fe78f-242">Use the following commands to</span></span>

01. <span data-ttu-id="fe78f-243">Wyświetl listę wszystkich kontenerów</span><span class="sxs-lookup"><span data-stu-id="fe78f-243">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="fe78f-244">Zatrzymaj uruchomione kontenery.</span><span class="sxs-lookup"><span data-stu-id="fe78f-244">Stop containers that are running.</span></span> <span data-ttu-id="fe78f-245">`CONTAINER_NAME` reprezentuje nazwę, która jest automatycznie przypisywana do kontenera.</span><span class="sxs-lookup"><span data-stu-id="fe78f-245">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="fe78f-246">Usuwanie kontenera</span><span class="sxs-lookup"><span data-stu-id="fe78f-246">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="fe78f-247">Następnie usuń wszystkie obrazy, które nie są już potrzebne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="fe78f-247">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="fe78f-248">Usuń obraz utworzony przez *pliku dockerfile* , a następnie Usuń obraz platformy .NET Core, na którym oparto *pliku dockerfile* .</span><span class="sxs-lookup"><span data-stu-id="fe78f-248">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="fe78f-249">Możesz użyć **identyfikatora obrazu** lub ciągu sformatowanego jako **tag** .</span><span class="sxs-lookup"><span data-stu-id="fe78f-249">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="fe78f-250">Użyj `docker images` polecenia, aby wyświetlić listę zainstalowanych obrazów.</span><span class="sxs-lookup"><span data-stu-id="fe78f-250">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="fe78f-251">Pliki obrazów mogą być duże.</span><span class="sxs-lookup"><span data-stu-id="fe78f-251">Image files can be large.</span></span> <span data-ttu-id="fe78f-252">Zazwyczaj można usunąć kontenery tymczasowe, które zostały utworzone podczas testowania i opracowywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe78f-252">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="fe78f-253">Obrazy podstawowe z zainstalowanym środowiskiem uruchomieniowym zwykle są zachowywane, jeśli planujesz tworzenie innych obrazów na podstawie tego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="fe78f-253">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fe78f-254">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="fe78f-254">Next steps</span></span>

- [<span data-ttu-id="fe78f-255">Wypróbuj ASP.NET Core samouczka mikrousług.</span><span class="sxs-lookup"><span data-stu-id="fe78f-255">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="fe78f-256">Przejrzyj usługi platformy Azure, które obsługują kontenery.</span><span class="sxs-lookup"><span data-stu-id="fe78f-256">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="fe78f-257">Przeczytaj o poleceniach pliku dockerfile.</span><span class="sxs-lookup"><span data-stu-id="fe78f-257">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="fe78f-258">Poznaj narzędzia kontenerów dla programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fe78f-258">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
