---
title: Tworzenie klienta REST przy użyciu programu .NET Core
description: W tym samouczku nauczy Cię wiele funkcji w .NET Core i języku C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 5796df2d2fd8c4d9aaca783d720448c90858c067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156860"
---
# <a name="rest-client"></a><span data-ttu-id="f78c3-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="f78c3-103">REST client</span></span>

<span data-ttu-id="f78c3-104">W tym samouczku nauczy Cię wiele funkcji w .NET Core i języku C#.</span><span class="sxs-lookup"><span data-stu-id="f78c3-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="f78c3-105">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="f78c3-105">You’ll learn:</span></span>

* <span data-ttu-id="f78c3-106">Podstawy cli.NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="f78c3-106">The basics of the .NET Core CLI.</span></span>
* <span data-ttu-id="f78c3-107">An overview of C# Language features.</span><span class="sxs-lookup"><span data-stu-id="f78c3-107">An overview of C# Language features.</span></span>
* <span data-ttu-id="f78c3-108">Zarządzanie zależnościami za pomocą NuGet</span><span class="sxs-lookup"><span data-stu-id="f78c3-108">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="f78c3-109">Komunikacja HTTP</span><span class="sxs-lookup"><span data-stu-id="f78c3-109">HTTP Communications</span></span>
* <span data-ttu-id="f78c3-110">Przetwarzanie informacji JSON</span><span class="sxs-lookup"><span data-stu-id="f78c3-110">Processing JSON information</span></span>
* <span data-ttu-id="f78c3-111">Zarządzanie konfiguracją za pomocą atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f78c3-111">Managing configuration with Attributes.</span></span>

<span data-ttu-id="f78c3-112">Stworzysz aplikację, która wystawia żądania HTTP do usługi REST w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="f78c3-112">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="f78c3-113">Będziesz czytać informacje w formacie JSON i konwertować ten pakiet JSON do obiektów C#.</span><span class="sxs-lookup"><span data-stu-id="f78c3-113">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="f78c3-114">Na koniec zobaczysz, jak pracować z obiektami Języka C#.</span><span class="sxs-lookup"><span data-stu-id="f78c3-114">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="f78c3-115">Istnieje wiele funkcji w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="f78c3-115">There are many features in this tutorial.</span></span> <span data-ttu-id="f78c3-116">Budujmy je jeden po drugim.</span><span class="sxs-lookup"><span data-stu-id="f78c3-116">Let’s build them one by one.</span></span>

<span data-ttu-id="f78c3-117">Jeśli wolisz śledzić wraz z [końcowego przykładu](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) dla tego tematu, można go pobrać.</span><span class="sxs-lookup"><span data-stu-id="f78c3-117">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="f78c3-118">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="f78c3-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f78c3-119">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f78c3-119">Prerequisites</span></span>

