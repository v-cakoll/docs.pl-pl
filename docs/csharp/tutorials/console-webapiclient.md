---
title: Tworzenie klienta REST przy użyciu platformy .NET Core
description: W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 1b85a03919ea057cda4526ac1c873bf058c9a825
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867363"
---
# <a name="rest-client"></a><span data-ttu-id="21514-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="21514-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="21514-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="21514-104">Introduction</span></span>

<span data-ttu-id="21514-105">W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka.</span><span class="sxs-lookup"><span data-stu-id="21514-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="21514-106">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="21514-106">You’ll learn:</span></span>

* <span data-ttu-id="21514-107">Podstawowe informacje o interfejsie wiersza polecenia (CLI) platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="21514-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
* <span data-ttu-id="21514-108">Omówienie funkcji C# języka.</span><span class="sxs-lookup"><span data-stu-id="21514-108">An overview of C# Language features.</span></span>
* <span data-ttu-id="21514-109">Zarządzanie zależnościami przy użyciu narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="21514-109">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="21514-110">HTTP Communications</span><span class="sxs-lookup"><span data-stu-id="21514-110">HTTP Communications</span></span>
* <span data-ttu-id="21514-111">Przetwarzanie informacji JSON</span><span class="sxs-lookup"><span data-stu-id="21514-111">Processing JSON information</span></span>
* <span data-ttu-id="21514-112">Zarządzanie konfiguracją przy użyciu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="21514-112">Managing configuration with Attributes.</span></span>

<span data-ttu-id="21514-113">Utworzysz aplikację, która wystawia żądania HTTP do usługi REST w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="21514-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="21514-114">Informacje są odczytywane w formacie JSON i konwertowane tego pakietu JSON na C# obiekty.</span><span class="sxs-lookup"><span data-stu-id="21514-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="21514-115">Na koniec zobaczysz, jak korzystać z C# obiektów.</span><span class="sxs-lookup"><span data-stu-id="21514-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="21514-116">Ten samouczek zawiera wiele funkcji.</span><span class="sxs-lookup"><span data-stu-id="21514-116">There are many features in this tutorial.</span></span> <span data-ttu-id="21514-117">Kompilujmy je po jednej.</span><span class="sxs-lookup"><span data-stu-id="21514-117">Let’s build them one by one.</span></span>

<span data-ttu-id="21514-118">Jeśli wolisz postępować wraz z [ostatnim przykładem](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) dla tego tematu, możesz go pobrać.</span><span class="sxs-lookup"><span data-stu-id="21514-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="21514-119">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="21514-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="21514-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="21514-120">Prerequisites</span></span>

<span data-ttu-id="21514-121">Musisz skonfigurować maszynę do uruchamiania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="21514-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="21514-122">Instrukcje instalacji można znaleźć na stronie [pliki do pobrania w programie .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="21514-122">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="21514-123">Tę aplikację można uruchomić w systemie Windows, Linux, macOS lub w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="21514-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="21514-124">Musisz zainstalować swój ulubiony Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="21514-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="21514-125">Poniższe opisy wykorzystują [Visual Studio Code](https://code.visualstudio.com/), czyli edytor Międzyplatformowy.</span><span class="sxs-lookup"><span data-stu-id="21514-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="21514-126">Można jednak korzystać z dowolnych narzędzi, z którymi masz doświadczenie.</span><span class="sxs-lookup"><span data-stu-id="21514-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="21514-127">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="21514-127">Create the Application</span></span>

