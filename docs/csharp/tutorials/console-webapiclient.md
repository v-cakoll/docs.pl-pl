---
title: Tworzenie klienta REST przy użyciu platformy .NET Core
description: W tym samouczku pokazano pewną liczbę funkcji platformy .NET Core i języka C#.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: bc3c23b277b233efba9f32cc49b29ac905f3abc8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480159"
---
# <a name="rest-client"></a><span data-ttu-id="2cfcd-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="2cfcd-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="2cfcd-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="2cfcd-104">Introduction</span></span>
<span data-ttu-id="2cfcd-105">W tym samouczku pokazano pewną liczbę funkcji platformy .NET Core i języka C#.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="2cfcd-106">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-106">You’ll learn:</span></span>
*   <span data-ttu-id="2cfcd-107">Podstawowe narzędzia .NET Core interfejsu wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="2cfcd-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
*   <span data-ttu-id="2cfcd-108">Omówienie funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-108">An overview of C# Language features.</span></span>
*   <span data-ttu-id="2cfcd-109">Zarządzanie zależnościami z NuGet</span><span class="sxs-lookup"><span data-stu-id="2cfcd-109">Managing dependencies with NuGet</span></span>
*   <span data-ttu-id="2cfcd-110">Połączenia HTTP</span><span class="sxs-lookup"><span data-stu-id="2cfcd-110">HTTP Communications</span></span>
*   <span data-ttu-id="2cfcd-111">Przetwarzanie informacji w formacie JSON</span><span class="sxs-lookup"><span data-stu-id="2cfcd-111">Processing JSON information</span></span>
*   <span data-ttu-id="2cfcd-112">Zarządzanie konfiguracją za pomocą atrybutów.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-112">Managing configuration with Attributes.</span></span> 

<span data-ttu-id="2cfcd-113">Skompiluj aplikację, która wysyła żądania HTTP do usługi REST w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="2cfcd-114">Będziesz odczytu informacji w formacie JSON, a następnie przekonwertować pakietu JSON na obiekty języka C#.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="2cfcd-115">Na koniec zobaczysz sposób pracy z obiektami w języku C#.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="2cfcd-116">Istnieje wiele funkcji, w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="2cfcd-117">Utworzymy je jedno po drugim.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-117">Let’s build them one by one.</span></span>