<span data-ttu-id="f78c3-120">Musisz skonfigurować komputer do uruchamiania rdzenia .NET.</span><span class="sxs-lookup"><span data-stu-id="f78c3-120">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="f78c3-121">Instrukcje instalacji można znaleźć na stronie [pobierania .NET Core.](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="f78c3-121">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="f78c3-122">Tę aplikację można uruchomić w systemie Windows, Linux, macOS lub w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="f78c3-122">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="f78c3-123">Musisz zainstalować swój ulubiony edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="f78c3-123">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="f78c3-124">Poniższe opisy używają [kodu Visual Studio](https://code.visualstudio.com/), który jest edytorem open source, między platformami.</span><span class="sxs-lookup"><span data-stu-id="f78c3-124">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="f78c3-125">Możesz jednak użyć dowolnych narzędzi, które Ci się podobają.</span><span class="sxs-lookup"><span data-stu-id="f78c3-125">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="f78c3-126">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="f78c3-126">Create the Application</span></span>

<span data-ttu-id="f78c3-127">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f78c3-127">The first step is to create a new application.</span></span> <span data-ttu-id="f78c3-128">Otwórz wiersz polecenia i utwórz nowy katalog dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f78c3-128">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="f78c3-129">Upewnij się, że bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="f78c3-129">Make that the current directory.</span></span> <span data-ttu-id="f78c3-130">W oknie konsoli wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f78c3-130">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebApiClient
```

<span data-ttu-id="f78c3-131">Spowoduje to utworzenie plików startowych dla podstawowej aplikacji "Hello World".</span><span class="sxs-lookup"><span data-stu-id="f78c3-131">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="f78c3-132">Nazwa projektu to "WebApiClient".</span><span class="sxs-lookup"><span data-stu-id="f78c3-132">The project name is "WebApiClient".</span></span> <span data-ttu-id="f78c3-133">Ponieważ jest to nowy projekt, żadna z zależności nie są na miejscu.</span><span class="sxs-lookup"><span data-stu-id="f78c3-133">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="f78c3-134">Pierwsze uruchomienie spowoduje pobranie struktury .NET Core, zainstalowanie certyfikatu dewelopera i uruchomienie Menedżera pakietów NuGet w celu przywrócenia brakujących zależności.</span><span class="sxs-lookup"><span data-stu-id="f78c3-134">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="f78c3-135">Przed rozpoczęciem wprowadzania modyfikacji wpisz `dotnet run` [(patrz uwaga)](#dotnet-restore-note)w wierszu polecenia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="f78c3-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="f78c3-136">`dotnet run`automatycznie wykonuje, `dotnet restore` jeśli w środowisku brakuje zależności.</span><span class="sxs-lookup"><span data-stu-id="f78c3-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="f78c3-137">Wykonuje `dotnet build` również, jeśli aplikacja musi zostać przebudowany.</span><span class="sxs-lookup"><span data-stu-id="f78c3-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="f78c3-138">Po wstępnej konfiguracji należy tylko `dotnet restore` uruchomić `dotnet build` lub gdy ma to sens dla projektu.</span><span class="sxs-lookup"><span data-stu-id="f78c3-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="f78c3-139">Dodawanie nowych zależności</span><span class="sxs-lookup"><span data-stu-id="f78c3-139">Adding New Dependencies</span></span>

<span data-ttu-id="f78c3-140">Jednym z kluczowych celów projektowych programu .NET Core jest zminimalizowanie rozmiaru instalacji .NET.</span><span class="sxs-lookup"><span data-stu-id="f78c3-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="f78c3-141">Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych swoich funkcji, należy dodać te\*zależności do pliku projektu C# (csproj).</span><span class="sxs-lookup"><span data-stu-id="f78c3-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="f78c3-142">W naszym przykładzie musisz dodać `System.Runtime.Serialization.Json` pakiet, aby aplikacja mogła przetwarzać odpowiedzi JSON.</span><span class="sxs-lookup"><span data-stu-id="f78c3-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="f78c3-143">Potrzebny pakiet `System.Runtime.Serialization.Json` dla tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f78c3-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="f78c3-144">Dodaj go do projektu, uruchamiając następujące polecenie [.NET CLI:](../../core/tools/dotnet-add-package.md)</span><span class="sxs-lookup"><span data-stu-id="f78c3-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="f78c3-145">Składanie żądań internetowych</span><span class="sxs-lookup"><span data-stu-id="f78c3-145">Making Web Requests</span></span>

<span data-ttu-id="f78c3-146">Teraz możesz rozpocząć pobieranie danych z sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f78c3-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="f78c3-147">W tej aplikacji będziesz czytać informacje z [interfejsu API GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="f78c3-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="f78c3-148">Przeczytajmy informacje o projektach w ramach parasola [.NET Foundation.](https://www.dotnetfoundation.org/)</span><span class="sxs-lookup"><span data-stu-id="f78c3-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="f78c3-149">Rozpoczniesz od złożenia żądania do interfejsu API usługi GitHub w celu pobrania informacji o projektach.</span><span class="sxs-lookup"><span data-stu-id="f78c3-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="f78c3-150">Punkt końcowy, którego użyjesz, to: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="f78c3-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="f78c3-151">Chcesz pobrać wszystkie informacje o tych projektach, więc użyjesz żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="f78c3-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="f78c3-152">Przeglądarka korzysta również z żądań HTTP GET, dzięki czemu można wkleić ten adres URL do przeglądarki, aby zobaczyć, jakie informacje będziesz otrzymywać i przetwarzać.</span><span class="sxs-lookup"><span data-stu-id="f78c3-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="f78c3-153">Klasa służy <xref:System.Net.Http.HttpClient> do tworzenia żądań sieci web.</span><span class="sxs-lookup"><span data-stu-id="f78c3-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="f78c3-154">Podobnie jak wszystkie nowoczesne <xref:System.Net.Http.HttpClient> interfejsy API .NET obsługuje tylko metody asynchroniczne dla jego długotrwałych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="f78c3-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="f78c3-155">Zacznij od metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="f78c3-155">Start by making an async method.</span></span> <span data-ttu-id="f78c3-156">Będziesz wypełnić implementacji podczas tworzenia funkcji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f78c3-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="f78c3-157">Rozpocznij `program.cs` od otwarcia pliku w katalogu projektu `Program` i dodania następującej metody do klasy:</span><span class="sxs-lookup"><span data-stu-id="f78c3-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="f78c3-158">Należy dodać dyrektywy `using` w górnej części `Main` metody, tak aby kompilator C# rozpoznaje <xref:System.Threading.Tasks.Task> typ:</span><span class="sxs-lookup"><span data-stu-id="f78c3-158">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="f78c3-159">Jeśli tworzysz projekt w tym momencie, otrzymasz ostrzeżenie wygenerowane dla tej metody, ponieważ nie zawiera żadnych `await` operatorów i będzie działać synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="f78c3-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="f78c3-160">Ignoruj to na razie; operatory dodasz `await` podczas wypełniania metody.</span><span class="sxs-lookup"><span data-stu-id="f78c3-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="f78c3-161">Następnie zmień nazwę obszaru nazw zdefiniowanego `namespace` w instrukcji `ConsoleApp` `WebAPIClient`z domyślnej wartości do .</span><span class="sxs-lookup"><span data-stu-id="f78c3-161">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="f78c3-162">Później zdefiniujemy `repo` klasę w tym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="f78c3-162">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="f78c3-163">Następnie zaktualizuj `Main` metodę wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="f78c3-163">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="f78c3-164">Metoda `ProcessRepositories` zwraca zadanie i nie należy zamykać programu przed zakończeniem tego zadania.</span><span class="sxs-lookup"><span data-stu-id="f78c3-164">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="f78c3-165">W związku z tym `Main`należy zmienić podpis .</span><span class="sxs-lookup"><span data-stu-id="f78c3-165">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="f78c3-166">Dodaj `async` modyfikator i zmień `Task`typ powrotu na .</span><span class="sxs-lookup"><span data-stu-id="f78c3-166">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="f78c3-167">Następnie w treści metody dodaj wywołanie `ProcessRepositories`do .</span><span class="sxs-lookup"><span data-stu-id="f78c3-167">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="f78c3-168">Dodaj `await` słowo kluczowe do tego wywołania metody:</span><span class="sxs-lookup"><span data-stu-id="f78c3-168">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="f78c3-169">Teraz masz program, który nic nie robi, ale robi to asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="f78c3-169">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="f78c3-170">Poprawmy to.</span><span class="sxs-lookup"><span data-stu-id="f78c3-170">Let's improve it.</span></span>

<span data-ttu-id="f78c3-171">Najpierw potrzebny jest obiekt, który jest w stanie pobrać dane z sieci Web; można użyć, <xref:System.Net.Http.HttpClient> aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="f78c3-171">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="f78c3-172">Ten obiekt obsługuje żądania i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f78c3-172">This object handles the request and the responses.</span></span> <span data-ttu-id="f78c3-173">Wystąpienia pojedynczego wystąpienia tego typu w `Program` klasie wewnątrz pliku *Program.cs.*</span><span class="sxs-lookup"><span data-stu-id="f78c3-173">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

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

<span data-ttu-id="f78c3-174">Wróćmy do `ProcessRepositories` metody i wypełnijmy jej pierwszą wersję:</span><span class="sxs-lookup"><span data-stu-id="f78c3-174">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="f78c3-175">Musisz również dodać dwie nowe `using` dyrektywy w górnej części pliku, aby to skompilować:</span><span class="sxs-lookup"><span data-stu-id="f78c3-175">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="f78c3-176">Ta pierwsza wersja sprawia, że żądanie sieci Web do odczytu listy wszystkich repozytoriów w organizacji fundacji dotnet.</span><span class="sxs-lookup"><span data-stu-id="f78c3-176">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="f78c3-177">(Identyfikator gitHub dla .NET Foundation to "dotnet").</span><span class="sxs-lookup"><span data-stu-id="f78c3-177">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="f78c3-178">Kilka pierwszych wierszy <xref:System.Net.Http.HttpClient> skonfigurować dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="f78c3-178">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="f78c3-179">Po pierwsze jest skonfigurowany do akceptowania odpowiedzi JSON GitHub.</span><span class="sxs-lookup"><span data-stu-id="f78c3-179">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="f78c3-180">Ten format jest po prostu JSON.</span><span class="sxs-lookup"><span data-stu-id="f78c3-180">This format is simply JSON.</span></span> <span data-ttu-id="f78c3-181">Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f78c3-181">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="f78c3-182">Te dwa nagłówki są sprawdzane przez kod serwera GitHub i są niezbędne do pobierania informacji z usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="f78c3-182">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="f78c3-183">Po skonfigurowaniu <xref:System.Net.Http.HttpClient>żądania sieci Web i pobrania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f78c3-183">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="f78c3-184">W tej pierwszej wersji <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> należy użyć metody wygody.</span><span class="sxs-lookup"><span data-stu-id="f78c3-184">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="f78c3-185">Ta metoda wygody uruchamia zadanie, które sprawia, że żądanie sieci web, a następnie po zwróceniu żądania odczytuje strumień odpowiedzi i wyodrębnia zawartość ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="f78c3-185">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="f78c3-186">Treść odpowiedzi jest zwracana jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f78c3-186">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="f78c3-187">Ciąg jest dostępny po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="f78c3-187">The string is available when the task completes.</span></span>

<span data-ttu-id="f78c3-188">Ostatnie dwa wiersze tej metody czekają na to zadanie, a następnie wydrukuj odpowiedź do konsoli.</span><span class="sxs-lookup"><span data-stu-id="f78c3-188">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="f78c3-189">Skompiluj aplikację i uruchom ją.</span><span class="sxs-lookup"><span data-stu-id="f78c3-189">Build the app, and run it.</span></span> <span data-ttu-id="f78c3-190">Ostrzeżenie kompilacji już nie `ProcessRepositories` ma, ponieważ `await` teraz zawiera operator.</span><span class="sxs-lookup"><span data-stu-id="f78c3-190">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="f78c3-191">Zobaczysz długi wyświetlacz tekstu sformatowanego przez JSON.</span><span class="sxs-lookup"><span data-stu-id="f78c3-191">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="f78c3-192">Przetwarzanie wyniku JSON</span><span class="sxs-lookup"><span data-stu-id="f78c3-192">Processing the JSON Result</span></span>

<span data-ttu-id="f78c3-193">W tym momencie został napisany kod, aby pobrać odpowiedź z serwera sieci web i wyświetlić tekst, który jest zawarty w tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f78c3-193">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="f78c3-194">Następnie przekonwertujmy tę odpowiedź JSON na obiekty Języka C#.</span><span class="sxs-lookup"><span data-stu-id="f78c3-194">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="f78c3-195">Klasa <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializuje obiekty do JSON i deserializuje JSON do obiektów.</span><span class="sxs-lookup"><span data-stu-id="f78c3-195">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="f78c3-196">Rozpocznij od zdefiniowania klasy do reprezentowania `repo` obiektu JSON zwróconego z interfejsu API GitHub:</span><span class="sxs-lookup"><span data-stu-id="f78c3-196">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

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

<span data-ttu-id="f78c3-197">Umieść powyższy kod w nowym pliku o nazwie 'repo.cs'.</span><span class="sxs-lookup"><span data-stu-id="f78c3-197">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="f78c3-198">Ta wersja klasy reprezentuje najprostszą ścieżkę do przetwarzania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="f78c3-198">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="f78c3-199">Nazwa klasy i nazwa elementu członkowskiego są zgodne z nazwami używanymi w pakiecie JSON, zamiast przestrzegać konwencji Języka C#.</span><span class="sxs-lookup"><span data-stu-id="f78c3-199">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="f78c3-200">Naprawisz to, podając niektóre atrybuty konfiguracji później.</span><span class="sxs-lookup"><span data-stu-id="f78c3-200">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="f78c3-201">Ta klasa pokazuje inną ważną cechą serializacji JSON i deserializacji: Nie wszystkie pola w pakiecie JSON są częścią tej klasy.</span><span class="sxs-lookup"><span data-stu-id="f78c3-201">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="f78c3-202">Serializator JSON zignoruje informacje, które nie są uwzględnione w typie klasy używane.</span><span class="sxs-lookup"><span data-stu-id="f78c3-202">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="f78c3-203">Ta funkcja ułatwia tworzenie typów, które działają tylko z podzbiorem pól w pakiecie JSON.</span><span class="sxs-lookup"><span data-stu-id="f78c3-203">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="f78c3-204">Teraz, gdy został utworzony typ, niech deserialize go.</span><span class="sxs-lookup"><span data-stu-id="f78c3-204">Now that you've created the type, let's deserialize it.</span></span>

<span data-ttu-id="f78c3-205">Następnie użyjesz serializatora do konwersji JSON na obiekty Języka C#.</span><span class="sxs-lookup"><span data-stu-id="f78c3-205">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="f78c3-206">Zastąp <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> wywołanie w metodzie `ProcessRepositories` następującymi trzema wierszami:</span><span class="sxs-lookup"><span data-stu-id="f78c3-206">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following three lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="f78c3-207">Używasz nowego obszaru nazw, więc musisz dodać go również w górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="f78c3-207">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="f78c3-208">Zwróć uwagę, że <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> używasz <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>teraz zamiast .</span><span class="sxs-lookup"><span data-stu-id="f78c3-208">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="f78c3-209">Serializator używa strumienia zamiast ciągu jako źródła.</span><span class="sxs-lookup"><span data-stu-id="f78c3-209">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="f78c3-210">Wyjaśnijmy kilka funkcji języka C#, które są używane w drugim wierszu poprzedniego fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="f78c3-210">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="f78c3-211">Pierwszy argument <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> jest `await` wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="f78c3-211">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="f78c3-212">(Pozostałe dwa parametry są opcjonalne i są pomijane we fragmencie kodu). Await wyrażenia mogą pojawić się prawie w dowolnym miejscu w kodzie, nawet jeśli do tej pory, widziałeś je tylko jako część instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="f78c3-212">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="f78c3-213">Metoda `Deserialize` jest *ogólna*, co oznacza, że należy podać argumenty typu dla jakiego rodzaju obiektów powinny być tworzone z tekstu JSON.</span><span class="sxs-lookup"><span data-stu-id="f78c3-213">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="f78c3-214">W tym przykładzie deserializing do `List<Repository>`, który jest inny <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>obiekt ogólny, .</span><span class="sxs-lookup"><span data-stu-id="f78c3-214">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f78c3-215">Klasa `List<>` przechowuje kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="f78c3-215">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="f78c3-216">Argument typu deklaruje typ obiektów przechowywanych `List<>`w pliku .</span><span class="sxs-lookup"><span data-stu-id="f78c3-216">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="f78c3-217">Tekst JSON reprezentuje kolekcję obiektów repo, więc `Repository`argument typu jest .</span><span class="sxs-lookup"><span data-stu-id="f78c3-217">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="f78c3-218">Prawie skończyłeś z tą sekcją.</span><span class="sxs-lookup"><span data-stu-id="f78c3-218">You're almost done with this section.</span></span> <span data-ttu-id="f78c3-219">Teraz, gdy zostały przekonwertowane JSON do C# obiektów, niech wyświetlić nazwę każdego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="f78c3-219">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="f78c3-220">Zamień wiersze, które brzmią:</span><span class="sxs-lookup"><span data-stu-id="f78c3-220">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="f78c3-221">z następującymi:</span><span class="sxs-lookup"><span data-stu-id="f78c3-221">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="f78c3-222">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="f78c3-222">Compile and run the application.</span></span> <span data-ttu-id="f78c3-223">Spowoduje to wydrukowanie nazw repozytoriów, które są częścią .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="f78c3-223">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="f78c3-224">Kontrolowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="f78c3-224">Controlling Serialization</span></span>

<span data-ttu-id="f78c3-225">Przed dodaniem więcej funkcji, niech adres `name` `[JsonPropertyName]` właściwości przy użyciu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f78c3-225">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="f78c3-226">Wprowadzić następujące zmiany w deklaracji `name` pola w repo.cs:</span><span class="sxs-lookup"><span data-stu-id="f78c3-226">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="f78c3-227">Aby `[JsonPropertyName]` użyć atrybutu, należy <xref:System.Text.Json.Serialization> dodać obszar `using` nazw do dyrektyw:</span><span class="sxs-lookup"><span data-stu-id="f78c3-227">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="f78c3-228">Ta zmiana oznacza, że musisz zmienić kod, który zapisuje nazwę każdego repozytorium w program.cs:</span><span class="sxs-lookup"><span data-stu-id="f78c3-228">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="f78c3-229">Wykonaj, `dotnet run` aby upewnić się, że mapowania są poprawne.</span><span class="sxs-lookup"><span data-stu-id="f78c3-229">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="f78c3-230">Powinien zostać wyświetlony te same dane wyjściowe, jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="f78c3-230">You should see the same output as before.</span></span>

<span data-ttu-id="f78c3-231">Przed dodaniem nowych funkcji dokonajmy jeszcze jednej zmiany.</span><span class="sxs-lookup"><span data-stu-id="f78c3-231">Let's make one more change before adding new features.</span></span> <span data-ttu-id="f78c3-232">Metoda `ProcessRepositories` może wykonać pracę asynchronicznej i zwrócić kolekcję repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="f78c3-232">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="f78c3-233">Wróćmy `List<Repository>` z tej metody i przenieść kod, który zapisuje `Main` informacje do metody.</span><span class="sxs-lookup"><span data-stu-id="f78c3-233">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="f78c3-234">Zmień `ProcessRepositories` podpis, aby zwrócić zadanie, którego `Repository` wynikiem jest lista obiektów:</span><span class="sxs-lookup"><span data-stu-id="f78c3-234">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="f78c3-235">Następnie po prostu zwróć repozytoria po przetworzeniu odpowiedzi JSON:</span><span class="sxs-lookup"><span data-stu-id="f78c3-235">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="f78c3-236">Kompilator generuje `Task<T>` obiekt dla zwracania, ponieważ oznaczono tę metodę jako `async`.</span><span class="sxs-lookup"><span data-stu-id="f78c3-236">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="f78c3-237">Następnie zmodyfikujmy `Main` metodę, aby przechwytywać te wyniki i zapisywać każdą nazwę repozytorium w konsoli.</span><span class="sxs-lookup"><span data-stu-id="f78c3-237">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="f78c3-238">Twoja `Main` metoda wygląda teraz następująco:</span><span class="sxs-lookup"><span data-stu-id="f78c3-238">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="f78c3-239">Czytanie więcej informacji</span><span class="sxs-lookup"><span data-stu-id="f78c3-239">Reading More Information</span></span>

<span data-ttu-id="f78c3-240">Zakończmy to, przetwarzając kilka więcej właściwości w pakiecie JSON, który jest wysyłany z interfejsu API GitHub.</span><span class="sxs-lookup"><span data-stu-id="f78c3-240">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="f78c3-241">Nie będzie chciał chwycić wszystko, ale dodanie kilku właściwości zademonstruje kilka funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="f78c3-241">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="f78c3-242">Zacznijmy od dodania kilku bardziej prostych `Repository` typów do definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="f78c3-242">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="f78c3-243">Dodaj te właściwości do tej klasy:</span><span class="sxs-lookup"><span data-stu-id="f78c3-243">Add these properties to that class:</span></span>

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

<span data-ttu-id="f78c3-244">Te właściwości mają wbudowane konwersje z typu ciągu (który jest to, co pakiety JSON zawierają) do typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f78c3-244">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="f78c3-245">Typ <xref:System.Uri> może być dla Ciebie nowy.</span><span class="sxs-lookup"><span data-stu-id="f78c3-245">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="f78c3-246">Reprezentuje identyfikator URI lub w tym przypadku adres URL.</span><span class="sxs-lookup"><span data-stu-id="f78c3-246">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="f78c3-247">W przypadku `Uri` i `int` typów, jeśli pakiet JSON zawiera dane, które nie konwertuje do typu docelowego, akcja serializacji spowoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f78c3-247">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="f78c3-248">Po dodaniu tych zaktualizuj `Main` metodę, aby wyświetlić te elementy:</span><span class="sxs-lookup"><span data-stu-id="f78c3-248">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="f78c3-249">Ostatnim krokiem jest dodawanie informacji dotyczących ostatniej operacji wypychania.</span><span class="sxs-lookup"><span data-stu-id="f78c3-249">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="f78c3-250">Informacje te są sformatowane w ten sposób w odpowiedzi JSON:</span><span class="sxs-lookup"><span data-stu-id="f78c3-250">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="f78c3-251">Ten format nie jest zgodny ze <xref:System.DateTime> standardowymi formatami .NET.</span><span class="sxs-lookup"><span data-stu-id="f78c3-251">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="f78c3-252">Z tego powodu musisz napisać niestandardową metodę konwersji.</span><span class="sxs-lookup"><span data-stu-id="f78c3-252">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="f78c3-253">Prawdopodobnie również nie chcesz, aby ciąg raw uwidocznił użytkowników `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="f78c3-253">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="f78c3-254">Atrybuty mogą pomóc kontrolować, że również.</span><span class="sxs-lookup"><span data-stu-id="f78c3-254">Attributes can help control that as well.</span></span> <span data-ttu-id="f78c3-255">`public` Najpierw zdefiniuj właściwość, która będzie przechowywać `Repository` reprezentację `LastPush` `readonly` ciągu daty i godziny w klasie oraz właściwość, która zwraca sformatowany ciąg reprezentujący zwróconą datę:</span><span class="sxs-lookup"><span data-stu-id="f78c3-255">First, define a `public` property that will hold the string representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns a formatted string that represents the returned date:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

<span data-ttu-id="f78c3-256">Przejdźmy do nowych konstrukcji, które właśnie zdefiniowaliśmy.</span><span class="sxs-lookup"><span data-stu-id="f78c3-256">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="f78c3-257">Właściwość `LastPush` jest zdefiniowana przy użyciu elementu `get` *członkowskiego zabudowane wyrażenie* dla akcesora.</span><span class="sxs-lookup"><span data-stu-id="f78c3-257">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="f78c3-258">Nie ma `set` akcesora.</span><span class="sxs-lookup"><span data-stu-id="f78c3-258">There is no `set` accessor.</span></span> <span data-ttu-id="f78c3-259">Pominięcie akcesorjest `set` jak zdefiniować właściwość tylko do *odczytu* w języku C#.</span><span class="sxs-lookup"><span data-stu-id="f78c3-259">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="f78c3-260">(Tak, można utworzyć właściwości tylko do *zapisu* w języku C#, ale ich wartość jest ograniczona). Metoda <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analizuje ciąg i tworzy <xref:System.DateTime> obiekt przy użyciu formatu podanych dat `DateTime` i `CultureInfo` dodaje dodatkowe metadane do przy użyciu obiektu.</span><span class="sxs-lookup"><span data-stu-id="f78c3-260">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="f78c3-261">Jeśli operacja analizy nie powiedzie się, akcesor właściwości zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f78c3-261">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="f78c3-262">Aby <xref:System.Globalization.CultureInfo.InvariantCulture>użyć , należy dodać <xref:System.Globalization> obszar nazw `using` do `repo.cs`dyrektyw w :</span><span class="sxs-lookup"><span data-stu-id="f78c3-262">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` directives in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="f78c3-263">Na koniec dodaj jeszcze jedną instrukcję danych wyjściowych w konsoli i możesz ponownie utworzyć i uruchomić tę aplikację:</span><span class="sxs-lookup"><span data-stu-id="f78c3-263">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="f78c3-264">Twoja wersja powinna teraz odpowiadać [gotowej próbce](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="f78c3-264">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="f78c3-265">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="f78c3-265">Conclusion</span></span>

<span data-ttu-id="f78c3-266">W tym samouczku pokazano, jak tworzyć żądania sieci Web, analizować wynik i wyświetlać właściwości tych wyników.</span><span class="sxs-lookup"><span data-stu-id="f78c3-266">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="f78c3-267">Dodano również nowe pakiety jako zależności w projekcie.</span><span class="sxs-lookup"><span data-stu-id="f78c3-267">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="f78c3-268">Widzieliście niektóre funkcje języka C#, które obsługują techniki obiektowe.</span><span class="sxs-lookup"><span data-stu-id="f78c3-268">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
