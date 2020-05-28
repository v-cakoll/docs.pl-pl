---
title: Tworzenie klienta REST przy użyciu platformy .NET Core
description: W tym samouczku przedstawiono szereg funkcji platformy .NET Core i języka C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 1d1d1bec8c6602e4fe34fa3ce243423290412736
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004858"
---
# <a name="rest-client"></a><span data-ttu-id="42506-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="42506-103">REST client</span></span>

<span data-ttu-id="42506-104">W tym samouczku przedstawiono szereg funkcji platformy .NET Core i języka C#.</span><span class="sxs-lookup"><span data-stu-id="42506-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="42506-105">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="42506-105">You’ll learn:</span></span>

* <span data-ttu-id="42506-106">Podstawowe informacje dotyczące interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="42506-106">The basics of the .NET Core CLI.</span></span>
* <span data-ttu-id="42506-107">Omówienie funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="42506-107">An overview of C# Language features.</span></span>
* <span data-ttu-id="42506-108">Zarządzanie zależnościami przy użyciu narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="42506-108">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="42506-109">Komunikacja HTTP</span><span class="sxs-lookup"><span data-stu-id="42506-109">HTTP Communications</span></span>
* <span data-ttu-id="42506-110">Przetwarzanie informacji JSON</span><span class="sxs-lookup"><span data-stu-id="42506-110">Processing JSON information</span></span>
* <span data-ttu-id="42506-111">Zarządzanie konfiguracją przy użyciu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="42506-111">Managing configuration with Attributes.</span></span>

<span data-ttu-id="42506-112">Utworzysz aplikację, która wystawia żądania HTTP do usługi REST w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="42506-112">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="42506-113">Informacje są odczytywane w formacie JSON i konwertowane na obiekty w języku C#.</span><span class="sxs-lookup"><span data-stu-id="42506-113">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="42506-114">Na koniec zobaczysz, jak korzystać z obiektów C#.</span><span class="sxs-lookup"><span data-stu-id="42506-114">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="42506-115">Ten samouczek zawiera wiele funkcji.</span><span class="sxs-lookup"><span data-stu-id="42506-115">There are many features in this tutorial.</span></span> <span data-ttu-id="42506-116">Kompilujmy je po jednej.</span><span class="sxs-lookup"><span data-stu-id="42506-116">Let’s build them one by one.</span></span>

<span data-ttu-id="42506-117">Jeśli wolisz postępować wraz z [ostatnim przykładem](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) dla tego tematu, możesz go pobrać.</span><span class="sxs-lookup"><span data-stu-id="42506-117">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="42506-118">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="42506-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="42506-119">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="42506-119">Prerequisites</span></span>