<span data-ttu-id="2cfcd-118">Jeśli wolisz postępuj zgodnie ze szczegółowymi [próbki końcowej](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) w tym temacie, możesz ją pobrać.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="2cfcd-119">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="2cfcd-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2cfcd-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="2cfcd-120">Prerequisites</span></span>
<span data-ttu-id="2cfcd-121">Należy skonfigurować maszynę, aby uruchomić platformy .NET core.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="2cfcd-122">Instrukcje dotyczące instalacji można znaleźć na [platformy .NET Core](https://www.microsoft.com/net/core) strony.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="2cfcd-123">Windows, Linux, macOS lub w kontenerze platformy Docker, mogą uruchamiać tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="2cfcd-124">Musisz zainstalować wybrany edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="2cfcd-125">Opisy poniżej użycia [programu Visual Studio Code](https://code.visualstudio.com/), która jest typu open source cross platform edytora.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="2cfcd-126">Można jednak użyć dowolnego narzędzia potrafisz.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-126">However, you can use whatever tools you are comfortable with.</span></span>
## <a name="create-the-application"></a><span data-ttu-id="2cfcd-127">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="2cfcd-127">Create the Application</span></span>
<span data-ttu-id="2cfcd-128">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-128">The first step is to create a new application.</span></span> <span data-ttu-id="2cfcd-129">Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="2cfcd-130">Upewnij się, że sposób bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-130">Make that the current directory.</span></span> <span data-ttu-id="2cfcd-131">Wpisz polecenie `dotnet new console` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="2cfcd-132">Spowoduje to utworzenie plikach startowych dla podstawowych aplikacji "Hello World".</span><span class="sxs-lookup"><span data-stu-id="2cfcd-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="2cfcd-133">Przed rozpoczęciem wprowadzania modyfikacji, Przejdźmy przez czynności, aby uruchomić prostej aplikacji Hello World.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-133">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="2cfcd-134">Po utworzeniu aplikacji wpisz `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-134">After creating the application, type `dotnet restore` ([see note](#dotnet-restore-note)) at the command prompt.</span></span> <span data-ttu-id="2cfcd-135">To polecenie uruchamia proces przywracania pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-135">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="2cfcd-136">NuGet to Menedżer pakietów .NET.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-136">NuGet is a .NET package manager.</span></span> <span data-ttu-id="2cfcd-137">To polecenie pobiera wszystkich brakujących zależności dla Twojego projektu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-137">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="2cfcd-138">Jak jest to nowy projekt, żaden z zależności jest w miejscu, dzięki czemu przy pierwszym uruchomieniu pobierze platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-138">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="2cfcd-139">Po wykonaniu tego kroku początkowego, wystarczy uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) podczas dodawania nowych pakietów zależnych lub zaktualizować wersje tych zależności.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-139">After this initial step, you will only need to run `dotnet restore` ([see note](#dotnet-restore-note)) when you add new dependent packages, or update the versions of any of your dependencies.</span></span>  

<span data-ttu-id="2cfcd-140">Po przywróceniu pakietów, możesz uruchomić `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-140">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="2cfcd-141">Wykonuje aparat kompilacji i tworzy aplikację.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-141">This executes the build engine and creates your application.</span></span> <span data-ttu-id="2cfcd-142">Na koniec wykonaj `dotnet run` do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-142">Finally, you execute `dotnet run` to run your application.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="2cfcd-143">Dodawanie nowych zależności</span><span class="sxs-lookup"><span data-stu-id="2cfcd-143">Adding New Dependencies</span></span>
<span data-ttu-id="2cfcd-144">Jednym z celów projektowania klucza dla platformy .NET Core jest minimalizacja rozmiaru instalacji programu .NET framework.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-144">One of the key design goals for .NET Core is to minimize the size of the .NET framework installation.</span></span> <span data-ttu-id="2cfcd-145">W ramach aplikacji .NET Core zawiera tylko najbardziej typowe elementy pełny .NET framework.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-145">The .NET Core Application framework contains only the most common elements of the .NET full framework.</span></span> <span data-ttu-id="2cfcd-146">Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych funkcji, możesz dodać te zależności w projekcie języka C# (\*.csproj) pliku.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-146">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="2cfcd-147">W tym przykładzie należy dodać `System.Runtime.Serialization.Json` pakietu, dzięki czemu aplikacja może przetworzyć odpowiedzi JSON.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-147">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="2cfcd-148">Otwórz swoje `csproj` pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-148">Open your `csproj` project file.</span></span> <span data-ttu-id="2cfcd-149">Pierwszy wiersz w pliku powinny się wyświetlać jako:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-149">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="2cfcd-150">Dodaj następujący kod bezpośrednio po tym wierszu:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-150">Add the following immediately after this line:</span></span> 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
<span data-ttu-id="2cfcd-151">Większość edytory kodu zapewni uzupełnianie przez różne wersje tych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-151">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="2cfcd-152">Zazwyczaj będziesz chciał użyć najnowszej wersji dowolnego pakietu, który dodajesz.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-152">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="2cfcd-153">Jednak należy się upewnić, że są zgodne wersje wszystkich pakietów i są również zgodne wersję platformy aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-153">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="2cfcd-154">Po wprowadzeniu tych zmian, należy uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) ponownie, aby pakiet jest zainstalowany w systemie.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-154">After you've made these changes, you should run `dotnet restore` ([see note](#dotnet-restore-note)) again so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="2cfcd-155">Tworzenie żądania sieci Web</span><span class="sxs-lookup"><span data-stu-id="2cfcd-155">Making Web Requests</span></span>
<span data-ttu-id="2cfcd-156">Teraz możesz rozpocząć pobieranie danych z sieci web.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-156">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="2cfcd-157">W tej aplikacji będzie odczytu informacji z [interfejsu API usługi GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="2cfcd-157">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="2cfcd-158">Spróbujmy odczytać informacji na temat projektów w ramach [.NET Foundation](http://www.dotnetfoundation.org/) ogólny.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-158">Let's read information about the projects under the [.NET Foundation](http://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="2cfcd-159">Można będzie uruchomić w żądaniu skierowanym do interfejsu API usługi GitHub, aby pobrać informacje na temat projektów.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-159">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="2cfcd-160">Punkt końcowy będziesz używał jest: [ https://api.github.com/orgs/dotnet/repos ](https://api.github.com/orgs/dotnet/repos).</span><span class="sxs-lookup"><span data-stu-id="2cfcd-160">The endpoint you'll use is: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span></span> <span data-ttu-id="2cfcd-161">Chcesz pobrać wszystkie informacje dotyczące tych projektów, dzięki czemu będziesz używać żądanie HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-161">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="2cfcd-162">Przeglądarka używa także żądania HTTP GET, dzięki czemu można wkleić, że adres URL w przeglądarce, aby zobaczyć, jakie informacje należy będziesz otrzymywać i przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-162">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="2cfcd-163">Możesz użyć <xref:System.Net.Http.HttpClient> klasy żądań sieci web.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-163">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="2cfcd-164">Wszystkie nowoczesnych interfejsów API programu .NET, takich jak <xref:System.Net.Http.HttpClient> obsługuje tylko metody asynchroniczne dla długotrwałych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-164">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="2cfcd-165">Rozpocznij metodą asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-165">Start by making an async method.</span></span> <span data-ttu-id="2cfcd-166">Podczas tworzenia funkcjonalność aplikacji będzie wypełniana w implementacji.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-166">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="2cfcd-167">Zacznij od otwarcia `program.cs` plik w katalogu projektu i dodawanie następującą metodę do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-167">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    
}
```

<span data-ttu-id="2cfcd-168">Musisz dodać `using` instrukcji w górnej części Twojej `Main` metoda tak, aby kompilator języka C# rozpoznaje <xref:System.Threading.Tasks.Task> typu:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-168">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="2cfcd-169">Jeśli na tym etapie tworzenia projektu uzyskasz ostrzeżenia generowane dla tej metody, ponieważ nie zawiera żadnego `await` operatorów i zostanie ona uruchomiona synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-169">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="2cfcd-170">Zignoruje teraz; następnie dodasz `await` operatorów jako możesz wypełnić w metodzie.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-170">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="2cfcd-171">Następnie zmień nazwę przestrzeni nazw, zdefiniowane w `namespace` instrukcji domyślne `ConsoleApp` do `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-171">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="2cfcd-172">Później zdefiniujemy `repo` klasy w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-172">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="2cfcd-173">Następnie zaktualizuj `Main` metodę do wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-173">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="2cfcd-174">`ProcessRepositories` Metoda zwraca klasę Task, i nie należy zakończyć program, przed zakończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-174">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="2cfcd-175">W związku z tym, należy użyć `Wait` metodę, aby zablokować i poczekaj na zakończenie zadania:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-175">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="2cfcd-176">Teraz masz program, nic nie robi, ale zajmuje asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-176">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="2cfcd-177">Możemy ją ulepszyć.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-177">Let's improve it.</span></span>

