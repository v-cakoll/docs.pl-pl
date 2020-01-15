---
title: Tworzenie klienta REST przy użyciu platformy .NET Core
description: W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 9478966598a9aaa1e9f592b72afce8f878a38abf
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964410"
---
# <a name="rest-client"></a><span data-ttu-id="12441-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="12441-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="12441-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="12441-104">Introduction</span></span>

<span data-ttu-id="12441-105">W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka.</span><span class="sxs-lookup"><span data-stu-id="12441-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="12441-106">Omawiane tematy:</span><span class="sxs-lookup"><span data-stu-id="12441-106">You’ll learn:</span></span>

* <span data-ttu-id="12441-107">Podstawowe informacje o interfejsie wiersza polecenia (CLI) platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="12441-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
* <span data-ttu-id="12441-108">Omówienie funkcji C# języka.</span><span class="sxs-lookup"><span data-stu-id="12441-108">An overview of C# Language features.</span></span>
* <span data-ttu-id="12441-109">Zarządzanie zależnościami przy użyciu narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="12441-109">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="12441-110">HTTP Communications</span><span class="sxs-lookup"><span data-stu-id="12441-110">HTTP Communications</span></span>
* <span data-ttu-id="12441-111">Przetwarzanie informacji JSON</span><span class="sxs-lookup"><span data-stu-id="12441-111">Processing JSON information</span></span>
* <span data-ttu-id="12441-112">Zarządzanie konfiguracją przy użyciu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="12441-112">Managing configuration with Attributes.</span></span>

<span data-ttu-id="12441-113">Utworzysz aplikację, która wystawia żądania HTTP do usługi REST w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="12441-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="12441-114">Informacje są odczytywane w formacie JSON i konwertowane tego pakietu JSON na C# obiekty.</span><span class="sxs-lookup"><span data-stu-id="12441-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="12441-115">Na koniec zobaczysz, jak korzystać z C# obiektów.</span><span class="sxs-lookup"><span data-stu-id="12441-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="12441-116">Ten samouczek zawiera wiele funkcji.</span><span class="sxs-lookup"><span data-stu-id="12441-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="12441-117">Kompilujmy je po jednej.</span><span class="sxs-lookup"><span data-stu-id="12441-117">Let’s build them one by one.</span></span>

<span data-ttu-id="12441-118">Jeśli wolisz postępować wraz z [ostatnim przykładem](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) dla tego tematu, możesz go pobrać.</span><span class="sxs-lookup"><span data-stu-id="12441-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="12441-119">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="12441-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="12441-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="12441-120">Prerequisites</span></span>

<span data-ttu-id="12441-121">Musisz skonfigurować maszynę do uruchamiania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="12441-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="12441-122">Instrukcje instalacji można znaleźć na stronie [pliki do pobrania w programie .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="12441-122">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="12441-123">Tę aplikację można uruchomić w systemie Windows, Linux, macOS lub w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="12441-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="12441-124">Musisz zainstalować swój ulubiony Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="12441-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="12441-125">Poniższe opisy wykorzystują [Visual Studio Code](https://code.visualstudio.com/), czyli edytor Międzyplatformowy.</span><span class="sxs-lookup"><span data-stu-id="12441-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="12441-126">Można jednak korzystać z dowolnych narzędzi, z którymi masz doświadczenie.</span><span class="sxs-lookup"><span data-stu-id="12441-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="12441-127">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="12441-127">Create the Application</span></span>

