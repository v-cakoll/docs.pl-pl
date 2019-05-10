---
title: Tworzenie klienta REST przy użyciu platformy .NET Core
description: W tym samouczku pokazano pewną liczbę funkcji platformy .NET Core i języka C#.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: f6e3371a72810b30f804169be4025360aa10c477
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063885"
---
# <a name="rest-client"></a><span data-ttu-id="1bec1-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="1bec1-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="1bec1-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="1bec1-104">Introduction</span></span>

<span data-ttu-id="1bec1-105">W tym samouczku pokazano pewną liczbę funkcji platformy .NET Core i języka C#.</span><span class="sxs-lookup"><span data-stu-id="1bec1-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="1bec1-106">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="1bec1-106">You’ll learn:</span></span>

* <span data-ttu-id="1bec1-107">Podstawowe narzędzia .NET Core interfejsu wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="1bec1-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
* <span data-ttu-id="1bec1-108">Omówienie funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="1bec1-108">An overview of C# Language features.</span></span>
* <span data-ttu-id="1bec1-109">Zarządzanie zależnościami z NuGet</span><span class="sxs-lookup"><span data-stu-id="1bec1-109">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="1bec1-110">HTTP Communications</span><span class="sxs-lookup"><span data-stu-id="1bec1-110">HTTP Communications</span></span>
* <span data-ttu-id="1bec1-111">Przetwarzanie informacji w formacie JSON</span><span class="sxs-lookup"><span data-stu-id="1bec1-111">Processing JSON information</span></span>
* <span data-ttu-id="1bec1-112">Zarządzanie konfiguracją za pomocą atrybutów.</span><span class="sxs-lookup"><span data-stu-id="1bec1-112">Managing configuration with Attributes.</span></span>

<span data-ttu-id="1bec1-113">Skompiluj aplikację, która wysyła żądania HTTP do usługi REST w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="1bec1-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="1bec1-114">Będziesz odczytu informacji w formacie JSON, a następnie przekonwertować pakietu JSON na obiekty języka C#.</span><span class="sxs-lookup"><span data-stu-id="1bec1-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="1bec1-115">Na koniec zobaczysz sposób pracy z obiektami w języku C#.</span><span class="sxs-lookup"><span data-stu-id="1bec1-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="1bec1-116">Istnieje wiele funkcji, w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="1bec1-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="1bec1-117">Utworzymy je jedno po drugim.</span><span class="sxs-lookup"><span data-stu-id="1bec1-117">Let’s build them one by one.</span></span>

<span data-ttu-id="1bec1-118">Jeśli wolisz postępuj zgodnie ze szczegółowymi [próbki końcowej](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) w tym temacie, możesz ją pobrać.</span><span class="sxs-lookup"><span data-stu-id="1bec1-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="1bec1-119">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="1bec1-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1bec1-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="1bec1-120">Prerequisites</span></span>

