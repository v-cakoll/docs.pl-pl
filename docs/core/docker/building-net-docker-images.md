---
title: Tworzenie obrazy usługi Docker .NET Core
description: Opis obrazy usługi Docker i .NET Core
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d26bd102d30c48785196322b9631e568a5002135
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697277"
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="bd99f-103">Tworzenie aplikacji programu .NET Core obrazy usługi Docker</span><span class="sxs-lookup"><span data-stu-id="bd99f-103">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="bd99f-104">W tym samouczku możemy skupić się na używanie .NET Core w Docker.</span><span class="sxs-lookup"><span data-stu-id="bd99f-104">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="bd99f-105">Najpierw możemy Poznaj różne obrazy Docker oferowane i przechowywane przez firmę Microsoft i przypadki użycia.</span><span class="sxs-lookup"><span data-stu-id="bd99f-105">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="bd99f-106">Firma Microsoft następnie Dowiedz się, jak utworzyć i dockerize aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd99f-106">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="bd99f-107">W trakcie tego samouczka dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="bd99f-107">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="bd99f-108">Więcej informacji o obrazach systemu Microsoft .NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="bd99f-108">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="bd99f-109">Pobierz przykładową aplikację Dockerize platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bd99f-109">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="bd99f-110">Uruchom przykładową aplikację ASP.NET lokalnie</span><span class="sxs-lookup"><span data-stu-id="bd99f-110">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="bd99f-111">Tworzenie i uruchamianie przykładu z rozwiązaniem Docker z kontenerów systemu Linux</span><span class="sxs-lookup"><span data-stu-id="bd99f-111">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="bd99f-112">Tworzenie i uruchamianie przykładu z kontenerami Docker dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bd99f-112">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="bd99f-113">Optymalizacja obrazów docker</span><span class="sxs-lookup"><span data-stu-id="bd99f-113">Docker Image Optimizations</span></span>

<span data-ttu-id="bd99f-114">Tworząc obrazy usługi Docker dla deweloperów, firma Microsoft skupia się na trzech głównych scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="bd99f-114">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="bd99f-115">Obrazy używane do opracowywania aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd99f-115">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="bd99f-116">Obrazy używane do tworzenia aplikacji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd99f-116">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="bd99f-117">Obrazy używane do uruchamiania aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd99f-117">Images used to run .NET Core apps</span></span>

<span data-ttu-id="bd99f-118">Dlaczego trzy obrazy?</span><span class="sxs-lookup"><span data-stu-id="bd99f-118">Why three images?</span></span>
<span data-ttu-id="bd99f-119">Podczas tworzenia, tworzenie i uruchamianie aplikacji konteneryzowanych, mamy różnych priorytetów.</span><span class="sxs-lookup"><span data-stu-id="bd99f-119">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="bd99f-120">**Programowanie:** skupiono się priorytet na szybko przejść zmiany i możliwość zmiany debugowania.</span><span class="sxs-lookup"><span data-stu-id="bd99f-120">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="bd99f-121">Rozmiar obrazu nie jest równie ważne, a nie można wprowadzić zmiany w kodzie i szybkie wyświetlenie?</span><span class="sxs-lookup"><span data-stu-id="bd99f-121">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="bd99f-122">**Kompilacja:** ten obraz zawiera wszystko, co jest potrzebne do skompilowania aplikacji, która obejmuje kompilator i innych zależności, aby zoptymalizować plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="bd99f-122">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="bd99f-123">Obraz kompilacji umożliwia tworzenie zasobów, które zostanie umieszczony w obrazie produkcji.</span><span class="sxs-lookup"><span data-stu-id="bd99f-123">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="bd99f-124">Obraz kompilacji będzie służyć do ciągłej integracji lub w środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bd99f-124">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="bd99f-125">Takie podejście umożliwia agenta kompilacji skompilować i utworzyć aplikację (z wymaganych zależności) w przypadku obrazu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bd99f-125">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="bd99f-126">Agenta kompilacji musi znać tylko sposób uruchamiania tego obrazu Docker.</span><span class="sxs-lookup"><span data-stu-id="bd99f-126">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="bd99f-127">**Produkcja:** tempa można wdrożyć i uruchomić obrazu?</span><span class="sxs-lookup"><span data-stu-id="bd99f-127">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="bd99f-128">Ten obraz jest mały, więc jest zoptymalizowana wydajność sieci z rejestru Docker na hostach Docker.</span><span class="sxs-lookup"><span data-stu-id="bd99f-128">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="bd99f-129">Zawartość jest gotowy do uruchomienia, włączanie o najszybszym czasie z Docker do przetwarzania wyników.</span><span class="sxs-lookup"><span data-stu-id="bd99f-129">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="bd99f-130">Kompilacja kodu dynamicznej nie jest wymagana w modelu Docker.</span><span class="sxs-lookup"><span data-stu-id="bd99f-130">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="bd99f-131">Zawartość, którą należy zaznaczyć ten obraz będzie ograniczony do plików binarnych i treści potrzebne do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bd99f-131">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="bd99f-132">Na przykład `dotnet publish` dane wyjściowe zawierają:</span><span class="sxs-lookup"><span data-stu-id="bd99f-132">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="bd99f-133">skompilowane pliki binarne</span><span class="sxs-lookup"><span data-stu-id="bd99f-133">the compiled binaries</span></span>
    * <span data-ttu-id="bd99f-134">pliki js i CSS</span><span class="sxs-lookup"><span data-stu-id="bd99f-134">.js and .css files</span></span>


