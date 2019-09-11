---
title: Tworzenie klienta REST przy użyciu platformy .NET Core
description: W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 001a9cbaae1cdb57b6451bc42ce326864f8dcf7b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850976"
---
# <a name="rest-client"></a><span data-ttu-id="ba8d3-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="ba8d3-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="ba8d3-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="ba8d3-104">Introduction</span></span>

<span data-ttu-id="ba8d3-105">W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="ba8d3-106">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-106">You’ll learn:</span></span>

* <span data-ttu-id="ba8d3-107">Podstawowe informacje o interfejsie wiersza polecenia (CLI) platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
* <span data-ttu-id="ba8d3-108">Omówienie funkcji C# języka.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-108">An overview of C# Language features.</span></span>
* <span data-ttu-id="ba8d3-109">Zarządzanie zależnościami przy użyciu narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="ba8d3-109">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="ba8d3-110">HTTP Communications</span><span class="sxs-lookup"><span data-stu-id="ba8d3-110">HTTP Communications</span></span>
* <span data-ttu-id="ba8d3-111">Przetwarzanie informacji JSON</span><span class="sxs-lookup"><span data-stu-id="ba8d3-111">Processing JSON information</span></span>
* <span data-ttu-id="ba8d3-112">Zarządzanie konfiguracją przy użyciu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-112">Managing configuration with Attributes.</span></span>

<span data-ttu-id="ba8d3-113">Utworzysz aplikację, która wystawia żądania HTTP do usługi REST w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="ba8d3-114">Informacje są odczytywane w formacie JSON i konwertowane tego pakietu JSON na C# obiekty.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="ba8d3-115">Na koniec zobaczysz, jak korzystać z C# obiektów.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="ba8d3-116">Ten samouczek zawiera wiele funkcji.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="ba8d3-117">Kompilujmy je po jednej.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-117">Let’s build them one by one.</span></span>

<span data-ttu-id="ba8d3-118">Jeśli wolisz postępować wraz z [ostatnim przykładem](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) dla tego tematu, możesz go pobrać.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="ba8d3-119">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ba8d3-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ba8d3-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ba8d3-120">Prerequisites</span></span>

