---
title: Tworzenie klienta REST przy użyciu programu .NET Core
description: W tym samouczku uczy się wielu funkcji w języku .NET Core i języku C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 0105db519f7accec6bf8bfbafdc6a67a444b1074
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249171"
---
# <a name="rest-client"></a><span data-ttu-id="1c17d-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="1c17d-103">REST client</span></span>

<span data-ttu-id="1c17d-104">W tym samouczku uczy się wielu funkcji w języku .NET Core i języku C#.</span><span class="sxs-lookup"><span data-stu-id="1c17d-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="1c17d-105">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="1c17d-105">You’ll learn:</span></span>

* <span data-ttu-id="1c17d-106">Podstawy interfejsu wiersza polecenia .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c17d-106">The basics of the .NET Core CLI.</span></span>
* <span data-ttu-id="1c17d-107">An overview of C# Language features.</span><span class="sxs-lookup"><span data-stu-id="1c17d-107">An overview of C# Language features.</span></span>
* <span data-ttu-id="1c17d-108">Zarządzanie zależnościami za pomocą nuget</span><span class="sxs-lookup"><span data-stu-id="1c17d-108">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="1c17d-109">Komunikacja HTTP</span><span class="sxs-lookup"><span data-stu-id="1c17d-109">HTTP Communications</span></span>
* <span data-ttu-id="1c17d-110">Przetwarzanie informacji JSON</span><span class="sxs-lookup"><span data-stu-id="1c17d-110">Processing JSON information</span></span>
* <span data-ttu-id="1c17d-111">Zarządzanie konfiguracją za pomocą atrybutów.</span><span class="sxs-lookup"><span data-stu-id="1c17d-111">Managing configuration with Attributes.</span></span>

<span data-ttu-id="1c17d-112">Będziesz tworzyć aplikację, która wystawia żądania HTTP do usługi REST w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="1c17d-112">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="1c17d-113">Będziesz czytać informacje w formacie JSON i konwertować ten pakiet JSON do obiektów języka C#.</span><span class="sxs-lookup"><span data-stu-id="1c17d-113">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="1c17d-114">Na koniec zobaczysz, jak pracować z obiektami języka C#.</span><span class="sxs-lookup"><span data-stu-id="1c17d-114">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="1c17d-115">Istnieje wiele funkcji w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="1c17d-115">There are many features in this tutorial.</span></span> <span data-ttu-id="1c17d-116">Zbudujmy je jeden po drugim.</span><span class="sxs-lookup"><span data-stu-id="1c17d-116">Let’s build them one by one.</span></span>

<span data-ttu-id="1c17d-117">Jeśli wolisz wykonać wraz z [próbką końcową](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) dla tego tematu, możesz go pobrać.</span><span class="sxs-lookup"><span data-stu-id="1c17d-117">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="1c17d-118">Aby uzyskać instrukcje pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="1c17d-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1c17d-119">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="1c17d-119">Prerequisites</span></span>