<span data-ttu-id="bd99f-135">Powód, aby uwzględnić `dotnet publish` danych wyjściowych polecenia w obrazie produkcji jest zachowanie jego "rozmiar do minimum.</span><span class="sxs-lookup"><span data-stu-id="bd99f-135">The reason to include the `dotnet publish` command output in your production image is to keep its' size to a minimum.</span></span>

<span data-ttu-id="bd99f-136">Niektóre obrazy .NET Core Udostępnianie warstw między tagami różnych tak pobieranie najnowszych tag jest stosunkowo lekkie procesu.</span><span class="sxs-lookup"><span data-stu-id="bd99f-136">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="bd99f-137">Jeśli już masz starszą wersję na komputerze, to architektura zmniejsza ilość miejsca na dysku wymagana.</span><span class="sxs-lookup"><span data-stu-id="bd99f-137">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="bd99f-138">Korzystając z wielu aplikacji wspólnej obrazów na tym samym komputerze, pamięci jest udostępniana między wspólnej obrazów.</span><span class="sxs-lookup"><span data-stu-id="bd99f-138">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="bd99f-139">Obrazy muszą być takie same, do udostępnienia.</span><span class="sxs-lookup"><span data-stu-id="bd99f-139">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="bd99f-140">Zmiany obrazu docker</span><span class="sxs-lookup"><span data-stu-id="bd99f-140">Docker image variations</span></span>

<span data-ttu-id="bd99f-141">Aby osiągnąć powyższe cele, firma Microsoft udostępnia wariantów obrazu w obszarze [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="bd99f-141">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="bd99f-142">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) Ten obraz zawiera .NET Core SDK, w tym oprogramowanie .NET Core i narzędzia wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="bd99f-142">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="bd99f-143">Ten obraz mapy do **rozwojowych**.</span><span class="sxs-lookup"><span data-stu-id="bd99f-143">This image maps to the **development scenario**.</span></span> <span data-ttu-id="bd99f-144">Skorzystaj z tego obrazu dla rozwoju lokalnych, debugowania i testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="bd99f-144">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="bd99f-145">Ten obraz może także służyć do Twojej **kompilacji** scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="bd99f-145">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="bd99f-146">Przy użyciu `microsoft/dotnet:sdk` zawsze zawiera najnowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="bd99f-146">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="bd99f-147">Jeśli nie wiesz o Twoje potrzeby, chcesz użyć `microsoft/dotnet:<version>-sdk` obrazu.</span><span class="sxs-lookup"><span data-stu-id="bd99f-147">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="bd99f-148">Jako "faktyczne" obrazu zostało zaprojektowane do użycia jako throw nieobecności kontenera (kodu źródłowego instalacji i rozpocząć kontener, aby uruchomić aplikację), a jako obrazu podstawowego, aby utworzyć inne obrazy z.</span><span class="sxs-lookup"><span data-stu-id="bd99f-148">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="bd99f-149">`microsoft/dotnet:<version>-runtime`: Ten obraz zawiera .NET Core (środowisko uruchomieniowe i biblioteki) i jest zoptymalizowana pod kątem uruchamiania aplikacji .NET Core **produkcji**.</span><span class="sxs-lookup"><span data-stu-id="bd99f-149">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="bd99f-150">Alternatywne obrazów</span><span class="sxs-lookup"><span data-stu-id="bd99f-150">Alternative images</span></span>