<span data-ttu-id="2cfcd-178">Najpierw należy obiekt, który jest w stanie pobrać danych z sieci web; Możesz użyć <xref:System.Net.Http.HttpClient> Aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-178">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="2cfcd-179">Ten obiekt obsługuje żądania i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-179">This object handles the request and the responses.</span></span> <span data-ttu-id="2cfcd-180">Utwórz wystąpienie jedno wystąpienie tego typu w `Program` klasy w pliku Program.cs.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-180">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

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

 <span data-ttu-id="2cfcd-181">Wróć do `ProcessRepositories` metody i wypełnij pierwszą wersję:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-181">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="2cfcd-182">Musisz również dodać dwie nowe przy użyciu instrukcji w górnej części pliku, w tym do skompilowania:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-182">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="2cfcd-183">Ta pierwsza wersja sprawia, że żądanie sieci web, aby zapoznać się z listą wszystkich repozytoriów w ramach organizacji foundation dotnet.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-183">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="2cfcd-184">(Identyfikator gitHub .NET Foundation jest "dotnet").</span><span class="sxs-lookup"><span data-stu-id="2cfcd-184">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="2cfcd-185">Pierwszych kilka wierszy, ustawianie <xref:System.Net.Http.HttpClient> dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-185">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="2cfcd-186">Najpierw jest skonfigurowany do akceptowania odpowiedziami JSON usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-186">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="2cfcd-187">Ten format jest po prostu JSON.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-187">This format is simply JSON.</span></span> <span data-ttu-id="2cfcd-188">Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-188">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="2cfcd-189">Te dwa nagłówki są sprawdzane przez kod serwera GitHub i są niezbędne w celu pobrania informacji z usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-189">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="2cfcd-190">Po skonfigurowaniu <xref:System.Net.Http.HttpClient>, upewnij sieci web, żądania i pobierania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-190">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="2cfcd-191">W pierwszej wersji, możesz użyć <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> wygodna metoda.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-191">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="2cfcd-192">Ta wygodna metoda uruchamia zadanie, które wysyła żądanie sieci web, a następnie po powrocie z żądania go odczytuje w strumieniu odpowiedzi i wyodrębnia zawartość ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-192">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="2cfcd-193">Treść odpowiedzi jest zwracana jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-193">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="2cfcd-194">Ten ciąg jest dostępna po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-194">The string is available when the task completes.</span></span> 