<span data-ttu-id="ba8d3-121">Musisz skonfigurować maszynę do uruchamiania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="ba8d3-122">Instrukcje instalacji można znaleźć na stronie [pliki do pobrania w programie .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="ba8d3-122">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="ba8d3-123">Tę aplikację można uruchomić w systemie Windows, Linux, macOS lub w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="ba8d3-124">Musisz zainstalować swój ulubiony Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="ba8d3-125">Poniższe opisy wykorzystują [Visual Studio Code](https://code.visualstudio.com/), czyli edytor Międzyplatformowy.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="ba8d3-126">Można jednak korzystać z dowolnych narzędzi, z którymi masz doświadczenie.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="ba8d3-127">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="ba8d3-127">Create the Application</span></span>

<span data-ttu-id="ba8d3-128">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-128">The first step is to create a new application.</span></span> <span data-ttu-id="ba8d3-129">Otwórz wiersz polecenia i Utwórz nowy katalog dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="ba8d3-130">Upewnij się, że bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-130">Make that the current directory.</span></span> <span data-ttu-id="ba8d3-131">Wpisz polecenie `dotnet new console` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="ba8d3-132">Spowoduje to utworzenie plików początkowych dla podstawowej aplikacji "Hello world".</span><span class="sxs-lookup"><span data-stu-id="ba8d3-132">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="ba8d3-133">Ponieważ jest to nowy projekt, nie są stosowane żadne zależności, więc pierwsze uruchomienie spowoduje pobranie platformy .NET Core, zainstalowanie certyfikatu deweloperskiego i uruchomienie Menedżera pakietów NuGet w celu przywrócenia brakujących zależności.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-133">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework, install a development certificate and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="ba8d3-134">Przed rozpoczęciem wprowadzania modyfikacji wpisz `dotnet run` ([Zobacz Uwaga](#dotnet-restore-note)) w wierszu polecenia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-134">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="ba8d3-135">`dotnet run`wykonuje `dotnet restore` automatycznie, jeśli w środowisku nie ma zależności.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-135">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="ba8d3-136">Wykonuje `dotnet build` również, jeśli aplikacja musi zostać odbudowana.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-136">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="ba8d3-137">Po wstępnej konfiguracji wystarczy uruchomić `dotnet restore` program lub `dotnet build` tylko wtedy, gdy jest to zrozumiałe dla projektu.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-137">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="ba8d3-138">Dodawanie nowych zależności</span><span class="sxs-lookup"><span data-stu-id="ba8d3-138">Adding New Dependencies</span></span>

<span data-ttu-id="ba8d3-139">Jednym z kluczowych celów projektowych dla platformy .NET Core jest Minimalizacja rozmiaru instalacji programu .NET.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-139">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="ba8d3-140">Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych funkcji, należy dodać te zależności do pliku C# projektu (\*. csproj).</span><span class="sxs-lookup"><span data-stu-id="ba8d3-140">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="ba8d3-141">Na potrzeby tego przykładu należy dodać `System.Runtime.Serialization.Json` pakiet, aby aplikacja mogła przetwarzać odpowiedzi JSON.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-141">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="ba8d3-142">Otwórz plik `csproj` projektu.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-142">Open your `csproj` project file.</span></span> <span data-ttu-id="ba8d3-143">Pierwszy wiersz pliku powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-143">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="ba8d3-144">Dodaj następujące elementy bezpośrednio po tym wierszu:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-144">Add the following immediately after this line:</span></span>

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup>
```

<span data-ttu-id="ba8d3-145">Większość edytorów kodu zapewnia uzupełnianie dla różnych wersji tych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-145">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="ba8d3-146">Zwykle zechcesz używać najnowszej wersji dowolnego dodawanego pakietu.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-146">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="ba8d3-147">Ważne jest jednak, aby upewnić się, że wersje wszystkich pakietów pasują do siebie i że są one zgodne z wersją struktury aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-147">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="ba8d3-148">Po wprowadzeniu tych zmian wykonaj `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)), aby pakiet został zainstalowany w systemie.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-148">After you've made these changes, execute `dotnet restore` ([see note](#dotnet-restore-note)) so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="ba8d3-149">Tworzenie żądań sieci Web</span><span class="sxs-lookup"><span data-stu-id="ba8d3-149">Making Web Requests</span></span>

<span data-ttu-id="ba8d3-150">Teraz wszystko jest gotowe do rozpoczęcia pobierania danych z sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-150">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="ba8d3-151">W tej aplikacji należy przeczytać informacje z [interfejsu API usługi GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="ba8d3-151">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="ba8d3-152">Zapoznajmy się z informacjami na temat projektów w ramach parasola [.NET Foundation](https://www.dotnetfoundation.org/) .</span><span class="sxs-lookup"><span data-stu-id="ba8d3-152">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="ba8d3-153">Zacznij od wprowadzenia żądania do interfejsu API usługi GitHub w celu pobrania informacji o projektach.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-153">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="ba8d3-154">Używany punkt końcowy to: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-154">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="ba8d3-155">Chcesz pobrać wszystkie informacje o tych projektach, aby użyć żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-155">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="ba8d3-156">Przeglądarka korzysta również z żądań HTTP GET, dlatego można wkleić ten adres URL do przeglądarki, aby zobaczyć, jakie informacje będą odbierane i przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-156">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="ba8d3-157">Użyj klasy, <xref:System.Net.Http.HttpClient> aby wykonywać żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-157">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="ba8d3-158">Podobnie jak w przypadku wszystkich nowoczesnych <xref:System.Net.Http.HttpClient> interfejsów API platformy .NET, obsługiwane są tylko metody asynchroniczne dla długotrwałych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-158">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="ba8d3-159">Zacznij od wprowadzenia metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-159">Start by making an async method.</span></span> <span data-ttu-id="ba8d3-160">Wdrożenie jest wypełniane podczas tworzenia funkcjonalności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-160">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="ba8d3-161">Najpierw Otwórz `program.cs` plik w katalogu projektu i Dodaj następującą metodę `Program` do klasy:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-161">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="ba8d3-162">Należy dodać `using` instrukcję w górnej `Main` części metody, aby C# kompilator rozpoznaje <xref:System.Threading.Tasks.Task> typ:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-162">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="ba8d3-163">Jeśli tworzysz projekt w tym momencie, otrzymasz ostrzeżenie wygenerowane dla tej metody, ponieważ nie zawiera ona żadnych `await` operatorów i zostanie uruchomiony synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-163">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="ba8d3-164">Zignoruj to teraz; Operatory należy dodać `await` podczas wypełniania.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-164">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="ba8d3-165">Następnie zmień nazwę przestrzeni nazw zdefiniowanej w `namespace` instrukcji z `ConsoleApp` domyślnej na `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-165">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="ba8d3-166">Później zdefiniujemy `repo` klasę w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-166">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="ba8d3-167">Następnie zaktualizuj `Main` metodę, aby wywołać tę metodę.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-167">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="ba8d3-168">`ProcessRepositories` Metoda zwraca zadanie i nie należy zamykać programu przed zakończeniem tego zadania.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-168">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="ba8d3-169">W związku z tym należy użyć `Wait` metody do blokowania i oczekiwania na zakończenie zadania:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-169">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="ba8d3-170">Teraz masz program, który nic nie robi, ale robi to asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-170">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="ba8d3-171">Ulepszamy go.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-171">Let's improve it.</span></span>

