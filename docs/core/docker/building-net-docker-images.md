---
title: Tworzenie obrazów platformy Docker programu .NET Core
description: Opis obrazów platformy Docker i platformy .NET Core
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 675b6821588f8d0dd9495346a13665a32986f060
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841167"
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="69f18-103">Tworzenie obrazów platformy Docker dla aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="69f18-103">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="69f18-104">W tym samouczku skupimy się na używanie platformy .NET Core w Docker.</span><span class="sxs-lookup"><span data-stu-id="69f18-104">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="69f18-105">Po pierwsze omówimy różnych obrazów platformy Docker, które są oferowane i konserwowane przez firmę Microsoft i przypadkami użycia.</span><span class="sxs-lookup"><span data-stu-id="69f18-105">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="69f18-106">Firma Microsoft następnie Dowiedz się, jak tworzyć i przekształcać aplikacji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="69f18-106">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="69f18-107">W trakcie tego samouczka dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="69f18-107">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="69f18-108">Więcej informacji na temat obrazów platformy Docker programu Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="69f18-108">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="69f18-109">Pobierz przykładową aplikację w celu Dockerize platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="69f18-109">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="69f18-110">Lokalne uruchamianie przykładowej aplikacji platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="69f18-110">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="69f18-111">Kompilowanie i uruchamianie przykładu z platformy Docker dla kontenerów systemu Linux</span><span class="sxs-lookup"><span data-stu-id="69f18-111">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="69f18-112">Kompilowanie i uruchamianie przykładu z kontenerów platformy Docker for Windows</span><span class="sxs-lookup"><span data-stu-id="69f18-112">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="69f18-113">Optymalizacje obrazu platformy docker</span><span class="sxs-lookup"><span data-stu-id="69f18-113">Docker Image Optimizations</span></span>

<span data-ttu-id="69f18-114">Tworzenie obrazów platformy Docker dla deweloperów, skupiliśmy się na trzech głównych scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="69f18-114">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="69f18-115">Obrazy używane do tworzenia aplikacji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="69f18-115">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="69f18-116">Obrazy używane do tworzenia aplikacji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="69f18-116">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="69f18-117">Obrazy używane do uruchamiania aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="69f18-117">Images used to run .NET Core apps</span></span>

<span data-ttu-id="69f18-118">Dlaczego trzy obrazy?</span><span class="sxs-lookup"><span data-stu-id="69f18-118">Why three images?</span></span>
<span data-ttu-id="69f18-119">Podczas tworzenia, kompilowania i uruchamiania konteneryzowanych aplikacji, mamy różnych priorytetach.</span><span class="sxs-lookup"><span data-stu-id="69f18-119">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="69f18-120">**Programowanie:** skupiono się priorytetu na szybko iterować zmiany i możliwość debugowania zmiany.</span><span class="sxs-lookup"><span data-stu-id="69f18-120">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="69f18-121">Rozmiar obrazu nie jest ważne, a nie można wprowadzić zmiany do kodu i szybkie wyświetlenie?</span><span class="sxs-lookup"><span data-stu-id="69f18-121">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="69f18-122">**Kompilacja:** ten obraz zawiera wszystko, co jest potrzebne do kompilowania aplikacji, która obejmuje kompilator i inne zależności, aby zoptymalizować pliki binarne.</span><span class="sxs-lookup"><span data-stu-id="69f18-122">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="69f18-123">Możesz użyć obrazu kompilacji umożliwia tworzenie zasobów, które można umieścić w środowisku produkcyjnym obraz.</span><span class="sxs-lookup"><span data-stu-id="69f18-123">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="69f18-124">Obraz kompilacji mogą być wykorzystane w celu zapewnienia ciągłej integracji, lub w środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="69f18-124">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="69f18-125">Takie podejście umożliwia agenta kompilacji skompilować i utworzyć aplikację (wszystkie wymagane zależności) w przypadku obrazu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="69f18-125">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="69f18-126">Agenta kompilacji, wystarczy wiedzieć, jak uruchomić tego obrazu platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="69f18-126">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="69f18-127">**Produkcyjne:** jak szybko możesz wdrożyć i uruchomić obraz?</span><span class="sxs-lookup"><span data-stu-id="69f18-127">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="69f18-128">Ten obraz jest mała, więc zoptymalizowane pod kątem wydajności sieci hostów platformy Docker z rejestru platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="69f18-128">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="69f18-129">Zawartość jest gotowa do uruchomienia, umożliwiając krótsze czasy docker, uruchom do przetwarzania wyników.</span><span class="sxs-lookup"><span data-stu-id="69f18-129">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="69f18-130">Kompilacja kodu dynamicznej nie jest potrzebna w modelu platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="69f18-130">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="69f18-131">Zawartość, które można umieścić w ten obraz będzie ograniczona do plików binarnych i zawartość wymaganą do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="69f18-131">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="69f18-132">Na przykład `dotnet publish` dane wyjściowe zawierają:</span><span class="sxs-lookup"><span data-stu-id="69f18-132">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="69f18-133">skompilowane pliki binarne</span><span class="sxs-lookup"><span data-stu-id="69f18-133">the compiled binaries</span></span>
    * <span data-ttu-id="69f18-134">pliki .js i CSS</span><span class="sxs-lookup"><span data-stu-id="69f18-134">.js and .css files</span></span>


