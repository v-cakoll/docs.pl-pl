---
title: "Tworzenie klienta REST przy użyciu platformy .NET Core"
description: "Ten samouczek zawiera szereg funkcji .NET Core i języka C#."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: bc74b644f432071dc2483e8df3e0938c9e9ee025
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2017
---
# <a name="rest-client"></a><span data-ttu-id="21b2f-104">Klient REST</span><span class="sxs-lookup"><span data-stu-id="21b2f-104">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="21b2f-105">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="21b2f-105">Introduction</span></span>
<span data-ttu-id="21b2f-106">Ten samouczek zawiera szereg funkcji .NET Core i języka C#.</span><span class="sxs-lookup"><span data-stu-id="21b2f-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="21b2f-107">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="21b2f-107">You’ll learn:</span></span>
*   <span data-ttu-id="21b2f-108">Podstawowe informacje dotyczące programu .NET Core interfejsu wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="21b2f-108">The basics of the .NET Core Command Line Interface (CLI).</span></span>
*   <span data-ttu-id="21b2f-109">Omówienie funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="21b2f-109">An overview of C# Language features.</span></span>
*   <span data-ttu-id="21b2f-110">Zarządzanie zależności nuget</span><span class="sxs-lookup"><span data-stu-id="21b2f-110">Managing dependencies with NuGet</span></span>
*   <span data-ttu-id="21b2f-111">Połączenia HTTP</span><span class="sxs-lookup"><span data-stu-id="21b2f-111">HTTP Communications</span></span>
*   <span data-ttu-id="21b2f-112">Przetwarzanie informacji dotyczących JSON</span><span class="sxs-lookup"><span data-stu-id="21b2f-112">Processing JSON information</span></span>
*   <span data-ttu-id="21b2f-113">Zarządzanie konfiguracją z atrybutami.</span><span class="sxs-lookup"><span data-stu-id="21b2f-113">Managing configuration with Attributes.</span></span> 

<span data-ttu-id="21b2f-114">Będzie utworzyć aplikację, która wystawia żądania HTTP dla usługi REST w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="21b2f-114">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="21b2f-115">Zostanie odczytu informacji w formacie JSON oraz konwersji pakietu JSON na obiekty C#.</span><span class="sxs-lookup"><span data-stu-id="21b2f-115">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="21b2f-116">Na koniec zostanie wyświetlone sposób pracy z obiektami C#.</span><span class="sxs-lookup"><span data-stu-id="21b2f-116">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="21b2f-117">Istnieje wiele funkcji, w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="21b2f-117">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="21b2f-118">Utworzymy je jeden po drugim.</span><span class="sxs-lookup"><span data-stu-id="21b2f-118">Let’s build them one by one.</span></span>