<span data-ttu-id="21514-128">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21514-128">The first step is to create a new application.</span></span> <span data-ttu-id="21514-129">Otwórz wiersz polecenia i Utwórz nowy katalog dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21514-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="21514-130">Upewnij się, że bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="21514-130">Make that the current directory.</span></span> <span data-ttu-id="21514-131">W oknie konsoli wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="21514-131">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebApiClient
```

<span data-ttu-id="21514-132">Spowoduje to utworzenie plików początkowych dla podstawowej aplikacji "Hello world".</span><span class="sxs-lookup"><span data-stu-id="21514-132">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="21514-133">Nazwa projektu to "WebApiClient".</span><span class="sxs-lookup"><span data-stu-id="21514-133">The project name is "WebApiClient".</span></span> <span data-ttu-id="21514-134">Ponieważ jest to nowy projekt, żadne zależności nie są stosowane.</span><span class="sxs-lookup"><span data-stu-id="21514-134">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="21514-135">Pierwsze uruchomienie spowoduje pobranie platformy .NET Core, zainstalowanie certyfikatu deweloperskiego i uruchomienie Menedżera pakietów NuGet w celu przywrócenia brakujących zależności.</span><span class="sxs-lookup"><span data-stu-id="21514-135">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="21514-136">Przed rozpoczęciem wprowadzania modyfikacji wpisz `dotnet run` ([Zobacz Uwaga](#dotnet-restore-note)) w wierszu polecenia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="21514-136">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="21514-137">`dotnet run` automatycznie wykonuje `dotnet restore`, jeśli w środowisku nie ma zależności.</span><span class="sxs-lookup"><span data-stu-id="21514-137">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="21514-138">Wykonuje również `dotnet build`, jeśli aplikacja musi zostać odbudowana.</span><span class="sxs-lookup"><span data-stu-id="21514-138">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="21514-139">Po wstępnej konfiguracji wystarczy uruchomić `dotnet restore` lub `dotnet build`, gdy ma to sens dla projektu.</span><span class="sxs-lookup"><span data-stu-id="21514-139">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="21514-140">Dodawanie nowych zależności</span><span class="sxs-lookup"><span data-stu-id="21514-140">Adding New Dependencies</span></span>

<span data-ttu-id="21514-141">Jednym z kluczowych celów projektowych dla platformy .NET Core jest Minimalizacja rozmiaru instalacji programu .NET.</span><span class="sxs-lookup"><span data-stu-id="21514-141">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="21514-142">Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych funkcji, należy dodać te zależności do pliku C# projektu (\*. csproj).</span><span class="sxs-lookup"><span data-stu-id="21514-142">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="21514-143">Na potrzeby tego przykładu należy dodać pakiet `System.Runtime.Serialization.Json`, aby aplikacja mogła przetwarzać odpowiedzi JSON.</span><span class="sxs-lookup"><span data-stu-id="21514-143">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="21514-144">Wymagany jest pakiet `System.Runtime.Serialization.Json` dla tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21514-144">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="21514-145">Dodaj go do projektu, uruchamiając następujące polecenie [interfejsu wiersza polecenia platformy .NET](../../core/tools/dotnet-add-package.md) :</span><span class="sxs-lookup"><span data-stu-id="21514-145">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```console
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="21514-146">Tworzenie żądań sieci Web</span><span class="sxs-lookup"><span data-stu-id="21514-146">Making Web Requests</span></span>

