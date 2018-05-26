---
title: Mikrousług hostowanych w Docker - C#
description: Dowiedz się, jak utworzyć asp.net podstawowe usługi, które są uruchamiane w kontenerach Docker
ms.date: 02/03/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: 7428051c1d9a29ba98ca1f28288b3c50ea36ae1a
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="d100a-103">Mikrousług hostowanych w Docker</span><span class="sxs-lookup"><span data-stu-id="d100a-103">Microservices hosted in Docker</span></span>

<span data-ttu-id="d100a-104">W tym samouczku opisano zadania niezbędne do tworzenia i wdrażania mikrousługi platformy ASP.NET Core w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="d100a-104">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="d100a-105">W trakcie tego samouczka dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="d100a-105">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="d100a-106">Sposób generowania aplikacji platformy ASP.NET Core za pomocą narzędzia Yeoman</span><span class="sxs-lookup"><span data-stu-id="d100a-106">How to generate an ASP.NET Core application using Yeoman</span></span>
* <span data-ttu-id="d100a-107">Jak utworzyć środowisko deweloperskie Docker</span><span class="sxs-lookup"><span data-stu-id="d100a-107">How to create a development Docker environment</span></span>
* <span data-ttu-id="d100a-108">Jak utworzyć obraz Docker na podstawie istniejącego obrazu.</span><span class="sxs-lookup"><span data-stu-id="d100a-108">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="d100a-109">Jak wdrożyć usługę w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="d100a-109">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="d100a-110">Na bieżąco zostanie wyświetlony również pewne funkcje języka C#:</span><span class="sxs-lookup"><span data-stu-id="d100a-110">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="d100a-111">Jak konwertować obiekty C# ładunek JSON.</span><span class="sxs-lookup"><span data-stu-id="d100a-111">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="d100a-112">Jak tworzyć obiekty niezmienne transferu danych</span><span class="sxs-lookup"><span data-stu-id="d100a-112">How to build immutable Data Transfer Objects</span></span>
* <span data-ttu-id="d100a-113">Jak do przetwarzania przychodzących żądań HTTP oraz do generowania odpowiedzi HTTP</span><span class="sxs-lookup"><span data-stu-id="d100a-113">How to process incoming HTTP Requests and generate the HTTP Response</span></span>
* <span data-ttu-id="d100a-114">Jak pracować z typów wartości null</span><span class="sxs-lookup"><span data-stu-id="d100a-114">How to work with nullable value types</span></span>

<span data-ttu-id="d100a-115">Możesz [wyświetlić lub pobrać przykładową aplikację](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) dla tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d100a-115">You can [view or download the sample app](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="d100a-116">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="d100a-116">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="why-docker"></a><span data-ttu-id="d100a-117">Dlaczego Docker?</span><span class="sxs-lookup"><span data-stu-id="d100a-117">Why Docker?</span></span>