<span data-ttu-id="2cfcd-195">Ostatnie dwie linie ta metoda poczekać na zadanie, a następnie wydrukuj odpowiedzi do konsoli.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-195">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="2cfcd-196">Tworzenie aplikacji i uruchom go.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-196">Build the app, and run it.</span></span> <span data-ttu-id="2cfcd-197">Ostrzeżenie kompilacji ma teraz, ponieważ `ProcessRepositories` teraz zawierać `await` operatora.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-197">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="2cfcd-198">Zobaczysz, że długie wyświetlanie JSON sformatowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-198">You'll see a long display of JSON formatted text.</span></span>   

## <a name="processing-the-json-result"></a><span data-ttu-id="2cfcd-199">Przetwarzanie wyników JSON</span><span class="sxs-lookup"><span data-stu-id="2cfcd-199">Processing the JSON Result</span></span>

<span data-ttu-id="2cfcd-200">W tym momencie został napisany kod, aby pobrać odpowiedzi z serwera sieci web oraz wyświetlać tekst, który znajduje się w tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-200">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="2cfcd-201">Następnie możemy przekonwertować odpowiedź JSON na obiekty języka C#.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-201">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="2cfcd-202">Serializator JSON konwertuje dane JSON na obiekty języka C#.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-202">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="2cfcd-203">Pierwsze zadanie jest zdefiniowanie typu klasy C# zawiera informacje, które od tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-203">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="2cfcd-204">Utwórzmy tym powoli, więc rozpoczyna się od prostego języka C# typ, który zawiera nazwę repozytorium:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-204">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

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

<span data-ttu-id="2cfcd-205">Powyższy kod należy umieścić w nowym pliku o nazwie "repo.cs".</span><span class="sxs-lookup"><span data-stu-id="2cfcd-205">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="2cfcd-206">Ta wersja klasy reprezentuje to najprostsza ścieżka do przetwarzania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-206">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="2cfcd-207">Nazwa klasy i nazwę elementu członkowskiego zgodne nazwy używane w pakiecie JSON zamiast następujących konwencji języka C#.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-207">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="2cfcd-208">Można to naprawić, zapewniając niektóre atrybuty konfiguracji później.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-208">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="2cfcd-209">Ta klasa przedstawia inną ważną cechą JSON serializacji i deserializacji: nie wszystkie pola w pakiecie JSON należą do tej klasy.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-209">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="2cfcd-210">Serializator JSON będzie ignorować informacje, które nie są objęte na typ klasy, które są używane.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-210">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="2cfcd-211">Ta funkcja sprawia, że łatwiej tworzyć typy, które działają z tylko podzestaw pól w pakiecie JSON.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-211">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="2cfcd-212">Teraz, po utworzeniu typu, możemy zdeserializuj ją.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-212">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="2cfcd-213">Musisz utworzyć <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-213">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="2cfcd-214">Ten obiekt musi znać typ CLR Oczekiwano pakietu JSON pobiera.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-214">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="2cfcd-215">Pakiet z repozytorium GitHub zawiera sekwencję repozytoriów, więc `List<repo>` jest poprawnego typu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-215">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="2cfcd-216">Dodaj następujący wiersz do Twojej `ProcessRepositories` metody:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-216">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="2cfcd-217">Używasz dwie nowe przestrzenie nazw, więc należy dodać te także:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-217">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="2cfcd-218">Następnie użyjemy serializatora do przekonwertowania formatu JSON na obiekty języka C#.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-218">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="2cfcd-219">Zastąp wywołanie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> w swojej `ProcessRepositories` metody za pomocą następujących dwóch wierszy:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-219">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="2cfcd-220">Należy zauważyć, że używasz teraz <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> zamiast <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-220">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="2cfcd-221">Serializator używa strumienia zamiast ciągu jako źródło.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-221">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="2cfcd-222">Możemy wyjaśnić kilka funkcji języka C#, które są używane w drugim wierszu powyżej.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-222">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="2cfcd-223">Argument <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> jest `await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-223">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="2cfcd-224">Await wyrażeń może znajdować się praktycznie dowolnym miejscu w kodzie, mimo że do chwili obecnej, tylko przedstawiono je w ramach instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-224">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="2cfcd-225">Po drugie `as` operator konwertuje typ czasu kompilacji `object` do `List<repo>`.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-225">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span> <span data-ttu-id="2cfcd-226">Deklaracja <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, że funkcja zwraca obiekt typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-226">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2cfcd-227"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> Zwraca typ określony podczas jego skonstruowano (`List<repo>` w ramach tego samouczka).</span><span class="sxs-lookup"><span data-stu-id="2cfcd-227"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="2cfcd-228">Jeśli konwersja nie powiedzie, `as` operatora daje w wyniku `null`, zamiast zgłaszać wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-228">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="2cfcd-229">Prawie gotowe z tą sekcją.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-229">You're almost done with this section.</span></span> <span data-ttu-id="2cfcd-230">Teraz, za pomocą pliku JSON zostały konwertowane na obiekty języka C#, możemy wyświetlić nazwę każdego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-230">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="2cfcd-231">Zamień wiersze, które odczytują:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-231">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="2cfcd-232">z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-232">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="2cfcd-233">Skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-233">Compile and run the application.</span></span> <span data-ttu-id="2cfcd-234">Zostanie ona wydrukowana nazwy repozytoria, które są częścią .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-234">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="2cfcd-235">Kontrolowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="2cfcd-235">Controlling Serialization</span></span>