<span data-ttu-id="21b2f-119">Jeśli wolisz wykonaj, wraz z [próbki](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient) dla tego tematu możesz pobrać go.</span><span class="sxs-lookup"><span data-stu-id="21b2f-119">If you prefer to follow along with the [final sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="21b2f-120">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="21b2f-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="21b2f-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="21b2f-121">Prerequisites</span></span>
<span data-ttu-id="21b2f-122">Należy skonfigurować komputer z usługami .NET core.</span><span class="sxs-lookup"><span data-stu-id="21b2f-122">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="21b2f-123">Instrukcje instalacji można znaleźć na [.NET Core](https://www.microsoft.com/net/core) strony.</span><span class="sxs-lookup"><span data-stu-id="21b2f-123">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="21b2f-124">Można uruchomić tej aplikacji, w systemie Windows, Linux, macOS lub w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="21b2f-124">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="21b2f-125">Należy zainstalować w edytorze kodu dotyczącego elementów ulubionych.</span><span class="sxs-lookup"><span data-stu-id="21b2f-125">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="21b2f-126">Opisy poniżej użyj [Visual Studio Code](https://code.visualstudio.com/), która jest typu open source cross platform edytora.</span><span class="sxs-lookup"><span data-stu-id="21b2f-126">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="21b2f-127">Można jednak użyć dowolnego narzędzia potrafisz.</span><span class="sxs-lookup"><span data-stu-id="21b2f-127">However, you can use whatever tools you are comfortable with.</span></span>
## <a name="create-the-application"></a><span data-ttu-id="21b2f-128">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="21b2f-128">Create the Application</span></span>
<span data-ttu-id="21b2f-129">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21b2f-129">The first step is to create a new application.</span></span> <span data-ttu-id="21b2f-130">Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21b2f-130">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="21b2f-131">Upewnij się, że sposób bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="21b2f-131">Make that the current directory.</span></span> <span data-ttu-id="21b2f-132">Wpisz polecenie `dotnet new console` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="21b2f-132">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="21b2f-133">Spowoduje to utworzenie plików starter podstawowe aplikacji "Hello World".</span><span class="sxs-lookup"><span data-stu-id="21b2f-133">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="21b2f-134">Przed wprowadzeniem modyfikacji przejdźmy do czynności, aby uruchomić prostej aplikacji Hello World.</span><span class="sxs-lookup"><span data-stu-id="21b2f-134">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="21b2f-135">Po utworzeniu aplikacji, wpisz `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="21b2f-135">After creating the application, type `dotnet restore` ([see note](#dotnet-restore-note)) at the command prompt.</span></span> <span data-ttu-id="21b2f-136">To polecenie uruchamia proces przywracania pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="21b2f-136">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="21b2f-137">NuGet jest Menedżera pakietów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="21b2f-137">NuGet is a .NET package manager.</span></span> <span data-ttu-id="21b2f-138">To polecenie pobiera wszelkie brakujące zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="21b2f-138">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="21b2f-139">Jak jest to nowy projekt, Brak zależności są na miejscu, więc przy pierwszym uruchomieniu pobierze framework .NET Core.</span><span class="sxs-lookup"><span data-stu-id="21b2f-139">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="21b2f-140">Po wykonaniu tego kroku początkowego, wystarczy uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) podczas dodawania nowych pakietów zależnych lub zaktualizować wersje zależności.</span><span class="sxs-lookup"><span data-stu-id="21b2f-140">After this initial step, you will only need to run `dotnet restore` ([see note](#dotnet-restore-note)) when you add new dependent packages, or update the versions of any of your dependencies.</span></span>  

<span data-ttu-id="21b2f-141">Po przywróceniu pakietów, możesz uruchomić `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="21b2f-141">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="21b2f-142">Wykonuje aparat kompilacji i tworzy aplikację.</span><span class="sxs-lookup"><span data-stu-id="21b2f-142">This executes the build engine and creates your application.</span></span> <span data-ttu-id="21b2f-143">Na koniec wykonaj `dotnet run` do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21b2f-143">Finally, you execute `dotnet run` to run your application.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="21b2f-144">Dodawanie nowych zależności</span><span class="sxs-lookup"><span data-stu-id="21b2f-144">Adding New Dependencies</span></span>
<span data-ttu-id="21b2f-145">Jest jednym z celów kluczy dla platformy .NET Core aby zminimalizować rozmiar instalacji programu .NET framework.</span><span class="sxs-lookup"><span data-stu-id="21b2f-145">One of the key design goals for .NET Core is to minimize the size of the .NET framework installation.</span></span> <span data-ttu-id="21b2f-146">Framework .NET Core aplikacji zawiera najbardziej typowe elementy pełna platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="21b2f-146">The .NET Core Application framework contains only the most common elements of the .NET full framework.</span></span> <span data-ttu-id="21b2f-147">Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych funkcji, Dodaj te zależności do projektu C# (\*.csproj) pliku.</span><span class="sxs-lookup"><span data-stu-id="21b2f-147">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="21b2f-148">W naszym przykładzie, musisz dodać `System.Runtime.Serialization.Json` pakietu dzięki aplikacji może przetworzyć odpowiedzi JSON.</span><span class="sxs-lookup"><span data-stu-id="21b2f-148">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="21b2f-149">Otwórz z `csproj` pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="21b2f-149">Open your `csproj` project file.</span></span> <span data-ttu-id="21b2f-150">Pierwszy wiersz pliku powinny się wyświetlać jako:</span><span class="sxs-lookup"><span data-stu-id="21b2f-150">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="21b2f-151">Dodaj następujący kod bezpośrednio po tym wierszu:</span><span class="sxs-lookup"><span data-stu-id="21b2f-151">Add the following immediately after this line:</span></span> 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
<span data-ttu-id="21b2f-152">Większość edytory kodu zapewni uzupełnianie różne wersje tych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="21b2f-152">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="21b2f-153">Zwykle należy używać najnowszej wersji dowolnego pakietu, który zostanie dodany.</span><span class="sxs-lookup"><span data-stu-id="21b2f-153">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="21b2f-154">Jest jednak należy się upewnić, że wersje wszystkich pakietów zgodne i są również zgodne wersji platformy .NET Core aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21b2f-154">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="21b2f-155">Po wprowadzeniu tych zmian, należy uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) ponownie, aby pakiet jest zainstalowany w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="21b2f-155">After you've made these changes, you should run `dotnet restore` ([see note](#dotnet-restore-note)) again so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="21b2f-156">Tworzenie żądania sieci Web</span><span class="sxs-lookup"><span data-stu-id="21b2f-156">Making Web Requests</span></span>
<span data-ttu-id="21b2f-157">Teraz możesz rozpocząć pobieranie danych z sieci web.</span><span class="sxs-lookup"><span data-stu-id="21b2f-157">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="21b2f-158">Ta aplikacja będzie odczytu informacji z [GitHub API](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="21b2f-158">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="21b2f-159">Załóżmy uzyskania informacji na temat projektów w ramach [.NET Foundation](http://www.dotnetfoundation.org/) parasola.</span><span class="sxs-lookup"><span data-stu-id="21b2f-159">Let's read information about the projects under the [.NET Foundation](http://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="21b2f-160">Można będzie uruchomić w żądaniu skierowanym do interfejsu API usługi GitHub można pobrać informacji dotyczących projektów.</span><span class="sxs-lookup"><span data-stu-id="21b2f-160">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="21b2f-161">Punkt końcowy będzie potrzebny jest: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span><span class="sxs-lookup"><span data-stu-id="21b2f-161">The endpoint you'll use is: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span></span> <span data-ttu-id="21b2f-162">Chcesz pobrać wszystkie informacje dotyczące tych projektów, więc użyjesz żądanie HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="21b2f-162">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="21b2f-163">Przeglądarka używa również żądania HTTP GET, więc możesz wkleić, że adres URL do przeglądarki, aby zobaczyć, jakie informacje należy będziesz otrzymywać i przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="21b2f-163">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="21b2f-164">Możesz użyć <xref:System.Net.Http.HttpClient> klasy żądań sieci web.</span><span class="sxs-lookup"><span data-stu-id="21b2f-164">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="21b2f-165">Wszystkie nowoczesne interfejsów API architektury .NET, takich jak <xref:System.Net.Http.HttpClient> obsługuje tylko asynchroniczne metody interfejsów API jego długotrwałe.</span><span class="sxs-lookup"><span data-stu-id="21b2f-165">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="21b2f-166">Rozpocznij metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="21b2f-166">Start by making an async method.</span></span> <span data-ttu-id="21b2f-167">Podczas tworzenia funkcjonalność aplikacji będzie Wypełnij implementacji.</span><span class="sxs-lookup"><span data-stu-id="21b2f-167">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="21b2f-168">Uruchamianie przez otwarcie `program.cs` plików w katalogu projektu i dodaniu następującą metodę do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="21b2f-168">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    
}
```

<span data-ttu-id="21b2f-169">Musisz dodać `using` instrukcji w górnej części programu `Main` metody co program rozpoznaje kompilatora C# <xref:System.Threading.Tasks.Task> typu:</span><span class="sxs-lookup"><span data-stu-id="21b2f-169">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="21b2f-170">Jeśli w tym momencie skompilowanie projektu uzyskasz ostrzeżenie wygenerowany dla tej metody, ponieważ nie zawiera żadnego `await` operatory i będzie wykonywana synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="21b2f-170">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="21b2f-171">Ignoruj, który obecnie; należy dodać `await` operatorów jako należy wypełnić w metodzie.</span><span class="sxs-lookup"><span data-stu-id="21b2f-171">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="21b2f-172">Następnie zmienić nazwę przestrzeń nazw zdefiniowana w `namespace` instrukcji domyślne `ConsoleApp` do `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="21b2f-172">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="21b2f-173">Później zdefiniujemy `repo` klasy w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="21b2f-173">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="21b2f-174">Następnie zaktualizuj `Main` metodę do wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="21b2f-174">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="21b2f-175">`ProcessRepositories` Metoda zwraca zadania i nie należy zamknąć program przed zakończeniem tego zadania.</span><span class="sxs-lookup"><span data-stu-id="21b2f-175">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="21b2f-176">W związku z tym należy użyć `Wait` metodę, aby zablokować i poczekaj na zakończenie zadania:</span><span class="sxs-lookup"><span data-stu-id="21b2f-176">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
public static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="21b2f-177">Masz teraz program, który nie działa, ale nie jej asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="21b2f-177">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="21b2f-178">Wróć do `ProcessRepositories` wypełnienia w pierwszej wersji i metody:</span><span class="sxs-lookup"><span data-stu-id="21b2f-178">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    var client = new HttpClient();
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

<span data-ttu-id="21b2f-179">Musisz również dodać dwie nowe za pomocą instrukcji u góry pliku dla tego skompilować:</span><span class="sxs-lookup"><span data-stu-id="21b2f-179">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="21b2f-180">Ta wersja pierwszy sprawia, że żądania sieci web, aby zapoznać się z listą wszystkich repozytoriów w ramach organizacji foundation dotnet.</span><span class="sxs-lookup"><span data-stu-id="21b2f-180">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="21b2f-181">(Identyfikator gitHub .NET Foundation jest "dotnet").</span><span class="sxs-lookup"><span data-stu-id="21b2f-181">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="21b2f-182">Najpierw należy utworzyć nowy <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="21b2f-182">First, you create a new <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="21b2f-183">Ten obiekt obsługuje żądania i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="21b2f-183">This object handles the request and the responses.</span></span> <span data-ttu-id="21b2f-184">Skonfiguruj dalej kilka wierszy <xref:System.Net.Http.HttpClient> dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="21b2f-184">The next few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="21b2f-185">Najpierw jest skonfigurowany do akceptowania odpowiedzi GitHub JSON.</span><span class="sxs-lookup"><span data-stu-id="21b2f-185">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="21b2f-186">Ten format jest po prostu JSON.</span><span class="sxs-lookup"><span data-stu-id="21b2f-186">This format is simply JSON.</span></span> <span data-ttu-id="21b2f-187">Następnego wiersza dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="21b2f-187">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="21b2f-188">Te dwa nagłówki są sprawdzane przez kod serwera GitHub i są niezbędne do pobrania informacji z usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="21b2f-188">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="21b2f-189">Po skonfigurowaniu <xref:System.Net.Http.HttpClient>, wprowadź sieci web żądania i pobierania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="21b2f-189">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="21b2f-190">W tej wersji pierwszej, użyj <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> wygodne metody.</span><span class="sxs-lookup"><span data-stu-id="21b2f-190">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="21b2f-191">Ta metoda wygody uruchamia zadanie, które wysyła żądanie sieci web, a następnie po powrocie z żądania go odczytuje w strumieniu odpowiedzi i wyodrębnia zawartość ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="21b2f-191">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="21b2f-192">Treść odpowiedzi jest zwracany jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="21b2f-192">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="21b2f-193">Ten ciąg jest dostępna po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="21b2f-193">The string is available when the task completes.</span></span> 

<span data-ttu-id="21b2f-194">Końcowe dwa wiersze w tej metody await tego zadania, a następnie wydrukuj odpowiedzi do konsoli.</span><span class="sxs-lookup"><span data-stu-id="21b2f-194">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="21b2f-195">Tworzenie aplikacji i uruchom go.</span><span class="sxs-lookup"><span data-stu-id="21b2f-195">Build the app, and run it.</span></span> <span data-ttu-id="21b2f-196">Ostrzeżenie kompilacji zostanie usunięty, ponieważ `ProcessRepositories` teraz zawierać `await` operatora.</span><span class="sxs-lookup"><span data-stu-id="21b2f-196">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="21b2f-197">Zobaczysz, że dużo wyświetlanie JSON sformatowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="21b2f-197">You'll see a long display of JSON formatted text.</span></span>   

## <a name="processing-the-json-result"></a><span data-ttu-id="21b2f-198">Przetwarzanie wyniku JSON</span><span class="sxs-lookup"><span data-stu-id="21b2f-198">Processing the JSON Result</span></span>

<span data-ttu-id="21b2f-199">W tym momencie napisanych kod, aby pobrać odpowiedzi z serwera sieci web i wyświetlić tekst, który znajduje się w tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="21b2f-199">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="21b2f-200">Następnie możemy przekonwertować tę odpowiedź JSON na obiekty C#.</span><span class="sxs-lookup"><span data-stu-id="21b2f-200">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="21b2f-201">Serializator JSON konwertuje dane JSON na obiekty C#.</span><span class="sxs-lookup"><span data-stu-id="21b2f-201">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="21b2f-202">Najpierw jest określenie typu klasy C# zawierają informacje, które korzystać z tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="21b2f-202">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="21b2f-203">Tym powoli, utworzymy tak rozpoczyna się od prostego C# typu, który zawiera nazwę repozytorium:</span><span class="sxs-lookup"><span data-stu-id="21b2f-203">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

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

<span data-ttu-id="21b2f-204">Umieść kod powyżej w nowym pliku o nazwie "repo.cs".</span><span class="sxs-lookup"><span data-stu-id="21b2f-204">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="21b2f-205">Ta wersja klasy reprezentuje to najprostsza ścieżka do przetwarzania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="21b2f-205">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="21b2f-206">Nazwa klasy i nazwę elementu członkowskiego zgodne nazw używanych w pakiecie JSON zamiast następujących konwencji C#.</span><span class="sxs-lookup"><span data-stu-id="21b2f-206">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="21b2f-207">Użytkownik będzie rozwiązać ten problem, zapewniając niektóre atrybuty konfiguracji później.</span><span class="sxs-lookup"><span data-stu-id="21b2f-207">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="21b2f-208">Ta klasa przedstawia inną ważną funkcją JSON serializacji i deserializacji: nie wszystkie pola w pakiecie JSON są częścią tej klasy.</span><span class="sxs-lookup"><span data-stu-id="21b2f-208">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="21b2f-209">Serializator JSON zignoruje informacje, które nie są uwzględnione w typie klasy używane.</span><span class="sxs-lookup"><span data-stu-id="21b2f-209">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="21b2f-210">Ta funkcja umożliwia tworzenie typów współpracujących z tylko podzestaw pól w pakiecie JSON.</span><span class="sxs-lookup"><span data-stu-id="21b2f-210">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="21b2f-211">Teraz, po utworzeniu typu teraz do deserializacji.</span><span class="sxs-lookup"><span data-stu-id="21b2f-211">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="21b2f-212">Musisz utworzyć <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obiektu.</span><span class="sxs-lookup"><span data-stu-id="21b2f-212">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="21b2f-213">Ten obiekt musi znać typu CLR Oczekiwano pakietu JSON pobiera.</span><span class="sxs-lookup"><span data-stu-id="21b2f-213">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="21b2f-214">Pakiet z witryny GitHub zawiera sekwencję repozytoriów, więc `List<repo>` jest nieprawidłowego typu.</span><span class="sxs-lookup"><span data-stu-id="21b2f-214">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="21b2f-215">Dodaj następujący wiersz do Twojej `ProcessRepositories` metody:</span><span class="sxs-lookup"><span data-stu-id="21b2f-215">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="21b2f-216">Używasz dwóch nowych przestrzeni nazw, więc musisz dodać te również:</span><span class="sxs-lookup"><span data-stu-id="21b2f-216">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="21b2f-217">Następnie użyjesz serializatora do konwertowania JSON do obiektów C#.</span><span class="sxs-lookup"><span data-stu-id="21b2f-217">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="21b2f-218">Zastąp wywołanie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> w Twojej `ProcessRepositories` metody za pomocą następujących dwóch wierszy:</span><span class="sxs-lookup"><span data-stu-id="21b2f-218">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="21b2f-219">Należy zauważyć, że używasz teraz <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> zamiast <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="21b2f-219">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="21b2f-220">Serializator używa strumienia zamiast ciągu jako źródło.</span><span class="sxs-lookup"><span data-stu-id="21b2f-220">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="21b2f-221">Załóżmy opisano kilka funkcji języka C#, które są używane w drugim wierszu powyżej.</span><span class="sxs-lookup"><span data-stu-id="21b2f-221">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="21b2f-222">Argument <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> jest `await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="21b2f-222">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="21b2f-223">Await wyrażenia może występować niemal z dowolnego miejsca w kodzie, nawet jeśli do chwili, tylko przedstawiono je w ramach instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="21b2f-223">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="21b2f-224">Po drugie `as` operator konwertuje z typu czasu kompilacji `object` do `List<repo>`.</span><span class="sxs-lookup"><span data-stu-id="21b2f-224">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span> <span data-ttu-id="21b2f-225">Deklaracja <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, że zwraca wartość typu obiektu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="21b2f-225">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="21b2f-226"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)>Zwraca typ określony podczas jego skonstruowany (`List<repo>` w ramach tego samouczka).</span><span class="sxs-lookup"><span data-stu-id="21b2f-226"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="21b2f-227">Jeśli konwersja nie powiedzie się, `as` operatora daje w wyniku `null`, zamiast generowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="21b2f-227">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="21b2f-228">Prawie gotowe z tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="21b2f-228">You're almost done with this section.</span></span> <span data-ttu-id="21b2f-229">Teraz, konwersji kodu JSON do obiektów C#, umożliwia wyświetlanie nazwy każdego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="21b2f-229">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="21b2f-230">Zamień wiersze do odczytu:</span><span class="sxs-lookup"><span data-stu-id="21b2f-230">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="21b2f-231">z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="21b2f-231">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="21b2f-232">Kompilowanie i uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21b2f-232">Compile and run the application.</span></span> <span data-ttu-id="21b2f-233">Będzie on Wydrukuj nazwy repozytoriów, które są częścią .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="21b2f-233">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="21b2f-234">Kontrolowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="21b2f-234">Controlling Serialization</span></span>

<span data-ttu-id="21b2f-235">Aby dodać więcej funkcji umożliwia adresów `repo` wpisać i dołączyć je zgodne z konwencjami więcej standard języka C#.</span><span class="sxs-lookup"><span data-stu-id="21b2f-235">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="21b2f-236">Można to zrobić przez dodawanie adnotacji do `repo` to typ *atrybuty* które kontrolują sposób działania serializator JSON.</span><span class="sxs-lookup"><span data-stu-id="21b2f-236">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="21b2f-237">W Twoim przypadku użyjesz tych atrybutów do definiowania mapowania między nazwami kluczy JSON oraz języka C# klasy i element członkowski nazwy.</span><span class="sxs-lookup"><span data-stu-id="21b2f-237">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="21b2f-238">Są dwa atrybuty używane `DataContract` atrybutu i `DataMember` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="21b2f-238">The two attributes used are the `DataContract` attribute and the `DataMember` attribute.</span></span> <span data-ttu-id="21b2f-239">Konwencja, wszystkie klasy atrybutu kończyć się sufiksem `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="21b2f-239">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="21b2f-240">Nie trzeba jednak używają tego sufiksu, po zastosowaniu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="21b2f-240">However, you do not need to use that suffix when you apply an attribute.</span></span> 

<span data-ttu-id="21b2f-241">`DataContract` i `DataMember` atrybutów znajdują się w innej biblioteki, musisz dodać do pliku projektu C# jako zależność tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="21b2f-241">The `DataContract` and `DataMember` attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="21b2f-242">Dodaj następujący wiersz do `<ItemGroup>` sekcji w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="21b2f-242">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="21b2f-243">Po zapisaniu pliku Uruchom `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) można pobrać tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="21b2f-243">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="21b2f-244">Następnie otwórz folder `repo.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="21b2f-244">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="21b2f-245">Teraz Zmień nazwę Pascal przypadków użycia i pełni pełnych nazwę `Repository`.</span><span class="sxs-lookup"><span data-stu-id="21b2f-245">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="21b2f-246">Chcemy nadal mapowanie węzłów 'repozytorium' JSON do tego typu, musisz dodać `DataContract` atrybutu deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="21b2f-246">We still want to map JSON 'repo' nodes to this type, so you'll need to add the `DataContract` attribute to the class declaration.</span></span> <span data-ttu-id="21b2f-247">Zostanie ustawiona `Name` właściwości atrybutu nazwy węzłów JSON, które mapują do tego typu:</span><span class="sxs-lookup"><span data-stu-id="21b2f-247">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="21b2f-248"><xref:System.Runtime.Serialization.DataContractAttribute> Jest elementem członkowskim <xref:System.Runtime.Serialization> przestrzeni nazw, dlatego należy dodać odpowiednią `using` instrukcji w górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="21b2f-248">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="21b2f-249">Zmieniono nazwę `repo` klasy do `Repository`, więc musisz wprowadzić taką samą nazwę, zmiany w pliku Program.cs (niektóre edytory może obsługiwać Refaktoryzacja zmiany nazwy, która automatycznie wprowadzić tę zmianę:)</span><span class="sxs-lookup"><span data-stu-id="21b2f-249">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="21b2f-250">Następnie można wprowadzić te same zmiany z `name` pole przy użyciu <xref:System.Runtime.Serialization.DataMemberAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="21b2f-250">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="21b2f-251">Wprowadź następujące zmiany do deklaracji `name` w repo.cs:</span><span class="sxs-lookup"><span data-stu-id="21b2f-251">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="21b2f-252">Ta zmiana oznacza, że trzeba będzie zmienić kod, który zapisuje nazwy każdego repozytorium w pliku program.cs:</span><span class="sxs-lookup"><span data-stu-id="21b2f-252">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="21b2f-253">Czy `dotnet build` następuje `dotnet run` się upewnić, że masz mapowania poprawne.</span><span class="sxs-lookup"><span data-stu-id="21b2f-253">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="21b2f-254">Tych samych danych wyjściowych jako przed powinna zostać wyświetlona.</span><span class="sxs-lookup"><span data-stu-id="21b2f-254">You should see the same output as before.</span></span> <span data-ttu-id="21b2f-255">Przed możemy przetworzyć więcej właściwości z serwera sieci web, można wprowadzić jeden więcej zmiana `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="21b2f-255">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="21b2f-256">`Name` Element członkowski jest polem publicznie.</span><span class="sxs-lookup"><span data-stu-id="21b2f-256">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="21b2f-257">Nie jest dobrym rozwiązaniem zorientowane obiektowo, więc warto zmienić właściwości.</span><span class="sxs-lookup"><span data-stu-id="21b2f-257">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="21b2f-258">Dla naszych celów, firma Microsoft nie ma potrzeby żadnych szczególnych kod wymagany do uruchomienia podczas pobierania lub ustawiania właściwości, ale zmiana właściwości ułatwia później dodać tych zmian bez przerywania kodu, który używa `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="21b2f-258">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="21b2f-259">Usuń definicję pola i zastąp go przy użyciu [automatycznie implementowanej właściwości](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span><span class="sxs-lookup"><span data-stu-id="21b2f-259">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="21b2f-260">Kompilator generuje treści `get` i `set` metody dostępu, a także pole prywatne do przechowywania nazwy.</span><span class="sxs-lookup"><span data-stu-id="21b2f-260">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="21b2f-261">Mogą być podobne do następujący kod, który można ręcznie wpisać:</span><span class="sxs-lookup"><span data-stu-id="21b2f-261">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="21b2f-262">Można wprowadzić jeden więcej zmiany przed dodaniem nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="21b2f-262">Let's make one more change before adding new features.</span></span> <span data-ttu-id="21b2f-263">`ProcessRepositories` Metody można wykonywać zadania asynchronicznego i zwracać kolekcji repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="21b2f-263">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="21b2f-264">Możemy zwrócić `List<Repository>` z tej metody i Przenieś kod, który zapisuje informacje w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="21b2f-264">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="21b2f-265">Zmiana podpisu `ProcessRepositories` do zwrócenia zadania, których wynikiem jest lista z `Repository` obiektów:</span><span class="sxs-lookup"><span data-stu-id="21b2f-265">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="21b2f-266">Następnie tylko zwrócić repozytoria po przetworzeniu JSON odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="21b2f-266">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="21b2f-267">Kompilator generuje `Task<T>` obiektu dla zwracany, ponieważ został oznaczony tej metody jako `async`.</span><span class="sxs-lookup"><span data-stu-id="21b2f-267">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="21b2f-268">Następnie zmodyfikujmy `Main` metodę, tak aby przechwytywać tych wyników i zapisuje nazwy repozytorium do konsoli.</span><span class="sxs-lookup"><span data-stu-id="21b2f-268">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="21b2f-269">Twoje `Main` metody teraz wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="21b2f-269">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="21b2f-270">Uzyskiwanie dostępu do `Result` właściwości zadania blokuje dopiero po ukończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="21b2f-270">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="21b2f-271">Zwykle wolisz `await` ukończenia zadania, jak w `ProcessRepositories` metody, ale nie jest dozwolona w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="21b2f-271">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="21b2f-272">Odczytywanie więcej informacji</span><span class="sxs-lookup"><span data-stu-id="21b2f-272">Reading More Information</span></span>

<span data-ttu-id="21b2f-273">Teraz zakończyć to przez przetwarzanie kilka kolejnych właściwości w pakiecie JSON, które są wysyłane z interfejsu API usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="21b2f-273">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="21b2f-274">Nie ma do pobrania wszystko, ale Dodawanie kilka właściwości przedstawiono kilka więcej funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="21b2f-274">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="21b2f-275">Zacznijmy od dodania więcej kilka typów prostych do `Repository` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="21b2f-275">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="21b2f-276">Te właściwości są dodawane do tej klasy:</span><span class="sxs-lookup"><span data-stu-id="21b2f-276">Add these properties to that class:</span></span>

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

<span data-ttu-id="21b2f-277">Te właściwości mają wbudowane konwersji z typu ciąg (czyli zawierać pakiety JSON) na typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="21b2f-277">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="21b2f-278"><xref:System.Uri> Typu może być nowe dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="21b2f-278">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="21b2f-279">Reprezentuje identyfikator URI, lub w tym przypadku adresu URL.</span><span class="sxs-lookup"><span data-stu-id="21b2f-279">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="21b2f-280">W przypadku liczby `Uri` i `int` typy pakietów JSON zawiera dane, które nie konwertować na typ docelowy, akcja serializacji spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="21b2f-280">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="21b2f-281">Po dodaniu tych aktualizacji `Main` metodę w celu wyświetlenia tych elementów:</span><span class="sxs-lookup"><span data-stu-id="21b2f-281">Once you've added these, update the `Main` method to display those elements:</span></span>

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
<span data-ttu-id="21b2f-282">Jako ostatni krok możemy dodać informacje z ostatniej operacji wypychania.</span><span class="sxs-lookup"><span data-stu-id="21b2f-282">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="21b2f-283">Te informacje jest sformatowany w ten sposób w formacie JSON odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="21b2f-283">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="21b2f-284">Ten format nie wykonuj żadnych standard .NET <xref:System.DateTime> formatów.</span><span class="sxs-lookup"><span data-stu-id="21b2f-284">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="21b2f-285">Z tego powodu konieczne jest napisanie metody konwersji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="21b2f-285">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="21b2f-286">Ponadto nie pożądane nieprzetworzony ciąg uwidoczniona dla użytkowników z `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="21b2f-286">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="21b2f-287">Atrybuty można kontrolować to również.</span><span class="sxs-lookup"><span data-stu-id="21b2f-287">Attributes can help control that as well.</span></span> <span data-ttu-id="21b2f-288">Najpierw należy zdefiniować `private` właściwości, w którym będą przechowywane reprezentację ciągu daty godziny w Twojej `Repository` klasy:</span><span class="sxs-lookup"><span data-stu-id="21b2f-288">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="21b2f-289">`DataMember` Atrybut informuje serializator czy to powinna zostać przetworzona, mimo że nie jest publicznym elementem członkowskim.</span><span class="sxs-lookup"><span data-stu-id="21b2f-289">The `DataMember` attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="21b2f-290">Następnie należy napisać publicznej właściwości tylko do odczytu, który konwertuje ciąg na prawidłową <xref:System.DateTime> obiektu i zwraca go <xref:System.DateTime>:</span><span class="sxs-lookup"><span data-stu-id="21b2f-290">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

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

<span data-ttu-id="21b2f-291">Przejdź przez nowe konstrukcje powyżej.</span><span class="sxs-lookup"><span data-stu-id="21b2f-291">Let's go over the new constructs above.</span></span> <span data-ttu-id="21b2f-292">`IgnoreDataMember` Atrybut serializator informuje, że ten typ nie należy do odczytu ani zapisywane z dowolnych obiektów JSON.</span><span class="sxs-lookup"><span data-stu-id="21b2f-292">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="21b2f-293">Ta właściwość zawiera tylko `get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="21b2f-293">This property contains only a `get` accessor.</span></span> <span data-ttu-id="21b2f-294">Brak nie `set` dostępu.</span><span class="sxs-lookup"><span data-stu-id="21b2f-294">There is no `set` accessor.</span></span> <span data-ttu-id="21b2f-295">To, jak zdefiniować *tylko do odczytu* właściwości w języku C#.</span><span class="sxs-lookup"><span data-stu-id="21b2f-295">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="21b2f-296">(Tak, możesz utworzyć *tylko do zapisu* wynosi właściwości w języku C#, ale ich wartości.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Metody analizowania ciągu i tworzy <xref:System.DateTime> przy użyciu formatu podana wartość daty i dodaje dodatkowe metadane na `DateTime` przy użyciu `CultureInfo` obiektu.</span><span class="sxs-lookup"><span data-stu-id="21b2f-296">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="21b2f-297">W przypadku niepowodzenia operacji analizowania metody dostępu właściwości zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="21b2f-297">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="21b2f-298">Aby użyć <xref:System.Globalization.CultureInfo.InvariantCulture>, należy dodać <xref:System.Globalization> przestrzeni nazw do `using` instrukcje w `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="21b2f-298">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="21b2f-299">Na koniec należy dodać więcej jeden wyjściowy instrukcji w konsoli i wszystko jest gotowe do tworzenia i ponownie uruchom tę aplikację:</span><span class="sxs-lookup"><span data-stu-id="21b2f-299">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="21b2f-300">Używana wersja teraz powinna być zgodna. [gotowej próbki](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="21b2f-300">Your version should now match the [finished sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient).</span></span>
 
## <a name="conclusion"></a><span data-ttu-id="21b2f-301">Wniosek</span><span class="sxs-lookup"><span data-stu-id="21b2f-301">Conclusion</span></span>

<span data-ttu-id="21b2f-302">W tym samouczku pokazano, jak żądania sieci web, wynik analizy i Wyświetl właściwości tych wyników.</span><span class="sxs-lookup"><span data-stu-id="21b2f-302">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="21b2f-303">Możesz także dodano nowe pakiety jako zależności w projekcie.</span><span class="sxs-lookup"><span data-stu-id="21b2f-303">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="21b2f-304">Przedstawiono niektóre funkcje języka C# obsługujące zorientowane obiektowo technik.</span><span class="sxs-lookup"><span data-stu-id="21b2f-304">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
