---
title: "Tworzenie klienta REST przy użyciu platformy .NET Core"
description: "Ten samouczek zawiera szereg funkcji .NET Core i języka C#."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 22391c4db3027c0fad2115c767b5e2808fee28a0
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="rest-client"></a><span data-ttu-id="a9262-104">Klient REST</span><span class="sxs-lookup"><span data-stu-id="a9262-104">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="a9262-105">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="a9262-105">Introduction</span></span>
<span data-ttu-id="a9262-106">Ten samouczek zawiera szereg funkcji .NET Core i języka C#.</span><span class="sxs-lookup"><span data-stu-id="a9262-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="a9262-107">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="a9262-107">You’ll learn:</span></span>
*   <span data-ttu-id="a9262-108">Podstawowe informacje dotyczące programu .NET Core interfejsu wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="a9262-108">The basics of the .NET Core Command Line Interface (CLI).</span></span>
*   <span data-ttu-id="a9262-109">Omówienie funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="a9262-109">An overview of C# Language features.</span></span>
*   <span data-ttu-id="a9262-110">Zarządzanie zależności nuget</span><span class="sxs-lookup"><span data-stu-id="a9262-110">Managing dependencies with NuGet</span></span>
*   <span data-ttu-id="a9262-111">Połączenia HTTP</span><span class="sxs-lookup"><span data-stu-id="a9262-111">HTTP Communications</span></span>
*   <span data-ttu-id="a9262-112">Przetwarzanie informacji dotyczących JSON</span><span class="sxs-lookup"><span data-stu-id="a9262-112">Processing JSON information</span></span>
*   <span data-ttu-id="a9262-113">Zarządzanie konfiguracją z atrybutami.</span><span class="sxs-lookup"><span data-stu-id="a9262-113">Managing configuration with Attributes.</span></span> 

<span data-ttu-id="a9262-114">Będzie utworzyć aplikację, która wystawia żądania HTTP dla usługi REST w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="a9262-114">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="a9262-115">Zostanie odczytu informacji w formacie JSON oraz konwersji pakietu JSON na obiekty C#.</span><span class="sxs-lookup"><span data-stu-id="a9262-115">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="a9262-116">Na koniec zostanie wyświetlone sposób pracy z obiektami C#.</span><span class="sxs-lookup"><span data-stu-id="a9262-116">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="a9262-117">Istnieje wiele funkcji, w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="a9262-117">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="a9262-118">Utworzymy je jeden po drugim.</span><span class="sxs-lookup"><span data-stu-id="a9262-118">Let’s build them one by one.</span></span>