<span data-ttu-id="2cfcd-236">Zanim dodasz więcej funkcji, możemy adresów `repo` wpisz i przypisz ją konwencjami bardziej standard języka C#.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-236">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="2cfcd-237">Możesz to zrobić poprzez dodawanie adnotacji do `repo` to typ *atrybuty* które kontrolują, jak działa serializator JSON.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-237">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="2cfcd-238">W Twoim przypadku użyjesz tych atrybutów do definiowania mapowania między nazwami kluczy JSON i języka C# nazwy klas i składowych.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-238">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="2cfcd-239">Są dwa atrybuty używane `DataContract` atrybutu i `DataMember` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-239">The two attributes used are the `DataContract` attribute and the `DataMember` attribute.</span></span> <span data-ttu-id="2cfcd-240">Zgodnie z Konwencją wszystkie klasy atrybutu kończyć się sufiksem `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-240">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="2cfcd-241">Jednak nie należy używać tego sufiksu, po zastosowaniu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-241">However, you do not need to use that suffix when you apply an attribute.</span></span> 

<span data-ttu-id="2cfcd-242">`DataContract` i `DataMember` atrybuty są w innej biblioteki, więc musisz dodać tej biblioteki do pliku projektu C# jako zależność.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-242">The `DataContract` and `DataMember` attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="2cfcd-243">Dodaj następujący wiersz do `<ItemGroup>` sekcji w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-243">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="2cfcd-244">Po zapisaniu pliku Uruchom `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) do pobrania tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-244">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="2cfcd-245">Następnie otwórz `repo.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-245">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="2cfcd-246">Zmienimy nazwę pisanymi wielkimi literami, a w pełni pisowni nazwiska `Repository`.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-246">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="2cfcd-247">Firma Microsoft nadal chcesz mapy JSON "repo" węzłów do tego typu, więc musisz dodać `DataContract` atrybutu deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-247">We still want to map JSON 'repo' nodes to this type, so you'll need to add the `DataContract` attribute to the class declaration.</span></span> <span data-ttu-id="2cfcd-248">Użytkownik ustawia `Name` właściwość atrybutu nazwy węzłów JSON, które mapują do tego typu:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-248">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="2cfcd-249"><xref:System.Runtime.Serialization.DataContractAttribute> Jest elementem członkowskim <xref:System.Runtime.Serialization> przestrzeni nazw, więc należy dodać odpowiedni `using` instrukcji w górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-249">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="2cfcd-250">Zmieniono nazwę elementu `repo` klasy `Repository`, więc musisz wprowadzić taką samą nazwę, zmiany w pliku Program.cs (niektóre edytory mogą obsługiwać Refaktoryzacja zmiany nazwy, automatycznie wprowadzić tę zmianę:)</span><span class="sxs-lookup"><span data-stu-id="2cfcd-250">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="2cfcd-251">Następnie można wprowadzić tę samą zmianę z `name` pola przy użyciu <xref:System.Runtime.Serialization.DataMemberAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-251">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="2cfcd-252">Wprowadź następujące zmiany do deklaracji `name` pole repo.cs:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-252">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="2cfcd-253">Ta zmiana oznacza, że zajdzie potrzeba zmiany kodu, który zapisuje nazwy każdego repozytorium w pliku program.cs:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-253">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="2cfcd-254">Czy `dotnet build` następuje `dotnet run` się upewnić, że masz mapowania poprawne.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-254">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="2cfcd-255">Ten sam wynik jako przed powinny być widoczne.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-255">You should see the same output as before.</span></span> <span data-ttu-id="2cfcd-256">Zanim będziemy przetwarzać więcej właściwości z serwera sieci web, upewnijmy się, co więcej zmian `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-256">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="2cfcd-257">`Name` Składowa jest polem dostępny publicznie.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-257">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="2cfcd-258">Nie jest dobrą praktyką zorientowane obiektowo, więc Zmieńmy go do właściwości.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-258">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="2cfcd-259">Dla naszych potrzeb, potrzebujemy dowolnego konkretnego kodu, który uruchamiany, gdy pobieranie lub ustawianie właściwości, ale zmiana właściwości ułatwia dodawanie tych zmian w przyszłości, bez przerywania wszelki kod, który używa `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-259">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="2cfcd-260">Usuń definicję pola i zastąp go wartością [automatycznie implementowana właściwość](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span><span class="sxs-lookup"><span data-stu-id="2cfcd-260">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="2cfcd-261">Kompilator generuje treści `get` i `set` metod dostępu, a także prywatnego pola do przechowywania nazwy.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-261">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="2cfcd-262">Będzie podobny do poniższego kodu, który można ręcznie wpisać:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-262">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="2cfcd-263">Upewnijmy się, co więcej zmian przed dodaniem nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-263">Let's make one more change before adding new features.</span></span> <span data-ttu-id="2cfcd-264">`ProcessRepositories` Zwracają kolekcję repozytoriów i oferuje Praca asynchroniczna metoda.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-264">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="2cfcd-265">Powrócimy `List<Repository>` z tej metody, a następnie przenieść kod, który zapisuje informacje w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-265">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="2cfcd-266">Zmień podpis `ProcessRepositories` zwracany typ task, którego wynikiem jest lista z `Repository` obiektów:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-266">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="2cfcd-267">Następnie, po prostu zwraca repozytoriów po przetworzeniu odpowiedź w formacie JSON:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-267">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="2cfcd-268">Kompilator generuje `Task<T>` obiekt do zwrotu, ponieważ został oznaczony jako tej metody jako `async`.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-268">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="2cfcd-269">Następnie zmodyfikujmy `Main` metodę, tak że przechwytuje te wyniki i zapisuje każdej nazwy repozytorium do konsoli.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-269">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="2cfcd-270">Twoje `Main` metoda wygląda teraz następująco:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-270">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="2cfcd-271">Uzyskiwanie dostępu do `Result` właściwość zadania blokuje, dopóki zadanie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-271">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="2cfcd-272">Zazwyczaj chcesz `await` ukończenia zadania, jak `ProcessRepositories` metody, ale nie jest dozwolona w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-272">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="2cfcd-273">Odczytywanie informacji</span><span class="sxs-lookup"><span data-stu-id="2cfcd-273">Reading More Information</span></span>

