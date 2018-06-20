---
title: Mikrousług hostowanych w Docker - C#
description: Dowiedz się, jak utworzyć asp.net podstawowe usługi, które są uruchamiane w kontenerach Docker
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: b043b0109bcf8a67867d2c73a5ab22e43a4963cf
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208387"
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="b738e-103">Mikrousług hostowanych w Docker</span><span class="sxs-lookup"><span data-stu-id="b738e-103">Microservices hosted in Docker</span></span>

<span data-ttu-id="b738e-104">W tym samouczku opisano zadania niezbędne do tworzenia i wdrażania mikrousługi platformy ASP.NET Core w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="b738e-104">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="b738e-105">W trakcie tego samouczka dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="b738e-105">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="b738e-106">Jak wygenerować aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b738e-106">How to generate an ASP.NET Core application.</span></span>
* <span data-ttu-id="b738e-107">Jak utworzyć środowisko deweloperskie Docker.</span><span class="sxs-lookup"><span data-stu-id="b738e-107">How to create a development Docker environment.</span></span>
* <span data-ttu-id="b738e-108">Jak utworzyć obraz Docker na podstawie istniejącego obrazu.</span><span class="sxs-lookup"><span data-stu-id="b738e-108">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="b738e-109">Jak wdrożyć usługę w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="b738e-109">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="b738e-110">Na bieżąco zostanie wyświetlony również pewne funkcje języka C#:</span><span class="sxs-lookup"><span data-stu-id="b738e-110">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="b738e-111">Jak konwertować obiekty C# ładunek JSON.</span><span class="sxs-lookup"><span data-stu-id="b738e-111">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="b738e-112">Jak utworzyć obiekty niezmienne transferu danych.</span><span class="sxs-lookup"><span data-stu-id="b738e-112">How to build immutable Data Transfer Objects.</span></span>
* <span data-ttu-id="b738e-113">Jak do przetwarzania przychodzących żądań HTTP oraz do generowania odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="b738e-113">How to process incoming HTTP Requests and generate the HTTP Response.</span></span>
* <span data-ttu-id="b738e-114">Jak pracować z typów wartości null.</span><span class="sxs-lookup"><span data-stu-id="b738e-114">How to work with nullable value types.</span></span>

<span data-ttu-id="b738e-115">Możesz [wyświetlić lub pobrać przykładową aplikację](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) dla tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b738e-115">You can [view or download the sample app](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="b738e-116">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="b738e-116">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="why-docker"></a><span data-ttu-id="b738e-117">Dlaczego Docker?</span><span class="sxs-lookup"><span data-stu-id="b738e-117">Why Docker?</span></span>

<span data-ttu-id="b738e-118">Docker można łatwo tworzyć obrazy standardowe maszyny do hostowania usług w centrum danych lub w chmurze publicznej.</span><span class="sxs-lookup"><span data-stu-id="b738e-118">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="b738e-119">Docker umożliwia konfigurowanie obrazu i replikować ją w razie potrzeby można skalować instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-119">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="b738e-120">Cały kod w tym samouczku będzie działać w dowolnym środowisku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b738e-120">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="b738e-121">Dodatkowe zadania dotyczące instalacji Docker będzie działać dla aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b738e-121">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="b738e-122">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b738e-122">Prerequisites</span></span>

<span data-ttu-id="b738e-123">Należy skonfigurować komputer, aby uruchomić oprogramowanie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b738e-123">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="b738e-124">Instrukcje instalacji można znaleźć na [.NET Core](https://www.microsoft.com/net/core) strony.</span><span class="sxs-lookup"><span data-stu-id="b738e-124">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="b738e-125">Można uruchomić tej aplikacji, w systemie Windows, Linux, macOS lub w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="b738e-125">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="b738e-126">Należy zainstalować w edytorze kodu dotyczącego elementów ulubionych.</span><span class="sxs-lookup"><span data-stu-id="b738e-126">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="b738e-127">Opisy poniżej użyj [Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora.</span><span class="sxs-lookup"><span data-stu-id="b738e-127">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="b738e-128">Można jednak użyć dowolnego narzędzia potrafisz.</span><span class="sxs-lookup"><span data-stu-id="b738e-128">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="b738e-129">Należy również zainstalować aparatem platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="b738e-129">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="b738e-130">Zobacz [strona instalacji Docker](http://www.docker.com/products/docker) instrukcje dla danej platformy.</span><span class="sxs-lookup"><span data-stu-id="b738e-130">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="b738e-131">Docker można zainstalować wiele dystrybucje systemu Linux, macOS lub systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b738e-131">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="b738e-132">Strona powyżej zawiera sekcje do każdego z dostępnych instalacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-132">The page referenced above contains sections to each of the available installations.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="b738e-133">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="b738e-133">Create the Application</span></span>

