---
title: "Przepływ pracy pętli wewnętrzny programowanie aplikacji Docker"
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 632c04507c1478238a5dc2573542f8c88bae2a51
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2018
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="5cb64-104">Przepływ pracy pętli wewnętrzny programowanie aplikacji Docker</span><span class="sxs-lookup"><span data-stu-id="5cb64-104">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="5cb64-105">Aby mogło nastąpić wyzwolenie przepływu pracy zewnętrznego pętli obejmujących całą DevOps cykl, zaczyna na każdy Deweloper maszyny, kodowania samej aplikacji, za pomocą ich preferowanych języków lub platform i testowanie go lokalnie (14 4 rysunek).</span><span class="sxs-lookup"><span data-stu-id="5cb64-105">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-14).</span></span> <span data-ttu-id="5cb64-106">Jednak w każdym przypadku należy bardzo ważnym, niezależnie od tego, jakie języka, framework i platform wybierz.</span><span class="sxs-lookup"><span data-stu-id="5cb64-106">But in every case, you will have a very important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="5cb64-107">W tym określonego przepływu pracy są zawsze programują i testują rozwiązania Docker kontenerów, ale lokalnie.</span><span class="sxs-lookup"><span data-stu-id="5cb64-107">In this specific workflow, you are always developing and testing Docker containers, but locally.</span></span>

![](./media/image18.png)

<span data-ttu-id="5cb64-108">Rysunek 4 — 14: wewnętrzny pętli programowanie kontekstu</span><span class="sxs-lookup"><span data-stu-id="5cb64-108">Figure 4-14: Inner-loop development context</span></span>

<span data-ttu-id="5cb64-109">Kontener lub wystąpienia obrazu Docker będzie zawierać następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="5cb64-109">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="5cb64-110">Wybór systemu operacyjnego (na przykład dystrybucji systemu Linux lub Windows)</span><span class="sxs-lookup"><span data-stu-id="5cb64-110">An operating system selection (for example, a Linux distribution or Windows)</span></span>

-   <span data-ttu-id="5cb64-111">Pliki dodane przez dewelopera (na przykład pliki binarne aplikacji)</span><span class="sxs-lookup"><span data-stu-id="5cb64-111">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="5cb64-112">Konfiguracja (na przykład ustawienia środowiska i zależności)</span><span class="sxs-lookup"><span data-stu-id="5cb64-112">Configuration (for example, environment settings and dependencies)</span></span>

-   <span data-ttu-id="5cb64-113">Instrukcje dotyczące przetwarza uruchamianie Docker</span><span class="sxs-lookup"><span data-stu-id="5cb64-113">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="5cb64-114">Można skonfigurować przepływ pracy programowanie pętli wewnętrzny, który wykorzystuje Docker jako proces (opisany w następnej sekcji).</span><span class="sxs-lookup"><span data-stu-id="5cb64-114">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="5cb64-115">Uwzględniać początkowe kroki, aby skonfigurować środowisko nie jest uwzględnione, ponieważ musisz to zrobić tylko raz.</span><span class="sxs-lookup"><span data-stu-id="5cb64-115">Take into account that the initial steps to set up the environment is not included, because you need to do that just once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="5cb64-116">Tworzenie tylko jednej aplikacji w kontenerze Docker przy użyciu programu Visual Studio Code i interfejsu wiersza polecenia Docker</span><span class="sxs-lookup"><span data-stu-id="5cb64-116">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="5cb64-117">Aplikacje składają się z własnych usług oraz dodatkowych bibliotek (zależności).</span><span class="sxs-lookup"><span data-stu-id="5cb64-117">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="5cb64-118">Rysunek 4 – 15 przedstawiono podstawowe kroki, które zwykle trzeba przeprowadzić podczas kompilowania aplikacji Docker następuje szczegółowy opis każdego kroku.</span><span class="sxs-lookup"><span data-stu-id="5cb64-118">Figure 4-15 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![](./media/image19.png)

<span data-ttu-id="5cb64-119">Rysunek 4 — 15: ogólny przepływ pracy cyklu życia aplikacji Docker konteneryzowanych za pomocą interfejsu wiersza polecenia Docker</span><span class="sxs-lookup"><span data-stu-id="5cb64-119">Figure 4-15: High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="5cb64-120">Krok 1: Rozpoczęcie kodowania w programie Visual Studio Code i utworzyć odniesienia początkowej aplikacji/usługi</span><span class="sxs-lookup"><span data-stu-id="5cb64-120">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="5cb64-121">Sposób tworzenia aplikacji jest bardzo podobny sposób jak bez Docker.</span><span class="sxs-lookup"><span data-stu-id="5cb64-121">The way you develop your application is pretty similar to the way you do it without Docker.</span></span> <span data-ttu-id="5cb64-122">Różnica polega na tym że podczas tworzenia, wdrażania i testowania aplikacji lub usługi działające w kontenerach Docker umieszczone w środowisku lokalnym (na przykład maszyny Wirtualnej systemu Linux lub Windows).</span><span class="sxs-lookup"><span data-stu-id="5cb64-122">The difference is that while developing, you are deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="5cb64-123">**Konfigurowanie środowiska lokalnego**</span><span class="sxs-lookup"><span data-stu-id="5cb64-123">**Setting up your local environment**</span></span>

