---
title: Przepływ pracy wewnętrznej pętli tworzenia aplikacji platformy Docker
description: Dowiedz się więcej "wewnętrzną pętlę" przepływu pracy dla opracowywania aplikacji platformy Docker.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 03eb4662e55551678105fa9ef25b42cc05c132a5
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219091"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="b135b-103">Przepływ pracy wewnętrznej pętli tworzenia aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="b135b-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="b135b-104">Przed wyzwoleniem zewnętrzna Pętla przepływu pracy, obejmujące cały DevOps cyklu, rozpoczyna na każdy Deweloper maszynie kodowania samej aplikacji, za pomocą swojego preferowanego języków lub platform i testowanie jej lokalnie (rysunek 4 – 14).</span><span class="sxs-lookup"><span data-stu-id="b135b-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-14).</span></span> <span data-ttu-id="b135b-105">Ale w każdym przypadku konieczne będzie bardzo ważna kwestia, niezależnie od tego, jaki język, struktury lub platform wybierz.</span><span class="sxs-lookup"><span data-stu-id="b135b-105">But in every case, you will have a very important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="b135b-106">W tym określonego przepływu pracy są zawsze tworzenia i testowania kontenerów platformy Docker, ale lokalnie.</span><span class="sxs-lookup"><span data-stu-id="b135b-106">In this specific workflow, you are always developing and testing Docker containers, but locally.</span></span>

![](./media/image18.png)

<span data-ttu-id="b135b-107">Rysunek 4 – 14: Kontekst wewnętrznej pętli tworzenia kodu</span><span class="sxs-lookup"><span data-stu-id="b135b-107">Figure 4-14: Inner-loop development context</span></span>

<span data-ttu-id="b135b-108">Kontener lub wystąpienia obrazu platformy Docker będzie zawierać tych składników:</span><span class="sxs-lookup"><span data-stu-id="b135b-108">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="b135b-109">Wybór systemu operacyjnego (na przykład dystrybucji systemu Linux lub Windows)</span><span class="sxs-lookup"><span data-stu-id="b135b-109">An operating system selection (for example, a Linux distribution or Windows)</span></span>

-   <span data-ttu-id="b135b-110">Pliki dodawane przez dewelopera (na przykład pliki binarne aplikacji)</span><span class="sxs-lookup"><span data-stu-id="b135b-110">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="b135b-111">Konfiguracja (na przykład ustawienia środowiska i zależności)</span><span class="sxs-lookup"><span data-stu-id="b135b-111">Configuration (for example, environment settings and dependencies)</span></span>

-   <span data-ttu-id="b135b-112">Instrukcje dotyczące jakie procesy do uruchomione przez platformy Docker</span><span class="sxs-lookup"><span data-stu-id="b135b-112">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="b135b-113">Możesz skonfigurować przepływ pracy wewnętrznej pętli tworzenia kodu, który korzysta z platformy Docker jako proces (opisany w następnej sekcji).</span><span class="sxs-lookup"><span data-stu-id="b135b-113">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="b135b-114">Weź pod uwagę początkowe kroki, aby skonfigurować środowisko nie jest uwzględniony, ponieważ trzeba to zrobić tylko raz.</span><span class="sxs-lookup"><span data-stu-id="b135b-114">Take into account that the initial steps to set up the environment is not included, because you need to do that just once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="b135b-115">Tworzenie pojedynczej aplikacji w kontenerze platformy Docker przy użyciu programu Visual Studio Code i interfejsu wiersza polecenia platformy Docker</span><span class="sxs-lookup"><span data-stu-id="b135b-115">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="b135b-116">Aplikacje składają się z własnych usług, a także dodatkowe biblioteki (zależności).</span><span class="sxs-lookup"><span data-stu-id="b135b-116">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="b135b-117">Rysunek 4 – 15 przedstawiono podstawowe kroki, które zazwyczaj trzeba przeprowadzić podczas kompilowania aplikacji platformy Docker, następuje szczegółowy opis każdego kroku.</span><span class="sxs-lookup"><span data-stu-id="b135b-117">Figure 4-15 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![](./media/image19.png)

<span data-ttu-id="b135b-118">Rysunek 4 — 15: Ogólny przepływ pracy dla cyklu życia aplikacji kontenerowych nimi platformy Docker za pomocą interfejsu wiersza polecenia platformy Docker</span><span class="sxs-lookup"><span data-stu-id="b135b-118">Figure 4-15: High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="b135b-119">Krok 1. Rozpocznij kodowanie w programie Visual Studio Code i utworzyć linię bazową początkową aplikacji/usługi</span><span class="sxs-lookup"><span data-stu-id="b135b-119">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="b135b-120">Sposób tworzenia aplikacji jest bardzo podobny sposób, co można zrobić bez platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="b135b-120">The way you develop your application is pretty similar to the way you do it without Docker.</span></span> <span data-ttu-id="b135b-121">Różnica jest, że podczas tworzenia, są wdrażanie i testowanie aplikacji lub usług działających w kontenerach platformy Docker, umieszczone w środowisku lokalnym (np. maszyny Wirtualnej systemu Linux lub Windows).</span><span class="sxs-lookup"><span data-stu-id="b135b-121">The difference is that while developing, you are deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="b135b-122">**Konfigurowanie środowiska lokalnego**</span><span class="sxs-lookup"><span data-stu-id="b135b-122">**Setting up your local environment**</span></span>