<span data-ttu-id="ba8d3-172">Najpierw wymagany jest obiekt, który może pobrać dane z sieci Web; Możesz użyć <xref:System.Net.Http.HttpClient> , aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-172">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="ba8d3-173">Ten obiekt obsługuje żądanie i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-173">This object handles the request and the responses.</span></span> <span data-ttu-id="ba8d3-174">Utwórz wystąpienie pojedynczego wystąpienia tego typu w `Program` klasie wewnątrz pliku program.cs.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-174">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
        {
            //...
        }
    }
}
```

<span data-ttu-id="ba8d3-175">Wróćmy do `ProcessRepositories` metody i wypełnimy ją pierwszą wersją:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-175">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

<span data-ttu-id="ba8d3-176">Należy również dodać dwie nowe instrukcje using na początku pliku do skompilowania:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-176">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="ba8d3-177">Ta pierwsza wersja wysyła żądanie sieci Web w celu odczytania listy wszystkich repozytoriów w ramach organizacji programu dotnet Foundation.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-177">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="ba8d3-178">(Identyfikator gitHub dla platformy .NET Foundation to "dotnet").</span><span class="sxs-lookup"><span data-stu-id="ba8d3-178">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="ba8d3-179">Pierwsze kilka wierszy zostało skonfigurowanych <xref:System.Net.Http.HttpClient> dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-179">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="ba8d3-180">Najpierw jest skonfigurowany do akceptowania odpowiedzi JSON usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-180">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="ba8d3-181">Ten format jest po prostu kod JSON.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-181">This format is simply JSON.</span></span> <span data-ttu-id="ba8d3-182">Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-182">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="ba8d3-183">Te dwa nagłówki są sprawdzane przez kod serwera usługi GitHub i są niezbędne do pobierania informacji z usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-183">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="ba8d3-184">Po skonfigurowaniu programu <xref:System.Net.Http.HttpClient>należy utworzyć żądanie sieci Web i pobrać odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-184">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="ba8d3-185">W tej pierwszej wersji jest używana <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> wygodna metoda.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-185">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="ba8d3-186">Ta wygodna metoda uruchamia zadanie, które wykonuje żądanie sieci Web, a następnie po powrocie żądania odczytuje strumień odpowiedzi i wyodrębnia zawartość ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-186">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="ba8d3-187">Treść odpowiedzi jest zwracana jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-187">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="ba8d3-188">Ten ciąg jest dostępny po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-188">The string is available when the task completes.</span></span>

<span data-ttu-id="ba8d3-189">Ostatnie dwie wiersze tej metody oczekują na zadanie, a następnie drukują odpowiedź do konsoli.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-189">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="ba8d3-190">Skompiluj aplikację i uruchom ją.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-190">Build the app, and run it.</span></span> <span data-ttu-id="ba8d3-191">Ostrzeżenie kompilacji pozostanie teraz, ponieważ `ProcessRepositories` teraz `await` zawiera operator.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-191">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="ba8d3-192">Zobaczysz długi sposób wyświetlania tekstu sformatowanego w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-192">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="ba8d3-193">Przetwarzanie wyniku JSON</span><span class="sxs-lookup"><span data-stu-id="ba8d3-193">Processing the JSON Result</span></span>

<span data-ttu-id="ba8d3-194">W tym momencie napisano kod umożliwiający pobranie odpowiedzi z serwera sieci Web i wyświetlenie tekstu zawartego w tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-194">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="ba8d3-195">Następnie przekonwertujmy tę odpowiedź JSON na C# obiekty.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-195">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="ba8d3-196">Serializator JSON konwertuje dane JSON na C# obiekty.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-196">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="ba8d3-197">Pierwsze zadanie polega na zdefiniowaniu typu C# klasy, aby zawierała informacje używane z tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-197">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="ba8d3-198">Kompilujmy ten ruch powoli, więc Zacznij od prostego C# typu, który zawiera nazwę repozytorium:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-198">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
```