<span data-ttu-id="2cfcd-274">Teraz zakończyć to przez przetwarzanie kilka innych właściwości w pakiecie JSON wysyłana z interfejsu API usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-274">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="2cfcd-275">Nie będzie konieczności Pobierz wszystko, ale dodanie kilka właściwości zademonstruje kilka więcej funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-275">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="2cfcd-276">Zacznijmy od dodania kilka więcej typów prostych do `Repository` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-276">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="2cfcd-277">Dodaj następujące właściwości dla tej klasy:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-277">Add these properties to that class:</span></span>

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

<span data-ttu-id="2cfcd-278">Te właściwości mają wbudowane definicje konwersji z typu string (czyli zawierać pakiety JSON) na typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-278">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="2cfcd-279"><xref:System.Uri> Typ może być dla Ciebie nowe.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-279">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="2cfcd-280">Reprezentuje identyfikator URI, lub w tym przypadku adresu URL.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-280">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="2cfcd-281">W przypadku właściwości `Uri` i `int` typy pakietów JSON zawiera dane, które nie konwersji na typ docelowy, akcja serializacji spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-281">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="2cfcd-282">Po dodaniu tych aktualizacji `Main` metodę w celu wyświetlenia tych elementów:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-282">Once you've added these, update the `Main` method to display those elements:</span></span>

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
<span data-ttu-id="2cfcd-283">W ostatnim kroku Dodajmy informacji z ostatniej operacji wypychania.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-283">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="2cfcd-284">Te informacje są sformatowane w ten sposób, w odpowiedzi JSON:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-284">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="2cfcd-285">Ten format nie jest zgodna z dowolnego programu standard .NET <xref:System.DateTime> formatów.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-285">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="2cfcd-286">Z tego powodu musisz napisać metodę konwersji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-286">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="2cfcd-287">Ponadto najprawdopodobniej nie chcesz, nieprzetworzonego ciągu widoczna dla użytkowników z `Repository` klasy.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-287">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="2cfcd-288">Atrybuty można kontrolować oznacza również.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-288">Attributes can help control that as well.</span></span> <span data-ttu-id="2cfcd-289">Najpierw należy zdefiniować `private` właściwość, która będzie przechowywać reprezentację ciągu daty, godziny w swojej `Repository` klasy:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-289">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="2cfcd-290">`DataMember` Atrybut informuje serializator, powinna to być przetworzone, mimo że nie ma publicznej składowej.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-290">The `DataMember` attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="2cfcd-291">Następnie należy napisać właściwość publiczna tylko do odczytu, która konwertuje ciąg na prawidłowym <xref:System.DateTime> obiektu i zwraca ją <xref:System.DateTime>:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-291">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

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