<span data-ttu-id="12441-128">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="12441-128">The first step is to create a new application.</span></span> <span data-ttu-id="12441-129">Otwórz wiersz polecenia i Utwórz nowy katalog dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="12441-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="12441-130">Upewnij się, że bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="12441-130">Make that the current directory.</span></span> <span data-ttu-id="12441-131">W oknie konsoli wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="12441-131">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebApiClient
```

<span data-ttu-id="12441-132">Spowoduje to utworzenie plików początkowych dla podstawowej aplikacji "Hello world".</span><span class="sxs-lookup"><span data-stu-id="12441-132">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="12441-133">Nazwa projektu to "WebApiClient".</span><span class="sxs-lookup"><span data-stu-id="12441-133">The project name is "WebApiClient".</span></span> <span data-ttu-id="12441-134">Ponieważ jest to nowy projekt, nie są stosowane żadne zależności, więc pierwsze uruchomienie spowoduje pobranie platformy .NET Core, zainstalowanie certyfikatu deweloperskiego i uruchomienie Menedżera pakietów NuGet w celu przywrócenia brakujących zależności.</span><span class="sxs-lookup"><span data-stu-id="12441-134">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework, install a development certificate and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="12441-135">Przed rozpoczęciem wprowadzania modyfikacji wpisz `dotnet run` ([Zobacz Uwaga](#dotnet-restore-note)) w wierszu polecenia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="12441-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="12441-136">`dotnet run` automatycznie wykonuje `dotnet restore`, jeśli w środowisku nie ma zależności.</span><span class="sxs-lookup"><span data-stu-id="12441-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="12441-137">Wykonuje również `dotnet build`, jeśli aplikacja musi zostać odbudowana.</span><span class="sxs-lookup"><span data-stu-id="12441-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="12441-138">Po wstępnej konfiguracji wystarczy uruchomić `dotnet restore` lub `dotnet build`, gdy ma to sens dla projektu.</span><span class="sxs-lookup"><span data-stu-id="12441-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="12441-139">Dodawanie nowych zależności</span><span class="sxs-lookup"><span data-stu-id="12441-139">Adding New Dependencies</span></span>

<span data-ttu-id="12441-140">Jednym z kluczowych celów projektowych dla platformy .NET Core jest Minimalizacja rozmiaru instalacji programu .NET.</span><span class="sxs-lookup"><span data-stu-id="12441-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="12441-141">Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych funkcji, należy dodać te zależności do pliku C# projektu (\*. csproj).</span><span class="sxs-lookup"><span data-stu-id="12441-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="12441-142">Na potrzeby tego przykładu należy dodać pakiet `System.Runtime.Serialization.Json`, aby aplikacja mogła przetwarzać odpowiedzi JSON.</span><span class="sxs-lookup"><span data-stu-id="12441-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="12441-143">Wymagany jest pakiet `System.Runtime.Serialization.Json` dla tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="12441-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="12441-144">Dodaj go do projektu, uruchamiając następujące polecenie [interfejsu wiersza polecenia platformy .NET](../../core/tools/dotnet-add-package.md) :</span><span class="sxs-lookup"><span data-stu-id="12441-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```console
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="12441-145">Tworzenie żądań sieci Web</span><span class="sxs-lookup"><span data-stu-id="12441-145">Making Web Requests</span></span>