<span data-ttu-id="d100a-118">Docker można łatwo tworzyć obrazy standardowe maszyny do hostowania usług w centrum danych lub w chmurze publicznej.</span><span class="sxs-lookup"><span data-stu-id="d100a-118">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="d100a-119">Docker umożliwia konfigurowanie obrazu i replikować ją w razie potrzeby można skalować instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-119">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="d100a-120">Cały kod w tym samouczku będzie działać w dowolnym środowisku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d100a-120">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="d100a-121">Dodatkowe zadania dotyczące instalacji Docker będzie działać dla aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d100a-121">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="d100a-122">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d100a-122">Prerequisites</span></span>
<span data-ttu-id="d100a-123">Należy skonfigurować komputer, aby uruchomić oprogramowanie .NET core.</span><span class="sxs-lookup"><span data-stu-id="d100a-123">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="d100a-124">Instrukcje instalacji można znaleźć na [.NET Core](https://www.microsoft.com/net/core) strony.</span><span class="sxs-lookup"><span data-stu-id="d100a-124">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="d100a-125">Można uruchomić tej aplikacji, w systemie Windows, Ubuntu Linux, macOS lub w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="d100a-125">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="d100a-126">Należy zainstalować w edytorze kodu dotyczącego elementów ulubionych.</span><span class="sxs-lookup"><span data-stu-id="d100a-126">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="d100a-127">Opisy poniżej użyj [Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora.</span><span class="sxs-lookup"><span data-stu-id="d100a-127">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="d100a-128">Można jednak użyć dowolnego narzędzia potrafisz.</span><span class="sxs-lookup"><span data-stu-id="d100a-128">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="d100a-129">Należy również zainstalować aparatem platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="d100a-129">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="d100a-130">Zobacz [strona instalacji Docker](http://www.docker.com/products/docker) instrukcje dla danej platformy.</span><span class="sxs-lookup"><span data-stu-id="d100a-130">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="d100a-131">Docker można zainstalować wiele dystrybucje systemu Linux, macOS lub systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d100a-131">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="d100a-132">Strona powyżej zawiera sekcje do każdego z dostępnych instalacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-132">The page referenced above contains sections to each of the available installations.</span></span>

<span data-ttu-id="d100a-133">Większość składników musi zostać zainstalowana, są wykonywane przez Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="d100a-133">Most components to be installed are done by a package manager.</span></span> <span data-ttu-id="d100a-134">Jeśli masz Menedżera pakietów w node.js `npm` zainstalowany, możesz pominąć ten krok.</span><span class="sxs-lookup"><span data-stu-id="d100a-134">If you have node.js's package manager `npm` installed you can skip this step.</span></span> <span data-ttu-id="d100a-135">W przeciwnym razie zainstaluj najnowszą NodeJs z [nodejs.org](https://nodejs.org) której zostanie zainstalowany Menedżer pakietów npm.</span><span class="sxs-lookup"><span data-stu-id="d100a-135">Otherwise install the latest NodeJs from [nodejs.org](https://nodejs.org) which will install the npm package manager.</span></span> 

<span data-ttu-id="d100a-136">Na tym etapie należy zainstalować wiele narzędzi wiersza polecenia, które obsługuje platformy ASP.NET core programowanie.</span><span class="sxs-lookup"><span data-stu-id="d100a-136">At this point you will need to install a number of command line tools that support ASP.NET core development.</span></span> <span data-ttu-id="d100a-137">Szablony wiersza polecenia, użyj narzędzia Yeoman, Grunt, Bower i Gulp.</span><span class="sxs-lookup"><span data-stu-id="d100a-137">The command line templates use Yeoman, Bower, Grunt, and Gulp.</span></span> <span data-ttu-id="d100a-138">Jeśli masz je zainstalowane, które dobrze, w przeciwnym razie wpisz następujące polecenie w ulubionych powłoki:</span><span class="sxs-lookup"><span data-stu-id="d100a-138">If you have them installed that is good, otherwise type the following into your favorite shell:</span></span>

`npm install -g yo bower grunt-cli gulp`

<span data-ttu-id="d100a-139">`-g` Opcja wskazuje, że jest on zainstalowany globalne, a te narzędzia są dostępne całym systemie.</span><span class="sxs-lookup"><span data-stu-id="d100a-139">The `-g` option indicates that it is a global install, and those tools are available system wide.</span></span> <span data-ttu-id="d100a-140">(Zakresy lokalnej instalacji pakietu do pojedynczego projektu).</span><span class="sxs-lookup"><span data-stu-id="d100a-140">(A local install scopes the package to a single project).</span></span> <span data-ttu-id="d100a-141">Po zainstalowaniu te podstawowe narzędzia, musisz zainstalować generatory szablonu platformy ASP.NET narzędzia yeoman:</span><span class="sxs-lookup"><span data-stu-id="d100a-141">Once you've installed those core tools, you need to install the yeoman ASP.NET template generators:</span></span>

`npm install -g generator-aspnet`

## <a name="create-the-application"></a><span data-ttu-id="d100a-142">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="d100a-142">Create the Application</span></span>

<span data-ttu-id="d100a-143">Teraz, po zainstalowaniu wszystkich narzędzi do tworzenia nowej aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d100a-143">Now that you've installed all the tools, create a new ASP.NET Core application.</span></span> <span data-ttu-id="d100a-144">Aby użyć generatora wiersza polecenia, należy wykonać następujące polecenie narzędzia yeoman w ulubionych powłoki:</span><span class="sxs-lookup"><span data-stu-id="d100a-144">To use the command line generator, execute the following yeoman command in your favorite shell:</span></span>

`yo aspnet`

<span data-ttu-id="d100a-145">To polecenie wyświetla monit o wybranie rodzaju aplikacji, w którym chcesz utworzyć.</span><span class="sxs-lookup"><span data-stu-id="d100a-145">This command prompts you to select what Type of application you want to create.</span></span> <span data-ttu-id="d100a-146">Dla tego mikrousługi mają aplikacji sieci web najprostszy, najbardziej lekkie możliwe, dlatego wybierz pustą aplikację sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d100a-146">For this microservice, you want the simplest, most lightweight web application possible, so select 'Empty Web Application'.</span></span> <span data-ttu-id="d100a-147">Szablon wyświetli monit o podanie nazwy.</span><span class="sxs-lookup"><span data-stu-id="d100a-147">The template will prompt you for a name.</span></span> <span data-ttu-id="d100a-148">Wybierz "WeatherMicroservice".</span><span class="sxs-lookup"><span data-stu-id="d100a-148">Select 'WeatherMicroservice'.</span></span> 

<span data-ttu-id="d100a-149">Szablon tworzy osiem plików:</span><span class="sxs-lookup"><span data-stu-id="d100a-149">The template creates eight files for you:</span></span>

* <span data-ttu-id="d100a-150">.Gitignore dostosowany do aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d100a-150">A .gitignore, customized for ASP.NET Core applications.</span></span>
* <span data-ttu-id="d100a-151">Pliku Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="d100a-151">A Startup.cs file.</span></span> <span data-ttu-id="d100a-152">Zawiera podstawę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-152">This contains the basis of the application.</span></span>
* <span data-ttu-id="d100a-153">Plik Program.cs.</span><span class="sxs-lookup"><span data-stu-id="d100a-153">A Program.cs file.</span></span> <span data-ttu-id="d100a-154">Zawiera punkt wejścia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-154">This contains the entry point of the application.</span></span>
* <span data-ttu-id="d100a-155">Plik WeatherMicroservice.csproj.</span><span class="sxs-lookup"><span data-stu-id="d100a-155">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="d100a-156">To jest plik kompilacji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-156">This is the build file for the application.</span></span>
* <span data-ttu-id="d100a-157">Plik Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="d100a-157">A Dockerfile.</span></span> <span data-ttu-id="d100a-158">Ten skrypt tworzy obraz Docker dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-158">This script creates a Docker image for the application.</span></span>
* <span data-ttu-id="d100a-159">A README.md.</span><span class="sxs-lookup"><span data-stu-id="d100a-159">A README.md.</span></span> <span data-ttu-id="d100a-160">Zawiera linki do innych zasobów platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d100a-160">This contains links to other ASP.NET Core resources.</span></span>
* <span data-ttu-id="d100a-161">Plik web.config.</span><span class="sxs-lookup"><span data-stu-id="d100a-161">A web.config file.</span></span> <span data-ttu-id="d100a-162">Zawiera podstawowe informacje o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d100a-162">This contains basic configuration information.</span></span>
* <span data-ttu-id="d100a-163">Plik runtimeconfig.template.json.</span><span class="sxs-lookup"><span data-stu-id="d100a-163">A runtimeconfig.template.json file.</span></span> <span data-ttu-id="d100a-164">Zawiera ustawienia debugowania używane przez IDEs.</span><span class="sxs-lookup"><span data-stu-id="d100a-164">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="d100a-165">Teraz możesz uruchomić aplikacji szablonu wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="d100a-165">Now you can run the template generated application.</span></span> <span data-ttu-id="d100a-166">Który ma odbywa się za pomocą szereg narzędzi wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d100a-166">That's done using a series of tools from the command line.</span></span> <span data-ttu-id="d100a-167">`dotnet` Polecenia są uruchamiane narzędzia niezbędne do tworzenia aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="d100a-167">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="d100a-168">Inne polecenie wykonuje każdego zlecenia</span><span class="sxs-lookup"><span data-stu-id="d100a-168">Each verb executes a different command</span></span>

<span data-ttu-id="d100a-169">Pierwszym krokiem jest, aby przywrócić wszystkie zależności:</span><span class="sxs-lookup"><span data-stu-id="d100a-169">The first step is to restore all the dependencies:</span></span>

```console
dotnet restore
```

<span data-ttu-id="d100a-170">Przywracania DotNet stosuje Menedżera pakietów NuGet w celu zainstalowania wymaganych pakietów do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-170">Dotnet restore uses the NuGet package manager to install all the necessary packages into the application directory.</span></span> <span data-ttu-id="d100a-171">Generuje plik project.json.lock.</span><span class="sxs-lookup"><span data-stu-id="d100a-171">It also generates a project.json.lock file.</span></span> <span data-ttu-id="d100a-172">Ten plik zawiera informacje dotyczące każdego pakietu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="d100a-172">This file contains information about each package that is referenced.</span></span> <span data-ttu-id="d100a-173">Po przywróceniu wszystkie zależności, należy skompilować aplikację:</span><span class="sxs-lookup"><span data-stu-id="d100a-173">After restoring all the dependencies, you build the application:</span></span>

```console
dotnet build
```
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="d100a-174">I po utworzeniu aplikacji, należy uruchomić z wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="d100a-174">And once you build the application, you run it from the command line:</span></span>

```console
dotnet run
```

<span data-ttu-id="d100a-175">Domyślna konfiguracja nasłuchuje `http://localhost:5000`.</span><span class="sxs-lookup"><span data-stu-id="d100a-175">The default configuration listens to `http://localhost:5000`.</span></span> <span data-ttu-id="d100a-176">Można otworzyć przeglądarkę i przejdź do strony i "Witaj świecie!" w temacie</span><span class="sxs-lookup"><span data-stu-id="d100a-176">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="d100a-177">Komunikat.</span><span class="sxs-lookup"><span data-stu-id="d100a-177">message.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="d100a-178">Anatomia aplikacji platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d100a-178">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="d100a-179">Teraz gdy masz utworzoną aplikację, Przyjrzyjmy się implementowania tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d100a-179">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="d100a-180">Istnieją dwa wygenerowanych plików, które są w tym momencie zastosowanie szczególnie: pliku project.json i pliku Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="d100a-180">There are two of the generated files that are particularly interesting at this point: project.json and Startup.cs.</span></span> 

<span data-ttu-id="d100a-181">Project.JSON zawiera informacje o projekcie.</span><span class="sxs-lookup"><span data-stu-id="d100a-181">Project.json contains information about the project.</span></span> <span data-ttu-id="d100a-182">Dwa węzły, które często będzie współpracować są 'zależności' i 'struktury'.</span><span class="sxs-lookup"><span data-stu-id="d100a-182">The two nodes you'll often work with are 'dependencies' and 'frameworks'.</span></span> <span data-ttu-id="d100a-183">Węzeł zależności zawiera listę wszystkich pakietów, które są wymagane dla tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-183">The dependencies node lists all the packages that are needed for this application.</span></span>
<span data-ttu-id="d100a-184">W tej chwili jest węzłem małych wymagające tylko pakiety, które uruchomić serwera sieci web.</span><span class="sxs-lookup"><span data-stu-id="d100a-184">At the moment, this is a small node, needing only the packages that run the web server.</span></span>

<span data-ttu-id="d100a-185">Węzeł 'struktury' Określa wersje i konfiguracje programu .NET framework, która może uruchomić tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="d100a-185">The 'frameworks' node specifies the versions and configurations of the .NET framework that will run this application.</span></span>

<span data-ttu-id="d100a-186">Aplikacja jest zaimplementowana w pliku Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="d100a-186">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="d100a-187">Ten plik zawiera klasę uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="d100a-187">This file contains the startup class.</span></span>

<span data-ttu-id="d100a-188">Te dwie metody są wywoływane przez infrastrukturę platformy ASP.NET Core, aby skonfigurować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="d100a-188">The two methods are called by the ASP.NET Core infrastructure to configure and run the application.</span></span> <span data-ttu-id="d100a-189">`ConfigureServices` Metoda opisuje usług, które są niezbędne dla tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-189">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="d100a-190">Tworzysz mikrousługi gotowa, więc nie trzeba skonfigurować wszelkie zależności.</span><span class="sxs-lookup"><span data-stu-id="d100a-190">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="d100a-191">`Configure` Metody konfiguruje obsługi przychodzących żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="d100a-191">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="d100a-192">Szablon generuje prosty program obsługi, który ma odpowiadać na każde żądanie od tekstu "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="d100a-192">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="d100a-193">Tworzenie mikrousługi</span><span class="sxs-lookup"><span data-stu-id="d100a-193">Build a microservice</span></span>

<span data-ttu-id="d100a-194">Możesz zacząć kompilacji usługi będzie dostarczać pogody z dowolnego miejsca na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="d100a-194">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="d100a-195">W aplikacji produkcyjnej możesz wywołać niektóre usługi do pobierania danych pogody.</span><span class="sxs-lookup"><span data-stu-id="d100a-195">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="d100a-196">Dla naszej próbki możemy zostanie wygenerowany losowe prognozie pogody.</span><span class="sxs-lookup"><span data-stu-id="d100a-196">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="d100a-197">Istnieje wiele zadań, które należy wykonać w celu wdrożenia naszej usługi pogody losowe:</span><span class="sxs-lookup"><span data-stu-id="d100a-197">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="d100a-198">Analizuje przychodzące żądanie odczytu współrzędne geograficzne.</span><span class="sxs-lookup"><span data-stu-id="d100a-198">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="d100a-199">Generowanie niektórych losowe dane prognozy.</span><span class="sxs-lookup"><span data-stu-id="d100a-199">Generate some random forecast data.</span></span>
* <span data-ttu-id="d100a-200">Konwertowanie losowe dane prognozy z C# obiektów JSON pakietów.</span><span class="sxs-lookup"><span data-stu-id="d100a-200">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="d100a-201">Ustaw nagłówek odpowiedzi, aby wskazać, że Twoje wyśle usługi z powrotem JSON.</span><span class="sxs-lookup"><span data-stu-id="d100a-201">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="d100a-202">Zapisu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="d100a-202">Write the response.</span></span>

<span data-ttu-id="d100a-203">Kolejnych sekcjach prowadzą użytkownika przez każdy z tych kroków.</span><span class="sxs-lookup"><span data-stu-id="d100a-203">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="d100a-204">Podczas analizowania ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="d100a-204">Parsing the Query String.</span></span>

<span data-ttu-id="d100a-205">Zostaną analizując ciąg zapytania.</span><span class="sxs-lookup"><span data-stu-id="d100a-205">You'll begin by parsing the query string.</span></span> <span data-ttu-id="d100a-206">Usługa będzie akceptować "lat" i "long" argumentów dla ciągu zapytania w tym formularzu:</span><span class="sxs-lookup"><span data-stu-id="d100a-206">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

`http://localhost:5000/?lat=-35.55&long=-12.35`  

<span data-ttu-id="d100a-207">Wszystkie zmiany, które należy podjąć są zdefiniowane jako argument wyrażenia lambda `app.Run` w klasie uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="d100a-207">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="d100a-208">Argument na wyrażeniu lambda jest `HttpContext` dla żądania.</span><span class="sxs-lookup"><span data-stu-id="d100a-208">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="d100a-209">Jedną z właściwości jest `Request` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d100a-209">One of its properties is the `Request` object.</span></span> <span data-ttu-id="d100a-210">`Request` Obiekt ma `Query` właściwość, która zawiera słownik wszystkich wartości na ciąg zapytania dla żądania.</span><span class="sxs-lookup"><span data-stu-id="d100a-210">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="d100a-211">Dodanie pierwszy jest to znalezienie wartości szerokości i długości geograficznej:</span><span class="sxs-lookup"><span data-stu-id="d100a-211">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="d100a-212">Słownik wartości zapytania są `StringValue` typu.</span><span class="sxs-lookup"><span data-stu-id="d100a-212">The Query dictionary values are `StringValue` type.</span></span> <span data-ttu-id="d100a-213">Tego typu może zawierać kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="d100a-213">That type can contain a collection of strings.</span></span> <span data-ttu-id="d100a-214">Usługi pogodzie każda wartość jest pojedynczy ciąg.</span><span class="sxs-lookup"><span data-stu-id="d100a-214">For your weather service, each value is a single string.</span></span> <span data-ttu-id="d100a-215">Dlatego jest wywołanie `FirstOrDefault()` w powyższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d100a-215">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="d100a-216">Następnie należy konwertować ciągi na symulacyjnych.</span><span class="sxs-lookup"><span data-stu-id="d100a-216">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="d100a-217">Metoda służy do przekonwertowania ciągu na wartość typu double jest `double.TryParse()`:</span><span class="sxs-lookup"><span data-stu-id="d100a-217">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="d100a-218">Ta metoda wykorzystuje C# limit parametrów, aby wskazać, czy ciąg wejściowy można przekonwertować na wartość typu double.</span><span class="sxs-lookup"><span data-stu-id="d100a-218">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="d100a-219">Jeśli ciąg reprezentują reprezentację prawidłową wartość o podwójnej precyzji, metoda zwraca wartość true i `result` argument zawiera wartość.</span><span class="sxs-lookup"><span data-stu-id="d100a-219">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="d100a-220">Jeśli ciąg nie reprezentuje prawidłową wartość o podwójnej precyzji, metoda zwraca wartość false.</span><span class="sxs-lookup"><span data-stu-id="d100a-220">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="d100a-221">Istnieje możliwość dostosowania tego interfejsu API przy użyciu *— metoda rozszerzenia* zwracającą *wartości null typu double*.</span><span class="sxs-lookup"><span data-stu-id="d100a-221">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="d100a-222">A *typ dopuszczający wartość null wartości* jest typem, który reprezentuje pewien typ wartości i również przechowywane braku lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="d100a-222">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="d100a-223">Typ dopuszczający wartość null jest reprezentowana przez dodanie `?` znak do deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="d100a-223">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="d100a-224">Metody rozszerzenia są metody, które są zdefiniowane jako metody statyczne, ale przez dodanie `this` modyfikator w pierwszym parametrze można wywołać tak, jakby są oni członkami tej klasy.</span><span class="sxs-lookup"><span data-stu-id="d100a-224">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="d100a-225">Metody rozszerzenia można zdefiniować tylko w klasach statycznych.</span><span class="sxs-lookup"><span data-stu-id="d100a-225">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="d100a-226">Poniżej przedstawiono definicję klasy zawierające metody rozszerzenia dla analizy:</span><span class="sxs-lookup"><span data-stu-id="d100a-226">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="d100a-227">`default(double?)` Wyrażenie zwraca wartość domyślną `double?` typu.</span><span class="sxs-lookup"><span data-stu-id="d100a-227">The `default(double?)` expression returns the default value for the `double?` type.</span></span> <span data-ttu-id="d100a-228">Czy wartość domyślna to wartość null (lub nie).</span><span class="sxs-lookup"><span data-stu-id="d100a-228">That default value is the null (or missing) value.</span></span>

<span data-ttu-id="d100a-229">Ta metoda rozszerzenia służy do konwertowania argumenty ciągu zapytania do typu double:</span><span class="sxs-lookup"><span data-stu-id="d100a-229">You can use this extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="d100a-230">Aby łatwo testowania analizy kodu, należy zaktualizować odpowiedzi, aby uwzględnić wartości argumentów:</span><span class="sxs-lookup"><span data-stu-id="d100a-230">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="d100a-231">W tym momencie można uruchomić aplikacji sieci web i czy działa analizy kodu.</span><span class="sxs-lookup"><span data-stu-id="d100a-231">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="d100a-232">Dodawanie wartości do żądania sieci web w przeglądarce i powinna zostać wyświetlona zaktualizowanych wyników.</span><span class="sxs-lookup"><span data-stu-id="d100a-232">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="d100a-233">Losowe prognozie pogody kompilacji</span><span class="sxs-lookup"><span data-stu-id="d100a-233">Build a random weather forecast</span></span>

<span data-ttu-id="d100a-234">Następnym zadaniem jest losowe prognozie pogody kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-234">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="d100a-235">Zacznijmy od kontener danych, który zawiera wartości, które mają dla prognozie pogody:</span><span class="sxs-lookup"><span data-stu-id="d100a-235">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions = new string[]
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HiTemperature { get; }
    public int LoTemperature { get; }
    public int AverageWindSpeed { get; }
    public string Conditions { get; }
}
```

<span data-ttu-id="d100a-236">Następnie utwórz konstruktora, który losowo ustawia te wartości.</span><span class="sxs-lookup"><span data-stu-id="d100a-236">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="d100a-237">Ten konstruktor korzysta wartości szerokości i długości geograficznej jako zalążek generatora liczb losowych.</span><span class="sxs-lookup"><span data-stu-id="d100a-237">This constructor uses the values for the latitude and longitude to seed the Random number generator.</span></span> <span data-ttu-id="d100a-238">Oznacza to, że prognozy dla tej samej lokalizacji jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="d100a-238">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="d100a-239">Jeśli zmienisz argumenty współrzędne geograficzne, otrzymasz różnych prognozy (ponieważ rozpoczyna różnych inicjatora.)</span><span class="sxs-lookup"><span data-stu-id="d100a-239">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed.)</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="d100a-240">Teraz można wygenerować prognozy 5 dni w metodę odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="d100a-240">You can now generate the 5-day forecast in your response method:</span></span>

[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Generate a random weather report")]

### <a name="build-the-json-response"></a><span data-ttu-id="d100a-241">Tworzenie odpowiedź w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="d100a-241">Build the JSON response.</span></span>

<span data-ttu-id="d100a-242">Zadanie kodu końcowego na serwerze jest konwertowanie tablicy WeatherReport pakietów JSON, a następnie Wyślij to do klienta.</span><span class="sxs-lookup"><span data-stu-id="d100a-242">The final code task on the server is to convert the WeatherReport array into a JSON packet, and send that back to the client.</span></span> <span data-ttu-id="d100a-243">Zacznijmy od utworzenia pakietu JSON.</span><span class="sxs-lookup"><span data-stu-id="d100a-243">Let's start by creating the JSON packet.</span></span> <span data-ttu-id="d100a-244">Serializator JSON NewtonSoft zostanie dodana do listy zależności.</span><span class="sxs-lookup"><span data-stu-id="d100a-244">You'll add the NewtonSoft JSON Serializer to the list of dependencies.</span></span> <span data-ttu-id="d100a-245">Możesz zrobić tego za pomocą `dotnet` interfejsu wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="d100a-245">You can do that using the `dotnet` CLI:</span></span>

```
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="d100a-246">Następnie należy użyć `JsonConvert` klasa umożliwiająca zapisanie obiektu na ciąg:</span><span class="sxs-lookup"><span data-stu-id="d100a-246">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="d100a-247">Powyższy kod konwertuje obiekt prognozy (lista `WeatherForecast` obiekty) w pakiecie JSON.</span><span class="sxs-lookup"><span data-stu-id="d100a-247">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON packet.</span></span> <span data-ttu-id="d100a-248">Po skonstruowaniu pakiet odpowiedzi, Ustaw typ zawartości `application/json`i zapisać ciąg.</span><span class="sxs-lookup"><span data-stu-id="d100a-248">After you've constructed the response packet, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="d100a-249">Teraz aplikacji działa i zwraca losowe prognoz.</span><span class="sxs-lookup"><span data-stu-id="d100a-249">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="d100a-250">Utwórz obraz Docker</span><span class="sxs-lookup"><span data-stu-id="d100a-250">Build a Docker image</span></span>

