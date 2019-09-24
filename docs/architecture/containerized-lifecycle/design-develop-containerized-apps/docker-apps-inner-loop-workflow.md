---
title: Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker
description: Zapoznaj się z przepływem pracy "pętla wewnętrzna" na potrzeby opracowywania aplikacji platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 04e1b29e6a0cef89df05cc9124806c74a38b5249
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214351"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="4383d-103">Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="4383d-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="4383d-104">Przed wyzwoleniem przepływu pracy z pętlą zewnętrzną obejmującą cały cykl DevOps, wszystko to rozpocznie się na maszynie każdego dewelopera, kodowanie samej aplikacji przy użyciu preferowanych języków lub platform i przetestowanie go lokalnie (rysunek 4-21).</span><span class="sxs-lookup"><span data-stu-id="4383d-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="4383d-105">Jednak w każdym przypadku będziesz mieć ważny, niezależnie od tego, jaki język, struktura lub platformy są wybrane.</span><span class="sxs-lookup"><span data-stu-id="4383d-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="4383d-106">W tym konkretnym przepływie pracy są zawsze opracowywanie i testowanie kontenerów platformy Docker, ale lokalnie.</span><span class="sxs-lookup"><span data-stu-id="4383d-106">In this specific workflow, you're always developing and testing Docker containers, but locally.</span></span>

![Krok 1 — Code/Run/Debug](./media/image18.png)

<span data-ttu-id="4383d-108">**Rysunek 4-21**.</span><span class="sxs-lookup"><span data-stu-id="4383d-108">**Figure 4-21**.</span></span> <span data-ttu-id="4383d-109">Kontekst programowania pętli wewnętrznej</span><span class="sxs-lookup"><span data-stu-id="4383d-109">Inner-loop development context</span></span>

<span data-ttu-id="4383d-110">Kontener lub wystąpienie obrazu platformy Docker będzie zawierać następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="4383d-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="4383d-111">Wybór systemu operacyjnego (na przykład dystrybucja systemu Linux lub Windows)</span><span class="sxs-lookup"><span data-stu-id="4383d-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="4383d-112">Pliki dodane przez dewelopera (na przykład pliki binarne aplikacji)</span><span class="sxs-lookup"><span data-stu-id="4383d-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="4383d-113">Konfiguracja (na przykład ustawienia środowiska i zależności)</span><span class="sxs-lookup"><span data-stu-id="4383d-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="4383d-114">Instrukcje dotyczące procesów uruchamianych przez platformę Docker</span><span class="sxs-lookup"><span data-stu-id="4383d-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="4383d-115">Można skonfigurować przepływ pracy programowania w pętli wewnętrznej, który wykorzystuje platformę Docker jako proces (opisany w następnej sekcji).</span><span class="sxs-lookup"><span data-stu-id="4383d-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="4383d-116">Należy pamiętać, że wstępne kroki konfigurowania środowiska nie są uwzględniane, ponieważ wystarczy tylko raz.</span><span class="sxs-lookup"><span data-stu-id="4383d-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="4383d-117">Tworzenie pojedynczej aplikacji w kontenerze platformy Docker przy użyciu Visual Studio Code i interfejsu wiersza polecenia platformy Docker</span><span class="sxs-lookup"><span data-stu-id="4383d-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="4383d-118">Aplikacje składają się z własnych usług i dodatkowych bibliotek (zależności).</span><span class="sxs-lookup"><span data-stu-id="4383d-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="4383d-119">Na rysunku 4-22 przedstawiono podstawowe kroki, które zwykle trzeba wykonać podczas kompilowania aplikacji platformy Docker, a następnie szczegółowe opisy poszczególnych kroków.</span><span class="sxs-lookup"><span data-stu-id="4383d-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Przegląd przepływu pracy: Krok 1. kod, krok 2 — zapis wieloetapowe dockerfile, krok 3 — Tworzenie obrazów zdefiniowanych za pomocą wieloetapowe dockerfile, krok 4 — Definiowanie usług przy użyciu pliku platformy Docker, krok 5 — Uruchamianie kontenerów lub aplikacji składających się z kroku 6 — Testowanie aplikacji, krok 7 — wypychanie aby rozpocząć pętlę zewnętrzną (potoki ciągłej integracji/ciągłego wdrażania) lub Kontynuuj de veloping.](./media/image19.png)

