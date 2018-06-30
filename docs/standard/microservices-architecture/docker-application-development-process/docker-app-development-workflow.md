---
title: Przepływ pracy tworzenia aplikacji Docker
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Przepływ pracy tworzenia aplikacji Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 0627a61e910b1d278fd2e604dd8de7021fdb0fed
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106220"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="30d21-103">Przepływ pracy tworzenia aplikacji Docker</span><span class="sxs-lookup"><span data-stu-id="30d21-103">Development workflow for Docker apps</span></span>

<span data-ttu-id="30d21-104">Cykl życia programowania aplikacji rozpoczyna się od wszystkich deweloperów maszyny, gdzie dewelopera kodów aplikacji przy użyciu preferowanego języka i sprawdza ją lokalnie.</span><span class="sxs-lookup"><span data-stu-id="30d21-104">The application development lifecycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="30d21-105">Niezależnie od tego, które języka, framework i platformy wybierze dewelopera, w tym przepływie pracy dewelopera jest zawsze tworzenie i testowanie kontenery Docker, ale w ten sposób lokalnie.</span><span class="sxs-lookup"><span data-stu-id="30d21-105">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="30d21-106">Każdego kontenera (wystąpienia obrazu Docker) obejmuje następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="30d21-106">Each container (an instance of a Docker image) includes the following components:</span></span>

-   <span data-ttu-id="30d21-107">Wybór systemu operacyjnego (na przykład dystrybucji systemu Linux, Windows Nano Server lub Windows Server Core).</span><span class="sxs-lookup"><span data-stu-id="30d21-107">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

-   <span data-ttu-id="30d21-108">Pliki dodane przez dewelopera (pliki binarne aplikacji itp.).</span><span class="sxs-lookup"><span data-stu-id="30d21-108">Files added by the developer (application binaries, etc.).</span></span>