<span data-ttu-id="42506-120">Musisz skonfigurować maszynę do uruchamiania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="42506-120">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="42506-121">Instrukcje instalacji można znaleźć na stronie [pliki do pobrania w programie .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="42506-121">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="42506-122">Tę aplikację można uruchomić w systemie Windows, Linux, macOS lub w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="42506-122">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="42506-123">Musisz zainstalować swój ulubiony Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="42506-123">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="42506-124">Poniższe opisy wykorzystują [Visual Studio Code](https://code.visualstudio.com/), czyli edytor Międzyplatformowy.</span><span class="sxs-lookup"><span data-stu-id="42506-124">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="42506-125">Można jednak korzystać z dowolnych narzędzi, z którymi masz doświadczenie.</span><span class="sxs-lookup"><span data-stu-id="42506-125">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="42506-126">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="42506-126">Create the Application</span></span>

<span data-ttu-id="42506-127">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42506-127">The first step is to create a new application.</span></span> <span data-ttu-id="42506-128">Otwórz wiersz polecenia i Utwórz nowy katalog dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42506-128">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="42506-129">Upewnij się, że bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="42506-129">Make that the current directory.</span></span> <span data-ttu-id="42506-130">W oknie konsoli wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="42506-130">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebAPIClient
```

<span data-ttu-id="42506-131">Spowoduje to utworzenie plików początkowych dla podstawowej aplikacji "Hello world".</span><span class="sxs-lookup"><span data-stu-id="42506-131">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="42506-132">Nazwa projektu to "WebAPIClient".</span><span class="sxs-lookup"><span data-stu-id="42506-132">The project name is "WebAPIClient".</span></span> <span data-ttu-id="42506-133">Ponieważ jest to nowy projekt, żadne zależności nie są stosowane.</span><span class="sxs-lookup"><span data-stu-id="42506-133">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="42506-134">Pierwsze uruchomienie spowoduje pobranie platformy .NET Core, zainstalowanie certyfikatu deweloperskiego i uruchomienie Menedżera pakietów NuGet w celu przywrócenia brakujących zależności.</span><span class="sxs-lookup"><span data-stu-id="42506-134">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="42506-135">Przed rozpoczęciem wprowadzania modyfikacji wpisz `dotnet run` ([Zobacz Uwaga](#dotnet-restore-note)) w wierszu polecenia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="42506-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="42506-136">`dotnet run`wykonuje automatycznie, `dotnet restore` Jeśli w środowisku nie ma zależności.</span><span class="sxs-lookup"><span data-stu-id="42506-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="42506-137">Wykonuje również, `dotnet build` Jeśli aplikacja musi zostać odbudowana.</span><span class="sxs-lookup"><span data-stu-id="42506-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="42506-138">Po wstępnej konfiguracji wystarczy uruchomić program `dotnet restore` lub tylko `dotnet build` wtedy, gdy jest to zrozumiałe dla projektu.</span><span class="sxs-lookup"><span data-stu-id="42506-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="42506-139">Dodawanie nowych zależności</span><span class="sxs-lookup"><span data-stu-id="42506-139">Adding New Dependencies</span></span>

<span data-ttu-id="42506-140">Jednym z kluczowych celów projektowych dla platformy .NET Core jest Minimalizacja rozmiaru instalacji programu .NET.</span><span class="sxs-lookup"><span data-stu-id="42506-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="42506-141">Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych funkcji, należy dodać te zależności do pliku projektu C# ( \* . csproj).</span><span class="sxs-lookup"><span data-stu-id="42506-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="42506-142">Na potrzeby tego przykładu należy dodać `System.Runtime.Serialization.Json` pakiet, aby aplikacja mogła przetwarzać odpowiedzi JSON.</span><span class="sxs-lookup"><span data-stu-id="42506-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="42506-143">Wymagany jest `System.Runtime.Serialization.Json` pakiet dla tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42506-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="42506-144">Dodaj go do projektu, uruchamiając następujące polecenie [interfejsu wiersza polecenia platformy .NET](../../core/tools/dotnet-add-package.md) :</span><span class="sxs-lookup"><span data-stu-id="42506-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="42506-145">Tworzenie żądań sieci Web</span><span class="sxs-lookup"><span data-stu-id="42506-145">Making Web Requests</span></span>

<span data-ttu-id="42506-146">Teraz wszystko jest gotowe do rozpoczęcia pobierania danych z sieci Web.</span><span class="sxs-lookup"><span data-stu-id="42506-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="42506-147">W tej aplikacji należy przeczytać informacje z [interfejsu API usługi GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="42506-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="42506-148">Zapoznajmy się z informacjami na temat projektów w ramach parasola [.NET Foundation](https://www.dotnetfoundation.org/) .</span><span class="sxs-lookup"><span data-stu-id="42506-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="42506-149">Zacznij od wprowadzenia żądania do interfejsu API usługi GitHub w celu pobrania informacji o projektach.</span><span class="sxs-lookup"><span data-stu-id="42506-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="42506-150">Używany punkt końcowy to: <https://api.github.com/orgs/dotnet/repos> .</span><span class="sxs-lookup"><span data-stu-id="42506-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="42506-151">Chcesz pobrać wszystkie informacje o tych projektach, aby użyć żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="42506-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="42506-152">Przeglądarka korzysta również z żądań HTTP GET, dlatego można wkleić ten adres URL do przeglądarki, aby zobaczyć, jakie informacje będą odbierane i przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="42506-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="42506-153">Użyj klasy, <xref:System.Net.Http.HttpClient> Aby wykonywać żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="42506-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="42506-154">Podobnie jak w przypadku wszystkich nowoczesnych interfejsów API platformy .NET, <xref:System.Net.Http.HttpClient> obsługiwane są tylko metody asynchroniczne dla długotrwałych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="42506-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="42506-155">Zacznij od wprowadzenia metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="42506-155">Start by making an async method.</span></span> <span data-ttu-id="42506-156">Wdrożenie jest wypełniane podczas tworzenia funkcjonalności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42506-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="42506-157">Najpierw Otwórz `program.cs` plik w katalogu projektu i Dodaj następującą metodę do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="42506-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="42506-158">Należy dodać `using` dyrektywę u góry `Main` metody, aby kompilator języka C# rozpoznał <xref:System.Threading.Tasks.Task> Typ:</span><span class="sxs-lookup"><span data-stu-id="42506-158">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="42506-159">Jeśli tworzysz projekt w tym momencie, otrzymasz ostrzeżenie wygenerowane dla tej metody, ponieważ nie zawiera ona żadnych `await` operatorów i zostanie uruchomiony synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="42506-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="42506-160">Zignoruj to teraz; Operatory należy dodać podczas `await` wypełniania.</span><span class="sxs-lookup"><span data-stu-id="42506-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="42506-161">Następnie zaktualizuj metodę, `Main` Aby wywołać `ProcessRepositories` metodę.</span><span class="sxs-lookup"><span data-stu-id="42506-161">Next, update the `Main` method to call the `ProcessRepositories` method.</span></span> <span data-ttu-id="42506-162">`ProcessRepositories`Metoda zwraca zadanie i nie należy zamykać programu przed zakończeniem tego zadania.</span><span class="sxs-lookup"><span data-stu-id="42506-162">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="42506-163">W związku z tym należy zmienić sygnaturę `Main` .</span><span class="sxs-lookup"><span data-stu-id="42506-163">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="42506-164">Dodaj `async` modyfikator i Zmień zwracany typ na `Task` .</span><span class="sxs-lookup"><span data-stu-id="42506-164">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="42506-165">Następnie w treści metody Dodaj wywołanie do `ProcessRepositories` .</span><span class="sxs-lookup"><span data-stu-id="42506-165">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="42506-166">Dodaj `await` słowo kluczowe do tego wywołania metody:</span><span class="sxs-lookup"><span data-stu-id="42506-166">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="42506-167">Teraz masz program, który nic nie robi, ale robi to asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="42506-167">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="42506-168">Ulepszamy go.</span><span class="sxs-lookup"><span data-stu-id="42506-168">Let's improve it.</span></span>

<span data-ttu-id="42506-169">Najpierw wymagany jest obiekt, który może pobrać dane z sieci Web; Możesz użyć, <xref:System.Net.Http.HttpClient> Aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="42506-169">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="42506-170">Ten obiekt obsługuje żądanie i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="42506-170">This object handles the request and the responses.</span></span> <span data-ttu-id="42506-171">Utwórz wystąpienie pojedynczego wystąpienia tego typu w `Program` klasie wewnątrz pliku *program.cs* .</span><span class="sxs-lookup"><span data-stu-id="42506-171">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

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

<span data-ttu-id="42506-172">Wróćmy do `ProcessRepositories` metody i wypełnimy ją pierwszą wersją:</span><span class="sxs-lookup"><span data-stu-id="42506-172">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="42506-173">Należy również dodać dwie nowe `using` dyrektywy w górnej części pliku do skompilowania:</span><span class="sxs-lookup"><span data-stu-id="42506-173">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="42506-174">Ta pierwsza wersja wysyła żądanie sieci Web w celu odczytania listy wszystkich repozytoriów w ramach organizacji programu dotnet Foundation.</span><span class="sxs-lookup"><span data-stu-id="42506-174">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="42506-175">(Identyfikator gitHub dla platformy .NET Foundation to "dotnet").</span><span class="sxs-lookup"><span data-stu-id="42506-175">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="42506-176">Pierwsze kilka wierszy zostało skonfigurowanych <xref:System.Net.Http.HttpClient> dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="42506-176">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="42506-177">Najpierw jest skonfigurowany do akceptowania odpowiedzi JSON usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="42506-177">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="42506-178">Ten format jest po prostu kod JSON.</span><span class="sxs-lookup"><span data-stu-id="42506-178">This format is simply JSON.</span></span> <span data-ttu-id="42506-179">Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="42506-179">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="42506-180">Te dwa nagłówki są sprawdzane przez kod serwera usługi GitHub i są niezbędne do pobierania informacji z usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="42506-180">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="42506-181">Po skonfigurowaniu programu należy <xref:System.Net.Http.HttpClient> utworzyć żądanie sieci Web i pobrać odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="42506-181">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="42506-182">W tej pierwszej wersji jest używana <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> wygodna metoda.</span><span class="sxs-lookup"><span data-stu-id="42506-182">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="42506-183">Ta wygodna metoda uruchamia zadanie, które wykonuje żądanie sieci Web, a następnie po powrocie żądania odczytuje strumień odpowiedzi i wyodrębnia zawartość ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="42506-183">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="42506-184">Treść odpowiedzi jest zwracana jako <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="42506-184">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="42506-185">Ten ciąg jest dostępny po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="42506-185">The string is available when the task completes.</span></span>

<span data-ttu-id="42506-186">Ostatnie dwie wiersze tej metody oczekują na zadanie, a następnie drukują odpowiedź do konsoli.</span><span class="sxs-lookup"><span data-stu-id="42506-186">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="42506-187">Skompiluj aplikację i uruchom ją.</span><span class="sxs-lookup"><span data-stu-id="42506-187">Build the app, and run it.</span></span> <span data-ttu-id="42506-188">Ostrzeżenie kompilacji pozostanie teraz, ponieważ `ProcessRepositories` teraz zawiera `await` operator.</span><span class="sxs-lookup"><span data-stu-id="42506-188">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="42506-189">Zobaczysz długi sposób wyświetlania tekstu sformatowanego w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="42506-189">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="42506-190">Przetwarzanie wyniku JSON</span><span class="sxs-lookup"><span data-stu-id="42506-190">Processing the JSON Result</span></span>

<span data-ttu-id="42506-191">W tym momencie napisano kod umożliwiający pobranie odpowiedzi z serwera sieci Web i wyświetlenie tekstu zawartego w tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="42506-191">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="42506-192">Następnie przekonwertujmy tę odpowiedź JSON na obiekty języka C#.</span><span class="sxs-lookup"><span data-stu-id="42506-192">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="42506-193"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>Klasa serializować obiekty do formatu JSON i deserializacji kod JSON w obiektach.</span><span class="sxs-lookup"><span data-stu-id="42506-193">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="42506-194">Zacznij od zdefiniowania klasy, która będzie reprezentować `repo` obiekt JSON zwrócony z interfejsu API usługi GitHub:</span><span class="sxs-lookup"><span data-stu-id="42506-194">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

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

<span data-ttu-id="42506-195">Umieść powyższy kod w nowym pliku o nazwie "repo. cs".</span><span class="sxs-lookup"><span data-stu-id="42506-195">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="42506-196">Ta wersja klasy reprezentuje najprostszą ścieżkę do przetwarzania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="42506-196">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="42506-197">Nazwa klasy i nazwa elementu członkowskiego są zgodne z nazwami użytymi w pakiecie JSON, a nie następującymi konwencjami języka C#.</span><span class="sxs-lookup"><span data-stu-id="42506-197">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="42506-198">Aby naprawić ten problem, należy w późniejszym czasie dostarczyć pewne atrybuty konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="42506-198">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="42506-199">Ta klasa pokazuje kolejną ważną funkcję serializacji i deserializacji kodu JSON: nie wszystkie pola w pakiecie JSON są częścią tej klasy.</span><span class="sxs-lookup"><span data-stu-id="42506-199">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="42506-200">Serializator JSON zignoruje informacje, które nie są uwzględnione w używanym typie klasy.</span><span class="sxs-lookup"><span data-stu-id="42506-200">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="42506-201">Ta funkcja ułatwia tworzenie typów, które współpracują z tylko podzbiorem pól w pakiecie JSON.</span><span class="sxs-lookup"><span data-stu-id="42506-201">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="42506-202">Teraz, po utworzeniu typu, przyjrzyjmy go.</span><span class="sxs-lookup"><span data-stu-id="42506-202">Now that you've created the type, let's deserialize it.</span></span>

<span data-ttu-id="42506-203">Następnie użyjemy serializatora do przekonwertowania JSON na obiekty języka C#.</span><span class="sxs-lookup"><span data-stu-id="42506-203">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="42506-204">Zastąp wywołanie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> `ProcessRepositories` metody w metodzie następującymi wierszami:</span><span class="sxs-lookup"><span data-stu-id="42506-204">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="42506-205">Używane są nowe przestrzenie nazw, więc należy je dodać również na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="42506-205">You're using new namespaces, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Text.Json;
```

<span data-ttu-id="42506-206">Zwróć uwagę, że jesteś teraz używany <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> zamiast <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> .</span><span class="sxs-lookup"><span data-stu-id="42506-206">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="42506-207">Serializator używa strumienia zamiast ciągu jako źródła.</span><span class="sxs-lookup"><span data-stu-id="42506-207">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="42506-208">Wyjaśnimy kilka funkcji języka C#, które są używane w drugim wierszu poprzedniego fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="42506-208">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="42506-209">Pierwszy argument <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> jest `await` wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="42506-209">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="42506-210">(Pozostałe dwa parametry są opcjonalne i pomijane we fragmencie kodu). Wyrażenia await mogą pojawiać się niemal wszędzie w kodzie, nawet w przypadku, gdy tylko do tej pory są widoczne jako część instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="42506-210">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="42506-211">`Deserialize`Metoda jest *rodzajowa*, co oznacza, że należy podać argumenty typu dla rodzaju obiektów, które mają być tworzone na podstawie tekstu JSON.</span><span class="sxs-lookup"><span data-stu-id="42506-211">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="42506-212">W tym przykładzie jest deserializowany do `List<Repository>` , który jest innym obiektem ogólnym, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="42506-212">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="42506-213">`List<>`Klasa przechowuje kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="42506-213">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="42506-214">Argument typu deklaruje typ obiektów przechowywanych w obiekcie `List<>` .</span><span class="sxs-lookup"><span data-stu-id="42506-214">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="42506-215">Tekst JSON reprezentuje kolekcję obiektów repozytorium, więc argument type ma wartość `Repository` .</span><span class="sxs-lookup"><span data-stu-id="42506-215">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="42506-216">Prawie gotowe do tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="42506-216">You're almost done with this section.</span></span> <span data-ttu-id="42506-217">Teraz, gdy dane JSON zostały przekonwertowane na obiekty języka C#, użyjmy nazwy każdego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="42506-217">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="42506-218">Zastąp odczytane wiersze:</span><span class="sxs-lookup"><span data-stu-id="42506-218">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="42506-219">należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="42506-219">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="42506-220">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="42506-220">Compile and run the application.</span></span> <span data-ttu-id="42506-221">Spowoduje to wydrukowanie nazw repozytoriów, które są częścią programu .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="42506-221">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="42506-222">Kontrolowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="42506-222">Controlling Serialization</span></span>

<span data-ttu-id="42506-223">Zanim dodasz więcej funkcji, przyjrzyjmy się `name` właściwości przy użyciu `[JsonPropertyName]` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="42506-223">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="42506-224">Wprowadź następujące zmiany w deklaracji `name` pola w repo.cs:</span><span class="sxs-lookup"><span data-stu-id="42506-224">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="42506-225">Aby użyć `[JsonPropertyName]` atrybutu, należy dodać <xref:System.Text.Json.Serialization> przestrzeń nazw do `using` dyrektyw:</span><span class="sxs-lookup"><span data-stu-id="42506-225">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="42506-226">Ta zmiana oznacza, że należy zmienić kod, który zapisuje nazwę każdego repozytorium w program.cs:</span><span class="sxs-lookup"><span data-stu-id="42506-226">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="42506-227">Wykonaj `dotnet run` , aby upewnić się, że mapowania są poprawne.</span><span class="sxs-lookup"><span data-stu-id="42506-227">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="42506-228">Powinny zostać wyświetlone te same dane wyjściowe co poprzednio.</span><span class="sxs-lookup"><span data-stu-id="42506-228">You should see the same output as before.</span></span>

<span data-ttu-id="42506-229">Utwórzmy jeszcze jedną zmianę przed dodaniem nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="42506-229">Let's make one more change before adding new features.</span></span> <span data-ttu-id="42506-230">`ProcessRepositories`Metoda może wykonywać działania asynchroniczne i zwracać kolekcję repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="42506-230">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="42506-231">Wróćmy do tej `List<Repository>` metody i przeniesiesz kod, który zapisuje informacje w `Main` metodzie.</span><span class="sxs-lookup"><span data-stu-id="42506-231">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="42506-232">Zmień sygnaturę, `ProcessRepositories` aby zwracała zadanie, którego wynikiem jest lista `Repository` obiektów:</span><span class="sxs-lookup"><span data-stu-id="42506-232">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="42506-233">Następnie po przetworzeniu odpowiedzi JSON należy zwrócić repozytoria:</span><span class="sxs-lookup"><span data-stu-id="42506-233">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="42506-234">Kompilator generuje `Task<T>` obiekt do zwrócenia, ponieważ oznaczono tę metodę jako `async` .</span><span class="sxs-lookup"><span data-stu-id="42506-234">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="42506-235">Następnie zmodyfikujemy `Main` metodę, aby przechwycić te wyniki i zapisywali nazwy poszczególnych repozytoriów w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="42506-235">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="42506-236">`Main`Teraz Metoda wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="42506-236">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="42506-237">Odczytywanie dodatkowych informacji</span><span class="sxs-lookup"><span data-stu-id="42506-237">Reading More Information</span></span>

<span data-ttu-id="42506-238">Zakończmy to przez przetwarzanie kilku większej liczby właściwości w pakiecie JSON, które są wysyłane z interfejsu API usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="42506-238">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="42506-239">Nie chcesz dowiedzieć się, ale dodanie kilku właściwości spowoduje pokazanie kilku funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="42506-239">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="42506-240">Zacznijmy od dodania kilku prostych typów do `Repository` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="42506-240">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="42506-241">Dodaj te właściwości do tej klasy:</span><span class="sxs-lookup"><span data-stu-id="42506-241">Add these properties to that class:</span></span>

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

<span data-ttu-id="42506-242">Te właściwości mają wbudowane konwersje z typu ciąg (który zawiera pakiety JSON) do typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="42506-242">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="42506-243"><xref:System.Uri>Typ może być nowy dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="42506-243">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="42506-244">Reprezentuje identyfikator URI lub w tym przypadku adres URL.</span><span class="sxs-lookup"><span data-stu-id="42506-244">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="42506-245">W przypadku `Uri` `int` typów i, jeśli pakiet JSON zawiera dane, które nie są konwertowane na typ docelowy, Akcja serializacji zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="42506-245">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="42506-246">Po dodaniu tych elementów zaktualizuj metodę, `Main` Aby wyświetlić te elementy:</span><span class="sxs-lookup"><span data-stu-id="42506-246">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="42506-247">Ostatnim krokiem jest dodanie informacji dla ostatniej operacji wypychania.</span><span class="sxs-lookup"><span data-stu-id="42506-247">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="42506-248">Te informacje są sformatowane w ten sposób w odpowiedzi JSON:</span><span class="sxs-lookup"><span data-stu-id="42506-248">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="42506-249">Ten format jest w uniwersalnym czasie koordynowanym (UTC), aby uzyskać <xref:System.DateTime> wartość, której <xref:System.DateTime.Kind%2A> Właściwość jest <xref:System.DateTimeKind.Utc> .</span><span class="sxs-lookup"><span data-stu-id="42506-249">That format is in Coordinated Universal Time (UTC) so you'll get a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Utc>.</span></span> <span data-ttu-id="42506-250">Jeśli wolisz daty reprezentowanej w strefie czasowej, musisz napisać niestandardową metodę konwersji.</span><span class="sxs-lookup"><span data-stu-id="42506-250">If you prefer a date represented in your time zone, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="42506-251">Najpierw Zdefiniuj `public` Właściwość, która będzie zawierać reprezentację UTC daty i godziny w `Repository` klasie oraz `LastPush` `readonly` Właściwość zwracającą datę przekonwertowaną na czas lokalny:</span><span class="sxs-lookup"><span data-stu-id="42506-251">First, define a `public` property that will hold the UTC representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns the date converted to local time:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

<span data-ttu-id="42506-252">Przejdźmy do nowej konstrukcji, która została właśnie zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="42506-252">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="42506-253">`LastPush`Właściwość jest definiowana przy użyciu *składowej z wyrażeniami* dla `get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="42506-253">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="42506-254">Brak `set` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="42506-254">There is no `set` accessor.</span></span> <span data-ttu-id="42506-255">Pominięcie `set` metody dostępu oznacza sposób definiowania właściwości tylko do *odczytu* w języku C#.</span><span class="sxs-lookup"><span data-stu-id="42506-255">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="42506-256">(Tak, możesz tworzyć właściwości *tylko do zapisu* w języku C#, ale ich wartości są ograniczone).</span><span class="sxs-lookup"><span data-stu-id="42506-256">(Yes, you can create *write-only* properties in C#, but their value is limited.)</span></span>

<span data-ttu-id="42506-257">Na koniec Dodaj jedną instrukcję wyjściową w konsoli i wszystko jest gotowe do skompilowania i uruchomienia tej aplikacji ponownie:</span><span class="sxs-lookup"><span data-stu-id="42506-257">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="42506-258">Twoja wersja powinna teraz być zgodna z [Zakończono przykładem](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="42506-258">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="42506-259">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="42506-259">Conclusion</span></span>

<span data-ttu-id="42506-260">W tym samouczku pokazano, jak wykonywać żądania sieci Web, analizować wyniki i wyświetlać właściwości tych wyników.</span><span class="sxs-lookup"><span data-stu-id="42506-260">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="42506-261">Dodano również nowe pakiety jako zależności w projekcie.</span><span class="sxs-lookup"><span data-stu-id="42506-261">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="42506-262">Zaobserwowano niektóre funkcje języka C#, które obsługują techniki zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="42506-262">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