<span data-ttu-id="21514-147">Teraz wszystko jest gotowe do rozpoczęcia pobierania danych z sieci Web.</span><span class="sxs-lookup"><span data-stu-id="21514-147">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="21514-148">W tej aplikacji należy przeczytać informacje z [interfejsu API usługi GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="21514-148">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="21514-149">Zapoznajmy się z informacjami na temat projektów w ramach parasola [.NET Foundation](https://www.dotnetfoundation.org/) .</span><span class="sxs-lookup"><span data-stu-id="21514-149">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="21514-150">Zacznij od wprowadzenia żądania do interfejsu API usługi GitHub w celu pobrania informacji o projektach.</span><span class="sxs-lookup"><span data-stu-id="21514-150">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="21514-151">Używany punkt końcowy to: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="21514-151">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="21514-152">Chcesz pobrać wszystkie informacje o tych projektach, aby użyć żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="21514-152">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="21514-153">Przeglądarka korzysta również z żądań HTTP GET, dlatego można wkleić ten adres URL do przeglądarki, aby zobaczyć, jakie informacje będą odbierane i przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="21514-153">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="21514-154">Użyj klasy <xref:System.Net.Http.HttpClient>, aby wykonywać żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="21514-154">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="21514-155">Podobnie jak w przypadku wszystkich nowoczesnych interfejsów API platformy .NET, <xref:System.Net.Http.HttpClient> obsługuje tylko metody asynchroniczne dla długotrwałych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="21514-155">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="21514-156">Zacznij od wprowadzenia metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="21514-156">Start by making an async method.</span></span> <span data-ttu-id="21514-157">Wdrożenie jest wypełniane podczas tworzenia funkcjonalności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21514-157">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="21514-158">Zacznij od otwarcia pliku `program.cs` w katalogu projektu i dodania następującej metody do klasy `Program`:</span><span class="sxs-lookup"><span data-stu-id="21514-158">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="21514-159">Należy dodać dyrektywę `using` w górnej części metody `Main`, aby C# kompilator rozpoznał <xref:System.Threading.Tasks.Task> typ:</span><span class="sxs-lookup"><span data-stu-id="21514-159">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="21514-160">W przypadku skompilowania projektu w tym momencie otrzymasz ostrzeżenie wygenerowane dla tej metody, ponieważ nie zawiera ona żadnych operatorów `await` i zostanie uruchomiona synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="21514-160">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="21514-161">Zignoruj to teraz; podczas wypełniania należy dodać operatory `await`.</span><span class="sxs-lookup"><span data-stu-id="21514-161">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="21514-162">Następnie zmień nazwę przestrzeni nazw zdefiniowanej w instrukcji `namespace` z jej domyślnego `ConsoleApp` na `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="21514-162">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="21514-163">W tej przestrzeni nazw będziemy później definiować klasy `repo`.</span><span class="sxs-lookup"><span data-stu-id="21514-163">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="21514-164">Następnie zaktualizuj metodę `Main`, aby wywołać tę metodę.</span><span class="sxs-lookup"><span data-stu-id="21514-164">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="21514-165">Metoda `ProcessRepositories` zwraca zadanie i nie należy zamykać programu przed zakończeniem tego zadania.</span><span class="sxs-lookup"><span data-stu-id="21514-165">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="21514-166">W związku z tym należy zmienić sygnaturę `Main`.</span><span class="sxs-lookup"><span data-stu-id="21514-166">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="21514-167">Dodaj modyfikator `async` i Zmień zwracany typ na `Task`.</span><span class="sxs-lookup"><span data-stu-id="21514-167">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="21514-168">Następnie w treści metody Dodaj wywołanie do `ProcessRepositories`.</span><span class="sxs-lookup"><span data-stu-id="21514-168">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="21514-169">Dodaj słowo kluczowe `await` do tego wywołania metody:</span><span class="sxs-lookup"><span data-stu-id="21514-169">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="21514-170">Teraz masz program, który nic nie robi, ale robi to asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="21514-170">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="21514-171">Ulepszamy go.</span><span class="sxs-lookup"><span data-stu-id="21514-171">Let's improve it.</span></span>

<span data-ttu-id="21514-172">Najpierw wymagany jest obiekt, który może pobrać dane z sieci Web; Aby to zrobić, możesz użyć <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="21514-172">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="21514-173">Ten obiekt obsługuje żądanie i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="21514-173">This object handles the request and the responses.</span></span> <span data-ttu-id="21514-174">Utwórz wystąpienie pojedynczego wystąpienia tego typu w klasie `Program` w pliku *program.cs* .</span><span class="sxs-lookup"><span data-stu-id="21514-174">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static async Task Main(string[] args)
        {
            //...
        }
    }
}
```

<span data-ttu-id="21514-175">Wróćmy do metody `ProcessRepositories` i wypełnimy ją pierwszą wersją:</span><span class="sxs-lookup"><span data-stu-id="21514-175">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="21514-176">Należy również dodać dwie nowe dyrektywy `using` w górnej części pliku do skompilowania:</span><span class="sxs-lookup"><span data-stu-id="21514-176">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="21514-177">Ta pierwsza wersja wysyła żądanie sieci Web w celu odczytania listy wszystkich repozytoriów w ramach organizacji programu dotnet Foundation.</span><span class="sxs-lookup"><span data-stu-id="21514-177">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="21514-178">(Identyfikator gitHub dla platformy .NET Foundation to "dotnet").</span><span class="sxs-lookup"><span data-stu-id="21514-178">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="21514-179">Pierwsze kilka wierszy skonfiguruje <xref:System.Net.Http.HttpClient> dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="21514-179">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="21514-180">Najpierw jest skonfigurowany do akceptowania odpowiedzi JSON usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="21514-180">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="21514-181">Ten format jest po prostu kod JSON.</span><span class="sxs-lookup"><span data-stu-id="21514-181">This format is simply JSON.</span></span> <span data-ttu-id="21514-182">Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="21514-182">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="21514-183">Te dwa nagłówki są sprawdzane przez kod serwera usługi GitHub i są niezbędne do pobierania informacji z usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="21514-183">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="21514-184">Po skonfigurowaniu <xref:System.Net.Http.HttpClient>należy utworzyć żądanie sieci Web i pobrać odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="21514-184">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="21514-185">W tej pierwszej wersji jest używana metoda <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> wygodna.</span><span class="sxs-lookup"><span data-stu-id="21514-185">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="21514-186">Ta wygodna metoda uruchamia zadanie, które wykonuje żądanie sieci Web, a następnie po powrocie żądania odczytuje strumień odpowiedzi i wyodrębnia zawartość ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="21514-186">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="21514-187">Treść odpowiedzi jest zwracana jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="21514-187">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="21514-188">Ten ciąg jest dostępny po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="21514-188">The string is available when the task completes.</span></span>

<span data-ttu-id="21514-189">Ostatnie dwie wiersze tej metody oczekują na zadanie, a następnie drukują odpowiedź do konsoli.</span><span class="sxs-lookup"><span data-stu-id="21514-189">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="21514-190">Skompiluj aplikację i uruchom ją.</span><span class="sxs-lookup"><span data-stu-id="21514-190">Build the app, and run it.</span></span> <span data-ttu-id="21514-191">Ostrzeżenie kompilacji teraz znikło, ponieważ `ProcessRepositories` teraz zawiera operator `await`.</span><span class="sxs-lookup"><span data-stu-id="21514-191">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="21514-192">Zobaczysz długi sposób wyświetlania tekstu sformatowanego w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="21514-192">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="21514-193">Przetwarzanie wyniku JSON</span><span class="sxs-lookup"><span data-stu-id="21514-193">Processing the JSON Result</span></span>

<span data-ttu-id="21514-194">W tym momencie napisano kod umożliwiający pobranie odpowiedzi z serwera sieci Web i wyświetlenie tekstu zawartego w tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="21514-194">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="21514-195">Następnie przekonwertujmy tę odpowiedź JSON na C# obiekty.</span><span class="sxs-lookup"><span data-stu-id="21514-195">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="21514-196">Klasa <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializować obiekty do formatu JSON i deserializacji kod JSON w obiektach.</span><span class="sxs-lookup"><span data-stu-id="21514-196">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="21514-197">Zacznij od zdefiniowania klasy, która będzie reprezentować `repo` obiekt JSON zwrócony z interfejsu API usługi GitHub:</span><span class="sxs-lookup"><span data-stu-id="21514-197">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; }
    }
}
```