<span data-ttu-id="69f18-135">Powód, aby uwzględnić `dotnet publish` danych wyjściowych polecenia w obrazie produkcji jest zapewnienie jego rozmiar do minimum.</span><span class="sxs-lookup"><span data-stu-id="69f18-135">The reason to include the `dotnet publish` command output in your production image is to keep its size to a minimum.</span></span>

<span data-ttu-id="69f18-136">Niektóre obrazy platformy .NET Core Udostępnij warstwy między różnych znaczników, więc pobieranie najnowszych tag jest stosunkowo lekkie procesu.</span><span class="sxs-lookup"><span data-stu-id="69f18-136">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="69f18-137">Jeśli masz już starszą wersję na komputerze, ta architektura zmniejsza wymagana ilość miejsca na dysku.</span><span class="sxs-lookup"><span data-stu-id="69f18-137">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="69f18-138">Korzystając z wielu aplikacji obrazów wspólnych na tym samym komputerze, pamięci jest współużytkowana przez obrazów wspólnych.</span><span class="sxs-lookup"><span data-stu-id="69f18-138">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="69f18-139">Obrazy musi być taka sama, do udostępnienia.</span><span class="sxs-lookup"><span data-stu-id="69f18-139">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="69f18-140">Różnice między obrazu platformy docker</span><span class="sxs-lookup"><span data-stu-id="69f18-140">Docker image variations</span></span>

<span data-ttu-id="69f18-141">Aby osiągnąć powyższe cele, firma Microsoft zapewnia wariantów obraz w ramach [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="69f18-141">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="69f18-142">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) Ten obraz zawiera zestaw .NET Core SDK, co obejmuje .NET Core i narzędzia wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="69f18-142">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="69f18-143">Ten obraz mapuje **scenariusz tworzenia**.</span><span class="sxs-lookup"><span data-stu-id="69f18-143">This image maps to the **development scenario**.</span></span> <span data-ttu-id="69f18-144">Możesz użyć tego obrazu lokalny rozwój, debugowanie i testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="69f18-144">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="69f18-145">Ten obraz może również służyć do Twojej **kompilacji** scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="69f18-145">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="69f18-146">Za pomocą `microsoft/dotnet:sdk` zawsze zawiera najnowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="69f18-146">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="69f18-147">Jeśli nie wiesz o Twoje potrzeby, chcesz użyć `microsoft/dotnet:<version>-sdk` obrazu.</span><span class="sxs-lookup"><span data-stu-id="69f18-147">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="69f18-148">Jako obraz "de facto", został zaprojektowany tak, ma być używany jako throw away kontenera instalacji kodu źródłowego i uruchamianie kontenera, aby uruchomić aplikację, a jako obraz podstawowy, tworzyć innych obrazów z.</span><span class="sxs-lookup"><span data-stu-id="69f18-148">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="69f18-149">`microsoft/dotnet:<version>-runtime`: Ten obraz zawiera .NET Core (środowisko uruchomieniowe i biblioteki) i jest zoptymalizowany pod kątem uruchamiania aplikacji .NET Core **produkcji**.</span><span class="sxs-lookup"><span data-stu-id="69f18-149">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="69f18-150">Alternatywne obrazów</span><span class="sxs-lookup"><span data-stu-id="69f18-150">Alternative images</span></span>