<span data-ttu-id="12441-146">Teraz wszystko jest gotowe do rozpoczęcia pobierania danych z sieci Web.</span><span class="sxs-lookup"><span data-stu-id="12441-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="12441-147">W tej aplikacji należy przeczytać informacje z [interfejsu API usługi GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="12441-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="12441-148">Zapoznajmy się z informacjami na temat projektów w ramach parasola [.NET Foundation](https://www.dotnetfoundation.org/) .</span><span class="sxs-lookup"><span data-stu-id="12441-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="12441-149">Zacznij od wprowadzenia żądania do interfejsu API usługi GitHub w celu pobrania informacji o projektach.</span><span class="sxs-lookup"><span data-stu-id="12441-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="12441-150">Używany punkt końcowy to: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="12441-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="12441-151">Chcesz pobrać wszystkie informacje o tych projektach, aby użyć żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="12441-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="12441-152">Przeglądarka korzysta również z żądań HTTP GET, dlatego można wkleić ten adres URL do przeglądarki, aby zobaczyć, jakie informacje będą odbierane i przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="12441-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="12441-153">Użyj klasy <xref:System.Net.Http.HttpClient>, aby wykonywać żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="12441-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="12441-154">Podobnie jak w przypadku wszystkich nowoczesnych interfejsów API platformy .NET, <xref:System.Net.Http.HttpClient> obsługuje tylko metody asynchroniczne dla długotrwałych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="12441-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="12441-155">Zacznij od wprowadzenia metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="12441-155">Start by making an async method.</span></span> <span data-ttu-id="12441-156">Wdrożenie jest wypełniane podczas tworzenia funkcjonalności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="12441-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="12441-157">Zacznij od otwarcia pliku `program.cs` w katalogu projektu i dodania następującej metody do klasy `Program`:</span><span class="sxs-lookup"><span data-stu-id="12441-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="12441-158">Musisz dodać instrukcję `using` w górnej części metody `Main`, aby C# kompilator rozpoznał <xref:System.Threading.Tasks.Task> typ:</span><span class="sxs-lookup"><span data-stu-id="12441-158">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="12441-159">W przypadku skompilowania projektu w tym momencie otrzymasz ostrzeżenie wygenerowane dla tej metody, ponieważ nie zawiera ona żadnych operatorów `await` i zostanie uruchomiona synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="12441-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="12441-160">Zignoruj to teraz; podczas wypełniania należy dodać operatory `await`.</span><span class="sxs-lookup"><span data-stu-id="12441-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="12441-161">Następnie zmień nazwę przestrzeni nazw zdefiniowanej w instrukcji `namespace` z jej domyślnego `ConsoleApp` na `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="12441-161">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="12441-162">W tej przestrzeni nazw będziemy później definiować klasy `repo`.</span><span class="sxs-lookup"><span data-stu-id="12441-162">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="12441-163">Następnie zaktualizuj metodę `Main`, aby wywołać tę metodę.</span><span class="sxs-lookup"><span data-stu-id="12441-163">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="12441-164">Metoda `ProcessRepositories` zwraca zadanie i nie należy zamykać programu przed zakończeniem tego zadania.</span><span class="sxs-lookup"><span data-stu-id="12441-164">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="12441-165">W związku z tym należy zmienić sygnaturę `Main`.</span><span class="sxs-lookup"><span data-stu-id="12441-165">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="12441-166">Dodaj modyfikator `async` i Zmień zwracany typ na `Task`.</span><span class="sxs-lookup"><span data-stu-id="12441-166">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="12441-167">Następnie w treści metody Dodaj wywołanie do `ProcessRepositories`.</span><span class="sxs-lookup"><span data-stu-id="12441-167">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="12441-168">Dodaj słowo kluczowe `await`, gdy to wywołanie metody:</span><span class="sxs-lookup"><span data-stu-id="12441-168">Add the `await` keyword when to that method call:</span></span>

```csharp
static Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="12441-169">Teraz masz program, który nic nie robi, ale robi to asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="12441-169">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="12441-170">Ulepszamy go.</span><span class="sxs-lookup"><span data-stu-id="12441-170">Let's improve it.</span></span>

<span data-ttu-id="12441-171">Najpierw wymagany jest obiekt, który może pobrać dane z sieci Web; Aby to zrobić, możesz użyć <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="12441-171">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="12441-172">Ten obiekt obsługuje żądanie i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="12441-172">This object handles the request and the responses.</span></span> <span data-ttu-id="12441-173">Utwórz wystąpienie pojedynczego wystąpienia tego typu w klasie `Program` w pliku Program.cs.</span><span class="sxs-lookup"><span data-stu-id="12441-173">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static Task Main(string[] args)
        {
            //...
        }
    }
}
```

<span data-ttu-id="12441-174">Wróćmy do metody `ProcessRepositories` i wypełnimy ją pierwszą wersją:</span><span class="sxs-lookup"><span data-stu-id="12441-174">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="12441-175">Należy również dodać dwie nowe instrukcje using na początku pliku do skompilowania:</span><span class="sxs-lookup"><span data-stu-id="12441-175">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="12441-176">Ta pierwsza wersja wysyła żądanie sieci Web w celu odczytania listy wszystkich repozytoriów w ramach organizacji programu dotnet Foundation.</span><span class="sxs-lookup"><span data-stu-id="12441-176">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="12441-177">(Identyfikator gitHub dla platformy .NET Foundation to "dotnet").</span><span class="sxs-lookup"><span data-stu-id="12441-177">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="12441-178">Pierwsze kilka wierszy skonfiguruje <xref:System.Net.Http.HttpClient> dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="12441-178">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="12441-179">Najpierw jest skonfigurowany do akceptowania odpowiedzi JSON usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="12441-179">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="12441-180">Ten format jest po prostu kod JSON.</span><span class="sxs-lookup"><span data-stu-id="12441-180">This format is simply JSON.</span></span> <span data-ttu-id="12441-181">Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="12441-181">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="12441-182">Te dwa nagłówki są sprawdzane przez kod serwera usługi GitHub i są niezbędne do pobierania informacji z usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="12441-182">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="12441-183">Po skonfigurowaniu <xref:System.Net.Http.HttpClient>należy utworzyć żądanie sieci Web i pobrać odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="12441-183">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="12441-184">W tej pierwszej wersji jest używana metoda <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> wygodna.</span><span class="sxs-lookup"><span data-stu-id="12441-184">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="12441-185">Ta wygodna metoda uruchamia zadanie, które wykonuje żądanie sieci Web, a następnie po powrocie żądania odczytuje strumień odpowiedzi i wyodrębnia zawartość ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="12441-185">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="12441-186">Treść odpowiedzi jest zwracana jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="12441-186">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="12441-187">Ten ciąg jest dostępny po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="12441-187">The string is available when the task completes.</span></span>

<span data-ttu-id="12441-188">Ostatnie dwie wiersze tej metody oczekują na zadanie, a następnie drukują odpowiedź do konsoli.</span><span class="sxs-lookup"><span data-stu-id="12441-188">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="12441-189">Skompiluj aplikację i uruchom ją.</span><span class="sxs-lookup"><span data-stu-id="12441-189">Build the app, and run it.</span></span> <span data-ttu-id="12441-190">Ostrzeżenie kompilacji teraz znikło, ponieważ `ProcessRepositories` teraz zawiera operator `await`.</span><span class="sxs-lookup"><span data-stu-id="12441-190">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="12441-191">Zobaczysz długi sposób wyświetlania tekstu sformatowanego w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="12441-191">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="12441-192">Przetwarzanie wyniku JSON</span><span class="sxs-lookup"><span data-stu-id="12441-192">Processing the JSON Result</span></span>

<span data-ttu-id="12441-193">W tym momencie napisano kod umożliwiający pobranie odpowiedzi z serwera sieci Web i wyświetlenie tekstu zawartego w tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="12441-193">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="12441-194">Następnie przekonwertujmy tę odpowiedź JSON na C# obiekty.</span><span class="sxs-lookup"><span data-stu-id="12441-194">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="12441-195">Klasa <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializować obiekty do formatu JSON i deserializacji kod JSON w obiektach.</span><span class="sxs-lookup"><span data-stu-id="12441-195">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="12441-196">Zacznij od zdefiniowania klasy, która będzie reprezentować `repo` obiekt JSON zwrócony z interfejsu API usługi GitHub:</span><span class="sxs-lookup"><span data-stu-id="12441-196">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; };
    }
}
```

<span data-ttu-id="12441-197">Umieść powyższy kod w nowym pliku o nazwie "repo. cs".</span><span class="sxs-lookup"><span data-stu-id="12441-197">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="12441-198">Ta wersja klasy reprezentuje najprostszą ścieżkę do przetwarzania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="12441-198">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="12441-199">Nazwa klasy i nazwa elementu członkowskiego są zgodne z nazwami użytymi w pakiecie JSON, a C# nie z następującymi konwencjami.</span><span class="sxs-lookup"><span data-stu-id="12441-199">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="12441-200">Aby naprawić ten problem, należy w późniejszym czasie dostarczyć pewne atrybuty konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="12441-200">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="12441-201">Ta klasa pokazuje kolejną ważną funkcję serializacji i deserializacji kodu JSON: nie wszystkie pola w pakiecie JSON są częścią tej klasy.</span><span class="sxs-lookup"><span data-stu-id="12441-201">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="12441-202">Serializator JSON zignoruje informacje, które nie są uwzględnione w używanym typie klasy.</span><span class="sxs-lookup"><span data-stu-id="12441-202">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="12441-203">Ta funkcja ułatwia tworzenie typów, które współpracują z tylko podzbiorem pól w pakiecie JSON.</span><span class="sxs-lookup"><span data-stu-id="12441-203">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="12441-204">Teraz, po utworzeniu typu, przyjrzyjmy go.</span><span class="sxs-lookup"><span data-stu-id="12441-204">Now that you've created the type, let's deserialize it.</span></span> 

<span data-ttu-id="12441-205">Następnie użyjesz serializatora, aby przekonwertować kod JSON na C# obiekty.</span><span class="sxs-lookup"><span data-stu-id="12441-205">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="12441-206">Zastąp wywołanie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> w metodzie `ProcessRepositories` następującymi trzema wierszami:</span><span class="sxs-lookup"><span data-stu-id="12441-206">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following three lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="12441-207">Używasz nowej przestrzeni nazw, więc musisz ją dodać również na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="12441-207">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="12441-208">Zwróć uwagę, że teraz używasz <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)>, a nie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="12441-208">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="12441-209">Serializator używa strumienia zamiast ciągu jako źródła.</span><span class="sxs-lookup"><span data-stu-id="12441-209">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="12441-210">Wyjaśnimy kilka funkcji C# języka, które są używane w drugim wierszu poprzedniego fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="12441-210">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="12441-211">Pierwszym argumentem <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> jest wyrażenie `await`.</span><span class="sxs-lookup"><span data-stu-id="12441-211">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="12441-212">(Pozostałe dwa parametry są opcjonalne i pomijane we fragmencie kodu). Wyrażenia await mogą pojawiać się niemal wszędzie w kodzie, nawet w przypadku, gdy tylko do tej pory są widoczne jako część instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="12441-212">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="12441-213">Metoda `Deserialize` jest *rodzajowa*, co oznacza, że należy podać argumenty typu dla rodzaju obiektów, które mają być tworzone na podstawie tekstu JSON.</span><span class="sxs-lookup"><span data-stu-id="12441-213">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="12441-214">W tym przykładzie Serializacja jest deserializowana do `List<Repository>`, który jest innym obiektem ogólnym, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="12441-214">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="12441-215">Klasa `List<>` przechowuje kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="12441-215">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="12441-216">Argument typu deklaruje typ obiektów przechowywanych w `List<>`.</span><span class="sxs-lookup"><span data-stu-id="12441-216">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="12441-217">Tekst JSON reprezentuje kolekcję obiektów repozytorium, więc argument typu jest `Repository`.</span><span class="sxs-lookup"><span data-stu-id="12441-217">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="12441-218">Prawie gotowe do tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="12441-218">You're almost done with this section.</span></span> <span data-ttu-id="12441-219">Teraz, gdy plik JSON został przekonwertowany C# do obiektów, zostanie wyświetlona nazwa każdego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="12441-219">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="12441-220">Zastąp odczytane wiersze:</span><span class="sxs-lookup"><span data-stu-id="12441-220">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="12441-221">należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="12441-221">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="12441-222">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="12441-222">Compile and run the application.</span></span> <span data-ttu-id="12441-223">Spowoduje to wydrukowanie nazw repozytoriów, które są częścią programu .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="12441-223">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="12441-224">Kontrolowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="12441-224">Controlling Serialization</span></span>

<span data-ttu-id="12441-225">Zanim dodasz więcej funkcji, przyjrzyjmy się `name` właściwości przy użyciu atrybutu `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="12441-225">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="12441-226">Wprowadź następujące zmiany w deklaracji pola `name` w repo.cs:</span><span class="sxs-lookup"><span data-stu-id="12441-226">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="12441-227">Ta zmiana oznacza, że należy zmienić kod, który zapisuje nazwę każdego repozytorium w program.cs:</span><span class="sxs-lookup"><span data-stu-id="12441-227">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="12441-228">Wykonaj `dotnet run`, aby upewnić się, że mapowania są poprawne.</span><span class="sxs-lookup"><span data-stu-id="12441-228">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="12441-229">Powinny zostać wyświetlone te same dane wyjściowe co poprzednio.</span><span class="sxs-lookup"><span data-stu-id="12441-229">You should see the same output as before.</span></span>

