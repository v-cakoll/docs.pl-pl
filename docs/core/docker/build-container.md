---
title: Konteneryzowanie aplikacji za pomocą samouczka platformy Docker
description: W tym samouczku dowiesz się, jak konteneryzowanie aplikacji .NET Core za pomocą platformy Docker.
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 6a1d366aceecdf4bd22a04f823aa6805060f8069
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539192"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="8517e-103">Samouczek: Konteneryzowanie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="8517e-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="8517e-104">Tym samouczku pokazano, jak utworzyć obraz platformy Docker, który zawiera aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8517e-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="8517e-105">Obraz, który może służyć do utworzenia kontenerów dla lokalnego środowiska deweloperskiego, Chmura prywatna lub chmury publicznej.</span><span class="sxs-lookup"><span data-stu-id="8517e-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="8517e-106">Dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="8517e-106">You'll learn to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="8517e-107">Tworzenie i publikowanie prostą aplikację platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="8517e-107">Create and publish a simple .NET Core app</span></span>
> * <span data-ttu-id="8517e-108">Tworzenie i konfigurowanie pliku Dockerfile dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="8517e-108">Create and configure a Dockerfile for .NET Core</span></span>
> * <span data-ttu-id="8517e-109">Zbuduj obraz Docker</span><span class="sxs-lookup"><span data-stu-id="8517e-109">Build a Docker image</span></span>
> * <span data-ttu-id="8517e-110">Tworzenie i uruchamianie kontenera platformy Docker</span><span class="sxs-lookup"><span data-stu-id="8517e-110">Create and run a Docker container</span></span>

<span data-ttu-id="8517e-111">Będziesz zrozumieć Docker kontenera, twórz i wdrażaj zadania dla aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8517e-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="8517e-112">*Platforma Docker* używa *aparat platformy Docker* umożliwiają szybkie tworzenie i pakowanie aplikacji jako *obrazów platformy Docker*.</span><span class="sxs-lookup"><span data-stu-id="8517e-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="8517e-113">Te obrazy są zapisywane *pliku Dockerfile* format zostaną wdrożone i uruchomione w kontenerze warstwowej.</span><span class="sxs-lookup"><span data-stu-id="8517e-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8517e-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8517e-114">Prerequisites</span></span>

<span data-ttu-id="8517e-115">Zainstaluj następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="8517e-115">Install the following prerequisites:</span></span>

