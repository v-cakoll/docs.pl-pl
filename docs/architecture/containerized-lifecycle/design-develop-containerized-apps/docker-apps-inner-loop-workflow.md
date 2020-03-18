---
title: Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker
description: Dowiedz się o przepływie pracy "pętli wewnętrznej" dla tworzenia aplikacji platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 3d2fc889d22dbf02acccfbf9231ad98fca224cff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936811"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="587c4-103">Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="587c4-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="587c4-104">Przed wyzwolenia przepływu pracy pętli zewnętrznej obejmujących cały cykl DevOps, wszystko zaczyna się na komputerze każdego dewelopera, kodowanie samej aplikacji, przy użyciu preferowanych języków lub platform i testowanie go lokalnie (Rysunek 4-21).</span><span class="sxs-lookup"><span data-stu-id="587c4-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="587c4-105">Ale w każdym przypadku będziesz mieć ważny wspólny punkt, bez względu na język, ramy lub wybrane platformy.</span><span class="sxs-lookup"><span data-stu-id="587c4-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="587c4-106">W tym określonym przepływie pracy zawsze tworzysz i testujesz kontenery platformy Docker, ale lokalnie.</span><span class="sxs-lookup"><span data-stu-id="587c4-106">In this specific workflow, you're always developing and testing Docker containers, but locally.</span></span>