<span data-ttu-id="12441-230">Utwórzmy jeszcze jedną zmianę przed dodaniem nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="12441-230">Let's make one more change before adding new features.</span></span> <span data-ttu-id="12441-231">Metoda `ProcessRepositories` może wykonywać działania asynchroniczne i zwracać kolekcję repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="12441-231">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="12441-232">Zwróćmy `List<Repository>` z tej metody i przeniesiesz kod, który zapisuje informacje w metodzie `Main`.</span><span class="sxs-lookup"><span data-stu-id="12441-232">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="12441-233">Zmień sygnaturę `ProcessRepositories`, aby zwracała zadanie, którego wynikiem jest lista obiektów `Repository`:</span><span class="sxs-lookup"><span data-stu-id="12441-233">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="12441-234">Następnie po przetworzeniu odpowiedzi JSON należy zwrócić repozytoria:</span><span class="sxs-lookup"><span data-stu-id="12441-234">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="12441-235">Kompilator generuje obiekt `Task<T>` dla zwracanych, ponieważ oznaczono tę metodę jako `async`.</span><span class="sxs-lookup"><span data-stu-id="12441-235">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="12441-236">Następnie Zmodyfikujmy metodę `Main` tak, aby przechwytł te wyniki i zapisywali nazwy poszczególnych repozytoriów w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="12441-236">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="12441-237">Teraz Metoda `Main` wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="12441-237">Your `Main` method now looks like this:</span></span>