<span data-ttu-id="d100a-251">Nasze ostatnim zadaniem jest aby uruchomić aplikację w Docker.</span><span class="sxs-lookup"><span data-stu-id="d100a-251">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="d100a-252">Utworzymy kontener Docker uruchomionym obrazem Docker reprezentujący naszej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-252">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="d100a-253">A ***Docker obrazu*** jest plik definiujący środowisko do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-253">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="d100a-254">A ***kontenera Docker*** reprezentuje działającego wystąpienia obrazu Docker.</span><span class="sxs-lookup"><span data-stu-id="d100a-254">A ***Docker Container*** represents a running instance of a Docker image.</span></span>

<span data-ttu-id="d100a-255">Analogicznie, można traktować *obrazu Docker* jako *klasy*i *kontenera Docker* jako obiekt lub wystąpienia tej klasy.</span><span class="sxs-lookup"><span data-stu-id="d100a-255">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="d100a-256">Plik Dockerfile utworzonej przez szablon ASP.NET będzie służyć do naszej celów.</span><span class="sxs-lookup"><span data-stu-id="d100a-256">The Dockerfile created by the ASP.NET template will serve for our purposes.</span></span> <span data-ttu-id="d100a-257">Przejdźmy za pośrednictwem jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="d100a-257">Let's go over its contents.</span></span>

