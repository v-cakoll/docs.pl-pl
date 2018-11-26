---
title: Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/05/2018
ms.openlocfilehash: 00cffde7e7eb548f755b60f64aa596210b570d07
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297520"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="7a2e9-103">Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="7a2e9-103">Development workflow for Docker apps</span></span>

<span data-ttu-id="7a2e9-104">Każdy deweloper maszyny, których Deweloper kody aplikacji przy użyciu preferowanego języka i sprawdza ją lokalnie rozpoczyna się cyklu tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-104">The application development life cycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="7a2e9-105">Niezależnie od tego, które języków i platformy, deweloper zdecyduje, w tym przepływie pracy dewelopera jest zawsze opracowywania i testowania kontenerów platformy Docker, ale sposób lokalnie.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-105">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="7a2e9-106">Każdy kontener (wystąpienia obrazu platformy Docker) obejmuje następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="7a2e9-106">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="7a2e9-107">Wybór systemu operacyjnego (na przykład dystrybucji systemu Linux, Windows Nano Server lub Windows Server Core).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-107">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

- <span data-ttu-id="7a2e9-108">Pliki dodawane przez dewelopera (pliki binarne aplikacji itp.).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-108">Files added by the developer (application binaries, etc.).</span></span>

- <span data-ttu-id="7a2e9-109">Informacje o konfiguracji (ustawienia środowiska i zależności).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-109">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="7a2e9-110">Przepływ pracy na potrzeby tworzenia aplikacji opartych na kontenerach platformy Docker</span><span class="sxs-lookup"><span data-stu-id="7a2e9-110">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="7a2e9-111">W tej sekcji opisano *pętli wewnętrzny* przepływ pracy tworzenia oprogramowania dla aplikacji opartych na kontenerach platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-111">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="7a2e9-112">Przepływ pracy wewnętrznej pętli oznacza, że to nie biorąc pod uwagę szersze przepływ pracy DevOps i po prostu koncentruje się na rozwoju pracy na komputerze dewelopera.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-112">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="7a2e9-113">Początkowe kroki konfigurowania środowiska nie są dołączane, ponieważ te są wykonywane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-113">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="7a2e9-114">Aplikacja składa się z własnych usług, a także dodatkowe biblioteki (zależności).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-114">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="7a2e9-115">Poniżej przedstawiono podstawowe kroki, które zwykle wykonać podczas kompilowania aplikacji platformy Docker, jak pokazano w rysunek 5-1.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-115">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![Instrukcje krok po kroku przepływu pracy tworzenia grafiki konteneryzowanych aplikacji platformy Docker](./media/image1.png)

<span data-ttu-id="7a2e9-117">**Rysunek 5-1.**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-117">**Figure 5-1.**</span></span> <span data-ttu-id="7a2e9-118">Instrukcje krok po kroku przepływu pracy do tworzenia aplikacji kontenerowych nimi platformy Docker</span><span class="sxs-lookup"><span data-stu-id="7a2e9-118">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="7a2e9-119">W tym przewodniku opisano szczegółowo całego tego procesu i na każdym kroku głównych zostało wyjaśnione, skupiając się na środowisko Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-119">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="7a2e9-120">Korzystając z podejście do tworzenia edytora/CLI (na przykład programu Visual Studio Code oraz interfejsu wiersza polecenia platformy Docker w systemie macOS lub Windows), musisz wiedzieć każdego kroku, zazwyczaj bardziej szczegółowo niż Jeśli używasz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-120">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="7a2e9-121">Aby uzyskać więcej informacji na temat pracy w środowisku interfejsu wiersza polecenia, zobacz książki elektronicznej [cykl życia aplikacji kontenerowych nimi platformy Docker z Platforms i narzędzi Microsoft](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-121">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="7a2e9-122">Podczas korzystania z programu Visual Studio, wiele z tych kroków są obsługiwane dla Ciebie, co znacznie zwiększa wydajność pracy.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-122">When you're using Visual Studio, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="7a2e9-123">Jest to szczególnie istotne w przypadku, gdy są przy użyciu programu Visual Studio 2017 i ustawianie elementów docelowych wielokontenerowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-123">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="7a2e9-124">Na przykład w tylko jednym kliknięciem, program Visual Studio dodaje *pliku Dockerfile* i *docker-compose.yml* plików do swoich projektów za pomocą konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-124">For instance, with just one mouse click, Visual Studio adds the *Dockerfile* and *docker-compose.yml* files to your projects with the configuration for your application.</span></span> <span data-ttu-id="7a2e9-125">Po uruchomieniu aplikacji w programie Visual Studio tworzy obraz platformy Docker i uruchamia aplikację obsługującą wiele kontenerów bezpośrednio na platformie Docker.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-125">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker.</span></span> <span data-ttu-id="7a2e9-126">Umożliwia ona nawet jednocześnie debugowanie kilka kontenerów.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-126">It even allows you to debug several containers at once.</span></span> <span data-ttu-id="7a2e9-127">Te funkcje zwiększania szybkiego rozwoju.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-127">These features boost your development speed.</span></span>

<span data-ttu-id="7a2e9-128">Do wytycznych, który następuje po Wyjaśnijmy, co dzieje się "dzieje się w tle" za pomocą platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-128">In the guidance that follows, we explain what's happening "under the covers" with Docker.</span></span>