-   <span data-ttu-id="30d21-109">Informacje o konfiguracji (ustawienia środowiska i zależności).</span><span class="sxs-lookup"><span data-stu-id="30d21-109">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="30d21-110">Przepływ pracy umożliwiający projektowanie aplikacji na podstawie kontenera Docker</span><span class="sxs-lookup"><span data-stu-id="30d21-110">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="30d21-111">W tej sekcji opisano *pętli wewnętrzny* przepływ pracy rozwoju aplikacji na podstawie kontenera Docker.</span><span class="sxs-lookup"><span data-stu-id="30d21-111">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="30d21-112">Wewnętrzny pętli przepływu pracy oznacza, że jest nie biorąc pod uwagę szerszych DevOps przepływu pracy i po prostu koncentruje się na programowanie pracować na komputerze dewelopera.</span><span class="sxs-lookup"><span data-stu-id="30d21-112">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="30d21-113">Początkowe kroki, aby skonfigurować środowisko nie są uwzględnione, ponieważ te są wykonywane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="30d21-113">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="30d21-114">Aplikacja składa się z własnych usług oraz dodatkowych bibliotek (zależności).</span><span class="sxs-lookup"><span data-stu-id="30d21-114">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="30d21-115">Poniżej przedstawiono podstawowe kroki, które zwykle wykonać podczas kompilowania aplikacji Docker, zgodnie z opisami w rysunek 5-1.</span><span class="sxs-lookup"><span data-stu-id="30d21-115">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="30d21-116">**Rysunek 5-1.**</span><span class="sxs-lookup"><span data-stu-id="30d21-116">**Figure 5-1.**</span></span> <span data-ttu-id="30d21-117">Krok przepływu pracy umożliwiający projektowanie aplikacji konteneryzowanych Docker</span><span class="sxs-lookup"><span data-stu-id="30d21-117">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="30d21-118">W tym przewodniku szczegółowo całego tego procesu i każdy krok głównych tłumaczy koncentrujących się na środowiska Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30d21-118">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="30d21-119">Korzystając z podejście do tworzenia edytora/interfejsu wiersza polecenia (na przykład Visual Studio Code oraz interfejsu wiersza polecenia Docker na macOS lub Windows), musisz wiedzieć każdy krok zazwyczaj bardziej szczegółowo niż Jeśli używasz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30d21-119">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="30d21-120">Aby uzyskać więcej informacji na temat pracy w środowisku interfejsu wiersza polecenia można znaleźć Książka elektroniczna [cyklem życia aplikacji Docker konteneryzowanych Platforms firmy Microsoft i narzędzia](http://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="30d21-120">For more details about working in a CLI environment, refer to the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](http://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="30d21-121">Jeśli używasz programu Visual Studio 2015 lub Visual Studio 2017 wiele z tych kroków obsługi dla Ciebie, co znacznie zwiększa wydajność pracy.</span><span class="sxs-lookup"><span data-stu-id="30d21-121">When you are using Visual Studio 2015 or Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="30d21-122">Jest to szczególnie istotne podczas przy użyciu programu Visual Studio 2017 i przeznaczonych dla wielu kontenera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30d21-122">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="30d21-123">Na przykład tylko jednym kliknięciem, Visual Studio dodaje plik Dockerfile i docker-compose.yml pliku swoje projekty z konfiguracją aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30d21-123">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="30d21-124">Po uruchomieniu aplikacji w programie Visual Studio tworzy obraz Docker i uruchamia aplikację usługi kontenera bezpośrednio w Docker; Umożliwia ona nawet debugowanie jednocześnie kilka kontenerów.</span><span class="sxs-lookup"><span data-stu-id="30d21-124">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="30d21-125">Te funkcje będą zwiększania szybkości rozwoju.</span><span class="sxs-lookup"><span data-stu-id="30d21-125">These features will boost your development speed.</span></span>

<span data-ttu-id="30d21-126">Jednakże wyłącznie z powodu Visual Studio sprawia, że te kroki są automatyczne oznacza, że nie trzeba znać, co się dzieje na dole z Docker.</span><span class="sxs-lookup"><span data-stu-id="30d21-126">However, just because Visual Studio makes those steps automatic does not mean that you do not need to know what is going on underneath with Docker.</span></span> <span data-ttu-id="30d21-127">W związku z tym w wytycznych, który jest zgodny, możemy szczegóły każdego kroku.</span><span class="sxs-lookup"><span data-stu-id="30d21-127">Therefore, in the guidance that follows, we detail every step.</span></span>

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="30d21-128">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="30d21-128">Step 1.</span></span> <span data-ttu-id="30d21-129">Rozpoczęcie kodowania i Utwórz początkową aplikacji lub usługi linii bazowej</span><span class="sxs-lookup"><span data-stu-id="30d21-129">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="30d21-130">Opracowanie aplikacji Docker jest podobny do sposobu opracowywania aplikacji bez rozwiązania Docker.</span><span class="sxs-lookup"><span data-stu-id="30d21-130">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="30d21-131">Różnica polega na tym że podczas projektowania dla Docker, wdrażanie i testowanie aplikacji lub usługi działające w kontenerach Docker w środowisku lokalnym.</span><span class="sxs-lookup"><span data-stu-id="30d21-131">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="30d21-132">Kontener może być kontenerem Linux lub kontenera systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="30d21-132">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="30d21-133">Konfigurowanie środowiska lokalnego z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30d21-133">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="30d21-134">Aby rozpocząć, upewnij się, że [Docker Community Edition (CE)](https://www.docker.com/community-edition) dla systemu Windows zainstalowane zgodnie z objaśnieniem w poniższych instrukcji:</span><span class="sxs-lookup"><span data-stu-id="30d21-134">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="30d21-135">Rozpoczynanie pracy z rozwiązaniem Docker CE dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="30d21-135">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="30d21-136">Ponadto należy Visual Studio 2017 r zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="30d21-136">In addition, you will need Visual Studio 2017 installed.</span></span> <span data-ttu-id="30d21-137">To jest preferowana przez Visual Studio 2015 z programu Visual Studio Tools dla platformy Docker dodatku, ponieważ Visual Studio 2017 zawiera bardziej zaawansowane obsługę Docker, takich jak obsługa debugowanie kontenerów.</span><span class="sxs-lookup"><span data-stu-id="30d21-137">This is preferred over Visual Studio 2015 with the Visual Studio Tools for Docker add-in, because Visual Studio 2017 has more advanced support for Docker, like support for debugging containers.</span></span> <span data-ttu-id="30d21-138">Visual Studio 2017 obejmuje narzędzi dla platformy Docker w przypadku wybrania **.NET Core i Docker** obciążenie podczas instalacji, jak pokazano na rysunku 5-2.</span><span class="sxs-lookup"><span data-stu-id="30d21-138">Visual Studio 2017 includes the tooling for Docker if you selected the **.NET Core and Docker** workload during installation, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="30d21-139">**Rysunek 5-2**.</span><span class="sxs-lookup"><span data-stu-id="30d21-139">**Figure 5-2**.</span></span> <span data-ttu-id="30d21-140">Wybieranie **.NET Core i Docker** obciążenie podczas instalacji programu Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="30d21-140">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="30d21-141">Możesz uruchomić kodowania aplikację w zwykły .NET (zwykle w .NET Core, jeśli planujesz używanie kontenerów), nawet przed włączeniem Docker w aplikacji i wdrażanie i testowanie w Docker.</span><span class="sxs-lookup"><span data-stu-id="30d21-141">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="30d21-142">Jednak zaleca się uruchamiania pracuje Docker tak szybko, jak to możliwe, który będzie stanowić rzeczywistego środowiska, ponieważ wszelkie problemy, które mogą być wykrywane tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="30d21-142">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="30d21-143">To zaleca się ponieważ Visual Studio ułatwia więc pracować z Docker że prawie uważa przezroczysty — najlepszy przykład podczas debugowania aplikacji kontenera wielu z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30d21-143">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="30d21-144">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="30d21-144">Additional resources</span></span>

-   <span data-ttu-id="30d21-145">**Rozpoczynanie pracy z rozwiązaniem Docker CE dla systemu Windows**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span><span class="sxs-lookup"><span data-stu-id="30d21-145">**Get started with Docker CE for Windows**
[*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span></span>

-   <span data-ttu-id="30d21-146">**Visual Studio 2017**
    [*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="30d21-146">**Visual Studio 2017**
[*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span></span>

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="30d21-147">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="30d21-147">Step 2.</span></span> <span data-ttu-id="30d21-148">Utwórz plik Dockerfile związane z istniejącego obrazu podstawowego .NET</span><span class="sxs-lookup"><span data-stu-id="30d21-148">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="30d21-149">Plik Dockerfile wymagane dla każdego niestandardowego obrazu, który chcesz utworzyć; należy również plik Dockerfile dla każdego kontenera do wdrożenia, czy wdrożyć automatycznie z programu Visual Studio lub ręcznie przy użyciu interfejsu wiersza polecenia Docker (Uruchom docker i docker-tworzą poleceń).</span><span class="sxs-lookup"><span data-stu-id="30d21-149">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="30d21-150">Jeśli aplikacja zawiera pojedynczą usługę niestandardowe, należy pojedynczy plik Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="30d21-150">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="30d21-151">Jeśli aplikacja zawiera wiele usług (jak architektura mikrousług), należy jeden plik Dockerfile dla każdej usługi.</span><span class="sxs-lookup"><span data-stu-id="30d21-151">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="30d21-152">Plik Dockerfile znajduje się w folderze głównym aplikacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="30d21-152">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="30d21-153">Zawiera polecenia określające sposób ustawiania i uruchamiania aplikacji lub usługi w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="30d21-153">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="30d21-154">Można ręcznie utworzyć plik Dockerfile w kodzie i dodaj go do projektu oraz zależności platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="30d21-154">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="30d21-155">Visual Studio i jej narzędzi dla platformy Docker to zadanie wymaga tylko kilka razy kliknąć myszą.</span><span class="sxs-lookup"><span data-stu-id="30d21-155">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="30d21-156">Po utworzeniu nowego projektu w Visual Studio 2017 jest opcja o nazwie **Obsługa Włączanie kontenerów (Docker)**, jak pokazano na rysunku 5-3.</span><span class="sxs-lookup"><span data-stu-id="30d21-156">When you create a new project in Visual Studio 2017, there is an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![](./media/image5.png)

<span data-ttu-id="30d21-157">**Rysunek 5-3**.</span><span class="sxs-lookup"><span data-stu-id="30d21-157">**Figure 5-3**.</span></span> <span data-ttu-id="30d21-158">Włączanie obsługi platformy Docker, podczas tworzenia nowego projektu w programie Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="30d21-158">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="30d21-159">Można również włączyć obsługę Docker na nowy lub istniejący projekt prawym przyciskiem myszy plik projektu w programie Visual Studio i wybierając opcję **Docker Dodaj projekt obsługuje**, jak pokazano na rysunku 5-4.</span><span class="sxs-lookup"><span data-stu-id="30d21-159">You can also enable Docker support on a new or existing project by right-clicking your project file in Visual Studio and selecting the option **Add-Docker Project Support**, as shown in Figure 5-4.</span></span>

![](./media/image6.png)

<span data-ttu-id="30d21-160">**Rysunek 5-4**.</span><span class="sxs-lookup"><span data-stu-id="30d21-160">**Figure 5-4**.</span></span> <span data-ttu-id="30d21-161">Włączanie obsługi platformy Docker w istniejącego projektu programu Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="30d21-161">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="30d21-162">Ta akcja na projekt (np. aplikacji sieci Web ASP.NET lub usługi sieci Web interfejsu API) dodaje plik Dockerfile do projektu z odpowiednią konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="30d21-162">This action on a project (like an ASP.NET Web application or Web API service) adds a Dockerfile to the project with the required configuration.</span></span> <span data-ttu-id="30d21-163">Dodaje plik docker-compose.yml dla całego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="30d21-163">It also adds a docker-compose.yml file for the whole solution.</span></span> <span data-ttu-id="30d21-164">W poniższych sekcjach opisano informacje, który jest przesyłany do każdego z tych plików.</span><span class="sxs-lookup"><span data-stu-id="30d21-164">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="30d21-165">Visual Studio można nie tę pracę za Ciebie, ale warto poznać, co prowadzi do plik Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="30d21-165">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="30d21-166">Opcja A: tworzenia projektu przy użyciu istniejącego obrazu oficjalnego .NET Docker</span><span class="sxs-lookup"><span data-stu-id="30d21-166">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="30d21-167">Zazwyczaj Tworzenie niestandardowego obrazu z kontenera na podstawowy obraz można uzyskać z oficjalnego repozytorium pod adresem [Centrum Docker](https://hub.docker.com/) rejestru.</span><span class="sxs-lookup"><span data-stu-id="30d21-167">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="30d21-168">To dokładnie co się stanie w tle po włączeniu obsługi Docker w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30d21-168">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="30d21-169">Twoje plik Dockerfile użyje istniejącego obrazu aspnetcore.</span><span class="sxs-lookup"><span data-stu-id="30d21-169">Your Dockerfile will use an existing aspnetcore image.</span></span>

<span data-ttu-id="30d21-170">Wcześniej wyjaśniono firma Microsoft, które obrazy usługi Docker i repozytoriów, można użyć, w zależności od framework i wybrano systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="30d21-170">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="30d21-171">Na przykład, jeśli chcesz używać platformy ASP.NET Core (Linux lub Windows), obrazu do użycia firma microsoft / aspnetcore:2.0.</span><span class="sxs-lookup"><span data-stu-id="30d21-171">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="30d21-172">W związku z tym wystarczy określić podstawową obrazów Docker będzie używany przez Twoje kontenera.</span><span class="sxs-lookup"><span data-stu-id="30d21-172">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="30d21-173">Można to zrobić przez dodanie firmy microsoft / aspnetcore:2.0 do Twojej plik Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="30d21-173">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="30d21-174">To zostanie automatycznie wykonane przez program Visual Studio, ale gdyby zaktualizuj wersję, zaktualizuj tę wartość.</span><span class="sxs-lookup"><span data-stu-id="30d21-174">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="30d21-175">Użycie oficjalnego repozytorium obrazów .NET z Centrum Docker z numerem wersji gwarantuje, że te same funkcje języka są dostępne na wszystkich komputerach (w tym programowania, testowania i produkcji).</span><span class="sxs-lookup"><span data-stu-id="30d21-175">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="30d21-176">W poniższym przykładzie przedstawiono przykładowy plik Dockerfile kontenera platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="30d21-176">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="30d21-177">W takim przypadku kontenera jest oparty na wersji 2.0 oficjalnego obrazu platformy ASP.NET Core Docker (wielu arch dla systemów Linux i Windows).</span><span class="sxs-lookup"><span data-stu-id="30d21-177">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="30d21-178">Jest to ustawienie `FROM microsoft/aspnetcore:2.0`.</span><span class="sxs-lookup"><span data-stu-id="30d21-178">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="30d21-179">(Dodatkowe szczegóły dotyczące tego obrazu podstawowego, zobacz [platformy ASP.NET Core Docker obrazu](https://hub.docker.com/r/microsoft/aspnetcore/) strony i [.NET Core Docker obrazu](https://hub.docker.com/r/microsoft/dotnet/) strony.) W plik Dockerfile należy także poinstruować Docker nasłuchiwanie na porcie TCP, które będą używane w czasie wykonywania (w tym przypadku portu 80, zgodnie z konfiguracją z ustawieniem UWIDACZNIANIE).</span><span class="sxs-lookup"><span data-stu-id="30d21-179">(For further details about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="30d21-180">Można określić dodatkowe ustawienia konfiguracji w plik Dockerfile, w zależności od języka i framework, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="30d21-180">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="30d21-181">Na przykład wiersz punktu wejścia z \["dotnet", "MySingleContainerWebApp.dll"\] informuje Docker na uruchamianie aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30d21-181">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="30d21-182">Jeśli korzystasz z zestawu SDK i .NET Core interfejsu wiersza polecenia (dotnet interfejsu wiersza polecenia) aby skompilować i uruchomić aplikację .NET, to ustawienie będzie się różnić.</span><span class="sxs-lookup"><span data-stu-id="30d21-182">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="30d21-183">Mierzenie jest, że wiersza punktu wejścia i inne ustawienia zostaną inne w zależności od języka i platformy wybrane dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30d21-183">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="30d21-184">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="30d21-184">Additional resources</span></span>

-   <span data-ttu-id="30d21-185">**Tworzenie aplikacji programu .NET Core obrazy usługi Docker**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="30d21-185">**Building Docker Images for .NET Core Applications**
[*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span></span>

-   <span data-ttu-id="30d21-186">**Utwórz własny obraz**.</span><span class="sxs-lookup"><span data-stu-id="30d21-186">**Build your own image**.</span></span> <span data-ttu-id="30d21-187">W oficjalnej dokumentacji Docker.</span><span class="sxs-lookup"><span data-stu-id="30d21-187">In the official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="30d21-188">Przy użyciu repozytoria wielu architektury obrazu</span><span class="sxs-lookup"><span data-stu-id="30d21-188">Using multi-arch image repositories</span></span>

<span data-ttu-id="30d21-189">Pojedynczy repozytorium może zawierać wariantów platform, takich jak obraz systemu Linux i obrazu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="30d21-189">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="30d21-190">Ta funkcja umożliwia dostawcom, takich jak Microsoft (obraz podstawowy kreatory) tworzyć jednego repozytorium, aby pokrywał się wiele platform (która jest systemu Linux i Windows).</span><span class="sxs-lookup"><span data-stu-id="30d21-190">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="30d21-191">Na przykład [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repozytorium, które są dostępne w rejestrze Centrum Docker zapewnia obsługę systemu Linux i Windows Nano Server przy użyciu tej samej nazwie repozytorium.</span><span class="sxs-lookup"><span data-stu-id="30d21-191">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="30d21-192">Jeśli określisz tag, przeznaczonych dla platformy, która jest jawne, takich jak w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="30d21-192">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

-   <span data-ttu-id="30d21-193">**microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="30d21-193">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux 

-   <span data-ttu-id="30d21-194">**microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="30d21-194">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="30d21-195">Ale i jest nowy od połowy 2017, jeśli określisz tej samej nazwie obrazu, nawet z tym samym tagiem, nowych obrazów wielu architektury (na przykład aspnetcore obrazu, który obsługuje wielu arch) będą używać wersji systemu Linux lub Windows, w zależności od platformy Docker systemu operacyjnego hosta wdrażasz , jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="30d21-195">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

-   <span data-ttu-id="30d21-196">**microsoft/aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="30d21-196">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="30d21-197">Dzięki temu podczas pobierania obrazu z hostem z systemem Windows, do jego wariant systemu Windows będzie pobierać i ściąganie taką samą nazwę obrazu z hosta systemu Linux będzie pobierać wariant systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="30d21-197">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="30d21-198">Opcja B: tworzenia obrazu podstawowego od podstaw</span><span class="sxs-lookup"><span data-stu-id="30d21-198">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="30d21-199">Można utworzyć własny obraz podstawowy Docker od podstaw.</span><span class="sxs-lookup"><span data-stu-id="30d21-199">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="30d21-200">W tym scenariuszu nie jest zalecane dla kogoś, kto jest począwszy Docker, ale jeśli chcesz ustawić określone bity obrazu podstawowego, możesz to zrobić.</span><span class="sxs-lookup"><span data-stu-id="30d21-200">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="30d21-201">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="30d21-201">Additional resources</span></span>

-   <span data-ttu-id="30d21-202">**Wiele architektury .NET Core obrazów**.</span><span class="sxs-lookup"><span data-stu-id="30d21-202">**Multi-arch .NET Core images**.</span></span>
<span data-ttu-id="30d21-203">https://github.com/dotnet/announcements/issues/14</span><span class="sxs-lookup"><span data-stu-id="30d21-203">https://github.com/dotnet/announcements/issues/14</span></span> 
-   <span data-ttu-id="30d21-204">**Tworzenie obrazu podstawowego**.</span><span class="sxs-lookup"><span data-stu-id="30d21-204">**Create a base image**.</span></span> <span data-ttu-id="30d21-205">Oficjalna dokumentacja Docker.</span><span class="sxs-lookup"><span data-stu-id="30d21-205">Official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="30d21-206">Krok 3.</span><span class="sxs-lookup"><span data-stu-id="30d21-206">Step 3.</span></span> <span data-ttu-id="30d21-207">Utwórz niestandardowe obrazy usługi Docker i osadzić w nich usługi lub aplikacji</span><span class="sxs-lookup"><span data-stu-id="30d21-207">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="30d21-208">Dla każdej usługi w aplikacji należy utworzyć obraz pokrewne.</span><span class="sxs-lookup"><span data-stu-id="30d21-208">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="30d21-209">Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, wystarczy jeden obraz.</span><span class="sxs-lookup"><span data-stu-id="30d21-209">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="30d21-210">Należy pamiętać, że obrazy usługi Docker są tworzone automatycznie dla Ciebie w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30d21-210">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="30d21-211">Poniższe kroki są tylko potrzebne do edytora/CLI przepływu pracy i wyjaśniono dla jasności informacji na temat efektów poniżej.</span><span class="sxs-lookup"><span data-stu-id="30d21-211">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="30d21-212">Deweloper, musisz opracowanie i przetestowanie lokalnie, dopóki wypychanych ukończone funkcji lub zmień system kontroli źródła (na przykład, aby GitHub).</span><span class="sxs-lookup"><span data-stu-id="30d21-212">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="30d21-213">Oznacza to, że trzeba tworzyć obrazy Docker i wdrażanie kontenerów do rozwiązania Docker hosta lokalnego (Windows lub Linux VM) i uruchom, testowanie i debugowanie względem tych kontenerach lokalnego.</span><span class="sxs-lookup"><span data-stu-id="30d21-213">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="30d21-214">Aby utworzyć obraz niestandardowy w środowisku lokalnym przy użyciu interfejsu wiersza polecenia Docker i Twoje plik Dockerfile, służy polecenie docker kompilacji, tak jak rysunek 5-5.</span><span class="sxs-lookup"><span data-stu-id="30d21-214">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![](./media/image8.png)

<span data-ttu-id="30d21-215">**Rysunek 5-5**.</span><span class="sxs-lookup"><span data-stu-id="30d21-215">**Figure 5-5**.</span></span> <span data-ttu-id="30d21-216">Tworzenie niestandardowego obrazu Docker</span><span class="sxs-lookup"><span data-stu-id="30d21-216">Creating a custom Docker image</span></span>

<span data-ttu-id="30d21-217">Opcjonalnie zamiast bezpośredniego uruchamiania kompilacji docker z folderu projektu, najpierw mogą generować folderem można wdrożyć za pomocą wymaganych bibliotek .NET i pliki binarne, uruchamiając dotnet opublikować, a następnie użyj polecenia docker kompilacji.</span><span class="sxs-lookup"><span data-stu-id="30d21-217">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="30d21-218">Spowoduje to utworzenie obrazu Docker o nazwie cesardl/netcore-webapi mikrousługi-docker: pierwszy.</span><span class="sxs-lookup"><span data-stu-id="30d21-218">This will create a Docker image with the name cesardl/netcore-webapi-microservice-docker:first.</span></span> <span data-ttu-id="30d21-219">W takim przypadku: najpierw jest znacznik reprezentujący określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="30d21-219">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="30d21-220">Można Powtórz ten krok dla każdego niestandardowego obrazu potrzebnych do tworzenia aplikacji składa Docker.</span><span class="sxs-lookup"><span data-stu-id="30d21-220">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="30d21-221">Jeśli aplikacja składa się z wielu kontenerów (to znaczy jest aplikacji kontenera wielu), można również użyć rozwiązania docker compose w górę — polecenie kompilacji do kompilacji wszystkich powiązanych obrazy za pomocą jednego polecenia przy użyciu metadanych w pokrewny pliki docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="30d21-221">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="30d21-222">Można znaleźć istniejących obrazów w lokalnym repozytorium przy użyciu rozwiązania docker polecenia obrazów, jak pokazano w rysunek 5 – 6.</span><span class="sxs-lookup"><span data-stu-id="30d21-222">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![](./media/image9.png)

<span data-ttu-id="30d21-223">**Rysunek 5-6.**</span><span class="sxs-lookup"><span data-stu-id="30d21-223">**Figure 5-6.**</span></span> <span data-ttu-id="30d21-224">Wyświetlanie istniejących obrazów za pomocą polecenia docker obrazów</span><span class="sxs-lookup"><span data-stu-id="30d21-224">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="30d21-225">Tworzenie obrazów Docker z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30d21-225">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="30d21-226">Używając programu Visual Studio do tworzenia projektu z obsługą Docker, nie jawnie utworzysz obrazu.</span><span class="sxs-lookup"><span data-stu-id="30d21-226">When you are using Visual Studio to create a project with Docker support, you do not explicitly create an image.</span></span> <span data-ttu-id="30d21-227">Zamiast tego obrazu jest tworzony automatycznie podczas naciśnij klawisz F5 i uruchom dockerized aplikacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="30d21-227">Instead, the image is created for you when you press F5 and run the dockerized application or service.</span></span> <span data-ttu-id="30d21-228">Ten krok jest automatycznie w programie Visual Studio i nie będzie on być widoczny, ale należy pamiętać, że wiesz, co się dzieje na dole.</span><span class="sxs-lookup"><span data-stu-id="30d21-228">This step is automatic in Visual Studio, and you will not see it happen, but it is important that you know what is going on underneath.</span></span>

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="30d21-229">Krok 4.</span><span class="sxs-lookup"><span data-stu-id="30d21-229">Step 4.</span></span> <span data-ttu-id="30d21-230">Zdefiniuj usług w rozwiązaniu docker-compose.yml podczas kompilowania aplikacji usługi kontenera Docker</span><span class="sxs-lookup"><span data-stu-id="30d21-230">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="30d21-231">[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) pliku pozwala zdefiniować zestaw usług wdrażanych jako aplikacja składa z poleceń wdrażania.</span><span class="sxs-lookup"><span data-stu-id="30d21-231">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="30d21-232">Aby użyć plik docker-compose.yml, należy utworzyć plik w sieci głównego lub głównego folderu rozwiązania z zawartością, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="30d21-232">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3'
  
services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment: 
      - ConnectionString=Server=sql.data;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"

```

<span data-ttu-id="30d21-233">Należy pamiętać, że ten plik docker-compose.yml wersji uproszczonym i scalone.</span><span class="sxs-lookup"><span data-stu-id="30d21-233">Note that this docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="30d21-234">Zawiera dane konfiguracji statycznych dla każdego kontenera (na przykład Nazwa niestandardowego obrazu), zawsze ma to zastosowanie, oraz informacje o konfiguracji, który może być zależna od środowiska wdrażania, takie jak parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="30d21-234">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="30d21-235">W kolejnych sekcjach dowiesz się, jak można podzielić konfiguracji docker-compose.yml w wielu rozwiązania docker compose plików i Zastąp wartości w zależności od typu środowiska i wykonywanie (debugowanie czy wydanie).</span><span class="sxs-lookup"><span data-stu-id="30d21-235">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="30d21-236">Przykładowy plik docker-compose.yml definiuje pięć usługi: Usługa webmvc (aplikacja sieci web), dwa mikrousług (catalog.api i ordering.api) i jednego danych źródła kontenera, sql.data, oparte na serwerze SQL dla systemu Linux uruchomiony jako kontener.</span><span class="sxs-lookup"><span data-stu-id="30d21-236">The docker-compose.yml file example defines five services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="30d21-237">Każda usługa jest wdrażana jako kontener, więc obrazu Docker jest wymagane dla każdego.</span><span class="sxs-lookup"><span data-stu-id="30d21-237">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="30d21-238">Plik docker-compose.yml określa nie tylko kontenery, które są używane, ale ich indywidualnie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="30d21-238">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="30d21-239">Na przykład webmvc kontenera definicję w pliku .yml:</span><span class="sxs-lookup"><span data-stu-id="30d21-239">For instance, the webmvc container definition in the .yml file:</span></span>

-   <span data-ttu-id="30d21-240">Używa wbudowanych eshop / sieci web: r obrazu.</span><span class="sxs-lookup"><span data-stu-id="30d21-240">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="30d21-241">Jednak można również skonfigurować obraz, który ma zostać utworzony jako część rozwiązania docker compose wykonywania z dodatkową konfigurację oparte na kompilację: sekcji w pliku docker-compose.</span><span class="sxs-lookup"><span data-stu-id="30d21-241">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

-   <span data-ttu-id="30d21-242">Inicjuje dwie zmienne środowiskowe (adres URL katalogu i OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="30d21-242">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

-   <span data-ttu-id="30d21-243">Przekazuje dostępnego portu 80 kontenera do portu zewnętrznego 80 na komputerze hosta.</span><span class="sxs-lookup"><span data-stu-id="30d21-243">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

-   <span data-ttu-id="30d21-244">Łączy aplikacji sieci web z katalogu i kolejność usługi o zależy od\_na ustawienie.</span><span class="sxs-lookup"><span data-stu-id="30d21-244">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="30d21-245">Powoduje to, że usługa poczekać, aż te usługi są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="30d21-245">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="30d21-246">Firma Microsoft będzie ponownie plik docker-compose.yml w dalszej części, gdy firma Microsoft opisano sposobu wdrażania wielu kontenera aplikacji i mikrousług.</span><span class="sxs-lookup"><span data-stu-id="30d21-246">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="30d21-247">Praca z docker-compose.yml w programie Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="30d21-247">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="30d21-248">Po dodaniu obsługi rozwiązania Docker do projektu usługi w rozwiązaniu Visual Studio, jak pokazano w rysunek 5-7, Visual Studio dodaje plik Dockerfile do projektu i dodaje sekcji usługi (projekt) w rozwiązaniu docker-compose.yml plików.</span><span class="sxs-lookup"><span data-stu-id="30d21-248">When you add Docker solution support to a service project in a Visual Studio solution, as shown in Figure 5-7, Visual Studio adds a Dockerfile to your project, and it adds a service section (project) in your solution with the docker-compose.yml files.</span></span> <span data-ttu-id="30d21-249">To łatwy sposób redagowania rozwiązania wielu kontenera.</span><span class="sxs-lookup"><span data-stu-id="30d21-249">It is an easy way to start composing your multiple-container solution.</span></span> <span data-ttu-id="30d21-250">Można następnie otwórz plik docker-compose.yml i zaktualizować je z dodatkowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="30d21-250">You can then open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image6.png)

<span data-ttu-id="30d21-251">**Rysunek 5-7**.</span><span class="sxs-lookup"><span data-stu-id="30d21-251">**Figure 5-7**.</span></span> <span data-ttu-id="30d21-252">Dodawanie obsługi Docker w Visual Studio 2017, klikając prawym przyciskiem myszy projekt platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="30d21-252">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="30d21-253">Dodawanie obsługi Docker w programie Visual Studio nie tylko dodaje plik Dockerfile do projektu, ale dodaje informacje o konfiguracji do kilku plików globalne docker-compose.yml ustawionych na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="30d21-253">Adding Docker support in Visual Studio not only adds the Dockerfile to your project, but adds the configuration information to several global docker-compose.yml files that are set at the solution level.</span></span>

<span data-ttu-id="30d21-254">Po dodaniu obsługi Docker do rozwiązania w programie Visual Studio widoczne będzie także nowy węzeł (w pliku projektu docker compose.dcproj) w Eksploratorze rozwiązań, zawierający pliki dodane docker-compose.yml, jak pokazano na rysunku 5-8.</span><span class="sxs-lookup"><span data-stu-id="30d21-254">After you add Docker support to your solution in Visual Studio, you will also see a new node (in the docker-compose.dcproj project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![](./media/image11.PNG)

<span data-ttu-id="30d21-255">**Rysunek 5 – 8**.</span><span class="sxs-lookup"><span data-stu-id="30d21-255">**Figure 5-8**.</span></span> <span data-ttu-id="30d21-256">**Rozwiązania docker compose** węzła drzewa dodane w Eksploratorze rozwiązań 2017 r w usłudze Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30d21-256">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="30d21-257">Można wdrożyć aplikacji usługi kontenera przy użyciu pliku pojedynczego docker-compose.yml przy użyciu rozwiązania docker compose zapasowej polecenia.</span><span class="sxs-lookup"><span data-stu-id="30d21-257">You could deploy a multi-container application with a single docker-compose.yml file by using the docker-compose up command.</span></span> <span data-ttu-id="30d21-258">Jednak program Visual Studio dodaje grupę z nich, można zastąpić wartości w zależności od środowiska (Programowanie i produkcja) i wykonywania typu (wersja i debugowania).</span><span class="sxs-lookup"><span data-stu-id="30d21-258">However, Visual Studio adds a group of them so you can override values depending on the environment (development versus production) and execution type (release versus debug).</span></span> <span data-ttu-id="30d21-259">W kolejnych sekcjach opisano tej możliwości.</span><span class="sxs-lookup"><span data-stu-id="30d21-259">This capability will be explained in later sections.</span></span>

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="30d21-260">Krok 5.</span><span class="sxs-lookup"><span data-stu-id="30d21-260">Step 5.</span></span> <span data-ttu-id="30d21-261">Tworzenie i uruchamianie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="30d21-261">Build and run your Docker application</span></span>

<span data-ttu-id="30d21-262">Jeśli aplikacja ma tylko jeden kontener, można uruchomić go przez wdrożenie jej do hosta Docker (maszyny Wirtualnej lub serwerów fizycznych).</span><span class="sxs-lookup"><span data-stu-id="30d21-262">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="30d21-263">Jednak jeśli aplikacja zawiera wielu usług, możesz go wdrożyć jako składa aplikacji, za pomocą jednego polecenia interfejsu wiersza polecenia (docker składać się), lub z programem Visual Studio, która będzie używać tego polecenia w obszarze obejmuje.</span><span class="sxs-lookup"><span data-stu-id="30d21-263">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="30d21-264">Przyjrzyjmy się różne opcje.</span><span class="sxs-lookup"><span data-stu-id="30d21-264">Let’s look at the different options.</span></span>

### <a name="option-a-running-a-single-container-with-docker-cli"></a><span data-ttu-id="30d21-265">Opcja A: uruchomiony jeden kontener z interfejsu wiersza polecenia Docker</span><span class="sxs-lookup"><span data-stu-id="30d21-265">Option A: Running a single-container with Docker CLI</span></span>

<span data-ttu-id="30d21-266">Kontener Docker przy użyciu rozwiązania docker, uruchom polecenie, tak jak rysunek 5 – 9, można uruchomić:</span><span class="sxs-lookup"><span data-stu-id="30d21-266">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

<span data-ttu-id="30d21-267">**Rysunek 5 – 9**.</span><span class="sxs-lookup"><span data-stu-id="30d21-267">**Figure 5-9**.</span></span> <span data-ttu-id="30d21-268">Uruchomione w kontenerze Docker przy użyciu rozwiązania docker, uruchom polecenie</span><span class="sxs-lookup"><span data-stu-id="30d21-268">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="30d21-269">W takim przypadku polecenie wiąże wewnętrzny port 5000 kontenera do portu 80 komputerze hosta.</span><span class="sxs-lookup"><span data-stu-id="30d21-269">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="30d21-270">Oznacza to, że host jest nasłuchiwanie na porcie 80 i przekazywania ich do portu 5000 w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="30d21-270">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="30d21-271">Opcja B: uruchamiania wielu kontenera aplikacji</span><span class="sxs-lookup"><span data-stu-id="30d21-271">Option B: Running a multi-container application</span></span>

<span data-ttu-id="30d21-272">W większości przypadków przedsiębiorstwa aplikacji Docker będzie składać się z wieloma usługami, co oznacza, że należy uruchomić aplikacji kontenera usługi, jak pokazano na rysunku 5-10.</span><span class="sxs-lookup"><span data-stu-id="30d21-272">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![](./media/image14.png)

<span data-ttu-id="30d21-273">**Rysunek 5 – 10**.</span><span class="sxs-lookup"><span data-stu-id="30d21-273">**Figure 5-10**.</span></span> <span data-ttu-id="30d21-274">Maszyna wirtualna o wdrożone kontenery Docker</span><span class="sxs-lookup"><span data-stu-id="30d21-274">VM with Docker containers deployed</span></span>

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a><span data-ttu-id="30d21-275">Aplikacja usługi kontenera uruchamiana za pomocą interfejsu wiersza polecenia Docker</span><span class="sxs-lookup"><span data-stu-id="30d21-275">Running a multi-container application with the Docker CLI</span></span>

<span data-ttu-id="30d21-276">Aby uruchomić aplikacji usługi kontenera przy użyciu interfejsu wiersza polecenia Docker, należy uruchomić docker-tworzą zapasowej polecenia.</span><span class="sxs-lookup"><span data-stu-id="30d21-276">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="30d21-277">Tego polecenia używa docker-compose.yml pliku masz na poziomie rozwiązania, aby wdrożyć aplikację usługi kontenera.</span><span class="sxs-lookup"><span data-stu-id="30d21-277">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="30d21-278">Rysunek 5-11 pokazuje wyniki podczas uruchamiania polecenia w katalogu głównym projektu, który zawiera plik docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="30d21-278">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![](./media/image15.png)

<span data-ttu-id="30d21-279">**Rysunek 5-11**.</span><span class="sxs-lookup"><span data-stu-id="30d21-279">**Figure 5-11**.</span></span> <span data-ttu-id="30d21-280">Przykład wyników podczas uruchamiania rozwiązania docker compose zapasowej polecenia</span><span class="sxs-lookup"><span data-stu-id="30d21-280">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="30d21-281">Po docker-tworzą zapasowej uruchamia polecenia, aplikacji i jej powiązane kontenery są wdrażane na hoście Docker, zgodnie z opisami w reprezentacji maszyny Wirtualnej w rysunek 5 – 10.</span><span class="sxs-lookup"><span data-stu-id="30d21-281">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as illustrated in the VM representation in Figure 5-10.</span></span>

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a><span data-ttu-id="30d21-282">Uruchomiona i debugowanie aplikacji kontenera wielu z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30d21-282">Running and debugging a multi-container application with Visual Studio</span></span> 

<span data-ttu-id="30d21-283">Nie można pobrać prostsze uruchamiania aplikacji usługi kontenera przy użyciu programu Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="30d21-283">Running a multi-container application using Visual Studio 2017 cannot get simpler.</span></span> <span data-ttu-id="30d21-284">Nie można jedynie uruchomić aplikacji kontenera usługi, ale można debugować jego kontenerów bezpośrednio z programu Visual Studio przez ustawienie regularne punktów przerwania.</span><span class="sxs-lookup"><span data-stu-id="30d21-284">You can not only run the multi-container application, but you are able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="30d21-285">Jak wspomniano wcześniej, podczas każdego dodawania obsługi rozwiązania Docker do projektu w ramach rozwiązania, projektu jest skonfigurowany w pliku globalnego (poziom rozwiązania) docker-compose.yml, który można uruchomić ani debugować jednocześnie całego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="30d21-285">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="30d21-286">Visual Studio będzie uruchomić jeden kontener dla każdego projektu, który ma włączoną obsługą rozwiązania Docker i wykonania wszystkich czynności wewnętrzny (dotnet opublikować, kompilacji docker itp.).</span><span class="sxs-lookup"><span data-stu-id="30d21-286">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="30d21-287">Należy koniecznie zwrócić uwagę, jak pokazano na rysunku 5-12, w programie Visual Studio 2017 rzeczy jest dodatkowe **Docker** polecenia dla akcji klucza F5.</span><span class="sxs-lookup"><span data-stu-id="30d21-287">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="30d21-288">Ta opcja pozwala uruchomić ani debugować aplikacji kontenera aplikacji przez uruchomienie wszystkich kontenerów, które są zdefiniowane w plikach docker-compose.yml na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="30d21-288">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="30d21-289">Możliwość debugowania kontenera wielu rozwiązań oznacza, że można ustawić kilka punktów przerwania, każdy punkt przerwania w innym projekcie (kontener), a podczas debugowania w programie Visual Studio zostanie zatrzymane w punktów przerwania zdefiniowany w różnych projektów i uruchomiona na różnych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="30d21-289">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![](./media/image16.png)

<span data-ttu-id="30d21-290">**Rysunek 5 – 12**.</span><span class="sxs-lookup"><span data-stu-id="30d21-290">**Figure 5-12**.</span></span> <span data-ttu-id="30d21-291">Uruchamianie aplikacji usługi kontenera w Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="30d21-291">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="30d21-292">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="30d21-292">Additional resources</span></span>

-   <span data-ttu-id="30d21-293">**Wdrażanie kontenera ASP.NET z hostem zdalnym Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="30d21-293">**Deploy an ASP.NET container to a remote Docker host**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="30d21-294">Uwagi dotyczące testowania i wdrażania z orchestrators</span><span class="sxs-lookup"><span data-stu-id="30d21-294">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="30d21-295">Rozwiązania docker compose w górę i docker uruchomienie polecenia (lub systemem i debugowanie kontenerów w programie Visual Studio) są odpowiednie do testowania kontenery w środowisku projektowania.</span><span class="sxs-lookup"><span data-stu-id="30d21-295">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="30d21-296">Jednak nie powinni używać tej metody, jeśli ma być przeznaczona dla klastrów Docker i orchestrators, takich jak Docker Swarm, Mesosphere DC/OS lub Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="30d21-296">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="30d21-297">Jeśli używasz klastra, takie jak [Docker Swarm tryb](https://docs.docker.com/engine/swarm/) (dostępne w CE Docker dla systemu Windows i Mac od wersji 1.12), należy wdrożyć i przetestować przy użyciu dodatkowych poleceń, takich jak [tworzenia usługi docker](https://docs.docker.com/engine/reference/commandline/service_create/) dla pojedynczy usługi.</span><span class="sxs-lookup"><span data-stu-id="30d21-297">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="30d21-298">Jeśli wdrażana jest aplikacja składa się z kilku kontenery, użyj [rozwiązania docker compose pakietu](https://docs.docker.com/compose/reference/bundle/) i [docker wdrażanie myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) do wdrożenia aplikacji złożony jako *stosu*.</span><span class="sxs-lookup"><span data-stu-id="30d21-298">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="30d21-299">Aby uzyskać więcej informacji, zobacz w blogu [wprowadzenie eksperymentalne rozproszonych aplikacji pakiety](https://blog.docker.com/2016/06/docker-app-bundle/) w dokumentacji programu Docker.</span><span class="sxs-lookup"><span data-stu-id="30d21-299">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="30d21-300">w witrynie Docker.</span><span class="sxs-lookup"><span data-stu-id="30d21-300">on the Docker site.</span></span>

<span data-ttu-id="30d21-301">Aby uzyskać [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) i [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) użyje inne wdrożenie poleceń i skryptów oraz.</span><span class="sxs-lookup"><span data-stu-id="30d21-301">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="30d21-302">Krok 6.</span><span class="sxs-lookup"><span data-stu-id="30d21-302">Step 6.</span></span> <span data-ttu-id="30d21-303">Testowanie aplikacji Docker za pomocą lokalnego hosta Docker</span><span class="sxs-lookup"><span data-stu-id="30d21-303">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="30d21-304">Ten krok będą się różnić w zależności od czynności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30d21-304">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="30d21-305">W prostą aplikację .NET Core w sieci Web, który jest wdrożony jako jeden kontener lub usługi uzyskać dostęp do usługi przez otwarcie przeglądarki na hoście Docker i przechodząc do tej lokacji, jak pokazano w rysunek 5-13.</span><span class="sxs-lookup"><span data-stu-id="30d21-305">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site as shown in Figure 5-13.</span></span> <span data-ttu-id="30d21-306">(Jeśli konfiguracji w plik Dockerfile mapuje kontenera do portu na hoście, który jest inny niż 80, m.in. port hosta w adresie URL).</span><span class="sxs-lookup"><span data-stu-id="30d21-306">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![](./media/image18.png)

<span data-ttu-id="30d21-307">**Rysunek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="30d21-307">**Figure 5-13**.</span></span> <span data-ttu-id="30d21-308">Przykład testowania aplikacji Docker lokalnie za pomocą localhost</span><span class="sxs-lookup"><span data-stu-id="30d21-308">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="30d21-309">Jeśli nie wskazuje localhost Docker adres IP hosta (domyślnie, gdy przy użyciu rozwiązania Docker CE, powinien), aby poruszać się z usługą, użyj adresu IP karty sieciowej tego komputera.</span><span class="sxs-lookup"><span data-stu-id="30d21-309">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="30d21-310">Należy pamiętać, że na przykład kontenerem omawiana tego adresu URL w przeglądarce korzysta z portu 80.</span><span class="sxs-lookup"><span data-stu-id="30d21-310">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="30d21-311">Jednak wewnętrznie żądania nastąpi przekierowanie do portu 5000, ponieważ który był jak została wdrożona z docker, uruchom polecenie, zgodnie z objaśnieniem w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="30d21-311">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="30d21-312">Może także przetestować aplikacji przy użyciu programu curl z terminalu, jak pokazano w rysunek 5-14.</span><span class="sxs-lookup"><span data-stu-id="30d21-312">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="30d21-313">W przypadku instalacji Docker w systemie Windows Docker IP hosta są zawsze domyślnie 10.0.75.1 Oprócz rzeczywisty adres IP komputera.</span><span class="sxs-lookup"><span data-stu-id="30d21-313">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![](./media/image19.png)

<span data-ttu-id="30d21-314">**Rysunek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="30d21-314">**Figure 5-14**.</span></span> <span data-ttu-id="30d21-315">Przykład testowania aplikacji Docker lokalnie przy użyciu programu curl</span><span class="sxs-lookup"><span data-stu-id="30d21-315">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="30d21-316">Testowanie i debugowanie kontenerów wyposażonych w Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="30d21-316">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="30d21-317">Podczas uruchamiania i debugowanie kontenerów wyposażonych w Visual Studio 2017 r, można debugować aplikacji .NET w podobny sposób jak w przypadku braku kontenerów.</span><span class="sxs-lookup"><span data-stu-id="30d21-317">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="30d21-318">Testowanie i debugowanie bez programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30d21-318">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="30d21-319">Jeśli tworzysz podejście Edytor/CLI trudniej jest debugowanie kontenerów i można debugować generując śladów.</span><span class="sxs-lookup"><span data-stu-id="30d21-319">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="30d21-320">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="30d21-320">Additional resources</span></span>

-   <span data-ttu-id="30d21-321">**Debugowanie aplikacji w kontenerze Docker lokalnego**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="30d21-321">**Debugging apps in a local Docker container**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

-   <span data-ttu-id="30d21-322">**Steve Lasker. Tworzenie, debugowanie, wdrażanie aplikacji platformy ASP.NET Core przy użyciu rozwiązania Docker.**</span><span class="sxs-lookup"><span data-stu-id="30d21-322">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="30d21-323">Wideo.</span><span class="sxs-lookup"><span data-stu-id="30d21-323">Video.</span></span>
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="30d21-324">Uproszczony przepływu pracy podczas opracowywania kontenery z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30d21-324">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="30d21-325">W rezultacie przepływu pracy przy użyciu programu Visual Studio jest znacznie prostsze niż w przypadku użycia metody Edytor/interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="30d21-325">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="30d21-326">Większość czynności wymagane przez Docker powiązane plik Dockerfile i docker-compose.yml pliki są ukryte lub uproszczony przez program Visual Studio, jak pokazano w rysunek 5 – 15.</span><span class="sxs-lookup"><span data-stu-id="30d21-326">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![](./media/image20.png)

<span data-ttu-id="30d21-327">**Rysunek 5 – 15**.</span><span class="sxs-lookup"><span data-stu-id="30d21-327">**Figure 5-15**.</span></span> <span data-ttu-id="30d21-328">Uproszczony przepływu pracy podczas opracowywania w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30d21-328">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="30d21-329">Ponadto należy wykonać krok 2 (Obsługa Docker dodawanie do projektów) tylko raz.</span><span class="sxs-lookup"><span data-stu-id="30d21-329">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="30d21-330">W związku z tym przepływu pracy jest podobna do zadań programowania zwykle, gdy dla innych Programowanie przy użyciu platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="30d21-330">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="30d21-331">Musisz wiedzieć, co dzieje się w obszarze obejmuje (procesu tworzenia obrazu, jakie obrazy podstawowe używasz, wdrożenia kontenerów, itp.) i czasami się, że należy również edytować plik Dockerfile lub docker-compose.yml plik, aby dostosować zachowania.</span><span class="sxs-lookup"><span data-stu-id="30d21-331">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="30d21-332">Jednak znacznie upraszcza większość zadań za pomocą programu Visual Studio, co możesz znacznie większą wydajność.</span><span class="sxs-lookup"><span data-stu-id="30d21-332">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="30d21-333">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="30d21-333">Additional resources</span></span>

-   <span data-ttu-id="30d21-334">**Steve Lasker. .NET — rozwój docker z programu Visual Studio 2017 r.**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span><span class="sxs-lookup"><span data-stu-id="30d21-334">**Steve Lasker. .NET Docker Development with Visual Studio 2017**
[*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span></span>

-   <span data-ttu-id="30d21-335">**Jeffrey T. Fritz. Umieść aplikacji .NET Core w kontenerze o nowe narzędzia Docker dla programu Visual Studio**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span><span class="sxs-lookup"><span data-stu-id="30d21-335">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**
[*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span></span>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="30d21-336">Za pomocą poleceń programu PowerShell w plik Dockerfile skonfigurować kontenery systemu Windows</span><span class="sxs-lookup"><span data-stu-id="30d21-336">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="30d21-337">[Kontenery systemu Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) umożliwiają konwertowanie istniejących aplikacji systemu Windows na obrazy usługi Docker i wdrażać je z tego samego narzędzia jako rest ekosystemu Docker.</span><span class="sxs-lookup"><span data-stu-id="30d21-337">[Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="30d21-338">Aby użyć kontenery systemu Windows, należy uruchomić polecenia programu PowerShell w plik Dockerfile, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="30d21-338">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="30d21-339">W takim przypadku wiemy przy użyciu podstawowy obraz systemu Windows Server Core (ustawienie FROM) i instalacji usług IIS za pomocą polecenia programu PowerShell (ustawienie URUCHAMIANIA).</span><span class="sxs-lookup"><span data-stu-id="30d21-339">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="30d21-340">W podobny sposób poleceń programu PowerShell można użyć również do skonfigurowania dodatkowych składników, takich jak ASP.NET 4.x, .NET 4.6 lub innego oprogramowania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="30d21-340">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="30d21-341">Na przykład następujące polecenie w plik Dockerfile konfiguruje ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="30d21-341">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="30d21-342">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="30d21-342">Additional resources</span></span>

-   <span data-ttu-id="30d21-343">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="30d21-343">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="30d21-344">Przykład polecenia programu Powershell do uruchamiania z dockerfiles dołączenie funkcji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="30d21-344">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
<span data-ttu-id="30d21-345">[Poprzednie](index.md)
[dalej](../net-core-single-containers-linux-windows-server-hosts/index.md)</span><span class="sxs-lookup"><span data-stu-id="30d21-345">[Previous](index.md)
[Next](../net-core-single-containers-linux-windows-server-hosts/index.md)</span></span>