<span data-ttu-id="b738e-134">Teraz, po zainstalowaniu wszystkich narzędzi do tworzenia nowej aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b738e-134">Now that you've installed all the tools, create a new ASP.NET Core application.</span></span> <span data-ttu-id="b738e-135">Aby to zrobić, Utwórz nowy katalog o nazwie "WeatherMicroservice" i uruchom następujące polecenie, w tym katalogu w ulubionych powłoki:</span><span class="sxs-lookup"><span data-stu-id="b738e-135">To do that, create a new directory called "WeatherMicroservice" and execute the following command in that directory in your favorite shell:</span></span>

```console
dotnet new web
```

<span data-ttu-id="b738e-136">`dotnet` Polecenia są uruchamiane narzędzia niezbędne do tworzenia aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="b738e-136">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="b738e-137">Każdy zlecenie wykonuje inne polecenie.</span><span class="sxs-lookup"><span data-stu-id="b738e-137">Each verb executes a different command.</span></span>

<span data-ttu-id="b738e-138">`dotnet new` Polecenie służy do tworzenia .net Core projektów.</span><span class="sxs-lookup"><span data-stu-id="b738e-138">The `dotnet new` command is used to create .Net Core projects.</span></span>

<span data-ttu-id="b738e-139">Dla tego mikrousługi chcemy aplikacji sieci web najprostszy, najbardziej lekkie to możliwe, więc użyliśmy "Core pustego szablonu platformy ASP.NET", określając jej nazwę krótką `web`.</span><span class="sxs-lookup"><span data-stu-id="b738e-139">For this microservice, we want the simplest, most lightweight web application possible, so we used the "ASP.NET Core Empty" template, by specifying its short name, `web`.</span></span>

<span data-ttu-id="b738e-140">Szablon tworzy cztery pliki:</span><span class="sxs-lookup"><span data-stu-id="b738e-140">The template creates four files for you:</span></span>

* <span data-ttu-id="b738e-141">Pliku Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="b738e-141">A Startup.cs file.</span></span> <span data-ttu-id="b738e-142">Zawiera podstawę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-142">This contains the basis of the application.</span></span>
* <span data-ttu-id="b738e-143">Plik Program.cs.</span><span class="sxs-lookup"><span data-stu-id="b738e-143">A Program.cs file.</span></span> <span data-ttu-id="b738e-144">Zawiera punkt wejścia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-144">This contains the entry point of the application.</span></span>
* <span data-ttu-id="b738e-145">Plik WeatherMicroservice.csproj.</span><span class="sxs-lookup"><span data-stu-id="b738e-145">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="b738e-146">To jest plik kompilacji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-146">This is the build file for the application.</span></span>
* <span data-ttu-id="b738e-147">Plik Properties/launchSettings.json.</span><span class="sxs-lookup"><span data-stu-id="b738e-147">A Properties/launchSettings.json file.</span></span> <span data-ttu-id="b738e-148">Zawiera ustawienia debugowania używane przez IDEs.</span><span class="sxs-lookup"><span data-stu-id="b738e-148">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="b738e-149">Teraz możesz uruchomić aplikacji szablonu wygenerowanego:</span><span class="sxs-lookup"><span data-stu-id="b738e-149">Now you can run the template generated application:</span></span>

```console
dotnet run
```

<span data-ttu-id="b738e-150">To polecenie spowoduje przywrócenie najpierw zależności wymagane do tworzenia aplikacji i późniejszego kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-150">This command will first restore dependencies required to build the application and then it will build the application.</span></span>

<span data-ttu-id="b738e-151">Domyślna konfiguracja nasłuchuje `http://localhost:5000`.</span><span class="sxs-lookup"><span data-stu-id="b738e-151">The default configuration listens to `http://localhost:5000`.</span></span> <span data-ttu-id="b738e-152">Można otworzyć przeglądarkę i przejdź do strony i "Witaj świecie!" w temacie</span><span class="sxs-lookup"><span data-stu-id="b738e-152">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="b738e-153">Komunikat.</span><span class="sxs-lookup"><span data-stu-id="b738e-153">message.</span></span>

<span data-ttu-id="b738e-154">Gdy wszystko będzie gotowe, można zamknąć aplikacji, naciskając klawisz <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b738e-154">When you're done, you can shut down the application by pressing <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="b738e-155">Anatomia aplikacji platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b738e-155">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="b738e-156">Teraz gdy masz utworzoną aplikację, Przyjrzyjmy się implementowania tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b738e-156">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="b738e-157">Istnieją dwa wygenerowanych plików, które są w tym momencie zastosowanie szczególnie: WeatherMicroservice.csproj i Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="b738e-157">There are two of the generated files that are particularly interesting at this point: WeatherMicroservice.csproj and Startup.cs.</span></span> 