<span data-ttu-id="1c17d-120">Musisz skonfigurować komputer do uruchamiania .NET core.</span><span class="sxs-lookup"><span data-stu-id="1c17d-120">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="1c17d-121">Instrukcje instalacji można znaleźć na stronie [.NET Core Downloads.](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="1c17d-121">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="1c17d-122">Tę aplikację można uruchomić w systemach Windows, Linux, macOS lub w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="1c17d-122">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="1c17d-123">Musisz zainstalować swój ulubiony edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="1c17d-123">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="1c17d-124">Poniższe opisy używają [programu Visual Studio Code](https://code.visualstudio.com/), który jest edytorem open source, międzyplatformowym.</span><span class="sxs-lookup"><span data-stu-id="1c17d-124">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="1c17d-125">Możesz jednak użyć dowolnych narzędzi, z których czujesz się komfortowo.</span><span class="sxs-lookup"><span data-stu-id="1c17d-125">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="1c17d-126">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="1c17d-126">Create the Application</span></span>

<span data-ttu-id="1c17d-127">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1c17d-127">The first step is to create a new application.</span></span> <span data-ttu-id="1c17d-128">Otwórz wiersz polecenia i utwórz nowy katalog dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1c17d-128">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="1c17d-129">Spraw, aby był to bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="1c17d-129">Make that the current directory.</span></span> <span data-ttu-id="1c17d-130">Wprowadź następujące polecenie w oknie konsoli:</span><span class="sxs-lookup"><span data-stu-id="1c17d-130">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebApiClient
```

<span data-ttu-id="1c17d-131">Spowoduje to utworzenie plików startowych dla podstawowej aplikacji "Hello World".</span><span class="sxs-lookup"><span data-stu-id="1c17d-131">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="1c17d-132">Nazwa projektu to "WebApiClient".</span><span class="sxs-lookup"><span data-stu-id="1c17d-132">The project name is "WebApiClient".</span></span> <span data-ttu-id="1c17d-133">Ponieważ jest to nowy projekt, żadna z zależności nie są na miejscu.</span><span class="sxs-lookup"><span data-stu-id="1c17d-133">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="1c17d-134">Pierwsze uruchomienie pobierze platformę .NET Core, zainstaluje certyfikat deweloperski i uruchomi menedżera pakietów NuGet, aby przywrócić brakujące zależności.</span><span class="sxs-lookup"><span data-stu-id="1c17d-134">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="1c17d-135">Przed rozpoczęciem wprowadzania zmian `dotnet run` wpisz[(patrz uwaga)](#dotnet-restore-note)w wierszu polecenia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="1c17d-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="1c17d-136">`dotnet run`automatycznie wykonuje, `dotnet restore` jeśli w środowisku brakuje zależności.</span><span class="sxs-lookup"><span data-stu-id="1c17d-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="1c17d-137">Działa `dotnet build` również, jeśli aplikacja musi zostać przebudowana.</span><span class="sxs-lookup"><span data-stu-id="1c17d-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="1c17d-138">Po wstępnej konfiguracji, trzeba będzie `dotnet restore` `dotnet build` tylko uruchomić lub gdy ma to sens dla projektu.</span><span class="sxs-lookup"><span data-stu-id="1c17d-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="1c17d-139">Dodawanie nowych zależności</span><span class="sxs-lookup"><span data-stu-id="1c17d-139">Adding New Dependencies</span></span>

<span data-ttu-id="1c17d-140">Jednym z kluczowych celów projektowych dla platformy .NET Core jest zminimalizowanie rozmiaru instalacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="1c17d-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="1c17d-141">Jeśli aplikacja potrzebuje dodatkowych bibliotek dla niektórych jego funkcji, należy dodać\*te zależności do pliku projektu C# (csproj).</span><span class="sxs-lookup"><span data-stu-id="1c17d-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="1c17d-142">W naszym przykładzie należy dodać `System.Runtime.Serialization.Json` pakiet, dzięki czemu aplikacja może przetwarzać odpowiedzi JSON.</span><span class="sxs-lookup"><span data-stu-id="1c17d-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="1c17d-143">Pakiet dla tej `System.Runtime.Serialization.Json` aplikacji jest potrzebny.</span><span class="sxs-lookup"><span data-stu-id="1c17d-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="1c17d-144">Dodaj go do projektu, uruchamiając następujące polecenie [.NET CLI:](../../core/tools/dotnet-add-package.md)</span><span class="sxs-lookup"><span data-stu-id="1c17d-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="1c17d-145">Składanie żądań sieci Web</span><span class="sxs-lookup"><span data-stu-id="1c17d-145">Making Web Requests</span></span>

<span data-ttu-id="1c17d-146">Teraz możesz rozpocząć pobieranie danych z sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1c17d-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="1c17d-147">W tej aplikacji przeczytasz informacje z [interfejsu API GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="1c17d-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="1c17d-148">Przeczytajmy informacje o projektach pod patronatem [.NET Foundation.](https://www.dotnetfoundation.org/)</span><span class="sxs-lookup"><span data-stu-id="1c17d-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="1c17d-149">Rozpoczniesz od złożenia żądania do interfejsu API Usługi GitHub, aby pobrać informacje o projektach.</span><span class="sxs-lookup"><span data-stu-id="1c17d-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="1c17d-150">Punkt końcowy, którego użyjesz, to: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="1c17d-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="1c17d-151">Chcesz pobrać wszystkie informacje o tych projektach, więc użyjesz żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="1c17d-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="1c17d-152">Twoja przeglądarka korzysta również z żądań HTTP GET, dzięki czemu możesz wkleić ten adres URL do przeglądarki, aby zobaczyć, jakie informacje będziesz otrzymywać i przetwarzać.</span><span class="sxs-lookup"><span data-stu-id="1c17d-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="1c17d-153">Klasy służy <xref:System.Net.Http.HttpClient> do żądania sieci web.</span><span class="sxs-lookup"><span data-stu-id="1c17d-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="1c17d-154">Podobnie jak wszystkie nowoczesne interfejsy API platformy .NET, <xref:System.Net.Http.HttpClient> obsługuje tylko metody asynchronii dla jego długotrwałych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="1c17d-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="1c17d-155">Zacznij od metody asynchronii.</span><span class="sxs-lookup"><span data-stu-id="1c17d-155">Start by making an async method.</span></span> <span data-ttu-id="1c17d-156">Podczas tworzenia funkcji aplikacji zostanie uzupełnina implementacja.</span><span class="sxs-lookup"><span data-stu-id="1c17d-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="1c17d-157">Zacznij od `program.cs` otwarcia pliku w katalogu projektu i dodania następującej metody do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="1c17d-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="1c17d-158">Musisz dodać dyrektywę `using` w górnej części `Main` metody, tak aby kompilator <xref:System.Threading.Tasks.Task> języka C# rozpoznaje typ:</span><span class="sxs-lookup"><span data-stu-id="1c17d-158">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="1c17d-159">Jeśli tworzysz projekt w tym momencie, otrzymasz ostrzeżenie wygenerowane dla tej `await` metody, ponieważ nie zawiera żadnych operatorów i będzie działać synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="1c17d-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="1c17d-160">Zignoruj to na razie; dodasz `await` operatory podczas wypełniania metody.</span><span class="sxs-lookup"><span data-stu-id="1c17d-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="1c17d-161">Następnie zmień nazwę obszaru nazw `namespace` zdefiniowanego w `ConsoleApp` instrukcji `WebAPIClient`z domyślnego na .</span><span class="sxs-lookup"><span data-stu-id="1c17d-161">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="1c17d-162">Później zdefiniujemy `repo` klasę w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c17d-162">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="1c17d-163">Następnie zaktualizuj `Main` metodę, aby wywołać tę metodę.</span><span class="sxs-lookup"><span data-stu-id="1c17d-163">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="1c17d-164">Metoda `ProcessRepositories` zwraca zadanie i nie należy kończyć programu przed zakończeniem tego zadania.</span><span class="sxs-lookup"><span data-stu-id="1c17d-164">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="1c17d-165">W związku z tym należy `Main`zmienić podpis .</span><span class="sxs-lookup"><span data-stu-id="1c17d-165">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="1c17d-166">Dodaj `async` modyfikator i zmień typ `Task`zwracany na .</span><span class="sxs-lookup"><span data-stu-id="1c17d-166">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="1c17d-167">Następnie w treści metody dodaj wywołanie `ProcessRepositories`do .</span><span class="sxs-lookup"><span data-stu-id="1c17d-167">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="1c17d-168">Dodaj `await` słowo kluczowe do tego wywołania metody:</span><span class="sxs-lookup"><span data-stu-id="1c17d-168">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="1c17d-169">Teraz masz program, który nic nie robi, ale robi to asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="1c17d-169">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="1c17d-170">Poprawmy to.</span><span class="sxs-lookup"><span data-stu-id="1c17d-170">Let's improve it.</span></span>

<span data-ttu-id="1c17d-171">Najpierw potrzebny jest obiekt, który jest w stanie pobrać dane z sieci Web; można użyć <xref:System.Net.Http.HttpClient> a to zrobić.</span><span class="sxs-lookup"><span data-stu-id="1c17d-171">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="1c17d-172">Ten obiekt obsługuje żądanie i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1c17d-172">This object handles the request and the responses.</span></span> <span data-ttu-id="1c17d-173">Tworzenie wystąpienia pojedynczego wystąpienia tego `Program` typu w klasie wewnątrz pliku *Program.cs.*</span><span class="sxs-lookup"><span data-stu-id="1c17d-173">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

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

<span data-ttu-id="1c17d-174">Wróćmy do `ProcessRepositories` metody i wypełnij pierwszą jej wersję:</span><span class="sxs-lookup"><span data-stu-id="1c17d-174">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="1c17d-175">Musisz również dodać dwie nowe `using` dyrektywy w górnej części pliku, aby to skompilować:</span><span class="sxs-lookup"><span data-stu-id="1c17d-175">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="1c17d-176">Ta pierwsza wersja sprawia, że żądanie sieci web, aby przeczytać listę wszystkich repozytoriów w organizacji dotnet fundacji.</span><span class="sxs-lookup"><span data-stu-id="1c17d-176">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="1c17d-177">(Identyfikator gitHub dla Fundacji .NET to 'dotnet').</span><span class="sxs-lookup"><span data-stu-id="1c17d-177">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="1c17d-178">Pierwsze kilka wierszy <xref:System.Net.Http.HttpClient> skonfigurować dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="1c17d-178">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="1c17d-179">Po pierwsze jest skonfigurowany do akceptowania odpowiedzi JSON GitHub.</span><span class="sxs-lookup"><span data-stu-id="1c17d-179">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="1c17d-180">Ten format jest po prostu JSON.</span><span class="sxs-lookup"><span data-stu-id="1c17d-180">This format is simply JSON.</span></span> <span data-ttu-id="1c17d-181">Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1c17d-181">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="1c17d-182">Te dwa nagłówki są sprawdzane przez kod serwera GitHub i są niezbędne do pobierania informacji z usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="1c17d-182">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="1c17d-183">Po skonfigurowaniu <xref:System.Net.Http.HttpClient>programu , należy złożyć żądanie sieci Web i pobrać odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="1c17d-183">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="1c17d-184">W tej pierwszej wersji <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> należy użyć metody wygody.</span><span class="sxs-lookup"><span data-stu-id="1c17d-184">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="1c17d-185">Ta metoda wygody uruchamia zadanie, które sprawia, że żądanie sieci web, a następnie po zwróceniu żądania odczytuje strumień odpowiedzi i wyodrębnia zawartość ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="1c17d-185">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="1c17d-186">Treść odpowiedzi jest zwracana <xref:System.String>jako .</span><span class="sxs-lookup"><span data-stu-id="1c17d-186">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="1c17d-187">Ciąg jest dostępny po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="1c17d-187">The string is available when the task completes.</span></span>

<span data-ttu-id="1c17d-188">Ostatnie dwa wiersze tej metody czekają na to zadanie, a następnie wydrukuj odpowiedź do konsoli.</span><span class="sxs-lookup"><span data-stu-id="1c17d-188">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="1c17d-189">Skompiluj aplikację i uruchom ją.</span><span class="sxs-lookup"><span data-stu-id="1c17d-189">Build the app, and run it.</span></span> <span data-ttu-id="1c17d-190">Ostrzeżenie kompilacji nie ma `ProcessRepositories` teraz, ponieważ `await` teraz zawiera operatora.</span><span class="sxs-lookup"><span data-stu-id="1c17d-190">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="1c17d-191">Zobaczysz długie wyświetlanie tekstu sformatowanego json.</span><span class="sxs-lookup"><span data-stu-id="1c17d-191">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="1c17d-192">Przetwarzanie wyniku JSON</span><span class="sxs-lookup"><span data-stu-id="1c17d-192">Processing the JSON Result</span></span>

<span data-ttu-id="1c17d-193">W tym momencie napisano kod, aby pobrać odpowiedź z serwera sieci web i wyświetlić tekst, który jest zawarty w tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1c17d-193">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="1c17d-194">Następnie przekonwertujmy tę odpowiedź JSON na obiekty języka C#.</span><span class="sxs-lookup"><span data-stu-id="1c17d-194">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="1c17d-195">Klasa <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializuje obiekty do JSON i deserializes JSON do obiektów.</span><span class="sxs-lookup"><span data-stu-id="1c17d-195">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="1c17d-196">Zacznij od zdefiniowania klasy `repo` reprezentującej obiekt JSON zwrócony z interfejsu API Usługi GitHub:</span><span class="sxs-lookup"><span data-stu-id="1c17d-196">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

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

<span data-ttu-id="1c17d-197">Umieść powyższy kod w nowym pliku o nazwie 'repo.cs'.</span><span class="sxs-lookup"><span data-stu-id="1c17d-197">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="1c17d-198">Ta wersja klasy reprezentuje najprostszą ścieżkę do przetwarzania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="1c17d-198">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="1c17d-199">Nazwa klasy i nazwa elementu członkowskiego są zgodne z nazwami używanymi w pakiecie JSON, zamiast następujących konwencji języka C#.</span><span class="sxs-lookup"><span data-stu-id="1c17d-199">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="1c17d-200">Naprawisz to, podając niektóre atrybuty konfiguracji później.</span><span class="sxs-lookup"><span data-stu-id="1c17d-200">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="1c17d-201">Ta klasa pokazuje inną ważną cechę serializacji JSON i deserializacji: nie wszystkie pola w pakiecie JSON są częścią tej klasy.</span><span class="sxs-lookup"><span data-stu-id="1c17d-201">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="1c17d-202">Serializator JSON zignoruje informacje, które nie są uwzględnione w typie klasy, który jest używany.</span><span class="sxs-lookup"><span data-stu-id="1c17d-202">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="1c17d-203">Ta funkcja ułatwia tworzenie typów, które działają tylko z podzbiorem pól w pakiecie JSON.</span><span class="sxs-lookup"><span data-stu-id="1c17d-203">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="1c17d-204">Teraz, gdy utworzono typ, niech deserialize go.</span><span class="sxs-lookup"><span data-stu-id="1c17d-204">Now that you've created the type, let's deserialize it.</span></span>

<span data-ttu-id="1c17d-205">Następnie użyjesz serializatora do konwersji JSON do obiektów języka C#.</span><span class="sxs-lookup"><span data-stu-id="1c17d-205">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="1c17d-206">Zastąp <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> wywołanie w swojej `ProcessRepositories` metodzie następującymi wierszami:</span><span class="sxs-lookup"><span data-stu-id="1c17d-206">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="1c17d-207">Używasz nowej przestrzeni nazw, więc musisz dodać ją również u góry pliku:</span><span class="sxs-lookup"><span data-stu-id="1c17d-207">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="1c17d-208">Zwróć uwagę, że <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> teraz używasz zamiast <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="1c17d-208">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="1c17d-209">Serializator używa strumienia zamiast ciągu jako źródła.</span><span class="sxs-lookup"><span data-stu-id="1c17d-209">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="1c17d-210">Wyjaśnijmy kilka funkcji języka C#, które są używane w drugim wierszu poprzedniego fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="1c17d-210">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="1c17d-211">Pierwszym argumentem <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> `await` jest wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1c17d-211">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="1c17d-212">(Pozostałe dwa parametry są opcjonalne i są pomijane we wpisie kodu). Await wyrażenia mogą pojawić się prawie w dowolnym miejscu w kodzie, nawet jeśli do tej pory, masz tylko widział je jako część instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="1c17d-212">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="1c17d-213">Metoda `Deserialize` jest *ogólna*, co oznacza, że należy podać argumenty typu dla jakiego rodzaju obiektów powinny być tworzone z tekstu JSON.</span><span class="sxs-lookup"><span data-stu-id="1c17d-213">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="1c17d-214">W tym przykładzie deserializacji do `List<Repository>`, który jest inny <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>obiekt ogólny, .</span><span class="sxs-lookup"><span data-stu-id="1c17d-214">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1c17d-215">Klasa `List<>` przechowuje kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="1c17d-215">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="1c17d-216">Argument typu deklaruje typ obiektów przechowywanych `List<>`w pliku .</span><span class="sxs-lookup"><span data-stu-id="1c17d-216">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="1c17d-217">Tekst JSON reprezentuje zbiór obiektów repozytorium, `Repository`więc argument typu jest .</span><span class="sxs-lookup"><span data-stu-id="1c17d-217">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="1c17d-218">Jesteś prawie gotowy z tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1c17d-218">You're almost done with this section.</span></span> <span data-ttu-id="1c17d-219">Teraz, gdy zostały przekonwertowane JSON do C# obiektów, wyświetlmy nazwę każdego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="1c17d-219">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="1c17d-220">Zastąp wiersze, które brzmią:</span><span class="sxs-lookup"><span data-stu-id="1c17d-220">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="1c17d-221">z następującymi:</span><span class="sxs-lookup"><span data-stu-id="1c17d-221">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="1c17d-222">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="1c17d-222">Compile and run the application.</span></span> <span data-ttu-id="1c17d-223">Spowoduje to wydrukowanie nazw repozytoriów, które są częścią fundacji .NET.</span><span class="sxs-lookup"><span data-stu-id="1c17d-223">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="1c17d-224">Kontrolowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="1c17d-224">Controlling Serialization</span></span>

<span data-ttu-id="1c17d-225">Przed dodaniem większej liczby funkcji, `name` zajmijmy się właściwości za pomocą atrybutu. `[JsonPropertyName]`</span><span class="sxs-lookup"><span data-stu-id="1c17d-225">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="1c17d-226">W repo.cs w repo.cs wykonuj `name` następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="1c17d-226">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="1c17d-227">Aby `[JsonPropertyName]` użyć atrybutu, <xref:System.Text.Json.Serialization> należy dodać obszar nazw `using` do dyrektyw:</span><span class="sxs-lookup"><span data-stu-id="1c17d-227">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="1c17d-228">Ta zmiana oznacza, że należy zmienić kod, który zapisuje nazwę każdego repozytorium w program.cs:</span><span class="sxs-lookup"><span data-stu-id="1c17d-228">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="1c17d-229">Wykonaj, `dotnet run` aby upewnić się, że masz mapowania poprawne.</span><span class="sxs-lookup"><span data-stu-id="1c17d-229">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="1c17d-230">Powinieneś zobaczyć takie same dane wyjściowe jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="1c17d-230">You should see the same output as before.</span></span>

<span data-ttu-id="1c17d-231">Przed dodaniem nowych funkcji należy wprowadzić jeszcze jedną zmianę.</span><span class="sxs-lookup"><span data-stu-id="1c17d-231">Let's make one more change before adding new features.</span></span> <span data-ttu-id="1c17d-232">Metoda `ProcessRepositories` może wykonać pracę asynchroniiową i zwrócić kolekcję repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="1c17d-232">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="1c17d-233">Wróćmy `List<Repository>` z tej metody i przenieść kod, który zapisuje informacje do `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="1c17d-233">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="1c17d-234">Zmień `ProcessRepositories` podpis, aby zwrócić zadanie, którego `Repository` wynikiem jest lista obiektów:</span><span class="sxs-lookup"><span data-stu-id="1c17d-234">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="1c17d-235">Następnie po prostu zwróć repozytoria po przetworzeniu odpowiedzi JSON:</span><span class="sxs-lookup"><span data-stu-id="1c17d-235">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="1c17d-236">Kompilator generuje `Task<T>` obiekt dla zwracania, ponieważ ta `async`metoda została oznaczona jako .</span><span class="sxs-lookup"><span data-stu-id="1c17d-236">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="1c17d-237">Następnie zmodyfikujmy `Main` metodę, tak aby przechwytuje te wyniki i zapisywał każdą nazwę repozytorium w konsoli.</span><span class="sxs-lookup"><span data-stu-id="1c17d-237">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="1c17d-238">Twoja `Main` metoda wygląda teraz następująco:</span><span class="sxs-lookup"><span data-stu-id="1c17d-238">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="1c17d-239">Czytaj więcej informacji</span><span class="sxs-lookup"><span data-stu-id="1c17d-239">Reading More Information</span></span>

<span data-ttu-id="1c17d-240">Zakończmy to, przetwarzając kilka właściwości w pakiecie JSON, który jest wysyłany z interfejsu API Usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="1c17d-240">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="1c17d-241">Nie chcesz pobrać wszystko, ale dodanie kilku właściwości zademonstruje kilka innych funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="1c17d-241">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="1c17d-242">Zacznijmy od dodania kilku bardziej prostych `Repository` typów do definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="1c17d-242">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="1c17d-243">Dodaj te właściwości do tej klasy:</span><span class="sxs-lookup"><span data-stu-id="1c17d-243">Add these properties to that class:</span></span>

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

<span data-ttu-id="1c17d-244">Te właściwości mają wbudowane konwersje z typu ciągu (który jest tym, co zawierają pakiety JSON) do typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="1c17d-244">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="1c17d-245">Typ <xref:System.Uri> może być dla Ciebie nowy.</span><span class="sxs-lookup"><span data-stu-id="1c17d-245">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="1c17d-246">Reprezentuje identyfikator URI lub w tym przypadku adres URL.</span><span class="sxs-lookup"><span data-stu-id="1c17d-246">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="1c17d-247">W przypadku `Uri` i `int` typów, jeśli pakiet JSON zawiera dane, które nie konwertują do typu docelowego, akcja serializacji zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1c17d-247">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="1c17d-248">Po dodaniu tych aktualizacji `Main` metody, aby wyświetlić te elementy:</span><span class="sxs-lookup"><span data-stu-id="1c17d-248">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="1c17d-249">Na koniec dodajmy informacje dotyczące ostatniej operacji wypychania.</span><span class="sxs-lookup"><span data-stu-id="1c17d-249">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="1c17d-250">Te informacje są sformatowane w ten sposób w odpowiedzi JSON:</span><span class="sxs-lookup"><span data-stu-id="1c17d-250">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="1c17d-251">Ten format jest w skoordynowany czas uniwersalny (UTC), <xref:System.DateTime.Kind%2A> więc <xref:System.DateTimeKind.Utc>otrzymasz wartość, <xref:System.DateTime> której właściwość jest .</span><span class="sxs-lookup"><span data-stu-id="1c17d-251">That format is in Coordinated Universal Time (UTC) so you'll get a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Utc>.</span></span> <span data-ttu-id="1c17d-252">Jeśli wolisz datę reprezentowaną w strefie czasowej, musisz napisać niestandardową metodę konwersji.</span><span class="sxs-lookup"><span data-stu-id="1c17d-252">If you prefer a date represented in your time zone, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="1c17d-253">Najpierw `public` zdefiniuj właściwość, która będzie przechowywać `Repository` reprezentację `LastPush` `readonly` UTC daty i godziny w klasie oraz właściwość, która zwraca datę przekonwertowane na czas lokalny:</span><span class="sxs-lookup"><span data-stu-id="1c17d-253">First, define a `public` property that will hold the UTC representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns the date converted to local time:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

<span data-ttu-id="1c17d-254">Przejdźmy do nowych konstrukcji, które właśnie zdefiniowaliśmy.</span><span class="sxs-lookup"><span data-stu-id="1c17d-254">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="1c17d-255">Właściwość `LastPush` jest zdefiniowana przy użyciu elementu *członkowskiego zabudowanego wyrażenia* dla `get` akcesora.</span><span class="sxs-lookup"><span data-stu-id="1c17d-255">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="1c17d-256">Nie ma `set` akcesora.</span><span class="sxs-lookup"><span data-stu-id="1c17d-256">There is no `set` accessor.</span></span> <span data-ttu-id="1c17d-257">Pomijając `set` akcesor jest jak zdefiniować właściwość *tylko do odczytu* w języku C#.</span><span class="sxs-lookup"><span data-stu-id="1c17d-257">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="1c17d-258">(Tak, można tworzyć właściwości *tylko do zapisu* w języku C#, ale ich wartość jest ograniczona.)</span><span class="sxs-lookup"><span data-stu-id="1c17d-258">(Yes, you can create *write-only* properties in C#, but their value is limited.)</span></span>

<span data-ttu-id="1c17d-259">Na koniec dodaj jeszcze jedną instrukcję danych wyjściowych w konsoli i możesz ponownie utworzyć i uruchomić tę aplikację:</span><span class="sxs-lookup"><span data-stu-id="1c17d-259">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="1c17d-260">Twoja wersja powinna teraz być zgodna z [gotową próbką](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="1c17d-260">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="1c17d-261">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="1c17d-261">Conclusion</span></span>

<span data-ttu-id="1c17d-262">W tym samouczku pokazano, jak tworzyć żądania sieci web, analizować wynik i wyświetlać właściwości tych wyników.</span><span class="sxs-lookup"><span data-stu-id="1c17d-262">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="1c17d-263">Dodano również nowe pakiety jako zależności w projekcie.</span><span class="sxs-lookup"><span data-stu-id="1c17d-263">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="1c17d-264">Widziałeś niektóre funkcje języka C#, które obsługują techniki obiektowe.</span><span class="sxs-lookup"><span data-stu-id="1c17d-264">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