<span data-ttu-id="bd99f-151">Oprócz zoptymalizowane scenariusze programowania, kompilacji i produkcji firma Microsoft udostępnia dodatkowe obrazy:</span><span class="sxs-lookup"><span data-stu-id="bd99f-151">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="bd99f-152">`microsoft/dotnet:<version>-runtime-deps`: **Deps środowiska uruchomieniowego** obraz zawiera system operacyjny ze wszystkimi zależnościami macierzystego, wymagane przez oprogramowanie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd99f-152">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="bd99f-153">Ten obraz dotyczy [niezależne aplikacji](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="bd99f-153">This image is for [self-contained applications](../deploying/index.md).</span></span>

<span data-ttu-id="bd99f-154">Najnowsze wersje każdego wariantu:</span><span class="sxs-lookup"><span data-stu-id="bd99f-154">Latest versions of each variant:</span></span>

* <span data-ttu-id="bd99f-155">`microsoft/dotnet` lub `microsoft/dotnet:latest` (alias obrazu zestawu SDK)</span><span class="sxs-lookup"><span data-stu-id="bd99f-155">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="bd99f-156">Przykłady do eksplorowania</span><span class="sxs-lookup"><span data-stu-id="bd99f-156">Samples to explore</span></span>

* <span data-ttu-id="bd99f-157">[W tym przykładzie platformy ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) pokazuje wzorzec najlepszych rozwiązań tworzenia obrazy usługi Docker dla platformy ASP.NET Core aplikacji w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="bd99f-157">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="bd99f-158">Przykład współdziała z kontenerów zarówno systemu Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="bd99f-158">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="bd99f-159">W tym przykładzie .NET Core Docker pokazuje wzorzec najlepsze praktyki dla [tworzenia obrazów Docker dla aplikacji .NET Core w środowisku produkcyjnym.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="bd99f-159">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="bd99f-160">Pierwszej aplikacji platformy ASP.NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="bd99f-160">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="bd99f-161">W tym samouczku umożliwia korzystanie z platformy ASP.NET Core Docker przykładowych aplikacji dla aplikacji, którą chcemy udostępnić dockerize.</span><span class="sxs-lookup"><span data-stu-id="bd99f-161">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="bd99f-162">Ta przykładowa aplikacja platformy ASP.NET Core Docker pokazuje wzorzec najlepszych rozwiązań tworzenia obrazy usługi Docker dla platformy ASP.NET Core aplikacji w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="bd99f-162">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="bd99f-163">Przykład współdziała z kontenerów zarówno systemu Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="bd99f-163">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="bd99f-164">Przykładowy plik Dockerfile tworzy obraz Docker aplikacji platformy ASP.NET Core, na podstawie obrazu platformy ASP.NET Core środowiska uruchomieniowego Docker.</span><span class="sxs-lookup"><span data-stu-id="bd99f-164">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="bd99f-165">Używa [Docker wieloetapowym kompilacji funkcji](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) do:</span><span class="sxs-lookup"><span data-stu-id="bd99f-165">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="bd99f-166">utworzyć przykład w kontenerze oparciu **większych** obrazu podstawowego platformy ASP.NET Core kompilacji Docker</span><span class="sxs-lookup"><span data-stu-id="bd99f-166">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="bd99f-167">kopiuje wynik końcowy kompilacji do obrazu platformy Docker na podstawie **mniejszych** obrazu podstawowego środowiska wykonawczego programu ASP.NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="bd99f-167">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!NOTE]
> <span data-ttu-id="bd99f-168">Obraz kompilacji zawiera wymagane narzędzia do tworzenia aplikacji, a nie w obrazie środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="bd99f-168">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="bd99f-169">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="bd99f-169">Prerequisites</span></span>