<span data-ttu-id="d100a-258">Pierwszy wiersz określa obrazu źródłowego:</span><span class="sxs-lookup"><span data-stu-id="d100a-258">The first line specifies the source image:</span></span>

```
FROM microsoft/dotnet:1.1-sdk-msbuild
```

<span data-ttu-id="d100a-259">Docker pozwala na skonfigurowanie obraz maszyny, na podstawie szablonu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d100a-259">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="d100a-260">To oznacza, nie trzeba podać parametry maszyny, podczas uruchamiania, wystarczy podać wszelkie zmiany.</span><span class="sxs-lookup"><span data-stu-id="d100a-260">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="d100a-261">Zmiany w tym miejscu należy dołączyć naszej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-261">The changes here will be to include our application.</span></span>

<span data-ttu-id="d100a-262">W tym przykładzie pierwsze użyjemy `1.1-sdk-msbuild` wersja obrazu dotnet.</span><span class="sxs-lookup"><span data-stu-id="d100a-262">In this first sample, we'll use the `1.1-sdk-msbuild` version of the dotnet image.</span></span> <span data-ttu-id="d100a-263">Jest to najprostszy sposób tworzenia działającego środowiska Docker.</span><span class="sxs-lookup"><span data-stu-id="d100a-263">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="d100a-264">Ten obraz to podstawowego środowiska wykonawczego platformy dotnet i dotnet zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="d100a-264">This image include the dotnet core runtime, and the dotnet SDK.</span></span> <span data-ttu-id="d100a-265">Który ułatwia rozpoczęcie pracy i kompilacji, ale utworzyć większy obraz.</span><span class="sxs-lookup"><span data-stu-id="d100a-265">That makes it easier to get started and build, but does create a larger image.</span></span>