<span data-ttu-id="2cfcd-292">Zajmijmy się nowe konstrukcje powyżej.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-292">Let's go over the new constructs above.</span></span> <span data-ttu-id="2cfcd-293">`IgnoreDataMember` Atrybutu powoduje, że tego typu nie należy do odczytu ani zapisane z dowolnych obiektów JSON i że, serializator.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-293">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="2cfcd-294">Ta właściwość zawiera tylko `get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-294">This property contains only a `get` accessor.</span></span> <span data-ttu-id="2cfcd-295">Istnieje nie `set` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-295">There is no `set` accessor.</span></span> <span data-ttu-id="2cfcd-296">To, jak zdefiniować *tylko do odczytu* właściwość w języku C#.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-296">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="2cfcd-297">(Tak, możesz utworzyć *tylko do zapisu* właściwości w języku C#, ale ich wartość jest ograniczona.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Metoda analizowania ciągu i tworzy <xref:System.DateTime> przy użyciu podanej daty w formacie, a następnie dodaje dodatkowe metadane `DateTime` przy użyciu `CultureInfo` obiektu.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-297">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="2cfcd-298">Metoda dostępu właściwości zgłasza wyjątek, w przypadku niepowodzenia operacji analizy.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-298">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="2cfcd-299">Aby użyć <xref:System.Globalization.CultureInfo.InvariantCulture>, należy dodać <xref:System.Globalization> przestrzeń nazw `using` instrukcji w `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-299">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="2cfcd-300">Na koniec należy dodać jeden wyjściowy więcej instrukcji, w konsoli i wszystko będzie gotowe skompilować i ponownie uruchomić tę aplikację:</span><span class="sxs-lookup"><span data-stu-id="2cfcd-300">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="2cfcd-301">Twoja wersja powinna być teraz zgodna [gotowych przykładowych](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="2cfcd-301">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>
 
## <a name="conclusion"></a><span data-ttu-id="2cfcd-302">Wniosek</span><span class="sxs-lookup"><span data-stu-id="2cfcd-302">Conclusion</span></span>

<span data-ttu-id="2cfcd-303">W tym samouczku pokazano, jak wysyłać żądania sieci web, przeanalizować wynik i wyświetlić właściwości tych wyników.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-303">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="2cfcd-304">Ponadto dodano nowe pakiety jako zależności w projekcie.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-304">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="2cfcd-305">Przedstawiono niektóre funkcje języka C#, które obsługują technik zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="2cfcd-305">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