<span data-ttu-id="ba8d3-199">Umieść powyższy kod w nowym pliku o nazwie "repo. cs".</span><span class="sxs-lookup"><span data-stu-id="ba8d3-199">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="ba8d3-200">Ta wersja klasy reprezentuje najprostszą ścieżkę do przetwarzania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-200">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="ba8d3-201">Nazwa klasy i nazwa elementu członkowskiego są zgodne z nazwami użytymi w pakiecie JSON, a C# nie z następującymi konwencjami.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-201">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="ba8d3-202">Aby naprawić ten problem, należy w późniejszym czasie dostarczyć pewne atrybuty konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-202">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="ba8d3-203">Ta klasa ilustruje kolejną ważną funkcję serializacji i deserializacji kodu JSON: Nie wszystkie pola w pakiecie JSON są częścią tej klasy.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-203">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="ba8d3-204">Serializator JSON zignoruje informacje, które nie są uwzględnione w używanym typie klasy.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-204">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="ba8d3-205">Ta funkcja ułatwia tworzenie typów, które współpracują z tylko podzbiorem pól w pakiecie JSON.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-205">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="ba8d3-206">Teraz, po utworzeniu typu, przyjrzyjmy go.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-206">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="ba8d3-207">Należy utworzyć <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obiekt.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-207">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="ba8d3-208">Ten obiekt musi znać typ CLR oczekiwany przez pobrany pakiet JSON.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-208">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="ba8d3-209">Pakiet z usługi GitHub zawiera sekwencję repozytoriów, więc `List<repo>` jest to poprawny typ.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-209">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="ba8d3-210">Dodaj następujący wiersz do `ProcessRepositories` metody:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-210">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="ba8d3-211">Używane są dwa nowe przestrzenie nazw, dlatego należy dodać je również:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-211">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="ba8d3-212">Następnie użyjesz serializatora, aby przekonwertować kod JSON na C# obiekty.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-212">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="ba8d3-213">Zastąp wywołanie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> `ProcessRepositories` w metodzie następującymi dwoma wierszami:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-213">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="ba8d3-214">Zwróć uwagę, że jesteś teraz <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> używany <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>zamiast.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-214">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="ba8d3-215">Serializator używa strumienia zamiast ciągu jako źródła.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-215">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="ba8d3-216">Wyjaśnimy kilka funkcji C# języka, które są używane w drugim wierszu powyżej.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-216">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="ba8d3-217"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> Argument`await` jest wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-217">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="ba8d3-218">Wyrażenia await mogą pojawiać się niemal wszędzie w kodzie, nawet w przypadku, gdy tylko do tej pory są widoczne jako część instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-218">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="ba8d3-219">Następnie operator konwertuje `object` typ czasu kompilacji na `List<repo>`. `as`</span><span class="sxs-lookup"><span data-stu-id="ba8d3-219">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span>
<span data-ttu-id="ba8d3-220">Deklaracja <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, że zwraca obiekt typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-220">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ba8d3-221"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)>zwróci typ określony podczas konstruowania (`List<repo>` w tym samouczku).</span><span class="sxs-lookup"><span data-stu-id="ba8d3-221"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="ba8d3-222">Jeśli konwersja nie powiedzie się, `as` operator zwróci wartość `null`, zamiast zgłaszać wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-222">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="ba8d3-223">Prawie gotowe do tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-223">You're almost done with this section.</span></span> <span data-ttu-id="ba8d3-224">Teraz, gdy plik JSON został przekonwertowany C# do obiektów, zostanie wyświetlona nazwa każdego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-224">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="ba8d3-225">Zastąp odczytane wiersze:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-225">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="ba8d3-226">należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-226">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="ba8d3-227">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-227">Compile and run the application.</span></span> <span data-ttu-id="ba8d3-228">Spowoduje to wydrukowanie nazw repozytoriów, które są częścią programu .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-228">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="ba8d3-229">Kontrolowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="ba8d3-229">Controlling Serialization</span></span>