<span data-ttu-id="4383d-121">**Rysunek 4-22**.</span><span class="sxs-lookup"><span data-stu-id="4383d-121">**Figure 4-22**.</span></span> <span data-ttu-id="4383d-122">Przepływ pracy wysokiego poziomu dla cyklu życia aplikacji kontenera platformy Docker przy użyciu interfejsu wiersza polecenia platformy Docker</span><span class="sxs-lookup"><span data-stu-id="4383d-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="4383d-123">Krok 1. Rozpocznij kodowanie w Visual Studio Code i Utwórz początkową aplikację/linię bazową usługi</span><span class="sxs-lookup"><span data-stu-id="4383d-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="4383d-124">Sposób tworzenia aplikacji jest podobny do sposobu, w jaki to zrobisz, bez dokowania.</span><span class="sxs-lookup"><span data-stu-id="4383d-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="4383d-125">Różnica polega na tym, że podczas tworzenia i testowania aplikacji lub usług działających w kontenerach platformy Docker umieszczonych w środowisku lokalnym (na przykład w przypadku maszyn wirtualnych z systemem Linux lub Windows).</span><span class="sxs-lookup"><span data-stu-id="4383d-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="4383d-126">**Konfigurowanie środowiska lokalnego**</span><span class="sxs-lookup"><span data-stu-id="4383d-126">**Setting up your local environment**</span></span>

<span data-ttu-id="4383d-127">Najnowsze wersje platformy Docker dla komputerów Mac i systemu Windows ułatwiają tworzenie aplikacji platformy Docker, a instalacja jest prosta.</span><span class="sxs-lookup"><span data-stu-id="4383d-127">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="4383d-128">Aby uzyskać instrukcje dotyczące konfigurowania Docker for Windows, przejdź do <https://docs.docker.com/docker-for-windows/>.</span><span class="sxs-lookup"><span data-stu-id="4383d-128">For instructions on setting up Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
><span data-ttu-id="4383d-129">Aby uzyskać instrukcje dotyczące konfigurowania platformy Docker dla komputerów Mac, <https://docs.docker.com/docker-for-mac/>przejdź do.</span><span class="sxs-lookup"><span data-stu-id="4383d-129">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="4383d-130">Ponadto potrzebny jest Edytor kodu, dzięki czemu można w rzeczywistości opracowywać aplikację przy użyciu interfejsu wiersza polecenia platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="4383d-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="4383d-131">Firma Microsoft udostępnia Visual Studio Code, który jest lekkim edytorem kodu obsługiwanym w systemach Mac, Windows i Linux oraz udostępnia technologię IntelliSense z [obsługą wielu języków](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, go, Java, Ruby, Python i większość nowoczesnych języków). [ Debugowanie](https://code.visualstudio.com/Docs/editor/debugging), [integracja z](https://code.visualstudio.com/Docs/editor/versioncontrol) [obsługą git i rozszerzeniami](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="4383d-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="4383d-132">Ten Edytor jest doskonałym rozwiązaniem dla deweloperów systemów Mac i Linux.</span><span class="sxs-lookup"><span data-stu-id="4383d-132">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="4383d-133">W systemie Windows można również użyć pełnej aplikacji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4383d-133">In Windows, you also can use the full Visual Studio application.</span></span>