* <span data-ttu-id="8517e-116">[.NET core SDK 2,2](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="8517e-116">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="8517e-117">Jeśli masz platformy .NET Core zainstalowany, użyj `dotnet --info` polecenie, aby określić zestaw SDK, których używasz.</span><span class="sxs-lookup"><span data-stu-id="8517e-117">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

* [<span data-ttu-id="8517e-118">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="8517e-118">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

* <span data-ttu-id="8517e-119">Tymczasowy folder roboczy dla *pliku Dockerfile* i .NET Core przykładowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8517e-119">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="8517e-120">W tym samouczku nazwa `docker-working` jest używany jako folder roboczy.</span><span class="sxs-lookup"><span data-stu-id="8517e-120">In this tutorial, the name `docker-working` is used as the working folder.</span></span>

### <a name="use-sdk-version-22"></a><span data-ttu-id="8517e-121">Korzystanie z zestawu SDK w wersji 2.2</span><span class="sxs-lookup"><span data-stu-id="8517e-121">Use SDK version 2.2</span></span>

<span data-ttu-id="8517e-122">Jeśli używasz zestawu SDK, która jest nowsza, takich jak 3.0, upewnij się, czy aplikacja jest zmuszony do używania 2,2 zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="8517e-122">If you're using an SDK that is newer, like 3.0, make sure that your app is forced to use the 2.2 SDK.</span></span> <span data-ttu-id="8517e-123">Utwórz plik o nazwie `global.json` w folderze roboczym i wklej następujący kod json:</span><span class="sxs-lookup"><span data-stu-id="8517e-123">Create a file named `global.json` in your working folder and paste in the following json code:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

<span data-ttu-id="8517e-124">Zapisz ten plik.</span><span class="sxs-lookup"><span data-stu-id="8517e-124">Save this file.</span></span> <span data-ttu-id="8517e-125">Obecność pliku spowoduje to wymuszenie platformy .NET Core, aby użyć wersji 2.2 dla każdego `dotnet` polecenie wywołane z tego folderu i poniżej.</span><span class="sxs-lookup"><span data-stu-id="8517e-125">The presence of file will force .NET Core to use version 2.2 for any `dotnet` command called from this folder and below.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="8517e-126">Tworzenie, .NET Core aplikacji</span><span class="sxs-lookup"><span data-stu-id="8517e-126">Create .NET Core app</span></span>

<span data-ttu-id="8517e-127">Potrzebujesz aplikacji .NET Core, która uruchomi kontener platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="8517e-127">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="8517e-128">Otwórz terminal, Utwórz folder roboczy, jeśli jeszcze tego nie zrobiłeś i wprowadź go.</span><span class="sxs-lookup"><span data-stu-id="8517e-128">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="8517e-129">W folderze roboczym uruchom następujące polecenie, aby utworzyć nowy projekt w podkatalogu o nazwie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="8517e-129">In the working folder, run the following command to create a new project in a subdirectory named app:</span></span>

```console
dotnet new console -o app -n myapp
```

<span data-ttu-id="8517e-130">Drzewo folderów będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="8517e-130">Your folder tree will look like the following:</span></span>

```console
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

<span data-ttu-id="8517e-131">`dotnet new` Polecenie tworzy nowy folder o nazwie *aplikacji* i wygeneruje aplikację "Hello World".</span><span class="sxs-lookup"><span data-stu-id="8517e-131">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="8517e-132">Wprowadź *aplikacji* folderu i uruchom polecenie `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="8517e-132">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="8517e-133">Zostanie wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="8517e-133">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="8517e-134">Domyślny szablon tworzy aplikację, która drukuje do terminala, a następnie kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="8517e-134">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="8517e-135">W tym samouczku użyjesz aplikacji, która działa w pętli nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="8517e-135">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="8517e-136">Otwórz **Program.cs** plik w edytorze tekstów.</span><span class="sxs-lookup"><span data-stu-id="8517e-136">Open the **Program.cs** file in a text editor.</span></span> <span data-ttu-id="8517e-137">On obecnie powinien wyglądać podobnie do poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="8517e-137">It should currently look like the following code:</span></span>

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

<span data-ttu-id="8517e-138">Zastąp go następującym kodem, który zlicza liczby co sekundę:</span><span class="sxs-lookup"><span data-stu-id="8517e-138">Replace the file with the following code that counts numbers every second:</span></span>

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
            while(max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

<span data-ttu-id="8517e-139">Zapisz plik i przetestować program ponownie, używając `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="8517e-139">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="8517e-140">Należy pamiętać, że ta aplikacja działa przez czas nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="8517e-140">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="8517e-141">Za pomocą polecenia Anuluj <kbd>klawisze CTRL + C</kbd> go zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="8517e-141">Use the cancel command <kbd>CTRL + C</kbd> to stop it.</span></span> <span data-ttu-id="8517e-142">Zostanie wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="8517e-142">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="8517e-143">Jeśli przekażesz liczbą w wierszu polecenia do aplikacji, zostanie tylko policzone maksymalnie, kwota, a następnie zamknij.</span><span class="sxs-lookup"><span data-stu-id="8517e-143">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="8517e-144">Wypróbuj ją za pomocą `dotnet run -- 5` zliczania do pięciu.</span><span class="sxs-lookup"><span data-stu-id="8517e-144">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="8517e-145">Wszelkie parametry po `--` nie zostaną przekazane do `dotnet run` polecenia, a zamiast tego są przekazywane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8517e-145">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="8517e-146">Publikowanie .NET Core aplikacji</span><span class="sxs-lookup"><span data-stu-id="8517e-146">Publish .NET Core app</span></span>

<span data-ttu-id="8517e-147">Przed dodaniem aplikacji .NET Core do obrazu platformy Docker, należy go opublikować.</span><span class="sxs-lookup"><span data-stu-id="8517e-147">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="8517e-148">Chcesz upewnić się, że kontener działa opublikowanej wersji aplikacji, gdy jest ona uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="8517e-148">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="8517e-149">W folderze roboczym wprowadź **aplikacji** folderu w przykładzie kodu źródłowego i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="8517e-149">From the working folder, enter the **app** folder with the example source code and run the following command:</span></span>

```console
dotnet publish -c Release
```

<span data-ttu-id="8517e-150">To polecenie kompiluje aplikację, aby **publikowania** folderu.</span><span class="sxs-lookup"><span data-stu-id="8517e-150">This command compiles your app to the **publish** folder.</span></span> <span data-ttu-id="8517e-151">Ścieżka do **publikowania** folder z folderu roboczego powinien być `.\app\bin\Release\netcoreapp2.2\publish\`</span><span class="sxs-lookup"><span data-stu-id="8517e-151">The path to the **publish** folder from the working folder should be `.\app\bin\Release\netcoreapp2.2\publish\`</span></span>

<span data-ttu-id="8517e-152">Pobierz listę katalogów folderu publikowania, aby sprawdzić, czy **myapp.dll** został utworzony.</span><span class="sxs-lookup"><span data-stu-id="8517e-152">Get a directory listing of the publish folder to verify that the **myapp.dll** was created.</span></span> <span data-ttu-id="8517e-153">Z **aplikacji** folder, uruchom jedno z następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="8517e-153">From the **app** folder, run one of the following commands:</span></span>

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

## <a name="create-the-dockerfile"></a><span data-ttu-id="8517e-154">Utwórz plik Dockerfile</span><span class="sxs-lookup"><span data-stu-id="8517e-154">Create the Dockerfile</span></span>

<span data-ttu-id="8517e-155">*Pliku Dockerfile* plik jest używany przez `docker build` polecenie, aby utworzyć obraz kontenera.</span><span class="sxs-lookup"><span data-stu-id="8517e-155">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="8517e-156">Ten plik jest plikiem zwykłego tekstu, o nazwie *pliku Dockerfile* nie ma rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="8517e-156">This file is a plaintext file named *Dockerfile* that does not have an extension.</span></span>

<span data-ttu-id="8517e-157">W terminalu przejdź do katalogu do folderu roboczego, który został utworzony na początku w górę.</span><span class="sxs-lookup"><span data-stu-id="8517e-157">In your terminal, navigate to up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="8517e-158">Utwórz plik o nazwie *pliku Dockerfile* w folderze roboczym, a następnie otwórz go w edytorze tekstów.</span><span class="sxs-lookup"><span data-stu-id="8517e-158">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="8517e-159">W pierwszym wierszu pliku, należy dodać następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="8517e-159">Add the following command as the first line of the file:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="8517e-160">`FROM` Polecenie informuje, Docker, aby ściągnąć obraz oznaczony **2.2** z **mcr.microsoft.com/dotnet/core/runtime** repozytorium.</span><span class="sxs-lookup"><span data-stu-id="8517e-160">The `FROM` command tells Docker to pull down the image tagged **2.2** from the **mcr.microsoft.com/dotnet/core/runtime** repository.</span></span> <span data-ttu-id="8517e-161">Upewnij się, ściągania środowiska uruchomieniowego .NET Core, które odpowiada celem zestawu SDK środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="8517e-161">Make sure that you pull the .NET Core runtime that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="8517e-162">Na przykład aplikację utworzoną w poprzedniej sekcji używane .NET Core 2.2 SDK i utworzyć aplikację, która docelowej platformy .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="8517e-162">For example, the app created in the previous section used the .NET Core 2.2 SDK and created an app that targeted .NET Core 2.2.</span></span> <span data-ttu-id="8517e-163">Dlatego obraz podstawowy, o których mowa w *pliku Dockerfile* oznakowano **2.2**.</span><span class="sxs-lookup"><span data-stu-id="8517e-163">So the base image referred to in the *Dockerfile* is tagged with **2.2**.</span></span>

<span data-ttu-id="8517e-164">Zapisz *pliku Dockerfile* pliku.</span><span class="sxs-lookup"><span data-stu-id="8517e-164">Save the *Dockerfile* file.</span></span> <span data-ttu-id="8517e-165">Struktura katalogów folderu roboczego powinien wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="8517e-165">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="8517e-166">Ma część poziom głębiej pliki i foldery Wytnij, aby zaoszczędzić miejsce w artykule:</span><span class="sxs-lookup"><span data-stu-id="8517e-166">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

```console
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

<span data-ttu-id="8517e-167">W terminalu Uruchom `docker build -t myimage -f Dockerfile .` i Docker będzie przetwarzać każdy wiersz w *pliku Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="8517e-167">From your terminal, run `docker build -t myimage -f Dockerfile .` and Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="8517e-168">`.` w `docker build` polecenie informuje platformy docker do korzystania z bieżącego folderu można znaleźć *pliku Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="8517e-168">The `.` in the `docker build` command tells docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="8517e-169">To polecenie tworzy obraz i tworzy lokalne repozytorium o nazwie **myimage** wskazującego na tym obrazie.</span><span class="sxs-lookup"><span data-stu-id="8517e-169">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="8517e-170">Po zakończeniu działania tego polecenia, uruchom `docker images` umożliwia wyświetlenie listy obrazów zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="8517e-170">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="8517e-171">Zwróć uwagę, że dwa obrazy współużytkować ten sam **identyfikator obrazu** wartość.</span><span class="sxs-lookup"><span data-stu-id="8517e-171">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="8517e-172">Wartość jest taka sama oba obrazy, ponieważ tylko polecenia w *pliku Dockerfile* został podstawą nowy obraz istniejącego obrazu.</span><span class="sxs-lookup"><span data-stu-id="8517e-172">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="8517e-173">Dodajmy dwa polecenia, aby *pliku Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="8517e-173">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="8517e-174">Każde polecenie tworzy nową warstwę obrazu za pomocą polecenia końcowego reprezentujący obraz **myimage** wskaż repozytorium.</span><span class="sxs-lookup"><span data-stu-id="8517e-174">Each command creates a new image layer with the final command representing the image the **myimage** repository will point to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="8517e-175">`COPY` Polecenie informuje, Docker, aby skopiować określonego folderu na komputerze do folderu w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="8517e-175">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="8517e-176">W tym przykładzie **publikowania** folder jest kopiowany do folderu o nazwie **aplikacji** w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="8517e-176">In this example, the **publish** folder is copied to a folder named **app** in the container.</span></span>

<span data-ttu-id="8517e-177">Następne polecenie `ENTRYPOINT`, platformy docker, aby skonfigurować kontener, aby działał jako plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="8517e-177">The next command, `ENTRYPOINT`, tells docker to configure the container to run as an executable.</span></span> <span data-ttu-id="8517e-178">Po uruchomieniu kontenera, `ENTRYPOINT` polecenia.</span><span class="sxs-lookup"><span data-stu-id="8517e-178">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="8517e-179">Po zakończeniu tego polecenia, kontenera zostanie automatycznie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="8517e-179">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="8517e-180">W terminalu Uruchom `docker build -t myimage -f Dockerfile .` i gdy które polecenie zostanie zakończone, uruchom `docker images`.</span><span class="sxs-lookup"><span data-stu-id="8517e-180">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

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

<span data-ttu-id="8517e-181">Każde polecenie w *pliku Dockerfile* wygenerowany warstwy i utworzyć **identyfikator obrazu**.</span><span class="sxs-lookup"><span data-stu-id="8517e-181">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="8517e-182">Końcowe **identyfikator obrazu** (Twój będzie inny) jest **ddcc6646461b** i następnie utworzysz kontener na podstawie tego obrazu.</span><span class="sxs-lookup"><span data-stu-id="8517e-182">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="8517e-183">Tworzenie kontenera</span><span class="sxs-lookup"><span data-stu-id="8517e-183">Create a container</span></span>

<span data-ttu-id="8517e-184">Teraz, gdy masz obrazu, który zawiera aplikację, można utworzyć kontenera.</span><span class="sxs-lookup"><span data-stu-id="8517e-184">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="8517e-185">Kontener można utworzyć na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="8517e-185">You can create a container in two ways.</span></span> <span data-ttu-id="8517e-186">Najpierw utwórz nowy kontener, który został zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="8517e-186">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

<span data-ttu-id="8517e-187">`docker create` Polecenia z powyższych utworzy kontener na podstawie **myimage** obrazu.</span><span class="sxs-lookup"><span data-stu-id="8517e-187">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="8517e-188">Wyświetlone dane wyjściowe tego polecenia **identyfikator kontenera** (Twój będzie inny) utworzonego kontenera.</span><span class="sxs-lookup"><span data-stu-id="8517e-188">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="8517e-189">Aby wyświetlić listę *wszystkich* kontenery, używają `docker ps -a` polecenia:</span><span class="sxs-lookup"><span data-stu-id="8517e-189">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a><span data-ttu-id="8517e-190">Zarządzaj kontenera</span><span class="sxs-lookup"><span data-stu-id="8517e-190">Manage the container</span></span>

<span data-ttu-id="8517e-191">Każdy kontener jest przypisany losową nazwę, która służy do odwoływania się do wystąpienia kontenera.</span><span class="sxs-lookup"><span data-stu-id="8517e-191">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="8517e-192">Na przykład kontener, który został utworzony automatycznie wybrana nazwa **boring_matsumoto** (Twój będzie inny), tę nazwę można umożliwia uruchamianie kontenera.</span><span class="sxs-lookup"><span data-stu-id="8517e-192">For example, the container that was created automatically chose the name **boring_matsumoto** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="8517e-193">Zastąp automatyczne nazwą jeden z nich przy użyciu `docker create --name` parametru.</span><span class="sxs-lookup"><span data-stu-id="8517e-193">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="8517e-194">W poniższym przykładzie użyto `docker start` polecenie, aby uruchomić kontener, a następnie używa `docker ps` polecenie, aby wyświetlić tylko kontenerów, które są uruchomione:</span><span class="sxs-lookup"><span data-stu-id="8517e-194">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

<span data-ttu-id="8517e-195">Podobnie `docker stop` polecenie spowoduje zatrzymanie kontenera.</span><span class="sxs-lookup"><span data-stu-id="8517e-195">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="8517e-196">W poniższym przykładzie użyto `docker stop` polecenie, aby zatrzymać kontener, a następnie używa `docker ps` polecenie, aby pokazać, że kontenery nie są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="8517e-196">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running.</span></span>

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="8517e-197">Łączenie do kontenera</span><span class="sxs-lookup"><span data-stu-id="8517e-197">Connect to a container</span></span>

<span data-ttu-id="8517e-198">Po uruchomieniu kontenera możesz połączyć się do niej, aby wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="8517e-198">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="8517e-199">Użyj `docker start` i `docker attach` poleceń, aby rozpocząć, kontener i wgląd w dane ze strumienia wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="8517e-199">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="8517e-200">W tym przykładzie <kbd>klawisze CTRL + C</kbd> polecenie jest używane do odłączenia uruchomionego kontenera.</span><span class="sxs-lookup"><span data-stu-id="8517e-200">In this example, the <kbd>CTRL + C</kbd> command is used to detach from the running container.</span></span> <span data-ttu-id="8517e-201">To, że faktycznie zakończenie procesu w kontenerze, w której zostanie zatrzymane kontenera.</span><span class="sxs-lookup"><span data-stu-id="8517e-201">This may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="8517e-202">`--sig-proxy=false` Parametru gwarantuje, że <kbd>klawisze CTRL + C</kbd> uporczywie procesu w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="8517e-202">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="8517e-203">Po odłączeniu z kontenera, ponownie dołączyć, aby sprawdzić, czy jest nadal uruchomiona i zliczania.</span><span class="sxs-lookup"><span data-stu-id="8517e-203">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

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

### <a name="delete-a-container"></a><span data-ttu-id="8517e-204">Usuń kontener</span><span class="sxs-lookup"><span data-stu-id="8517e-204">Delete a container</span></span>

<span data-ttu-id="8517e-205">Na potrzeby tego artykułu nie chcesz po prostu zawiesza się wokół czynności kontenerów.</span><span class="sxs-lookup"><span data-stu-id="8517e-205">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="8517e-206">Usuń kontener, który został wcześniej utworzony.</span><span class="sxs-lookup"><span data-stu-id="8517e-206">Delete the container you previously created.</span></span> <span data-ttu-id="8517e-207">Jeśli kontener jest uruchomiona, zatrzymaj ją.</span><span class="sxs-lookup"><span data-stu-id="8517e-207">If the container is running, stop it.</span></span>

```console
> docker stop boring_matsumoto
```

<span data-ttu-id="8517e-208">Poniższy przykład wyświetla listę wszystkich kontenerów.</span><span class="sxs-lookup"><span data-stu-id="8517e-208">The following example lists all containers.</span></span> <span data-ttu-id="8517e-209">Następnie używa `docker rm` polecenia można usunąć kontenera, a następnie sprawdza po raz drugi dla dowolnego uruchomione kontenery.</span><span class="sxs-lookup"><span data-stu-id="8517e-209">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="8517e-210">Pojedynczy przebieg</span><span class="sxs-lookup"><span data-stu-id="8517e-210">Single run</span></span>

<span data-ttu-id="8517e-211">Środowisko docker zawiera `docker run` polecenia do tworzenia i uruchamiania kontenera jako pojedyncze polecenie.</span><span class="sxs-lookup"><span data-stu-id="8517e-211">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="8517e-212">To polecenie eliminuje konieczność uruchamiania `docker create` i następnie `docker start`.</span><span class="sxs-lookup"><span data-stu-id="8517e-212">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="8517e-213">Można również ustawić to polecenie, aby automatycznie usunąć kontener po zatrzymaniu kontenera.</span><span class="sxs-lookup"><span data-stu-id="8517e-213">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="8517e-214">Na przykład użyć `docker run -it --rm` zrobić dwie rzeczy, najpierw automatycznie za pomocą bieżącego terminalu połączyć z kontenera i następnie po zakończeniu kontenera, usuń go:</span><span class="sxs-lookup"><span data-stu-id="8517e-214">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="8517e-215">Za pomocą `docker run -it`, <kbd>klawisze CTRL + C</kbd> polecenie spowoduje zatrzymanie procesu, który jest uruchomiony w kontenerze, który z kolei zatrzymuje kontener.</span><span class="sxs-lookup"><span data-stu-id="8517e-215">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="8517e-216">Ponieważ `--rm` podano parametr, kontenera są automatycznie usuwane, gdy proces zostanie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="8517e-216">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="8517e-217">Sprawdź, czy nie istnieją:</span><span class="sxs-lookup"><span data-stu-id="8517e-217">Verify that it does not exist:</span></span>

```
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="8517e-218">Zmiana punktu wejścia</span><span class="sxs-lookup"><span data-stu-id="8517e-218">Change the ENTRYPOINT</span></span>

<span data-ttu-id="8517e-219">`docker run` Polecenie umożliwia również modyfikowanie `ENTRYPOINT` polecenia *pliku Dockerfile* i uruchom coś innego, ale tylko dla tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="8517e-219">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="8517e-220">Na przykład następujące polecenie do uruchomienia `bash` lub `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="8517e-220">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="8517e-221">Edytuj polecenia zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="8517e-221">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="8517e-222">Windows</span><span class="sxs-lookup"><span data-stu-id="8517e-222">Windows</span></span>
<span data-ttu-id="8517e-223">W tym przykładzie `ENTRYPOINT` jest zmieniana na `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="8517e-223">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="8517e-224"><kbd>CTRL + C,</kbd> jest wciśnięty, aby zakończyć proces i zatrzymać kontenera.</span><span class="sxs-lookup"><span data-stu-id="8517e-224"><kbd>CTRL + C</kbd> is pressed to end the process and stop the container.</span></span>

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

#### <a name="linux"></a><span data-ttu-id="8517e-225">Linux</span><span class="sxs-lookup"><span data-stu-id="8517e-225">Linux</span></span>

<span data-ttu-id="8517e-226">W tym przykładzie `ENTRYPOINT` jest zmieniana na `bash`.</span><span class="sxs-lookup"><span data-stu-id="8517e-226">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="8517e-227">`quit` Polecenie jest wykonywane, która kończy proces i przestanie kontenera.</span><span class="sxs-lookup"><span data-stu-id="8517e-227">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="8517e-228">Podstawowe polecenia</span><span class="sxs-lookup"><span data-stu-id="8517e-228">Essential commands</span></span>

<span data-ttu-id="8517e-229">Docker ma wiele różnych poleceń, które obejmują co chcesz zrobić za pomocą kontenera i obrazy.</span><span class="sxs-lookup"><span data-stu-id="8517e-229">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="8517e-230">Te polecenia Docker mają zasadnicze znaczenie dla zarządzania kontenerów:</span><span class="sxs-lookup"><span data-stu-id="8517e-230">These Docker commands are essential to managing your containers:</span></span>

* [<span data-ttu-id="8517e-231">kompilacji platformy docker</span><span class="sxs-lookup"><span data-stu-id="8517e-231">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="8517e-232">Uruchamianie platformy docker</span><span class="sxs-lookup"><span data-stu-id="8517e-232">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="8517e-233">docker ps</span><span class="sxs-lookup"><span data-stu-id="8517e-233">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="8517e-234">Zatrzymaj platformy docker</span><span class="sxs-lookup"><span data-stu-id="8517e-234">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="8517e-235">Menedżer zasobów platformy docker</span><span class="sxs-lookup"><span data-stu-id="8517e-235">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="8517e-236">rmi platformy docker</span><span class="sxs-lookup"><span data-stu-id="8517e-236">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="8517e-237">Obraz platformy docker</span><span class="sxs-lookup"><span data-stu-id="8517e-237">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="8517e-238">Oczyszczanie zasobów</span><span class="sxs-lookup"><span data-stu-id="8517e-238">Clean up resources</span></span>

<span data-ttu-id="8517e-239">W tym samouczku utworzono kontenerów i obrazy.</span><span class="sxs-lookup"><span data-stu-id="8517e-239">During this tutorial you created containers and images.</span></span> <span data-ttu-id="8517e-240">Jeśli chcesz, należy usunąć te zasoby.</span><span class="sxs-lookup"><span data-stu-id="8517e-240">If you want, delete these resources.</span></span> <span data-ttu-id="8517e-241">Użyj następujących poleceń do</span><span class="sxs-lookup"><span data-stu-id="8517e-241">Use the following commands to</span></span>

01. <span data-ttu-id="8517e-242">Listę wszystkich kontenerów</span><span class="sxs-lookup"><span data-stu-id="8517e-242">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="8517e-243">Zatrzymaj kontenerów, które są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="8517e-243">Stop containers that are running.</span></span> <span data-ttu-id="8517e-244">`CONTAINER_NAME` Reprezentuje nazwę automatycznie przypisywane do kontenera.</span><span class="sxs-lookup"><span data-stu-id="8517e-244">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="8517e-245">Usuwanie kontenera</span><span class="sxs-lookup"><span data-stu-id="8517e-245">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="8517e-246">Następnie usuń wszelkie obrazy, które nie mają już na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8517e-246">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="8517e-247">Usuń obraz utworzone przez użytkownika *pliku Dockerfile* , a następnie usuń obraz platformy .NET Core *pliku Dockerfile* zależała od.</span><span class="sxs-lookup"><span data-stu-id="8517e-247">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="8517e-248">Możesz użyć **identyfikator obrazu** lub **REPOZYTORIUM: TAG** ciąg w formacie.</span><span class="sxs-lookup"><span data-stu-id="8517e-248">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="8517e-249">Użyj `docker images` polecenie, aby wyświetlić listę obrazów, zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="8517e-249">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="8517e-250">Pliki obrazów mogą być duże.</span><span class="sxs-lookup"><span data-stu-id="8517e-250">Image files can be large.</span></span> <span data-ttu-id="8517e-251">Zazwyczaj należy usunąć kontenery tymczasowe, utworzone podczas testowania i opracowywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8517e-251">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="8517e-252">Zazwyczaj można przechowywać obrazy podstawowe za pomocą środowiska uruchomieniowego zainstalowanego, jeśli planujesz tworzenie innych obrazów oparte na tego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="8517e-252">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8517e-253">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8517e-253">Next steps</span></span>

* [<span data-ttu-id="8517e-254">Wypróbuj samouczek platformy ASP.NET Core Mikrousług.</span><span class="sxs-lookup"><span data-stu-id="8517e-254">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [<span data-ttu-id="8517e-255">Przegląd usług platformy Azure, które obsługują kontenery.</span><span class="sxs-lookup"><span data-stu-id="8517e-255">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
* [<span data-ttu-id="8517e-256">Informacje na temat poleceń pliku Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="8517e-256">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
* [<span data-ttu-id="8517e-257">Poznaj narzędzia kontenerów programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8517e-257">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