<span data-ttu-id="69f18-151">Oprócz zoptymalizowane scenariusze programowania, kompilacji i produkcji oferujemy dodatkowe obrazy:</span><span class="sxs-lookup"><span data-stu-id="69f18-151">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="69f18-152">`microsoft/dotnet:<version>-runtime-deps`**Deps środowiska uruchomieniowego** obraz zawiera system operacyjny, ze wszystkimi natywnych zależności wymagane przez platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="69f18-152">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="69f18-153">Ten obraz dotyczy [aplikacje samodzielne](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="69f18-153">This image is for [self-contained applications](../deploying/index.md).</span></span>

<span data-ttu-id="69f18-154">Najnowsze wersje każdego wariantu:</span><span class="sxs-lookup"><span data-stu-id="69f18-154">Latest versions of each variant:</span></span>

* <span data-ttu-id="69f18-155">`microsoft/dotnet` lub `microsoft/dotnet:latest` (alias obrazu zestawu SDK)</span><span class="sxs-lookup"><span data-stu-id="69f18-155">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="69f18-156">Przykłady, aby zapoznać się z</span><span class="sxs-lookup"><span data-stu-id="69f18-156">Samples to explore</span></span>

* <span data-ttu-id="69f18-157">[W tym przykładzie platformy Docker programu ASP.NET Core](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) przedstawiono najlepsze praktyki wzorzec do tworzenia obrazów platformy Docker dla platformy ASP.NET Core z aplikacji w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="69f18-157">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="69f18-158">Przykład współdziała z kontenerów systemów Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="69f18-158">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="69f18-159">Docker w programie .NET Core w przykładzie pokazano wzorzec najlepsze praktyki dla [tworzenie obrazów platformy Docker dla aplikacji platformy .NET Core w środowisku produkcyjnym.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)</span><span class="sxs-lookup"><span data-stu-id="69f18-159">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)</span></span>

## <a name="forward-the-request-scheme-and-original-ip-address"></a><span data-ttu-id="69f18-160">Przesyła schemat żądania i oryginalnego adresu IP</span><span class="sxs-lookup"><span data-stu-id="69f18-160">Forward the request scheme and original IP address</span></span>

<span data-ttu-id="69f18-161">Serwery proxy, moduły równoważenia obciążenia i innych urządzeniach sieciowych często zasłaniać informacje o żądaniu przed osiągnięciem przez nią konteneryzowaną aplikację:</span><span class="sxs-lookup"><span data-stu-id="69f18-161">Proxy servers, load balancers, and other network appliances often obscure information about a request before it reaches the containerized app:</span></span>

* <span data-ttu-id="69f18-162">Gdy żądania HTTPS są przekazywane za pośrednictwem protokołu HTTP, oryginalnym schematem (HTTPS) zostaną utracone i muszą być przekazywane w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="69f18-162">When HTTPS requests are proxied over HTTP, the original scheme (HTTPS) is lost and must be forwarded in a header.</span></span>
* <span data-ttu-id="69f18-163">Ponieważ aplikacja odbiera żądanie z serwera proxy i jej wartość true, źródła w Internecie lub w sieci firmowej, oryginalnego adresu IP klienta, również muszą być przekazywane w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="69f18-163">Because an app receives a request from the proxy and not its true source on the Internet or corporate network, the original client IP address must also be forwarded in a header.</span></span>