> [!TIP]
> <span data-ttu-id="4383d-134">Aby uzyskać instrukcje dotyczące instalowania Visual Studio Code dla systemu Windows, Mac lub Linux, przejdź <https://code.visualstudio.com/docs/setup/setup-overview/>do.</span><span class="sxs-lookup"><span data-stu-id="4383d-134">For instructions on installing Visual Studio Code for Windows, Mac, or Linux, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="4383d-135">Aby uzyskać instrukcje dotyczące konfigurowania platformy Docker dla komputerów Mac, <https://docs.docker.com/docker-for-mac/>przejdź do.</span><span class="sxs-lookup"><span data-stu-id="4383d-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="4383d-136">Możesz współpracować z interfejsem wiersza polecenia platformy Docker i pisać kod przy użyciu dowolnego edytora kodu, ale używanie Visual Studio Code z rozszerzeniem Docker ułatwia tworzenie i `Dockerfile` `docker-compose.yml` opracowywanie plików w obszarze roboczym.</span><span class="sxs-lookup"><span data-stu-id="4383d-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="4383d-137">Możesz również uruchamiać zadania i skrypty z Visual Studio Code IDE, aby wykonywać polecenia platformy Docker przy użyciu interfejsu wiersza polecenia platformy Docker poniżej.</span><span class="sxs-lookup"><span data-stu-id="4383d-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="4383d-138">Rozszerzenie Docker dla VS Code zapewnia następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="4383d-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="4383d-139">Automatyczne `Dockerfile` i`docker-compose.yml` generowanie plików</span><span class="sxs-lookup"><span data-stu-id="4383d-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="4383d-140">Podświetlanie składni i wskazówki dotyczące kursora `docker-compose.yml` dla `Dockerfile` i plików</span><span class="sxs-lookup"><span data-stu-id="4383d-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="4383d-141">Technologia IntelliSense (uzupełnianie) `Dockerfile` dla `docker-compose.yml` plików i</span><span class="sxs-lookup"><span data-stu-id="4383d-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="4383d-142">Zaznaczanie błędów (błędy i ostrzeżenia) dla `Dockerfile` plików</span><span class="sxs-lookup"><span data-stu-id="4383d-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="4383d-143">Paleta poleceń (F1) dla najpopularniejszych poleceń platformy Docker</span><span class="sxs-lookup"><span data-stu-id="4383d-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="4383d-144">Integracja Eksploratora do zarządzania obrazami i kontenerami</span><span class="sxs-lookup"><span data-stu-id="4383d-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="4383d-145">Wdróż obrazy z DockerHub i rejestrów kontenerów platformy Azure, aby Azure App Service</span><span class="sxs-lookup"><span data-stu-id="4383d-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="4383d-146">Aby zainstalować rozszerzenie platformy Docker, naciśnij kombinację klawiszy Ctrl + Shift + `ext install`P, wpisz polecenie, a następnie uruchom rozszerzenie install, aby wyświetlić listę rozszerzeń portalu Marketplace.</span><span class="sxs-lookup"><span data-stu-id="4383d-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="4383d-147">Następnie wpisz **Docker** , aby przefiltrować wyniki, a następnie wybierz rozszerzenie obsługa platformy Docker, jak przedstawiono na rysunku 4-23.</span><span class="sxs-lookup"><span data-stu-id="4383d-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![Widok rozszerzenia Docker dla VS Code.](./media/image20.png)

<span data-ttu-id="4383d-149">**Rysunek 4-23**.</span><span class="sxs-lookup"><span data-stu-id="4383d-149">**Figure 4-23**.</span></span> <span data-ttu-id="4383d-150">Instalowanie rozszerzenia platformy Docker w Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4383d-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="4383d-151">Krok 2. Tworzenie pliku dockerfile związanych z istniejącym obrazem (zwykłym systemem operacyjnym lub środowiskami deweloperskimi, takimi jak .NET Core, Node. js i Ruby)</span><span class="sxs-lookup"><span data-stu-id="4383d-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="4383d-152">Musisz `DockerFile` utworzyć obraz niestandardowy do skompilowania i na kontener, który ma zostać wdrożony.</span><span class="sxs-lookup"><span data-stu-id="4383d-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="4383d-153">Jeśli Twoja aplikacja składa się z pojedynczej usługi niestandardowej, będziesz potrzebować jednego `DockerFile`z nich.</span><span class="sxs-lookup"><span data-stu-id="4383d-153">If your app is made up of a single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="4383d-154">Jeśli jednak aplikacja składa się z wielu usług (podobnie jak w przypadku architektury mikrousług), będzie potrzebna jedna `Dockerfile` na usługę.</span><span class="sxs-lookup"><span data-stu-id="4383d-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="4383d-155">`DockerFile` Jest to zwykle umieszczane w folderze głównym aplikacji lub usługi i zawiera wymagane polecenia, dzięki czemu platforma Docker wie, jak skonfigurować i uruchomić tę aplikację lub usługę.</span><span class="sxs-lookup"><span data-stu-id="4383d-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="4383d-156">Możesz utworzyć `DockerFile` i dodać go do projektu wraz z kodem (Node. js, .NET Core itp.) lub, jeśli jesteś nowym środowiskiem, zapoznaj się z poniższą wskazówką.</span><span class="sxs-lookup"><span data-stu-id="4383d-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="4383d-157">Możesz użyć rozszerzenia Docker, aby poprowadzić Cię podczas korzystania `Dockerfile` z `docker-compose.yml` plików i związanych z kontenerami platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="4383d-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="4383d-158">Na koniec prawdopodobnie napiszesz te rodzaje plików bez tego narzędzia, ale przy użyciu rozszerzenia Docker jest dobrym punktem wyjścia, który przyspiesza uczenie się.</span><span class="sxs-lookup"><span data-stu-id="4383d-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="4383d-159">Na rysunku 4-24 można zobaczyć, jak zostanie dodany plik do redagowania platformy Docker przy użyciu rozszerzenia Docker dla VS Code.</span><span class="sxs-lookup"><span data-stu-id="4383d-159">In Figure 4-24, you can see how a docker-compose file is added by using the Docker Extension for VS Code.</span></span>