![Krok 1 — kod aplikacji grafiki](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="7a2e9-130">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-130">Step 1.</span></span> <span data-ttu-id="7a2e9-131">Rozpocznij kodowanie i tworzenie początkowej aplikacja lub usługa linii bazowej</span><span class="sxs-lookup"><span data-stu-id="7a2e9-131">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="7a2e9-132">Tworzenie aplikacji platformy Docker to podobnie, jak opracować aplikację bez platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-132">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="7a2e9-133">Różnica jest, że podczas tworzenia dla platformy Docker, są wdrażanie i testowanie aplikacji lub usług działających w kontenerach platformy Docker w środowisku lokalnym.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-133">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="7a2e9-134">Kontener może być kontenera systemu Linux lub kontenerów Windows.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-134">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="7a2e9-135">Konfigurowanie środowiska lokalnego z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a2e9-135">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="7a2e9-136">Aby rozpocząć, upewnij się, że masz [Docker Community Edition (CE)](https://www.docker.com/community-edition) dla Windows zainstalowany zgodnie z opisem w poniższych instrukcjach:</span><span class="sxs-lookup"><span data-stu-id="7a2e9-136">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="7a2e9-137">Wprowadzenie do platformy Docker CE dla Windows</span><span class="sxs-lookup"><span data-stu-id="7a2e9-137">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="7a2e9-138">Ponadto konieczne Visual Studio 2017 z **programowanie dla wielu platform .NET Core** obciążenia zainstalowany, jak pokazano w rysunek 5-2.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-138">In addition, you need Visual Studio 2017 with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="7a2e9-139">**Rysunek 5-2**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-139">**Figure 5-2**.</span></span> <span data-ttu-id="7a2e9-140">Wybieranie **.NET Core i Docker** obciążenie podczas instalacji programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7a2e9-140">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="7a2e9-141">Możesz rozpocząć kodowanie swoją aplikację w zwykły .NET (zwykle w .NET Core, jeśli planowane jest korzystanie z kontenerów), nawet przed włączeniem platformy Docker w aplikacji i wdrażanie i testowanie na platformie Docker.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-141">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="7a2e9-142">Jednak zaleca się uruchamiania nad platformy Docker tak szybko, jak to możliwe, ponieważ się rzeczywistego środowiska i wszelkie problemy, które mogą być wykrywane tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-142">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="7a2e9-143">To zaleca się, ponieważ dzięki programowi Visual Studio tak łatwe do pracy z rozwiązaniem Docker, że niemal pozornie przezroczyste — najlepszy przykład podczas debugowania aplikacji obsługującej wiele kontenerów za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-143">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent — the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7a2e9-144">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="7a2e9-144">Additional resources</span></span>

- <span data-ttu-id="7a2e9-145">**Wprowadzenie do platformy Docker CE dla Windows**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-145">**Get started with Docker CE for Windows**</span></span>

   [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

- <span data-ttu-id="7a2e9-146">**Visual Studio 2017**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-146">**Visual Studio 2017**</span></span>

   [*https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![Krok 2 — grafika zapisu plików Dockerfile](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="7a2e9-148">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-148">Step 2.</span></span> <span data-ttu-id="7a2e9-149">Tworzenie pliku Dockerfile związane z istniejącego obrazu podstawowego platformy .NET</span><span class="sxs-lookup"><span data-stu-id="7a2e9-149">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="7a2e9-150">Potrzebujesz pliku Dockerfile dla niestandardowego obrazu, z którą chcesz skompilować; należy również plik Dockerfile dla każdego kontenera do wdrożenia, czy wdrożyć automatycznie z programu Visual Studio lub ręcznie przy użyciu interfejsu wiersza polecenia platformy Docker (docker, uruchom i docker-compose poleceń).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-150">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="7a2e9-151">Jeśli aplikacja zawiera pojedynczą usługę niestandardowych, konieczne będzie pojedynczego pliku Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-151">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="7a2e9-152">Jeśli aplikacja zawiera wiele usług (tak jak w architekturze mikrousług), należy jeden plik Dockerfile dla każdej usługi.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-152">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="7a2e9-153">Plik Dockerfile znajduje się w folderze głównym aplikacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-153">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="7a2e9-154">Zawiera polecenia, określające sposób konfigurowania i uruchamiania aplikacji lub usługi w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-154">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="7a2e9-155">Można ręcznie utworzyć plik Dockerfile w kodzie i dodać go do projektu, wraz z zależności .NET.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-155">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="7a2e9-156">Program Visual Studio Tools for Docker to zadanie wymaga tylko kilku kliknięć myszą.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-156">With Visual Studio Tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="7a2e9-157">Po utworzeniu nowego projektu w programie Visual Studio 2017 jest dostępna opcja o nazwie **włączyć obsługę platformy Docker**, jak pokazano w rysunek 5-3.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-157">When you create a new project in Visual Studio 2017, there's an option named **Enable Docker Support**, as shown in Figure 5-3.</span></span>

![Włączanie obsługi platformy Docker, podczas tworzenia nowego projektu w programie Visual Studio 2017](./media/image5.png)

<span data-ttu-id="7a2e9-159">**Rysunek 5-3**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-159">**Figure 5-3**.</span></span> <span data-ttu-id="7a2e9-160">Włączanie obsługi platformy Docker, podczas tworzenia nowego projektu w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7a2e9-160">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="7a2e9-161">Można również włączyć obsługę platformy Docker w istniejącym projekcie aplikacji sieci web platformy .NET Core, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając polecenie **Dodaj** > **obsługę platformy Docker** , jak pokazano na rysunku 5-4.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-161">You can also enable Docker support on an existing .NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support**, as shown in Figure 5-4.</span></span>

![Dodaj opcję menu pomocy technicznej platformy Docker w programie Visual Studio](./media/add-docker-support.png)

<span data-ttu-id="7a2e9-163">**Rysunek 5-4**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-163">**Figure 5-4**.</span></span> <span data-ttu-id="7a2e9-164">Włączanie obsługi platformy Docker w istniejącym projekcie programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7a2e9-164">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="7a2e9-165">Ta akcja spowoduje dodanie *pliku Dockerfile* do projektu za pomocą wymaganej konfiguracji i jest dostępny tylko dla projektów aplikacji sieci web platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-165">This action adds a *Dockerfile* to the project with the required configuration, and is only available on .NET Core web app projects.</span></span>

<span data-ttu-id="7a2e9-166">Aby dodać *docker-compose.yml* plików dla całego rozwiązania, kliknij prawym przyciskiem myszy nad projektem w **Eksploratora rozwiązań** i wybierz **Dodaj**  >   **Obsługa Orkiestratora kontenerów**, jak pokazano na rysunku 5-5.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-166">To add a *docker-compose.yml* file for the whole solution, right-click on the project in **Solution Explorer** and select **Add** > **Container Orchestrator Support**, as shown in Figure 5-5.</span></span>

![Dodaj opcję menu pomocy technicznej koordynatora kontenerów w programie Visual Studio](./media/add-container-orchestrator-support.png)

<span data-ttu-id="7a2e9-168">**Rysunek 5-5**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-168">**Figure 5-5**.</span></span> <span data-ttu-id="7a2e9-169">Dodawanie obsługi orkiestratora kontenerów do istniejącego projektu w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-169">Adding container orchestrator support to an existing project in Visual Studio 2017.</span></span>

<span data-ttu-id="7a2e9-170">W poniższych sekcjach opisano informacje, które przechodzi do każdego z tych plików.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-170">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="7a2e9-171">Program Visual Studio można wykonać to zadanie dla Ciebie, ale warto zrozumieć, co jest umieszczane w pliku Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-171">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="7a2e9-172">Opcja A: Tworzenie projektu przy użyciu istniejących oficjalnego obrazu Docker w programie .NET</span><span class="sxs-lookup"><span data-stu-id="7a2e9-172">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="7a2e9-173">Zazwyczaj Tworzenie niestandardowego obrazu kontenera na podstawie obrazu podstawowego można uzyskać z oficjalnego repozytorium na [usługi Docker Hub](https://hub.docker.com/) rejestru.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-173">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="7a2e9-174">To jest dokładnie co się dzieje w tle po włączeniu obsługi platformy Docker w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-174">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="7a2e9-175">Plik Dockerfile używa istniejący obraz aspnetcore.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-175">The Dockerfile uses an existing aspnetcore image.</span></span>

<span data-ttu-id="7a2e9-176">Wcześniej opisano firma Microsoft, które obrazów platformy Docker i repozytoriów, można użyć w zależności od framework i systemu operacyjnego zostały wybrane.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-176">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="7a2e9-177">Na przykład, jeśli chcesz użyć programu ASP.NET Core (Linux lub Windows), obrazu do wykorzystania jest microsoft / aspnetcore:2.0.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-177">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="7a2e9-178">W związku z tym wystarczy określić, jakie podstawowego obrazu platformy Docker, który będzie używany dla kontenera.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-178">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="7a2e9-179">Można to zrobić, dodając firmy microsoft / aspnetcore:2.0 do Twojego pliku Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-179">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="7a2e9-180">Jest to wykonywane automatycznie przez program Visual Studio, ale w przypadku zaktualizowania wersji zaktualizuj tę wartość.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-180">This is automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="7a2e9-181">Oficjalna repozytorium obrazów platformy .NET z usługi Docker Hub przy użyciu numeru wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym programowanie, testowanie i produkcja).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-181">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="7a2e9-182">Poniższy kod przedstawia przykładowy plik Dockerfile dla kontenera platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-182">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0

ARG source

WORKDIR /app

EXPOSE 80

COPY ${source:-obj/Docker/publish} .

ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="7a2e9-183">W tym przypadku kontener zależy od wersji 2.0 oficjalny obraz platformy Docker programu ASP.NET Core (wielu arch dla systemów Linux i Windows).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-183">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="7a2e9-184">Jest to ustawienie `FROM microsoft/aspnetcore:2.0`.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-184">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="7a2e9-185">(Aby uzyskać więcej informacji na temat tego obrazu podstawowego zobacz [obrazu platformy Docker programu ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) strony i [obrazu platformy Docker programu .NET Core](https://hub.docker.com/r/microsoft/dotnet/) strony.) W pliku Dockerfile trzeba będzie również poinstruować platformy Docker do nasłuchiwania na porcie TCP, używane w czasie wykonywania (w tym przypadku port 80, zgodnie z konfiguracją z ustawieniem UDOSTĘPNIAJĄ).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-185">(For more information about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="7a2e9-186">Można określić dodatkowe ustawienia konfiguracji w pliku Dockerfile, w zależności od języka i struktury, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-186">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="7a2e9-187">Na przykład wiersz punktu wejścia z \["dotnet", "MySingleContainerWebApp.dll"\] platformy docker, aby uruchomić aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-187">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="7a2e9-188">Jeśli używasz zestawu SDK i .NET Core interfejsu wiersza polecenia (interfejsu wiersza polecenia platformy dotnet) aby skompilować i uruchomić aplikację .NET, to ustawienie będzie inny.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-188">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="7a2e9-189">Mierzenie to, że wiersz punktu wejścia i inne ustawienia będą różnić w zależności od języka i platformy, wybrany dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-189">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7a2e9-190">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="7a2e9-190">Additional resources</span></span>

- <span data-ttu-id="7a2e9-191">**Tworzenie obrazów platformy Docker dla aplikacji .NET Core**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-191">**Building Docker Images for .NET Core Applications**</span></span>

   [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

- <span data-ttu-id="7a2e9-192">**Tworzenie własnego obrazu**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-192">**Build your own image**.</span></span> <span data-ttu-id="7a2e9-193">W oficjalnej dokumentacji platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-193">In the official Docker documentation.</span></span>

   [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="7a2e9-194">Przy użyciu repozytoriów wielu architektury obrazu</span><span class="sxs-lookup"><span data-stu-id="7a2e9-194">Using multi-arch image repositories</span></span>

<span data-ttu-id="7a2e9-195">Jednym repozytorium może zawierać warianty platformy, takich jak obraz systemu Linux i Windows obraz.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-195">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="7a2e9-196">Ta funkcja umożliwia dostawców, takich jak Microsoft (obraz podstawowy dla twórców) do utworzenia pojedynczego repozytorium na pokrycie wiele platform (dotyczy to systemów Linux i Windows).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-196">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="7a2e9-197">Na przykład [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repozytorium, które są dostępne w rejestrze usługi Docker Hub zapewnia obsługę dla systemów Linux i Windows Nano Server przy użyciu tej samej nazwy repozytorium.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-197">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="7a2e9-198">Jeśli określony tag, przeznaczonych dla platformy, która jest jawne, takich jak w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="7a2e9-198">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- <span data-ttu-id="7a2e9-199">**microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-199">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux

- <span data-ttu-id="7a2e9-200">**microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-200">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="7a2e9-201">Jednak i to jest nowy od połowy 2017 r. w przypadku określenia taką samą nazwę obrazu, nawet w przypadku tego samego tagu, nowe obrazy wielu architektury (na przykład obraz aspnetcore obsługuje wielu arch) będą używać wersji systemu Linux lub Windows, w zależności od hosta platformy Docker systemu operacyjnego, który jest wdrażany , jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7a2e9-201">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image, which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

- <span data-ttu-id="7a2e9-202">**microsoft/aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-202">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="7a2e9-203">Dzięki temu podczas ściągnąć obraz z hosta Windows go każda będzie ściągać wariant Windows i ściągania taką samą nazwę obrazu na hoście z systemem Linux każda będzie ściągać wariantów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-203">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="7a2e9-204">Opcja B: tworzenia obrazu podstawowego od podstaw</span><span class="sxs-lookup"><span data-stu-id="7a2e9-204">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="7a2e9-205">Można utworzyć własny obraz podstawowy platformy Docker, od podstaw.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-205">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="7a2e9-206">W tym scenariuszu nie jest zalecane w przypadku osobą, która jest uruchamiana przy użyciu rozwiązania Docker, ale jeśli chcesz ustawić bity określonego obrazu podstawowego, możesz to zrobić.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-206">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7a2e9-207">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="7a2e9-207">Additional resources</span></span>

- <span data-ttu-id="7a2e9-208">**Wielu architektury obrazów platformy .NET Core**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-208">**Multi-arch .NET Core images**.</span></span>

   https://github.com/dotnet/announcements/issues/14

- <span data-ttu-id="7a2e9-209">**Tworzenie obrazu podstawowego**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-209">**Create a base image**.</span></span> <span data-ttu-id="7a2e9-210">Oficjalna dokumentacja platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-210">Official Docker documentation.</span></span>

   [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![Krok 3 — Tworzenie obrazów grafiki](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="7a2e9-212">Krok 3.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-212">Step 3.</span></span> <span data-ttu-id="7a2e9-213">Tworzenie niestandardowych obrazów platformy Docker i osadzanie aplikacji lub usługi w nich</span><span class="sxs-lookup"><span data-stu-id="7a2e9-213">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="7a2e9-214">Dla każdej usługi w aplikacji należy utworzyć obraz powiązane.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-214">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="7a2e9-215">Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, wystarczy pojedynczego obrazu.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-215">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="7a2e9-216">Obrazy platformy Docker są tworzone automatycznie dla Ciebie w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-216">The Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="7a2e9-217">Poniższe kroki są tylko potrzebne dla przepływu pracy edytorze/interfejsu wiersza polecenia i wyjaśnione w celu uściślenia, o co się stanie, poniżej.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-217">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="7a2e9-218">Jako deweloper musisz opracowywać i testować lokalnie, przed wypchnięciem ukończonych funkcji lub zmień wartość na system kontroli źródła (na przykład w usłudze GitHub).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-218">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="7a2e9-219">Oznacza to, że trzeba tworzenie obrazów platformy Docker i wdrażanie kontenerów do lokalnego hosta platformy Docker (Windows lub maszyny Wirtualnej systemu Linux) i uruchamianie, testowanie i debugowanie względem tych kontenerów lokalnego.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-219">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="7a2e9-220">Aby utworzyć niestandardowy obraz w środowisku lokalnym przy użyciu interfejsu wiersza polecenia platformy Docker i z pliku Dockerfile, można użyć polecenia kompilacji platformy docker, tak jak rysunek 5-5.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-220">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Tworzenie niestandardowego obrazu platformy Docker](./media/image8.png)

<span data-ttu-id="7a2e9-222">**Rysunek 5-5**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-222">**Figure 5-5**.</span></span> <span data-ttu-id="7a2e9-223">Tworzenie niestandardowego obrazu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="7a2e9-223">Creating a custom Docker image</span></span>

<span data-ttu-id="7a2e9-224">Opcjonalnie zamiast bezpośredniego uruchamiania kompilacji platformy docker z folderu projektu, możesz najpierw wygenerować folderem do wdrożenia przy użyciu wymaganych bibliotek .NET i pliki binarne, uruchamiając polecenia dotnet publikowania, a następnie użyj polecenia kompilacji platformy docker.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-224">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="7a2e9-225">Spowoduje to utworzenie obrazu platformy Docker o nazwie **cesardl/netcore-webapi mikrousługi — docker: pierwszy**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-225">This will create a Docker image with the name **cesardl/netcore-webapi-microservice-docker:first**.</span></span> <span data-ttu-id="7a2e9-226">W tym przypadku: pierwszy to znacznik reprezentujący określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-226">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="7a2e9-227">Za Powtórz ten krok dla każdego obrazu niestandardowego, potrzebne do tworzenia aplikacji platformy Docker złożone.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-227">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="7a2e9-228">Jeśli aplikacja składa się z wielu kontenerów (czyli jest aplikację obsługującą wiele kontenerów), można również użyć narzędzia docker compose się — polecenie kompilacji, aby skompilować wszystkie obrazy powiązane z jednym poleceniem, posługując się metadanymi ujawnione w powiązane pliki docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-228">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="7a2e9-229">Można znaleźć istniejących obrazów w repozytorium lokalnym za pomocą platformy docker polecenie obrazów, jak pokazano w rysunek 5 – 6.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-229">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Wyświetlanie istniejących obrazów za pomocą polecenia obrazów platformy docker](./media/image9.png)

<span data-ttu-id="7a2e9-231">**Rysunek 5 – 6.**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-231">**Figure 5-6.**</span></span> <span data-ttu-id="7a2e9-232">Wyświetlanie istniejących obrazów za pomocą polecenia obrazów platformy docker</span><span class="sxs-lookup"><span data-stu-id="7a2e9-232">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="7a2e9-233">Tworzenie obrazów platformy Docker za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a2e9-233">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="7a2e9-234">Podczas tworzenia projektu z obsługą platformy Docker przy użyciu programu Visual Studio, nie są jawnie tworzone obrazu.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-234">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="7a2e9-235">Zamiast tego obrazu zostanie utworzony po naciśnięciu klawisza **F5** do uruchamiania dockerized aplikacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-235">Instead, the image is created for you when you press **F5** to run the dockerized application or service.</span></span> <span data-ttu-id="7a2e9-236">Ten krok jest automatycznie w programie Visual Studio i nie będziesz widzieć praca, ale jest ważne, że wiesz, co się dzieje na dole.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-236">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![Krok 4 — Definiowanie usług grafiki](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="7a2e9-238">Krok 4.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-238">Step 4.</span></span> <span data-ttu-id="7a2e9-239">Zdefiniuj swoje usługi w docker-compose.yml, podczas kompilowania aplikacji platformy Docker z wieloma kontenerami</span><span class="sxs-lookup"><span data-stu-id="7a2e9-239">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="7a2e9-240">[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) pliku pozwala zdefiniować zestaw powiązanych usług, który można wdrożyć jako złożone aplikacji za pomocą poleceń wdrażania.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-240">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="7a2e9-241">Aby użyć pliku docker-compose.yml, musisz utworzyć głównego pliku lub folderu głównego rozwiązania z zawartością, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7a2e9-241">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

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

<span data-ttu-id="7a2e9-242">Ten plik docker-compose.yml jest nieco uproszczona i scalone.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-242">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="7a2e9-243">Zawiera on statyczne dane konfiguracji dla każdego kontenera (na przykład nazwa obrazu niestandardowego), która zawsze ma to zastosowanie, a także informacje o konfiguracji, które mogą być zależne od środowiska wdrażania, takie jak parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-243">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="7a2e9-244">W kolejnych sekcjach dowiesz się, jak można podzielić na wiele konfiguracji platformy docker-compose.yml docker-compose plików i zastąpienie wartości w zależności od typu środowiska i wykonywanie (debugowanie lub wydanie).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-244">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="7a2e9-245">Przykład pliku docker-compose.yml definiuje czterema usługami: webmvc usługi (aplikacja sieci web), dwa mikrousługi (catalog.api i ordering.api) i jeden źródłowy kontener danych, sql.data, oparte na programie SQL Server dla uruchomionego jako kontener systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-245">The docker-compose.yml file example defines four services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="7a2e9-246">Każda usługa jest wdrażana jako kontener, dzięki czemu obraz platformy Docker jest wymagana dla każdego.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-246">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="7a2e9-247">Plik docker-compose.yml określa nie tylko jakie kontenery są używane, ale ich indywidualnie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-247">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="7a2e9-248">Na przykład webmvc definicja kontenera w plik yml:</span><span class="sxs-lookup"><span data-stu-id="7a2e9-248">For instance, the webmvc container definition in the .yml file:</span></span>

- <span data-ttu-id="7a2e9-249">Używa wstępnie skompilowanych eshop / sieci web: latest obrazu.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-249">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="7a2e9-250">Jednakże można także skonfigurować obraz, który ma zostać utworzony jako część narzędzia docker compose wykonywania bez dodatkowej konfiguracji oparte na kompilację: sekcji w pliku docker-compose.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-250">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="7a2e9-251">Inicjuje dwóch zmiennych środowiskowych (adres URL katalogu i OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-251">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="7a2e9-252">Przekazuje narażonych port 80 w kontenerze na zewnętrzny port 80 na maszynie hosta.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-252">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="7a2e9-253">Linki w aplikacji sieci web do wykazu i kolejność usłudze zależy od\_ustawienia.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-253">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="7a2e9-254">Powoduje to, że usługa poczekaj, aż te usługi są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-254">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="7a2e9-255">Firma Microsoft będzie ponownie plik docker-compose.yml w dalszej części tego tematu, gdy opisujemy sposób implementacji aplikacji obsługującej wiele kontenerów i mikrousług.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-255">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="7a2e9-256">Praca z docker-compose.yml w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7a2e9-256">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="7a2e9-257">Podczas dodawania obsługi orkiestratora kontenerów do projektu aplikacji sieci web, jak pokazano w rysunek 5 – 7, program Visual Studio dodaje sekcję service (projekt) do rozwiązania, który zawiera plik docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-257">When you add container orchestrator support to a web app project, as shown in Figure 5-7, Visual Studio adds a service section (project) to the solution that contains a docker-compose.yml file.</span></span> <span data-ttu-id="7a2e9-258">Jest to prosty sposób rozpocząć tworzenie rozwiązania wielu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-258">This is an easy way to start composing a multiple-container solution.</span></span>

![Dodaj element menu pomocy technicznej koordynatora kontenerów w programie Visual Studio](./media/add-container-orchestrator-support.png)

<span data-ttu-id="7a2e9-260">**Rysunek 5 – 7**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-260">**Figure 5-7**.</span></span> <span data-ttu-id="7a2e9-261">Dodanie obsługi platformy Docker w programie Visual Studio 2017, klikając prawym przyciskiem myszy projekt ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7a2e9-261">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="7a2e9-262">Dodawanie obsługi orkiestratora kontenerów dodaje plik Dockerfile do projektu (jeśli jeszcze nie istnieje).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-262">Adding container orchestrator support adds the Dockerfile to your project (if it doesn't already exist).</span></span> <span data-ttu-id="7a2e9-263">Dodaje także informacje o konfiguracji do pliku docker-compose.yml globalnego na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-263">It also adds configuration information to a global docker-compose.yml file at the solution level.</span></span> <span data-ttu-id="7a2e9-264">Zobaczysz nowy węzeł projektu ( *docker compose.dcproj* pliku projektu) w **Eksploratora rozwiązań** zawierający plik docker-compose.yml, jak pokazano w rysunek 5 – 8.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-264">You'll see a new project node (the *docker-compose.dcproj* project file) in **Solution Explorer** that contains the docker-compose.yml file, as shown in Figure 5-8.</span></span>

![docker-compose węzła w Eksploratorze rozwiązań](./media/docker-compose-files.png)

<span data-ttu-id="7a2e9-266">**Rysunek 5 – 8**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-266">**Figure 5-8**.</span></span> <span data-ttu-id="7a2e9-267">**Narzędzia docker compose** węzła drzewa dodane w Eksploratorze rozwiązań 2017 r. w usłudze Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a2e9-267">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="7a2e9-268">Następnie można otworzyć pliku docker-compose.yml i zaktualizować je z dodatkowymi funkcjami.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-268">You can then open the docker-compose.yml file and update it with additional features.</span></span>

<span data-ttu-id="7a2e9-269">Można wdrożyć aplikację obsługującą wiele kontenerów za pomocą pliku docker-compose.yml pojedynczego za pomocą `docker-compose up` polecenia.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-269">You can deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span>

![Krok 5 — uruchom aplikację grafiki](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="7a2e9-271">Krok 5.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-271">Step 5.</span></span> <span data-ttu-id="7a2e9-272">Kompilowanie i uruchamianie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="7a2e9-272">Build and run your Docker application</span></span>

<span data-ttu-id="7a2e9-273">Jeśli aplikacja ma tylko jeden kontener, możesz uruchomić go przez wdrożenie jej do hosta platformy Docker (maszyny Wirtualnej lub serwera fizycznego).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-273">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="7a2e9-274">Jednak jeśli aplikacja zawiera wiele usług, możesz go wdrożyć jako złożone aplikacji, za pomocą jednego polecenia interfejsu wiersza polecenia (docker-compose się), lub za pomocą programu Visual Studio, które korzystają z tego polecenia w sposób niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-274">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="7a2e9-275">Przyjrzyjmy się różne opcje.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-275">Let’s look at the different options.</span></span>

### <a name="option-a-run-a-single-container-app"></a><span data-ttu-id="7a2e9-276">Opcja odpowiedź: uruchamianie aplikacji jednego kontenera</span><span class="sxs-lookup"><span data-stu-id="7a2e9-276">Option A: Run a single-container app</span></span>

#### <a name="docker-cli"></a><span data-ttu-id="7a2e9-277">Interfejs CLI platformy docker</span><span class="sxs-lookup"><span data-stu-id="7a2e9-277">Docker CLI</span></span>

<span data-ttu-id="7a2e9-278">Można uruchomić kontener platformy Docker za pomocą platformy docker, uruchom polecenie, tak jak rysunek 5-9:</span><span class="sxs-lookup"><span data-stu-id="7a2e9-278">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![Uruchamianie kontenera platformy Docker za pomocą platformy docker, uruchom polecenie](./media/image13.png)

<span data-ttu-id="7a2e9-280">**Rysunek 5-9**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-280">**Figure 5-9**.</span></span> <span data-ttu-id="7a2e9-281">Uruchamianie kontenera platformy Docker za pomocą platformy docker, uruchom polecenie</span><span class="sxs-lookup"><span data-stu-id="7a2e9-281">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="7a2e9-282">W takim przypadku polecenie wiąże wewnętrznego portu 5000 kontenera do portu 80 maszyny hosta.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-282">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="7a2e9-283">Oznacza to, że host jest nasłuchuje na porcie 80 i przekazywania do portu 5000 kontenera.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-283">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

#### <a name="visual-studio"></a><span data-ttu-id="7a2e9-284">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a2e9-284">Visual Studio</span></span>

<span data-ttu-id="7a2e9-285">Jeśli jeszcze nie została dodana obsługa orkiestratora kontenerów, można również uruchomić aplikację jeden kontener w programie Visual Studio, naciskając klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-285">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **F5**.</span></span> <span data-ttu-id="7a2e9-286">Kontener działa lokalnie przy użyciu platformy docker, uruchom.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-286">The container runs locally using docker run.</span></span>

### <a name="option-b-run-a-multi-container-app"></a><span data-ttu-id="7a2e9-287">Opcja B: Uruchom aplikację obsługującą wiele kontenerów</span><span class="sxs-lookup"><span data-stu-id="7a2e9-287">Option B: Run a multi-container app</span></span>

<span data-ttu-id="7a2e9-288">W większości przypadków enterprise aplikację platformy Docker będzie składać się z wielu usług, co oznacza, że należy uruchomić aplikację obsługującą wiele kontenerów, jak pokazano na rysunku 5-10.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-288">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![Grafika przedstawiająca maszyny Wirtualnej za pomocą kontenerów Docker wdrożonych](./media/image14.png)

<span data-ttu-id="7a2e9-290">**Rysunek 5 – 10**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-290">**Figure 5-10**.</span></span> <span data-ttu-id="7a2e9-291">Maszyny Wirtualnej przy użyciu kontenerów Docker wdrożonych</span><span class="sxs-lookup"><span data-stu-id="7a2e9-291">VM with Docker containers deployed</span></span>

#### <a name="docker-cli"></a><span data-ttu-id="7a2e9-292">Interfejs CLI platformy docker</span><span class="sxs-lookup"><span data-stu-id="7a2e9-292">Docker CLI</span></span>

<span data-ttu-id="7a2e9-293">Aby uruchomić aplikację obsługującą wiele kontenerów za pomocą interfejsu wiersza polecenia platformy Docker, możesz uruchomić platformy docker-compose się polecenia.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-293">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="7a2e9-294">Tego polecenia używa docker-compose.yml pliku masz na poziomie rozwiązania, aby wdrożyć aplikację obsługującą wiele kontenerów.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-294">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="7a2e9-295">Rysunek 5 – 11 przedstawia wyniki przy uruchamianiu polecenia z katalogu głównego projektu, który zawiera plik docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-295">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![Przykład powoduje podczas uruchamiania narzędzia docker compose się polecenia](./media/image15.png)

<span data-ttu-id="7a2e9-297">**Rysunek 5 – 11**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-297">**Figure 5-11**.</span></span> <span data-ttu-id="7a2e9-298">Przykład powoduje podczas uruchamiania narzędzia docker compose się polecenia</span><span class="sxs-lookup"><span data-stu-id="7a2e9-298">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="7a2e9-299">Po platformy docker-compose się polecenia uruchomienia, aplikacji i jej powiązane kontenery są wdrażane w sieci hosta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-299">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host.</span></span>

#### <a name="visual-studio"></a><span data-ttu-id="7a2e9-300">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a2e9-300">Visual Studio</span></span>

<span data-ttu-id="7a2e9-301">Korzystanie z aplikacji obsługującej wiele kontenerów, w programie Visual Studio 2017 jest proste.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-301">Running a multi-container application using Visual Studio 2017 is simple.</span></span> <span data-ttu-id="7a2e9-302">Nie tylko możesz uruchomić aplikację obsługującą wiele kontenerów, ale możesz debugować swoje kontenery bezpośrednio z programu Visual Studio przez ustawienie regularne punkty przerwania.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-302">Not only can you run the multi-container application, but you're able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="7a2e9-303">Jak wspomniano wcześniej, podczas dodawania każdego kolejnego obsługi orkiestratora kontenerów do projektu w ramach rozwiązania, projektu jest skonfigurowany w pliku globalnego docker-compose.yml (poziomie rozwiązania), który umożliwia uruchamiania lub debugowania całego rozwiązania tylko raz.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-303">As mentioned before, each time you add container orchestrator support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="7a2e9-304">Program Visual Studio uruchomi jeden kontener dla każdego projektu, który ma włączoną obsługę rozwiązań platformy Docker i wykonaj wszystkie kroki wewnętrznego dla Ciebie (dotnet publikowania, docker kompilacji itd.).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-304">Visual Studio will start one container for each project that has Docker solution support enabled and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="7a2e9-305">Istotną kwestią jest, jak pokazano na rysunku 5-12, w programie Visual Studio 2017 dodatkowego **Docker** polecenie, aby uzyskać **F5** klucza akcji.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-305">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there's an additional **Docker** command for the **F5** key action.</span></span> <span data-ttu-id="7a2e9-306">Ta opcja pozwala uruchomić lub debugować aplikację obsługującą wiele kontenerów przez uruchomienie wszystkich kontenerów, które są zdefiniowane w plikach docker-compose.yml na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-306">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="7a2e9-307">Możliwość debugowania rozwiązań do obsługi wielu kontenerów oznacza, że można ustawić kilka punktów przerwania, w każdym punkcie przerwania, które znajdują się w innym projekcie (kontenera), a podczas debugowania w programie Visual Studio przestanie w punktach przerwania, zdefiniowane w różnych projektach i uruchomiona na różnych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-307">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Uruchamianie aplikacji obsługującej wiele kontenerów w programie Visual Studio 2017](./media/image16.png)

<span data-ttu-id="7a2e9-309">**Rysunek 5 – 12**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-309">**Figure 5-12**.</span></span> <span data-ttu-id="7a2e9-310">Uruchamianie aplikacji obsługującej wiele kontenerów w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7a2e9-310">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7a2e9-311">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="7a2e9-311">Additional resources</span></span>

-  <span data-ttu-id="7a2e9-312">**Wdrażanie kontenera platformy ASP.NET ha zdalnym hoście platformy Docker**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-312">**Deploy an ASP.NET container to a remote Docker host**</span></span>

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="7a2e9-313">Uwaga dotycząca testowanie i wdrażanie przy użyciu koordynatorów</span><span class="sxs-lookup"><span data-stu-id="7a2e9-313">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="7a2e9-314">Narzędzia docker compose się i platformy docker, Uruchom polecenia (lub uruchamianie i debugowanie kontenerów w programie Visual Studio) są odpowiednie do testowania kontenerów w środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-314">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="7a2e9-315">Ale nie powinni używać tej metody, jeśli są przeznaczone dla klastrów platformy Docker i koordynatorów, takich jak Docker Swarm, Mesosphere DC/OS lub Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-315">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="7a2e9-316">Jeśli używasz klastra, takie jak [trybu Docker Swarm](https://docs.docker.com/engine/swarm/) (dostępne w Docker CE dla Windows i Mac od wersji 1.12), należy wdrożyć i przetestować przy użyciu dodatkowych poleceń, takich jak [tworzenia usługi docker](https://docs.docker.com/engine/reference/commandline/service_create/) dla jednej usługi.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-316">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="7a2e9-317">Jeśli wdrażasz aplikację składa się z kilku kontenerów, możesz użyć [pakietu Narzędzia docker compose](https://docs.docker.com/compose/reference/bundle/) i [myBundleFile wdrażana w rozwiązaniu docker](https://docs.docker.com/engine/reference/commandline/deploy/) wdrożyć złożone aplikację jako *stosu*.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-317">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="7a2e9-318">Aby uzyskać więcej informacji, zobacz wpis w blogu [Przedstawiamy eksperymentalne rozproszonych aplikacji pakiety](https://blog.docker.com/2016/06/docker-app-bundle/) w dokumentacji platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-318">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="7a2e9-319">w witrynie platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-319">on the Docker site.</span></span>

<span data-ttu-id="7a2e9-320">Dla [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) i [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/) użyje wdrożenia różnych poleceń i skryptów w także.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-320">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![Krok 6 grafiki](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="7a2e9-322">Krok 6.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-322">Step 6.</span></span> <span data-ttu-id="7a2e9-323">Testowanie aplikacji platformy Docker za pomocą lokalnego hosta platformy Docker</span><span class="sxs-lookup"><span data-stu-id="7a2e9-323">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="7a2e9-324">W tym kroku różnią się w zależności od tego, co robi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-324">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="7a2e9-325">W prostej aplikacji sieci Web platformy .NET Core, który jest wdrażany jako jeden kontener lub usługi uzyskać dostęp do usługi, otwierając przeglądarki na hoście platformy Docker i przechodząc do tej lokacji, jak pokazano w rysunek 5-13.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-325">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="7a2e9-326">(Jeśli konfiguracji w pliku Dockerfile kontenera jest mapowany na port na hoście, który jest inna niż 80, obejmuje port hosta w adresie URL).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-326">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Przykład testowanie aplikacji platformy Docker lokalnie przy użyciu localhost](./media/image18.png)

<span data-ttu-id="7a2e9-328">**Rysunek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-328">**Figure 5-13**.</span></span> <span data-ttu-id="7a2e9-329">Przykład testowanie aplikacji platformy Docker lokalnie przy użyciu localhost</span><span class="sxs-lookup"><span data-stu-id="7a2e9-329">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="7a2e9-330">Adres IP hosta w przypadku platformy Docker nie wskazuje localhost (domyślnie, gdy za pomocą platformy Docker CE, powinien), aby przejść do usługi, użyj adresu IP karty sieciowej komputera.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-330">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="7a2e9-331">Ten adres URL w przeglądarce na przykład kontenerem omawiana korzysta z portu 80.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-331">This URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="7a2e9-332">Jednak wewnętrznie żądania nastąpi przekierowanie do portu 5000, ponieważ było jak miała być wdrożona przy użyciu rozwiązania docker, uruchom polecenie, zgodnie z opisem w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-332">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="7a2e9-333">Możesz również przetestować aplikację przy użyciu programu curl w terminalu, jak pokazano w rysunek 5-14.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-333">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="7a2e9-334">W przypadku instalacji platformy Docker na Windows domyślny adres IP hosta platformy Docker jest zawsze 10.0.75.1 Oprócz rzeczywistego adresu IP tego komputera.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-334">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![Przykład testowanie aplikacji platformy Docker lokalnie przy użyciu programu curl](./media/image19.png)

<span data-ttu-id="7a2e9-336">**Rysunek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-336">**Figure 5-14**.</span></span> <span data-ttu-id="7a2e9-337">Przykład testowanie aplikacji platformy Docker lokalnie przy użyciu programu curl</span><span class="sxs-lookup"><span data-stu-id="7a2e9-337">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="7a2e9-338">Testowanie i debugowanie kontenerów przy użyciu programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7a2e9-338">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="7a2e9-339">Gdy uruchamianie i debugowanie kontenerów za pomocą programu Visual Studio 2017, tak jak w przypadku braku pojemników można debugować aplikację platformy .NET w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-339">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="7a2e9-340">Testowanie i debugowanie bez programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a2e9-340">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="7a2e9-341">Jeśli tworzysz przy użyciu podejścia edytora/CLI debugowanie kontenerów jest trudniejsze, i chcesz debugować, generując ślady.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-341">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7a2e9-342">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="7a2e9-342">Additional resources</span></span>

- <span data-ttu-id="7a2e9-343">**Debugowanie aplikacji w lokalnym kontenerze Docker**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-343">**Debugging apps in a local Docker container**</span></span>

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

- <span data-ttu-id="7a2e9-344">**Steve Lasker. Kompilowanie, debugowanie, wdrażanie aplikacji platformy ASP.NET Core przy użyciu platformy Docker.**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-344">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="7a2e9-345">Film wideo.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-345">Video.</span></span>

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="7a2e9-346">Uproszczone przepływu pracy podczas tworzenia kontenerów przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a2e9-346">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="7a2e9-347">Skutecznie przepływ pracy przy użyciu programu Visual Studio jest znacznie prostsze niż w przypadku użycia podejście edytora/interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-347">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="7a2e9-348">Większość czynności wymagane przez platformę Docker związane z pliku Dockerfile i pliki docker-compose.yml są ukryte lub uproszczone przez program Visual Studio, jak pokazano w rysunek 5 – 15.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-348">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![Uproszczone przepływu pracy podczas tworzenia w programie Visual Studio](./media/image20.png)

<span data-ttu-id="7a2e9-350">**Rysunek 5 – 15**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-350">**Figure 5-15**.</span></span> <span data-ttu-id="7a2e9-351">Uproszczone przepływu pracy podczas tworzenia w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a2e9-351">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="7a2e9-352">Ponadto należy wykonać tylko raz w kroku 2 (Dodawanie obsługę platformy Docker do swoich projektów).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-352">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="7a2e9-353">W związku z tym przepływ pracy jest podobne do zadań rozwoju zwykle, gdy przy użyciu platformy .NET do tworzenia innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-353">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="7a2e9-354">Musisz wiedzieć, co się dzieje dzieje się w tle (procesu tworzenia obrazu, jakie obrazy podstawowe, którego używasz, wdrażanie kontenerów, itp.) i czasami również należy edytować plik Dockerfile lub docker-compose.yml dostosowywania zachowania.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-354">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="7a2e9-355">Jednak większość pracy jest znacznie uproszczone przy użyciu programu Visual Studio, co możesz o wiele bardziej produktywne.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-355">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7a2e9-356">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="7a2e9-356">Additional resources</span></span>

- <span data-ttu-id="7a2e9-357">**Steve Lasker. Programowanie na platformie .NET platformy docker przy użyciu programu Visual Studio 2017**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-357">**Steve Lasker. .NET Docker Development with Visual Studio 2017**</span></span>

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

- <span data-ttu-id="7a2e9-358">**Jeffrey T. Fritz. Umieszczanie aplikacji platformy .NET Core w kontenerze za pomocą nowych narzędzi platformy Docker dla programu Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-358">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**</span></span>

   [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="7a2e9-359">Używanie poleceń programu PowerShell w pliku Dockerfile do konfigurowania kontenerów Windows</span><span class="sxs-lookup"><span data-stu-id="7a2e9-359">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="7a2e9-360">[Kontenery Windows](/virtualization/windowscontainers/about/) umożliwiają konwertowanie istniejących aplikacji Windows obrazów platformy Docker i wdrożyć je przy użyciu tych samych narzędzi, jak w pozostałych ekosystemie Docker.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-360">[Windows Containers](/virtualization/windowscontainers/about/) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="7a2e9-361">Aby użyć kontenery Windows, możesz uruchomić poleceń programu PowerShell w pliku Dockerfile, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7a2e9-361">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore

LABEL Description="IIS" Vendor="Microsoft" Version="10"

RUN powershell -Command Add-WindowsFeature Web-Server

CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="7a2e9-362">W tym przypadku jesteśmy przy użyciu obrazu podstawowego systemu Windows Server Core (ustawienie FROM) i instalowanie usług IIS za pomocą polecenia programu PowerShell (Ustawienie Uruchom).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-362">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="7a2e9-363">W podobny sposób można również użyć poleceń programu PowerShell do skonfigurowania dodatkowych składników, takich jak ASP.NET 4.x, .NET 4.6 lub innego oprogramowania Windows.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-363">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="7a2e9-364">Na przykład następujące polecenie w pliku Dockerfile konfiguruje ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="7a2e9-364">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="7a2e9-365">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="7a2e9-365">Additional resources</span></span>

- <span data-ttu-id="7a2e9-366">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="7a2e9-366">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="7a2e9-367">Przykładowe polecenia programu Powershell do uruchamiania z plików dockerfile w celu uwzględnienia funkcji Windows.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-367">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>

   [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
<span data-ttu-id="7a2e9-368">[Poprzednie](index.md)
[dalej](../net-core-single-containers-linux-windows-server-hosts/index.md)</span><span class="sxs-lookup"><span data-stu-id="7a2e9-368">[Previous](index.md)
[Next](../net-core-single-containers-linux-windows-server-hosts/index.md)</span></span>