<span data-ttu-id="1bec1-121">Należy skonfigurować maszynę, aby uruchomić platformy .NET core.</span><span class="sxs-lookup"><span data-stu-id="1bec1-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="1bec1-122">Instrukcje dotyczące instalacji można znaleźć na [platformy .NET Core](https://www.microsoft.com/net/core) strony.</span><span class="sxs-lookup"><span data-stu-id="1bec1-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="1bec1-123">Windows, Linux, macOS lub w kontenerze platformy Docker, mogą uruchamiać tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="1bec1-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="1bec1-124">Musisz zainstalować wybrany edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="1bec1-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="1bec1-125">Opisy poniżej użycia [programu Visual Studio Code](https://code.visualstudio.com/), która jest typu open source cross platform edytora.</span><span class="sxs-lookup"><span data-stu-id="1bec1-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="1bec1-126">Można jednak użyć dowolnego narzędzia potrafisz.</span><span class="sxs-lookup"><span data-stu-id="1bec1-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="1bec1-127">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="1bec1-127">Create the Application</span></span>

<span data-ttu-id="1bec1-128">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1bec1-128">The first step is to create a new application.</span></span> <span data-ttu-id="1bec1-129">Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1bec1-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="1bec1-130">Upewnij się, że sposób bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="1bec1-130">Make that the current directory.</span></span> <span data-ttu-id="1bec1-131">Wpisz polecenie `dotnet new console` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="1bec1-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="1bec1-132">Spowoduje to utworzenie plikach startowych dla podstawowych aplikacji "Hello World".</span><span class="sxs-lookup"><span data-stu-id="1bec1-132">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="1bec1-133">Jak jest to nowy projekt, żaden z zależności jest w miejscu, dzięki czemu przy pierwszym uruchomieniu Pobierz platformę .NET Core, można zainstalować certyfikatu deweloperskiego i uruchamiać Menedżera pakietów NuGet, aby przywrócić brakujących zależności.</span><span class="sxs-lookup"><span data-stu-id="1bec1-133">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework, install a development certificate and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="1bec1-134">Przed rozpoczęciem wprowadzania modyfikacji, wpisz `dotnet run` ([patrz Uwaga](#dotnet-restore-note)) w wierszu polecenia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="1bec1-134">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="1bec1-135">`dotnet run` automatycznie wykonuje `dotnet restore` Jeśli środowisko nie ma zależności.</span><span class="sxs-lookup"><span data-stu-id="1bec1-135">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="1bec1-136">Wykonuje także `dotnet build` Jeśli aplikacja wymaga odbudowania.</span><span class="sxs-lookup"><span data-stu-id="1bec1-136">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="1bec1-137">Po początkowej konfiguracji, wystarczy uruchomić `dotnet restore` lub `dotnet build` po sens dla Twojego projektu.</span><span class="sxs-lookup"><span data-stu-id="1bec1-137">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="1bec1-138">Dodawanie nowych zależności</span><span class="sxs-lookup"><span data-stu-id="1bec1-138">Adding New Dependencies</span></span>

<span data-ttu-id="1bec1-139">Jednym z celów projektowania klucza dla platformy .NET Core jest minimalizacja rozmiaru instalacji programu .NET.</span><span class="sxs-lookup"><span data-stu-id="1bec1-139">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="1bec1-140">Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych funkcji, możesz dodać te zależności w projekcie języka C# (\*.csproj) pliku.</span><span class="sxs-lookup"><span data-stu-id="1bec1-140">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="1bec1-141">W tym przykładzie należy dodać `System.Runtime.Serialization.Json` pakietu, dzięki czemu aplikacja może przetworzyć odpowiedzi JSON.</span><span class="sxs-lookup"><span data-stu-id="1bec1-141">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="1bec1-142">Otwórz swoje `csproj` pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="1bec1-142">Open your `csproj` project file.</span></span> <span data-ttu-id="1bec1-143">Pierwszy wiersz w pliku powinny się wyświetlać jako:</span><span class="sxs-lookup"><span data-stu-id="1bec1-143">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="1bec1-144">Dodaj następujący kod bezpośrednio po tym wierszu:</span><span class="sxs-lookup"><span data-stu-id="1bec1-144">Add the following immediately after this line:</span></span>

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup>
```

<span data-ttu-id="1bec1-145">Większość edytory kodu zapewni uzupełnianie przez różne wersje tych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="1bec1-145">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="1bec1-146">Zazwyczaj będziesz chciał użyć najnowszej wersji dowolnego pakietu, który dodajesz.</span><span class="sxs-lookup"><span data-stu-id="1bec1-146">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="1bec1-147">Jednak należy się upewnić, że są zgodne wersje wszystkich pakietów i są również zgodne wersję platformy aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1bec1-147">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="1bec1-148">Po wprowadzeniu tych zmian należy wykonać `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) tak, aby pakiet jest zainstalowany w systemie.</span><span class="sxs-lookup"><span data-stu-id="1bec1-148">After you've made these changes, execute `dotnet restore` ([see note](#dotnet-restore-note)) so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="1bec1-149">Tworzenie żądania sieci Web</span><span class="sxs-lookup"><span data-stu-id="1bec1-149">Making Web Requests</span></span>

<span data-ttu-id="1bec1-150">Teraz możesz rozpocząć pobieranie danych z sieci web.</span><span class="sxs-lookup"><span data-stu-id="1bec1-150">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="1bec1-151">W tej aplikacji będzie odczytu informacji z [interfejsu API usługi GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="1bec1-151">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="1bec1-152">Spróbujmy odczytać informacji na temat projektów w ramach [.NET Foundation](https://www.dotnetfoundation.org/) ogólny.</span><span class="sxs-lookup"><span data-stu-id="1bec1-152">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="1bec1-153">Można będzie uruchomić w żądaniu skierowanym do interfejsu API usługi GitHub, aby pobrać informacje na temat projektów.</span><span class="sxs-lookup"><span data-stu-id="1bec1-153">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="1bec1-154">Punkt końcowy będziesz używał jest: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="1bec1-154">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="1bec1-155">Chcesz pobrać wszystkie informacje dotyczące tych projektów, dzięki czemu będziesz używać żądanie HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="1bec1-155">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="1bec1-156">Przeglądarka używa także żądania HTTP GET, dzięki czemu można wkleić, że adres URL w przeglądarce, aby zobaczyć, jakie informacje należy będziesz otrzymywać i przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="1bec1-156">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="1bec1-157">Możesz użyć <xref:System.Net.Http.HttpClient> klasy żądań sieci web.</span><span class="sxs-lookup"><span data-stu-id="1bec1-157">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="1bec1-158">Wszystkie nowoczesnych interfejsów API programu .NET, takich jak <xref:System.Net.Http.HttpClient> obsługuje tylko metody asynchroniczne dla długotrwałych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="1bec1-158">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="1bec1-159">Rozpocznij metodą asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="1bec1-159">Start by making an async method.</span></span> <span data-ttu-id="1bec1-160">Podczas tworzenia funkcjonalność aplikacji będzie wypełniana w implementacji.</span><span class="sxs-lookup"><span data-stu-id="1bec1-160">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="1bec1-161">Zacznij od otwarcia `program.cs` plik w katalogu projektu i dodawanie następującą metodę do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="1bec1-161">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="1bec1-162">Musisz dodać `using` instrukcji w górnej części Twojej `Main` metoda tak, aby kompilator języka C# rozpoznaje <xref:System.Threading.Tasks.Task> typu:</span><span class="sxs-lookup"><span data-stu-id="1bec1-162">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="1bec1-163">Jeśli na tym etapie tworzenia projektu uzyskasz ostrzeżenia generowane dla tej metody, ponieważ nie zawiera żadnego `await` operatorów i zostanie ona uruchomiona synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="1bec1-163">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="1bec1-164">Zignoruje teraz; następnie dodasz `await` operatorów jako możesz wypełnić w metodzie.</span><span class="sxs-lookup"><span data-stu-id="1bec1-164">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="1bec1-165">Następnie zmień nazwę przestrzeni nazw, zdefiniowane w `namespace` instrukcji domyślne `ConsoleApp` do `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="1bec1-165">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="1bec1-166">Później zdefiniujemy `repo` klasy w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1bec1-166">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="1bec1-167">Następnie zaktualizuj `Main` metodę do wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="1bec1-167">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="1bec1-168">`ProcessRepositories` Metoda zwraca klasę Task, i nie należy zakończyć program, przed zakończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="1bec1-168">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="1bec1-169">W związku z tym, należy użyć `Wait` metodę, aby zablokować i poczekaj na zakończenie zadania:</span><span class="sxs-lookup"><span data-stu-id="1bec1-169">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="1bec1-170">Teraz masz program, nic nie robi, ale zajmuje asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="1bec1-170">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="1bec1-171">Możemy ją ulepszyć.</span><span class="sxs-lookup"><span data-stu-id="1bec1-171">Let's improve it.</span></span>

<span data-ttu-id="1bec1-172">Najpierw należy obiekt, który jest w stanie pobrać danych z sieci web; Możesz użyć <xref:System.Net.Http.HttpClient> Aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="1bec1-172">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="1bec1-173">Ten obiekt obsługuje żądania i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1bec1-173">This object handles the request and the responses.</span></span> <span data-ttu-id="1bec1-174">Utwórz wystąpienie jedno wystąpienie tego typu w `Program` klasy w pliku Program.cs.</span><span class="sxs-lookup"><span data-stu-id="1bec1-174">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

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

<span data-ttu-id="1bec1-175">Wróć do `ProcessRepositories` metody i wypełnij pierwszą wersję:</span><span class="sxs-lookup"><span data-stu-id="1bec1-175">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="1bec1-176">Musisz również dodać dwie nowe przy użyciu instrukcji w górnej części pliku, w tym do skompilowania:</span><span class="sxs-lookup"><span data-stu-id="1bec1-176">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="1bec1-177">Ta pierwsza wersja sprawia, że żądanie sieci web, aby zapoznać się z listą wszystkich repozytoriów w ramach organizacji foundation dotnet.</span><span class="sxs-lookup"><span data-stu-id="1bec1-177">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="1bec1-178">(Identyfikator gitHub .NET Foundation jest "dotnet").</span><span class="sxs-lookup"><span data-stu-id="1bec1-178">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="1bec1-179">Pierwszych kilka wierszy, ustawianie <xref:System.Net.Http.HttpClient> dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="1bec1-179">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="1bec1-180">Najpierw jest skonfigurowany do akceptowania odpowiedziami JSON usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="1bec1-180">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="1bec1-181">Ten format jest po prostu JSON.</span><span class="sxs-lookup"><span data-stu-id="1bec1-181">This format is simply JSON.</span></span> <span data-ttu-id="1bec1-182">Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1bec1-182">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="1bec1-183">Te dwa nagłówki są sprawdzane przez kod serwera GitHub i są niezbędne w celu pobrania informacji z usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="1bec1-183">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="1bec1-184">Po skonfigurowaniu <xref:System.Net.Http.HttpClient>, upewnij sieci web, żądania i pobierania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1bec1-184">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="1bec1-185">W pierwszej wersji, możesz użyć <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> wygodna metoda.</span><span class="sxs-lookup"><span data-stu-id="1bec1-185">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="1bec1-186">Ta wygodna metoda uruchamia zadanie, które wysyła żądanie sieci web, a następnie po powrocie z żądania go odczytuje w strumieniu odpowiedzi i wyodrębnia zawartość ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="1bec1-186">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="1bec1-187">Treść odpowiedzi jest zwracana jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="1bec1-187">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="1bec1-188">Ten ciąg jest dostępna po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="1bec1-188">The string is available when the task completes.</span></span>

<span data-ttu-id="1bec1-189">Ostatnie dwie linie ta metoda poczekać na zadanie, a następnie wydrukuj odpowiedzi do konsoli.</span><span class="sxs-lookup"><span data-stu-id="1bec1-189">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="1bec1-190">Tworzenie aplikacji i uruchom go.</span><span class="sxs-lookup"><span data-stu-id="1bec1-190">Build the app, and run it.</span></span> <span data-ttu-id="1bec1-191">Ostrzeżenie kompilacji ma teraz, ponieważ `ProcessRepositories` teraz zawierać `await` operatora.</span><span class="sxs-lookup"><span data-stu-id="1bec1-191">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="1bec1-192">Zobaczysz, że długie wyświetlanie JSON sformatowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="1bec1-192">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="1bec1-193">Przetwarzanie wyników JSON</span><span class="sxs-lookup"><span data-stu-id="1bec1-193">Processing the JSON Result</span></span>

<span data-ttu-id="1bec1-194">W tym momencie został napisany kod, aby pobrać odpowiedzi z serwera sieci web oraz wyświetlać tekst, który znajduje się w tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1bec1-194">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="1bec1-195">Następnie możemy przekonwertować odpowiedź JSON na obiekty języka C#.</span><span class="sxs-lookup"><span data-stu-id="1bec1-195">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="1bec1-196">Serializator JSON konwertuje dane JSON na obiekty języka C#.</span><span class="sxs-lookup"><span data-stu-id="1bec1-196">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="1bec1-197">Pierwsze zadanie jest zdefiniowanie typu klasy C# zawiera informacje, które od tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1bec1-197">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="1bec1-198">Utwórzmy tym powoli, więc rozpoczyna się od prostego języka C# typ, który zawiera nazwę repozytorium:</span><span class="sxs-lookup"><span data-stu-id="1bec1-198">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

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

<span data-ttu-id="1bec1-199">Powyższy kod należy umieścić w nowym pliku o nazwie "repo.cs".</span><span class="sxs-lookup"><span data-stu-id="1bec1-199">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="1bec1-200">Ta wersja klasy reprezentuje to najprostsza ścieżka do przetwarzania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="1bec1-200">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="1bec1-201">Nazwa klasy i nazwę elementu członkowskiego zgodne nazwy używane w pakiecie JSON zamiast następujących konwencji języka C#.</span><span class="sxs-lookup"><span data-stu-id="1bec1-201">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="1bec1-202">Można to naprawić, zapewniając niektóre atrybuty konfiguracji później.</span><span class="sxs-lookup"><span data-stu-id="1bec1-202">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="1bec1-203">Ta klasa przedstawia inną ważną cechą JSON serializacji i deserializacji: Nie wszystkie pola w pakiecie JSON należą do tej klasy.</span><span class="sxs-lookup"><span data-stu-id="1bec1-203">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="1bec1-204">Serializator JSON będzie ignorować informacje, które nie są objęte na typ klasy, które są używane.</span><span class="sxs-lookup"><span data-stu-id="1bec1-204">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="1bec1-205">Ta funkcja sprawia, że łatwiej tworzyć typy, które działają z tylko podzestaw pól w pakiecie JSON.</span><span class="sxs-lookup"><span data-stu-id="1bec1-205">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="1bec1-206">Teraz, po utworzeniu typu, możemy zdeserializuj ją.</span><span class="sxs-lookup"><span data-stu-id="1bec1-206">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="1bec1-207">Musisz utworzyć <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obiektu.</span><span class="sxs-lookup"><span data-stu-id="1bec1-207">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="1bec1-208">Ten obiekt musi znać typ CLR Oczekiwano pakietu JSON pobiera.</span><span class="sxs-lookup"><span data-stu-id="1bec1-208">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="1bec1-209">Pakiet z repozytorium GitHub zawiera sekwencję repozytoriów, więc `List<repo>` jest poprawnego typu.</span><span class="sxs-lookup"><span data-stu-id="1bec1-209">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="1bec1-210">Dodaj następujący wiersz do Twojej `ProcessRepositories` metody:</span><span class="sxs-lookup"><span data-stu-id="1bec1-210">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="1bec1-211">Używasz dwie nowe przestrzenie nazw, więc należy dodać te także:</span><span class="sxs-lookup"><span data-stu-id="1bec1-211">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="1bec1-212">Następnie użyjemy serializatora do przekonwertowania formatu JSON na obiekty języka C#.</span><span class="sxs-lookup"><span data-stu-id="1bec1-212">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="1bec1-213">Zastąp wywołanie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> w swojej `ProcessRepositories` metody za pomocą następujących dwóch wierszy:</span><span class="sxs-lookup"><span data-stu-id="1bec1-213">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="1bec1-214">Należy zauważyć, że używasz teraz <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> zamiast <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="1bec1-214">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="1bec1-215">Serializator używa strumienia zamiast ciągu jako źródło.</span><span class="sxs-lookup"><span data-stu-id="1bec1-215">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="1bec1-216">Możemy wyjaśnić kilka funkcji języka C#, które są używane w drugim wierszu powyżej.</span><span class="sxs-lookup"><span data-stu-id="1bec1-216">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="1bec1-217">Argument <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> jest `await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1bec1-217">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="1bec1-218">Await wyrażeń może znajdować się praktycznie dowolnym miejscu w kodzie, mimo że do chwili obecnej, tylko przedstawiono je w ramach instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="1bec1-218">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="1bec1-219">Po drugie `as` operator konwertuje typ czasu kompilacji `object` do `List<repo>`.</span><span class="sxs-lookup"><span data-stu-id="1bec1-219">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span>
<span data-ttu-id="1bec1-220">Deklaracja <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, że funkcja zwraca obiekt typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1bec1-220">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1bec1-221"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> Zwraca typ określony podczas jego skonstruowano (`List<repo>` w ramach tego samouczka).</span><span class="sxs-lookup"><span data-stu-id="1bec1-221"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="1bec1-222">Jeśli konwersja nie powiedzie, `as` operatora daje w wyniku `null`, zamiast zgłaszać wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1bec1-222">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="1bec1-223">Prawie gotowe z tą sekcją.</span><span class="sxs-lookup"><span data-stu-id="1bec1-223">You're almost done with this section.</span></span> <span data-ttu-id="1bec1-224">Teraz, za pomocą pliku JSON zostały konwertowane na obiekty języka C#, możemy wyświetlić nazwę każdego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="1bec1-224">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="1bec1-225">Zamień wiersze, które odczytują:</span><span class="sxs-lookup"><span data-stu-id="1bec1-225">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="1bec1-226">z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1bec1-226">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="1bec1-227">Skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="1bec1-227">Compile and run the application.</span></span> <span data-ttu-id="1bec1-228">Zostanie ona wydrukowana nazwy repozytoria, które są częścią .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="1bec1-228">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="1bec1-229">Kontrolowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="1bec1-229">Controlling Serialization</span></span>

<span data-ttu-id="1bec1-230">Zanim dodasz więcej funkcji, możemy adresów `repo` wpisz i przypisz ją konwencjami bardziej standard języka C#.</span><span class="sxs-lookup"><span data-stu-id="1bec1-230">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="1bec1-231">Możesz to zrobić poprzez dodawanie adnotacji do `repo` to typ *atrybuty* które kontrolują, jak działa serializator JSON.</span><span class="sxs-lookup"><span data-stu-id="1bec1-231">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="1bec1-232">W Twoim przypadku użyjesz tych atrybutów do definiowania mapowania między nazwami kluczy JSON i języka C# nazwy klas i składowych.</span><span class="sxs-lookup"><span data-stu-id="1bec1-232">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="1bec1-233">Są dwa atrybuty używane <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="1bec1-233">The two attributes used are the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes.</span></span> <span data-ttu-id="1bec1-234">Zgodnie z Konwencją wszystkie klasy atrybutu kończyć się sufiksem `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="1bec1-234">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="1bec1-235">Jednak nie należy używać tego sufiksu, po zastosowaniu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1bec1-235">However, you do not need to use that suffix when you apply an attribute.</span></span>

<span data-ttu-id="1bec1-236"><xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty są w innej biblioteki, więc musisz dodać tej biblioteki do pliku projektu C# jako zależność.</span><span class="sxs-lookup"><span data-stu-id="1bec1-236">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="1bec1-237">Dodaj następujący wiersz do `<ItemGroup>` sekcji w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="1bec1-237">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="1bec1-238">Po zapisaniu pliku Uruchom `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) do pobrania tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="1bec1-238">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="1bec1-239">Następnie otwórz `repo.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="1bec1-239">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="1bec1-240">Zmienimy nazwę pisanymi wielkimi literami, a w pełni pisowni nazwiska `Repository`.</span><span class="sxs-lookup"><span data-stu-id="1bec1-240">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="1bec1-241">Firma Microsoft nadal chcesz mapy JSON "repo" węzłów do tego typu, więc musisz dodać <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="1bec1-241">We still want to map JSON 'repo' nodes to this type, so you'll need to add the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class declaration.</span></span> <span data-ttu-id="1bec1-242">Użytkownik ustawia `Name` właściwość atrybutu nazwy węzłów JSON, które mapują do tego typu:</span><span class="sxs-lookup"><span data-stu-id="1bec1-242">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="1bec1-243"><xref:System.Runtime.Serialization.DataContractAttribute> Jest elementem członkowskim <xref:System.Runtime.Serialization> przestrzeni nazw, więc należy dodać odpowiedni `using` instrukcji w górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="1bec1-243">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="1bec1-244">Zmieniono nazwę elementu `repo` klasy `Repository`, więc musisz wprowadzić taką samą nazwę, zmiany w pliku Program.cs (niektóre edytory mogą obsługiwać Refaktoryzacja zmiany nazwy, automatycznie wprowadzić tę zmianę:)</span><span class="sxs-lookup"><span data-stu-id="1bec1-244">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="1bec1-245">Następnie można wprowadzić tę samą zmianę z `name` pola przy użyciu <xref:System.Runtime.Serialization.DataMemberAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="1bec1-245">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="1bec1-246">Wprowadź następujące zmiany do deklaracji `name` pole repo.cs:</span><span class="sxs-lookup"><span data-stu-id="1bec1-246">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="1bec1-247">Ta zmiana oznacza, że zajdzie potrzeba zmiany kodu, który zapisuje nazwy każdego repozytorium w pliku program.cs:</span><span class="sxs-lookup"><span data-stu-id="1bec1-247">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="1bec1-248">Czy `dotnet build` następuje `dotnet run` się upewnić, że masz mapowania poprawne.</span><span class="sxs-lookup"><span data-stu-id="1bec1-248">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="1bec1-249">Ten sam wynik jako przed powinny być widoczne.</span><span class="sxs-lookup"><span data-stu-id="1bec1-249">You should see the same output as before.</span></span> <span data-ttu-id="1bec1-250">Zanim będziemy przetwarzać więcej właściwości z serwera sieci web, upewnijmy się, co więcej zmian `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="1bec1-250">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="1bec1-251">`Name` Składowa jest polem dostępny publicznie.</span><span class="sxs-lookup"><span data-stu-id="1bec1-251">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="1bec1-252">Nie jest dobrą praktyką zorientowane obiektowo, więc Zmieńmy go do właściwości.</span><span class="sxs-lookup"><span data-stu-id="1bec1-252">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="1bec1-253">Dla naszych potrzeb, potrzebujemy dowolnego konkretnego kodu, który uruchamiany, gdy pobieranie lub ustawianie właściwości, ale zmiana właściwości ułatwia dodawanie tych zmian w przyszłości, bez przerywania wszelki kod, który używa `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="1bec1-253">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="1bec1-254">Usuń definicję pola i zastąp go wartością [automatycznie implementowana właściwość](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span><span class="sxs-lookup"><span data-stu-id="1bec1-254">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="1bec1-255">Kompilator generuje treści `get` i `set` metod dostępu, a także prywatnego pola do przechowywania nazwy.</span><span class="sxs-lookup"><span data-stu-id="1bec1-255">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="1bec1-256">Będzie podobny do poniższego kodu, który można ręcznie wpisać:</span><span class="sxs-lookup"><span data-stu-id="1bec1-256">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name
{
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="1bec1-257">Upewnijmy się, co więcej zmian przed dodaniem nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="1bec1-257">Let's make one more change before adding new features.</span></span> <span data-ttu-id="1bec1-258">`ProcessRepositories` Zwracają kolekcję repozytoriów i oferuje Praca asynchroniczna metoda.</span><span class="sxs-lookup"><span data-stu-id="1bec1-258">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="1bec1-259">Powrócimy `List<Repository>` z tej metody, a następnie przenieść kod, który zapisuje informacje w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="1bec1-259">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="1bec1-260">Zmień podpis `ProcessRepositories` zwracany typ task, którego wynikiem jest lista z `Repository` obiektów:</span><span class="sxs-lookup"><span data-stu-id="1bec1-260">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="1bec1-261">Następnie, po prostu zwraca repozytoriów po przetworzeniu odpowiedź w formacie JSON:</span><span class="sxs-lookup"><span data-stu-id="1bec1-261">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="1bec1-262">Kompilator generuje `Task<T>` obiekt do zwrotu, ponieważ został oznaczony jako tej metody jako `async`.</span><span class="sxs-lookup"><span data-stu-id="1bec1-262">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="1bec1-263">Następnie zmodyfikujmy `Main` metodę, tak że przechwytuje te wyniki i zapisuje każdej nazwy repozytorium do konsoli.</span><span class="sxs-lookup"><span data-stu-id="1bec1-263">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="1bec1-264">Twoje `Main` metoda wygląda teraz następująco:</span><span class="sxs-lookup"><span data-stu-id="1bec1-264">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="1bec1-265">Uzyskiwanie dostępu do `Result` właściwość zadania blokuje, dopóki zadanie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="1bec1-265">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="1bec1-266">Zazwyczaj chcesz `await` ukończenia zadania, jak `ProcessRepositories` metody, ale nie jest dozwolona w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="1bec1-266">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="1bec1-267">Odczytywanie informacji</span><span class="sxs-lookup"><span data-stu-id="1bec1-267">Reading More Information</span></span>

<span data-ttu-id="1bec1-268">Teraz zakończyć to przez przetwarzanie kilka innych właściwości w pakiecie JSON wysyłana z interfejsu API usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="1bec1-268">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="1bec1-269">Nie będzie konieczności Pobierz wszystko, ale dodanie kilka właściwości zademonstruje kilka więcej funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="1bec1-269">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="1bec1-270">Zacznijmy od dodania kilka więcej typów prostych do `Repository` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="1bec1-270">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="1bec1-271">Dodaj następujące właściwości dla tej klasy:</span><span class="sxs-lookup"><span data-stu-id="1bec1-271">Add these properties to that class:</span></span>

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

<span data-ttu-id="1bec1-272">Te właściwości mają wbudowane definicje konwersji z typu string (czyli zawierać pakiety JSON) na typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="1bec1-272">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="1bec1-273"><xref:System.Uri> Typ może być dla Ciebie nowe.</span><span class="sxs-lookup"><span data-stu-id="1bec1-273">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="1bec1-274">Reprezentuje identyfikator URI, lub w tym przypadku adresu URL.</span><span class="sxs-lookup"><span data-stu-id="1bec1-274">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="1bec1-275">W przypadku właściwości `Uri` i `int` typy pakietów JSON zawiera dane, które nie konwersji na typ docelowy, akcja serializacji spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1bec1-275">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="1bec1-276">Po dodaniu tych aktualizacji `Main` metodę w celu wyświetlenia tych elementów:</span><span class="sxs-lookup"><span data-stu-id="1bec1-276">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="1bec1-277">W ostatnim kroku Dodajmy informacji z ostatniej operacji wypychania.</span><span class="sxs-lookup"><span data-stu-id="1bec1-277">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="1bec1-278">Te informacje są sformatowane w ten sposób, w odpowiedzi JSON:</span><span class="sxs-lookup"><span data-stu-id="1bec1-278">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="1bec1-279">Ten format nie jest zgodna z dowolnego programu standard .NET <xref:System.DateTime> formatów.</span><span class="sxs-lookup"><span data-stu-id="1bec1-279">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="1bec1-280">Z tego powodu musisz napisać metodę konwersji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1bec1-280">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="1bec1-281">Ponadto najprawdopodobniej nie chcesz, nieprzetworzonego ciągu widoczna dla użytkowników z `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="1bec1-281">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="1bec1-282">Atrybuty można kontrolować oznacza również.</span><span class="sxs-lookup"><span data-stu-id="1bec1-282">Attributes can help control that as well.</span></span> <span data-ttu-id="1bec1-283">Najpierw należy zdefiniować `private` właściwość, która będzie przechowywać reprezentację ciągu daty, godziny w swojej `Repository` klasy:</span><span class="sxs-lookup"><span data-stu-id="1bec1-283">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="1bec1-284"><xref:System.Runtime.Serialization.DataMemberAttribute> Atrybut informuje serializator, powinna to być przetworzone, mimo że nie ma publicznej składowej.</span><span class="sxs-lookup"><span data-stu-id="1bec1-284">The <xref:System.Runtime.Serialization.DataMemberAttribute> attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="1bec1-285">Następnie należy napisać właściwość publiczna tylko do odczytu, która konwertuje ciąg na prawidłowym <xref:System.DateTime> obiektu i zwraca ją <xref:System.DateTime>:</span><span class="sxs-lookup"><span data-stu-id="1bec1-285">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

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

<span data-ttu-id="1bec1-286">Zajmijmy się nowe konstrukcje powyżej.</span><span class="sxs-lookup"><span data-stu-id="1bec1-286">Let's go over the new constructs above.</span></span> <span data-ttu-id="1bec1-287">`IgnoreDataMember` Atrybutu powoduje, że tego typu nie należy do odczytu ani zapisane z dowolnych obiektów JSON i że, serializator.</span><span class="sxs-lookup"><span data-stu-id="1bec1-287">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="1bec1-288">Ta właściwość zawiera tylko `get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="1bec1-288">This property contains only a `get` accessor.</span></span> <span data-ttu-id="1bec1-289">Istnieje nie `set` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="1bec1-289">There is no `set` accessor.</span></span> <span data-ttu-id="1bec1-290">To, jak zdefiniować *tylko do odczytu* właściwość w języku C#.</span><span class="sxs-lookup"><span data-stu-id="1bec1-290">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="1bec1-291">(Tak, możesz utworzyć *tylko do zapisu* właściwości w języku C#, ale ich wartość jest ograniczona.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Metoda analizowania ciągu i tworzy <xref:System.DateTime> przy użyciu podanej daty w formacie, a następnie dodaje dodatkowe metadane `DateTime` przy użyciu `CultureInfo` obiektu.</span><span class="sxs-lookup"><span data-stu-id="1bec1-291">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="1bec1-292">Metoda dostępu właściwości zgłasza wyjątek, w przypadku niepowodzenia operacji analizy.</span><span class="sxs-lookup"><span data-stu-id="1bec1-292">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="1bec1-293">Aby użyć <xref:System.Globalization.CultureInfo.InvariantCulture>, należy dodać <xref:System.Globalization> przestrzeń nazw `using` instrukcji w `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="1bec1-293">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="1bec1-294">Na koniec należy dodać jeden wyjściowy więcej instrukcji, w konsoli i wszystko będzie gotowe skompilować i ponownie uruchomić tę aplikację:</span><span class="sxs-lookup"><span data-stu-id="1bec1-294">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="1bec1-295">Twoja wersja powinna być teraz zgodna [gotowych przykładowych](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="1bec1-295">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="1bec1-296">Wniosek</span><span class="sxs-lookup"><span data-stu-id="1bec1-296">Conclusion</span></span>

<span data-ttu-id="1bec1-297">W tym samouczku pokazano, jak wysyłać żądania sieci web, przeanalizować wynik i wyświetlić właściwości tych wyników.</span><span class="sxs-lookup"><span data-stu-id="1bec1-297">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="1bec1-298">Ponadto dodano nowe pakiety jako zależności w projekcie.</span><span class="sxs-lookup"><span data-stu-id="1bec1-298">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="1bec1-299">Przedstawiono niektóre funkcje języka C#, które obsługują technik zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="1bec1-299">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