<span data-ttu-id="bd99f-170">Aby skompilować i uruchomić, należy zainstalować następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="bd99f-170">To build and run, install the following items:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="bd99f-171">.NET core 2.0 SDK</span><span class="sxs-lookup"><span data-stu-id="bd99f-171">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="bd99f-172">Zainstaluj [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="bd99f-172">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="bd99f-173">Jeśli nie jest jeszcze, należy zainstalować w edytorze kodu ulubionych.</span><span class="sxs-lookup"><span data-stu-id="bd99f-173">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="bd99f-174">Należy zainstalować Edytor kodu?</span><span class="sxs-lookup"><span data-stu-id="bd99f-174">Need to install a code editor?</span></span> <span data-ttu-id="bd99f-175">Spróbuj [programu Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="bd99f-175">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="bd99f-176">Instalowanie klienta Docker</span><span class="sxs-lookup"><span data-stu-id="bd99f-176">Installing Docker Client</span></span>

<span data-ttu-id="bd99f-177">Zainstaluj [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) lub nowszego klienta Docker.</span><span class="sxs-lookup"><span data-stu-id="bd99f-177">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="bd99f-178">Klient Docker można zainstalować w:</span><span class="sxs-lookup"><span data-stu-id="bd99f-178">The Docker client can be installed in:</span></span>

* <span data-ttu-id="bd99f-179">Dystrybucje systemu Linux</span><span class="sxs-lookup"><span data-stu-id="bd99f-179">Linux distributions</span></span>

   * [<span data-ttu-id="bd99f-180">CentOS</span><span class="sxs-lookup"><span data-stu-id="bd99f-180">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="bd99f-181">Debian</span><span class="sxs-lookup"><span data-stu-id="bd99f-181">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="bd99f-182">Fedora</span><span class="sxs-lookup"><span data-stu-id="bd99f-182">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="bd99f-183">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="bd99f-183">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="bd99f-184">macOS</span><span class="sxs-lookup"><span data-stu-id="bd99f-184">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="bd99f-185">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="bd99f-185">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="bd99f-186">Instalowanie narzędzia Git do repozytorium przykładowej</span><span class="sxs-lookup"><span data-stu-id="bd99f-186">Installing Git for sample repository</span></span>

* <span data-ttu-id="bd99f-187">Zainstaluj [git](https://git-scm.com/download) Jeśli chcesz sklonować repozytorium.</span><span class="sxs-lookup"><span data-stu-id="bd99f-187">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="bd99f-188">Pobieranie przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="bd99f-188">Getting the sample application</span></span>

<span data-ttu-id="bd99f-189">Najprostszym sposobem uzyskania próbki jest w klonowania [przykłady repozytorium](https://github.com/dotnet/dotnet-docker-samples) za pomocą narzędzia git, korzystając z następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="bd99f-189">The easiest way to get the sample is by cloning the [samples repository](https://github.com/dotnet/dotnet-docker-samples) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

<span data-ttu-id="bd99f-190">Możesz również pobrać repozytorium (jest mała) jako zip z repozytorium przykłady .NET Core Docker.</span><span class="sxs-lookup"><span data-stu-id="bd99f-190">You can also download the repository (it is small) as a zip from the .NET Core Docker samples repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="bd99f-191">Lokalne uruchamianie aplikacji platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bd99f-191">Run the ASP.NET app locally</span></span>

<span data-ttu-id="bd99f-192">Jako punkt odniesienia przed możemy containerize aplikacji, najpierw uruchom aplikację lokalnie.</span><span class="sxs-lookup"><span data-stu-id="bd99f-192">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="bd99f-193">Możesz skompilować i uruchomić aplikację lokalnie .NET SDK 2.0 Core za pomocą następujących poleceń (zgodnie z instrukcjami przyjmowane jest, folderze głównym repozytorium):</span><span class="sxs-lookup"><span data-stu-id="bd99f-193">You can build and run the application locally with the .NET Core 2.0 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
dotnet run
```

<span data-ttu-id="bd99f-194">Po uruchomieniu aplikacji, odwiedź stronę **http://localhost:5000** w przeglądarce sieci web.</span><span class="sxs-lookup"><span data-stu-id="bd99f-194">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="bd99f-195">Tworzenie i uruchamianie przykładu z rozwiązaniem Docker z kontenerów systemu Linux</span><span class="sxs-lookup"><span data-stu-id="bd99f-195">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="bd99f-196">Możesz skompilować i uruchomić przykładowy w Docker przy użyciu kontenerów systemu Linux przy użyciu następujących poleceń (zgodnie z instrukcjami przyjmowane jest, folderze głównym repozytorium):</span><span class="sxs-lookup"><span data-stu-id="bd99f-196">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> <span data-ttu-id="bd99f-197">`docker run` "-P" argument mapy port 5000 na komputerze lokalnym do portu 80 w kontenerze (formularz mapowania portów jest `host:container`).</span><span class="sxs-lookup"><span data-stu-id="bd99f-197">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="bd99f-198">Aby uzyskać więcej informacji, zobacz [docker Uruchom](https://docs.docker.com/engine/reference/commandline/exec/) odwołania dotyczące parametrów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bd99f-198">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="bd99f-199">Po uruchomieniu aplikacji, odwiedź stronę **http://localhost:5000** w przeglądarce sieci web.</span><span class="sxs-lookup"><span data-stu-id="bd99f-199">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="bd99f-200">Tworzenie i uruchamianie przykładu z kontenerami Docker dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bd99f-200">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="bd99f-201">Możesz skompilować i uruchomić przykładowy w Docker przy użyciu kontenery systemu Windows za pomocą następujących poleceń (zgodnie z instrukcjami przyjmowane jest, folderze głównym repozytorium):</span><span class="sxs-lookup"><span data-stu-id="bd99f-201">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="bd99f-202">Musisz przejść do **adres IP kontenera** (w przeciwieństwie do http://localhost) w przeglądarce bezpośrednio po użyciu kontenery systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bd99f-202">You must navigate to the **container IP address** (as opposed to http://localhost) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="bd99f-203">Możesz uzyskać adres IP z kontenera następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bd99f-203">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="bd99f-204">Otwórz innego wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bd99f-204">Open up another command prompt.</span></span>
* <span data-ttu-id="bd99f-205">Uruchom `docker ps` wyświetlić uruchomionych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="bd99f-205">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="bd99f-206">Kontener "aspnetcore_sample" powinny być dostępne.</span><span class="sxs-lookup"><span data-stu-id="bd99f-206">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="bd99f-207">Run `docker exec aspnetcore_sample ipconfig`.</span><span class="sxs-lookup"><span data-stu-id="bd99f-207">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="bd99f-208">Skopiuj adres IP kontenera i Wklej w przeglądarce (na przykład 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="bd99f-208">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!NOTE]
> <span data-ttu-id="bd99f-209">Docker exec obsługuje identyfikację kontenery o nazwie lub wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="bd99f-209">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="bd99f-210">Nazwa (aspnetcore_sample) jest używana w naszym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bd99f-210">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="bd99f-211">Zobacz poniższy przykład sposobu uzyskania adresu IP uruchomionych kontenera systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bd99f-211">See the following example of how to get the IP address of a running Windows container.</span></span>

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
> <span data-ttu-id="bd99f-212">Docker exec uruchamia nowe polecenie w kontenerze uruchomione.</span><span class="sxs-lookup"><span data-stu-id="bd99f-212">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="bd99f-213">Aby uzyskać więcej informacji, zobacz [odwołania exec docker](https://docs.docker.com/engine/reference/commandline/exec/) na parametry wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bd99f-213">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="bd99f-214">Służy do tworzenia aplikacji, która jest gotowe do wdrożenia w środowisku produkcyjnym lokalnie za pomocą [publikowania dotnet](../tools/dotnet-publish.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="bd99f-214">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c Release -o published
```

> [!NOTE]
> <span data-ttu-id="bd99f-215">- C argument wersji kompilacji aplikacji w trybie przygotowania do wydania (wartość domyślna to tryb debugowania).</span><span class="sxs-lookup"><span data-stu-id="bd99f-215">The -c Release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="bd99f-216">Aby uzyskać więcej informacji, zobacz [dotnet Uruchom odwołanie](../tools/dotnet-run.md) na parametry wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bd99f-216">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="bd99f-217">Aplikację można uruchomić na **Windows** przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="bd99f-217">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="bd99f-218">Aplikację można uruchomić na **Linux** lub **macOS** przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="bd99f-218">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="bd99f-219">Używane w tym przykładzie obrazy usługi docker</span><span class="sxs-lookup"><span data-stu-id="bd99f-219">Docker Images used in this sample</span></span>

<span data-ttu-id="bd99f-220">Na poniższych ilustracjach Docker są używane w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="bd99f-220">The following Docker images are used in this sample</span></span>

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

<span data-ttu-id="bd99f-221">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="bd99f-221">Congratulations!</span></span> <span data-ttu-id="bd99f-222">masz tylko:</span><span class="sxs-lookup"><span data-stu-id="bd99f-222">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="bd99f-223">Podstawowe informacje o obrazach systemu Microsoft .NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="bd99f-223">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="bd99f-224">Otrzymano Dockerize przykładowej aplikacji platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bd99f-224">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="bd99f-225">Uruchomiono lokalnie przykładową aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bd99f-225">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="bd99f-226">Wbudowane i uruchomiono próbki z rozwiązaniem Docker z kontenerów systemu Linux</span><span class="sxs-lookup"><span data-stu-id="bd99f-226">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="bd99f-227">Wbudowane i uruchomiono próbki z kontenerów Docker dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bd99f-227">Built and ran the sample with Docker for Windows containers</span></span>


<span data-ttu-id="bd99f-228">**Następne kroki**</span><span class="sxs-lookup"><span data-stu-id="bd99f-228">**Next Steps**</span></span>

<span data-ttu-id="bd99f-229">Poniżej przedstawiono niektóre czynności, które można wykonać:</span><span class="sxs-lookup"><span data-stu-id="bd99f-229">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="bd99f-230">Praca z narzędzia Docker programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bd99f-230">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="bd99f-231">Wdrażanie obrazów Docker z rejestru kontenera platformy Azure do wystąpień kontenera platformy Azure</span><span class="sxs-lookup"><span data-stu-id="bd99f-231">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="bd99f-232">Profilowanie kodu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bd99f-232">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="bd99f-233">Wprowadzenie ręce na z programem Visual Studio for Mac, kontenery i niekorzystającą kodu w chmurze</span><span class="sxs-lookup"><span data-stu-id="bd99f-233">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="bd99f-234">Pierwsze kroki z Docker i Visual Studio for Mac laboratorium</span><span class="sxs-lookup"><span data-stu-id="bd99f-234">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> <span data-ttu-id="bd99f-235">Jeśli nie masz subskrypcji platformy Azure, [Zarejestruj się już dziś](https://azure.microsoft.com/free/?b=16.48) bezpłatnej 30-dniowe konto i 200 USD interweniować środków Azure wypróbowanie dowolną kombinację usługami Azure.</span><span class="sxs-lookup"><span data-stu-id="bd99f-235">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