<span data-ttu-id="d100a-266">Następne pięć wierszy Instalatora i skompilować aplikację:</span><span class="sxs-lookup"><span data-stu-id="d100a-266">The next five lines setup and build your application:</span></span>

```
WORKDIR /app

# copy csproj and restore as distinct layers

COPY WeatherMicroService.csproj .
RUN dotnet restore 

# copy and build everything else

COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out
```

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="d100a-267">Spowoduje to skopiuj plik projektu z bieżącego katalogu do maszyny Wirtualnej platformy Docker i przywrócić wszystkie pakiety.</span><span class="sxs-lookup"><span data-stu-id="d100a-267">This will copy the project file from the  current directory to the Docker VM, and restore all the packages.</span></span> <span data-ttu-id="d100a-268">Użycie dotnet interfejsu wiersza polecenia oznacza, że obraz Docker musi zawierać .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d100a-268">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="d100a-269">Po wykonaniu tej pozostałej części aplikacji są kopiowane i dotnet publikowanie polecenie kompilacji i pakiety aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-269">After that, the rest of your application gets copied, and the dotnet publish command builds and packages your application.</span></span>

<span data-ttu-id="d100a-270">Aplikacja jest uruchamiana w ostatnim wierszu pliku:</span><span class="sxs-lookup"><span data-stu-id="d100a-270">The final line of the file runs the application:</span></span>

