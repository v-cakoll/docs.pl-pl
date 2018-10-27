---
title: Mikrousługi hostowane na platformie Docker-C#
description: Dowiedz się, jak utworzyć asp.net podstawowych usług, które są uruchamiane w kontenerach platformy Docker
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: b1f7159a222ab4d68715844e9997ca922676bc80
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454489"
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="c32fc-103">Mikrousługi hostowane na platformie Docker</span><span class="sxs-lookup"><span data-stu-id="c32fc-103">Microservices hosted in Docker</span></span>

<span data-ttu-id="c32fc-104">Ten samouczek zawiera szczegółowe zadania, które są niezbędne do tworzenia i wdrażania mikrousług platformy ASP.NET Core w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="c32fc-104">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="c32fc-105">W trakcie tego samouczka dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="c32fc-105">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="c32fc-106">Jak wygenerować aplikację ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c32fc-106">How to generate an ASP.NET Core application.</span></span>
* <span data-ttu-id="c32fc-107">Jak utworzyć środowisko deweloperskie platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="c32fc-107">How to create a development Docker environment.</span></span>
* <span data-ttu-id="c32fc-108">Jak utworzyć obraz platformy Docker, na podstawie istniejącego obrazu.</span><span class="sxs-lookup"><span data-stu-id="c32fc-108">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="c32fc-109">Jak wdrożyć usługę w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="c32fc-109">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="c32fc-110">Po drodze widoczna jest także niektóre C# funkcji języka:</span><span class="sxs-lookup"><span data-stu-id="c32fc-110">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="c32fc-111">Jak konwertować C# obiektów do ładunków JSON.</span><span class="sxs-lookup"><span data-stu-id="c32fc-111">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="c32fc-112">Jak utworzyć niemodyfikowalny obiektów transferu danych.</span><span class="sxs-lookup"><span data-stu-id="c32fc-112">How to build immutable Data Transfer Objects.</span></span>
* <span data-ttu-id="c32fc-113">Instrukcje przetwarzania przychodzących żądań HTTP i generowanie odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="c32fc-113">How to process incoming HTTP Requests and generate the HTTP Response.</span></span>
* <span data-ttu-id="c32fc-114">Jak pracować z typami wartości null.</span><span class="sxs-lookup"><span data-stu-id="c32fc-114">How to work with nullable value types.</span></span>