![Widok konsoli rozszerzenia platformy Docker dla VS Code.](./media/image24.png)

<span data-ttu-id="4383d-161">**Rysunek 4-24**.</span><span class="sxs-lookup"><span data-stu-id="4383d-161">**Figure 4-24**.</span></span> <span data-ttu-id="4383d-162">Pliki platformy Docker dodane za pomocą **polecenia Dodaj pliki platformy Docker do obszaru roboczego**</span><span class="sxs-lookup"><span data-stu-id="4383d-162">Docker files added using the **Add Docker files to Workspace command**</span></span>

<span data-ttu-id="4383d-163">Po dodaniu pliku dockerfile należy określić, który podstawowy obraz platformy Docker będzie używany (na przykład za pomocą `FROM mcr.microsoft.com/dotnet/core/aspnet`programu).</span><span class="sxs-lookup"><span data-stu-id="4383d-163">When you add a DockerFile, you specify what base Docker image you’ll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="4383d-164">Zwykle utworzysz niestandardowy obraz na podstawie obrazu podstawowego, który można uzyskać z dowolnego oficjalnego repozytorium w [rejestrze usługi Docker Hub](https://hub.docker.com/) (na przykład [obrazu dla platformy .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) lub [dla środowiska Node. js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="4383d-164">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="4383d-165">***Użyj istniejącego oficjalnego obrazu platformy Docker***</span><span class="sxs-lookup"><span data-stu-id="4383d-165">***Use an existing official Docker image***</span></span>

<span data-ttu-id="4383d-166">Korzystanie z oficjalnego repozytorium stosu języka z numerem wersji zapewnia, że te same funkcje językowe są dostępne na wszystkich komputerach (w tym na etapie projektowania, testowania i produkcji).</span><span class="sxs-lookup"><span data-stu-id="4383d-166">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="4383d-167">Poniżej znajduje się przykład pliku dockerfile dla kontenera .NET Core:</span><span class="sxs-lookup"><span data-stu-id="4383d-167">The following is a sample DockerFile for a .NET Core container:</span></span>

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

<span data-ttu-id="4383d-168">W tym przypadku obraz jest oparty na wersji 2,2 ASP.NET Core oficjalnego obrazu platformy Docker (wiele rozwiązań dla systemów Linux i Windows), zgodnie z wierszem `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="4383d-168">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="4383d-169">(Aby uzyskać więcej informacji na temat tego tematu, zobacz stronę [ASP.NET Core Docker](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) i stronę [obrazu platformy Docker programu .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) ).</span><span class="sxs-lookup"><span data-stu-id="4383d-169">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="4383d-170">W pliku dockerfile można także nakazać platformie Docker nasłuchiwanie portu TCP, który będzie używany w czasie wykonywania (na przykład port 80).</span><span class="sxs-lookup"><span data-stu-id="4383d-170">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80).</span></span>

<span data-ttu-id="4383d-171">Możesz określić dodatkowe ustawienia konfiguracji w pliku dockerfile, w zależności od używanego języka i platformy.</span><span class="sxs-lookup"><span data-stu-id="4383d-171">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="4383d-172">Na przykład `ENTRYPOINT` wiersz z `["dotnet", "MySingleContainerWebApp.dll"]` poleceniem instruuje platformę Docker, aby uruchomić aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4383d-172">For instance, the `ENTRYPOINT` line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="4383d-173">Jeśli używasz zestawu SDK i interfejs wiersza polecenia platformy .NET Core (`dotnet CLI`) do kompilowania i uruchamiania aplikacji .NET, to ustawienie będzie inne.</span><span class="sxs-lookup"><span data-stu-id="4383d-173">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="4383d-174">Kluczowym punktem jest to, że wiersz punktu wejścia i inne ustawienia zależą od języka i platformy wybranej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4383d-174">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="4383d-175">Aby uzyskać więcej informacji na temat tworzenia obrazów platformy Docker dla aplikacji platformy .NET <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>Core, przejdź do.</span><span class="sxs-lookup"><span data-stu-id="4383d-175">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="4383d-176">Aby dowiedzieć się więcej na temat tworzenia własnych obrazów, <https://docs.docker.com/engine/tutorials/dockerimages/>przejdź do.</span><span class="sxs-lookup"><span data-stu-id="4383d-176">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="4383d-177">**Używanie repozytoriów obrazów wieloskładnikowych**</span><span class="sxs-lookup"><span data-stu-id="4383d-177">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="4383d-178">Nazwa pojedynczego obrazu w repozytorium może zawierać warianty platformy, takie jak obraz systemu Linux i obraz Windows.</span><span class="sxs-lookup"><span data-stu-id="4383d-178">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="4383d-179">Ta funkcja umożliwia dostawcom, takim jak firma Microsoft (twórcy obrazów podstawowych), tworzenie jednego repozytorium w celu pokrycia wielu platform (to jest Linux i Windows).</span><span class="sxs-lookup"><span data-stu-id="4383d-179">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="4383d-180">Na przykład repozytorium [dotnet/rdzeń/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) dostępne w rejestrze usługi Docker Hub zapewnia obsługę systemu Linux i Windows nano Server przy użyciu tej samej nazwy obrazu.</span><span class="sxs-lookup"><span data-stu-id="4383d-180">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="4383d-181">Ściąganie obrazu [dotnet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) z hosta z systemem Windows powoduje pobranie wariantu systemu Windows, podczas gdy ściąganie tej samej nazwy obrazu z hosta z systemem Linux jest ściągane.</span><span class="sxs-lookup"><span data-stu-id="4383d-181">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="4383d-182">***Tworzenie obrazu podstawowego od podstaw***</span><span class="sxs-lookup"><span data-stu-id="4383d-182">***Create your base image from scratch***</span></span>

<span data-ttu-id="4383d-183">Możesz utworzyć własny obraz podstawowy platformy Docker od podstaw, jak wyjaśniono w tym [artykule](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="4383d-183">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="4383d-184">Ten scenariusz prawdopodobnie nie jest najlepszym rozwiązaniem, jeśli właśnie zaczynasz pracę z platformą Docker, ale jeśli chcesz ustawić określone bity obrazu podstawowego, możesz to zrobić.</span><span class="sxs-lookup"><span data-stu-id="4383d-184">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="4383d-185">Krok 3. Tworzenie niestandardowych obrazów platformy Docker osadzania w niej usługi</span><span class="sxs-lookup"><span data-stu-id="4383d-185">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="4383d-186">Dla każdej usługi niestandardowej, która składa się z aplikacji, konieczne będzie utworzenie powiązanego obrazu.</span><span class="sxs-lookup"><span data-stu-id="4383d-186">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="4383d-187">Jeśli aplikacja składa się z pojedynczej usługi lub aplikacji sieci Web, będzie potrzebny tylko jeden obraz.</span><span class="sxs-lookup"><span data-stu-id="4383d-187">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="4383d-188">Podczas wzięcia pod uwagę "przepływu pracy DevOps pętla zewnętrzna" obrazy zostaną utworzone przez zautomatyzowany proces kompilacji po każdym wypchnięciu kodu źródłowego do repozytorium git (ciągłej integracji), dzięki czemu obrazy zostaną utworzone w tym środowisku globalnym z kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="4383d-188">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="4383d-189">Jednak przed rozważeniem przechodzenia do tej trasy z pętlą zewnętrzną musimy upewnić się, że aplikacja platformy Docker rzeczywiście działa prawidłowo, aby nie wypchnięcia kodu, który może nie działać prawidłowo w systemie kontroli źródła (git itp.).</span><span class="sxs-lookup"><span data-stu-id="4383d-189">But before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="4383d-190">W związku z tym każdy Deweloper musi najpierw wykonać cały proces pętli wewnętrznej, aby przetestować lokalnie i kontynuować programowanie do momentu, gdy chcą wypchnąć kompletną funkcję lub zmienić system kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="4383d-190">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="4383d-191">Aby utworzyć obraz w środowisku lokalnym i przy użyciu pliku dockerfile, można użyć polecenia Docker Build, jak pokazano na rysunku 4-25 (można również uruchamiać `docker-compose up --build` aplikacje składające się z kilku kontenerów/usług).</span><span class="sxs-lookup"><span data-stu-id="4383d-191">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-25 (you also can run `docker-compose up --build` for applications composed by several containers/services).</span></span>

![Dane wyjściowe konsoli dla kompilacji Docker-Zredaguj, pokazujące postęp pobierania obrazów.](./media/image25.png)

<span data-ttu-id="4383d-193">**Rysunek 4-25**.</span><span class="sxs-lookup"><span data-stu-id="4383d-193">**Figure 4-25**.</span></span> <span data-ttu-id="4383d-194">Uruchamianie kompilacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="4383d-194">Running docker build</span></span>

<span data-ttu-id="4383d-195">Opcjonalnie, zamiast bezpośrednio `docker build` z poziomu folderu projektu, można najpierw wygenerować folder do wdrożenia z bibliotekami platformy .NET wymaganymi przy użyciu polecenia Uruchom `dotnet publish` , a następnie uruchomić `docker build`polecenie.</span><span class="sxs-lookup"><span data-stu-id="4383d-195">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="4383d-196">W tym przykładzie tworzony jest obraz platformy Docker o `cesardl/netcore-webapi-microservice-docker:first` nazwie`:first` (jest to tag, taki jak określona wersja).</span><span class="sxs-lookup"><span data-stu-id="4383d-196">This example creates a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first` (`:first` is a tag, like a specific version).</span></span> <span data-ttu-id="4383d-197">Ten krok można wykonać dla każdego niestandardowego obrazu, który trzeba utworzyć dla złożonej aplikacji platformy Docker z kilkoma kontenerami.</span><span class="sxs-lookup"><span data-stu-id="4383d-197">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="4383d-198">Istniejące obrazy można znaleźć w lokalnym repozytorium (na komputerze deweloperskim) przy użyciu polecenia Docker images, jak pokazano na rysunku 4-26.</span><span class="sxs-lookup"><span data-stu-id="4383d-198">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-26.</span></span>

![Dane wyjściowe konsoli z obrazów platformy Docker, pokazujące istniejące obrazy.](./media/image26.png)

<span data-ttu-id="4383d-200">**Rysunek 4-26**.</span><span class="sxs-lookup"><span data-stu-id="4383d-200">**Figure 4-26**.</span></span> <span data-ttu-id="4383d-201">Wyświetlanie istniejących obrazów przy użyciu obrazów platformy Docker</span><span class="sxs-lookup"><span data-stu-id="4383d-201">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="4383d-202">Krok 4. Zdefiniuj usługi w Docker-Compose. yml podczas tworzenia złożonej aplikacji platformy Docker z wieloma usługami</span><span class="sxs-lookup"><span data-stu-id="4383d-202">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="4383d-203">Przy użyciu `docker-compose.yml` pliku można zdefiniować zestaw powiązanych usług, które mają zostać wdrożone jako aplikacja składająca się z poleceniami wdrażania wyjaśnionymi w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="4383d-203">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="4383d-204">Utwórz ten plik w folderze głównym lub głównym rozwiązania. powinna zawierać zawartość podobną do pokazanej w `docker-compose.yml` tym pliku:</span><span class="sxs-lookup"><span data-stu-id="4383d-204">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

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

<span data-ttu-id="4383d-205">W tym konkretnym przypadku ten plik definiuje dwie usługi: usługi sieci Web (usługi niestandardowej) i usługi Redis (popularne usługi pamięci podręcznej).</span><span class="sxs-lookup"><span data-stu-id="4383d-205">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="4383d-206">Każda usługa zostanie wdrożona jako kontener, dlatego musimy użyć konkretnego obrazu platformy Docker dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="4383d-206">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="4383d-207">W przypadku tej konkretnej usługi sieci Web obraz będzie musiał wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4383d-207">For this particular web service, the image will need to do the following:</span></span>

- <span data-ttu-id="4383d-208">Kompiluj z pliku dockerfile w bieżącym katalogu</span><span class="sxs-lookup"><span data-stu-id="4383d-208">Build from the DockerFile in the current directory</span></span>

- <span data-ttu-id="4383d-209">Przekazuj uwidoczniony port 80 w kontenerze do portu 81 na komputerze hosta</span><span class="sxs-lookup"><span data-stu-id="4383d-209">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

- <span data-ttu-id="4383d-210">Zainstaluj katalog projektu na hoście do/Code w kontenerze, dzięki czemu można modyfikować kod bez konieczności ponownego kompilowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="4383d-210">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

- <span data-ttu-id="4383d-211">Łączenie usługi sieci Web z usługą Redis</span><span class="sxs-lookup"><span data-stu-id="4383d-211">Link the web service to the redis service</span></span>

<span data-ttu-id="4383d-212">Usługa Redis używa [najnowszego publicznego obrazu Redis](https://hub.docker.com/_/redis/) pobranego z rejestru usługi Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="4383d-212">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="4383d-213">[Redis](https://redis.io/) to popularny system pamięci podręcznej dla aplikacji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="4383d-213">[redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="4383d-214">Krok 5. Kompilowanie i uruchamianie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="4383d-214">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="4383d-215">Jeśli aplikacja ma tylko jeden kontener, wystarczy ją uruchomić, wdrażając ją na hoście platformy Docker (maszynie wirtualnej lub serwerze fizycznym).</span><span class="sxs-lookup"><span data-stu-id="4383d-215">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="4383d-216">Jeśli jednak aplikacja składa się z wielu usług, musisz *ją utworzyć*.</span><span class="sxs-lookup"><span data-stu-id="4383d-216">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="4383d-217">Zobaczmy różne opcje.</span><span class="sxs-lookup"><span data-stu-id="4383d-217">Let's see the different options.</span></span>

<span data-ttu-id="4383d-218">***Opcja A: Uruchamianie pojedynczego kontenera lub usługi***</span><span class="sxs-lookup"><span data-stu-id="4383d-218">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="4383d-219">Obraz platformy Docker można uruchomić przy użyciu polecenia Docker Run, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="4383d-219">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="4383d-220">W przypadku tego konkretnego wdrożenia będziemy przekierowywać żądania wysyłane do portu 80 do wewnętrznego portu 5000.</span><span class="sxs-lookup"><span data-stu-id="4383d-220">For this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="4383d-221">Teraz aplikacja nasłuchuje na porcie zewnętrznym 80 na poziomie hosta.</span><span class="sxs-lookup"><span data-stu-id="4383d-221">Now the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="4383d-222">***Opcja B: Tworzenie i uruchamianie aplikacji z wieloma kontenerami***</span><span class="sxs-lookup"><span data-stu-id="4383d-222">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="4383d-223">W większości scenariuszy przedsiębiorstwa aplikacja platformy Docker będzie składać się z wielu usług.</span><span class="sxs-lookup"><span data-stu-id="4383d-223">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="4383d-224">W takich przypadkach można uruchomić `docker-compose up` polecenie (rysunek 4-27), które będzie korzystać z pliku Docker-Compose. yml, który został wcześniej utworzony.</span><span class="sxs-lookup"><span data-stu-id="4383d-224">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="4383d-225">Uruchomienie tego polecenia powoduje wdrożenie aplikacji składającej ze wszystkimi powiązanymi kontenerami.</span><span class="sxs-lookup"><span data-stu-id="4383d-225">Running this command deploys a composed application with all of its related containers.</span></span>

![Dane wyjściowe konsoli z platformy Docker — tworzenie.](./media/image27.png)

<span data-ttu-id="4383d-227">**Rysunek 4-27**.</span><span class="sxs-lookup"><span data-stu-id="4383d-227">**Figure 4-27**.</span></span> <span data-ttu-id="4383d-228">Wyniki uruchamiania polecenia "Docker-Zredaguj do"</span><span class="sxs-lookup"><span data-stu-id="4383d-228">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="4383d-229">Po uruchomieniu `docker-compose up`programu aplikacja i powiązane z nim kontenery są wdrażane na hoście platformy Docker, jak pokazano na rysunku 4-28 w reprezentacji maszyny wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="4383d-229">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![Maszyna wirtualna z uruchomioną funkcją wielokontenera aplikacji.](./media/image28.png)

<span data-ttu-id="4383d-231">**Rysunek 4-28**.</span><span class="sxs-lookup"><span data-stu-id="4383d-231">**Figure 4-28**.</span></span> <span data-ttu-id="4383d-232">Maszyna wirtualna z wdrożonymi kontenerami platformy Docker</span><span class="sxs-lookup"><span data-stu-id="4383d-232">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="4383d-233">Krok 6. Testowanie aplikacji platformy Docker (lokalnie, na lokalnej maszynie wirtualnej z płytą CD)</span><span class="sxs-lookup"><span data-stu-id="4383d-233">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="4383d-234">Ten krok będzie się różnić w zależności od tego, co aplikacja działa.</span><span class="sxs-lookup"><span data-stu-id="4383d-234">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="4383d-235">W prostym interfejsie API sieci Web platformy .NET Core "Hello world" wdrożonym jako pojedynczy kontener lub usługa, wystarczy uzyskać dostęp do usługi, podając port TCP określony w pliku dockerfile.</span><span class="sxs-lookup"><span data-stu-id="4383d-235">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="4383d-236">Jeśli localhost nie jest włączona, aby przejść do usługi, Znajdź adres IP dla maszyny za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="4383d-236">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

<span data-ttu-id="4383d-237">Na hoście platformy Docker Otwórz przeglądarkę i przejdź do tej witryny. powinna zostać wyświetlona aplikacja/usługa, jak pokazano na rysunku 4-29.</span><span class="sxs-lookup"><span data-stu-id="4383d-237">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Widok przeglądarki odpowiedzi z localhost/API/Values.](./media/image29.png)

<span data-ttu-id="4383d-239">**Rysunek 4-29**.</span><span class="sxs-lookup"><span data-stu-id="4383d-239">**Figure 4-29**.</span></span> <span data-ttu-id="4383d-240">Testowanie aplikacji platformy Docker lokalnie przy użyciu hosta lokalnego</span><span class="sxs-lookup"><span data-stu-id="4383d-240">Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="4383d-241">Należy zauważyć, że korzysta on z portu 80, ale wewnętrznie jest przekierowywany do portu 5000, ponieważ został on wdrożony w programie `docker run`, jak wyjaśniono wcześniej.</span><span class="sxs-lookup"><span data-stu-id="4383d-241">Note that it's using port 80, but internally it's being redirected to port 5000, because that's how it was deployed with `docker run`, as explained earlier.</span></span>

<span data-ttu-id="4383d-242">Można to przetestować przy użyciu ZWINIĘCIEa z terminalu.</span><span class="sxs-lookup"><span data-stu-id="4383d-242">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="4383d-243">W przypadku instalacji platformy Docker w systemie Windows domyślny adres IP to 10.0.75.1, jak przedstawiono na rysunku 4-30.</span><span class="sxs-lookup"><span data-stu-id="4383d-243">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-30.</span></span>

![Dane wyjściowe konsoli od pobrania http://10.0.75.1/API/values z](./media/image30.png)

<span data-ttu-id="4383d-245">**Rysunek 4-30**.</span><span class="sxs-lookup"><span data-stu-id="4383d-245">**Figure 4-30**.</span></span> <span data-ttu-id="4383d-246">Lokalne testowanie aplikacji platformy Docker przy użyciu programu ZWINIĘCIE</span><span class="sxs-lookup"><span data-stu-id="4383d-246">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="4383d-247">**Debugowanie kontenera działającego na platformie Docker**</span><span class="sxs-lookup"><span data-stu-id="4383d-247">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="4383d-248">Visual Studio Code obsługuje debugowanie platformy Docker, jeśli używasz środowiska Node. js i innych platform, takich jak kontenery .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4383d-248">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="4383d-249">Można również debugować kontenery .NET Core lub .NET Framework w programie Docker podczas korzystania z programu Visual Studio dla systemu Windows lub Mac, zgodnie z opisem w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="4383d-249">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> <span data-ttu-id="4383d-250">[! ZAWARTYCH</span><span class="sxs-lookup"><span data-stu-id="4383d-250">[!INFORMATION]</span></span>
>
> <span data-ttu-id="4383d-251">Aby dowiedzieć się więcej na temat debugowania kontenerów platformy Docker Node <https://blog.docker.com/2016/07/live-debugging-docker/> . <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>js, przejdź do i.</span><span class="sxs-lookup"><span data-stu-id="4383d-251">To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4383d-252">[Poprzedni](docker-apps-development-environment.md)
>[Następny](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="4383d-252">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
