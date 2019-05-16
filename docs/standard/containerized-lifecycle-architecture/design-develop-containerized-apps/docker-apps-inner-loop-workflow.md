---
title: Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker
description: Dowiedz się więcej "wewnętrzną pętlę" przepływu pracy dla opracowywania aplikacji platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: ce573546f61b98c2f93e998203497fa949e9efe8
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644864"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="fde1e-103">Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fde1e-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="fde1e-104">Przed wyzwoleniem zewnętrzna Pętla przepływu pracy, obejmujące cały DevOps cyklu, rozpoczyna na każdy Deweloper maszynie kodowania samej aplikacji, za pomocą swojego preferowanego języków lub platform i testowanie jej lokalnie (rysunek 4-21).</span><span class="sxs-lookup"><span data-stu-id="fde1e-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="fde1e-105">Jednak w każdym przypadku, będziesz mieć to ważny punkt, niezależnie od tego, jaki język, struktury lub platform wybierz.</span><span class="sxs-lookup"><span data-stu-id="fde1e-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="fde1e-106">W tym określonego przepływu pracy zawsze tworzenia i testowania kontenerów platformy Docker, ale lokalnie.</span><span class="sxs-lookup"><span data-stu-id="fde1e-106">In this specific workflow, you're always developing and testing Docker containers, but locally.</span></span>

![Krok 1 — Kod/uruchomienia/debugowania](./media/image18.png)

<span data-ttu-id="fde1e-108">**Rysunek 4-21**.</span><span class="sxs-lookup"><span data-stu-id="fde1e-108">**Figure 4-21**.</span></span> <span data-ttu-id="fde1e-109">Kontekst wewnętrznej pętli tworzenia kodu</span><span class="sxs-lookup"><span data-stu-id="fde1e-109">Inner-loop development context</span></span>

<span data-ttu-id="fde1e-110">Kontener lub wystąpienia obrazu platformy Docker będzie zawierać tych składników:</span><span class="sxs-lookup"><span data-stu-id="fde1e-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="fde1e-111">Wybór systemu operacyjnego (na przykład dystrybucji systemu Linux lub Windows)</span><span class="sxs-lookup"><span data-stu-id="fde1e-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="fde1e-112">Pliki dodawane przez dewelopera (na przykład pliki binarne aplikacji)</span><span class="sxs-lookup"><span data-stu-id="fde1e-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="fde1e-113">Konfiguracja (na przykład ustawienia środowiska i zależności)</span><span class="sxs-lookup"><span data-stu-id="fde1e-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="fde1e-114">Instrukcje dotyczące jakie procesy do uruchomione przez platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fde1e-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="fde1e-115">Możesz skonfigurować przepływ pracy wewnętrznej pętli tworzenia kodu, który korzysta z platformy Docker jako proces (opisany w następnej sekcji).</span><span class="sxs-lookup"><span data-stu-id="fde1e-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="fde1e-116">Należy wziąć pod uwagę początkowe kroki konfigurowania środowiska nie są dołączane, ponieważ należy ją wykonać jeden raz.</span><span class="sxs-lookup"><span data-stu-id="fde1e-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="fde1e-117">Tworzenie pojedynczej aplikacji w kontenerze platformy Docker przy użyciu programu Visual Studio Code i interfejsu wiersza polecenia platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fde1e-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="fde1e-118">Aplikacje składają się z własnych usług, a także dodatkowe biblioteki (zależności).</span><span class="sxs-lookup"><span data-stu-id="fde1e-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="fde1e-119">Rysunek 4-22 przedstawiono podstawowe kroki, które zazwyczaj trzeba przeprowadzić podczas kompilowania aplikacji platformy Docker, następuje szczegółowy opis każdego kroku.</span><span class="sxs-lookup"><span data-stu-id="fde1e-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Omówienie przepływu pracy: Krok 1 — kodu, krok 2 — zapis plików Dockerfile, krok 3 — Tworzenie obrazów zdefiniowane przy użyciu plików Dockerfile, krok 4 — zdefiniowanie usług przy użyciu pliku docker-compose, krok 5 — uruchom kontenery lub złożone aplikacje, krok 6 — aplikacje testowe, krok 7 — Wypychanie do rozpoczęcia zewnętrzna pętla (potoki ciągłej integracji/ciągłego wdrażania) lub kontynuować de veloping.](./media/image19.png)