<span data-ttu-id="69f18-164">Te informacje mogą być ważne przetwarzanie żądań, na przykład w przekierowania, uwierzytelnianie, generowanie konsolidacji, ocena zasad i geolokalizacja klienta.</span><span class="sxs-lookup"><span data-stu-id="69f18-164">This information may be important in request processing, for example in redirects, authentication, link generation, policy evaluation, and client geolocation.</span></span>

<span data-ttu-id="69f18-165">Do przekazywania schemat i oryginalnego adresu IP do konteneryzowanych aplikacji platformy ASP.NET Core, użyj przekazywane oprogramowania pośredniczącego nagłówków.</span><span class="sxs-lookup"><span data-stu-id="69f18-165">To forward the scheme and original IP address to a containerized ASP.NET Core app, use Forwarded Headers Middleware.</span></span> <span data-ttu-id="69f18-166">Aby uzyskać więcej informacji, zobacz [Konfigurowanie platformy ASP.NET Core pracować z serwerów proxy i moduły równoważenia obciążenia](/aspnet/core/host-and-deploy/proxy-load-balancer).</span><span class="sxs-lookup"><span data-stu-id="69f18-166">For more information, see [Configure ASP.NET Core to work with proxy servers and load balancers](/aspnet/core/host-and-deploy/proxy-load-balancer).</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="69f18-167">Twoja pierwsza aplikacja platformy ASP.NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="69f18-167">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="69f18-168">W tym samouczku umożliwia korzystanie z aplikacji przykładowej platformy ASP.NET Core Docker dla aplikacji, którą chcemy, aby przekształcać.</span><span class="sxs-lookup"><span data-stu-id="69f18-168">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="69f18-169">Ta przykładowa aplikacja platformy ASP.NET Core Docker przedstawiono najlepsze praktyki wzorzec do tworzenia obrazów platformy Docker dla platformy ASP.NET Core z aplikacji w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="69f18-169">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="69f18-170">Przykład współdziała z kontenerów systemów Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="69f18-170">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="69f18-171">Przykładowy plik Dockerfile tworzy obraz platformy Docker aplikacji dla platformy ASP.NET Core na podstawie obrazu podstawowego platformy Docker programu ASP.NET Core środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="69f18-171">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="69f18-172">Używa ona [wieloetapowych platformy Docker, tworzenie funkcji](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) do:</span><span class="sxs-lookup"><span data-stu-id="69f18-172">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="69f18-173">stworzyć próbkę w kontenerze, w oparciu o **większych** obraz podstawowy platformy Docker programu ASP.NET Core kompilacji</span><span class="sxs-lookup"><span data-stu-id="69f18-173">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="69f18-174">kopiuje wynik końcowy kompilacji do obrazu platformy Docker, na podstawie **mniejszych** obrazu podstawowego środowiska uruchomieniowego programu ASP.NET Core platformy Docker</span><span class="sxs-lookup"><span data-stu-id="69f18-174">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!NOTE]
> <span data-ttu-id="69f18-175">Obraz kompilacji zawiera wymagane narzędzia do kompilowania aplikacji, a nie obraz środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="69f18-175">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="69f18-176">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="69f18-176">Prerequisites</span></span>

<span data-ttu-id="69f18-177">Aby skompilować i uruchomić, należy zainstalować następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="69f18-177">To build and run, install the following items:</span></span>

#### <a name="net-core-21-sdk"></a><span data-ttu-id="69f18-178">.NET core 2.1 SDK</span><span class="sxs-lookup"><span data-stu-id="69f18-178">.NET Core 2.1 SDK</span></span>