<span data-ttu-id="21514-198">Umieść powyższy kod w nowym pliku o nazwie "repo. cs".</span><span class="sxs-lookup"><span data-stu-id="21514-198">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="21514-199">Ta wersja klasy reprezentuje najprostszą ścieżkę do przetwarzania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="21514-199">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="21514-200">Nazwa klasy i nazwa elementu członkowskiego są zgodne z nazwami użytymi w pakiecie JSON, a C# nie z następującymi konwencjami.</span><span class="sxs-lookup"><span data-stu-id="21514-200">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="21514-201">Aby naprawić ten problem, należy w późniejszym czasie dostarczyć pewne atrybuty konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="21514-201">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="21514-202">Ta klasa pokazuje kolejną ważną funkcję serializacji i deserializacji kodu JSON: nie wszystkie pola w pakiecie JSON są częścią tej klasy.</span><span class="sxs-lookup"><span data-stu-id="21514-202">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="21514-203">Serializator JSON zignoruje informacje, które nie są uwzględnione w używanym typie klasy.</span><span class="sxs-lookup"><span data-stu-id="21514-203">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="21514-204">Ta funkcja ułatwia tworzenie typów, które współpracują z tylko podzbiorem pól w pakiecie JSON.</span><span class="sxs-lookup"><span data-stu-id="21514-204">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="21514-205">Teraz, po utworzeniu typu, przyjrzyjmy go.</span><span class="sxs-lookup"><span data-stu-id="21514-205">Now that you've created the type, let's deserialize it.</span></span> 