<span data-ttu-id="fde1e-121">**Rysunek 4-22**.</span><span class="sxs-lookup"><span data-stu-id="fde1e-121">**Figure 4-22**.</span></span> <span data-ttu-id="fde1e-122">Ogólny przepływ pracy dla cyklu życia aplikacji kontenerowych nimi platformy Docker za pomocą interfejsu wiersza polecenia platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fde1e-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="fde1e-123">Krok 1. Rozpocznij kodowanie w programie Visual Studio Code i utworzyć linię bazową początkową aplikacji/usługi</span><span class="sxs-lookup"><span data-stu-id="fde1e-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="fde1e-124">Sposób tworzenia aplikacji jest podobny sposób, co można zrobić bez platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="fde1e-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="fde1e-125">Różnica jest, że podczas tworzenia, jesteś wdrażania i testowania aplikacji lub usług działających w kontenerach platformy Docker, umieszczone w środowisku lokalnym (np. maszyny Wirtualnej systemu Linux lub Windows).</span><span class="sxs-lookup"><span data-stu-id="fde1e-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="fde1e-126">**Konfigurowanie środowiska lokalnego**</span><span class="sxs-lookup"><span data-stu-id="fde1e-126">**Setting up your local environment**</span></span>

<span data-ttu-id="fde1e-127">Najnowsze wersje platformy Docker dla systemów Mac i Windows jest łatwiejsze niż kiedykolwiek do tworzenia aplikacji platformy Docker i konfiguracja jest prosta.</span><span class="sxs-lookup"><span data-stu-id="fde1e-127">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [! INFORMACJE O]
>
> <span data-ttu-id="fde1e-129">Aby uzyskać instrukcje na temat konfigurowania Docker for Windows, przejdź do <https://docs.docker.com/docker-for-windows/>.</span><span class="sxs-lookup"><span data-stu-id="fde1e-129">For instructions on setting up Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
><span data-ttu-id="fde1e-130">Aby uzyskać instrukcje na temat konfigurowania platformy Docker dla komputerów Mac, przejdź do <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="fde1e-130">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="fde1e-131">Ponadto należy Edytor kodu, aby faktycznie można opracować aplikację przy użyciu interfejsu wiersza polecenia platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="fde1e-131">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="fde1e-132">Firma Microsoft udostępnia programu Visual Studio Code, czyli lekkiemu edytorowi kodu, która jest obsługiwana na komputerach Mac, Windows i Linux, oferuje funkcję IntelliSense za pomocą [Obsługa wielu języków](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python i większość nowoczesnych języków), [debugowania](https://code.visualstudio.com/Docs/editor/debugging), [integracji z usługą Git](https://code.visualstudio.com/Docs/editor/versioncontrol) i [Obsługa rozszerzeń](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="fde1e-132">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="fde1e-133">Ten edytor to doskonałe rozwiązanie dla deweloperów systemów Mac i Linux.</span><span class="sxs-lookup"><span data-stu-id="fde1e-133">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="fde1e-134">W Windows możesz również można użyć pełnej aplikacji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fde1e-134">In Windows, you also can use the full Visual Studio application.</span></span>

> [! INFORMACJE O]
>
> <span data-ttu-id="fde1e-136">Aby uzyskać instrukcje na temat instalowania programu Visual Studio Code dla Windows, Mac lub Linux, przejdź do <https://code.visualstudio.com/docs/setup/setup-overview/>.</span><span class="sxs-lookup"><span data-stu-id="fde1e-136">For instructions on installing Visual Studio Code for Windows, Mac, or Linux, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="fde1e-137">Aby uzyskać instrukcje na temat konfigurowania platformy Docker dla komputerów Mac, przejdź do <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="fde1e-137">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="fde1e-138">Można pracować z interfejsem wiersza polecenia platformy Docker i pisanie kodu za pomocą dowolnego edytora kodu, ale z rozszerzeniem platformy Docker przy użyciu programu Visual Studio Code to łatwe do autora `Dockerfile` i `docker-compose.yml` plików w obszarze roboczym.</span><span class="sxs-lookup"><span data-stu-id="fde1e-138">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="fde1e-139">Zadania i skrypty można również uruchomić z programu Visual Studio IDE kod do wykonywania poleceń platformy Docker przy użyciu interfejsu wiersza polecenia Docker poniżej.</span><span class="sxs-lookup"><span data-stu-id="fde1e-139">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="fde1e-140">Rozszerzenia platformy Docker dla programu VS Code oferuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="fde1e-140">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="fde1e-141">Automatyczne `Dockerfile` i `docker-compose.yml` Generowanie pliku</span><span class="sxs-lookup"><span data-stu-id="fde1e-141">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="fde1e-142">Wyróżnianie i aktywuje porady dotyczące składni dla `docker-compose.yml` i `Dockerfile` plików</span><span class="sxs-lookup"><span data-stu-id="fde1e-142">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="fde1e-143">Funkcja IntelliSense (uzupełnianie) dla `Dockerfile` i `docker-compose.yml` plików</span><span class="sxs-lookup"><span data-stu-id="fde1e-143">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="fde1e-144">Zaznaczanie błędów (błędy i ostrzeżenia) dla `Dockerfile` plików</span><span class="sxs-lookup"><span data-stu-id="fde1e-144">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="fde1e-145">Polecenie integracji palety (F1) dla najczęściej używanych poleceń platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fde1e-145">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="fde1e-146">Integracja z Eksploratorem zarządzania obrazami i kontenery</span><span class="sxs-lookup"><span data-stu-id="fde1e-146">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="fde1e-147">Wdrażanie obrazów z witryny DockerHub i rejestry kontenerów platformy Azure w usłudze Azure App Service</span><span class="sxs-lookup"><span data-stu-id="fde1e-147">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="fde1e-148">Aby zainstalować rozszerzenia platformy Docker, naciśnij klawisze Ctrl + Shift + P, wpisz `ext install`, a następnie uruchom polecenie Zainstaluj rozszerzenie, aby wyświetlić listę rozszerzeń witryny Marketplace.</span><span class="sxs-lookup"><span data-stu-id="fde1e-148">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="fde1e-149">Następnie wpisz **docker** do filtrowania wyników, a następnie wybierz rozszerzenie obsługi programu Docker, jak pokazano w rysunek 4-23.</span><span class="sxs-lookup"><span data-stu-id="fde1e-149">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![Wyświetl rozszerzenia platformy Docker dla programu VS Code.](./media/image20.png)

<span data-ttu-id="fde1e-151">**Rysunek 4-23**.</span><span class="sxs-lookup"><span data-stu-id="fde1e-151">**Figure 4-23**.</span></span> <span data-ttu-id="fde1e-152">Instalowanie rozszerzenia platformy Docker w programie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fde1e-152">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="fde1e-153">Krok 2. Tworzenie pliku DockerFile związane z istniejącego obrazu (zwykły system operacyjny lub środowiskach deweloperskich, takich jak .NET Core, Node.js i Ruby)</span><span class="sxs-lookup"><span data-stu-id="fde1e-153">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="fde1e-154">Będziesz potrzebować `DockerFile` według obrazu niestandardowego do zbudowania i kontenera do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="fde1e-154">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="fde1e-155">Jeśli aplikacja składa się z jednej usługi niestandardowe, należy jeden `DockerFile`.</span><span class="sxs-lookup"><span data-stu-id="fde1e-155">If your app is made up of a single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="fde1e-156">Ale jeśli aplikacja składa się z wielu usług (tak jak w architekturze mikrousług), trzeba będzie je utworzyć `Dockerfile` na usługę.</span><span class="sxs-lookup"><span data-stu-id="fde1e-156">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="fde1e-157">`DockerFile` Często znajduje się w folderze głównym aplikacji lub usługi i zawiera wymagane polecenia, tak że platforma Docker wie, jak skonfigurować i uruchomić tej aplikacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="fde1e-157">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="fde1e-158">Można utworzyć usługi `DockerFile` i dodaj go do swojego projektu, wraz z kodu (node.js, .NET Core, itp.), lub, jeśli jesteś nowym użytkownikiem środowiska, spójrz na poniższe porady.</span><span class="sxs-lookup"><span data-stu-id="fde1e-158">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
>
> <span data-ttu-id="fde1e-159">Można użyć rozszerzenia platformy Docker, przeprowadzenie Cię w przypadku korzystania z `Dockerfile` i `docker-compose.yml` pliki związane z programem kontenerów Docker.</span><span class="sxs-lookup"><span data-stu-id="fde1e-159">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="fde1e-160">Po pewnym czasie prawdopodobnie napiszesz te rodzaje plików bez tego narzędzia, ale przy użyciu rozszerzenia platformy Docker jest dobry punkt wyjścia przyspieszy swoje nauki.</span><span class="sxs-lookup"><span data-stu-id="fde1e-160">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="fde1e-161">W rysunek 4 – 24, możesz zobaczyć jak docker-compose plik zostanie dodany przy użyciu rozszerzenia platformy Docker dla programu VS Code.</span><span class="sxs-lookup"><span data-stu-id="fde1e-161">In Figure 4-24, you can see how a docker-compose file is added by using the Docker Extension for VS Code.</span></span>

![Widok konsoli rozszerzenia platformy Docker dla programu VS Code.](./media/image24.png)

<span data-ttu-id="fde1e-163">**Rysunek 4-24**.</span><span class="sxs-lookup"><span data-stu-id="fde1e-163">**Figure 4-24**.</span></span> <span data-ttu-id="fde1e-164">Pliki docker dodać za pomocą **plików Dodaj Docker do polecenia obszaru roboczego**</span><span class="sxs-lookup"><span data-stu-id="fde1e-164">Docker files added using the **Add Docker files to Workspace command**</span></span>

<span data-ttu-id="fde1e-165">Po dodaniu pliku DockerFile, określ jaki podstawowego obrazu platformy Docker, należy używać (takimi jak wymaganie użycia `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span><span class="sxs-lookup"><span data-stu-id="fde1e-165">When you add a DockerFile, you specify what base Docker image you’ll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="fde1e-166">Zazwyczaj utworzysz obraz niestandardowy na podstawie obrazu podstawowego, który można pobrać z dowolnego oficjalne repozytorium na [rejestru usługi Docker Hub](https://hub.docker.com/) (takich jak [obrazu dla platformy .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) lub [dla środowiska Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="fde1e-166">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="fde1e-167">***Użyj istniejącego oficjalny obraz platformy Docker***</span><span class="sxs-lookup"><span data-stu-id="fde1e-167">***Use an existing official Docker image***</span></span>

<span data-ttu-id="fde1e-168">Za pomocą oficjalnego repozytorium stos języka z numerem wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym programowanie, testowanie i produkcja).</span><span class="sxs-lookup"><span data-stu-id="fde1e-168">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="fde1e-169">Poniżej przedstawiono przykładowy plik DockerFile dla kontenera platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="fde1e-169">The following is a sample DockerFile for a .NET Core container:</span></span>

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

<span data-ttu-id="fde1e-170">W tym przypadku obraz, który jest oparty na wersji 2.2 oficjalny obraz platformy Docker programu ASP.NET Core (wielu arch dla systemów Linux i Windows), zgodnie z wiersza `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="fde1e-170">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="fde1e-171">(Aby uzyskać więcej informacji na ten temat, zobacz [obrazu platformy Docker programu ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) strony i [obrazu platformy Docker programu .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) strony).</span><span class="sxs-lookup"><span data-stu-id="fde1e-171">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="fde1e-172">W pliku DockerFile można również poinstruować platformy Docker do nasłuchiwania na portach TCP, którego będziesz używać w czasie wykonywania (np. port 80).</span><span class="sxs-lookup"><span data-stu-id="fde1e-172">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80).</span></span>

<span data-ttu-id="fde1e-173">Można określić dodatkowe ustawienia konfiguracji w pliku Dockerfile, w zależności od języka i struktury, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="fde1e-173">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="fde1e-174">Na przykład `ENTRYPOINT` linia z `["dotnet", "MySingleContainerWebApp.dll"]` platformy docker, aby uruchomić aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fde1e-174">For instance, the `ENTRYPOINT` line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="fde1e-175">Jeśli używasz zestawu SDK oraz interfejsu wiersza polecenia platformy .NET Core (`dotnet CLI`) aby skompilować i uruchomić aplikację .NET, to ustawienie będzie inny.</span><span class="sxs-lookup"><span data-stu-id="fde1e-175">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="fde1e-176">Kluczowym punktem tutaj jest, że wiersz punktu wejścia i inne ustawienia zależą od języka i platformy, wybrany dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fde1e-176">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [! INFORMACJE O]
>
> <span data-ttu-id="fde1e-178">Aby uzyskać więcej informacji na temat Tworzenie obrazów platformy Docker dla aplikacji platformy .NET Core, przejdź do <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="fde1e-178">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="fde1e-179">Aby dowiedzieć się więcej o tworzeniu własnych obrazów, przejdź do <https://docs.docker.com/engine/tutorials/dockerimages/>.</span><span class="sxs-lookup"><span data-stu-id="fde1e-179">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="fde1e-180">**Użyj wielu architektury obrazu repozytoriów**</span><span class="sxs-lookup"><span data-stu-id="fde1e-180">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="fde1e-181">Nazwa pojedynczego obrazu w repozytorium może zawierać warianty platformy, takich jak obraz systemu Linux i Windows obraz.</span><span class="sxs-lookup"><span data-stu-id="fde1e-181">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="fde1e-182">Ta funkcja umożliwia dostawców, takich jak Microsoft (obraz podstawowy dla twórców) do utworzenia pojedynczego repozytorium na pokrycie wiele platform (oznacza to, Linux i Windows).</span><span class="sxs-lookup"><span data-stu-id="fde1e-182">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="fde1e-183">Na przykład [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repozytorium, które są dostępne w rejestrze usługi Docker Hub zapewnia obsługę dla systemów Linux i Windows Nano Server, korzystając z taką samą nazwę obrazu.</span><span class="sxs-lookup"><span data-stu-id="fde1e-183">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="fde1e-184">Ściąganie [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) obrazu z hosta Windows pobiera wariant Windows, natomiast ściągania taką samą nazwę obrazu na hoście z systemem Linux ściąga wariantów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="fde1e-184">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="fde1e-185">***Tworzenie obrazu podstawowego od podstaw***</span><span class="sxs-lookup"><span data-stu-id="fde1e-185">***Create your base image from scratch***</span></span>

<span data-ttu-id="fde1e-186">Można utworzyć własny obraz podstawowy platformy Docker od podstaw, zgodnie z opisem w tym [artykułu](https://docs.docker.com/engine/userguide/eng-image/baseimages/) docker.</span><span class="sxs-lookup"><span data-stu-id="fde1e-186">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="fde1e-187">Ten scenariusz jest prawdopodobnie nie najlepiej dla Ciebie, jeśli dopiero zaczynasz przy użyciu rozwiązania Docker, ale jeśli chcesz ustawić bity określonego obrazu podstawowego, możesz to zrobić.</span><span class="sxs-lookup"><span data-stu-id="fde1e-187">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="fde1e-188">Krok 3. Tworzenie niestandardowych obrazów platformy Docker osadzania usługi w nim</span><span class="sxs-lookup"><span data-stu-id="fde1e-188">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="fde1e-189">Dla każdej usługi niestandardowego, który składa się z aplikacji należy utworzyć obraz powiązane.</span><span class="sxs-lookup"><span data-stu-id="fde1e-189">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="fde1e-190">Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, musisz pojedynczego obrazu.</span><span class="sxs-lookup"><span data-stu-id="fde1e-190">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
>
> <span data-ttu-id="fde1e-191">Biorąc pod uwagę "zewnętrzna pętla DevOps przepływu pracy", obrazy zostanie utworzona przez zautomatyzowanego procesu kompilacji po każdym wypchnięciu kodu źródłowego do repozytorium Git (ciągła integracja), więc obrazy zostanie utworzony w tym środowisku globalnych z usługi Kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="fde1e-191">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="fde1e-192">Jednak zanim firma Microsoft uważa, przechodząc do tej trasy zewnętrzna pętla, musimy upewnić się, że aplikację platformy Docker faktycznie działa prawidłowo, aby nie mogą umieścić kod, który może nie działać poprawnie do systemu kontroli źródła (Git itp.).</span><span class="sxs-lookup"><span data-stu-id="fde1e-192">But before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="fde1e-193">W związku z tym Każdy deweloper musi najpierw celu cały proces wewnętrzny pętli do testowania lokalnie i kontynuować tworzenie, dopóki nie chcą wypchnąć pełne funkcji lub zmień wartość na system kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="fde1e-193">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="fde1e-194">Aby utworzyć obraz w środowisku lokalnym i za pomocą pliku DockerFile, można użyć polecenia kompilacji platformy docker, jak pokazano w rysunek 4-25 (możesz także uruchomić `docker-compose up --build` aplikacji poprzez wiele kontenerów/usług).</span><span class="sxs-lookup"><span data-stu-id="fde1e-194">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-25 (you also can run `docker-compose up --build` for applications composed by several containers/services).</span></span>

![Dane wyjściowe konsoli kompilacji docker-compose pokazywanie obrazów pobieranie w toku.](./media/image25.png)

<span data-ttu-id="fde1e-196">**Rysunek 4-25**.</span><span class="sxs-lookup"><span data-stu-id="fde1e-196">**Figure 4-25**.</span></span> <span data-ttu-id="fde1e-197">Uruchamianie kompilacji platformy docker</span><span class="sxs-lookup"><span data-stu-id="fde1e-197">Running docker build</span></span>

<span data-ttu-id="fde1e-198">Opcjonalnie, zamiast bezpośredniego uruchamiania `docker build` z folderu projektu, najpierw można wygenerować folderu do wdrożenia z bibliotekami .NET potrzebne przy użyciu opcji Uruchom `dotnet publish` polecenia, a następnie uruchom `docker build`.</span><span class="sxs-lookup"><span data-stu-id="fde1e-198">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="fde1e-199">W tym przykładzie tworzy obraz platformy Docker o nazwie `cesardl/netcore-webapi-microservice-docker:first` (`:first` jest tag, takich jak określonej wersji).</span><span class="sxs-lookup"><span data-stu-id="fde1e-199">This example creates a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first` (`:first` is a tag, like a specific version).</span></span> <span data-ttu-id="fde1e-200">Możesz wykonać ten krok dla każdego obrazu niestandardowego, potrzebne do utworzenia złożone aplikacji platformy Docker za pomocą wielu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="fde1e-200">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="fde1e-201">Można znaleźć istniejących obrazów w lokalnym repozytorium (komputerze deweloperskim) przy użyciu platformy docker polecenie obrazów, jak pokazano w rysunek 4-26.</span><span class="sxs-lookup"><span data-stu-id="fde1e-201">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-26.</span></span>

![Dane wyjściowe z polecenia obrazów platformy docker, wyświetlanie istniejących obrazów z konsoli.](./media/image26.png)

<span data-ttu-id="fde1e-203">**Rysunek 4-26**.</span><span class="sxs-lookup"><span data-stu-id="fde1e-203">**Figure 4-26**.</span></span> <span data-ttu-id="fde1e-204">Wyświetlanie istniejących obrazów przy użyciu obrazów platformy docker</span><span class="sxs-lookup"><span data-stu-id="fde1e-204">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="fde1e-205">Krok 4. Zdefiniuj swoje usługi w docker-compose.yml, podczas kompilowania złożone aplikacji platformy Docker z wieloma usługami</span><span class="sxs-lookup"><span data-stu-id="fde1e-205">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="fde1e-206">Za pomocą `docker-compose.yml` pliku, można zdefiniować zestaw powiązanych usług, który można wdrożyć jako złożone aplikacji za pomocą poleceń wdrażania opisano w następnej sekcji krok.</span><span class="sxs-lookup"><span data-stu-id="fde1e-206">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="fde1e-207">Tworzenie tego pliku w głównego lub główny folder rozwiązania; powinien być podobny do przedstawionego w tym zawartości `docker-compose.yml` pliku:</span><span class="sxs-lookup"><span data-stu-id="fde1e-207">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

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

<span data-ttu-id="fde1e-208">W tym konkretnym przypadku ten plik definiuje dwie usługi: Usługa sieci web (usługa niestandardowa) i usługa redis (usługa popularnej pamięci podręcznej).</span><span class="sxs-lookup"><span data-stu-id="fde1e-208">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="fde1e-209">Każda usługa zostanie wdrożony jako kontener, dlatego musimy użyć konkretnego obrazu platformy Docker dla każdego.</span><span class="sxs-lookup"><span data-stu-id="fde1e-209">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="fde1e-210">Dla tej usługi sieci web określonego obrazu należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fde1e-210">For this particular web service, the image will need to do the following:</span></span>

- <span data-ttu-id="fde1e-211">Twórz z pliku DockerFile w bieżącym katalogu</span><span class="sxs-lookup"><span data-stu-id="fde1e-211">Build from the DockerFile in the current directory</span></span>

- <span data-ttu-id="fde1e-212">Przekazuj narażonych port 80 w kontenerze na porcie 81 na komputerze hosta</span><span class="sxs-lookup"><span data-stu-id="fde1e-212">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

- <span data-ttu-id="fde1e-213">Zainstaluj w katalogu projektu na hoście/Code w kontenerze, dzięki czemu można zmodyfikować kod bez konieczności ponownego kompilowania obrazu</span><span class="sxs-lookup"><span data-stu-id="fde1e-213">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

- <span data-ttu-id="fde1e-214">Połączenia usługi sieci web z usługą redis Cache</span><span class="sxs-lookup"><span data-stu-id="fde1e-214">Link the web service to the redis service</span></span>

<span data-ttu-id="fde1e-215">Używa usługi redis [najnowszego obrazu publicznego redis](https://hub.docker.com/_/redis/) pobierane z rejestru usługi Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="fde1e-215">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="fde1e-216">[redis](https://redis.io/) to system popularnej pamięci podręcznej dla aplikacji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="fde1e-216">[redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="fde1e-217">Krok 5. Kompilowanie i uruchamianie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fde1e-217">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="fde1e-218">Jeśli aplikacja ma tylko jeden kontener, wystarczy uruchomić go przez wdrożenie jej do hosta platformy Docker (maszyny Wirtualnej lub serwera fizycznego).</span><span class="sxs-lookup"><span data-stu-id="fde1e-218">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="fde1e-219">Jednak jeśli Twoja aplikacja składa się z wielu usług, musisz *została utworzona*również.</span><span class="sxs-lookup"><span data-stu-id="fde1e-219">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="fde1e-220">Teraz widzieć różne opcje.</span><span class="sxs-lookup"><span data-stu-id="fde1e-220">Let's see the different options.</span></span>

<span data-ttu-id="fde1e-221">***Opcja A: Uruchom jeden kontener lub usługi***</span><span class="sxs-lookup"><span data-stu-id="fde1e-221">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="fde1e-222">Obraz platformy Docker można uruchomić przy użyciu platformy docker, uruchom polecenie, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="fde1e-222">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="fde1e-223">Dla tego konkretnego wdrożenia firma Microsoft będzie można Przekierowywanie żądań wysyłanych do portu 80 na port wewnętrzny 5000.</span><span class="sxs-lookup"><span data-stu-id="fde1e-223">For this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="fde1e-224">Teraz aplikacja nasłuchuje na porcie zewnętrznym 80 na poziomie hosta.</span><span class="sxs-lookup"><span data-stu-id="fde1e-224">Now the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="fde1e-225">***Opcja B: Tworzenie i uruchamianie aplikacji wielu kontenerów***</span><span class="sxs-lookup"><span data-stu-id="fde1e-225">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="fde1e-226">W większości przypadków enterprise aplikację platformy Docker składać się z wielu usług.</span><span class="sxs-lookup"><span data-stu-id="fde1e-226">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="fde1e-227">W takich przypadkach można uruchomić `docker-compose up` polecenia (rysunek 4-27), który będzie używany plik docker-compose.yml, które zostały utworzone wcześniej.</span><span class="sxs-lookup"><span data-stu-id="fde1e-227">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="fde1e-228">Uruchomienie tego polecenia wdraża złożone aplikacji ze wszystkimi jego powiązane kontenerów.</span><span class="sxs-lookup"><span data-stu-id="fde1e-228">Running this command deploys a composed application with all of its related containers.</span></span>

![Dane wyjściowe z konsoli narzędzia docker compose się polecenia.](./media/image27.png)

<span data-ttu-id="fde1e-230">**Rysunek 4-27**.</span><span class="sxs-lookup"><span data-stu-id="fde1e-230">**Figure 4-27**.</span></span> <span data-ttu-id="fde1e-231">Wyniki polecenia "docker-compose up"</span><span class="sxs-lookup"><span data-stu-id="fde1e-231">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="fde1e-232">Po uruchomieniu `docker-compose up`, wdrażania aplikacji i jej powiązane kontenerów w hoście platformy Docker, jak pokazano w rysunek 4-28 w reprezentacji maszyny Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="fde1e-232">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![Maszyny Wirtualnej z systemem wielokontenerowych aplikacji.](./media/image28.png)

<span data-ttu-id="fde1e-234">**Rysunek 4-28**.</span><span class="sxs-lookup"><span data-stu-id="fde1e-234">**Figure 4-28**.</span></span> <span data-ttu-id="fde1e-235">Maszyny Wirtualnej przy użyciu kontenerów Docker wdrożonych</span><span class="sxs-lookup"><span data-stu-id="fde1e-235">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="fde1e-236">Krok 6. Testowanie aplikacji platformy Docker (lokalnie, w swojej lokalnej maszyny Wirtualnej dysku CD)</span><span class="sxs-lookup"><span data-stu-id="fde1e-236">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="fde1e-237">W tym kroku różnią się w zależności od tego, jakie działania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fde1e-237">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="fde1e-238">W prostych platformy .NET Core interfejsu API sieci Web "Hello World" wdrażane jako pojedynczy kontener lub usługi czy wystarczy dostęp do usługi, zapewniając portu TCP, określone w pliku DockerFile.</span><span class="sxs-lookup"><span data-stu-id="fde1e-238">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="fde1e-239">Jeśli host lokalny nie jest włączony, aby przejść do swojej usługi, należy znaleźć adres IP dla maszyny, za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="fde1e-239">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

<span data-ttu-id="fde1e-240">Na hoście platformy Docker Otwórz przeglądarkę i przejdź do tej lokacji; Twoja aplikacja/Usługa jest uruchomiona, powinien zostać wyświetlony, jak pokazano w rysunek 4-29.</span><span class="sxs-lookup"><span data-stu-id="fde1e-240">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Widok w przeglądarce odpowiedź z localhost/API/wartości.](./media/image29.png)

<span data-ttu-id="fde1e-242">**Rysunek 4-29**.</span><span class="sxs-lookup"><span data-stu-id="fde1e-242">**Figure 4-29**.</span></span> <span data-ttu-id="fde1e-243">Testowanie aplikacji platformy Docker lokalnie przy użyciu localhost</span><span class="sxs-lookup"><span data-stu-id="fde1e-243">Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="fde1e-244">Pamiętaj, że jest ona przy użyciu portu 80, ale wewnętrznie jest nastąpi przekierowanie do portu 5000, ponieważ jest to, jak została ona wdrożona na `docker run`, jak wyjaśniono wcześniej.</span><span class="sxs-lookup"><span data-stu-id="fde1e-244">Note that it's using port 80, but internally it's being redirected to port 5000, because that's how it was deployed with `docker run`, as explained earlier.</span></span>

<span data-ttu-id="fde1e-245">Można to sprawdzić, używając programu CURL z poziomu terminalu.</span><span class="sxs-lookup"><span data-stu-id="fde1e-245">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="fde1e-246">W przypadku instalacji platformy Docker na Windows domyślny adres IP jest 10.0.75.1, jak pokazano w rysunek 4-30.</span><span class="sxs-lookup"><span data-stu-id="fde1e-246">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-30.</span></span>

![Pobieranie danych wyjściowych konsoli http://10.0.75.1/API/values za pomocą programu curl](./media/image30.png)

<span data-ttu-id="fde1e-248">**Rysunek 4-30**.</span><span class="sxs-lookup"><span data-stu-id="fde1e-248">**Figure 4-30**.</span></span> <span data-ttu-id="fde1e-249">Testowanie aplikacji platformy Docker lokalnie, używając programu CURL</span><span class="sxs-lookup"><span data-stu-id="fde1e-249">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="fde1e-250">**Debugowanie kontenera uruchomionego w platformy Docker**</span><span class="sxs-lookup"><span data-stu-id="fde1e-250">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="fde1e-251">Jeśli używasz środowiska Node.js i innych platform, takich jak kontenery platformy .NET Core, programu Visual Studio Code obsługuje debugowania platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="fde1e-251">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="fde1e-252">Możesz również debugować platformy .NET Core lub .NET Framework w kontenerach na platformie Docker podczas korzystania z programu Visual Studio for Windows lub Mac, zgodnie z opisem w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="fde1e-252">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [! INFORMACJE O]
>
> <span data-ttu-id="fde1e-254">Aby dowiedzieć się więcej o debugowaniu w kontenerach platformy Docker w środowisku Node.js, przejdź do <https://blog.docker.com/2016/07/live-debugging-docker/> i <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.</span><span class="sxs-lookup"><span data-stu-id="fde1e-254">To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fde1e-255">[Poprzednie](docker-apps-development-environment.md)
>[dalej](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="fde1e-255">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