<span data-ttu-id="b738e-158">Pliku .csproj zawiera informacje o projekcie.</span><span class="sxs-lookup"><span data-stu-id="b738e-158">The .csproj file contains information about the project.</span></span>
<span data-ttu-id="b738e-159">Są dwa węzły, które są najbardziej interesujące `<TargetFramework>` i `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="b738e-159">The two nodes that are most interesting are `<TargetFramework>` and `<PackageReference>`.</span></span>

<span data-ttu-id="b738e-160">`<TargetFramework>` Węzeł określa wersję platformy .NET, która może uruchomić tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="b738e-160">The `<TargetFramework>` node specifies the version of .NET that will run this application.</span></span>

<span data-ttu-id="b738e-161">Każdy `<PackageReference>` węzła jest używany do określenia pakietu, który jest wymagany dla tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-161">Each `<PackageReference>` node is used to specify a package that is needed for this application.</span></span>

<span data-ttu-id="b738e-162">Aplikacja jest zaimplementowana w pliku Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="b738e-162">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="b738e-163">Ten plik zawiera klasę uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="b738e-163">This file contains the startup class.</span></span>

<span data-ttu-id="b738e-164">Te dwie metody są wywoływane przez infrastrukturę platformy ASP.NET Core, aby skonfigurować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b738e-164">The two methods are called by the ASP.NET Core infrastructure to configure and run the application.</span></span> <span data-ttu-id="b738e-165">`ConfigureServices` Metoda opisuje usług, które są niezbędne dla tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-165">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="b738e-166">Tworzysz mikrousługi gotowa, więc nie trzeba skonfigurować wszelkie zależności.</span><span class="sxs-lookup"><span data-stu-id="b738e-166">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="b738e-167">`Configure` Metody konfiguruje obsługi przychodzących żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="b738e-167">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="b738e-168">Szablon generuje prosty program obsługi, który ma odpowiadać na każde żądanie od tekstu "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="b738e-168">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="b738e-169">Tworzenie mikrousługi</span><span class="sxs-lookup"><span data-stu-id="b738e-169">Build a microservice</span></span>

<span data-ttu-id="b738e-170">Możesz zacząć kompilacji usługi będzie dostarczać pogody z dowolnego miejsca na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="b738e-170">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="b738e-171">W aplikacji produkcyjnej możesz wywołać niektóre usługi do pobierania danych pogody.</span><span class="sxs-lookup"><span data-stu-id="b738e-171">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="b738e-172">Dla naszej próbki możemy zostanie wygenerowany losowe prognozie pogody.</span><span class="sxs-lookup"><span data-stu-id="b738e-172">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="b738e-173">Istnieje wiele zadań, które należy wykonać w celu wdrożenia naszej usługi pogody losowe:</span><span class="sxs-lookup"><span data-stu-id="b738e-173">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="b738e-174">Analizuje przychodzące żądanie odczytu współrzędne geograficzne.</span><span class="sxs-lookup"><span data-stu-id="b738e-174">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="b738e-175">Generowanie niektórych losowe dane prognozy.</span><span class="sxs-lookup"><span data-stu-id="b738e-175">Generate some random forecast data.</span></span>
* <span data-ttu-id="b738e-176">Konwertowanie losowe dane prognozy z C# obiektów JSON pakietów.</span><span class="sxs-lookup"><span data-stu-id="b738e-176">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="b738e-177">Ustaw nagłówek odpowiedzi, aby wskazać, że Twoje wyśle usługi z powrotem JSON.</span><span class="sxs-lookup"><span data-stu-id="b738e-177">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="b738e-178">Zapisu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="b738e-178">Write the response.</span></span>

<span data-ttu-id="b738e-179">Kolejnych sekcjach prowadzą użytkownika przez każdy z tych kroków.</span><span class="sxs-lookup"><span data-stu-id="b738e-179">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="b738e-180">Podczas analizowania ciągu zapytania</span><span class="sxs-lookup"><span data-stu-id="b738e-180">Parsing the Query String</span></span>

<span data-ttu-id="b738e-181">Zostaną analizując ciąg zapytania.</span><span class="sxs-lookup"><span data-stu-id="b738e-181">You'll begin by parsing the query string.</span></span> <span data-ttu-id="b738e-182">Usługa będzie akceptować "lat" i "long" argumentów dla ciągu zapytania w tym formularzu:</span><span class="sxs-lookup"><span data-stu-id="b738e-182">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

<span data-ttu-id="b738e-183">Wszystkie zmiany, które należy podjąć są zdefiniowane jako argument wyrażenia lambda `app.Run` w klasie uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="b738e-183">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="b738e-184">Argument na wyrażeniu lambda jest `HttpContext` dla żądania.</span><span class="sxs-lookup"><span data-stu-id="b738e-184">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="b738e-185">Jedną z właściwości jest `Request` obiektu.</span><span class="sxs-lookup"><span data-stu-id="b738e-185">One of its properties is the `Request` object.</span></span> <span data-ttu-id="b738e-186">`Request` Obiekt ma `Query` właściwość, która zawiera słownik wszystkich wartości na ciąg zapytania dla żądania.</span><span class="sxs-lookup"><span data-stu-id="b738e-186">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="b738e-187">Dodanie pierwszy jest to znalezienie wartości szerokości i długości geograficznej:</span><span class="sxs-lookup"><span data-stu-id="b738e-187">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="b738e-188">`Query` Słownika wartości są `StringValue` typu.</span><span class="sxs-lookup"><span data-stu-id="b738e-188">The `Query` dictionary values are `StringValue` type.</span></span> <span data-ttu-id="b738e-189">Tego typu może zawierać kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="b738e-189">That type can contain a collection of strings.</span></span> <span data-ttu-id="b738e-190">Usługi pogodzie każda wartość jest pojedynczy ciąg.</span><span class="sxs-lookup"><span data-stu-id="b738e-190">For your weather service, each value is a single string.</span></span> <span data-ttu-id="b738e-191">Dlatego jest wywołanie `FirstOrDefault()` w powyższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b738e-191">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="b738e-192">Następnie należy konwertować ciągi na symulacyjnych.</span><span class="sxs-lookup"><span data-stu-id="b738e-192">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="b738e-193">Metoda służy do przekonwertowania ciągu na wartość typu double jest `double.TryParse()`:</span><span class="sxs-lookup"><span data-stu-id="b738e-193">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="b738e-194">Ta metoda wykorzystuje C# limit parametrów, aby wskazać, czy ciąg wejściowy można przekonwertować na wartość typu double.</span><span class="sxs-lookup"><span data-stu-id="b738e-194">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="b738e-195">Jeśli ciąg reprezentują reprezentację prawidłową wartość o podwójnej precyzji, metoda zwraca wartość true i `result` argument zawiera wartość.</span><span class="sxs-lookup"><span data-stu-id="b738e-195">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="b738e-196">Jeśli ciąg nie reprezentuje prawidłową wartość o podwójnej precyzji, metoda zwraca wartość false.</span><span class="sxs-lookup"><span data-stu-id="b738e-196">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="b738e-197">Istnieje możliwość dostosowania tego interfejsu API przy użyciu *— metoda rozszerzenia* zwracającą *wartości null typu double*.</span><span class="sxs-lookup"><span data-stu-id="b738e-197">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="b738e-198">A *typ dopuszczający wartość null wartości* jest typem, który reprezentuje pewien typ wartości i również przechowywane braku lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="b738e-198">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="b738e-199">Typ dopuszczający wartość null jest reprezentowana przez dodanie `?` znak do deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="b738e-199">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="b738e-200">Metody rozszerzenia są metody, które są zdefiniowane jako metody statyczne, ale przez dodanie `this` modyfikator w pierwszym parametrze można wywołać tak, jakby są oni członkami tej klasy.</span><span class="sxs-lookup"><span data-stu-id="b738e-200">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="b738e-201">Metody rozszerzenia można zdefiniować tylko w klasach statycznych.</span><span class="sxs-lookup"><span data-stu-id="b738e-201">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="b738e-202">Poniżej przedstawiono definicję klasy zawierające metody rozszerzenia dla analizy:</span><span class="sxs-lookup"><span data-stu-id="b738e-202">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="b738e-203">Przed wywołaniem metody rozszerzenia, należy zmienić bieżącej kultury invariant:</span><span class="sxs-lookup"><span data-stu-id="b738e-203">Before calling the extension method, change the current culture to invariant:</span></span>

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

<span data-ttu-id="b738e-204">Dzięki temu, że Twojej aplikacji po analizie numery takie same na każdym serwerze, niezależnie od jego domyślną kulturę.</span><span class="sxs-lookup"><span data-stu-id="b738e-204">This ensures that your application parses numbers the same on any server, regardless of its default culture.</span></span>

<span data-ttu-id="b738e-205">Teraz można użyć — metoda rozszerzenia Aby przekonwertować typu double argumenty ciągu zapytania:</span><span class="sxs-lookup"><span data-stu-id="b738e-205">Now you can use the extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="b738e-206">Aby łatwo testowania analizy kodu, należy zaktualizować odpowiedzi, aby uwzględnić wartości argumentów:</span><span class="sxs-lookup"><span data-stu-id="b738e-206">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="b738e-207">W tym momencie można uruchomić aplikacji sieci web i czy działa analizy kodu.</span><span class="sxs-lookup"><span data-stu-id="b738e-207">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="b738e-208">Dodawanie wartości do żądania sieci web w przeglądarce i powinna zostać wyświetlona zaktualizowanych wyników.</span><span class="sxs-lookup"><span data-stu-id="b738e-208">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="b738e-209">Losowe prognozie pogody kompilacji</span><span class="sxs-lookup"><span data-stu-id="b738e-209">Build a random weather forecast</span></span>

<span data-ttu-id="b738e-210">Następnym zadaniem jest losowe prognozie pogody kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-210">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="b738e-211">Zacznijmy od kontener danych, który zawiera wartości, które mają dla prognozie pogody:</span><span class="sxs-lookup"><span data-stu-id="b738e-211">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

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

<span data-ttu-id="b738e-212">Następnie utwórz konstruktora, który losowo ustawia te wartości.</span><span class="sxs-lookup"><span data-stu-id="b738e-212">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="b738e-213">Ten konstruktor korzysta wartości dla współrzędne geograficzne do inicjatora `Random` generatora liczb.</span><span class="sxs-lookup"><span data-stu-id="b738e-213">This constructor uses the values for the latitude and longitude to seed the `Random` number generator.</span></span> <span data-ttu-id="b738e-214">Oznacza to, że prognozy dla tej samej lokalizacji jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="b738e-214">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="b738e-215">Jeśli zmienisz argumenty współrzędne geograficzne, uzyskasz różnych prognozy (ponieważ rozpoczynać różnych inicjatora).</span><span class="sxs-lookup"><span data-stu-id="b738e-215">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed).</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="b738e-216">Teraz można wygenerować prognozy 5 dni w metodę odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="b738e-216">You can now generate the 5-day forecast in your response method:</span></span>

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

### <a name="build-the-json-response"></a><span data-ttu-id="b738e-217">Tworzenie odpowiedź w formacie JSON</span><span class="sxs-lookup"><span data-stu-id="b738e-217">Build the JSON response</span></span>

<span data-ttu-id="b738e-218">Zadanie kodu końcowego na serwerze jest konwersja `WeatherReport` listy w dokumencie JSON i wysyłania, która z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="b738e-218">The final code task on the server is to convert the `WeatherReport` list into JSON document, and send that back to the client.</span></span> <span data-ttu-id="b738e-219">Zacznijmy od utworzenia dokumentu JSON.</span><span class="sxs-lookup"><span data-stu-id="b738e-219">Let's start by creating the JSON document.</span></span> <span data-ttu-id="b738e-220">Serializator Newtonsoft JSON zostanie dodana do listy zależności.</span><span class="sxs-lookup"><span data-stu-id="b738e-220">You'll add the Newtonsoft JSON serializer to the list of dependencies.</span></span> <span data-ttu-id="b738e-221">Możesz to zrobić przy użyciu następujących `dotnet` polecenia:</span><span class="sxs-lookup"><span data-stu-id="b738e-221">You can do that using the following `dotnet` command:</span></span>

```console
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="b738e-222">Następnie należy użyć `JsonConvert` klasa umożliwiająca zapisanie obiektu na ciąg:</span><span class="sxs-lookup"><span data-stu-id="b738e-222">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="b738e-223">Powyższy kod konwertuje obiekt prognozy (lista `WeatherForecast` obiekty) w dokumencie JSON.</span><span class="sxs-lookup"><span data-stu-id="b738e-223">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON document.</span></span> <span data-ttu-id="b738e-224">Po skonstruowaniu dokumentu odpowiedzi, Ustaw typ zawartości `application/json`i zapisać ciąg.</span><span class="sxs-lookup"><span data-stu-id="b738e-224">After you've constructed the response document, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="b738e-225">Teraz aplikacji działa i zwraca losowe prognoz.</span><span class="sxs-lookup"><span data-stu-id="b738e-225">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="b738e-226">Utwórz obraz Docker</span><span class="sxs-lookup"><span data-stu-id="b738e-226">Build a Docker image</span></span>