<span data-ttu-id="a9262-119">Jeśli wolisz wykonaj, wraz z [próbki](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient) dla tego tematu możesz pobrać go.</span><span class="sxs-lookup"><span data-stu-id="a9262-119">If you prefer to follow along with the [final sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="a9262-120">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="a9262-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a9262-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a9262-121">Prerequisites</span></span>
<span data-ttu-id="a9262-122">Należy skonfigurować komputer z usługami .NET core.</span><span class="sxs-lookup"><span data-stu-id="a9262-122">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="a9262-123">Instrukcje instalacji można znaleźć na [.NET Core](https://www.microsoft.com/net/core) strony.</span><span class="sxs-lookup"><span data-stu-id="a9262-123">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="a9262-124">Można uruchomić tej aplikacji, w systemie Windows, Linux, macOS lub w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="a9262-124">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="a9262-125">Należy zainstalować w edytorze kodu dotyczącego elementów ulubionych.</span><span class="sxs-lookup"><span data-stu-id="a9262-125">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="a9262-126">Opisy poniżej użyj [Visual Studio Code](https://code.visualstudio.com/), która jest typu open source cross platform edytora.</span><span class="sxs-lookup"><span data-stu-id="a9262-126">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="a9262-127">Można jednak użyć dowolnego narzędzia potrafisz.</span><span class="sxs-lookup"><span data-stu-id="a9262-127">However, you can use whatever tools you are comfortable with.</span></span>
## <a name="create-the-application"></a><span data-ttu-id="a9262-128">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="a9262-128">Create the Application</span></span>
<span data-ttu-id="a9262-129">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9262-129">The first step is to create a new application.</span></span> <span data-ttu-id="a9262-130">Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9262-130">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="a9262-131">Upewnij się, że sposób bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="a9262-131">Make that the current directory.</span></span> <span data-ttu-id="a9262-132">Wpisz polecenie `dotnet new console` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a9262-132">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="a9262-133">Spowoduje to utworzenie plików starter podstawowe aplikacji "Hello World".</span><span class="sxs-lookup"><span data-stu-id="a9262-133">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="a9262-134">Przed wprowadzeniem modyfikacji przejdźmy do czynności, aby uruchomić prostej aplikacji Hello World.</span><span class="sxs-lookup"><span data-stu-id="a9262-134">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="a9262-135">Po utworzeniu aplikacji, wpisz `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a9262-135">After creating the application, type `dotnet restore` ([see note](#dotnet-restore-note)) at the command prompt.</span></span> <span data-ttu-id="a9262-136">To polecenie uruchamia proces przywracania pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="a9262-136">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="a9262-137">NuGet jest Menedżera pakietów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="a9262-137">NuGet is a .NET package manager.</span></span> <span data-ttu-id="a9262-138">To polecenie pobiera wszelkie brakujące zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="a9262-138">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="a9262-139">Jak jest to nowy projekt, Brak zależności są na miejscu, więc przy pierwszym uruchomieniu pobierze framework .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9262-139">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="a9262-140">Po wykonaniu tego kroku początkowego, wystarczy uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) podczas dodawania nowych pakietów zależnych lub zaktualizować wersje zależności.</span><span class="sxs-lookup"><span data-stu-id="a9262-140">After this initial step, you will only need to run `dotnet restore` ([see note](#dotnet-restore-note)) when you add new dependent packages, or update the versions of any of your dependencies.</span></span>  

<span data-ttu-id="a9262-141">Po przywróceniu pakietów, możesz uruchomić `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="a9262-141">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="a9262-142">Wykonuje aparat kompilacji i tworzy aplikację.</span><span class="sxs-lookup"><span data-stu-id="a9262-142">This executes the build engine and creates your application.</span></span> <span data-ttu-id="a9262-143">Na koniec wykonaj `dotnet run` do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9262-143">Finally, you execute `dotnet run` to run your application.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="a9262-144">Dodawanie nowych zależności</span><span class="sxs-lookup"><span data-stu-id="a9262-144">Adding New Dependencies</span></span>
<span data-ttu-id="a9262-145">Jest jednym z celów kluczy dla platformy .NET Core aby zminimalizować rozmiar instalacji programu .NET framework.</span><span class="sxs-lookup"><span data-stu-id="a9262-145">One of the key design goals for .NET Core is to minimize the size of the .NET framework installation.</span></span> <span data-ttu-id="a9262-146">Framework .NET Core aplikacji zawiera najbardziej typowe elementy pełna platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="a9262-146">The .NET Core Application framework contains only the most common elements of the .NET full framework.</span></span> <span data-ttu-id="a9262-147">Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych funkcji, Dodaj te zależności do projektu C# (\*.csproj) pliku.</span><span class="sxs-lookup"><span data-stu-id="a9262-147">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="a9262-148">W naszym przykładzie, musisz dodać `System.Runtime.Serialization.Json` pakietu dzięki aplikacji może przetworzyć odpowiedzi JSON.</span><span class="sxs-lookup"><span data-stu-id="a9262-148">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="a9262-149">Otwórz z `csproj` pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a9262-149">Open your `csproj` project file.</span></span> <span data-ttu-id="a9262-150">Pierwszy wiersz pliku powinny się wyświetlać jako:</span><span class="sxs-lookup"><span data-stu-id="a9262-150">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="a9262-151">Dodaj następujący kod bezpośrednio po tym wierszu:</span><span class="sxs-lookup"><span data-stu-id="a9262-151">Add the following immediately after this line:</span></span> 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
<span data-ttu-id="a9262-152">Większość edytory kodu zapewni uzupełnianie różne wersje tych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="a9262-152">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="a9262-153">Zwykle należy używać najnowszej wersji dowolnego pakietu, który zostanie dodany.</span><span class="sxs-lookup"><span data-stu-id="a9262-153">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="a9262-154">Jest jednak należy się upewnić, że wersje wszystkich pakietów zgodne i są również zgodne wersji platformy .NET Core aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9262-154">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="a9262-155">Po wprowadzeniu tych zmian, należy uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) ponownie, aby pakiet jest zainstalowany w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="a9262-155">After you've made these changes, you should run `dotnet restore` ([see note](#dotnet-restore-note)) again so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="a9262-156">Tworzenie żądania sieci Web</span><span class="sxs-lookup"><span data-stu-id="a9262-156">Making Web Requests</span></span>
<span data-ttu-id="a9262-157">Teraz możesz rozpocząć pobieranie danych z sieci web.</span><span class="sxs-lookup"><span data-stu-id="a9262-157">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="a9262-158">Ta aplikacja będzie odczytu informacji z [GitHub API](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="a9262-158">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="a9262-159">Załóżmy uzyskania informacji na temat projektów w ramach [.NET Foundation](http://www.dotnetfoundation.org/) parasola.</span><span class="sxs-lookup"><span data-stu-id="a9262-159">Let's read information about the projects under the [.NET Foundation](http://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="a9262-160">Można będzie uruchomić w żądaniu skierowanym do interfejsu API usługi GitHub można pobrać informacji dotyczących projektów.</span><span class="sxs-lookup"><span data-stu-id="a9262-160">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="a9262-161">Punkt końcowy będzie potrzebny jest: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span><span class="sxs-lookup"><span data-stu-id="a9262-161">The endpoint you'll use is: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span></span> <span data-ttu-id="a9262-162">Chcesz pobrać wszystkie informacje dotyczące tych projektów, więc użyjesz żądanie HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="a9262-162">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="a9262-163">Przeglądarka używa również żądania HTTP GET, więc możesz wkleić, że adres URL do przeglądarki, aby zobaczyć, jakie informacje należy będziesz otrzymywać i przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="a9262-163">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="a9262-164">Możesz użyć <xref:System.Net.Http.HttpClient> klasy żądań sieci web.</span><span class="sxs-lookup"><span data-stu-id="a9262-164">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="a9262-165">Wszystkie nowoczesne interfejsów API architektury .NET, takich jak <xref:System.Net.Http.HttpClient> obsługuje tylko asynchroniczne metody interfejsów API jego długotrwałe.</span><span class="sxs-lookup"><span data-stu-id="a9262-165">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="a9262-166">Rozpocznij metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="a9262-166">Start by making an async method.</span></span> <span data-ttu-id="a9262-167">Podczas tworzenia funkcjonalność aplikacji będzie Wypełnij implementacji.</span><span class="sxs-lookup"><span data-stu-id="a9262-167">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="a9262-168">Uruchamianie przez otwarcie `program.cs` plików w katalogu projektu i dodaniu następującą metodę do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="a9262-168">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    
}
```

<span data-ttu-id="a9262-169">Musisz dodać `using` instrukcji w górnej części programu `Main` metody co program rozpoznaje kompilatora C# <xref:System.Threading.Tasks.Task> typu:</span><span class="sxs-lookup"><span data-stu-id="a9262-169">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="a9262-170">Jeśli w tym momencie skompilowanie projektu uzyskasz ostrzeżenie wygenerowany dla tej metody, ponieważ nie zawiera żadnego `await` operatory i będzie wykonywana synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="a9262-170">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="a9262-171">Ignoruj, który obecnie; należy dodać `await` operatorów jako należy wypełnić w metodzie.</span><span class="sxs-lookup"><span data-stu-id="a9262-171">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="a9262-172">Następnie zmienić nazwę przestrzeń nazw zdefiniowana w `namespace` instrukcji domyślne `ConsoleApp` do `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="a9262-172">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="a9262-173">Później zdefiniujemy `repo` klasy w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a9262-173">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="a9262-174">Następnie zaktualizuj `Main` metodę do wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="a9262-174">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="a9262-175">`ProcessRepositories` Metoda zwraca zadania i nie należy zamknąć program przed zakończeniem tego zadania.</span><span class="sxs-lookup"><span data-stu-id="a9262-175">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="a9262-176">W związku z tym należy użyć `Wait` metodę, aby zablokować i poczekaj na zakończenie zadania:</span><span class="sxs-lookup"><span data-stu-id="a9262-176">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="a9262-177">Masz teraz program, który nie działa, ale nie jej asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="a9262-177">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="a9262-178">Załóżmy ją udoskonalać.</span><span class="sxs-lookup"><span data-stu-id="a9262-178">Let's improve it.</span></span>

<span data-ttu-id="a9262-179">Najpierw należy obiektu, który jest w stanie pobrać danych z sieci web; można użyć <xref:System.Net.Http.HttpClient> w tym celu.</span><span class="sxs-lookup"><span data-stu-id="a9262-179">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="a9262-180">Ten obiekt obsługuje żądania i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9262-180">This object handles the request and the responses.</span></span> <span data-ttu-id="a9262-181">Utworzyć pojedynczego wystąpienia tego typu w `Program` klasy w pliku Program.cs.</span><span class="sxs-lookup"><span data-stu-id="a9262-181">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

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

 <span data-ttu-id="a9262-182">Wróć do `ProcessRepositories` wypełnienia w pierwszej wersji i metody:</span><span class="sxs-lookup"><span data-stu-id="a9262-182">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="a9262-183">Musisz również dodać dwie nowe za pomocą instrukcji u góry pliku dla tego skompilować:</span><span class="sxs-lookup"><span data-stu-id="a9262-183">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="a9262-184">Ta wersja pierwszy sprawia, że żądania sieci web, aby zapoznać się z listą wszystkich repozytoriów w ramach organizacji foundation dotnet.</span><span class="sxs-lookup"><span data-stu-id="a9262-184">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="a9262-185">(Identyfikator gitHub .NET Foundation jest "dotnet").</span><span class="sxs-lookup"><span data-stu-id="a9262-185">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="a9262-186">Skonfiguruj kilka pierwszych wierszy <xref:System.Net.Http.HttpClient> dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="a9262-186">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="a9262-187">Najpierw jest skonfigurowany do akceptowania odpowiedzi GitHub JSON.</span><span class="sxs-lookup"><span data-stu-id="a9262-187">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="a9262-188">Ten format jest po prostu JSON.</span><span class="sxs-lookup"><span data-stu-id="a9262-188">This format is simply JSON.</span></span> <span data-ttu-id="a9262-189">Następnego wiersza dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a9262-189">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="a9262-190">Te dwa nagłówki są sprawdzane przez kod serwera GitHub i są niezbędne do pobrania informacji z usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="a9262-190">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="a9262-191">Po skonfigurowaniu <xref:System.Net.Http.HttpClient>, wprowadź sieci web żądania i pobierania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9262-191">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="a9262-192">W tej wersji pierwszej, użyj <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> wygodne metody.</span><span class="sxs-lookup"><span data-stu-id="a9262-192">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="a9262-193">Ta metoda wygody uruchamia zadanie, które wysyła żądanie sieci web, a następnie po powrocie z żądania go odczytuje w strumieniu odpowiedzi i wyodrębnia zawartość ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="a9262-193">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="a9262-194">Treść odpowiedzi jest zwracany jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a9262-194">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="a9262-195">Ten ciąg jest dostępna po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="a9262-195">The string is available when the task completes.</span></span> 

<span data-ttu-id="a9262-196">Końcowe dwa wiersze w tej metody await tego zadania, a następnie wydrukuj odpowiedzi do konsoli.</span><span class="sxs-lookup"><span data-stu-id="a9262-196">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="a9262-197">Tworzenie aplikacji i uruchom go.</span><span class="sxs-lookup"><span data-stu-id="a9262-197">Build the app, and run it.</span></span> <span data-ttu-id="a9262-198">Ostrzeżenie kompilacji zostanie usunięty, ponieważ `ProcessRepositories` teraz zawierać `await` operatora.</span><span class="sxs-lookup"><span data-stu-id="a9262-198">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="a9262-199">Zobaczysz, że dużo wyświetlanie JSON sformatowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="a9262-199">You'll see a long display of JSON formatted text.</span></span>   

## <a name="processing-the-json-result"></a><span data-ttu-id="a9262-200">Przetwarzanie wyniku JSON</span><span class="sxs-lookup"><span data-stu-id="a9262-200">Processing the JSON Result</span></span>

<span data-ttu-id="a9262-201">W tym momencie napisanych kod, aby pobrać odpowiedzi z serwera sieci web i wyświetlić tekst, który znajduje się w tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9262-201">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="a9262-202">Następnie możemy przekonwertować tę odpowiedź JSON na obiekty C#.</span><span class="sxs-lookup"><span data-stu-id="a9262-202">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="a9262-203">Serializator JSON konwertuje dane JSON na obiekty C#.</span><span class="sxs-lookup"><span data-stu-id="a9262-203">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="a9262-204">Najpierw jest określenie typu klasy C# zawierają informacje, które korzystać z tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9262-204">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="a9262-205">Tym powoli, utworzymy tak rozpoczyna się od prostego C# typu, który zawiera nazwę repozytorium:</span><span class="sxs-lookup"><span data-stu-id="a9262-205">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

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

<span data-ttu-id="a9262-206">Umieść kod powyżej w nowym pliku o nazwie "repo.cs".</span><span class="sxs-lookup"><span data-stu-id="a9262-206">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="a9262-207">Ta wersja klasy reprezentuje to najprostsza ścieżka do przetwarzania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="a9262-207">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="a9262-208">Nazwa klasy i nazwę elementu członkowskiego zgodne nazw używanych w pakiecie JSON zamiast następujących konwencji C#.</span><span class="sxs-lookup"><span data-stu-id="a9262-208">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="a9262-209">Użytkownik będzie rozwiązać ten problem, zapewniając niektóre atrybuty konfiguracji później.</span><span class="sxs-lookup"><span data-stu-id="a9262-209">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="a9262-210">Ta klasa przedstawia inną ważną funkcją JSON serializacji i deserializacji: nie wszystkie pola w pakiecie JSON są częścią tej klasy.</span><span class="sxs-lookup"><span data-stu-id="a9262-210">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="a9262-211">Serializator JSON zignoruje informacje, które nie są uwzględnione w typie klasy używane.</span><span class="sxs-lookup"><span data-stu-id="a9262-211">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="a9262-212">Ta funkcja umożliwia tworzenie typów współpracujących z tylko podzestaw pól w pakiecie JSON.</span><span class="sxs-lookup"><span data-stu-id="a9262-212">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="a9262-213">Teraz, po utworzeniu typu teraz do deserializacji.</span><span class="sxs-lookup"><span data-stu-id="a9262-213">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="a9262-214">Musisz utworzyć <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a9262-214">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="a9262-215">Ten obiekt musi znać typu CLR Oczekiwano pakietu JSON pobiera.</span><span class="sxs-lookup"><span data-stu-id="a9262-215">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="a9262-216">Pakiet z witryny GitHub zawiera sekwencję repozytoriów, więc `List<repo>` jest nieprawidłowego typu.</span><span class="sxs-lookup"><span data-stu-id="a9262-216">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="a9262-217">Dodaj następujący wiersz do Twojej `ProcessRepositories` metody:</span><span class="sxs-lookup"><span data-stu-id="a9262-217">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="a9262-218">Używasz dwóch nowych przestrzeni nazw, więc musisz dodać te również:</span><span class="sxs-lookup"><span data-stu-id="a9262-218">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="a9262-219">Następnie użyjesz serializatora do konwertowania JSON do obiektów C#.</span><span class="sxs-lookup"><span data-stu-id="a9262-219">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="a9262-220">Zastąp wywołanie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> w Twojej `ProcessRepositories` metody za pomocą następujących dwóch wierszy:</span><span class="sxs-lookup"><span data-stu-id="a9262-220">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="a9262-221">Należy zauważyć, że używasz teraz <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> zamiast <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="a9262-221">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="a9262-222">Serializator używa strumienia zamiast ciągu jako źródło.</span><span class="sxs-lookup"><span data-stu-id="a9262-222">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="a9262-223">Załóżmy opisano kilka funkcji języka C#, które są używane w drugim wierszu powyżej.</span><span class="sxs-lookup"><span data-stu-id="a9262-223">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="a9262-224">Argument <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> jest `await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a9262-224">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="a9262-225">Await wyrażenia może występować niemal z dowolnego miejsca w kodzie, nawet jeśli do chwili, tylko przedstawiono je w ramach instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="a9262-225">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="a9262-226">Po drugie `as` operator konwertuje z typu czasu kompilacji `object` do `List<repo>`.</span><span class="sxs-lookup"><span data-stu-id="a9262-226">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span> <span data-ttu-id="a9262-227">Deklaracja <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, że zwraca wartość typu obiektu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a9262-227">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a9262-228"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> Zwraca typ określony podczas jego skonstruowany (`List<repo>` w ramach tego samouczka).</span><span class="sxs-lookup"><span data-stu-id="a9262-228"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="a9262-229">Jeśli konwersja nie powiedzie się, `as` operatora daje w wyniku `null`, zamiast generowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a9262-229">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="a9262-230">Prawie gotowe z tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="a9262-230">You're almost done with this section.</span></span> <span data-ttu-id="a9262-231">Teraz, konwersji kodu JSON do obiektów C#, umożliwia wyświetlanie nazwy każdego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="a9262-231">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="a9262-232">Zamień wiersze do odczytu:</span><span class="sxs-lookup"><span data-stu-id="a9262-232">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="a9262-233">z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a9262-233">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="a9262-234">Kompilowanie i uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9262-234">Compile and run the application.</span></span> <span data-ttu-id="a9262-235">Będzie on Wydrukuj nazwy repozytoriów, które są częścią .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="a9262-235">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="a9262-236">Kontrolowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="a9262-236">Controlling Serialization</span></span>

<span data-ttu-id="a9262-237">Aby dodać więcej funkcji umożliwia adresów `repo` wpisać i dołączyć je zgodne z konwencjami więcej standard języka C#.</span><span class="sxs-lookup"><span data-stu-id="a9262-237">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="a9262-238">Można to zrobić przez dodawanie adnotacji do `repo` to typ *atrybuty* które kontrolują sposób działania serializator JSON.</span><span class="sxs-lookup"><span data-stu-id="a9262-238">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="a9262-239">W Twoim przypadku użyjesz tych atrybutów do definiowania mapowania między nazwami kluczy JSON oraz języka C# klasy i element członkowski nazwy.</span><span class="sxs-lookup"><span data-stu-id="a9262-239">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="a9262-240">Są dwa atrybuty używane `DataContract` atrybutu i `DataMember` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a9262-240">The two attributes used are the `DataContract` attribute and the `DataMember` attribute.</span></span> <span data-ttu-id="a9262-241">Konwencja, wszystkie klasy atrybutu kończyć się sufiksem `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="a9262-241">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="a9262-242">Nie trzeba jednak używają tego sufiksu, po zastosowaniu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a9262-242">However, you do not need to use that suffix when you apply an attribute.</span></span> 

<span data-ttu-id="a9262-243">`DataContract` i `DataMember` atrybutów znajdują się w innej biblioteki, musisz dodać do pliku projektu C# jako zależność tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="a9262-243">The `DataContract` and `DataMember` attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="a9262-244">Dodaj następujący wiersz do `<ItemGroup>` sekcji w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="a9262-244">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="a9262-245">Po zapisaniu pliku Uruchom `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) można pobrać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="a9262-245">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="a9262-246">Następnie otwórz folder `repo.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="a9262-246">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="a9262-247">Teraz Zmień nazwę Pascal przypadków użycia i pełni pełnych nazwę `Repository`.</span><span class="sxs-lookup"><span data-stu-id="a9262-247">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="a9262-248">Chcemy nadal mapowanie węzłów 'repozytorium' JSON do tego typu, musisz dodać `DataContract` atrybutu deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="a9262-248">We still want to map JSON 'repo' nodes to this type, so you'll need to add the `DataContract` attribute to the class declaration.</span></span> <span data-ttu-id="a9262-249">Zostanie ustawiona `Name` właściwości atrybutu nazwy węzłów JSON, które mapują do tego typu:</span><span class="sxs-lookup"><span data-stu-id="a9262-249">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="a9262-250"><xref:System.Runtime.Serialization.DataContractAttribute> Jest elementem członkowskim <xref:System.Runtime.Serialization> przestrzeni nazw, dlatego należy dodać odpowiednią `using` instrukcji w górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="a9262-250">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="a9262-251">Zmieniono nazwę `repo` klasy do `Repository`, więc musisz wprowadzić taką samą nazwę, zmiany w pliku Program.cs (niektóre edytory może obsługiwać Refaktoryzacja zmiany nazwy, która automatycznie wprowadzić tę zmianę:)</span><span class="sxs-lookup"><span data-stu-id="a9262-251">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="a9262-252">Następnie można wprowadzić te same zmiany z `name` pole przy użyciu <xref:System.Runtime.Serialization.DataMemberAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="a9262-252">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="a9262-253">Wprowadź następujące zmiany do deklaracji `name` w repo.cs:</span><span class="sxs-lookup"><span data-stu-id="a9262-253">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="a9262-254">Ta zmiana oznacza, że trzeba będzie zmienić kod, który zapisuje nazwy każdego repozytorium w pliku program.cs:</span><span class="sxs-lookup"><span data-stu-id="a9262-254">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="a9262-255">Czy `dotnet build` następuje `dotnet run` się upewnić, że masz mapowania poprawne.</span><span class="sxs-lookup"><span data-stu-id="a9262-255">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="a9262-256">Tych samych danych wyjściowych jako przed powinna zostać wyświetlona.</span><span class="sxs-lookup"><span data-stu-id="a9262-256">You should see the same output as before.</span></span> <span data-ttu-id="a9262-257">Przed możemy przetworzyć więcej właściwości z serwera sieci web, można wprowadzić jeden więcej zmiana `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="a9262-257">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="a9262-258">`Name` Element członkowski jest polem publicznie.</span><span class="sxs-lookup"><span data-stu-id="a9262-258">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="a9262-259">Nie jest dobrym rozwiązaniem zorientowane obiektowo, więc warto zmienić właściwości.</span><span class="sxs-lookup"><span data-stu-id="a9262-259">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="a9262-260">Dla naszych celów, firma Microsoft nie ma potrzeby żadnych szczególnych kod wymagany do uruchomienia podczas pobierania lub ustawiania właściwości, ale zmiana właściwości ułatwia później dodać tych zmian bez przerywania kodu, który używa `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="a9262-260">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="a9262-261">Usuń definicję pola i zastąp go przy użyciu [automatycznie implementowanej właściwości](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span><span class="sxs-lookup"><span data-stu-id="a9262-261">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="a9262-262">Kompilator generuje treści `get` i `set` metody dostępu, a także pole prywatne do przechowywania nazwy.</span><span class="sxs-lookup"><span data-stu-id="a9262-262">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="a9262-263">Mogą być podobne do następujący kod, który można ręcznie wpisać:</span><span class="sxs-lookup"><span data-stu-id="a9262-263">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="a9262-264">Można wprowadzić jeden więcej zmiany przed dodaniem nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9262-264">Let's make one more change before adding new features.</span></span> <span data-ttu-id="a9262-265">`ProcessRepositories` Metody można wykonywać zadania asynchronicznego i zwracać kolekcji repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="a9262-265">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="a9262-266">Możemy zwrócić `List<Repository>` z tej metody i Przenieś kod, który zapisuje informacje w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="a9262-266">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="a9262-267">Zmiana podpisu `ProcessRepositories` do zwrócenia zadania, których wynikiem jest lista z `Repository` obiektów:</span><span class="sxs-lookup"><span data-stu-id="a9262-267">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="a9262-268">Następnie tylko zwrócić repozytoria po przetworzeniu JSON odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="a9262-268">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="a9262-269">Kompilator generuje `Task<T>` obiektu dla zwracany, ponieważ został oznaczony tej metody jako `async`.</span><span class="sxs-lookup"><span data-stu-id="a9262-269">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="a9262-270">Następnie zmodyfikujmy `Main` metodę, tak aby przechwytywać tych wyników i zapisuje nazwy repozytorium do konsoli.</span><span class="sxs-lookup"><span data-stu-id="a9262-270">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="a9262-271">Twoje `Main` metody teraz wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="a9262-271">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="a9262-272">Uzyskiwanie dostępu do `Result` właściwości zadania blokuje dopiero po ukończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="a9262-272">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="a9262-273">Zwykle wolisz `await` ukończenia zadania, jak w `ProcessRepositories` metody, ale nie jest dozwolona w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="a9262-273">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="a9262-274">Odczytywanie więcej informacji</span><span class="sxs-lookup"><span data-stu-id="a9262-274">Reading More Information</span></span>

<span data-ttu-id="a9262-275">Teraz zakończyć to przez przetwarzanie kilka kolejnych właściwości w pakiecie JSON, które są wysyłane z interfejsu API usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="a9262-275">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="a9262-276">Nie ma do pobrania wszystko, ale Dodawanie kilka właściwości przedstawiono kilka więcej funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="a9262-276">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="a9262-277">Zacznijmy od dodania więcej kilka typów prostych do `Repository` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="a9262-277">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="a9262-278">Te właściwości są dodawane do tej klasy:</span><span class="sxs-lookup"><span data-stu-id="a9262-278">Add these properties to that class:</span></span>

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

<span data-ttu-id="a9262-279">Te właściwości mają wbudowane konwersji z typu ciąg (czyli zawierać pakiety JSON) na typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="a9262-279">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="a9262-280"><xref:System.Uri> Typu może być nowe dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="a9262-280">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="a9262-281">Reprezentuje identyfikator URI, lub w tym przypadku adresu URL.</span><span class="sxs-lookup"><span data-stu-id="a9262-281">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="a9262-282">W przypadku liczby `Uri` i `int` typy pakietów JSON zawiera dane, które nie konwertować na typ docelowy, akcja serializacji spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a9262-282">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="a9262-283">Po dodaniu tych aktualizacji `Main` metodę w celu wyświetlenia tych elementów:</span><span class="sxs-lookup"><span data-stu-id="a9262-283">Once you've added these, update the `Main` method to display those elements:</span></span>

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
<span data-ttu-id="a9262-284">Jako ostatni krok możemy dodać informacje z ostatniej operacji wypychania.</span><span class="sxs-lookup"><span data-stu-id="a9262-284">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="a9262-285">Te informacje jest sformatowany w ten sposób w formacie JSON odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="a9262-285">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="a9262-286">Ten format nie wykonuj żadnych standard .NET <xref:System.DateTime> formatów.</span><span class="sxs-lookup"><span data-stu-id="a9262-286">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="a9262-287">Z tego powodu konieczne jest napisanie metody konwersji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="a9262-287">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="a9262-288">Ponadto nie pożądane nieprzetworzony ciąg uwidoczniona dla użytkowników z `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="a9262-288">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="a9262-289">Atrybuty można kontrolować to również.</span><span class="sxs-lookup"><span data-stu-id="a9262-289">Attributes can help control that as well.</span></span> <span data-ttu-id="a9262-290">Najpierw należy zdefiniować `private` właściwości, w którym będą przechowywane reprezentację ciągu daty godziny w Twojej `Repository` klasy:</span><span class="sxs-lookup"><span data-stu-id="a9262-290">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="a9262-291">`DataMember` Atrybut informuje serializator czy to powinna zostać przetworzona, mimo że nie jest publicznym elementem członkowskim.</span><span class="sxs-lookup"><span data-stu-id="a9262-291">The `DataMember` attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="a9262-292">Następnie należy napisać publicznej właściwości tylko do odczytu, który konwertuje ciąg na prawidłową <xref:System.DateTime> obiektu i zwraca go <xref:System.DateTime>:</span><span class="sxs-lookup"><span data-stu-id="a9262-292">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

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

<span data-ttu-id="a9262-293">Przejdź przez nowe konstrukcje powyżej.</span><span class="sxs-lookup"><span data-stu-id="a9262-293">Let's go over the new constructs above.</span></span> <span data-ttu-id="a9262-294">`IgnoreDataMember` Atrybut serializator informuje, że ten typ nie należy do odczytu ani zapisywane z dowolnych obiektów JSON.</span><span class="sxs-lookup"><span data-stu-id="a9262-294">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="a9262-295">Ta właściwość zawiera tylko `get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="a9262-295">This property contains only a `get` accessor.</span></span> <span data-ttu-id="a9262-296">Brak nie `set` dostępu.</span><span class="sxs-lookup"><span data-stu-id="a9262-296">There is no `set` accessor.</span></span> <span data-ttu-id="a9262-297">To, jak zdefiniować *tylko do odczytu* właściwości w języku C#.</span><span class="sxs-lookup"><span data-stu-id="a9262-297">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="a9262-298">(Tak, możesz utworzyć *tylko do zapisu* wynosi właściwości w języku C#, ale ich wartości.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Metody analizowania ciągu i tworzy <xref:System.DateTime> przy użyciu formatu podana wartość daty i dodaje dodatkowe metadane na `DateTime` przy użyciu `CultureInfo` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a9262-298">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="a9262-299">W przypadku niepowodzenia operacji analizowania metody dostępu właściwości zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a9262-299">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="a9262-300">Aby użyć <xref:System.Globalization.CultureInfo.InvariantCulture>, należy dodać <xref:System.Globalization> przestrzeni nazw do `using` instrukcje w `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="a9262-300">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="a9262-301">Na koniec należy dodać więcej jeden wyjściowy instrukcji w konsoli i wszystko jest gotowe do tworzenia i ponownie uruchom tę aplikację:</span><span class="sxs-lookup"><span data-stu-id="a9262-301">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="a9262-302">Używana wersja teraz powinna być zgodna. [gotowej próbki](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="a9262-302">Your version should now match the [finished sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient).</span></span>
 
## <a name="conclusion"></a><span data-ttu-id="a9262-303">Wniosek</span><span class="sxs-lookup"><span data-stu-id="a9262-303">Conclusion</span></span>

<span data-ttu-id="a9262-304">W tym samouczku pokazano, jak żądania sieci web, wynik analizy i Wyświetl właściwości tych wyników.</span><span class="sxs-lookup"><span data-stu-id="a9262-304">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="a9262-305">Możesz także dodano nowe pakiety jako zależności w projekcie.</span><span class="sxs-lookup"><span data-stu-id="a9262-305">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="a9262-306">Przedstawiono niektóre funkcje języka C# obsługujące zorientowane obiektowo technik.</span><span class="sxs-lookup"><span data-stu-id="a9262-306">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