<span data-ttu-id="b135b-123">Najnowsze wersje platformy Docker dla systemów Mac i Windows jest łatwiejsze niż kiedykolwiek do tworzenia aplikacji platformy Docker i konfiguracja jest prosta.</span><span class="sxs-lookup"><span data-stu-id="b135b-123">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

<span data-ttu-id="b135b-124">**Więcej informacji o** Aby uzyskać instrukcje na temat konfigurowania Docker for Windows, przejdź do [ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="b135b-124">**More info** For instructions on setting up Docker for Windows, go to [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).</span></span>

<span data-ttu-id="b135b-125">Aby uzyskać instrukcje na temat konfigurowania platformy Docker dla komputerów Mac, przejdź do <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="b135b-125">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="b135b-126">Ponadto należy Edytor kodu, aby faktycznie można opracować aplikację przy użyciu interfejsu wiersza polecenia platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="b135b-126">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="b135b-127">Firma Microsoft udostępnia programu Visual Studio Code, czyli lekkiemu edytorowi kodu, która jest obsługiwana na komputerach Mac, Windows i Linux, oferuje funkcję IntelliSense za pomocą [Obsługa wielu języków](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python i większość nowoczesnych języków), [debugowania](https://code.visualstudio.com/Docs/editor/debugging), [integracji z usługą Git](https://code.visualstudio.com/Docs/editor/versioncontrol) i [Obsługa rozszerzeń](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="b135b-127">Microsoft provides Visual Studio Code, which is a lightweight code editor that is supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="b135b-128">Ten edytor to doskonałe rozwiązanie dla deweloperów systemów Mac i Linux.</span><span class="sxs-lookup"><span data-stu-id="b135b-128">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="b135b-129">W Windows możesz również można użyć pełnej aplikacji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b135b-129">In Windows, you also can use the full Visual Studio application.</span></span>

<span data-ttu-id="b135b-130">**Więcej informacji o** Aby uzyskać instrukcje na temat instalowania programu Visual Studio for Windows, Mac lub Linux, przejdź do <https://code.visualstudio.com/docs/setup/setup-overview/>.</span><span class="sxs-lookup"><span data-stu-id="b135b-130">**More info** For instructions on installing Visual Studio for Windows, Mac, or Linux, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>

<span data-ttu-id="b135b-131">Można pracować z interfejsem wiersza polecenia platformy Docker i pisanie kodu za pomocą dowolnego edytora kodu, ale jeśli używasz programu Visual Studio Code, jego sprawia, że ułatwiają tworzenie pliku Dockerfile i pliki docker-compose.yml w obszarze roboczym.</span><span class="sxs-lookup"><span data-stu-id="b135b-131">You can work with Docker CLI and write your code using any code editor, but if you use Visual Studio Code, it makes it easy to author Dockerfile and docker-compose.yml files in your workspace.</span></span> <span data-ttu-id="b135b-132">Ponadto można uruchamiać zadania programu Visual Studio Code z poziomu środowiska IDE, które wyświetli monit o skrypty, które mogą działać rozwinięciem operacje, przy użyciu interfejsu wiersza polecenia Docker poniżej.</span><span class="sxs-lookup"><span data-stu-id="b135b-132">Plus, you can run Visual Studio Code tasks from the IDE that will prompt scripts that can be running elaborated operations using Docker CLI underneath.</span></span>

<span data-ttu-id="b135b-133">Visual Studio Code jest zapewniana przez rozszerzenie, należy zainstalować.</span><span class="sxs-lookup"><span data-stu-id="b135b-133">Visual Studio Code is provided by an extension, which you'll need to install.</span></span> <span data-ttu-id="b135b-134">Aby to zrobić, naciśnij klawisze Ctrl + Shift + P, wpisz **zainstalować ext**, a następnie uruchomić rozszerzenia: Zainstaluj rozszerzenie polecenie, aby wyświetlić listę rozszerzeń witryny Marketplace.</span><span class="sxs-lookup"><span data-stu-id="b135b-134">To do so, Press Ctrl+Shift+P, type **ext install**, and then run the Extensions: Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="b135b-135">Następnie wpisz **docker** do filtrowania wyników, a następnie wybierz plik Dockerfile i pliku platformy Docker Compose (yml) rozszerzenia pomocy technicznej, jak pokazano w rysunek 4 – 16.</span><span class="sxs-lookup"><span data-stu-id="b135b-135">Next, type **docker** to filter the results, and then select the Dockerfile And Docker Compose File (yml) Support extension, as depicted in Figure 4-16.</span></span>

![](./media/image20.png)

<span data-ttu-id="b135b-136">Rysunek 4 – 16: Instalowanie rozszerzenia platformy Docker w programie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b135b-136">Figure 4-16: Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="b135b-137">Krok 2. Tworzenie pliku DockerFile związane z istniejącego obrazu (zwykły system operacyjny lub środowiskach deweloperskich, takich jak .NET Core, Node.js i Ruby)</span><span class="sxs-lookup"><span data-stu-id="b135b-137">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="b135b-138">Potrzebny będzie plik DockerFile według obrazu niestandardowego do zbudowania i kontenera do wdrożenia, w związku z tym, jeśli aplikacja składa się z jednej usługi niestandardowych, konieczne będzie pojedynczego pliku DockerFile.</span><span class="sxs-lookup"><span data-stu-id="b135b-138">You will need a DockerFile per custom image to be built and per container to be deployed, therefore, if your app is made up of a single custom service, you will need a single DockerFile.</span></span> <span data-ttu-id="b135b-139">Ale jeśli aplikacja składa się z wielu usług (tak jak w architekturze mikrousług), musisz mieć jeden plik Dockerfile na usługę.</span><span class="sxs-lookup"><span data-stu-id="b135b-139">But, if your app is composed of multiple services (as in a microservices architecture), you'll need one Dockerfile per service.</span></span>

<span data-ttu-id="b135b-140">Plik DockerFile znajduje się zwykle w folderze głównym aplikacji lub usługi i zawiera wymagane polecenia, tak że platforma Docker wie, jak skonfigurować i uruchomić tej aplikacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="b135b-140">The DockerFile is usually placed within the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="b135b-141">Można tworzyć z pliku DockerFile i dodać go do projektu, wraz z kodu (.NET Core, node.js itp.), lub, jeśli jesteś nowym użytkownikiem środowiska, spójrz na poniższe porady.</span><span class="sxs-lookup"><span data-stu-id="b135b-141">You can create your DockerFile and add it to your project along with your code (node.js, .NET Core, etc.), or, if you are new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="b135b-142">Można użyć narzędzia wiersza polecenia o nazwie [yo docker](https://github.com/Microsoft/generator-docker), który szkielety mechanizmów pliki z projektu w języku, wybierz i dodaje wymagane pliki konfiguracji platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="b135b-142">You can use a command-line tool called [yo docker](https://github.com/Microsoft/generator-docker), which scaffolds files from your project in the language you choose and adds the required Docker configuration files.</span></span> <span data-ttu-id="b135b-143">Zasadniczo, aby ułatwić deweloperów rozpoczynających pracę, tworzy odpowiedni plik DockerFile, docker-compose.yml i inne skojarzone skrypty, aby skompilować i uruchomić kontenerów Docker.</span><span class="sxs-lookup"><span data-stu-id="b135b-143">Basically, to assist developers getting started, it creates the appropriate DockerFile, docker-compose.yml, and other associated scripts to build and run your Docker containers.</span></span> <span data-ttu-id="b135b-144">Tego generatora yeoman wyświetli monit o na kilka pytań, pytaniem hosta tworzenia wybranego języka i docelowy kontener.</span><span class="sxs-lookup"><span data-stu-id="b135b-144">This yeoman generator will prompt you with a few questions, asking your selected development language and destination container host.</span></span>

![yo platformy docker](./media/image21.png)

<span data-ttu-id="b135b-146">Na przykład rysunek 4-17 pokazuje dwa zrzuty ekranu z terminali w Windows i na komputerze Mac, w obu przypadkach uruchamianie yo platformy docker, która spowoduje wygenerowanie przykładowych projektów kodu (obecnie platformy .NET Core, języka Golang i Node.js jako obsługiwanych języków) już skonfigurowany do pracy początku platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="b135b-146">For instance, Figure 4-17 shows two screenshots from the terminals in Windows and on a Mac, in both cases, running yo docker, which will generate the sample code projects (currently .NET Core, Golang, and Node.js as supported languages) already configured to work on top of Docker.</span></span>

![](./media/image22.PNG)  ![](./media/image23.png)

<span data-ttu-id="b135b-147">Rysunek 4-17: yo platformy docker narzędzia polecenia w Windows (po lewej) i na komputerze Mac</span><span class="sxs-lookup"><span data-stu-id="b135b-147">Figure 4-17: yo docker command tool in Windows (left) and on a Mac</span></span>

<span data-ttu-id="b135b-148">Rysunek 4-18 stanowi przykład za pomocą yo platformy docker po utworzeniu istniejącego projektu platformy .NET Core w miejscu, aby być szkielet.</span><span class="sxs-lookup"><span data-stu-id="b135b-148">Figure 4-18 presents an example using yo docker after you have an existing .NET Core project in place to be scaffolded.</span></span>

![](./media/image24.PNG)

<span data-ttu-id="b135b-149">Rysunek 4 — 18: yo platformy docker przy użyciu istniejącej platformy .NET Core projektu w miejscu</span><span class="sxs-lookup"><span data-stu-id="b135b-149">Figure 4-18: yo docker with an existing .NET Core project in place</span></span>

<span data-ttu-id="b135b-150">Z pliku DockerFile należy określić, jakie podstawowego obrazu platformy Docker, który ma być używany (np. przy użyciu "od microsoft/dotnet:1.0.0-core").</span><span class="sxs-lookup"><span data-stu-id="b135b-150">From the DockerFile, you specify what base Docker image you'll be using (like using "FROM microsoft/dotnet:1.0.0-core").</span></span> <span data-ttu-id="b135b-151">Zazwyczaj utworzysz obraz niestandardowy na podstawie podstawowy obraz, który można uzyskać z dowolnego oficjalne repozytorium na [rejestru usługi Docker Hub](https://hub.docker.com/) (takich jak [obrazu dla platformy .NET Core](https://hub.docker.com/r/microsoft/dotnet/) lub jeden [dla środowiska Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="b135b-151">You usually will build your custom image on top of a base image that you can get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/r/microsoft/dotnet/) or one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="b135b-152">***Opcja A: Użyj istniejącego oficjalny obraz platformy Docker***</span><span class="sxs-lookup"><span data-stu-id="b135b-152">***Option A: Use an existing official Docker image***</span></span>

<span data-ttu-id="b135b-153">Za pomocą oficjalnego repozytorium stos języka z numerem wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym programowanie, testowanie i produkcja).</span><span class="sxs-lookup"><span data-stu-id="b135b-153">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="b135b-154">Poniżej przedstawiono przykładowy plik DockerFile dla kontenera platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="b135b-154">Following is a sample DockerFile for a .NET Core container:</span></span>

```
# Base Docker image to use
FROM microsoft/aspnetcore:1.0.1\

# Set the Working Directory and files to be copied to the image
ARG source
WORKDIR /app
COPY ${source:-bin/Release/PublishOutput} .

# Configure the listening port to 80 (Internal/Secured port within Docker host)
EXPOSE 80

# Application entry point
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="b135b-155">W tym przypadku wykorzystywana jest wersja 1.0.1 oficjalny obraz platformy Docker programu ASP.NET Core dla systemu Linux o nazwie microsoft/aspnetcore:1.0.1.</span><span class="sxs-lookup"><span data-stu-id="b135b-155">In this case, it is using the version 1.0.1 of the official ASP.NET Core Docker image for Linux named microsoft/aspnetcore:1.0.1.</span></span> <span data-ttu-id="b135b-156">Aby uzyskać więcej informacji, zapoznaj się z [strony obrazu platformy Docker programu ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) i [strony obrazu platformy Docker programu .NET Core](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="b135b-156">For further details, consult the [ASP.NET Core Docker Image page](https://hub.docker.com/r/microsoft/aspnetcore/) and the [.NET Core Docker Image page](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="b135b-157">Możesz również mogą korzystać z innego obrazu porównywalne, np. węzeł: 4-onbuild dla środowiska Node.js i wiele innych wstępnie skonfigurowanych obrazów dla języków programowania, które są dostępne pod adresem [usługi Docker Hub](https://hub.docker.com/explore/).</span><span class="sxs-lookup"><span data-stu-id="b135b-157">You also could be using another comparable image like node:4-onbuild for Node.js, or many other preconfigured images for development languages, which are available at [Docker Hub](https://hub.docker.com/explore/).</span></span>

<span data-ttu-id="b135b-158">W pliku DockerFile trzeba będzie również poinstruować platformy Docker do nasłuchiwania na portach TCP, która będzie używana w czasie wykonywania (np. port 80).</span><span class="sxs-lookup"><span data-stu-id="b135b-158">In the DockerFile, you also need to instruct Docker to listen to the TCP port that you will use at runtime (such as port 80).</span></span>

<span data-ttu-id="b135b-159">Istnieją inne wiersze konfiguracji, którą można dodać w pliku DockerFile w zależności od języka/platformy, którego używasz, dzięki czemu Docker wie, jak uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b135b-159">There are other lines of configuration that you can add in the DockerFile depending on the language/framework you are using, so Docker knows how to run the app.</span></span> <span data-ttu-id="b135b-160">Na przykład, potrzebny jest wiersz punktu wejścia przy użyciu \["dotnet", "MyCustomMicroservice.dll"\] do uruchamiania aplikacji .NET Core, chociaż może mieć wiele wariantów w zależności od podejście do kompilowania i uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="b135b-160">For instance, you need the ENTRYPOINT line with \["dotnet", "MyCustomMicroservice.dll"\] to run a .NET Core app, although you can have multiple variants depending on the approach to build and run your service.</span></span> <span data-ttu-id="b135b-161">Jeśli używasz zestawu SDK i interfejsu wiersza polecenia platformy dotnet do kompilowania i uruchamiania aplikacji .NET może być nieco inne.</span><span class="sxs-lookup"><span data-stu-id="b135b-161">If you're using the SDK and dotnet CLI to build and run the .NET app, it would be slightly different.</span></span> <span data-ttu-id="b135b-162">Mierzenie to, że wiersz punktu wejścia, a także dodatkowe wiersze będą różnić w zależności od języka/platformy, na której możesz wybrać dla swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b135b-162">The bottom line is that the ENTRYPOINT line plus additional lines will be different depending on the language/platform you choose for your application.</span></span>

<span data-ttu-id="b135b-163">**Więcej informacji o** uzyskać informacji na temat Tworzenie obrazów platformy Docker dla aplikacji platformy .NET Core, przejdź do <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="b135b-163">**More info** For information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>

<span data-ttu-id="b135b-164">Aby dowiedzieć się więcej o tworzeniu własnych obrazów, przejdź do [ https://docs.docker.com/engine/\ samouczki/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span><span class="sxs-lookup"><span data-stu-id="b135b-164">To learn more about building your own images, go to [https://docs.docker.com/engine/\ tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span></span>

<span data-ttu-id="b135b-165">**Repozytoria obrazu dla wielu platform**</span><span class="sxs-lookup"><span data-stu-id="b135b-165">**Multiplatform image repositories**</span></span>

<span data-ttu-id="b135b-166">W miarę koncentruje się kontenery Windows jednym repozytorium może zawierać warianty platformy, takich jak obraz systemu Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="b135b-166">As Windows containers become more prevalent, a single repository can contain platform variants, such as a Linux and Windows image.</span></span> <span data-ttu-id="b135b-167">Jest to nowa funkcja dostępna na platformie Docker, który umożliwia dostawcom obejmują wiele platform, takich jak za pomocą pojedynczego repozytorium na [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repozytorium, która jest dostępna w witrynie DockerHub rejestru.</span><span class="sxs-lookup"><span data-stu-id="b135b-167">This is a new feature coming in Docker that makes it possible for vendors to use a single repository to cover multiple platforms, such as [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repository, which is available at DockerHub registry.</span></span> <span data-ttu-id="b135b-168">Jak funkcja nabierają życia, ściągając ten obraz z hosta Windows będzie pobierać wariant Windows, natomiast ściągania taką samą nazwę obrazu na hoście z systemem Linux każda będzie ściągać wariantów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="b135b-168">As the feature comes alive, pulling this image from a Windows host will pull the Windows variant, whereas pulling the same image name from a Linux host will pull the Linux variant.</span></span>

<span data-ttu-id="b135b-169">***Opcja B: Tworzenie obrazu podstawowego od podstaw***</span><span class="sxs-lookup"><span data-stu-id="b135b-169">***Option B: Create your base image from scratch***</span></span>

<span data-ttu-id="b135b-170">Można utworzyć własny obraz podstawowy platformy Docker od podstaw, zgodnie z opisem w tym [artykułu](https://docs.docker.com/engine/userguide/eng-image/baseimages/) docker.</span><span class="sxs-lookup"><span data-stu-id="b135b-170">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="b135b-171">Jest to scenariusz, który prawdopodobnie nie jest najlepszym rozwiązaniem dla Ciebie, jeśli po prostu rozpoczynasz korzystanie z platformy Docker, ale jeśli chcesz ustawić bity określonego obrazu podstawowego, możesz to zrobić.</span><span class="sxs-lookup"><span data-stu-id="b135b-171">This is a scenario that is probably not best for you if you are just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="b135b-172">Krok 3. Tworzenie niestandardowych obrazów platformy Docker osadzania usługi w nim</span><span class="sxs-lookup"><span data-stu-id="b135b-172">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="b135b-173">Dla każdej usługi niestandardowego, który składa się z aplikacji należy utworzyć obraz powiązane.</span><span class="sxs-lookup"><span data-stu-id="b135b-173">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="b135b-174">Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, musisz pojedynczego obrazu.</span><span class="sxs-lookup"><span data-stu-id="b135b-174">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="b135b-175">Biorąc pod uwagę "zewnętrzna pętla DevOps przepływu pracy", obrazy zostanie utworzona przez zautomatyzowanego procesu kompilacji po każdym wypchnięciu kodu źródłowego do repozytorium Git (ciągła integracja), więc obrazy zostanie utworzony w tym środowisku globalnych z usługi Kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="b135b-175">When taking into account the "outer-loop DevOps workflow," the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration) so the images will be created in that global environment from your source code.</span></span>

<span data-ttu-id="b135b-176">Jednak zanim firma Microsoft uważa, przechodząc do tej trasy zewnętrzna pętla, musimy upewnić się, że aplikację platformy Docker faktycznie działa prawidłowo, aby nie mogą umieścić kod, który może nie działać poprawnie do systemu kontroli źródła (Git itp.).</span><span class="sxs-lookup"><span data-stu-id="b135b-176">But, before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>

<span data-ttu-id="b135b-177">W związku z tym Każdy deweloper musi najpierw celu cały proces wewnętrzny pętli do testowania lokalnie i kontynuować tworzenie, dopóki nie chcą wypchnąć pełne funkcji lub zmień wartość na system kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="b135b-177">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="b135b-178">Aby utworzyć obraz w środowisku lokalnym i za pomocą pliku DockerFile, można użyć polecenia kompilacji platformy docker, jak pokazano w rysunek 4-19 (możesz również uruchomić narzędzia docker compose — tworzenie aplikacji poprzez wiele kontenerów/usług).</span><span class="sxs-lookup"><span data-stu-id="b135b-178">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-19 (you also can run docker-compose up --build for applications composed by several containers/services).</span></span>

![](./media/image25.png)

<span data-ttu-id="b135b-179">Rysunek 4 — 19: Uruchamianie kompilacji platformy docker</span><span class="sxs-lookup"><span data-stu-id="b135b-179">Figure 4-19: Running docker build</span></span>

<span data-ttu-id="b135b-180">Opcjonalnie, zamiast bezpośredniego uruchamiania docker kompilacji z folderu projektu, można najpierw wygenerować folderu do wdrożenia z bibliotekami .NET potrzebne przy użyciu dotnet wykonywania polecenia publikowania, a następnie uruchom kompilacji platformy docker.</span><span class="sxs-lookup"><span data-stu-id="b135b-180">Optionally, instead of directly running docker build from the project's folder, you first can generate a deployable folder with the .NET libraries needed by using the run dotnet publish command, and then run docker build.</span></span>

<span data-ttu-id="b135b-181">W tym przykładzie, spowoduje to utworzenie obrazu platformy Docker przy użyciu nazwy cesardl/netcore-webapi mikrousługi — docker: pierwszy (: najpierw jest tag, takich jak określonej wersji).</span><span class="sxs-lookup"><span data-stu-id="b135b-181">In this example, this creates a Docker image with the name cesardl/netcore-webapi-microservice-docker:first (:first is a tag, like a specific version).</span></span> <span data-ttu-id="b135b-182">Możesz wykonać ten krok dla każdego obrazu niestandardowego, potrzebne do utworzenia złożone aplikacji platformy Docker za pomocą wielu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="b135b-182">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="b135b-183">Można znaleźć istniejących obrazów w lokalnym repozytorium (komputerze deweloperskim) przy użyciu platformy docker polecenie obrazów, jak pokazano w rysunek 4-20.</span><span class="sxs-lookup"><span data-stu-id="b135b-183">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-20.</span></span>

![](./media/image26.png)

<span data-ttu-id="b135b-184">Rysunek 4-20: Wyświetlanie istniejących obrazów przy użyciu obrazów platformy docker</span><span class="sxs-lookup"><span data-stu-id="b135b-184">Figure 4-20: Viewing existing images using docker images</span></span>

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="b135b-185">Krok 4. (Opcjonalnie) Zdefiniuj swoje usługi w docker-compose.yml, podczas kompilowania złożone aplikacji platformy Docker z wieloma usługami</span><span class="sxs-lookup"><span data-stu-id="b135b-185">Step 4: (Optional) Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="b135b-186">Za pomocą pliku docker-compose.yml można zdefiniować zestaw powiązanych usług, który można wdrożyć jako złożone aplikacji za pomocą poleceń wdrażania opisano w następnej sekcji krok.</span><span class="sxs-lookup"><span data-stu-id="b135b-186">With the docker-compose.yml file you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="b135b-187">Musisz utworzyć ten plik w głównego lub główny folder rozwiązania; w następującym pliku docker-compose.yml powinien mieć podobnej zawartości:</span><span class="sxs-lookup"><span data-stu-id="b135b-187">You need to create that file in your main or root solution folder; it should have a similar content to the following docker-compose.yml file:</span></span>

```yml
version: '2'
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

<span data-ttu-id="b135b-188">W tym konkretnym przypadku ten plik definiuje dwie usługi: Usługa sieci web (usługa niestandardowa) i usługa redis (usługa popularnej pamięci podręcznej).</span><span class="sxs-lookup"><span data-stu-id="b135b-188">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="b135b-189">Każda usługa zostanie wdrożony jako kontener, dlatego musimy użyć konkretnego obrazu platformy Docker dla każdego.</span><span class="sxs-lookup"><span data-stu-id="b135b-189">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="b135b-190">Dla tej usługi sieci web określonego obrazu należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b135b-190">For this particular web service, the image will need to do the following:</span></span>

-   <span data-ttu-id="b135b-191">Twórz z pliku DockerFile w bieżącym katalogu</span><span class="sxs-lookup"><span data-stu-id="b135b-191">Build from the DockerFile in the current directory</span></span>

-   <span data-ttu-id="b135b-192">Przekazuj narażonych port 80 w kontenerze na porcie 81 na komputerze hosta</span><span class="sxs-lookup"><span data-stu-id="b135b-192">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

-   <span data-ttu-id="b135b-193">Zainstaluj w katalogu projektu na hoście/Code w kontenerze, dzięki czemu można zmodyfikować kod bez konieczności ponownego kompilowania obrazu</span><span class="sxs-lookup"><span data-stu-id="b135b-193">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

-   <span data-ttu-id="b135b-194">Połączenia usługi sieci web z usługą redis Cache</span><span class="sxs-lookup"><span data-stu-id="b135b-194">Link the web service to the redis service</span></span>

<span data-ttu-id="b135b-195">Używa usługi redis [najnowszego obrazu publicznego redis](https://hub.docker.com/_/redis/) pobierane z rejestru usługi Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="b135b-195">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="b135b-196">[redis](https://redis.io/) to system bardzo popularnej pamięci podręcznej dla aplikacji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="b135b-196">[redis](https://redis.io/) is a very popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="b135b-197">Krok 5. Kompilowanie i uruchamianie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="b135b-197">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="b135b-198">Jeśli aplikacja ma tylko jeden kontener, wystarczy uruchomić go przez wdrożenie jej do hosta platformy Docker (maszyny Wirtualnej lub serwera fizycznego).</span><span class="sxs-lookup"><span data-stu-id="b135b-198">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="b135b-199">Jednak jeśli Twoja aplikacja składa się z wielu usług, musisz *została utworzona*również.</span><span class="sxs-lookup"><span data-stu-id="b135b-199">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="b135b-200">Teraz widzieć różne opcje.</span><span class="sxs-lookup"><span data-stu-id="b135b-200">Let's see the different options.</span></span>

<span data-ttu-id="b135b-201">***Opcja A: Uruchom jeden kontener lub usługi***</span><span class="sxs-lookup"><span data-stu-id="b135b-201">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="b135b-202">Obraz platformy Docker można uruchomić przy użyciu platformy docker, uruchom polecenie, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="b135b-202">You can run the Docker image by using the docker run command, as shown here:</span></span>

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="b135b-203">Należy pamiętać, że dla tego konkretnego wdrożenia, firma Microsoft będzie można przekierowywanie żądania wysyłane do portu 80 na port wewnętrzny 5000.</span><span class="sxs-lookup"><span data-stu-id="b135b-203">Note that for this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="b135b-204">Teraz aplikacja nasłuchuje na porcie zewnętrznym 80 na poziomie hosta.</span><span class="sxs-lookup"><span data-stu-id="b135b-204">Now, the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="b135b-205">***Opcja B: Tworzenie i uruchamianie aplikacji wielu kontenerów***</span><span class="sxs-lookup"><span data-stu-id="b135b-205">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="b135b-206">W większości przypadków enterprise aplikację platformy Docker składać się z wielu usług.</span><span class="sxs-lookup"><span data-stu-id="b135b-206">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="b135b-207">W takiej sytuacji polecenie można uruchomić narzędzia docker compose się (rysunek 4-21), w której zostanie użyty plik docker-compose.yml, które zostały utworzone wcześniej.</span><span class="sxs-lookup"><span data-stu-id="b135b-207">For these cases, you can run the command docker-compose up (Figure 4-21), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="b135b-208">Uruchomienie tego polecenia wdraża złożone aplikacji ze wszystkimi jego powiązane kontenerów.</span><span class="sxs-lookup"><span data-stu-id="b135b-208">Running this command deploys a composed application with all of its related containers.</span></span>

![](./media/image27.png)

<span data-ttu-id="b135b-209">Rysunek 4 — 21: Wyniki polecenia "docker-compose up"</span><span class="sxs-lookup"><span data-stu-id="b135b-209">Figure 4-21: Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="b135b-210">Po uruchomieniu docker-compose w górę, wdrażania aplikacji i jej powiązane kontenerów w hoście platformy Docker, jak pokazano w rysunek 4-22 w reprezentacji maszyny Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="b135b-210">After you run docker-compose up, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-22, in the VM representation.</span></span>

![](./media/image28.png)

<span data-ttu-id="b135b-211">Rysunek 4-22: Maszyny Wirtualnej przy użyciu kontenerów Docker wdrożonych</span><span class="sxs-lookup"><span data-stu-id="b135b-211">Figure 4-22: VM with Docker containers deployed</span></span>

<span data-ttu-id="b135b-212">Uwaga docker-compose się i platformy docker, uruchom może być wystarczający do testowania kontenerów w środowisku deweloperskim, ale użytkownik nie może on używać ich na wszystkich koordynatorów, takich jak Docker Swarm, Mesosphere DC/OS lub Kubernetes, jeśli są oczekiwane do pracy z klastrami platformy Docker Aby można było skalować w górę.</span><span class="sxs-lookup"><span data-stu-id="b135b-212">Note docker-compose up and docker run might be enough for testing your containers in your development environment, but you might not use them at all if you are expecting to work with Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes in order to be able to scale up.</span></span> <span data-ttu-id="b135b-213">Jeśli używasz klastra, takie jak [trybu Docker Swarm](https://docs.docker.com/engine/swarm/) (dostępne w Docker for Windows i Mac od wersji 1.12), należy wdrożyć i przetestować z dodatkowymi poleceniami, takie jak usługa docker utworzyć dla jednej usługi lub gdy wszystko Wdrażanie aplikacji składających się z kilku kontenerów, za pomocą platformy docker compose pakietu i wdrażana w rozwiązaniu docker myBundleFile, wdrażając złożone aplikacji jako stosu, zgodnie z opisem w artykule [pakiety aplikacji rozproszonych](https://blog.docker.com/2016/06/docker-app-bundle/) docker.</span><span class="sxs-lookup"><span data-stu-id="b135b-213">If you're using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker for Windows and Mac since version 1.12), you need to deploy and test with additional commands such as docker service create for single services, or when you're deploying an app composed of several containers, using docker compose bundle and docker deploy myBundleFile, by deploying the composed app as a stack, as explained in the article [Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) from Docker.</span></span>

<span data-ttu-id="b135b-214">Dla [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) i [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) użyje wdrożenia różnych poleceń i skryptów, jak również.</span><span class="sxs-lookup"><span data-stu-id="b135b-214">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) you would use different deployment commands and scripts, as well.</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="b135b-215">Krok 6. Testowanie aplikacji platformy Docker (lokalnie, w swojej lokalnej maszyny Wirtualnej dysku CD)</span><span class="sxs-lookup"><span data-stu-id="b135b-215">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="b135b-216">W tym kroku różnią się w zależności od tego, jakie działania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b135b-216">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="b135b-217">W bardzo prosty .NET Core internetowego interfejsu API "Hello World" wdrażane jako pojedynczy kontener lub usługi czy po prostu potrzebujesz dostępu do usługi, zapewniając portu TCP, określone w pliku DockerFile.</span><span class="sxs-lookup"><span data-stu-id="b135b-217">In a very simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="b135b-218">Jeśli host lokalny nie jest włączony, aby przejść do swojej usługi, należy znaleźć adres IP dla maszyny, za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="b135b-218">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

<span data-ttu-id="b135b-219">adresu ip maszyny platformy docker *nazwa usługi kontenera*</span><span class="sxs-lookup"><span data-stu-id="b135b-219">docker-machine ip *your-container-name*</span></span>

<span data-ttu-id="b135b-220">Na hoście platformy Docker Otwórz przeglądarkę i przejdź do tej lokacji; Twoja aplikacja/Usługa jest uruchomiona, powinien zostać wyświetlony, jak pokazano w rysunek 4-23.</span><span class="sxs-lookup"><span data-stu-id="b135b-220">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-23.</span></span>

![](./media/image29.png)

<span data-ttu-id="b135b-221">Rysunek 4-23: Testowanie aplikacji platformy Docker lokalnie przy użyciu localhost</span><span class="sxs-lookup"><span data-stu-id="b135b-221">Figure 4-23: Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="b135b-222">Należy pamiętać, że korzysta ona z portu 80, ale wewnętrznie była nastąpi przekierowanie do portu 5000, ponieważ jest to, jak został wdrożony za pomocą platformy docker, uruchom, jak wyjaśniono wcześniej.</span><span class="sxs-lookup"><span data-stu-id="b135b-222">Note that it is using port 80, but internally it was being redirected to port 5000, because that's how it was deployed with docker run, as explained earlier.</span></span>

<span data-ttu-id="b135b-223">Można to sprawdzić, używając programu CURL z poziomu terminalu.</span><span class="sxs-lookup"><span data-stu-id="b135b-223">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="b135b-224">W przypadku instalacji platformy Docker na Windows domyślny adres IP jest 10.0.75.1, jak pokazano w rysunek 4-24.</span><span class="sxs-lookup"><span data-stu-id="b135b-224">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-24.</span></span>

![](./media/image30.png)

<span data-ttu-id="b135b-225">Rysunek 4 – 24: Testowanie aplikacji platformy Docker lokalnie, używając programu CURL</span><span class="sxs-lookup"><span data-stu-id="b135b-225">Figure 4-24: Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="b135b-226">**Debugowanie kontenera uruchomionego w platformy Docker**</span><span class="sxs-lookup"><span data-stu-id="b135b-226">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="b135b-227">Jeśli używasz środowiska Node.js i innych platform, takich jak kontenery platformy .NET Core, programu Visual Studio Code obsługuje debugowania platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="b135b-227">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="b135b-228">Możesz również debugować platformy .NET Core kontenerów platformy Docker przy użyciu programu Visual Studio, zgodnie z opisem w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b135b-228">You also can debug .NET Core containers in Docker when using Visual Studio, as described in the next section.</span></span>

<span data-ttu-id="b135b-229">**Więcej informacji:** Aby dowiedzieć się więcej o debugowaniu w kontenerach platformy Docker w środowisku Node.js, przejdź do <https://blog.docker.com/2016/07/live-debugging-docker/> i [ https://blogs.msdn.microsoft.com/\ użytkownika\_ed/2016/02/27 / Visual-Studio-Code-New-Features-13-big-Debugging-Updates-Rich-Object-Hover-Conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span><span class="sxs-lookup"><span data-stu-id="b135b-229">**More info:** To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and [https://blogs.msdn.microsoft.com/\ user\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b135b-230">[Poprzednie](docker-apps-development-environment.md)
>[dalej](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="b135b-230">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>