* <span data-ttu-id="69f18-179">Zainstaluj [platformy .NET Core SDK 2.1](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="69f18-179">Install [.NET Core SDK 2.1](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="69f18-180">Wybrany edytor kodu, należy zainstalować, jeśli jeszcze go.</span><span class="sxs-lookup"><span data-stu-id="69f18-180">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="69f18-181">Należy zainstalować Edytor kodu?</span><span class="sxs-lookup"><span data-stu-id="69f18-181">Need to install a code editor?</span></span> <span data-ttu-id="69f18-182">Spróbuj [programu Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="69f18-182">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="69f18-183">Instalowanie klienta platformy Docker</span><span class="sxs-lookup"><span data-stu-id="69f18-183">Installing Docker Client</span></span>

<span data-ttu-id="69f18-184">Zainstaluj [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) lub nowszego klienta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="69f18-184">Install [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="69f18-185">Klient platformy Docker można zainstalować w:</span><span class="sxs-lookup"><span data-stu-id="69f18-185">The Docker client can be installed in:</span></span>

* <span data-ttu-id="69f18-186">Dystrybucje systemu Linux</span><span class="sxs-lookup"><span data-stu-id="69f18-186">Linux distributions</span></span>

   * [<span data-ttu-id="69f18-187">CentOS</span><span class="sxs-lookup"><span data-stu-id="69f18-187">CentOS</span></span>](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [<span data-ttu-id="69f18-188">Debian</span><span class="sxs-lookup"><span data-stu-id="69f18-188">Debian</span></span>](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [<span data-ttu-id="69f18-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="69f18-189">Fedora</span></span>](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [<span data-ttu-id="69f18-190">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="69f18-190">Ubuntu</span></span>](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [<span data-ttu-id="69f18-191">macOS</span><span class="sxs-lookup"><span data-stu-id="69f18-191">macOS</span></span>](https://docs.docker.com/docker-for-mac/install/)

* <span data-ttu-id="69f18-192">[Windows](https://docs.docker.com/docker-for-windows/install/).</span><span class="sxs-lookup"><span data-stu-id="69f18-192">[Windows](https://docs.docker.com/docker-for-windows/install/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="69f18-193">Instalowanie usługi Git do repozytorium przykładów</span><span class="sxs-lookup"><span data-stu-id="69f18-193">Installing Git for sample repository</span></span>

* <span data-ttu-id="69f18-194">Zainstaluj [git](https://git-scm.com/download) Jeśli chcesz sklonować repozytorium.</span><span class="sxs-lookup"><span data-stu-id="69f18-194">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="69f18-195">Wprowadzenie do przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="69f18-195">Getting the sample application</span></span>

<span data-ttu-id="69f18-196">Najprostszym sposobem uzyskania próbki jest przez Sklonowanie [repozytorium Docker w programie .NET Core](https://github.com/dotnet/dotnet-docker) przy użyciu narzędzia git, przy użyciu następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="69f18-196">The easiest way to get the sample is by cloning the [.NET Core Docker repository](https://github.com/dotnet/dotnet-docker) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker
```

<span data-ttu-id="69f18-197">Można również pobrać repozytorium (jest to mała) w formie pliku zip z repozytorium Docker w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="69f18-197">You can also download the repository (it is small) as a zip from the .NET Core Docker repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="69f18-198">Lokalne uruchamianie aplikacji platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="69f18-198">Run the ASP.NET app locally</span></span>

<span data-ttu-id="69f18-199">Dla punktu odniesienia zanim będziemy konteneryzowanie aplikacji, najpierw uruchom aplikację lokalnie.</span><span class="sxs-lookup"><span data-stu-id="69f18-199">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="69f18-200">Można tworzyć i uruchom aplikację lokalnie, za pomocą zestawu .NET Core 2.1 SDK przy użyciu następujących poleceń (wskazówkach przyjęto założenie, folderze głównym repozytorium):</span><span class="sxs-lookup"><span data-stu-id="69f18-200">You can build and run the application locally with the .NET Core 2.1 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located
cd aspnetapp // project scope

dotnet run
```

<span data-ttu-id="69f18-201">Po uruchomieniu aplikacji, odwiedź stronę **http://localhost:5000** w przeglądarce sieci web.</span><span class="sxs-lookup"><span data-stu-id="69f18-201">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="69f18-202">Kompilowanie i uruchamianie przykładu z platformy Docker dla kontenerów systemu Linux</span><span class="sxs-lookup"><span data-stu-id="69f18-202">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="69f18-203">Można tworzyć i uruchom aplikację przykładową na platformie Docker przy użyciu kontenerów systemu Linux przy użyciu następujących poleceń (wskazówkach przyjęto założenie, folderze głównym repozytorium):</span><span class="sxs-lookup"><span data-stu-id="69f18-203">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> <span data-ttu-id="69f18-204">`docker run` "-P" argument mapowania portu 5000 na komputerze lokalnym do portu 80 w kontenerze (formularz mapowania portów jest `host:container`).</span><span class="sxs-lookup"><span data-stu-id="69f18-204">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="69f18-205">Aby uzyskać więcej informacji, zobacz [platformy docker, uruchom](https://docs.docker.com/engine/reference/commandline/exec/) odwołania dotyczące parametrów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="69f18-205">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="69f18-206">Po uruchomieniu aplikacji, odwiedź stronę **http://localhost:5000** w przeglądarce sieci web.</span><span class="sxs-lookup"><span data-stu-id="69f18-206">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="69f18-207">Kompilowanie i uruchamianie przykładu z kontenerów platformy Docker for Windows</span><span class="sxs-lookup"><span data-stu-id="69f18-207">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="69f18-208">Można tworzyć i uruchom aplikację przykładową na platformie Docker przy użyciu kontenerów Windows za pomocą następujących poleceń (wskazówkach przyjęto założenie, folderze głównym repozytorium):</span><span class="sxs-lookup"><span data-stu-id="69f18-208">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="69f18-209">Musisz przejść do **adres IP kontenera** (w przeciwieństwie do `http://localhost`) w przeglądarce bezpośrednio podczas korzystania z kontenerów Windows.</span><span class="sxs-lookup"><span data-stu-id="69f18-209">You must navigate to the **container IP address** (as opposed to `http://localhost`) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="69f18-210">Można uzyskać adresu IP kontenera wykonując następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="69f18-210">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="69f18-211">Otwórz innego wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="69f18-211">Open up another command prompt.</span></span>
* <span data-ttu-id="69f18-212">Uruchom `docker ps` Aby wyświetlić uruchomione kontenery.</span><span class="sxs-lookup"><span data-stu-id="69f18-212">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="69f18-213">Kontener "aspnetcore_sample" powinny być dostępne.</span><span class="sxs-lookup"><span data-stu-id="69f18-213">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="69f18-214">Uruchom `docker exec aspnetcore_sample ipconfig`.</span><span class="sxs-lookup"><span data-stu-id="69f18-214">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="69f18-215">Skopiuj adres IP kontenera, a następnie wklej w przeglądarce (na przykład 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="69f18-215">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!NOTE]
> <span data-ttu-id="69f18-216">Docker exec obsługuje identyfikujące kontenery przy użyciu nazwy lub wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="69f18-216">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="69f18-217">Nazwa (aspnetcore_sample) jest używana w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="69f18-217">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="69f18-218">Zobacz poniższy przykład sposobu uzyskania adresu IP działający kontener Windows.</span><span class="sxs-lookup"><span data-stu-id="69f18-218">See the following example of how to get the IP address of a running Windows container.</span></span>

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!NOTE]
> <span data-ttu-id="69f18-219">Docker exec działa nowego polecenia w uruchomionego kontenera.</span><span class="sxs-lookup"><span data-stu-id="69f18-219">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="69f18-220">Aby uzyskać więcej informacji, zobacz [odwołania exec docker](https://docs.docker.com/engine/reference/commandline/exec/) dotyczące parametrów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="69f18-220">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="69f18-221">Służy do tworzenia aplikacji, która jest gotowa do wdrożenia w środowisku produkcyjnym lokalnie przy użyciu [publikowania dotnet](../tools/dotnet-publish.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="69f18-221">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c Release -o published
```

> [!NOTE]
> <span data-ttu-id="69f18-222">- C argument wersji kompilacji aplikacji w trybie wydania (wartość domyślna to tryb debugowania).</span><span class="sxs-lookup"><span data-stu-id="69f18-222">The -c Release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="69f18-223">Aby uzyskać więcej informacji, zobacz [dotnet Uruchom odwołanie](../tools/dotnet-run.md) dotyczące parametrów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="69f18-223">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="69f18-224">Aplikację można uruchomić na **Windows** przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="69f18-224">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="69f18-225">Aplikację można uruchomić na **Linux** lub **macOS** przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="69f18-225">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="69f18-226">Obrazy platformy docker, używane w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="69f18-226">Docker Images used in this sample</span></span>

<span data-ttu-id="69f18-227">Następujące obrazy platformy Docker są używane w tym przykładowego pliku dockerfile.</span><span class="sxs-lookup"><span data-stu-id="69f18-227">The following Docker images are used in this sample's dockerfile.</span></span>

* `microsoft/dotnet:2.1-sdk`
* `microsoft/dotnet:2.1-aspnetcore-runtime`

<span data-ttu-id="69f18-228">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="69f18-228">Congratulations!</span></span> <span data-ttu-id="69f18-229">masz tylko:</span><span class="sxs-lookup"><span data-stu-id="69f18-229">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="69f18-230">Przedstawia informacje na temat obrazów platformy Docker programu Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="69f18-230">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="69f18-231">Otrzymano przykładową aplikację w celu Dockerize platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="69f18-231">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="69f18-232">Lokalnie uruchomiono przykładową aplikację platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="69f18-232">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="69f18-233">Wbudowane i uruchomiono przykład za pomocą platformy Docker dla kontenerów systemu Linux</span><span class="sxs-lookup"><span data-stu-id="69f18-233">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="69f18-234">Wbudowane i uruchomiono przykład za pomocą kontenerów platformy Docker for Windows</span><span class="sxs-lookup"><span data-stu-id="69f18-234">Built and ran the sample with Docker for Windows containers</span></span>

<span data-ttu-id="69f18-235">**Następne kroki**</span><span class="sxs-lookup"><span data-stu-id="69f18-235">**Next Steps**</span></span>

<span data-ttu-id="69f18-236">Poniżej przedstawiono niektóre kolejne kroki, które należy wykonać:</span><span class="sxs-lookup"><span data-stu-id="69f18-236">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="69f18-237">Praca z narzędzia Docker programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="69f18-237">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="69f18-238">Wdrażanie obrazów platformy Docker z rejestru kontenerów platformy Azure w usłudze Azure Container Instances</span><span class="sxs-lookup"><span data-stu-id="69f18-238">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="69f18-239">Debugowanie za pomocą programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="69f18-239">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="69f18-240">Praktycznym doświadczeniu z programem Visual Studio dla komputerów Mac, kontenerów i kod bez użycia serwera w chmurze</span><span class="sxs-lookup"><span data-stu-id="69f18-240">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="69f18-241">Wprowadzenie do platformy Docker i programu Visual Studio dla komputerów Mac laboratorium</span><span class="sxs-lookup"><span data-stu-id="69f18-241">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> <span data-ttu-id="69f18-242">Jeśli nie masz subskrypcji platformy Azure, [Zarejestruj się dzisiaj](https://azure.microsoft.com/free/?b=16.48) bezpłatne konto 30-dniowej i Odbierz 200 USD środków na korzystanie z platformy Azure możesz wypróbować dowolną kombinację usług platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="69f18-242">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