<span data-ttu-id="c32fc-115">Możesz [wyświetlić lub pobrać przykładową aplikację](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="c32fc-115">You can [view or download the sample app](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="c32fc-116">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="c32fc-116">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="why-docker"></a><span data-ttu-id="c32fc-117">Dlaczego Docker?</span><span class="sxs-lookup"><span data-stu-id="c32fc-117">Why Docker?</span></span>

<span data-ttu-id="c32fc-118">Docker sprawia, że łatwo jest tworzyć obrazy standardowych maszyn do hostowania usługi w centrum danych lub w chmurze publicznej.</span><span class="sxs-lookup"><span data-stu-id="c32fc-118">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="c32fc-119">Docker umożliwia Skonfiguruj obraz i Replikuj ją w razie potrzeby skalowania w instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c32fc-119">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="c32fc-120">Cały kod w tym samouczku będą działać w dowolnym środowisku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c32fc-120">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="c32fc-121">Dodatkowe zadania instalacji platformy Docker będzie działać w przypadku aplikacji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c32fc-121">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="c32fc-122">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c32fc-122">Prerequisites</span></span>

<span data-ttu-id="c32fc-123">Należy skonfigurować maszynę w taki sposób, aby uruchomić platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c32fc-123">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="c32fc-124">Instrukcje dotyczące instalacji można znaleźć na [platformy .NET Core](https://www.microsoft.com/net/core) strony.</span><span class="sxs-lookup"><span data-stu-id="c32fc-124">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="c32fc-125">Windows, Linux, macOS lub w kontenerze platformy Docker, mogą uruchamiać tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="c32fc-125">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="c32fc-126">Musisz zainstalować wybrany edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="c32fc-126">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="c32fc-127">Opisy poniżej użycia [programu Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora.</span><span class="sxs-lookup"><span data-stu-id="c32fc-127">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="c32fc-128">Można jednak użyć dowolnego narzędzia potrafisz.</span><span class="sxs-lookup"><span data-stu-id="c32fc-128">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="c32fc-129">Należy również zainstalować aparat platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="c32fc-129">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="c32fc-130">Zobacz [strona instalacji platformy Docker](https://docs.docker.com/install/overview/) instrukcje dla danej platformy.</span><span class="sxs-lookup"><span data-stu-id="c32fc-130">See the [Docker Installation page](https://docs.docker.com/install/overview/) for instructions for your platform.</span></span>
<span data-ttu-id="c32fc-131">Platformy docker można zainstalować w wiele dystrybucji systemu Linux, macOS lub Windows.</span><span class="sxs-lookup"><span data-stu-id="c32fc-131">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="c32fc-132">Strona wyżej zawiera sekcje dla każdego z dostępnych instalacji.</span><span class="sxs-lookup"><span data-stu-id="c32fc-132">The page referenced above contains sections to each of the available installations.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="c32fc-133">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="c32fc-133">Create the Application</span></span>

<span data-ttu-id="c32fc-134">Teraz, po zainstalowaniu wszystkie narzędzia, należy utworzyć nową aplikację platformy ASP.NET Core w katalogu o nazwie "WeatherMicroservice", wykonując następujące polecenie w powłoce Ulubione:</span><span class="sxs-lookup"><span data-stu-id="c32fc-134">Now that you've installed all the tools, create a new ASP.NET Core application in a directory called "WeatherMicroservice" by executing the following command in your favorite shell:</span></span>

```console
dotnet new web -o WeatherMicroservice
```

<span data-ttu-id="c32fc-135">`dotnet` Polecenie zostanie uruchomione narzędzia niezbędne do tworzenia aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="c32fc-135">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="c32fc-136">Każdy zlecenie wykonuje inne polecenie.</span><span class="sxs-lookup"><span data-stu-id="c32fc-136">Each verb executes a different command.</span></span>

<span data-ttu-id="c32fc-137">`dotnet new` Polecenie służy do tworzenia.Net Core projektów.</span><span class="sxs-lookup"><span data-stu-id="c32fc-137">The `dotnet new` command is used to create .Net Core projects.</span></span>

<span data-ttu-id="c32fc-138">`-o WeatherMicroservice` Po opcji `dotnet new` polecenie służy do lokalizację, aby utworzyć aplikację platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c32fc-138">The `-o WeatherMicroservice` option after the `dotnet new` command is used to give the location to create the ASP.NET Core application.</span></span>

<span data-ttu-id="c32fc-139">Dla tego mikrousług chcemy, aby aplikacja sieci web najprostszy, najbardziej lekki jest to możliwe, więc użyliśmy "Platformy ASP.NET Core puste" szablonu, określając jego krótką nazwę `web`.</span><span class="sxs-lookup"><span data-stu-id="c32fc-139">For this microservice, we want the simplest, most lightweight web application possible, so we used the "ASP.NET Core Empty" template, by specifying its short name, `web`.</span></span>

<span data-ttu-id="c32fc-140">Szablon tworzy cztery pliki:</span><span class="sxs-lookup"><span data-stu-id="c32fc-140">The template creates four files for you:</span></span>

* <span data-ttu-id="c32fc-141">Plik Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="c32fc-141">A Startup.cs file.</span></span> <span data-ttu-id="c32fc-142">Zawiera podstawę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c32fc-142">This contains the basis of the application.</span></span>
* <span data-ttu-id="c32fc-143">Plik Program.cs.</span><span class="sxs-lookup"><span data-stu-id="c32fc-143">A Program.cs file.</span></span> <span data-ttu-id="c32fc-144">Zawiera punkt wejścia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c32fc-144">This contains the entry point of the application.</span></span>
* <span data-ttu-id="c32fc-145">Plik WeatherMicroservice.csproj.</span><span class="sxs-lookup"><span data-stu-id="c32fc-145">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="c32fc-146">Jest to plik kompilacji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c32fc-146">This is the build file for the application.</span></span>
* <span data-ttu-id="c32fc-147">Plik Properties/launchSettings.json.</span><span class="sxs-lookup"><span data-stu-id="c32fc-147">A Properties/launchSettings.json file.</span></span> <span data-ttu-id="c32fc-148">Zawiera ustawienia debugowania, używane przez środowiska IDE.</span><span class="sxs-lookup"><span data-stu-id="c32fc-148">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="c32fc-149">Teraz możesz uruchomić aplikację wygenerowanego szablonu:</span><span class="sxs-lookup"><span data-stu-id="c32fc-149">Now you can run the template generated application:</span></span>

```console
dotnet run
```

<span data-ttu-id="c32fc-150">To polecenie spowoduje najpierw przywrócenie zależności wymagane do kompilowania aplikacji i późniejszego kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c32fc-150">This command will first restore dependencies required to build the application and then it will build the application.</span></span>

<span data-ttu-id="c32fc-151">Domyślna konfiguracja nasłuchuje `http://localhost:5000`.</span><span class="sxs-lookup"><span data-stu-id="c32fc-151">The default configuration listens to `http://localhost:5000`.</span></span> <span data-ttu-id="c32fc-152">Możesz otworzyć przeglądarkę i przejdź do tej strony i wyświetlić "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c32fc-152">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="c32fc-153">Komunikat.</span><span class="sxs-lookup"><span data-stu-id="c32fc-153">message.</span></span>

<span data-ttu-id="c32fc-154">Po wykonaniu tych czynności można zamknąć aplikację, naciskając klawisz <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c32fc-154">When you're done, you can shut down the application by pressing <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="c32fc-155">Anatomia aplikacji ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c32fc-155">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="c32fc-156">Teraz, gdy masz utworzoną aplikację, Przyjrzyjmy się jak ta funkcja jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="c32fc-156">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="c32fc-157">Istnieją dwa wygenerowanych plików, które są szczególnie istotne w tym momencie: WeatherMicroservice.csproj i pliku Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="c32fc-157">There are two of the generated files that are particularly interesting at this point: WeatherMicroservice.csproj and Startup.cs.</span></span> 

<span data-ttu-id="c32fc-158">Plik .csproj zawiera informacje o projekcie.</span><span class="sxs-lookup"><span data-stu-id="c32fc-158">The .csproj file contains information about the project.</span></span>
<span data-ttu-id="c32fc-159">Są dwa węzły, które są najbardziej interesujących `<TargetFramework>` i `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="c32fc-159">The two nodes that are most interesting are `<TargetFramework>` and `<PackageReference>`.</span></span>

<span data-ttu-id="c32fc-160">`<TargetFramework>` Węzła Określa wersję platformy .NET, która może uruchomić tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="c32fc-160">The `<TargetFramework>` node specifies the version of .NET that will run this application.</span></span>

<span data-ttu-id="c32fc-161">Każdy `<PackageReference>` węzła jest używany do określenia pakietu, który jest wymagany dla tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c32fc-161">Each `<PackageReference>` node is used to specify a package that is needed for this application.</span></span>

<span data-ttu-id="c32fc-162">Aplikacja została zaimplementowana w pliku Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="c32fc-162">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="c32fc-163">Ten plik zawiera klasę uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="c32fc-163">This file contains the startup class.</span></span>

<span data-ttu-id="c32fc-164">Te dwie metody są wywoływane przez infrastrukturę platformy ASP.NET Core, aby skonfigurować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c32fc-164">The two methods are called by the ASP.NET Core infrastructure to configure and run the application.</span></span> <span data-ttu-id="c32fc-165">`ConfigureServices` Metoda opisano usługi, które są niezbędne dla tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c32fc-165">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="c32fc-166">W przypadku tworzenia zwarte mikrousług, dzięki czemu nie trzeba skonfigurować wszelkie zależności.</span><span class="sxs-lookup"><span data-stu-id="c32fc-166">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="c32fc-167">`Configure` Metoda konfiguruje programy obsługi dla przychodzących żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="c32fc-167">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="c32fc-168">Szablon generuje prosty program obsługi, który odpowiada na każde żądanie z tekstu "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="c32fc-168">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="c32fc-169">Tworzenie mikrousług</span><span class="sxs-lookup"><span data-stu-id="c32fc-169">Build a microservice</span></span>

<span data-ttu-id="c32fc-170">Usługi, możesz zacząć tworzyć będzie dostarczać raporty o pogodzie z dowolnego miejsca na świecie.</span><span class="sxs-lookup"><span data-stu-id="c32fc-170">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="c32fc-171">W przypadku aplikacji produkcyjnej wywoływałby niektóre usługi w celu pobrania danych o pogodzie.</span><span class="sxs-lookup"><span data-stu-id="c32fc-171">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="c32fc-172">W naszym przykładzie polega na wygenerowaniu prognozę pogody losowych.</span><span class="sxs-lookup"><span data-stu-id="c32fc-172">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="c32fc-173">Istnieje kilka zadań, które należy wykonać w celu zaimplementowania naszej usługi pogody losowe:</span><span class="sxs-lookup"><span data-stu-id="c32fc-173">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="c32fc-174">Analizowanie żądania przychodzącego, które można odczytać szerokości i długości geograficznej.</span><span class="sxs-lookup"><span data-stu-id="c32fc-174">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="c32fc-175">Generowanie losowe dane prognozy.</span><span class="sxs-lookup"><span data-stu-id="c32fc-175">Generate some random forecast data.</span></span>
* <span data-ttu-id="c32fc-176">Konwertuj losowych danych prognozowania z C# obiektów na pakiety JSON.</span><span class="sxs-lookup"><span data-stu-id="c32fc-176">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="c32fc-177">Ustaw nagłówek odpowiedzi, aby wskazać, że Twoja usługa wysyła kopię JSON.</span><span class="sxs-lookup"><span data-stu-id="c32fc-177">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="c32fc-178">Zapisu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="c32fc-178">Write the response.</span></span>

<span data-ttu-id="c32fc-179">W kolejnych sekcjach opisano każdy z tych kroków.</span><span class="sxs-lookup"><span data-stu-id="c32fc-179">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="c32fc-180">Podczas analizowania ciągu zapytania</span><span class="sxs-lookup"><span data-stu-id="c32fc-180">Parsing the Query String</span></span>

<span data-ttu-id="c32fc-181">Rozpocznie się analizując ciąg zapytania.</span><span class="sxs-lookup"><span data-stu-id="c32fc-181">You'll begin by parsing the query string.</span></span> <span data-ttu-id="c32fc-182">Usługa będzie akceptować "lat" i "long" argumentów dla ciągu zapytania w tym formularzu:</span><span class="sxs-lookup"><span data-stu-id="c32fc-182">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

<span data-ttu-id="c32fc-183">Wszystkie zmiany, należy wprowadzić są w wyrażeniu lambda zdefiniowany jako argument do `app.Run` w klasie uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="c32fc-183">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="c32fc-184">Argument wyrażenia lambda jest `HttpContext` dla żądania.</span><span class="sxs-lookup"><span data-stu-id="c32fc-184">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="c32fc-185">Jednym z jego właściwości jest `Request` obiektu.</span><span class="sxs-lookup"><span data-stu-id="c32fc-185">One of its properties is the `Request` object.</span></span> <span data-ttu-id="c32fc-186">`Request` Obiekt ma `Query` właściwość, która zawiera słownik wszystkich wartości na ciąg zapytania dla żądania.</span><span class="sxs-lookup"><span data-stu-id="c32fc-186">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="c32fc-187">Dodawanie pierwszego ma na celu znalezienie wartości szerokości i długości geograficznej:</span><span class="sxs-lookup"><span data-stu-id="c32fc-187">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="c32fc-188">`Query` Słownika wartości są `StringValue` typu.</span><span class="sxs-lookup"><span data-stu-id="c32fc-188">The `Query` dictionary values are `StringValue` type.</span></span> <span data-ttu-id="c32fc-189">Tego typu może zawierać kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="c32fc-189">That type can contain a collection of strings.</span></span> <span data-ttu-id="c32fc-190">Dla usługi pogody każda wartość jest pojedynczy ciąg.</span><span class="sxs-lookup"><span data-stu-id="c32fc-190">For your weather service, each value is a single string.</span></span> <span data-ttu-id="c32fc-191">Dlatego jest wywołanie `FirstOrDefault()` w powyższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c32fc-191">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="c32fc-192">Następnie należy Konwertowanie ciągów na wartości podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="c32fc-192">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="c32fc-193">Ta metoda służy do przekonwertowania ciągu na wartość o podwójnej precyzji jest `double.TryParse()`:</span><span class="sxs-lookup"><span data-stu-id="c32fc-193">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="c32fc-194">Ta metoda wykorzystuje C# się parametry, aby wskazać, jeśli ciąg wejściowy można przekonwertować na wartość typu double.</span><span class="sxs-lookup"><span data-stu-id="c32fc-194">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="c32fc-195">Jeśli ciąg reprezentuje prawidłowy reprezentację wartość o podwójnej precyzji, metoda zwraca wartość true, a `result` argument zawiera wartość.</span><span class="sxs-lookup"><span data-stu-id="c32fc-195">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="c32fc-196">Jeśli ciąg nie reprezentuje prawidłową wartość o podwójnej precyzji, metoda zwraca wartość false.</span><span class="sxs-lookup"><span data-stu-id="c32fc-196">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="c32fc-197">Możesz dostosować tego interfejsu API przy użyciu *— metoda rozszerzenia* zwracającego *nullable double*.</span><span class="sxs-lookup"><span data-stu-id="c32fc-197">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="c32fc-198">A *typem wartościowym* to typ, który reprezentuje określony typ wartości i można również przechowywać braku lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="c32fc-198">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="c32fc-199">Typ dopuszczający wartość null jest reprezentowany przez dołączenie `?` znak do deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="c32fc-199">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="c32fc-200">Metody rozszerzające są metody, które są zdefiniowane jako metody statyczne, ale przez dodanie `this` modyfikator w pierwszym parametrze może być wywoływany tak, jakby są członkami tej klasy.</span><span class="sxs-lookup"><span data-stu-id="c32fc-200">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="c32fc-201">Metody rozszerzające można zdefiniować tylko w klasach statycznych.</span><span class="sxs-lookup"><span data-stu-id="c32fc-201">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="c32fc-202">Poniżej przedstawiono definicję klasy zawierającej metodę rozszerzenia dla analizy:</span><span class="sxs-lookup"><span data-stu-id="c32fc-202">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="c32fc-203">Przed wywołaniem metody rozszerzenia, zmień bieżącą kulturę niezmienną:</span><span class="sxs-lookup"><span data-stu-id="c32fc-203">Before calling the extension method, change the current culture to invariant:</span></span>

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

<span data-ttu-id="c32fc-204">Daje to gwarancję, że analizuje Twojej aplikacji liczby takie same na dowolnym serwerze, niezależnie od jego kultury domyślnej.</span><span class="sxs-lookup"><span data-stu-id="c32fc-204">This ensures that your application parses numbers the same on any server, regardless of its default culture.</span></span>

<span data-ttu-id="c32fc-205">Teraz można metody rozszerzenia konwertować argumenty ciągu zapytania z typem double:</span><span class="sxs-lookup"><span data-stu-id="c32fc-205">Now you can use the extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="c32fc-206">Aby łatwo przetestować kod przetwarzania, zaktualizuj odpowiedzi, aby uwzględnić wartości argumentów:</span><span class="sxs-lookup"><span data-stu-id="c32fc-206">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="c32fc-207">W tym momencie można uruchomić aplikacji sieci web i czy działa analizy kodu.</span><span class="sxs-lookup"><span data-stu-id="c32fc-207">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="c32fc-208">Dodawanie wartości do żądania sieci web w przeglądarce i powinna wyświetlić zaktualizowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="c32fc-208">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="c32fc-209">Tworzenie losowego prognozę pogody</span><span class="sxs-lookup"><span data-stu-id="c32fc-209">Build a random weather forecast</span></span>

<span data-ttu-id="c32fc-210">Kolejnego zadania jest tworzenie losowego prognozę pogody.</span><span class="sxs-lookup"><span data-stu-id="c32fc-210">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="c32fc-211">Zacznijmy od kontener danych, który zawiera wartości, które chcesz uzyskać prognozę pogody:</span><span class="sxs-lookup"><span data-stu-id="c32fc-211">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions =
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HighTemperatureFahrenheit { get; }
    public int LowTemperatureFahrenheit { get; }
    public int AverageWindSpeedMph { get; }
    public string Condition { get; }
}
```

<span data-ttu-id="c32fc-212">Następnie można utworzyć konstruktora, który losowo ustawia te wartości.</span><span class="sxs-lookup"><span data-stu-id="c32fc-212">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="c32fc-213">Ten konstruktor korzysta z wartości dla szerokości i długości geograficznej, inicjator `Random` generator liczb.</span><span class="sxs-lookup"><span data-stu-id="c32fc-213">This constructor uses the values for the latitude and longitude to seed the `Random` number generator.</span></span> <span data-ttu-id="c32fc-214">Oznacza to, że prognozy dla tej samej lokalizacji jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="c32fc-214">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="c32fc-215">Jeśli zmienisz argumenty dla szerokości i długości geograficznej, uzyskasz różne prognozy (z powodu uruchamiania innego materiału siewnego).</span><span class="sxs-lookup"><span data-stu-id="c32fc-215">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed).</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="c32fc-216">Można teraz wygenerować prognozy 5-dniowy w metodzie odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="c32fc-216">You can now generate the 5-day forecast in your response method:</span></span>

```csharp
if (latitude.HasValue && longitude.HasValue)
{
    var forecast = new List<WeatherReport>();
    for (var days = 1; days <= 5; days++)
    {
        forecast.Add(new WeatherReport(latitude.Value, longitude.Value, days));
    }
}
```

### <a name="build-the-json-response"></a><span data-ttu-id="c32fc-217">Tworzenie odpowiedź w formacie JSON</span><span class="sxs-lookup"><span data-stu-id="c32fc-217">Build the JSON response</span></span>

<span data-ttu-id="c32fc-218">Zadanie kodu końcowego na serwerze polega na przekonwertowaniu `WeatherReport` listy w dokumencie JSON i Wyślij z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="c32fc-218">The final code task on the server is to convert the `WeatherReport` list into JSON document, and send that back to the client.</span></span> <span data-ttu-id="c32fc-219">Zacznijmy od utworzenia dokumentu JSON.</span><span class="sxs-lookup"><span data-stu-id="c32fc-219">Let's start by creating the JSON document.</span></span> <span data-ttu-id="c32fc-220">Serializator Newtonsoft JSON dodasz do listy zależności.</span><span class="sxs-lookup"><span data-stu-id="c32fc-220">You'll add the Newtonsoft JSON serializer to the list of dependencies.</span></span> <span data-ttu-id="c32fc-221">Możesz to zrobić za pomocą następujących `dotnet` polecenia:</span><span class="sxs-lookup"><span data-stu-id="c32fc-221">You can do that using the following `dotnet` command:</span></span>

```console
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="c32fc-222">Następnie należy użyć `JsonConvert` klasę umożliwiającą zapisanie obiektu na ciąg:</span><span class="sxs-lookup"><span data-stu-id="c32fc-222">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="c32fc-223">Powyższy kod konwertuje obiekt prognozy (lista `WeatherForecast` obiektów) do dokumentu JSON.</span><span class="sxs-lookup"><span data-stu-id="c32fc-223">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON document.</span></span> <span data-ttu-id="c32fc-224">Po skonstruowaniu dokumentu odpowiedzi, Ustaw typ zawartości `application/json`i zapisać ciąg.</span><span class="sxs-lookup"><span data-stu-id="c32fc-224">After you've constructed the response document, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="c32fc-225">Aplikacja zostanie teraz uruchomiona i zwraca losową prognozy.</span><span class="sxs-lookup"><span data-stu-id="c32fc-225">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="c32fc-226">Zbuduj obraz Docker</span><span class="sxs-lookup"><span data-stu-id="c32fc-226">Build a Docker image</span></span>

<span data-ttu-id="c32fc-227">Nasze ostatnim zadaniem jest do uruchamiania aplikacji na platformie Docker.</span><span class="sxs-lookup"><span data-stu-id="c32fc-227">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="c32fc-228">Utworzymy kontener platformy Docker działającą obrazu platformy Docker, który reprezentuje naszej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c32fc-228">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="c32fc-229">A ***obrazu platformy Docker*** jest plikiem, który definiuje środowisko do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c32fc-229">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="c32fc-230">A ***kontener platformy Docker*** reprezentuje uruchomionego wystąpienia obrazu platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="c32fc-230">A ***Docker Container*** represents a running instance of a Docker Image.</span></span>

<span data-ttu-id="c32fc-231">Analogicznie, można traktować *obrazu platformy Docker* jako *klasy*i *kontener platformy Docker* jako obiekt lub wystąpienie tej klasy.</span><span class="sxs-lookup"><span data-stu-id="c32fc-231">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="c32fc-232">Następujący plik Dockerfile będzie służyć do naszych potrzeb:</span><span class="sxs-lookup"><span data-stu-id="c32fc-232">The following Dockerfile will serve for our purposes:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="c32fc-233">Zajmijmy się jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="c32fc-233">Let's go over its contents.</span></span>

<span data-ttu-id="c32fc-234">Pierwszy wiersz określa obrazu źródłowego, używana do tworzenia aplikacji:</span><span class="sxs-lookup"><span data-stu-id="c32fc-234">The first line specifies the source image used for building the application:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
```

<span data-ttu-id="c32fc-235">Docker umożliwia skonfigurowanie obraz maszyny, na podstawie szablonu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="c32fc-235">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="c32fc-236">Oznacza, nie musisz podać wszystkie parametry maszyny, podczas uruchamiania, wystarczy podać wszelkie zmiany.</span><span class="sxs-lookup"><span data-stu-id="c32fc-236">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="c32fc-237">Zmiany w tym miejscu będzie zawierać naszej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c32fc-237">The changes here will be to include our application.</span></span>

<span data-ttu-id="c32fc-238">W tym przykładzie użyjemy `2.1-sdk` wersję `dotnet` obrazu.</span><span class="sxs-lookup"><span data-stu-id="c32fc-238">In this sample, we'll use the `2.1-sdk` version of the `dotnet` image.</span></span> <span data-ttu-id="c32fc-239">To jest najprostszym sposobem utworzenia działającego środowiska Docker.</span><span class="sxs-lookup"><span data-stu-id="c32fc-239">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="c32fc-240">Ten obraz zawiera środowisko uruchomieniowe platformy .NET Core i .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c32fc-240">This image includes the .NET Core runtime, and the .NET Core SDK.</span></span>
<span data-ttu-id="c32fc-241">Który sprawia, że łatwiej rozpocząć pracę i skompilować, ale utworzyć większy obraz, dlatego użyjemy tego obrazu do tworzenia aplikacji i inny obraz do jej uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="c32fc-241">That makes it easier to get started and build, but does create a larger image, so we'll use this image for building the application and a different image to run it.</span></span>

<span data-ttu-id="c32fc-242">Następne wiersze instalacji i skompilować aplikację:</span><span class="sxs-lookup"><span data-stu-id="c32fc-242">The next lines setup and build your application:</span></span>

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="c32fc-243">Spowoduje to kopiowanie pliku projektu z bieżącego katalogu, do maszyny Wirtualnej platformy Docker i Przywróć wszystkie pakiety.</span><span class="sxs-lookup"><span data-stu-id="c32fc-243">This will copy the project file from the  current directory to the Docker VM, and restore all the packages.</span></span> <span data-ttu-id="c32fc-244">Przy użyciu interfejsu wiersza polecenia platformy dotnet oznacza, że obraz platformy Docker musi zawierać zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c32fc-244">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="c32fc-245">Po tym kopiowane pozostałej części aplikacji, a `dotnet
publish` polecenie kompiluje i pakiety aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c32fc-245">After that, the rest of your application gets copied, and the `dotnet
publish` command builds and packages your application.</span></span>

<span data-ttu-id="c32fc-246">Na koniec Utwórz drugi obraz platformy Docker, który uruchamia aplikację:</span><span class="sxs-lookup"><span data-stu-id="c32fc-246">Finally, we create a second Docker image that runs the application:</span></span>

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="c32fc-247">Używa tego obrazu `2.1-aspnetcore-runtime` wersję `dotnet` obrazu, który zawiera wszystkie elementy niezbędne do uruchamiania aplikacji ASP.NET Core, ale nie zawiera zestawu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c32fc-247">This image uses the `2.1-aspnetcore-runtime` version of the `dotnet` image, which contains everything necessary to run ASP.NET Core applications, but does not include the .NET Core SDK.</span></span> <span data-ttu-id="c32fc-248">Oznacza to, ten obraz nie może służyć do tworzenia aplikacji .NET Core, ale zapewnia także finalnego obrazu mniejsze.</span><span class="sxs-lookup"><span data-stu-id="c32fc-248">This means this image can't be used to build .NET Core applications, but it also makes the final image smaller.</span></span>

<span data-ttu-id="c32fc-249">Aby działało, możemy skopiować zbudowanych aplikacji z pierwszy obraz do drugiej.</span><span class="sxs-lookup"><span data-stu-id="c32fc-249">To make this work, we copy the built application from the first image to the second one.</span></span>

<span data-ttu-id="c32fc-250">`ENTRYPOINT` Polecenia informowania platformy Docker, jakie polecenia uruchamia usługę.</span><span class="sxs-lookup"><span data-stu-id="c32fc-250">The `ENTRYPOINT` command informs Docker what command starts the service.</span></span>

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="c32fc-251">Tworzenie i uruchamianie obrazu w kontenerze</span><span class="sxs-lookup"><span data-stu-id="c32fc-251">Building and running the image in a container</span></span>

<span data-ttu-id="c32fc-252">Umożliwia tworzenie obrazu i uruchom usługę w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="c32fc-252">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="c32fc-253">Nie chcesz, wszystkie pliki z katalogu lokalnego do obrazu.</span><span class="sxs-lookup"><span data-stu-id="c32fc-253">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="c32fc-254">Zamiast tego będziesz tworzyć aplikacji w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="c32fc-254">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="c32fc-255">Utworzysz `.dockerignore` plik, aby określić katalogi, które nie są kopiowane do obrazu.</span><span class="sxs-lookup"><span data-stu-id="c32fc-255">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="c32fc-256">Nie chcesz dowolne zasoby kompilacji skopiowane.</span><span class="sxs-lookup"><span data-stu-id="c32fc-256">You don't want any of the build assets copied.</span></span> <span data-ttu-id="c32fc-257">Określ kompilację i publikowanie katalogów w `.dockerignore` pliku:</span><span class="sxs-lookup"><span data-stu-id="c32fc-257">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="c32fc-258">Tworzenia obrazów przy użyciu `docker build` polecenia.</span><span class="sxs-lookup"><span data-stu-id="c32fc-258">You build the image using the `docker build` command.</span></span> <span data-ttu-id="c32fc-259">Uruchom następujące polecenie z katalogu zawierającego kod w języku.</span><span class="sxs-lookup"><span data-stu-id="c32fc-259">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="c32fc-260">To polecenie powoduje utworzenie obrazu kontenera na podstawie informacji z pliku Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="c32fc-260">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="c32fc-261">`-t` Argument zawiera tag lub nazwę dla tego obrazu kontenera.</span><span class="sxs-lookup"><span data-stu-id="c32fc-261">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="c32fc-262">W powyższym wierszu polecenia jest znacznika używany w kontenerze platformy Docker `weather-microservice`.</span><span class="sxs-lookup"><span data-stu-id="c32fc-262">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="c32fc-263">Po wykonaniu tego polecenia, masz kontener gotowe do uruchomienia nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="c32fc-263">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="c32fc-264">Uruchom następujące polecenie, aby uruchomić kontenera i uruchomić usługi:</span><span class="sxs-lookup"><span data-stu-id="c32fc-264">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

<span data-ttu-id="c32fc-265">`-d` Opcji oznacza, że uruchomienia kontenera odłączona od bieżącego terminalu.</span><span class="sxs-lookup"><span data-stu-id="c32fc-265">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="c32fc-266">Oznacza to, że dane wyjściowe polecenia nie będą widzieć w terminalu.</span><span class="sxs-lookup"><span data-stu-id="c32fc-266">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="c32fc-267">`-p` Opcja wskazuje mapowanie portów między usługą i hosta.</span><span class="sxs-lookup"><span data-stu-id="c32fc-267">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="c32fc-268">W tym miejscu mówi, że wszystkie żądania przychodzącego na porcie 80 powinien być przekazywany do portu 80 w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="c32fc-268">Here it says that any incoming request on port 80 should be forwarded to port 80 on the container.</span></span> <span data-ttu-id="c32fc-269">Za pomocą 80 zastępuje port, który nasłuchuje usługi, i jest domyślnym portem dla aplikacji produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="c32fc-269">Using 80 matches the port your service is listening on, which is the default port for production applications.</span></span> <span data-ttu-id="c32fc-270">`--name` Argument nazwy działającym kontenerem.</span><span class="sxs-lookup"><span data-stu-id="c32fc-270">The `--name` argument names your running container.</span></span> <span data-ttu-id="c32fc-271">Jest wygodną nazwę, której można użyć do pracy z tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="c32fc-271">It's a convenient name you can use to work with that container.</span></span>

<span data-ttu-id="c32fc-272">Możesz zobaczyć, czy obraz jest uruchomiona, sprawdzając polecenia:</span><span class="sxs-lookup"><span data-stu-id="c32fc-272">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="c32fc-273">Jeśli Twój kontener działa, zobaczysz wiersza, który jest wyświetlany w uruchomionych procesów.</span><span class="sxs-lookup"><span data-stu-id="c32fc-273">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="c32fc-274">(Może być tylko jeden).</span><span class="sxs-lookup"><span data-stu-id="c32fc-274">(It may be the only one.)</span></span>

<span data-ttu-id="c32fc-275">Usługi można sprawdzić, otwierając przeglądarkę i przejdź do hosta lokalnego i określenie szerokości i długości geograficznej:</span><span class="sxs-lookup"><span data-stu-id="c32fc-275">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="c32fc-276">Dołączanie do uruchomionego kontenera</span><span class="sxs-lookup"><span data-stu-id="c32fc-276">Attaching to a running container</span></span>

<span data-ttu-id="c32fc-277">Po uruchomieniu usługi w oknie polecenia można uzyskać informacje diagnostyczne drukowania dla każdego żądania.</span><span class="sxs-lookup"><span data-stu-id="c32fc-277">When you ran your service in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="c32fc-278">Nie widzisz tych informacji, gdy kontener jest uruchomiony w trybie odłączonym.</span><span class="sxs-lookup"><span data-stu-id="c32fc-278">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="c32fc-279">Platformy Docker dołączyć polecenia umożliwia dołączanie do uruchomionego kontenera, dzięki czemu można wyświetlić informacje dziennika.</span><span class="sxs-lookup"><span data-stu-id="c32fc-279">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="c32fc-280">Uruchom następujące polecenie z poziomu okna polecenia:</span><span class="sxs-lookup"><span data-stu-id="c32fc-280">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="c32fc-281">`--sig-proxy=false` Argument oznacza, że <kbd>Ctrl</kbd>+<kbd>C</kbd> polecenia nie są wysyłane do procesu kontenera, lecz raczej zatrzymać `docker attach` polecenia.</span><span class="sxs-lookup"><span data-stu-id="c32fc-281">The `--sig-proxy=false` argument means that <kbd>Ctrl</kbd>+<kbd>C</kbd> commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="c32fc-282">Ostatni argument jest nazwa nadana kontenera w `docker run` polecenia.</span><span class="sxs-lookup"><span data-stu-id="c32fc-282">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="c32fc-283">Przypisany identyfikator kontenera platformy Docker można również użyć do odwoływania się do dowolnego kontenera.</span><span class="sxs-lookup"><span data-stu-id="c32fc-283">You can also use the Docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="c32fc-284">Jeśli nie określono nazwy kontenera w `docker run` należy użyć identyfikator kontenera.</span><span class="sxs-lookup"><span data-stu-id="c32fc-284">If you didn't specify a name for your container in `docker run` you must use the container ID.</span></span>

<span data-ttu-id="c32fc-285">Otwórz przeglądarkę i przejdź do usługi.</span><span class="sxs-lookup"><span data-stu-id="c32fc-285">Open a browser and navigate to your service.</span></span> <span data-ttu-id="c32fc-286">Zostaną wyświetlone komunikaty diagnostyczne w oknie polecenia z dołączonym uruchomionego kontenera.</span><span class="sxs-lookup"><span data-stu-id="c32fc-286">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="c32fc-287">Naciśnij klawisz <kbd>Ctrl</kbd>+<kbd>C</kbd> można zatrzymać procesu dołączania.</span><span class="sxs-lookup"><span data-stu-id="c32fc-287">Press <kbd>Ctrl</kbd>+<kbd>C</kbd> to stop the attach process.</span></span>

<span data-ttu-id="c32fc-288">Po zakończeniu pracy z kontenera, możesz zatrzymać:</span><span class="sxs-lookup"><span data-stu-id="c32fc-288">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="c32fc-289">Kontener i obraz jest nadal dostępna w przypadku ponownego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="c32fc-289">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="c32fc-290">Jeśli chcesz usunąć kontener z komputera, należy użyć tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c32fc-290">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="c32fc-291">Jeśli chcesz usunąć nieużywane obrazy z komputera, należy użyć tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c32fc-291">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="c32fc-292">Wniosek</span><span class="sxs-lookup"><span data-stu-id="c32fc-292">Conclusion</span></span> 

<span data-ttu-id="c32fc-293">W ramach tego samouczka skompilowane mikrousług platformy ASP.NET Core, a wyposażony w kilka funkcji proste.</span><span class="sxs-lookup"><span data-stu-id="c32fc-293">In this tutorial, you built an ASP.NET Core microservice, and added a few simple features.</span></span>

<span data-ttu-id="c32fc-294">Wbudowane obrazu kontenera na potrzeby usługi Docker i uruchomienia kontenera na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c32fc-294">You built a Docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="c32fc-295">Dołączony oknie terminalu do usługi i dostrzegła komunikaty diagnostyczne z poziomu usługi.</span><span class="sxs-lookup"><span data-stu-id="c32fc-295">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="c32fc-296">Po drodze pokazano kilka funkcji C# języka w działaniu.</span><span class="sxs-lookup"><span data-stu-id="c32fc-296">Along the way, you saw several features of the C# language in action.</span></span>