<span data-ttu-id="5cb64-124">Najnowsze wersje Docker dla systemów Mac i systemu Windows jest łatwiejsze niż kiedykolwiek do tworzenia aplikacji Docker i Instalator jest proste.</span><span class="sxs-lookup"><span data-stu-id="5cb64-124">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

<span data-ttu-id="5cb64-125">**Więcej informacji o** instrukcje dotyczące konfigurowania Docker dla systemu Windows, przejdź do [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="5cb64-125">**More info** For instructions on setting up Docker for Windows, go to [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).</span></span>

<span data-ttu-id="5cb64-126">Aby uzyskać instrukcje na temat konfigurowania Docker dla komputerów Mac, przejdź do <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="5cb64-126">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="5cb64-127">Ponadto należy edytora kodu, dzięki czemu można faktycznie opracowywanie aplikacji przy użyciu interfejsu wiersza polecenia Docker.</span><span class="sxs-lookup"><span data-stu-id="5cb64-127">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="5cb64-128">Firma Microsoft udostępnia Visual Studio Code, czyli edytorze niewielki kod, który jest obsługiwany w Mac, Windows i Linux i udostępnia IntelliSense z [obsługi wielu języków](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, przejdź, Java, Ruby, Python i większość Nowoczesne języki), [debugowania](https://code.visualstudio.com/Docs/editor/debugging), [integracji z usługą Git](https://code.visualstudio.com/Docs/editor/versioncontrol) i [Obsługa rozszerzeń](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="5cb64-128">Microsoft provides Visual Studio Code, which is a lightweight code editor that is supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="5cb64-129">Ten edytor jest doskonałym dopasowania dla deweloperów komputerów Mac i Linux.</span><span class="sxs-lookup"><span data-stu-id="5cb64-129">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="5cb64-130">W systemie Windows również służy pełnej aplikacji Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5cb64-130">In Windows, you also can use the full Visual Studio application.</span></span>

<span data-ttu-id="5cb64-131">**Więcej informacji o** instrukcje dotyczące instalowania programu Visual Studio dla systemu Windows, Mac lub Linux, przejdź do [http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).</span><span class="sxs-lookup"><span data-stu-id="5cb64-131">**More info** For instructions on installing Visual Studio for Windows, Mac, or Linux, go to [http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).</span></span>

<span data-ttu-id="5cb64-132">Możesz pracować z interfejsu wiersza polecenia Docker i wpisz swój kod, za pomocą dowolnego edytora kodu, ale jeśli używasz programu Visual Studio Code pozwala ułatwiają tworzenie plik Dockerfile i pliki docker-compose.yml w obszarze roboczym.</span><span class="sxs-lookup"><span data-stu-id="5cb64-132">You can work with Docker CLI and write your code using any code editor, but if you use Visual Studio Code, it makes it easy to author Dockerfile and docker-compose.yml files in your workspace.</span></span> <span data-ttu-id="5cb64-133">Ponadto można uruchamiać zadania programu Visual Studio Code z IDE, która wyświetli monit o skrypty, które mogą być uruchomione rozwinięciem operacji za pomocą interfejsu wiersza polecenia Docker poniżej.</span><span class="sxs-lookup"><span data-stu-id="5cb64-133">Plus, you can run Visual Studio Code tasks from the IDE that will prompt scripts that can be running elaborated operations using Docker CLI underneath.</span></span>

<span data-ttu-id="5cb64-134">Visual Studio Code są udostępniane przez rozszerzenie, należy zainstalować.</span><span class="sxs-lookup"><span data-stu-id="5cb64-134">Visual Studio Code is provided by an extension, which you'll need to install.</span></span> <span data-ttu-id="5cb64-135">Aby to zrobić, naciśnij kombinację klawiszy Ctrl + Shift + P, wpisz **zainstalować ext**, a następnie uruchom rozszerzenia: polecenia instalowania rozszerzenia można wyświetlić listy rozszerzeń witryny Marketplace.</span><span class="sxs-lookup"><span data-stu-id="5cb64-135">To do so, Press Ctrl+Shift+P, type **ext install**, and then run the Extensions: Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="5cb64-136">Następnie wpisz **docker** Aby filtrować wyniki, a następnie wybierz plik Dockerfile i Docker Compose pliku (yml) rozszerzenia obsługi, jak pokazano w rysunek 4-16.</span><span class="sxs-lookup"><span data-stu-id="5cb64-136">Next, type **docker** to filter the results, and then select the Dockerfile And Docker Compose File (yml) Support extension, as depicted in Figure 4-16.</span></span>

![](./media/image20.png)

<span data-ttu-id="5cb64-137">Rysunek 4 – 16: Instalowanie rozszerzenia Docker w kodzie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5cb64-137">Figure 4-16: Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="5cb64-138">Krok 2: Tworzenie plik DockerFile związane z istniejącego obrazu (zwykły system operacyjny lub deweloperów środowiskach, takich jak .NET Core, Node.js i Ruby)</span><span class="sxs-lookup"><span data-stu-id="5cb64-138">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="5cb64-139">Konieczne będzie plik DockerFile dla poszczególnych niestandardowy obraz ma zostać utworzony i kontener do wdrożenia, w związku z tym, jeśli aplikacja składa się z jednej usługi niestandardowe, konieczne będzie pojedynczy plik DockerFile.</span><span class="sxs-lookup"><span data-stu-id="5cb64-139">You will need a DockerFile per custom image to be built and per container to be deployed, therefore, if your app is made up of a single custom service, you will need a single DockerFile.</span></span> <span data-ttu-id="5cb64-140">Jednak jeśli aplikacja składa się z wielu usług (jak architektura mikrousług), będziesz potrzebować co plik Dockerfile dla danej usługi.</span><span class="sxs-lookup"><span data-stu-id="5cb64-140">But, if your app is composed of multiple services (as in a microservices architecture), you'll need one Dockerfile per service.</span></span>

<span data-ttu-id="5cb64-141">Plik DockerFile zazwyczaj znajduje się w folderze głównym aplikacji lub usługi i zawiera wymagane polecenia, tak że Docker wie, jak skonfigurować i uruchomić tej aplikacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="5cb64-141">The DockerFile is usually placed within the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="5cb64-142">Można tworzyć z plik DockerFile i dodaj go do projektu wraz z kodu (node.js, .NET Core itp.), lub jeśli dopiero zaczynasz do środowiska, Przyjrzyjmy się następujące porady.</span><span class="sxs-lookup"><span data-stu-id="5cb64-142">You can create your DockerFile and add it to your project along with your code (node.js, .NET Core, etc.), or, if you are new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="5cb64-143">Można użyć narzędzia wiersza polecenia o nazwie [yo docker](https://github.com/Microsoft/generator-docker), który rusztowania pliki z projektu w języku, wybierz i dodaje wymagane pliki konfiguracji Docker.</span><span class="sxs-lookup"><span data-stu-id="5cb64-143">You can use a command-line tool called [yo docker](https://github.com/Microsoft/generator-docker), which scaffolds files from your project in the language you choose and adds the required Docker configuration files.</span></span> <span data-ttu-id="5cb64-144">Zasadniczo, aby pomóc deweloperom wprowadzenie, tworzy odpowiedni plik DockerFile, docker-compose.yml i inne skojarzone skrypty, aby skompilować i uruchomić kontenerów Docker.</span><span class="sxs-lookup"><span data-stu-id="5cb64-144">Basically, to assist developers getting started, it creates the appropriate DockerFile, docker-compose.yml, and other associated scripts to build and run your Docker containers.</span></span> <span data-ttu-id="5cb64-145">Tego generatora narzędzia yeoman wyświetli monit o na kilka pytań, prosząc programowanie wybranego hosta kontenera języka i docelowego.</span><span class="sxs-lookup"><span data-stu-id="5cb64-145">This yeoman generator will prompt you with a few questions, asking your selected development language and destination container host.</span></span>

![yo docker](./media/image21.png)

<span data-ttu-id="5cb64-147">Na przykład rysunek 4-17 zawiera dwa zrzuty ekranu z terminali systemu Windows i na komputerze Mac, w obu przypadkach systemem yo docker, co spowoduje, że przykładowy kod projektów (obecnie .NET Core Golang i Node.js jako obsługiwanych języków) już skonfigurowana do pracy w w górnej części Docker.</span><span class="sxs-lookup"><span data-stu-id="5cb64-147">For instance, Figure 4-17 shows two screenshots from the terminals in Windows and on a Mac, in both cases, running yo docker, which will generate the sample code projects (currently .NET Core, Golang, and Node.js as supported languages) already configured to work on top of Docker.</span></span>

![](./media/image22.PNG)  ![](./media/image23.png)

<span data-ttu-id="5cb64-148">Rysunek 4 — 17: yo docker narzędzia polecenia w systemie Windows (lewych) i na komputerze Mac</span><span class="sxs-lookup"><span data-stu-id="5cb64-148">Figure 4-17: yo docker command tool in Windows (left) and on a Mac</span></span>

<span data-ttu-id="5cb64-149">Rysunek 4-18 stanowi przykład przy użyciu yo docker po miejscowej można szkieletu istniejącego projektu platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5cb64-149">Figure 4-18 presents an example using yo docker after you have an existing .NET Core project in place to be scaffolded.</span></span>

![](./media/image24.PNG)

<span data-ttu-id="5cb64-150">Rysunek 4 — 18: yo docker z istniejących .NET Core projektu w miejscu</span><span class="sxs-lookup"><span data-stu-id="5cb64-150">Figure 4-18: yo docker with an existing .NET Core project in place</span></span>

<span data-ttu-id="5cb64-151">Z plik DockerFile możesz określić podstawową obrazów Docker należy używać (np. przy użyciu "od microsoft/dotnet:1.0.0-core").</span><span class="sxs-lookup"><span data-stu-id="5cb64-151">From the DockerFile, you specify what base Docker image you'll be using (like using "FROM microsoft/dotnet:1.0.0-core").</span></span> <span data-ttu-id="5cb64-152">Zazwyczaj utworzysz niestandardowego obrazu na podstawowy obraz, który można uzyskać z dowolnego oficjalnego repozytorium pod adresem [rejestru Centrum Docker](https://hub.docker.com/) (takich jak [obrazu dla platformy .NET Core](https://hub.docker.com/r/microsoft/dotnet/) lub [dla środowiska Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="5cb64-152">You usually will build your custom image on top of a base image that you can get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/r/microsoft/dotnet/) or one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="5cb64-153">***Opcja A: użycie istniejącego obrazu platformy Docker urzędowego***</span><span class="sxs-lookup"><span data-stu-id="5cb64-153">***Option A: Use an existing official Docker image***</span></span>

<span data-ttu-id="5cb64-154">Użycie oficjalnego repozytorium stosu języka z numerem wersji gwarantuje, że te same funkcje języka są dostępne na wszystkich komputerach (w tym programowania, testowania i produkcji).</span><span class="sxs-lookup"><span data-stu-id="5cb64-154">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="5cb64-155">Poniżej przedstawiono przykładowy plik DockerFile kontenera .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5cb64-155">Following is a sample DockerFile for a .NET Core container:</span></span>

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

<span data-ttu-id="5cb64-156">W takim przypadku go używa wersji 1.0.1 oficjalnego obrazu platformy ASP.NET Core Docker Linux o nazwie microsoft/aspnetcore:1.0.1.</span><span class="sxs-lookup"><span data-stu-id="5cb64-156">In this case, it is using the version 1.0.1 of the official ASP.NET Core Docker image for Linux named microsoft/aspnetcore:1.0.1.</span></span> <span data-ttu-id="5cb64-157">Aby uzyskać szczegółowe informacje, zapoznaj się [strony platformy ASP.NET Core Docker obrazu](https://hub.docker.com/r/microsoft/aspnetcore/) i [strona .NET Core Docker obrazu](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="5cb64-157">For further details, consult the [ASP.NET Core Docker Image page](https://hub.docker.com/r/microsoft/aspnetcore/) and the [.NET Core Docker Image page](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="5cb64-158">Możesz również może używać innego obrazu można porównywać pod względem, takich jak węzła: 4-onbuild dla środowiska Node.js lub wielu innych obrazów wstępnie skonfigurowane dla języków programowania, które są dostępne pod adresem [Centrum Docker](https://hub.docker.com/explore/).</span><span class="sxs-lookup"><span data-stu-id="5cb64-158">You also could be using another comparable image like node:4-onbuild for Node.js, or many other preconfigured images for development languages, which are available at [Docker Hub](https://hub.docker.com/explore/).</span></span>

<span data-ttu-id="5cb64-159">W plik DockerFile należy także poinstruować Docker do nasłuchiwania na portach TCP, która będzie używana w czasie wykonywania (np. port 80).</span><span class="sxs-lookup"><span data-stu-id="5cb64-159">In the DockerFile, you also need to instruct Docker to listen to the TCP port that you will use at runtime (such as port 80).</span></span>

<span data-ttu-id="5cb64-160">Istnieją inne wiersze konfiguracji, które można dodać w plik DockerFile w zależności od języka/framework, którego używasz, więc Docker potrafi uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="5cb64-160">There are other lines of configuration that you can add in the DockerFile depending on the language/framework you are using, so Docker knows how to run the app.</span></span> <span data-ttu-id="5cb64-161">Na przykład, potrzebny jest wiersz punktu wejścia z \["dotnet", "MyCustomMicroservice.dll"\] do uruchamiania aplikacji .NET Core, chociaż może mieć wiele wariantów w zależności od rozwiązania do tworzenia i uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="5cb64-161">For instance, you need the ENTRYPOINT line with \["dotnet", "MyCustomMicroservice.dll"\] to run a .NET Core app, although you can have multiple variants depending on the approach to build and run your service.</span></span> <span data-ttu-id="5cb64-162">Jeśli używasz zestawu SDK i interfejsu wiersza polecenia platformy dotnet tworzenie i uruchamianie aplikacji .NET, może być nieco inne.</span><span class="sxs-lookup"><span data-stu-id="5cb64-162">If you're using the SDK and dotnet CLI to build and run the .NET app, it would be slightly different.</span></span> <span data-ttu-id="5cb64-163">Mierzenie jest, że ENTRYPOINT wiersza oraz dodatkowe wiersze będą różne w zależności od języka/platformy wybrane dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5cb64-163">The bottom line is that the ENTRYPOINT line plus additional lines will be different depending on the language/platform you choose for your application.</span></span>

<span data-ttu-id="5cb64-164">**Więcej informacji o** dla informacji o tworzeniu obrazy usługi Docker dla aplikacji .NET Core, przejdź do <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="5cb64-164">**More info** For information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>

<span data-ttu-id="5cb64-165">Aby dowiedzieć się więcej na temat tworzenia własnych obrazów, przejdź do [https://docs.docker.com/engine/ \samouczki/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span><span class="sxs-lookup"><span data-stu-id="5cb64-165">To learn more about building your own images, go to [https://docs.docker.com/engine/\ tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span></span>

<span data-ttu-id="5cb64-166">**Repozytoria obrazu dla wielu platform**</span><span class="sxs-lookup"><span data-stu-id="5cb64-166">**Multiplatform image repositories**</span></span>

<span data-ttu-id="5cb64-167">Jak kontenery Windows staną się bardziej powszechnie, jednym repozytorium mogą zawierać wariantów platform, takich jak obraz systemu Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="5cb64-167">As Windows containers become more prevalent, a single repository can contain platform variants, such as a Linux and Windows image.</span></span> <span data-ttu-id="5cb64-168">Jest to nowa funkcja dostępna w Docker, który umożliwia dostawcom obejmują wiele platform, takich jak za pomocą jednego repozytorium [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repozytorium, która jest dostępna w DockerHub rejestru.</span><span class="sxs-lookup"><span data-stu-id="5cb64-168">This is a new feature coming in Docker that makes it possible for vendors to use a single repository to cover multiple platforms, such as [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repository, which is available at DockerHub registry.</span></span> <span data-ttu-id="5cb64-169">Jak funkcja zawiera aktywności, ściąganie tego obrazu na hoście systemu Windows będzie pobierać wariant systemu Windows, natomiast ściąganie taką samą nazwę obrazu z hosta systemu Linux będzie pobierać wariant systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="5cb64-169">As the feature comes alive, pulling this image from a Windows host will pull the Windows variant, whereas pulling the same image name from a Linux host will pull the Linux variant.</span></span>

<span data-ttu-id="5cb64-170">***Opcja B: tworzenia obrazu podstawowego od podstaw***</span><span class="sxs-lookup"><span data-stu-id="5cb64-170">***Option B: Create your base image from scratch***</span></span>

<span data-ttu-id="5cb64-171">Można utworzyć własny obraz podstawowy Docker od początku, zgodnie z objaśnieniem w tym [artykułu](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z Docker.</span><span class="sxs-lookup"><span data-stu-id="5cb64-171">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="5cb64-172">Ten scenariusz, który prawdopodobnie nie jest najważniejsze dla Ciebie, jeśli jest uruchamiany tylko z rozwiązaniem Docker z jest, ale jeśli chcesz ustawić określone bity obrazu podstawowego, możesz to zrobić.</span><span class="sxs-lookup"><span data-stu-id="5cb64-172">This is a scenario that is probably not best for you if you are just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="5cb64-173">Krok 3: Tworzenie niestandardowe obrazy usługi Docker osadzanie w nim usługi</span><span class="sxs-lookup"><span data-stu-id="5cb64-173">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="5cb64-174">Dla każdej usługi niestandardowych, który składa się z aplikacji musisz utworzyć obraz pokrewne.</span><span class="sxs-lookup"><span data-stu-id="5cb64-174">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="5cb64-175">Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, musisz tylko jeden obraz.</span><span class="sxs-lookup"><span data-stu-id="5cb64-175">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="5cb64-176">Biorąc pod uwagę "zewnętrzne pętli DevOps przepływu pracy", obrazy zostaną utworzone przez proces kompilacji automatycznych zawsze, gdy wypychanie kodu źródłowego do repozytorium Git (ciągłej integracji), obrazów, które zostaną utworzone w tym globalnych środowisku z sieci Kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="5cb64-176">When taking into account the "outer-loop DevOps workflow," the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration) so the images will be created in that global environment from your source code.</span></span>

<span data-ttu-id="5cb64-177">Jednak zanim możemy należy wziąć pod uwagę będzie tego trasy zewnętrzne pętli, musimy upewnij się, że aplikacja Docker faktycznie działa prawidłowo, aby ich nie umieścić kod, który może nie działać poprawnie do systemu kontroli źródła (Git, itp.).</span><span class="sxs-lookup"><span data-stu-id="5cb64-177">But, before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>

<span data-ttu-id="5cb64-178">W związku z tym Każdy deweloper musi najpierw celu cały proces wewnętrzny pętli do testowania lokalnie i kontynuować tworzenie dopóki mają push pełną funkcji lub zmiany z systemu kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="5cb64-178">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="5cb64-179">Do utworzenia obrazu w środowisku lokalnym i za pomocą plik DockerFile, służy polecenie kompilacji docker, jak pokazano w rysunek 4-19 (można także uruchomić rozwiązania docker compose — tworzenie aplikacji składane przez kilka kontenery/usługi).</span><span class="sxs-lookup"><span data-stu-id="5cb64-179">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-19 (you also can run docker-compose up --build for applications composed by several containers/services).</span></span>

![](./media/image25.png)

<span data-ttu-id="5cb64-180">Rysunek 4 — 19: uruchomioną kompilację docker</span><span class="sxs-lookup"><span data-stu-id="5cb64-180">Figure 4-19: Running docker build</span></span>

<span data-ttu-id="5cb64-181">Opcjonalnie, zamiast bezpośredniego uruchamiania docker kompilacji z folderu projektu, najpierw można wygenerować folderu do wdrożenia z bibliotekami .NET potrzebne przy użyciu wykonywania dotnet publikowania polecenia, a następnie uruchom kompilacji docker.</span><span class="sxs-lookup"><span data-stu-id="5cb64-181">Optionally, instead of directly running docker build from the project's folder, you first can generate a deployable folder with the .NET libraries needed by using the run dotnet publish command, and then run docker build.</span></span>

<span data-ttu-id="5cb64-182">W tym przykładzie, spowoduje to utworzenie obrazu Docker z nazwy cesardl/netcore-webapi mikrousługi-docker: pierwszy (: najpierw jest znacznik, podobnie jak w określonej wersji).</span><span class="sxs-lookup"><span data-stu-id="5cb64-182">In this example, this creates a Docker image with the name cesardl/netcore-webapi-microservice-docker:first (:first is a tag, like a specific version).</span></span> <span data-ttu-id="5cb64-183">Można wykonać ten krok dla każdego niestandardowego obrazu potrzebnych do tworzenia aplikacji Docker składać się z kilku kontenerów.</span><span class="sxs-lookup"><span data-stu-id="5cb64-183">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="5cb64-184">Można znaleźć istniejących obrazów w lokalnym repozytorium (komputerze deweloperskim) przy użyciu rozwiązania docker polecenia obrazów, zgodnie z opisami w rysunek 4-20.</span><span class="sxs-lookup"><span data-stu-id="5cb64-184">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-20.</span></span>

![](./media/image26.png)

<span data-ttu-id="5cb64-185">Rysunek 4-20: wyświetlanie istniejących obrazów za pomocą obrazy usługi docker</span><span class="sxs-lookup"><span data-stu-id="5cb64-185">Figure 4-20: Viewing existing images using docker images</span></span>

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="5cb64-186">Krok 4: Definiowanie (opcjonalnie) usług w rozwiązaniu docker-compose.yml podczas kompilowania aplikacji przez Docker składać się z wieloma usługami</span><span class="sxs-lookup"><span data-stu-id="5cb64-186">Step 4: (Optional) Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="5cb64-187">Plik docker-compose.yml można zdefiniować zestawu usług wdrażanych jako aplikacja składa z poleceń wdrażania szczegółowo w następnej sekcji krok.</span><span class="sxs-lookup"><span data-stu-id="5cb64-187">With the docker-compose.yml file you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="5cb64-188">Musisz utworzyć ten plik w sieci głównym lub głównego folderu rozwiązania; powinien mieć zawartość podobny do następującego pliku docker-compose.yml:</span><span class="sxs-lookup"><span data-stu-id="5cb64-188">You need to create that file in your main or root solution folder; it should have a similar content to the following docker-compose.yml file:</span></span>

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

<span data-ttu-id="5cb64-189">W tym przypadku plik definiuje dwie usługi: Usługa sieci web (usługa niestandardowych) i usługę redis (usługa popularnych pamięci podręcznej).</span><span class="sxs-lookup"><span data-stu-id="5cb64-189">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="5cb64-190">Każdej usługi zostanie wdrożony jako kontener, więc musimy używane dla każdego konkretnego obrazu Docker.</span><span class="sxs-lookup"><span data-stu-id="5cb64-190">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="5cb64-191">Dla tej usługi sieci web określonego obrazu należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5cb64-191">For this particular web service, the image will need to do the following:</span></span>

-   <span data-ttu-id="5cb64-192">Konstruuj z plik DockerFile w bieżącym katalogu</span><span class="sxs-lookup"><span data-stu-id="5cb64-192">Build from the DockerFile in the current directory</span></span>

-   <span data-ttu-id="5cb64-193">Przekazuj dostępnego portu 80 kontenera do portu 81 na komputerze hosta</span><span class="sxs-lookup"><span data-stu-id="5cb64-193">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

-   <span data-ttu-id="5cb64-194">Katalogu projektu instalacji na hoście /code w kontenerze, dzięki czemu można zmodyfikować kod bez konieczności odbudować obrazu</span><span class="sxs-lookup"><span data-stu-id="5cb64-194">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

-   <span data-ttu-id="5cb64-195">Łączenie z usługą redis usługi sieci web</span><span class="sxs-lookup"><span data-stu-id="5cb64-195">Link the web service to the redis service</span></span>

<span data-ttu-id="5cb64-196">Używane przez usługę redis [najnowsze obrazu publicznego redis](https://hub.docker.com/_/redis/) pobierane z rejestru Centrum Docker.</span><span class="sxs-lookup"><span data-stu-id="5cb64-196">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="5cb64-197">[redis](http://redis.io/) to system bardzo popularny pamięci podręcznej dla aplikacji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="5cb64-197">[redis](http://redis.io/) is a very popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="5cb64-198">Krok 5: Tworzenie i uruchamianie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="5cb64-198">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="5cb64-199">Jeśli aplikacja ma tylko jeden kontener, wystarczy uruchomić go przez wdrożenie jej (maszyny Wirtualnej lub serwerze fizycznym) hosta Docker.</span><span class="sxs-lookup"><span data-stu-id="5cb64-199">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="5cb64-200">Jednak jeśli aplikacja składa się z wielu usług, musisz *została utworzona*, zbyt.</span><span class="sxs-lookup"><span data-stu-id="5cb64-200">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="5cb64-201">Zobaczmy różne opcje.</span><span class="sxs-lookup"><span data-stu-id="5cb64-201">Let's see the different options.</span></span>

<span data-ttu-id="5cb64-202">***Opcja A: uruchom jeden kontener lub usługi***</span><span class="sxs-lookup"><span data-stu-id="5cb64-202">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="5cb64-203">Obraz Docker można uruchomić przy użyciu rozwiązania docker, uruchom polecenie, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="5cb64-203">You can run the Docker image by using the docker run command, as shown here:</span></span>

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="5cb64-204">Należy pamiętać, że dla tego konkretnego wdrożenia, firma Microsoft będzie można Przekierowywanie żądań wysyłane do portu 80 do wewnętrznego portu 5000.</span><span class="sxs-lookup"><span data-stu-id="5cb64-204">Note that for this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="5cb64-205">Teraz aplikacja nasłuchuje na porcie zewnętrznym 80 na poziomie hosta.</span><span class="sxs-lookup"><span data-stu-id="5cb64-205">Now, the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="5cb64-206">***Opcja B: tworzenia i uruchamiania aplikacji kontenera wielu***</span><span class="sxs-lookup"><span data-stu-id="5cb64-206">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="5cb64-207">W większości przypadków przedsiębiorstwa aplikacji Docker składać się z wielu usług.</span><span class="sxs-lookup"><span data-stu-id="5cb64-207">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="5cb64-208">W tych przypadkach można uruchomić polecenie rozwiązania docker compose górę (rysunek 4-21), którego użyje plik docker-compose.yml, które zostały utworzone wcześniej.</span><span class="sxs-lookup"><span data-stu-id="5cb64-208">For these cases, you can run the command docker-compose up (Figure 4-21), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="5cb64-209">Uruchomienie tego polecenia wdraża składa aplikacji ze wszystkimi jego powiązanych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="5cb64-209">Running this command deploys a composed application with all of its related containers.</span></span>

![](./media/image27.png)

<span data-ttu-id="5cb64-210">Rysunek 4 — 21: Wyniki uruchomienia polecenia "docker tworzą się"</span><span class="sxs-lookup"><span data-stu-id="5cb64-210">Figure 4-21: Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="5cb64-211">Po uruchomieniu programu docker-tworzą w górę, wdrażania aplikacji i jej powiązane kontenerów do hosta Docker, zgodnie z opisami 4 rysunek-22, w reprezentacji maszyny Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="5cb64-211">After you run docker-compose up, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-22, in the VM representation.</span></span>

![](./media/image28.png)

<span data-ttu-id="5cb64-212">Rysunek 4 — 22: maszyna wirtualna o wdrożone kontenery Docker</span><span class="sxs-lookup"><span data-stu-id="5cb64-212">Figure 4-22: VM with Docker containers deployed</span></span>

<span data-ttu-id="5cb64-213">Uwaga docker tworzą się i docker Uruchom może być wystarczająca do testowania kontenerów w środowisku projektowania, ale nie można na przykład je na wszystkich jeśli są oczekiwane do pracy z klastrami Docker i orchestrators, takich jak Docker Swarm, Mesosphere DC/OS lub Kubernetes Aby można było skalowanie w górę.</span><span class="sxs-lookup"><span data-stu-id="5cb64-213">Note docker-compose up and docker run might be enough for testing your containers in your development environment, but you might not use them at all if you are expecting to work with Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes in order to be able to scale up.</span></span> <span data-ttu-id="5cb64-214">Jeśli używasz klastra, takie jak [Docker Swarm tryb](https://docs.docker.com/engine/swarm/) (dostępne w Docker dla systemu Windows i Mac od wersji 1.12), należy do wdrożenia i przetestowania przy użyciu dodatkowych poleceń, takich jak usługa docker utworzyć dla jednej usługi lub podczas pracy Wdrażanie aplikacji składający się z kilku kontenerów, przy użyciu rozwiązania docker compose pakietu i docker wdrażanie myBundleFile, wdrażając składa aplikacji jako stosu, zgodnie z opisem w artykule [pakiety aplikacji rozproszonych](https://blog.docker.com/2016/06/docker-app-bundle/) z Docker.</span><span class="sxs-lookup"><span data-stu-id="5cb64-214">If you're using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker for Windows and Mac since version 1.12), you need to deploy and test with additional commands such as docker service create for single services, or when you're deploying an app composed of several containers, using docker compose bundle and docker deploy myBundleFile, by deploying the composed app as a stack, as explained in the article [Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) from Docker.</span></span>

<span data-ttu-id="5cb64-215">Aby uzyskać [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) i [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) użyje inne wdrożenie poleceń i skryptów, jak również.</span><span class="sxs-lookup"><span data-stu-id="5cb64-215">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) you would use different deployment commands and scripts, as well.</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="5cb64-216">Krok 6: Przetestować aplikację Docker (lokalnie, w sieci lokalnej maszyny Wirtualnej CD)</span><span class="sxs-lookup"><span data-stu-id="5cb64-216">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="5cb64-217">Ten krok będą się różnić w zależności od czynności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5cb64-217">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="5cb64-218">W bardzo proste .NET Core interfejsu API sieci Web "Hello World" wdrożony jako jeden kontener lub usługi czy wystarczy uzyskać dostęp do usługi, zapewniając określonym w plik DockerFile porcie TCP.</span><span class="sxs-lookup"><span data-stu-id="5cb64-218">In a very simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="5cb64-219">Jeśli host lokalny nie jest włączony, przejdź do usługi, znaleźć adres IP dla komputera, za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="5cb64-219">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

<span data-ttu-id="5cb64-220">ip komputera docker *your nazwa kontenera*</span><span class="sxs-lookup"><span data-stu-id="5cb64-220">docker-machine ip *your-container-name*</span></span>

<span data-ttu-id="5cb64-221">Na hoście Docker Otwórz przeglądarkę i przejdź do tej lokacji; powinny pojawić się aplikacji/usługi uruchomione, jak pokazano w rysunek 4-23.</span><span class="sxs-lookup"><span data-stu-id="5cb64-221">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-23.</span></span>

![](./media/image29.png)

<span data-ttu-id="5cb64-222">Rysunek 4 — 23: testowanie aplikacji Docker lokalnie za pomocą localhost</span><span class="sxs-lookup"><span data-stu-id="5cb64-222">Figure 4-23: Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="5cb64-223">Należy pamiętać, że używa portu 80, ale wewnętrznie został nastąpi przekierowanie do portu 5000, ponieważ jest to, jak została wdrożona z docker uruchomić, zgodnie z opisem.</span><span class="sxs-lookup"><span data-stu-id="5cb64-223">Note that it is using port 80, but internally it was being redirected to port 5000, because that's how it was deployed with docker run, as explained earlier.</span></span>

<span data-ttu-id="5cb64-224">Można to sprawdzić za pomocą CURL z terminala.</span><span class="sxs-lookup"><span data-stu-id="5cb64-224">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="5cb64-225">W instalacji Docker w systemie Windows domyślny adres IP jest 10.0.75.1, jak pokazano w rysunek 4 do 24.</span><span class="sxs-lookup"><span data-stu-id="5cb64-225">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-24.</span></span>

![](./media/image30.png)

<span data-ttu-id="5cb64-226">Rysunek 4 – 24: testowanie aplikacji Docker lokalnie, przy użyciu programu CURL</span><span class="sxs-lookup"><span data-stu-id="5cb64-226">Figure 4-24: Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="5cb64-227">**Debugowanie kontenera systemem Docker**</span><span class="sxs-lookup"><span data-stu-id="5cb64-227">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="5cb64-228">Visual Studio Code obsługuje Docker debugowania, jeśli używasz środowiska Node.js i innych platform, takich jak kontenery .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5cb64-228">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="5cb64-229">Możesz również debugować kontenerów .NET Core w Docker przy użyciu programu Visual Studio, zgodnie z opisem w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="5cb64-229">You also can debug .NET Core containers in Docker when using Visual Studio, as described in the next section.</span></span>

<span data-ttu-id="5cb64-230">**Aby dowiedzieć się więcej:** Aby dowiedzieć się więcej na temat debugowania kontenery Node.js Docker, <https://blog.docker.com/2016/07/live-debugging-docker/> i [https://blogs.msdn.microsoft.com/ \ użytkownika\_ed/2016/02/27 / Visual-Studio-Code-New-Features-13-big-Debugging-Updates-Rich-Object-Hover-Conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span><span class="sxs-lookup"><span data-stu-id="5cb64-230">**More info:** To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and [https://blogs.msdn.microsoft.com/\ user\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5cb64-231">[Poprzednie] (docker aplikacje development-environment.md) [dalej] (visual-studio narzędzia do docker.md)</span><span class="sxs-lookup"><span data-stu-id="5cb64-231">[Previous] (docker-apps-development-environment.md) [Next] (visual-studio-tools-for-docker.md)</span></span>