<span data-ttu-id="21514-206">Następnie użyjesz serializatora, aby przekonwertować kod JSON na C# obiekty.</span><span class="sxs-lookup"><span data-stu-id="21514-206">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="21514-207">Zastąp wywołanie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> w metodzie `ProcessRepositories` następującymi trzema wierszami:</span><span class="sxs-lookup"><span data-stu-id="21514-207">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following three lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="21514-208">Używasz nowej przestrzeni nazw, więc musisz ją dodać również na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="21514-208">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="21514-209">Zwróć uwagę, że teraz używasz <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)>, a nie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="21514-209">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="21514-210">Serializator używa strumienia zamiast ciągu jako źródła.</span><span class="sxs-lookup"><span data-stu-id="21514-210">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="21514-211">Wyjaśnimy kilka funkcji C# języka, które są używane w drugim wierszu poprzedniego fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="21514-211">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="21514-212">Pierwszym argumentem <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> jest wyrażenie `await`.</span><span class="sxs-lookup"><span data-stu-id="21514-212">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="21514-213">(Pozostałe dwa parametry są opcjonalne i pomijane we fragmencie kodu). Wyrażenia await mogą pojawiać się niemal wszędzie w kodzie, nawet w przypadku, gdy tylko do tej pory są widoczne jako część instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="21514-213">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="21514-214">Metoda `Deserialize` jest *rodzajowa*, co oznacza, że należy podać argumenty typu dla rodzaju obiektów, które mają być tworzone na podstawie tekstu JSON.</span><span class="sxs-lookup"><span data-stu-id="21514-214">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="21514-215">W tym przykładzie Serializacja jest deserializowana do `List<Repository>`, który jest innym obiektem ogólnym, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="21514-215">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="21514-216">Klasa `List<>` przechowuje kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="21514-216">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="21514-217">Argument typu deklaruje typ obiektów przechowywanych w `List<>`.</span><span class="sxs-lookup"><span data-stu-id="21514-217">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="21514-218">Tekst JSON reprezentuje kolekcję obiektów repozytorium, więc argument typu jest `Repository`.</span><span class="sxs-lookup"><span data-stu-id="21514-218">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="21514-219">Prawie gotowe do tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="21514-219">You're almost done with this section.</span></span> <span data-ttu-id="21514-220">Teraz, gdy plik JSON został przekonwertowany C# do obiektów, zostanie wyświetlona nazwa każdego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="21514-220">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="21514-221">Zastąp odczytane wiersze:</span><span class="sxs-lookup"><span data-stu-id="21514-221">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="21514-222">należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="21514-222">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="21514-223">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="21514-223">Compile and run the application.</span></span> <span data-ttu-id="21514-224">Spowoduje to wydrukowanie nazw repozytoriów, które są częścią programu .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="21514-224">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="21514-225">Kontrolowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="21514-225">Controlling Serialization</span></span>