![Diagram przedstawiający pojęcie środowiska dewelopera pętli wewnętrznej.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

<span data-ttu-id="587c4-108">**Rysunek 4-21**.</span><span class="sxs-lookup"><span data-stu-id="587c4-108">**Figure 4-21**.</span></span> <span data-ttu-id="587c4-109">Kontekst rozwoju pętli wewnętrznej</span><span class="sxs-lookup"><span data-stu-id="587c4-109">Inner-loop development context</span></span>

<span data-ttu-id="587c4-110">Kontener lub wystąpienie obrazu platformy Docker będzie zawierać następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="587c4-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="587c4-111">Wybór systemu operacyjnego (na przykład dystrybucja Systemu Linux lub Windows)</span><span class="sxs-lookup"><span data-stu-id="587c4-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="587c4-112">Pliki dodane przez dewelopera (na przykład pliki binarne aplikacji)</span><span class="sxs-lookup"><span data-stu-id="587c4-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="587c4-113">Konfiguracja (na przykład ustawienia środowiska i zależności)</span><span class="sxs-lookup"><span data-stu-id="587c4-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="587c4-114">Instrukcje dotyczące procesów uruchamianych przez platformę Docker</span><span class="sxs-lookup"><span data-stu-id="587c4-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="587c4-115">Można skonfigurować przepływ pracy tworzenia pętli wewnętrznej, który wykorzystuje platformę Docker jako proces (opisany w następnej sekcji).</span><span class="sxs-lookup"><span data-stu-id="587c4-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="587c4-116">Należy wziąć pod uwagę, że początkowe kroki, aby skonfigurować środowisko nie są uwzględniane, ponieważ wystarczy zrobić to tylko raz.</span><span class="sxs-lookup"><span data-stu-id="587c4-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="587c4-117">Tworzenie pojedynczej aplikacji w kontenerze platformy Docker przy użyciu kodu programu Visual Studio i funkcji cli platformy Docker</span><span class="sxs-lookup"><span data-stu-id="587c4-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="587c4-118">Aplikacje są składane z własnych usług oraz dodatkowych bibliotek (zależności).</span><span class="sxs-lookup"><span data-stu-id="587c4-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="587c4-119">Rysunek 4-22 przedstawia podstawowe kroki, które zwykle należy wykonać podczas tworzenia aplikacji platformy Docker, a następnie szczegółowe opisy każdego kroku.</span><span class="sxs-lookup"><span data-stu-id="587c4-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Diagram przedstawiający siedem kroków potrzebnych do utworzenia aplikacji konteneryzowanej.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

<span data-ttu-id="587c4-121">**Rysunek 4-22**.</span><span class="sxs-lookup"><span data-stu-id="587c4-121">**Figure 4-22**.</span></span> <span data-ttu-id="587c4-122">Wysokopoziomowy przepływ pracy dla cyklu życia dla aplikacji konteneryzowanych platformy Docker przy użyciu interfejsu cli platformy Docker</span><span class="sxs-lookup"><span data-stu-id="587c4-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="587c4-123">Krok 1: Rozpocznij kodowanie w kodzie programu Visual Studio i utwórz początkową linię bazową aplikacji/usługi</span><span class="sxs-lookup"><span data-stu-id="587c4-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="587c4-124">Sposób tworzenia aplikacji jest podobny do sposobu, w jaki to zrobić bez platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="587c4-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="587c4-125">Różnica polega na tym, że podczas opracowywania wdrażasz i testujesz aplikację lub usługi uruchomione w kontenerach platformy Docker umieszczonych w środowisku lokalnym (takich jak maszyna wirtualna systemu Linux lub windows).</span><span class="sxs-lookup"><span data-stu-id="587c4-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="587c4-126">**Konfigurowanie lokalnego środowiska**</span><span class="sxs-lookup"><span data-stu-id="587c4-126">**Setting up your local environment**</span></span>

<span data-ttu-id="587c4-127">Dzięki najnowszym wersjom platformy Docker dla komputerów Mac i systemu Windows tworzenie aplikacji Docker jest łatwiejsze niż kiedykolwiek, a konfiguracja jest prosta.</span><span class="sxs-lookup"><span data-stu-id="587c4-127">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="587c4-128">Aby uzyskać instrukcje dotyczące konfigurowania platformy <https://docs.docker.com/docker-for-windows/>Docker dla systemu Windows, przejdź do strony .</span><span class="sxs-lookup"><span data-stu-id="587c4-128">For instructions on setting up Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
><span data-ttu-id="587c4-129">Aby uzyskać instrukcje dotyczące konfigurowania platformy <https://docs.docker.com/docker-for-mac/>Docker dla komputerów Mac, przejdź do strony .</span><span class="sxs-lookup"><span data-stu-id="587c4-129">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="587c4-130">Ponadto musisz edytor kodu, dzięki czemu można faktycznie rozwijać aplikację przy użyciu interfejsów cli platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="587c4-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="587c4-131">Firma Microsoft udostępnia program Visual Studio Code, który jest lekkim edytorem kodu obsługiwanym w systemach Windows, Linux i macOS, i zapewnia programowi IntelliSense [obsługę wielu języków](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python i najnowocześniejsze języki), [debugowanie,](https://code.visualstudio.com/Docs/editor/debugging) [integrację z obsługą git](https://code.visualstudio.com/Docs/editor/versioncontrol) i [rozszerzeń.](https://code.visualstudio.com/docs/extensions/overview)</span><span class="sxs-lookup"><span data-stu-id="587c4-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Windows, Linux, and macOS, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="587c4-132">Ten edytor jest doskonałym rozwiązaniem dla programistów macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="587c4-132">This editor is a great fit for macOS and Linux developers.</span></span> <span data-ttu-id="587c4-133">W systemie Windows można również użyć programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="587c4-133">In Windows, you also can use Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="587c4-134">Aby uzyskać instrukcje dotyczące instalowania kodu programu Visual Studio dla <https://code.visualstudio.com/docs/setup/setup-overview/>systemu Windows, Systemu Linux lub systemu macOS, przejdź do strony .</span><span class="sxs-lookup"><span data-stu-id="587c4-134">For instructions on installing Visual Studio Code for Windows, Linux, or macOS, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="587c4-135">Aby uzyskać instrukcje dotyczące konfigurowania platformy <https://docs.docker.com/docker-for-mac/>Docker dla komputerów Mac, przejdź do strony .</span><span class="sxs-lookup"><span data-stu-id="587c4-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="587c4-136">Można pracować z platformą Docker CLI i napisać kod przy użyciu dowolnego edytora kodu, `Dockerfile` `docker-compose.yml` ale za pomocą kodu programu Visual Studio z rozszerzeniem platformy Docker ułatwia tworzenie i pliki w obszarze roboczym.</span><span class="sxs-lookup"><span data-stu-id="587c4-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="587c4-137">Można również uruchamiać zadania i skrypty z IDE kodu programu Visual Studio do wykonywania poleceń platformy Docker przy użyciu polecenia wiersza polecenia platformy Docker poniżej.</span><span class="sxs-lookup"><span data-stu-id="587c4-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="587c4-138">Rozszerzenie platformy Docker dla kodu VS zawiera następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="587c4-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="587c4-139">Automatyczne `Dockerfile` `docker-compose.yml` i generowanie plików</span><span class="sxs-lookup"><span data-stu-id="587c4-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="587c4-140">Opisy wyróżniania i `docker-compose.yml` aktywowania składni i `Dockerfile` aktywowanie</span><span class="sxs-lookup"><span data-stu-id="587c4-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="587c4-141">IntelliSense (uzupełnienia) `Dockerfile` dla `docker-compose.yml` i plików</span><span class="sxs-lookup"><span data-stu-id="587c4-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="587c4-142">Linting (błędy i ostrzeżenia) dla `Dockerfile` plików</span><span class="sxs-lookup"><span data-stu-id="587c4-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="587c4-143">Integracja z paletą poleceń (F1) dla najpopularniejszych poleceń platformy Docker</span><span class="sxs-lookup"><span data-stu-id="587c4-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="587c4-144">Integracja eksploratora do zarządzania obrazami i kontenerami</span><span class="sxs-lookup"><span data-stu-id="587c4-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="587c4-145">Wdrażanie obrazów z usługi DockerHub i usługi Azure Container Registries w usłudze Azure App Service</span><span class="sxs-lookup"><span data-stu-id="587c4-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="587c4-146">Aby zainstalować rozszerzenie platformy Docker, naciśnij `ext install`klawisze Ctrl+Shift+P, wpisz , a następnie uruchom polecenie Zainstaluj rozszerzenie, aby wyświetlić listę rozszerzeń marketplace.</span><span class="sxs-lookup"><span data-stu-id="587c4-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="587c4-147">Następnie wpisz **docker,** aby filtrować wyniki, a następnie wybierz rozszerzenie docker Support, jak przedstawiono na rysunku 4-23.</span><span class="sxs-lookup"><span data-stu-id="587c4-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![Widok rozszerzenia platformy Docker dla kodu VS.](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

<span data-ttu-id="587c4-149">**Rysunek 4-23**.</span><span class="sxs-lookup"><span data-stu-id="587c4-149">**Figure 4-23**.</span></span> <span data-ttu-id="587c4-150">Instalowanie rozszerzenia platformy Docker w kodzie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="587c4-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="587c4-151">Krok 2: Tworzenie pliku DockerFile powiązanego z istniejącym obrazem (zwykły system operacyjny lub środowiska deweloperów, takie jak .NET Core, Node.js i Ruby)</span><span class="sxs-lookup"><span data-stu-id="587c4-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="587c4-152">Do skonstruowania `DockerFile` i wdrożenia należy wykonać obraz niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="587c4-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="587c4-153">Jeśli aplikacja składa się z jednej usługi niestandardowej, `DockerFile`potrzebujesz jednej usługi.</span><span class="sxs-lookup"><span data-stu-id="587c4-153">If your app is made up of a single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="587c4-154">Ale jeśli aplikacja składa się z wielu usług (jak w architekturze mikrousług), trzeba jeden `Dockerfile` na usługę.</span><span class="sxs-lookup"><span data-stu-id="587c4-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="587c4-155">Jest `DockerFile` często umieszczany w folderze głównym aplikacji lub usługi i zawiera wymagane polecenia, dzięki czemu platforma Docker wie, jak skonfigurować i uruchomić tę aplikację lub usługę.</span><span class="sxs-lookup"><span data-stu-id="587c4-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="587c4-156">Możesz utworzyć `DockerFile` i dodać go do projektu wraz z kodem (node.js, .NET Core itp.) lub, jeśli jesteś nowy w środowisku, spójrz na następującą końcówkę.</span><span class="sxs-lookup"><span data-stu-id="587c4-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="587c4-157">Rozszerzenie platformy Docker służy do prowadzenia `Dockerfile` `docker-compose.yml` użytkownika podczas korzystania z plików związanych z kontenerami platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="587c4-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="587c4-158">W końcu prawdopodobnie napiszesz tego rodzaju pliki bez tego narzędzia, ale użycie rozszerzenia Docker jest dobrym punktem wyjścia, który przyspieszy krzywą uczenia się.</span><span class="sxs-lookup"><span data-stu-id="587c4-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="587c4-159">Na rysunku 4-24 można zobaczyć, jak plik docker-compose jest dodawany przy użyciu rozszerzenia platformy Docker dla kodu VS.</span><span class="sxs-lookup"><span data-stu-id="587c4-159">In Figure 4-24, you can see how a docker-compose file is added by using the Docker Extension for VS Code.</span></span>

![Widok konsoli rozszerzenia platformy Docker dla kodu VS.](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

<span data-ttu-id="587c4-161">**Rysunek 4-24**.</span><span class="sxs-lookup"><span data-stu-id="587c4-161">**Figure 4-24**.</span></span> <span data-ttu-id="587c4-162">Pliki docker dodane przy użyciu **polecenia Dodaj pliki docker do obszaru roboczego**</span><span class="sxs-lookup"><span data-stu-id="587c4-162">Docker files added using the **Add Docker files to Workspace command**</span></span>

<span data-ttu-id="587c4-163">Po dodaniu pliku DockerFile należy określić, jakiego podstawowego obrazu `FROM mcr.microsoft.com/dotnet/core/aspnet`platformy Docker będziesz używać (np. przy użyciu).</span><span class="sxs-lookup"><span data-stu-id="587c4-163">When you add a DockerFile, you specify what base Docker image you’ll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="587c4-164">Zazwyczaj tworzysz obraz niestandardowy na obrazie podstawowym uzyskanym z dowolnego oficjalnego repozytorium w [rejestrze docker hub](https://hub.docker.com/) (na przykład [obraz dla programu .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) lub obraz dla [node.js).](https://hub.docker.com/_/node/)</span><span class="sxs-lookup"><span data-stu-id="587c4-164">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="587c4-165">***Używanie istniejącego oficjalnego obrazu platformy Docker***</span><span class="sxs-lookup"><span data-stu-id="587c4-165">***Use an existing official Docker image***</span></span>

<span data-ttu-id="587c4-166">Korzystanie z oficjalnego repozytorium stosu językowego z numerem wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym rozwoju, testowania i produkcji).</span><span class="sxs-lookup"><span data-stu-id="587c4-166">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="587c4-167">Poniżej przedstawiono przykładowy plik DockerFile dla kontenera .NET Core:</span><span class="sxs-lookup"><span data-stu-id="587c4-167">The following is a sample DockerFile for a .NET Core container:</span></span>

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

<span data-ttu-id="587c4-168">W tym przypadku obraz jest oparty na wersji 2.2 oficjalnego ASP.NET Core Docker (multi-arch `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`dla Linuksa i Windows), zgodnie z linią .</span><span class="sxs-lookup"><span data-stu-id="587c4-168">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="587c4-169">(Aby uzyskać więcej informacji na ten temat, zobacz ASP.NET core [docker image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) strony i [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) strony).</span><span class="sxs-lookup"><span data-stu-id="587c4-169">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="587c4-170">W pliku DockerFile można również poinstruować platformę Docker, aby nasłuchiwać portu TCP, który będzie używany w czasie wykonywania (na przykład port 80).</span><span class="sxs-lookup"><span data-stu-id="587c4-170">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80).</span></span>

<span data-ttu-id="587c4-171">Można określić dodatkowe ustawienia konfiguracji w pliku Dockerfile, w zależności od języka i struktury, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="587c4-171">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="587c4-172">Na przykład `ENTRYPOINT` wiersz `["dotnet", "MySingleContainerWebApp.dll"]` z mówi docker do uruchomienia aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="587c4-172">For instance, the `ENTRYPOINT` line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="587c4-173">Jeśli używasz sdk i .NET Core CLI`dotnet CLI`( ) do tworzenia i uruchamiania aplikacji .NET, to ustawienie będzie inna.</span><span class="sxs-lookup"><span data-stu-id="587c4-173">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="587c4-174">Kluczową kwestią jest to, że linia ENTRYPOINT i inne ustawienia zależą od języka i platformy wybranej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="587c4-174">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="587c4-175">Aby uzyskać więcej informacji na temat tworzenia obrazów <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>platformy Docker dla aplikacji .NET Core, przejdź do .</span><span class="sxs-lookup"><span data-stu-id="587c4-175">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="587c4-176">Aby dowiedzieć się więcej o tworzeniu <https://docs.docker.com/engine/tutorials/dockerimages/>własnych obrazów, przejdź do .</span><span class="sxs-lookup"><span data-stu-id="587c4-176">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="587c4-177">**Korzystanie z repozytoriów obrazów wielołukowych**</span><span class="sxs-lookup"><span data-stu-id="587c4-177">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="587c4-178">Nazwa pojedynczego obrazu w reppo może zawierać warianty platformy, takie jak obraz systemu Linux i obraz systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="587c4-178">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="587c4-179">Ta funkcja umożliwia dostawcom takim jak Microsoft (twórcy obrazów bazowych) tworzenie pojedynczego reponu na wiele platform (czyli Linux i Windows).</span><span class="sxs-lookup"><span data-stu-id="587c4-179">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="587c4-180">Na przykład repozytorium [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) dostępne w rejestrze docker Hub zapewnia obsługę systemów Linux i Windows Nano Server przy użyciu tej samej nazwy obrazu.</span><span class="sxs-lookup"><span data-stu-id="587c4-180">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="587c4-181">Wyciąganie obrazu [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) z hosta systemu Windows pobiera wariant systemu Windows, podczas gdy pobieranie tej samej nazwy obrazu z hosta Linux ściąga wariant Linuksa.</span><span class="sxs-lookup"><span data-stu-id="587c4-181">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="587c4-182">***Tworzenie obrazu bazowego od podstaw***</span><span class="sxs-lookup"><span data-stu-id="587c4-182">***Create your base image from scratch***</span></span>

<span data-ttu-id="587c4-183">Można utworzyć własny obraz podstawowy platformy Docker od podstaw, jak wyjaśniono w tym [artykule](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="587c4-183">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="587c4-184">Ten scenariusz prawdopodobnie nie jest najlepszy dla Ciebie, jeśli dopiero zaczynasz z platformą Docker, ale jeśli chcesz ustawić określone bity własnego obrazu podstawowego, możesz to zrobić.</span><span class="sxs-lookup"><span data-stu-id="587c4-184">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="587c4-185">Krok 3: Tworzenie niestandardowych obrazów platformy Docker osadzania usługi w nim</span><span class="sxs-lookup"><span data-stu-id="587c4-185">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="587c4-186">Dla każdej usługi niestandardowej, która składa się z aplikacji, należy utworzyć powiązany obraz.</span><span class="sxs-lookup"><span data-stu-id="587c4-186">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="587c4-187">Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci Web, potrzebujesz tylko jednego obrazu.</span><span class="sxs-lookup"><span data-stu-id="587c4-187">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="587c4-188">Biorąc pod uwagę "przepływ pracy DevOps w pętli zewnętrznej", obrazy będą tworzone przez zautomatyzowany proces kompilacji za każdym razem, gdy wypchniesz kod źródłowy do repozytorium Git (Ciągła integracja), dzięki czemu obrazy zostaną utworzone w tym środowisku globalnym z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="587c4-188">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="587c4-189">Ale zanim rozważymy przejście do tej trasy pętli zewnętrznej, musimy upewnić się, że aplikacja Docker faktycznie działa poprawnie, tak aby nie wypychać kodu, który może nie działać poprawnie do systemu kontroli źródła (Git, itp.).</span><span class="sxs-lookup"><span data-stu-id="587c4-189">But before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="587c4-190">W związku z tym każdy deweloper najpierw musi wykonać cały proces pętli wewnętrznej, aby przetestować lokalnie i kontynuować rozwój, dopóki nie będzie chciał wypchnąć pełną funkcję lub zmienić system kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="587c4-190">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="587c4-191">Aby utworzyć obraz w środowisku lokalnym i za pomocą DockerFile, można użyć polecenia kompilacji platformy docker, jak pokazano na rysunku 4-25 (można również uruchomić `docker-compose up --build` dla aplikacji złożonych przez kilka kontenerów/usług).</span><span class="sxs-lookup"><span data-stu-id="587c4-191">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-25 (you also can run `docker-compose up --build` for applications composed by several containers/services).</span></span>

![Zrzut ekranu przedstawiający dane wyjściowe konsoli polecenia kompilacji platformy docker.](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

<span data-ttu-id="587c4-193">**Rysunek 4-25**.</span><span class="sxs-lookup"><span data-stu-id="587c4-193">**Figure 4-25**.</span></span> <span data-ttu-id="587c4-194">Uruchamianie kompilacji platformy docker</span><span class="sxs-lookup"><span data-stu-id="587c4-194">Running docker build</span></span>

<span data-ttu-id="587c4-195">Opcjonalnie zamiast bezpośrednio `docker build` uruchamiać z folderu projektu, można najpierw wygenerować folder wdrażalny z `dotnet publish` bibliotekami .NET potrzebnymi przy użyciu polecenia uruchom, a następnie uruchomić `docker build`.</span><span class="sxs-lookup"><span data-stu-id="587c4-195">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="587c4-196">W tym przykładzie tworzy obraz `cesardl/netcore-webapi-microservice-docker:first` platformy Docker o nazwie (jest`:first` tagiem, jak określona wersja).</span><span class="sxs-lookup"><span data-stu-id="587c4-196">This example creates a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first` (`:first` is a tag, like a specific version).</span></span> <span data-ttu-id="587c4-197">Można wykonać ten krok dla każdego niestandardowego obrazu, który należy utworzyć dla skomponowanej aplikacji platformy Docker z kilku kontenerów.</span><span class="sxs-lookup"><span data-stu-id="587c4-197">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="587c4-198">Istniejące obrazy można znaleźć w lokalnym repozytorium (komputerze deweloperskim) za pomocą polecenia obrazy dokowane, jak pokazano na rysunku 4-26.</span><span class="sxs-lookup"><span data-stu-id="587c4-198">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-26.</span></span>

![Wyjście konsoli z obrazów dokatki poleceń, pokazujące istniejące obrazy.](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="587c4-200">**Rysunek 4-26**.</span><span class="sxs-lookup"><span data-stu-id="587c4-200">**Figure 4-26**.</span></span> <span data-ttu-id="587c4-201">Wyświetlanie istniejących obrazów przy użyciu obrazów dokowane</span><span class="sxs-lookup"><span data-stu-id="587c4-201">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="587c4-202">Krok 4: Definiowanie usług w pliku docker-compose.yml podczas tworzenia skomponowanej aplikacji platformy Docker z wieloma usługami</span><span class="sxs-lookup"><span data-stu-id="587c4-202">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="587c4-203">Za `docker-compose.yml` pomocą pliku można zdefiniować zestaw powiązanych usług, które mają zostać wdrożone jako złożona aplikacja z poleceniami wdrażania wyjaśnionymi w sekcji następny krok.</span><span class="sxs-lookup"><span data-stu-id="587c4-203">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="587c4-204">Utwórz ten plik w głównym lub głównym folderze rozwiązania; powinien mieć treści podobne do `docker-compose.yml` tych pokazanych w tym pliku:</span><span class="sxs-lookup"><span data-stu-id="587c4-204">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

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

<span data-ttu-id="587c4-205">W tym konkretnym przypadku ten plik definiuje dwie usługi: usługę sieci web (usługa niestandardowa) i usługę redis (popularną usługę pamięci podręcznej).</span><span class="sxs-lookup"><span data-stu-id="587c4-205">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="587c4-206">Każda usługa zostanie wdrożona jako kontener, więc musimy użyć konkretnego obrazu platformy Docker dla każdego.</span><span class="sxs-lookup"><span data-stu-id="587c4-206">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="587c4-207">W przypadku tej konkretnej usługi sieci Web obraz będzie musiał wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="587c4-207">For this particular web service, the image will need to do the following:</span></span>

- <span data-ttu-id="587c4-208">Tworzenie z pliku DockerFile w bieżącym katalogu</span><span class="sxs-lookup"><span data-stu-id="587c4-208">Build from the DockerFile in the current directory</span></span>

- <span data-ttu-id="587c4-209">Prześlij odsłonięty port 80 na kontenerze do portu 81 na maszynie hosta</span><span class="sxs-lookup"><span data-stu-id="587c4-209">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

- <span data-ttu-id="587c4-210">Zamontuj katalog projektu na hoście do /code w kontenerze, umożliwiając modyfikowanie kodu bez konieczności odbudowywania obrazu</span><span class="sxs-lookup"><span data-stu-id="587c4-210">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

- <span data-ttu-id="587c4-211">Połącz usługę sieci web z usługą redis</span><span class="sxs-lookup"><span data-stu-id="587c4-211">Link the web service to the redis service</span></span>

<span data-ttu-id="587c4-212">Usługa redis używa [najnowszego publicznego obrazu redis](https://hub.docker.com/_/redis/) pobieranego z rejestru docker hub.</span><span class="sxs-lookup"><span data-stu-id="587c4-212">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="587c4-213">[redis](https://redis.io/) to popularny system pamięci podręcznej dla aplikacji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="587c4-213">[redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="587c4-214">Krok 5: Tworzenie i uruchamianie aplikacji Platformy Docker</span><span class="sxs-lookup"><span data-stu-id="587c4-214">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="587c4-215">Jeśli aplikacja ma tylko jeden kontener, wystarczy uruchomić go, wdrażając go na hoście platformy Docker (maszynie wirtualnej lub serwerze fizycznym).</span><span class="sxs-lookup"><span data-stu-id="587c4-215">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="587c4-216">Jeśli jednak aplikacja składa się z wielu usług, należy *ją również skomponować.*</span><span class="sxs-lookup"><span data-stu-id="587c4-216">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="587c4-217">Zobaczmy różne opcje.</span><span class="sxs-lookup"><span data-stu-id="587c4-217">Let's see the different options.</span></span>

<span data-ttu-id="587c4-218">***Opcja A: Uruchamianie pojedynczego kontenera lub usługi***</span><span class="sxs-lookup"><span data-stu-id="587c4-218">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="587c4-219">Obraz platformy Docker można uruchomić za pomocą polecenia docker run, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="587c4-219">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="587c4-220">W przypadku tego konkretnego wdrożenia będziemy przekierowywać żądania wysłane do portu 80 do portu wewnętrznego 5000.</span><span class="sxs-lookup"><span data-stu-id="587c4-220">For this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="587c4-221">Teraz aplikacja nasłuchuje na zewnętrznym porcie 80 na poziomie hosta.</span><span class="sxs-lookup"><span data-stu-id="587c4-221">Now the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="587c4-222">***Opcja B: Tworzenie i uruchamianie aplikacji z wieloma kontenerami***</span><span class="sxs-lookup"><span data-stu-id="587c4-222">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="587c4-223">W większości scenariuszy przedsiębiorstwa aplikacja platformy Docker będzie składać się z wielu usług.</span><span class="sxs-lookup"><span data-stu-id="587c4-223">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="587c4-224">W takich przypadkach można `docker-compose up` uruchomić polecenie (Rysunek 4-27), które będzie używać pliku docker-compose.yml, który został utworzony wcześniej.</span><span class="sxs-lookup"><span data-stu-id="587c4-224">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="587c4-225">Uruchomienie tego polecenia wdraża skomponowaną aplikację ze wszystkimi powiązanymi kontenerami.</span><span class="sxs-lookup"><span data-stu-id="587c4-225">Running this command deploys a composed application with all of its related containers.</span></span>

![Dane wyjściowe konsoli z polecenia docker-compose up.](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

<span data-ttu-id="587c4-227">**Rysunek 4-27**.</span><span class="sxs-lookup"><span data-stu-id="587c4-227">**Figure 4-27**.</span></span> <span data-ttu-id="587c4-228">Wyniki uruchamiania polecenia "docker-compose up"</span><span class="sxs-lookup"><span data-stu-id="587c4-228">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="587c4-229">Po uruchomieniu `docker-compose up`należy wdrożyć aplikację i powiązane z nią kontenery w hoście platformy Docker, jak pokazano na rysunku 4-28, w reprezentacji maszyny Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="587c4-229">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![Maszyna wirtualna z aplikacjami wielokontenerowymi.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="587c4-231">**Rysunek 4-28**.</span><span class="sxs-lookup"><span data-stu-id="587c4-231">**Figure 4-28**.</span></span> <span data-ttu-id="587c4-232">Maszyna wirtualna z wdrożonymi kontenerami platformy Docker</span><span class="sxs-lookup"><span data-stu-id="587c4-232">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="587c4-233">Krok 6: Przetestuj aplikację platformy Docker (lokalnie, w lokalnej maszynie wirtualnej CD)</span><span class="sxs-lookup"><span data-stu-id="587c4-233">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="587c4-234">Ten krok będzie się różnić w zależności od tego, co aplikacja robi.</span><span class="sxs-lookup"><span data-stu-id="587c4-234">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="587c4-235">W prostym interfejsie API sieci Web programu .NET Core "Hello World" wdrożonym jako pojedynczy kontener lub usługa wystarczy uzyskać dostęp do usługi, udostępniając port TCP określony w pliku DockerFile.</span><span class="sxs-lookup"><span data-stu-id="587c4-235">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="587c4-236">Jeśli host lokalny nie jest włączony, aby przejść do usługi, znajdź adres IP komputera za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="587c4-236">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

<span data-ttu-id="587c4-237">Na hoście platformy Docker otwórz przeglądarkę i przejdź do tej witryny; powinna zostać wyświetlona uruchomiona aplikacja/usługa, jak pokazano na rysunku 4-29.</span><span class="sxs-lookup"><span data-stu-id="587c4-237">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Widok przeglądarki odpowiedzi z localhost/API/wartości.](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="587c4-239">**Rysunek 4-29**.</span><span class="sxs-lookup"><span data-stu-id="587c4-239">**Figure 4-29**.</span></span> <span data-ttu-id="587c4-240">Testowanie aplikacji platformy Docker lokalnie przy użyciu localhost</span><span class="sxs-lookup"><span data-stu-id="587c4-240">Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="587c4-241">Należy pamiętać, że używa portu 80, ale wewnętrznie jest przekierowywany do portu 5000, `docker run`ponieważ tak został wdrożony z , jak wyjaśniono wcześniej.</span><span class="sxs-lookup"><span data-stu-id="587c4-241">Note that it's using port 80, but internally it's being redirected to port 5000, because that's how it was deployed with `docker run`, as explained earlier.</span></span>

<span data-ttu-id="587c4-242">Można to sprawdzić za pomocą CURL z terminala.</span><span class="sxs-lookup"><span data-stu-id="587c4-242">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="587c4-243">W instalacji platformy Docker w systemie Windows domyślnyadres IP to 10.0.75.1, jak przedstawiono na rysunku 4-30.</span><span class="sxs-lookup"><span data-stu-id="587c4-243">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-30.</span></span>

![Wyjście konsoli z http://10.0.75.1/API/values uzyskania z curl](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="587c4-245">**Rysunek 4-30**.</span><span class="sxs-lookup"><span data-stu-id="587c4-245">**Figure 4-30**.</span></span> <span data-ttu-id="587c4-246">Testowanie aplikacji Platformy Docker lokalnie przy użyciu curl</span><span class="sxs-lookup"><span data-stu-id="587c4-246">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="587c4-247">**Debugowanie kontenera działającego na platformie Docker**</span><span class="sxs-lookup"><span data-stu-id="587c4-247">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="587c4-248">Visual Studio Code obsługuje debugowanie platformy Docker, jeśli używasz Node.js i innych platform, takich jak kontenery .NET Core.</span><span class="sxs-lookup"><span data-stu-id="587c4-248">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="587c4-249">Można również debugować kontenery .NET Core lub .NET Framework w platformie Docker podczas korzystania z programu Visual Studio dla systemu Windows lub Mac, zgodnie z opisem w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="587c4-249">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="587c4-250">Aby dowiedzieć się więcej na temat debugowania kontenerów platformy Docker węzła js, zobacz <https://blog.docker.com/2016/07/live-debugging-docker/> i <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span><span class="sxs-lookup"><span data-stu-id="587c4-250">To learn more about debugging Node.js Docker containers, see <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="587c4-251">[Poprzedni](docker-apps-development-environment.md)
>[następny](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="587c4-251">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