<span data-ttu-id="ba8d3-230">Zanim dodasz więcej funkcji, przyjrzyjmy się `repo` typowi C# .</span><span class="sxs-lookup"><span data-stu-id="ba8d3-230">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="ba8d3-231">W tym celu należy dodać adnotację do `repo` typu z *atrybutami* , które kontrolują sposób działania serializatora JSON.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-231">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="ba8d3-232">W Twoim przypadku te atrybuty zostaną użyte do zdefiniowania mapowania między nazwami kluczy JSON i nazwami C# klas i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-232">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="ba8d3-233">Używane są <xref:System.Runtime.Serialization.DataContractAttribute> atrybuty i <xref:System.Runtime.Serialization.DataMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ba8d3-233">The two attributes used are the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes.</span></span> <span data-ttu-id="ba8d3-234">Według Konwencji wszystkie klasy atrybutów kończą się sufiksem `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-234">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="ba8d3-235">Nie trzeba jednak używać tego sufiksu podczas stosowania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-235">However, you do not need to use that suffix when you apply an attribute.</span></span>

<span data-ttu-id="ba8d3-236">Atrybuty <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> znajdują się w innej bibliotece, dlatego należy dodać tę bibliotekę do pliku C# projektu jako zależność.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-236">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="ba8d3-237">Dodaj następujący wiersz do `<ItemGroup>` sekcji pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-237">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="ba8d3-238">Po zapisaniu pliku Uruchom `dotnet restore` polecenie ([patrz Uwaga](#dotnet-restore-note)), aby pobrać ten pakiet.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-238">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="ba8d3-239">Następnie otwórz `repo.cs` plik.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-239">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="ba8d3-240">Zmieńmy nazwę tak, aby korzystała z przypadku języka Pascal, i w pełni `Repository`Wyewidencjonuj nazwę.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-240">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="ba8d3-241">Nadal chcemy zmapować węzły "repozytorium" JSON na ten typ, dlatego należy dodać <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-241">We still want to map JSON 'repo' nodes to this type, so you'll need to add the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class declaration.</span></span> <span data-ttu-id="ba8d3-242">Ustawisz `Name` właściwość atrybutu na nazwę węzłów JSON, które są mapowane na ten typ:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-242">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="ba8d3-243">Jest członkiem <xref:System.Runtime.Serialization> przestrzeni nazw, dlatego należy dodać odpowiednią `using` instrukcję na początku pliku: <xref:System.Runtime.Serialization.DataContractAttribute></span><span class="sxs-lookup"><span data-stu-id="ba8d3-243">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="ba8d3-244">Zmieniono nazwę `repo` klasy na `Repository`, więc musisz wprowadzić taką samą zmianę nazwy w program.cs (niektóre edytory mogą obsługiwać refaktoryzację zmiany nazwy, która spowoduje automatyczne wprowadzenie tej zmiany:)</span><span class="sxs-lookup"><span data-stu-id="ba8d3-244">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="ba8d3-245">Następnie wprowadź tę samą zmianę w `name` polu przy <xref:System.Runtime.Serialization.DataMemberAttribute> użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-245">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="ba8d3-246">Wprowadź następujące zmiany w deklaracji `name` pola w repo.cs:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-246">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="ba8d3-247">Ta zmiana oznacza, że należy zmienić kod, który zapisuje nazwę każdego repozytorium w program.cs:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-247">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="ba8d3-248">Aby upewnić się, że mapowania są poprawne, należy wykonać jedną z nich.`dotnet build` `dotnet run`</span><span class="sxs-lookup"><span data-stu-id="ba8d3-248">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="ba8d3-249">Powinny zostać wyświetlone te same dane wyjściowe co poprzednio.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-249">You should see the same output as before.</span></span> <span data-ttu-id="ba8d3-250">Przed przetworzeniem większej liczby właściwości na serwerze sieci Web należy wprowadzić nową zmianę `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-250">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="ba8d3-251">`Name` Składowa jest polem dostępnym publicznie.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-251">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="ba8d3-252">To nie jest dobre rozwiązanie zorientowane obiektowo, więc zmień je na właściwość.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-252">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="ba8d3-253">Z tego względu nie potrzebujemy żadnego konkretnego kodu do uruchomienia podczas pobierania lub ustawiania właściwości, ale zmiana na Właściwość ułatwia dodawanie tych zmian w późniejszym czasie bez przerywania żadnego kodu, który używa `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-253">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="ba8d3-254">Usuń definicję pola i Zastąp ją [zaimplementowaną właściwością](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span><span class="sxs-lookup"><span data-stu-id="ba8d3-254">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="ba8d3-255">Kompilator generuje treść `get` metod dostępu i `set` , a także pole prywatne do przechowywania nazwy.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-255">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="ba8d3-256">Będzie wyglądać podobnie do następującego kodu, który można wpisać ręcznie:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-256">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name
{
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="ba8d3-257">Utwórzmy jeszcze jedną zmianę przed dodaniem nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-257">Let's make one more change before adding new features.</span></span> <span data-ttu-id="ba8d3-258">`ProcessRepositories` Metoda może wykonywać działania asynchroniczne i zwracać kolekcję repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-258">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="ba8d3-259">Wróćmy do `List<Repository>` tej metody i przeniesiesz kod, który zapisuje informacje `Main` w metodzie.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-259">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="ba8d3-260">Zmień sygnaturę `ProcessRepositories` , aby zwracała zadanie, którego wynikiem jest `Repository` lista obiektów:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-260">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="ba8d3-261">Następnie po przetworzeniu odpowiedzi JSON należy zwrócić repozytoria:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-261">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="ba8d3-262">Kompilator generuje `Task<T>` obiekt do zwrócenia, ponieważ oznaczono tę metodę jako `async`.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-262">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="ba8d3-263">Następnie zmodyfikujemy `Main` metodę, aby przechwycić te wyniki i zapisywali nazwy poszczególnych repozytoriów w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-263">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="ba8d3-264">Teraz `Main` Metoda wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-264">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="ba8d3-265">Uzyskiwanie dostępu do właściwości bloków zadań do momentu ukończenia zadania. `Result`</span><span class="sxs-lookup"><span data-stu-id="ba8d3-265">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="ba8d3-266">Zwykle wolisz wykonać `await` zadanie, jak `ProcessRepositories` w metodzie, ale nie jest `Main` to dozwolone w metodzie.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-266">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="ba8d3-267">Odczytywanie dodatkowych informacji</span><span class="sxs-lookup"><span data-stu-id="ba8d3-267">Reading More Information</span></span>

<span data-ttu-id="ba8d3-268">Zakończmy to przez przetwarzanie kilku większej liczby właściwości w pakiecie JSON, które są wysyłane z interfejsu API usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-268">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="ba8d3-269">Nie chcesz dowiedzieć się wszystkiego, ale dodanie kilku właściwości spowoduje pokazanie kilku funkcji C# języka.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-269">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="ba8d3-270">Zacznijmy od dodania kilku prostych typów do `Repository` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-270">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="ba8d3-271">Dodaj te właściwości do tej klasy:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-271">Add these properties to that class:</span></span>

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="ba8d3-272">Te właściwości mają wbudowane konwersje z typu ciąg (który zawiera pakiety JSON) do typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-272">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="ba8d3-273"><xref:System.Uri> Typ może być nowy dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-273">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="ba8d3-274">Reprezentuje identyfikator URI lub w tym przypadku adres URL.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-274">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="ba8d3-275">W przypadku `Uri` typów i `int` , jeśli pakiet JSON zawiera dane, które nie są konwertowane na typ docelowy, Akcja serializacji zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-275">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="ba8d3-276">Po dodaniu tych elementów zaktualizuj `Main` metodę, aby wyświetlić te elementy:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-276">Once you've added these, update the `Main` method to display those elements:</span></span>

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```

<span data-ttu-id="ba8d3-277">Ostatnim krokiem jest dodanie informacji dla ostatniej operacji wypychania.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-277">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="ba8d3-278">Te informacje są sformatowane w ten sposób w odpowiedzi JSON:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-278">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="ba8d3-279">Ten format nie jest zgodny z żadnym ze standardowych formatów <xref:System.DateTime> .NET.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-279">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="ba8d3-280">Z tego powodu należy napisać niestandardową metodę konwersji.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-280">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="ba8d3-281">Prawdopodobnie nie chcesz również, aby nieprzetworzony ciąg był uwidoczniony dla `Repository` użytkowników klasy.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-281">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="ba8d3-282">Atrybuty mogą również ułatwić kontrolę.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-282">Attributes can help control that as well.</span></span> <span data-ttu-id="ba8d3-283">Najpierw Zdefiniuj `private` właściwość, która będzie przechowywać ciąg reprezentujący datę i godzinę `Repository` w klasie:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-283">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="ba8d3-284"><xref:System.Runtime.Serialization.DataMemberAttribute> Atrybut informuje Serializator, który powinien być przetwarzany, nawet jeśli nie jest to publiczny element członkowski.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-284">The <xref:System.Runtime.Serialization.DataMemberAttribute> attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="ba8d3-285">Następnie musisz napisać publiczną właściwość tylko do odczytu, która konwertuje ciąg na prawidłowy <xref:System.DateTime> obiekt, i <xref:System.DateTime>zwraca:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-285">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

<span data-ttu-id="ba8d3-286">Przejdźmy do nowych konstrukcji powyżej.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-286">Let's go over the new constructs above.</span></span> <span data-ttu-id="ba8d3-287">Ten `IgnoreDataMember` atrybut nakazuje serializatorowi, że ten typ nie powinien być odczytany ani zapisany z dowolnego obiektu JSON.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-287">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="ba8d3-288">Ta właściwość zawiera tylko `get` metodę dostępu.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-288">This property contains only a `get` accessor.</span></span> <span data-ttu-id="ba8d3-289">`set` Brak metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-289">There is no `set` accessor.</span></span> <span data-ttu-id="ba8d3-290">To właśnie definiuje właściwość tylko do *odczytu* w C#.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-290">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="ba8d3-291">(Tak, możesz tworzyć właściwości *tylko do zapisu* w C#, ale ich wartości są ograniczone). Metoda analizuje ciąg i <xref:System.DateTime> tworzy obiekt przy użyciu podanego formatu daty i `DateTime` dodaje dodatkowe `CultureInfo` metadane do obiektu za pomocą. <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)></span><span class="sxs-lookup"><span data-stu-id="ba8d3-291">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="ba8d3-292">Jeśli operacja analizy zakończy się niepowodzeniem, metoda dostępu do właściwości zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-292">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="ba8d3-293">Aby użyć <xref:System.Globalization.CultureInfo.InvariantCulture>, należy <xref:System.Globalization> dodać przestrzeń nazw do `using` instrukcji w `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-293">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="ba8d3-294">Na koniec Dodaj jedną instrukcję wyjściową w konsoli i wszystko jest gotowe do skompilowania i uruchomienia tej aplikacji ponownie:</span><span class="sxs-lookup"><span data-stu-id="ba8d3-294">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="ba8d3-295">Twoja wersja powinna teraz być zgodna z [Zakończono przykładem](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="ba8d3-295">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="ba8d3-296">Wniosek</span><span class="sxs-lookup"><span data-stu-id="ba8d3-296">Conclusion</span></span>

<span data-ttu-id="ba8d3-297">W tym samouczku pokazano, jak wykonywać żądania sieci Web, analizować wyniki i wyświetlać właściwości tych wyników.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-297">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="ba8d3-298">Dodano również nowe pakiety jako zależności w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-298">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="ba8d3-299">Zaobserwowano niektóre funkcje C# języka, które obsługują techniki zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="ba8d3-299">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