<span data-ttu-id="21514-226">Zanim dodasz więcej funkcji, przyjrzyjmy się `name` właściwości przy użyciu atrybutu `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="21514-226">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="21514-227">Wprowadź następujące zmiany w deklaracji pola `name` w repo.cs:</span><span class="sxs-lookup"><span data-stu-id="21514-227">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="21514-228">Aby użyć `[JsonPropertyName]` atrybutu, należy dodać przestrzeń nazw <xref:System.Text.Json.Serialization> do dyrektyw `using`:</span><span class="sxs-lookup"><span data-stu-id="21514-228">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="21514-229">Ta zmiana oznacza, że należy zmienić kod, który zapisuje nazwę każdego repozytorium w program.cs:</span><span class="sxs-lookup"><span data-stu-id="21514-229">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="21514-230">Wykonaj `dotnet run`, aby upewnić się, że mapowania są poprawne.</span><span class="sxs-lookup"><span data-stu-id="21514-230">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="21514-231">Powinny zostać wyświetlone te same dane wyjściowe co poprzednio.</span><span class="sxs-lookup"><span data-stu-id="21514-231">You should see the same output as before.</span></span>

<span data-ttu-id="21514-232">Utwórzmy jeszcze jedną zmianę przed dodaniem nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="21514-232">Let's make one more change before adding new features.</span></span> <span data-ttu-id="21514-233">Metoda `ProcessRepositories` może wykonywać działania asynchroniczne i zwracać kolekcję repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="21514-233">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="21514-234">Zwróćmy `List<Repository>` z tej metody i przeniesiesz kod, który zapisuje informacje w metodzie `Main`.</span><span class="sxs-lookup"><span data-stu-id="21514-234">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="21514-235">Zmień sygnaturę `ProcessRepositories`, aby zwracała zadanie, którego wynikiem jest lista obiektów `Repository`:</span><span class="sxs-lookup"><span data-stu-id="21514-235">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="21514-236">Następnie po przetworzeniu odpowiedzi JSON należy zwrócić repozytoria:</span><span class="sxs-lookup"><span data-stu-id="21514-236">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="21514-237">Kompilator generuje obiekt `Task<T>` dla zwracanych, ponieważ oznaczono tę metodę jako `async`.</span><span class="sxs-lookup"><span data-stu-id="21514-237">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="21514-238">Następnie Zmodyfikujmy metodę `Main` tak, aby przechwytł te wyniki i zapisywali nazwy poszczególnych repozytoriów w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="21514-238">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="21514-239">Teraz Metoda `Main` wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="21514-239">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="21514-240">Odczytywanie dodatkowych informacji</span><span class="sxs-lookup"><span data-stu-id="21514-240">Reading More Information</span></span>

<span data-ttu-id="21514-241">Zakończmy to przez przetwarzanie kilku większej liczby właściwości w pakiecie JSON, które są wysyłane z interfejsu API usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="21514-241">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="21514-242">Nie chcesz dowiedzieć się wszystkiego, ale dodanie kilku właściwości spowoduje pokazanie kilku funkcji C# języka.</span><span class="sxs-lookup"><span data-stu-id="21514-242">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="21514-243">Zacznijmy od dodania kilku prostych typów do definicji klasy `Repository`.</span><span class="sxs-lookup"><span data-stu-id="21514-243">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="21514-244">Dodaj te właściwości do tej klasy:</span><span class="sxs-lookup"><span data-stu-id="21514-244">Add these properties to that class:</span></span>

```csharp
[JsonPropertyName("description")]
public string Description { get; set; }