```
ENTRYPOINT ["dotnet", "out/WeatherMicroService.dll", "--server.urls", "http://0.0.0.0:5000"]
```

<span data-ttu-id="d100a-271">Odwołuje się tego skonfigurowanego portu `--server.urls` argument `dotnet` w ostatnim wierszu plik Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="d100a-271">This configured port is referenced in the `--server.urls` argument to `dotnet` on the last  line of the Dockerfile.</span></span> <span data-ttu-id="d100a-272">`ENTRYPOINT` Polecenie informuje Docker, jakie polecenia i opcje wiersza polecenia Uruchom usługę.</span><span class="sxs-lookup"><span data-stu-id="d100a-272">The `ENTRYPOINT` command informs Docker what command and command-line options start the service.</span></span> 

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="d100a-273">Tworzenie i uruchamianie obrazu w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="d100a-273">Building and running the image in a container.</span></span>

<span data-ttu-id="d100a-274">Umożliwia tworzenie obrazu i uruchom usługę w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="d100a-274">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="d100a-275">Nie ma wszystkich plików z katalogu lokalnego kopiowane do obrazu.</span><span class="sxs-lookup"><span data-stu-id="d100a-275">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="d100a-276">Zamiast tego zostanie utworzenie aplikacji w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="d100a-276">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="d100a-277">Utworzysz `.dockerignore` plik, aby określić katalogi, które nie są kopiowane do obrazu.</span><span class="sxs-lookup"><span data-stu-id="d100a-277">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="d100a-278">Nie ma żadnego zasoby kompilacji skopiowane.</span><span class="sxs-lookup"><span data-stu-id="d100a-278">You don't want any of the build assets copied.</span></span> <span data-ttu-id="d100a-279">Określ kompilację i publikowanie katalogów w `.dockerignore` pliku:</span><span class="sxs-lookup"><span data-stu-id="d100a-279">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="d100a-280">Tworzenie, przy użyciu obrazu `docker build` polecenia.</span><span class="sxs-lookup"><span data-stu-id="d100a-280">You build the image using the `docker build` command.</span></span> <span data-ttu-id="d100a-281">Uruchom następujące polecenie z katalogu z kodem.</span><span class="sxs-lookup"><span data-stu-id="d100a-281">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="d100a-282">To polecenie tworzy obraz kontenera, zgodnie z informacjami w Twojej plik Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="d100a-282">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="d100a-283">`-t` Argument zawiera tag lub nazwę dla tego obrazu kontenera.</span><span class="sxs-lookup"><span data-stu-id="d100a-283">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="d100a-284">W powyższym wierszu polecenia jest znacznik kontenera Docker `weather-microservice`.</span><span class="sxs-lookup"><span data-stu-id="d100a-284">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="d100a-285">Po zakończeniu wykonywania tego polecenia należy kontener gotowy do uruchomienia nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="d100a-285">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="d100a-286">Uruchom następujące polecenie, aby uruchomić kontenera i uruchomić usługi:</span><span class="sxs-lookup"><span data-stu-id="d100a-286">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:5000 --name hello-docker weather-microservice
```

<span data-ttu-id="d100a-287">`-d` Opcja oznacza, że Uruchom kontenera odłączona od bieżącego terminala.</span><span class="sxs-lookup"><span data-stu-id="d100a-287">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="d100a-288">Oznacza to, że dane wyjściowe polecenia nie będą widzieć w terminalu.</span><span class="sxs-lookup"><span data-stu-id="d100a-288">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="d100a-289">`-p` Opcja wskazuje mapowanie portów między usługą i hosta.</span><span class="sxs-lookup"><span data-stu-id="d100a-289">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="d100a-290">W tym miejscu mówi, że wszystkie żądania przychodzącego na porcie 80 powinny zostać przekazane port 5000 w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="d100a-290">Here it says that any incoming request on port 80 should be forwarded to port 5000 on the container.</span></span> <span data-ttu-id="d100a-291">Za pomocą 5000 odpowiada port, którego nasłuchuje usługi z określonego w powyższym plik Dockerfile argumenty wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d100a-291">Using 5000 matches the port your service is listening on from the command line arguments specified in the Dockerfile above.</span></span> <span data-ttu-id="d100a-292">`--name` Argument nazwy użytkownika uruchomionych kontenera.</span><span class="sxs-lookup"><span data-stu-id="d100a-292">The `--name` argument names your running container.</span></span> <span data-ttu-id="d100a-293">Jest to nazwa wygodny, używanej do pracy z tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="d100a-293">It's a convenient name you can use to work with that container.</span></span> 

<span data-ttu-id="d100a-294">Możesz sprawdzić, czy obraz jest uruchomiony przez sprawdzenie, polecenie:</span><span class="sxs-lookup"><span data-stu-id="d100a-294">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="d100a-295">Jeśli działa z kontenera, zobaczysz wiersza, który jest wyświetlany w uruchomionych procesów.</span><span class="sxs-lookup"><span data-stu-id="d100a-295">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="d100a-296">(Może być tylko jeden).</span><span class="sxs-lookup"><span data-stu-id="d100a-296">(It may be the only one).</span></span>

<span data-ttu-id="d100a-297">Usługi można sprawdzić, otwierając przeglądarkę i przechodząc do localhost i określający współrzędne geograficzne:</span><span class="sxs-lookup"><span data-stu-id="d100a-297">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="d100a-298">Dołączanie do uruchomionego kontenera</span><span class="sxs-lookup"><span data-stu-id="d100a-298">Attaching to a running container</span></span>

<span data-ttu-id="d100a-299">Podczas korzystania z usługi w oknie polecenia mogliby zobaczyć informacje diagnostyczne drukowane dla każdego żądania.</span><span class="sxs-lookup"><span data-stu-id="d100a-299">When you ran your sevice in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="d100a-300">Gdy z kontenera działa w trybie odłączony nie widzisz tych informacji.</span><span class="sxs-lookup"><span data-stu-id="d100a-300">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="d100a-301">Polecenie Dołącz Docker umożliwia dołączanie do uruchomionego kontenera tak, aby informacje dziennika.</span><span class="sxs-lookup"><span data-stu-id="d100a-301">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="d100a-302">W oknie polecenie Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d100a-302">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="d100a-303">`--sig-proxy=false` Argumentu oznacza, że `Ctrl-C` poleceń nie wysyłana do procesu kontenera, ale raczej zatrzymać `docker attach` polecenia.</span><span class="sxs-lookup"><span data-stu-id="d100a-303">The `--sig-proxy=false` argument means that `Ctrl-C` commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="d100a-304">Ostatni argument jest nazwa kontenera w `docker run` polecenia.</span><span class="sxs-lookup"><span data-stu-id="d100a-304">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="d100a-305">Umożliwia także Docker przypisany identyfikator kontenera do odwoływania się do dowolnego kontenera.</span><span class="sxs-lookup"><span data-stu-id="d100a-305">You can also use the Docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="d100a-306">Jeśli nie określono nazwę Twojej kontenera w `docker run` musisz użyć identyfikatora kontenera.</span><span class="sxs-lookup"><span data-stu-id="d100a-306">If you didn't specify a name for your container in `docker run` you must use the container id.</span></span>

<span data-ttu-id="d100a-307">Otwórz przeglądarkę i przejdź do usługi.</span><span class="sxs-lookup"><span data-stu-id="d100a-307">Open a browser and navigate to your service.</span></span> <span data-ttu-id="d100a-308">Zostanie wyświetlone komunikaty diagnostyczne w systemie windows polecenie z dołączonego uruchomionych kontenera.</span><span class="sxs-lookup"><span data-stu-id="d100a-308">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="d100a-309">Naciśnij klawisz `Ctrl-C` można zatrzymać procesu dołączania.</span><span class="sxs-lookup"><span data-stu-id="d100a-309">Press `Ctrl-C` to stop the attach process.</span></span>

<span data-ttu-id="d100a-310">Po zakończeniu pracy z Twojej kontenera, można zatrzymać go:</span><span class="sxs-lookup"><span data-stu-id="d100a-310">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="d100a-311">Kontener i obrazu jest wciąż dostępna na potrzeby ponownego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="d100a-311">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="d100a-312">Jeśli chcesz usunąć kontener z komputera, możesz użyć tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="d100a-312">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="d100a-313">Jeśli chcesz usunąć nieużywane obrazów z komputera, możesz użyć tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="d100a-313">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="d100a-314">Wniosek</span><span class="sxs-lookup"><span data-stu-id="d100a-314">Conclusion</span></span> 

<span data-ttu-id="d100a-315">W tym samouczku wbudowane mikrousługi platformy ASP.NET Core i dodać kilka prostych funkcji.</span><span class="sxs-lookup"><span data-stu-id="d100a-315">In this tutorial, you built an ASP.NET Core microservice, and added a few simple features.</span></span>

<span data-ttu-id="d100a-316">Wbudowane Docker kontenera obrazu dla tej usługi i uruchomienia tego kontenera na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d100a-316">You built a Docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="d100a-317">Dołączone do usługi okno terminalu i był wyświetlany komunikaty diagnostyczne z usługi.</span><span class="sxs-lookup"><span data-stu-id="d100a-317">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="d100a-318">Przeglądania widać kilka funkcji języka C# w akcji.</span><span class="sxs-lookup"><span data-stu-id="d100a-318">Along the way, you saw several features of the C# language in action.</span></span>