<span data-ttu-id="b738e-227">Nasze ostatnim zadaniem jest aby uruchomić aplikację w Docker.</span><span class="sxs-lookup"><span data-stu-id="b738e-227">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="b738e-228">Utworzymy kontener Docker uruchomionym obrazem Docker reprezentujący naszej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-228">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="b738e-229">A ***Docker obrazu*** jest plik definiujący środowisko do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-229">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="b738e-230">A ***kontenera Docker*** reprezentuje działającego wystąpienia obrazu Docker.</span><span class="sxs-lookup"><span data-stu-id="b738e-230">A ***Docker Container*** represents a running instance of a Docker Image.</span></span>

<span data-ttu-id="b738e-231">Analogicznie, można traktować *obrazu Docker* jako *klasy*i *kontenera Docker* jako obiekt lub wystąpienia tej klasy.</span><span class="sxs-lookup"><span data-stu-id="b738e-231">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="b738e-232">Następujący plik Dockerfile będzie służyć do naszej celów:</span><span class="sxs-lookup"><span data-stu-id="b738e-232">The following Dockerfile will serve for our purposes:</span></span>

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

<span data-ttu-id="b738e-233">Przejdźmy za pośrednictwem jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="b738e-233">Let's go over its contents.</span></span>

<span data-ttu-id="b738e-234">Pierwszy wiersz określa obrazu źródłowego używaną do tworzenia aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b738e-234">The first line specifies the source image used for building the application:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
```

<span data-ttu-id="b738e-235">Docker pozwala na skonfigurowanie obraz maszyny, na podstawie szablonu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="b738e-235">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="b738e-236">To oznacza, nie trzeba podać parametry maszyny, podczas uruchamiania, wystarczy podać wszelkie zmiany.</span><span class="sxs-lookup"><span data-stu-id="b738e-236">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="b738e-237">Zmiany w tym miejscu należy dołączyć naszej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-237">The changes here will be to include our application.</span></span>

<span data-ttu-id="b738e-238">W tym przykładzie użyjemy `2.1-sdk` wersji `dotnet` obrazu.</span><span class="sxs-lookup"><span data-stu-id="b738e-238">In this sample, we'll use the `2.1-sdk` version of the `dotnet` image.</span></span> <span data-ttu-id="b738e-239">Jest to najprostszy sposób tworzenia działającego środowiska Docker.</span><span class="sxs-lookup"><span data-stu-id="b738e-239">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="b738e-240">Ten obraz zawiera środowisko uruchomieniowe .NET Core i Core SDK platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="b738e-240">This image includes the .NET Core runtime, and the .NET Core SDK.</span></span>
<span data-ttu-id="b738e-241">Który ułatwia rozpoczęcie pracy i kompilacji, ale utworzyć większy obraz, dlatego użyjemy tego obrazu do tworzenia aplikacji i inny obraz go uruchomić.</span><span class="sxs-lookup"><span data-stu-id="b738e-241">That makes it easier to get started and build, but does create a larger image, so we'll use this image for building the application and a different image to run it.</span></span>

<span data-ttu-id="b738e-242">Następne wiersze Instalatora i skompilować aplikację:</span><span class="sxs-lookup"><span data-stu-id="b738e-242">The next lines setup and build your application:</span></span>

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="b738e-243">Spowoduje to skopiuj plik projektu z bieżącego katalogu do maszyny Wirtualnej platformy Docker i przywrócić wszystkie pakiety.</span><span class="sxs-lookup"><span data-stu-id="b738e-243">This will copy the project file from the  current directory to the Docker VM, and restore all the packages.</span></span> <span data-ttu-id="b738e-244">Użycie dotnet interfejsu wiersza polecenia oznacza, że obraz Docker musi zawierać .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="b738e-244">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="b738e-245">Po wykonaniu tej pozostałej części aplikacji są kopiowane i `dotnet
publish` polecenie tworzy i pakiety aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-245">After that, the rest of your application gets copied, and the `dotnet
publish` command builds and packages your application.</span></span>

<span data-ttu-id="b738e-246">Na koniec utworzymy obraz Docker drugiej, który uruchomi aplikację:</span><span class="sxs-lookup"><span data-stu-id="b738e-246">Finally, we create a second Docker image that runs the application:</span></span>

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="b738e-247">Używa tego obrazu `2.1-aspnetcore-runtime` wersji `dotnet` obrazu, który zawiera wszystkie elementy niezbędne do uruchomienia aplikacji platformy ASP.NET Core, ale nie zawiera zestawu SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b738e-247">This image uses the `2.1-aspnetcore-runtime` version of the `dotnet` image, which contains everything necessary to run ASP.NET Core applications, but does not include the .NET Core SDK.</span></span> <span data-ttu-id="b738e-248">Oznacza to, ten obraz nie może służyć do tworzenia aplikacji platformy .NET Core, ale zapewnia także finalnego obrazu mniejsze.</span><span class="sxs-lookup"><span data-stu-id="b738e-248">This means this image can't be used to build .NET Core applications, but it also makes the final image smaller.</span></span>

<span data-ttu-id="b738e-249">Aby działało, możemy skopiować zbudowanych aplikacji z pierwszego obrazu do drugiej.</span><span class="sxs-lookup"><span data-stu-id="b738e-249">To make this work, we copy the built application from the first image to the second one.</span></span>

<span data-ttu-id="b738e-250">`ENTRYPOINT` Polecenie informuje Docker, jakie polecenia uruchamia usługę.</span><span class="sxs-lookup"><span data-stu-id="b738e-250">The `ENTRYPOINT` command informs Docker what command starts the service.</span></span>

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="b738e-251">Tworzenie i uruchamianie obrazu w kontenerze</span><span class="sxs-lookup"><span data-stu-id="b738e-251">Building and running the image in a container</span></span>

<span data-ttu-id="b738e-252">Umożliwia tworzenie obrazu i uruchom usługę w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="b738e-252">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="b738e-253">Nie ma wszystkich plików z katalogu lokalnego kopiowane do obrazu.</span><span class="sxs-lookup"><span data-stu-id="b738e-253">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="b738e-254">Zamiast tego zostanie utworzenie aplikacji w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="b738e-254">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="b738e-255">Utworzysz `.dockerignore` plik, aby określić katalogi, które nie są kopiowane do obrazu.</span><span class="sxs-lookup"><span data-stu-id="b738e-255">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="b738e-256">Nie ma żadnego zasoby kompilacji skopiowane.</span><span class="sxs-lookup"><span data-stu-id="b738e-256">You don't want any of the build assets copied.</span></span> <span data-ttu-id="b738e-257">Określ kompilację i publikowanie katalogów w `.dockerignore` pliku:</span><span class="sxs-lookup"><span data-stu-id="b738e-257">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="b738e-258">Tworzenie, przy użyciu obrazu `docker build` polecenia.</span><span class="sxs-lookup"><span data-stu-id="b738e-258">You build the image using the `docker build` command.</span></span> <span data-ttu-id="b738e-259">Uruchom następujące polecenie z katalogu z kodem.</span><span class="sxs-lookup"><span data-stu-id="b738e-259">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="b738e-260">To polecenie tworzy obraz kontenera, zgodnie z informacjami w Twojej plik Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="b738e-260">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="b738e-261">`-t` Argument zawiera tag lub nazwę dla tego obrazu kontenera.</span><span class="sxs-lookup"><span data-stu-id="b738e-261">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="b738e-262">W powyższym wierszu polecenia jest znacznik kontenera Docker `weather-microservice`.</span><span class="sxs-lookup"><span data-stu-id="b738e-262">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="b738e-263">Po zakończeniu wykonywania tego polecenia należy kontener gotowy do uruchomienia nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="b738e-263">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="b738e-264">Uruchom następujące polecenie, aby uruchomić kontenera i uruchomić usługi:</span><span class="sxs-lookup"><span data-stu-id="b738e-264">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

<span data-ttu-id="b738e-265">`-d` Opcja oznacza, że Uruchom kontenera odłączona od bieżącego terminala.</span><span class="sxs-lookup"><span data-stu-id="b738e-265">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="b738e-266">Oznacza to, że dane wyjściowe polecenia nie będą widzieć w terminalu.</span><span class="sxs-lookup"><span data-stu-id="b738e-266">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="b738e-267">`-p` Opcja wskazuje mapowanie portów między usługą i hosta.</span><span class="sxs-lookup"><span data-stu-id="b738e-267">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="b738e-268">W tym miejscu mówi, że wszystkie żądania przychodzącego na porcie 80 powinny być przekazywane do portu 80 w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="b738e-268">Here it says that any incoming request on port 80 should be forwarded to port 80 on the container.</span></span> <span data-ttu-id="b738e-269">Przy użyciu 80 odpowiada port, który nasłuchiwanie usługi, który jest domyślnym portem dla aplikacji produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="b738e-269">Using 80 matches the port your service is listening on, which is the default port for production applications.</span></span> <span data-ttu-id="b738e-270">`--name` Argument nazwy użytkownika uruchomionych kontenera.</span><span class="sxs-lookup"><span data-stu-id="b738e-270">The `--name` argument names your running container.</span></span> <span data-ttu-id="b738e-271">Jest to nazwa wygodny, używanej do pracy z tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="b738e-271">It's a convenient name you can use to work with that container.</span></span>

<span data-ttu-id="b738e-272">Możesz sprawdzić, czy obraz jest uruchomiony przez sprawdzenie, polecenie:</span><span class="sxs-lookup"><span data-stu-id="b738e-272">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="b738e-273">Jeśli działa z kontenera, zobaczysz wiersza, który jest wyświetlany w uruchomionych procesów.</span><span class="sxs-lookup"><span data-stu-id="b738e-273">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="b738e-274">(Może być tylko jeden).</span><span class="sxs-lookup"><span data-stu-id="b738e-274">(It may be the only one.)</span></span>

<span data-ttu-id="b738e-275">Usługi można sprawdzić, otwierając przeglądarkę i przechodząc do localhost i określający współrzędne geograficzne:</span><span class="sxs-lookup"><span data-stu-id="b738e-275">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="b738e-276">Dołączanie do uruchomionego kontenera</span><span class="sxs-lookup"><span data-stu-id="b738e-276">Attaching to a running container</span></span>

<span data-ttu-id="b738e-277">Po uruchomieniu usługi w oknie polecenia mogliby zobaczyć informacje diagnostyczne drukowane dla każdego żądania.</span><span class="sxs-lookup"><span data-stu-id="b738e-277">When you ran your service in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="b738e-278">Gdy z kontenera działa w trybie odłączony nie widzisz tych informacji.</span><span class="sxs-lookup"><span data-stu-id="b738e-278">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="b738e-279">Polecenie Dołącz Docker umożliwia dołączanie do uruchomionego kontenera tak, aby informacje dziennika.</span><span class="sxs-lookup"><span data-stu-id="b738e-279">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="b738e-280">W oknie polecenie Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="b738e-280">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="b738e-281">`--sig-proxy=false` Argumentu oznacza, że <kbd>Ctrl</kbd>+<kbd>C</kbd> poleceń nie wysyłana do procesu kontenera, ale raczej zatrzymać `docker attach` polecenia.</span><span class="sxs-lookup"><span data-stu-id="b738e-281">The `--sig-proxy=false` argument means that <kbd>Ctrl</kbd>+<kbd>C</kbd> commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="b738e-282">Ostatni argument jest nazwa kontenera w `docker run` polecenia.</span><span class="sxs-lookup"><span data-stu-id="b738e-282">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="b738e-283">Umożliwia także Docker przypisany identyfikator kontenera do odwoływania się do dowolnego kontenera.</span><span class="sxs-lookup"><span data-stu-id="b738e-283">You can also use the Docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="b738e-284">Jeśli nie określono nazwę Twojej kontenera w `docker run` musisz użyć identyfikatora kontenera.</span><span class="sxs-lookup"><span data-stu-id="b738e-284">If you didn't specify a name for your container in `docker run` you must use the container ID.</span></span>

<span data-ttu-id="b738e-285">Otwórz przeglądarkę i przejdź do usługi.</span><span class="sxs-lookup"><span data-stu-id="b738e-285">Open a browser and navigate to your service.</span></span> <span data-ttu-id="b738e-286">Zostanie wyświetlone komunikaty diagnostyczne w systemie windows polecenie z dołączonego uruchomionych kontenera.</span><span class="sxs-lookup"><span data-stu-id="b738e-286">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="b738e-287">Naciśnij klawisz <kbd>Ctrl</kbd>+<kbd>C</kbd> można zatrzymać procesu dołączania.</span><span class="sxs-lookup"><span data-stu-id="b738e-287">Press <kbd>Ctrl</kbd>+<kbd>C</kbd> to stop the attach process.</span></span>

<span data-ttu-id="b738e-288">Po zakończeniu pracy z Twojej kontenera, można zatrzymać go:</span><span class="sxs-lookup"><span data-stu-id="b738e-288">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="b738e-289">Kontener i obrazu jest wciąż dostępna na potrzeby ponownego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="b738e-289">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="b738e-290">Jeśli chcesz usunąć kontener z komputera, możesz użyć tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="b738e-290">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="b738e-291">Jeśli chcesz usunąć nieużywane obrazów z komputera, możesz użyć tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="b738e-291">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="b738e-292">Wniosek</span><span class="sxs-lookup"><span data-stu-id="b738e-292">Conclusion</span></span> 

<span data-ttu-id="b738e-293">W tym samouczku wbudowane mikrousługi platformy ASP.NET Core i dodać kilka prostych funkcji.</span><span class="sxs-lookup"><span data-stu-id="b738e-293">In this tutorial, you built an ASP.NET Core microservice, and added a few simple features.</span></span>

<span data-ttu-id="b738e-294">Wbudowane Docker kontenera obrazu dla tej usługi i uruchomienia tego kontenera na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b738e-294">You built a Docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="b738e-295">Dołączone do usługi okno terminalu i był wyświetlany komunikaty diagnostyczne z usługi.</span><span class="sxs-lookup"><span data-stu-id="b738e-295">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="b738e-296">Przeglądania widać kilka funkcji języka C# w akcji.</span><span class="sxs-lookup"><span data-stu-id="b738e-296">Along the way, you saw several features of the C# language in action.</span></span>