```csharp
public static Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="12441-238">Odczytywanie dodatkowych informacji</span><span class="sxs-lookup"><span data-stu-id="12441-238">Reading More Information</span></span>

<span data-ttu-id="12441-239">Zakończmy to przez przetwarzanie kilku większej liczby właściwości w pakiecie JSON, które są wysyłane z interfejsu API usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="12441-239">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="12441-240">Nie chcesz dowiedzieć się wszystkiego, ale dodanie kilku właściwości spowoduje pokazanie kilku funkcji C# języka.</span><span class="sxs-lookup"><span data-stu-id="12441-240">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="12441-241">Zacznijmy od dodania kilku prostych typów do definicji klasy `Repository`.</span><span class="sxs-lookup"><span data-stu-id="12441-241">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="12441-242">Dodaj te właściwości do tej klasy:</span><span class="sxs-lookup"><span data-stu-id="12441-242">Add these properties to that class:</span></span>

```csharp
[JsonPropertyName(Name="description")]
public string Description { get; set; }

[JsonPropertyName(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName(Name="homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName(Name="watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="12441-243">Te właściwości mają wbudowane konwersje z typu ciąg (który zawiera pakiety JSON) do typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="12441-243">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="12441-244">Typ <xref:System.Uri> może być nowy dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="12441-244">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="12441-245">Reprezentuje identyfikator URI lub w tym przypadku adres URL.</span><span class="sxs-lookup"><span data-stu-id="12441-245">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="12441-246">W przypadku typów `Uri` i `int`, jeśli pakiet JSON zawiera dane, które nie są konwertowane na typ docelowy, Akcja serializacji zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="12441-246">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="12441-247">Po dodaniu tych elementów zaktualizuj metodę `Main`, aby wyświetlić te elementy:</span><span class="sxs-lookup"><span data-stu-id="12441-247">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="12441-248">Ostatnim krokiem jest dodanie informacji dla ostatniej operacji wypychania.</span><span class="sxs-lookup"><span data-stu-id="12441-248">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="12441-249">Te informacje są sformatowane w ten sposób w odpowiedzi JSON:</span><span class="sxs-lookup"><span data-stu-id="12441-249">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="12441-250">Ten format nie jest zgodny z żadnym ze standardowych formatów programu .NET <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="12441-250">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="12441-251">Z tego powodu należy napisać niestandardową metodę konwersji.</span><span class="sxs-lookup"><span data-stu-id="12441-251">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="12441-252">Prawdopodobnie nie chcesz również, aby nieprzetworzony ciąg był widoczny dla użytkowników klasy `Repository`.</span><span class="sxs-lookup"><span data-stu-id="12441-252">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="12441-253">Atrybuty mogą również ułatwić kontrolę.</span><span class="sxs-lookup"><span data-stu-id="12441-253">Attributes can help control that as well.</span></span> <span data-ttu-id="12441-254">Najpierw Zdefiniuj `public` właściwość, która będzie przechowywać ciąg reprezentujący datę i godzinę w klasie `Repository` i Właściwość `LastPush` `readonly`, która zwraca sformatowany ciąg, który reprezentuje datę zwróconą:</span><span class="sxs-lookup"><span data-stu-id="12441-254">First, define a `public` property that will hold the string representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns a formatted string that represents the returned date:</span></span>

```csharp
[JsonPropertyName(Name="pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

<span data-ttu-id="12441-255">Przejdźmy do nowej konstrukcji, która została właśnie zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="12441-255">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="12441-256">Właściwość `LastPush` jest definiowana przy użyciu *składowej z wyrażeniami* dla metody dostępu `get`.</span><span class="sxs-lookup"><span data-stu-id="12441-256">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="12441-257">Brak metody dostępu `set`.</span><span class="sxs-lookup"><span data-stu-id="12441-257">There is no `set` accessor.</span></span> <span data-ttu-id="12441-258">Pomijanie metody dostępu `set` jest sposobem definiowania właściwości *tylko do odczytu* w C#.</span><span class="sxs-lookup"><span data-stu-id="12441-258">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="12441-259">(Tak, możesz tworzyć właściwości *tylko do zapisu* w C#, ale ich wartości są ograniczone). Metoda <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analizuje ciąg i tworzy obiekt <xref:System.DateTime> przy użyciu podanego formatu daty i dodaje dodatkowe metadane do `DateTime` przy użyciu obiektu `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="12441-259">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="12441-260">Jeśli operacja analizy zakończy się niepowodzeniem, metoda dostępu do właściwości zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="12441-260">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="12441-261">Aby użyć <xref:System.Globalization.CultureInfo.InvariantCulture>, należy dodać przestrzeń nazw <xref:System.Globalization> do instrukcji `using` w `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="12441-261">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="12441-262">Na koniec Dodaj jedną instrukcję wyjściową w konsoli i wszystko jest gotowe do skompilowania i uruchomienia tej aplikacji ponownie:</span><span class="sxs-lookup"><span data-stu-id="12441-262">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="12441-263">Twoja wersja powinna teraz być zgodna z [Zakończono przykładem](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="12441-263">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="12441-264">Wniosek</span><span class="sxs-lookup"><span data-stu-id="12441-264">Conclusion</span></span>

<span data-ttu-id="12441-265">W tym samouczku pokazano, jak wykonywać żądania sieci Web, analizować wyniki i wyświetlać właściwości tych wyników.</span><span class="sxs-lookup"><span data-stu-id="12441-265">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="12441-266">Dodano również nowe pakiety jako zależności w projekcie.</span><span class="sxs-lookup"><span data-stu-id="12441-266">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="12441-267">Zaobserwowano niektóre funkcje C# języka, które obsługują techniki zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="12441-267">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
