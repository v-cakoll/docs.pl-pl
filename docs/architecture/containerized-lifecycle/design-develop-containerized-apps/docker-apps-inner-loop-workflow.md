---
title: Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker
description: Dowiedz się, przepływ pracy "pętla wewnętrzna" do tworzenia aplikacji platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: bce047bd5ba75f9ef652a294ff6a15656fc5ac34
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738409"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="31180-103">Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="31180-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="31180-104">Przed wyzwoleniem przepływu pracy pętli zewnętrznej obejmującej cały cykl DevOps wszystko zaczyna się na komputerze każdego dewelopera, kodowanie samej aplikacji, przy użyciu preferowanych języków lub platform i testowanie go lokalnie (Rysunek 4-21).</span><span class="sxs-lookup"><span data-stu-id="31180-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="31180-105">Ale w każdym przypadku będziesz miał ważny punkt wspólny, bez względu na język, ramy lub platformy, które wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="31180-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="31180-106">W tym określonym przepływie pracy zawsze tworzysz i testujesz kontenery platformy Docker, ale lokalnie.</span><span class="sxs-lookup"><span data-stu-id="31180-106">In this specific workflow, you're always developing and testing Docker containers, but locally.</span></span>

![Diagram przedstawiający koncepcję środowiska deweloperskiego pętli wewnętrznej.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

<span data-ttu-id="31180-108">**Rysunek 4-21**.</span><span class="sxs-lookup"><span data-stu-id="31180-108">**Figure 4-21**.</span></span> <span data-ttu-id="31180-109">Kontekst rozwoju pętli wewnętrznej</span><span class="sxs-lookup"><span data-stu-id="31180-109">Inner-loop development context</span></span>

<span data-ttu-id="31180-110">Kontener lub wystąpienie obrazu platformy Docker będzie zawierać następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="31180-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="31180-111">Wybór systemu operacyjnego (na przykład dystrybucja Linuksa lub Windows)</span><span class="sxs-lookup"><span data-stu-id="31180-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="31180-112">Pliki dodane przez dewelopera (na przykład pliki binarne aplikacji)</span><span class="sxs-lookup"><span data-stu-id="31180-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="31180-113">Konfiguracja (na przykład ustawienia środowiska i zależności)</span><span class="sxs-lookup"><span data-stu-id="31180-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="31180-114">Instrukcje dotyczące procesów uruchamianych przez platformę Docker</span><span class="sxs-lookup"><span data-stu-id="31180-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="31180-115">Można skonfigurować przepływ pracy tworzenia pętli wewnętrznej, który wykorzystuje docker jako proces (opisane w następnej sekcji).</span><span class="sxs-lookup"><span data-stu-id="31180-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="31180-116">Należy wziąć pod uwagę, że początkowe kroki konfigurowania środowiska nie są uwzględniane, ponieważ wystarczy to zrobić tylko raz.</span><span class="sxs-lookup"><span data-stu-id="31180-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="31180-117">Tworzenie pojedynczej aplikacji w kontenerze platformy Docker przy użyciu kodu programu Visual Studio i interfejsu wiersza polecenia platformy Docker</span><span class="sxs-lookup"><span data-stu-id="31180-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="31180-118">Aplikacje są wykonane z własnych usług oraz dodatkowych bibliotek (zależności).</span><span class="sxs-lookup"><span data-stu-id="31180-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="31180-119">Rysunek 4-22 przedstawia podstawowe kroki, które zwykle należy wykonać podczas tworzenia aplikacji platformy Docker, a następnie szczegółowe opisy każdego kroku.</span><span class="sxs-lookup"><span data-stu-id="31180-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Diagram przedstawiający siedem kroków, które należy wykonać do utworzenia aplikacji konteneryzowanej.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

<span data-ttu-id="31180-121">**Rysunek 4-22**.</span><span class="sxs-lookup"><span data-stu-id="31180-121">**Figure 4-22**.</span></span> <span data-ttu-id="31180-122">Przepływ pracy wysokiego poziomu dla cyklu życia konteneryzowanych aplikacji platformy Docker przy użyciu interfejsu wiersza polecenia platformy Docker</span><span class="sxs-lookup"><span data-stu-id="31180-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="31180-123">Krok 1: Rozpocznij kodowanie w programie Visual Studio Code i utwórz początkową linię bazową aplikacji/usługi</span><span class="sxs-lookup"><span data-stu-id="31180-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="31180-124">Sposób tworzenia aplikacji jest podobny do sposobu, w jaki to zrobić bez platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="31180-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="31180-125">Różnica polega na tym, że podczas tworzenia wdrażasz i testujesz aplikację lub usługi uruchomione w kontenerach platformy Docker umieszczonych w środowisku lokalnym (takim jak maszyna wirtualna z systemem Linux lub system Windows).</span><span class="sxs-lookup"><span data-stu-id="31180-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="31180-126">**Konfigurowanie środowiska lokalnego**</span><span class="sxs-lookup"><span data-stu-id="31180-126">**Setting up your local environment**</span></span>

<span data-ttu-id="31180-127">Dzięki najnowszym wersjom platformy Docker dla komputerów Mac i Windows tworzenie aplikacji platformy Docker jest łatwiejsze niż kiedykolwiek, a konfiguracja jest prosta.</span><span class="sxs-lookup"><span data-stu-id="31180-127">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="31180-128">Aby uzyskać instrukcje dotyczące konfigurowania platformy <https://docs.docker.com/docker-for-windows/>Docker dla systemu Windows, przejdź do pliku .</span><span class="sxs-lookup"><span data-stu-id="31180-128">For instructions on setting up Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
><span data-ttu-id="31180-129">Aby uzyskać instrukcje dotyczące konfigurowania platformy <https://docs.docker.com/docker-for-mac/>Docker dla komputerów Mac, przejdź do pliku .</span><span class="sxs-lookup"><span data-stu-id="31180-129">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="31180-130">Ponadto potrzebny jest edytor kodu, dzięki czemu można faktycznie tworzyć aplikacji podczas korzystania z interfejsu wiersza polecenia platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="31180-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="31180-131">Firma Microsoft udostępnia program Visual Studio Code, który jest lekkim edytorem kodu obsługiwanym w [systemach](https://code.visualstudio.com/docs/languages/overview) Windows, Linux i macOS, i zapewnia intellisense obsługę wielu języków (JavaScript, .NET, Go, Java, Ruby, Python i większość nowoczesnych języków), [debugowanie,](https://code.visualstudio.com/Docs/editor/debugging) [integrację z obsługą Git](https://code.visualstudio.com/Docs/editor/versioncontrol) i [rozszerzenia .](https://code.visualstudio.com/docs/extensions/overview)</span><span class="sxs-lookup"><span data-stu-id="31180-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Windows, Linux, and macOS, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="31180-132">Ten edytor doskonale pasuje do programistów macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="31180-132">This editor is a great fit for macOS and Linux developers.</span></span> <span data-ttu-id="31180-133">W systemie Windows można również użyć programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="31180-133">In Windows, you can also use Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="31180-134">Aby uzyskać instrukcje dotyczące instalowania programu Visual Studio Code <https://code.visualstudio.com/docs/setup/setup-overview/>dla systemów Windows, Linux lub macOS, przejdź do pliku .</span><span class="sxs-lookup"><span data-stu-id="31180-134">For instructions on installing Visual Studio Code for Windows, Linux, or macOS, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="31180-135">Aby uzyskać instrukcje dotyczące konfigurowania platformy <https://docs.docker.com/docker-for-mac/>Docker dla komputerów Mac, przejdź do pliku .</span><span class="sxs-lookup"><span data-stu-id="31180-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="31180-136">Można pracować z docker CLI i napisać kod przy użyciu dowolnego edytora kodu, ale `Dockerfile` przy `docker-compose.yml` użyciu programu Visual Studio Code z rozszerzeniem platformy Docker ułatwia tworzenie i pliki w obszarze roboczym.</span><span class="sxs-lookup"><span data-stu-id="31180-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="31180-137">Można również uruchamiać zadania i skrypty z ide kodu programu Visual Studio do wykonywania poleceń platformy Docker przy użyciu interfejsu wiersza polecenia platformy Docker pod spodem.</span><span class="sxs-lookup"><span data-stu-id="31180-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="31180-138">Rozszerzenie platformy Docker dla programu VS Code zawiera następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="31180-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="31180-139">Automatyczne `Dockerfile` `docker-compose.yml` generowanie plików i ich generowanie</span><span class="sxs-lookup"><span data-stu-id="31180-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="31180-140">Wskazówki dotyczące wyróżniania i `docker-compose.yml` `Dockerfile` aktywowania składni dla plików i plików</span><span class="sxs-lookup"><span data-stu-id="31180-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="31180-141">IntelliSense (uzupełnienia) `Dockerfile` `docker-compose.yml` dla i plików</span><span class="sxs-lookup"><span data-stu-id="31180-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="31180-142">Linting (błędy i ostrzeżenia) dla `Dockerfile` plików</span><span class="sxs-lookup"><span data-stu-id="31180-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="31180-143">Integracja z paletą poleceń (F1) dla najpopularniejszych poleceń platformy Docker</span><span class="sxs-lookup"><span data-stu-id="31180-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="31180-144">Integracja z Eksploratorem do zarządzania obrazami i kontenerami</span><span class="sxs-lookup"><span data-stu-id="31180-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="31180-145">Wdrażanie obrazów z rejestrów kontenerów usługi DockerHub i azure do usługi Azure App Service</span><span class="sxs-lookup"><span data-stu-id="31180-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="31180-146">Aby zainstalować rozszerzenie platformy Docker, naciśnij klawisze `ext install`Ctrl+Shift+P, wpisz polecenie Zainstaluj rozszerzenie, aby wyświetlić listę rozszerzeń portalu Marketplace.</span><span class="sxs-lookup"><span data-stu-id="31180-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="31180-147">Następnie wpisz **dok.** aby filtrować wyniki, a następnie wybierz rozszerzenie Docker Support, jak pokazano na rysunku 4-23.</span><span class="sxs-lookup"><span data-stu-id="31180-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![Widok rozszerzenia platformy Docker dla programu VS Code.](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

<span data-ttu-id="31180-149">**Rysunek 4-23**.</span><span class="sxs-lookup"><span data-stu-id="31180-149">**Figure 4-23**.</span></span> <span data-ttu-id="31180-150">Instalowanie rozszerzenia platformy Docker w programie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="31180-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="31180-151">Krok 2: Tworzenie pliku dockerfile powiązanego z istniejącym obrazem (zwykły system operacyjny lub środowiska deweloperów, takie jak .NET Core, Node.js i Ruby)</span><span class="sxs-lookup"><span data-stu-id="31180-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="31180-152">Musisz na obraz `DockerFile` niestandardowy do zbudowannia i na kontener do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="31180-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="31180-153">Jeśli aplikacja składa się z jednej usługi niestandardowej, `DockerFile`potrzebujesz jednej .</span><span class="sxs-lookup"><span data-stu-id="31180-153">If your app is made up of a single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="31180-154">Ale jeśli aplikacja składa się z wielu usług (jak w architekturze `Dockerfile` mikrousług), trzeba będzie jeden na usługę.</span><span class="sxs-lookup"><span data-stu-id="31180-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="31180-155">Jest `DockerFile` często umieszczany w folderze głównym aplikacji lub usługi i zawiera wymagane polecenia, dzięki czemu program Docker wie, jak skonfigurować i uruchomić tę aplikację lub usługę.</span><span class="sxs-lookup"><span data-stu-id="31180-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="31180-156">Możesz utworzyć `DockerFile` i dodać go do projektu wraz z kodem (node.js, .NET Core itp.) lub, jeśli jesteś nowy w środowisku, zapoznaj się z następującą poradą.</span><span class="sxs-lookup"><span data-stu-id="31180-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="31180-157">Rozszerzenie platformy Docker służy do prowadzenia `Dockerfile` podczas `docker-compose.yml` korzystania z plików i plików związanych z kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="31180-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="31180-158">Ostatecznie prawdopodobnie napiszesz tego rodzaju pliki bez tego narzędzia, ale użycie rozszerzenia Platformy Docker jest dobrym punktem wyjścia, który przyspieszy krzywą uczenia się.</span><span class="sxs-lookup"><span data-stu-id="31180-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="31180-159">Na rysunku 4-24 można zobaczyć, jak plik docker-compose jest dodawany przy użyciu rozszerzenia platformy Docker dla kodu VS.</span><span class="sxs-lookup"><span data-stu-id="31180-159">In Figure 4-24, you can see how a docker-compose file is added by using the Docker Extension for VS Code.</span></span>

![Widok konsoli rozszerzenia platformy Docker dla programu VS Code.](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

<span data-ttu-id="31180-161">**Rysunek 4-24**.</span><span class="sxs-lookup"><span data-stu-id="31180-161">**Figure 4-24**.</span></span> <span data-ttu-id="31180-162">Pliki docker dodane za pomocą **polecenia Dodaj pliki platformy Docker do obszaru roboczego**</span><span class="sxs-lookup"><span data-stu-id="31180-162">Docker files added using the **Add Docker files to Workspace command**</span></span>

<span data-ttu-id="31180-163">Podczas dodawania pliku dockerfile należy określić, jaki bazowy obraz `FROM mcr.microsoft.com/dotnet/core/aspnet`platformy Docker będzie używany (np. przy użyciu ).</span><span class="sxs-lookup"><span data-stu-id="31180-163">When you add a DockerFile, you specify what base Docker image you'll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="31180-164">Zwykle tworzysz obraz niestandardowy na obrazie podstawowym, który można uzyskać z dowolnego oficjalnego repozytorium w [rejestrze Docker Hub](https://hub.docker.com/) (np. [obraz dla .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) lub obraz dla [node.js).](https://hub.docker.com/_/node/)</span><span class="sxs-lookup"><span data-stu-id="31180-164">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="31180-165">***Używanie istniejącego oficjalnego obrazu platformy Docker***</span><span class="sxs-lookup"><span data-stu-id="31180-165">***Use an existing official Docker image***</span></span>

<span data-ttu-id="31180-166">Korzystanie z oficjalnego repozytorium stosu języka z numerem wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym rozwoju, testowania i produkcji).</span><span class="sxs-lookup"><span data-stu-id="31180-166">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="31180-167">Poniżej przedstawiono przykładowy plik DockerFile dla kontenera .NET Core:</span><span class="sxs-lookup"><span data-stu-id="31180-167">The following is a sample DockerFile for a .NET Core container:</span></span>

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="31180-168">W tym przypadku obraz jest oparty na wersji 2.2 oficjalnego obrazu Core Docker ASP.NET (multi-arch `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`dla Linuksa i Windowsa), zgodnie z linią .</span><span class="sxs-lookup"><span data-stu-id="31180-168">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="31180-169">(Aby uzyskać więcej informacji na ten temat, zobacz [stronę ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) i stronę [.NET Core Docker Image).](https://hub.docker.com/_/microsoft-dotnet-core/)</span><span class="sxs-lookup"><span data-stu-id="31180-169">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="31180-170">W pliku DockerFile można również poinstruować program Docker, aby nasłuchiwać portu TCP, który będzie używany w czasie wykonywania (na przykład port 80).</span><span class="sxs-lookup"><span data-stu-id="31180-170">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80).</span></span>

<span data-ttu-id="31180-171">Można określić dodatkowe ustawienia konfiguracji w Dockerfile, w zależności od języka i struktury, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="31180-171">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="31180-172">Na przykład `ENTRYPOINT` wiersz `["dotnet", "MySingleContainerWebApp.dll"]` z informuje Docker, aby uruchomić aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="31180-172">For instance, the `ENTRYPOINT` line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="31180-173">Jeśli używasz SDK i .NET Core`dotnet CLI`CLI ( ) do tworzenia i uruchamiania aplikacji .NET, to ustawienie będzie inne.</span><span class="sxs-lookup"><span data-stu-id="31180-173">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="31180-174">Kluczowym punktem jest to, że linia ENTRYPOINT i inne ustawienia zależą od języka i platformy, którą wybierzesz dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="31180-174">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="31180-175">Aby uzyskać więcej informacji na temat tworzenia obrazów <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>platformy Docker dla aplikacji .NET Core, przejdź do pliku .</span><span class="sxs-lookup"><span data-stu-id="31180-175">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="31180-176">Aby dowiedzieć się więcej o <https://docs.docker.com/engine/tutorials/dockerimages/>tworzeniu własnych obrazów, przejdź do .</span><span class="sxs-lookup"><span data-stu-id="31180-176">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="31180-177">**Korzystanie z repozytoriów obrazów wielokołowych**</span><span class="sxs-lookup"><span data-stu-id="31180-177">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="31180-178">Pojedyncza nazwa obrazu w repozytorium może zawierać warianty platformy, takie jak obraz systemu Linux i obraz systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="31180-178">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="31180-179">Ta funkcja umożliwia dostawcom, takim jak Microsoft (twórcom obrazów podstawowych), tworzenie jednego repozytorium obejmującego wiele platform (czyli Linuksa i Windowsa).</span><span class="sxs-lookup"><span data-stu-id="31180-179">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="31180-180">Na przykład repozytorium [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) dostępne w rejestrze Docker Hub zapewnia obsługę systemów Linux i Windows Nano Server przy użyciu tej samej nazwy obrazu.</span><span class="sxs-lookup"><span data-stu-id="31180-180">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="31180-181">Ciągnięcie obrazu [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) z hosta systemu Windows ściąga wariant systemu Windows, podczas gdy ciągnięcie tej samej nazwy obrazu z hosta Linuksa ściąga wariant Linuksa.</span><span class="sxs-lookup"><span data-stu-id="31180-181">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="31180-182">***Tworzenie obrazu bazowego od podstaw***</span><span class="sxs-lookup"><span data-stu-id="31180-182">***Create your base image from scratch***</span></span>

<span data-ttu-id="31180-183">Można utworzyć własny obraz bazowy platformy Docker od podstaw, jak wyjaśniono w tym [artykule](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="31180-183">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="31180-184">Ten scenariusz prawdopodobnie nie jest najlepszy dla Ciebie, jeśli dopiero zaczynasz z platformą Docker, ale jeśli chcesz ustawić określone bity własnego obrazu podstawowego, możesz to zrobić.</span><span class="sxs-lookup"><span data-stu-id="31180-184">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="31180-185">Krok 3: Tworzenie niestandardowych obrazów platformy Docker osadzających w niej usługę</span><span class="sxs-lookup"><span data-stu-id="31180-185">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="31180-186">Dla każdej usługi niestandardowej, która obejmuje aplikację, musisz utworzyć powiązany obraz.</span><span class="sxs-lookup"><span data-stu-id="31180-186">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="31180-187">Jeśli aplikacja składa się z jednej usługi lub aplikacji internetowej, potrzebujesz tylko jednego obrazu.</span><span class="sxs-lookup"><span data-stu-id="31180-187">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="31180-188">Biorąc pod uwagę "przepływ pracy DevOps w pętli zewnętrznej", obrazy zostaną utworzone przez zautomatyzowany proces kompilacji za każdym razem, gdy wypchniesz kod źródłowy do repozytorium Git (ciągła integracja), więc obrazy zostaną utworzone w tym środowisku globalnym z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="31180-188">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="31180-189">Zanim jednak rozważymy przejście do tej trasy w pętli zewnętrznej, musimy upewnić się, że aplikacja platformy Docker działa poprawnie, aby nie wypychać kodu, który może nie działać poprawnie w systemie kontroli źródła (Git itp.).</span><span class="sxs-lookup"><span data-stu-id="31180-189">But before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="31180-190">W związku z tym każdy deweloper najpierw musi wykonać cały proces pętli wewnętrznej, aby przetestować lokalnie i kontynuować rozwój, dopóki nie chce wypchnąć pełną funkcję lub zmiany do systemu kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="31180-190">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="31180-191">Aby utworzyć obraz w środowisku lokalnym i przy użyciu DockerFile, można użyć polecenia kompilacji platformy docker, jak `docker-compose up --build` pokazano na rysunku 4-25 (można również uruchomić dla aplikacji składanych przez kilka kontenerów/usług).</span><span class="sxs-lookup"><span data-stu-id="31180-191">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-25 (you can also run `docker-compose up --build` for applications composed by several containers/services).</span></span>

![Zrzut ekranu przedstawiający dane wyjściowe konsoli polecenia kompilacji platformy docker.](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

<span data-ttu-id="31180-193">**Rysunek 4-25**.</span><span class="sxs-lookup"><span data-stu-id="31180-193">**Figure 4-25**.</span></span> <span data-ttu-id="31180-194">Uruchamianie kompilacji platformy docker</span><span class="sxs-lookup"><span data-stu-id="31180-194">Running docker build</span></span>

<span data-ttu-id="31180-195">Opcjonalnie zamiast uruchamiać bezpośrednio `docker build` z folderu projektu, najpierw można wygenerować folder z możliwością `dotnet publish` wdrożenia z `docker build`bibliotekami .NET potrzebnymi za pomocą polecenia uruchom, a następnie uruchomić program .</span><span class="sxs-lookup"><span data-stu-id="31180-195">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="31180-196">W tym przykładzie tworzy obraz `cesardl/netcore-webapi-microservice-docker:first` `:first` platformy Docker o nazwie ( jest tagiem, jak określona wersja).</span><span class="sxs-lookup"><span data-stu-id="31180-196">This example creates a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first` (`:first` is a tag, like a specific version).</span></span> <span data-ttu-id="31180-197">Można wykonać ten krok dla każdego obrazu niestandardowego, który należy utworzyć dla złożonej aplikacji platformy Docker z kilkoma kontenerami.</span><span class="sxs-lookup"><span data-stu-id="31180-197">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="31180-198">Istniejące obrazy można znaleźć w lokalnym repozytorium (komputerze deweloperskim) za pomocą polecenia obrazy platformy docker, jak pokazano na rysunku 4-26.</span><span class="sxs-lookup"><span data-stu-id="31180-198">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-26.</span></span>

![Wyjście konsoli z obrazów dokowane polecenia, pokazując istniejące obrazy.](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="31180-200">**Rysunek 4-26**.</span><span class="sxs-lookup"><span data-stu-id="31180-200">**Figure 4-26**.</span></span> <span data-ttu-id="31180-201">Wyświetlanie istniejących obrazów przy użyciu obrazów dokowych</span><span class="sxs-lookup"><span data-stu-id="31180-201">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="31180-202">Krok 4: Zdefiniuj swoje usługi w docker-compose.yml podczas tworzenia złożonej aplikacji platformy Docker z wieloma usługami</span><span class="sxs-lookup"><span data-stu-id="31180-202">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="31180-203">Za `docker-compose.yml` pomocą pliku można zdefiniować zestaw powiązanych usług, które mają być wdrożone jako złożona aplikacja z poleceniami wdrażania wyjaśnionymi w następnej sekcji kroku.</span><span class="sxs-lookup"><span data-stu-id="31180-203">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="31180-204">Utwórz ten plik w głównym lub głównym folderze rozwiązania; powinien mieć zawartość podobną do `docker-compose.yml` tej pokazanej w tym pliku:</span><span class="sxs-lookup"><span data-stu-id="31180-204">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

```yml
version: '3.4'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

<span data-ttu-id="31180-205">W tym konkretnym przypadku ten plik definiuje dwie usługi: usługę sieci web (usługę niestandardową) i usługę redis (popularną usługę pamięci podręcznej).</span><span class="sxs-lookup"><span data-stu-id="31180-205">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="31180-206">Każda usługa zostanie wdrożona jako kontener, więc musimy użyć konkretnego obrazu platformy Docker dla każdego.</span><span class="sxs-lookup"><span data-stu-id="31180-206">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="31180-207">W przypadku tej konkretnej usługi sieci web obraz będzie musiał wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="31180-207">For this particular web service, the image will need to do the following:</span></span>

- <span data-ttu-id="31180-208">Kompilacja z pliku DockerFile w bieżącym katalogu</span><span class="sxs-lookup"><span data-stu-id="31180-208">Build from the DockerFile in the current directory</span></span>

- <span data-ttu-id="31180-209">Prześlij odsłonięty port 80 na kontenerze do portu 81 na komputerze-hoście</span><span class="sxs-lookup"><span data-stu-id="31180-209">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

- <span data-ttu-id="31180-210">Zamontuj katalog projektu na hoście, aby /code w kontenerze, umożliwiając modyfikowanie kodu bez konieczności przebudowyowania obrazu</span><span class="sxs-lookup"><span data-stu-id="31180-210">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

- <span data-ttu-id="31180-211">Łączenie usługi sieci web z usługą redis</span><span class="sxs-lookup"><span data-stu-id="31180-211">Link the web service to the redis service</span></span>

<span data-ttu-id="31180-212">Usługa redis używa [najnowszego publicznego obrazu redis](https://hub.docker.com/_/redis/) pobranego z rejestru usługi Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="31180-212">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="31180-213">[redis](https://redis.io/) to popularny system pamięci podręcznej dla aplikacji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="31180-213">[redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="31180-214">Krok 5: Tworzenie i uruchamianie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="31180-214">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="31180-215">Jeśli aplikacja ma tylko jeden kontener, wystarczy go uruchomić, wdrażając go na hoście platformy Docker Host (VM lub serwer fizyczny).</span><span class="sxs-lookup"><span data-stu-id="31180-215">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="31180-216">Jeśli jednak aplikacja składa się z wielu usług, musisz *ją skomponować.*</span><span class="sxs-lookup"><span data-stu-id="31180-216">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="31180-217">Zobaczmy różne opcje.</span><span class="sxs-lookup"><span data-stu-id="31180-217">Let's see the different options.</span></span>

<span data-ttu-id="31180-218">***Opcja A: Uruchamianie pojedynczego kontenera lub usługi***</span><span class="sxs-lookup"><span data-stu-id="31180-218">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="31180-219">Obraz platformy Docker można uruchomić za pomocą polecenia uruchom docker, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="31180-219">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="31180-220">W przypadku tego konkretnego wdrożenia będziemy przekierowywać żądania wysyłane do portu 80 do portu wewnętrznego 5000.</span><span class="sxs-lookup"><span data-stu-id="31180-220">For this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="31180-221">Teraz aplikacja nasłuchuje na zewnętrznym porcie 80 na poziomie hosta.</span><span class="sxs-lookup"><span data-stu-id="31180-221">Now the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="31180-222">***Opcja B: Komponowanie i uruchamianie aplikacji z wieloma kontenerami***</span><span class="sxs-lookup"><span data-stu-id="31180-222">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="31180-223">W większości scenariuszy przedsiębiorstw aplikacja platformy Docker będzie składać się z wielu usług.</span><span class="sxs-lookup"><span data-stu-id="31180-223">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="31180-224">W takich przypadkach można `docker-compose up` uruchomić polecenie (Rysunek 4-27), które będzie używać pliku docker-compose.yml, który mógł zostać utworzony wcześniej.</span><span class="sxs-lookup"><span data-stu-id="31180-224">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="31180-225">Uruchomienie tego polecenia wdraża złożoną aplikację ze wszystkimi powiązanymi kontenerami.</span><span class="sxs-lookup"><span data-stu-id="31180-225">Running this command deploys a composed application with all of its related containers.</span></span>

![Wyjście konsoli z polecenia docker-compose up.](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

<span data-ttu-id="31180-227">**Rysunek 4-27**.</span><span class="sxs-lookup"><span data-stu-id="31180-227">**Figure 4-27**.</span></span> <span data-ttu-id="31180-228">Wyniki uruchamiania polecenia "docker-compose up"</span><span class="sxs-lookup"><span data-stu-id="31180-228">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="31180-229">Po uruchomieniu `docker-compose up`można wdrożyć aplikację i jej powiązanych kontenerów do hosta platformy Docker, jak pokazano na rysunku 4-28, w reprezentacji maszyny Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="31180-229">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![Maszyna wirtualna z aplikacjami z wieloma kontenerami.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="31180-231">**Rysunek 4-28**.</span><span class="sxs-lookup"><span data-stu-id="31180-231">**Figure 4-28**.</span></span> <span data-ttu-id="31180-232">Maszyna wirtualna z wdrożonymi kontenerami platformy Docker</span><span class="sxs-lookup"><span data-stu-id="31180-232">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="31180-233">Krok 6: Przetestuj aplikację platformy Docker (lokalnie, w lokalnej maszynie wirtualnej cd)</span><span class="sxs-lookup"><span data-stu-id="31180-233">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="31180-234">Ten krok będzie się różnić w zależności od tego, co robi aplikacja.</span><span class="sxs-lookup"><span data-stu-id="31180-234">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="31180-235">W prostym interfejsie API sieci Web .NET Core "Hello World" wdrożonym jako pojedynczy kontener lub usługa wystarczy uzyskać dostęp do usługi, udostępniając port TCP określony w pliku DockerFile.</span><span class="sxs-lookup"><span data-stu-id="31180-235">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="31180-236">Jeśli localhost nie jest włączony, aby przejść do usługi, znajdź adres IP komputera za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="31180-236">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

<span data-ttu-id="31180-237">Na hoście platformy Docker otwórz przeglądarkę i przejdź do tej witryny; powinien zostać wyświetlony aplikacji/usługi uruchomione, jak pokazano na rysunku 4-29.</span><span class="sxs-lookup"><span data-stu-id="31180-237">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Widok przeglądarki odpowiedzi z localhost/API/values.](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="31180-239">**Rysunek 4-29**.</span><span class="sxs-lookup"><span data-stu-id="31180-239">**Figure 4-29**.</span></span> <span data-ttu-id="31180-240">Testowanie aplikacji platformy Docker lokalnie przy użyciu localhost</span><span class="sxs-lookup"><span data-stu-id="31180-240">Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="31180-241">Należy pamiętać, że używa portu 80, ale wewnętrznie jest przekierowywany do portu 5000, `docker run`ponieważ tak został wdrożony z , jak wyjaśniono wcześniej.</span><span class="sxs-lookup"><span data-stu-id="31180-241">Note that it's using port 80, but internally it's being redirected to port 5000, because that's how it was deployed with `docker run`, as explained earlier.</span></span>

<span data-ttu-id="31180-242">Można to sprawdzić za pomocą CURL z terminala.</span><span class="sxs-lookup"><span data-stu-id="31180-242">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="31180-243">W instalacji platformy Docker w systemie Windows domyślny adres IP to 10.0.75.1, jak pokazano na rysunku 4-30.</span><span class="sxs-lookup"><span data-stu-id="31180-243">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-30.</span></span>

![Wyjście konsoli z http://10.0.75.1/API/values coraz z curl](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="31180-245">**Rysunek 4-30**.</span><span class="sxs-lookup"><span data-stu-id="31180-245">**Figure 4-30**.</span></span> <span data-ttu-id="31180-246">Testowanie aplikacji platformy Docker lokalnie przy użyciu CURL</span><span class="sxs-lookup"><span data-stu-id="31180-246">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="31180-247">**Debugowanie kontenera uruchomionego w programie Docker**</span><span class="sxs-lookup"><span data-stu-id="31180-247">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="31180-248">Visual Studio Code obsługuje debugowanie platformy Docker, jeśli używasz Node.js i innych platform, takich jak kontenery .NET Core.</span><span class="sxs-lookup"><span data-stu-id="31180-248">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="31180-249">Można również debugować kontenery .NET Core lub .NET Framework w programie Docker podczas korzystania z programu Visual Studio dla systemu Windows lub Mac, zgodnie z opisem w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="31180-249">You can also debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="31180-250">Aby dowiedzieć się więcej o debugowaniu kontenerów platformy Docker node.js, zobacz <https://blog.docker.com/2016/07/live-debugging-docker/> i <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span><span class="sxs-lookup"><span data-stu-id="31180-250">To learn more about debugging Node.js Docker containers, see <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="31180-251">[Poprzedni](docker-apps-development-environment.md)
>[następny](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="31180-251">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