[JsonPropertyName("html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName("homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName("watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="21514-245">Te właściwości mają wbudowane konwersje z typu ciąg (który zawiera pakiety JSON) do typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="21514-245">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="21514-246">Typ <xref:System.Uri> może być nowy dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="21514-246">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="21514-247">Reprezentuje identyfikator URI lub w tym przypadku adres URL.</span><span class="sxs-lookup"><span data-stu-id="21514-247">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="21514-248">W przypadku typów `Uri` i `int`, jeśli pakiet JSON zawiera dane, które nie są konwertowane na typ docelowy, Akcja serializacji zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="21514-248">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="21514-249">Po dodaniu tych elementów zaktualizuj metodę `Main`, aby wyświetlić te elementy:</span><span class="sxs-lookup"><span data-stu-id="21514-249">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="21514-250">Ostatnim krokiem jest dodanie informacji dla ostatniej operacji wypychania.</span><span class="sxs-lookup"><span data-stu-id="21514-250">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="21514-251">Te informacje są sformatowane w ten sposób w odpowiedzi JSON:</span><span class="sxs-lookup"><span data-stu-id="21514-251">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="21514-252">Ten format nie jest zgodny z żadnym ze standardowych formatów programu .NET <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="21514-252">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="21514-253">Z tego powodu należy napisać niestandardową metodę konwersji.</span><span class="sxs-lookup"><span data-stu-id="21514-253">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="21514-254">Prawdopodobnie nie chcesz również, aby nieprzetworzony ciąg był widoczny dla użytkowników klasy `Repository`.</span><span class="sxs-lookup"><span data-stu-id="21514-254">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="21514-255">Atrybuty mogą również ułatwić kontrolę.</span><span class="sxs-lookup"><span data-stu-id="21514-255">Attributes can help control that as well.</span></span> <span data-ttu-id="21514-256">Najpierw Zdefiniuj `public` właściwość, która będzie przechowywać ciąg reprezentujący datę i godzinę w klasie `Repository` i Właściwość `LastPush` `readonly`, która zwraca sformatowany ciąg, który reprezentuje datę zwróconą:</span><span class="sxs-lookup"><span data-stu-id="21514-256">First, define a `public` property that will hold the string representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns a formatted string that represents the returned date:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

<span data-ttu-id="21514-257">Przejdźmy do nowej konstrukcji, która została właśnie zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="21514-257">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="21514-258">Właściwość `LastPush` jest definiowana przy użyciu *składowej z wyrażeniami* dla metody dostępu `get`.</span><span class="sxs-lookup"><span data-stu-id="21514-258">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="21514-259">Brak metody dostępu `set`.</span><span class="sxs-lookup"><span data-stu-id="21514-259">There is no `set` accessor.</span></span> <span data-ttu-id="21514-260">Pomijanie metody dostępu `set` jest sposobem definiowania właściwości *tylko do odczytu* w C#.</span><span class="sxs-lookup"><span data-stu-id="21514-260">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="21514-261">(Tak, możesz tworzyć właściwości *tylko do zapisu* w C#, ale ich wartości są ograniczone). Metoda <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analizuje ciąg i tworzy obiekt <xref:System.DateTime> przy użyciu podanego formatu daty i dodaje dodatkowe metadane do `DateTime` przy użyciu obiektu `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="21514-261">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="21514-262">Jeśli operacja analizy zakończy się niepowodzeniem, metoda dostępu do właściwości zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="21514-262">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="21514-263">Aby użyć <xref:System.Globalization.CultureInfo.InvariantCulture>, należy dodać przestrzeń nazw <xref:System.Globalization> do dyrektyw `using` w `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="21514-263">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` directives in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="21514-264">Na koniec Dodaj jedną instrukcję wyjściową w konsoli i wszystko jest gotowe do skompilowania i uruchomienia tej aplikacji ponownie:</span><span class="sxs-lookup"><span data-stu-id="21514-264">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="21514-265">Twoja wersja powinna teraz być zgodna z [Zakończono przykładem](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="21514-265">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="21514-266">Wniosek</span><span class="sxs-lookup"><span data-stu-id="21514-266">Conclusion</span></span>

<span data-ttu-id="21514-267">W tym samouczku pokazano, jak wykonywać żądania sieci Web, analizować wyniki i wyświetlać właściwości tych wyników.</span><span class="sxs-lookup"><span data-stu-id="21514-267">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="21514-268">Dodano również nowe pakiety jako zależności w projekcie.</span><span class="sxs-lookup"><span data-stu-id="21514-268">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="21514-269">Zaobserwowano niektóre funkcje C# języka, które obsługują techniki zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="21514-269">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
