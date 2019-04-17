---
title: Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker
description: Poznaj szczegóły przepływu pracy do tworzenia aplikacji opartych na platformie Docker. Rozpocznij krok po kroku i Uzyskaj do niektórych szczegółów, aby zoptymalizować pliki Dockerfile oraz kończyć się znakiem uproszczonego przepływu pracy dostępna przy użyciu programu Visual Studio.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: f23a2352d86d5c77d2f05af2a2452fb3c944e049
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613372"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="fd51e-104">Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fd51e-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="fd51e-105">Cyklu tworzenia aplikacji rozpoczyna się na komputerze, jako programista, gdy kod aplikacji przy użyciu preferowanego języka i przetestować go lokalnie.</span><span class="sxs-lookup"><span data-stu-id="fd51e-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="fd51e-106">W tym przepływie pracy, niezależnie od tego, które języków i platformy możesz są zawsze opracowywania i testowania kontenerów platformy Docker, ale sposób lokalnie.</span><span class="sxs-lookup"><span data-stu-id="fd51e-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="fd51e-107">Każdy kontener (wystąpienia obrazu platformy Docker) obejmuje następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="fd51e-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="fd51e-108">Opcji wyboru systemu operacyjnego, na przykład Linux dystrybucji Windows Nano Server i Windows Server Core.</span><span class="sxs-lookup"><span data-stu-id="fd51e-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="fd51e-109">Pliki dodane podczas tworzenia aplikacji, na przykład źródła danych binarnych kodu i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fd51e-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="fd51e-110">Informacje o konfiguracji, takie jak ustawienia środowiska i zależności.</span><span class="sxs-lookup"><span data-stu-id="fd51e-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="fd51e-111">Przepływ pracy na potrzeby tworzenia aplikacji opartych na kontenerach platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fd51e-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="fd51e-112">W tej sekcji opisano *pętli wewnętrzny* przepływ pracy tworzenia oprogramowania dla aplikacji opartych na kontenerach platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="fd51e-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="fd51e-113">Przepływ pracy wewnętrznej pętli oznacza, że nie rozważa szersze DevOps przepływu pracy, który może zawierać maksymalnie wdrożenia produkcyjnego, a po prostu koncentruje się na rozwoju pracy na komputerze dewelopera.</span><span class="sxs-lookup"><span data-stu-id="fd51e-113">The inner-loop workflow means it's not considering the broader DevOps workflow, that can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="fd51e-114">Początkowe kroki konfigurowania środowiska nie są uwzględnione, ponieważ te kroki są wykonywane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="fd51e-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="fd51e-115">Aplikacja składa się z własnych usług, a także dodatkowe biblioteki (zależności).</span><span class="sxs-lookup"><span data-stu-id="fd51e-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="fd51e-116">Poniżej przedstawiono podstawowe kroki, które zwykle wykonać podczas kompilowania aplikacji platformy Docker, jak pokazano w rysunek 5-1.</span><span class="sxs-lookup"><span data-stu-id="fd51e-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![<span data-ttu-id="fd51e-117">Proces programowania dla aplikacji platformy Docker: 1 - kodu aplikacji, 2 - zapisu pliku Dockerfile/s, 3 — Tworzenie obrazów zdefiniowanych w pliku Dockerfile/s, 4 - (opcjonalnie) usług Compose w pliku docker-compose.yml, 5, - uruchomienia kontenera lub docker-compose aplikacji, 6 - testów aplikacji sieci Web lub mikrousług, 7 - wypychania do repozytorium i powtórz tę czynność.</span><span class="sxs-lookup"><span data-stu-id="fd51e-117">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span> ](./media/image1.png)

<span data-ttu-id="fd51e-118">**Rysunek 5-1.**</span><span class="sxs-lookup"><span data-stu-id="fd51e-118">**Figure 5-1.**</span></span> <span data-ttu-id="fd51e-119">Instrukcje krok po kroku przepływu pracy do tworzenia aplikacji kontenerowych nimi platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fd51e-119">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="fd51e-120">W tej sekcji opisano szczegółowo całego tego procesu i na każdym kroku głównych zostało wyjaśnione, skupiając się na środowisko Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fd51e-120">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="fd51e-121">Podczas korzystania z podejście do tworzenia edytora/CLI (na przykład programu Visual Studio Code oraz interfejsu wiersza polecenia platformy Docker w systemie macOS lub Windows), musisz wiedzieć każdego kroku, zazwyczaj bardziej szczegółowo niż w przypadku korzystania z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fd51e-121">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="fd51e-122">Aby uzyskać więcej informacji na temat pracy w środowisku interfejsu wiersza polecenia, zobacz książki elektronicznej [cykl życia aplikacji kontenerowych nimi platformy Docker z Platforms i narzędzi Microsoft](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="fd51e-122">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="fd51e-123">Podczas korzystania z programu Visual Studio 2017, wiele z tych kroków są obsługiwane dla Ciebie, co znacznie zwiększa wydajność pracy.</span><span class="sxs-lookup"><span data-stu-id="fd51e-123">When you're using Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="fd51e-124">Jest to szczególnie istotne, przy użyciu programu Visual Studio 2017 i przeznaczone dla aplikacji obsługującej wiele kontenerów.</span><span class="sxs-lookup"><span data-stu-id="fd51e-124">This is especially true when you're using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="fd51e-125">Na przykład tylko jednym kliknięciem, Visual Studio dodaje plik Dockerfile i docker-compose.yml do swoich projektów za pomocą konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fd51e-125">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="fd51e-126">Po uruchomieniu aplikacji w programie Visual Studio tworzy obraz platformy Docker i uruchamia aplikację obsługującą wiele kontenerów bezpośrednio na platformie Docker; Umożliwia ona nawet jednocześnie debugowanie kilka kontenerów.</span><span class="sxs-lookup"><span data-stu-id="fd51e-126">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="fd51e-127">Te funkcje będą zwiększyć szybkość rozwoju.</span><span class="sxs-lookup"><span data-stu-id="fd51e-127">These features will boost your development speed.</span></span>

<span data-ttu-id="fd51e-128">Po prostu, ponieważ program Visual Studio sprawia, że te kroki są automatyczne nie oznacza to jednak, że nie musisz wiedzieć, co się dzieje na dole z platformą Docker.</span><span class="sxs-lookup"><span data-stu-id="fd51e-128">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="fd51e-129">W związku z tym korzystając ze wskazówek szczegóły każdego kroku.</span><span class="sxs-lookup"><span data-stu-id="fd51e-129">Therefore, the following guidance details every step.</span></span>

![1 — kodu aplikacji](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="fd51e-131">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="fd51e-131">Step 1.</span></span> <span data-ttu-id="fd51e-132">Rozpocznij kodowanie i tworzenie początkowej aplikacja lub usługa linii bazowej</span><span class="sxs-lookup"><span data-stu-id="fd51e-132">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="fd51e-133">Tworzenie aplikacji platformy Docker to podobnie, jak opracować aplikację bez platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="fd51e-133">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="fd51e-134">Różnica jest, że podczas tworzenia dla platformy Docker, możesz teraz wdrażanie i testowanie aplikacji lub usług działających w kontenerach platformy Docker w środowisku lokalnym, albo (konfiguracja maszyny Wirtualnej systemu Linux przez platformę Docker), albo Windows bezpośrednio, jeśli przy użyciu kontenerów Windows.</span><span class="sxs-lookup"><span data-stu-id="fd51e-134">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="fd51e-135">Konfigurowanie środowiska lokalnego z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd51e-135">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="fd51e-136">Aby rozpocząć, upewnij się, że masz [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) dla Windows zainstalowany zgodnie z opisem w poniższych instrukcjach:</span><span class="sxs-lookup"><span data-stu-id="fd51e-136">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="fd51e-137">Wprowadzenie do platformy Docker CE dla Windows</span><span class="sxs-lookup"><span data-stu-id="fd51e-137">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="fd51e-138">Ponadto konieczne Visual Studio 2017 w wersji 15.7 lub nowszej z **programowanie dla wielu platform .NET Core** obciążenia zainstalowany, jak pokazano w rysunek 5-2.</span><span class="sxs-lookup"><span data-stu-id="fd51e-138">In addition, you need Visual Studio 2017 version 15.7 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![.NET core wieloplatformowego opracowywania aplikacji obciążenia wybór podczas instalacji programu Visual Studio.](./media/image3.png)

<span data-ttu-id="fd51e-140">**Rysunek 5-2**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-140">**Figure 5-2**.</span></span> <span data-ttu-id="fd51e-141">Wybieranie **programowanie dla wielu platform .NET Core** obciążenie podczas instalacji programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fd51e-141">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="fd51e-142">Możesz rozpocząć kodowanie swoją aplikację w zwykły .NET (zwykle w .NET Core, jeśli planowane jest korzystanie z kontenerów), nawet przed włączeniem platformy Docker w aplikacji i wdrażanie i testowanie na platformie Docker.</span><span class="sxs-lookup"><span data-stu-id="fd51e-142">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="fd51e-143">Jednak zaleca się uruchamiania nad platformy Docker tak szybko, jak to możliwe, ponieważ się rzeczywistego środowiska i wszelkie problemy, które mogą być wykrywane tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="fd51e-143">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="fd51e-144">To zaleca się, ponieważ dzięki programowi Visual Studio tak łatwe do pracy z rozwiązaniem Docker, że niemal pozornie przezroczyste — najlepszy przykład podczas debugowania aplikacji obsługującej wiele kontenerów za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fd51e-144">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="fd51e-145">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="fd51e-145">Additional resources</span></span>

- <span data-ttu-id="fd51e-146">**Wprowadzenie do platformy Docker CE dla Windows** \\</span><span class="sxs-lookup"><span data-stu-id="fd51e-146">**Get started with Docker CE for Windows** \\</span></span>
  <https://docs.docker.com/docker-for-windows/>

- <span data-ttu-id="fd51e-147">**Visual Studio 2017** \\</span><span class="sxs-lookup"><span data-stu-id="fd51e-147">**Visual Studio 2017** \\</span></span>
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)

![2 — pisanie plików Dockerfile](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="fd51e-149">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="fd51e-149">Step 2.</span></span> <span data-ttu-id="fd51e-150">Tworzenie pliku Dockerfile związane z istniejącego obrazu podstawowego platformy .NET</span><span class="sxs-lookup"><span data-stu-id="fd51e-150">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="fd51e-151">Potrzebujesz pliku Dockerfile dla niestandardowego obrazu, z którą chcesz skompilować; należy również plik Dockerfile dla każdego kontenera do wdrożenia, czy wdrożyć automatycznie z programu Visual Studio lub ręcznie przy użyciu interfejsu wiersza polecenia platformy Docker (docker, uruchom i docker-compose poleceń).</span><span class="sxs-lookup"><span data-stu-id="fd51e-151">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="fd51e-152">Jeśli aplikacja zawiera pojedynczą usługę niestandardowych, konieczne będzie pojedynczego pliku Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="fd51e-152">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="fd51e-153">Jeśli aplikacja zawiera wiele usług (tak jak w architekturze mikrousług), należy jeden plik Dockerfile dla każdej usługi.</span><span class="sxs-lookup"><span data-stu-id="fd51e-153">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="fd51e-154">Plik Dockerfile znajduje się w folderze głównym aplikacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="fd51e-154">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="fd51e-155">Zawiera polecenia, określające sposób konfigurowania i uruchamiania aplikacji lub usługi w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="fd51e-155">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="fd51e-156">Można ręcznie utworzyć plik Dockerfile w kodzie i dodać go do projektu, wraz z zależności .NET.</span><span class="sxs-lookup"><span data-stu-id="fd51e-156">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="fd51e-157">Korzystając z programu Visual Studio i jego narzędzi platformy Docker to zadanie wymaga tylko kilku kliknięć myszą.</span><span class="sxs-lookup"><span data-stu-id="fd51e-157">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="fd51e-158">Po utworzeniu nowego projektu w programie Visual Studio 2017 jest dostępna opcja o nazwie **Obsługa Włączanie kontenerów (Docker)**, jak pokazano w rysunek 5-3.</span><span class="sxs-lookup"><span data-stu-id="fd51e-158">When you create a new project in Visual Studio 2017, there's an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![Włącz obsługę platformy Docker wyboru podczas tworzenia nowego projektu ASP.NET Core w programie Visual Studio 2017](./media/image5.png)

<span data-ttu-id="fd51e-160">**Rysunek 5-3**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-160">**Figure 5-3**.</span></span> <span data-ttu-id="fd51e-161">Włączanie obsługi platformy Docker, podczas tworzenia nowego projektu ASP.NET Core w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fd51e-161">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2017</span></span>

<span data-ttu-id="fd51e-162">Można również włączyć obsługę platformy Docker w istniejącym projekcie aplikacji sieci web platformy ASP.NET Core, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając polecenie **Dodaj** > **obsługę platformy Docker** , jak pokazano na rysunku 5-4.</span><span class="sxs-lookup"><span data-stu-id="fd51e-162">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support**, as shown in Figure 5-4.</span></span>

![Dodaj opcję menu pomocy technicznej platformy Docker w programie Visual Studio](./media/image6.png)

<span data-ttu-id="fd51e-164">**Rysunek 5-4**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-164">**Figure 5-4**.</span></span> <span data-ttu-id="fd51e-165">Włączanie obsługi platformy Docker w istniejącym projekcie programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fd51e-165">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="fd51e-166">Ta akcja spowoduje dodanie *pliku Dockerfile* do projektu za pomocą wymaganej konfiguracji i jest dostępna tylko w projektach programu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="fd51e-166">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="fd51e-167">W podobny sposób, program Visual Studio można również dodać plik docker-compose.yml dla całego rozwiązania z opcją **Dodaj > Obsługa Orkiestratora kontenerów**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-167">In a similar fashion, Visual Studio can also add a docker-compose.yml file for the whole solution with the option **Add > Container Orchestrator Support**.</span></span> <span data-ttu-id="fd51e-168">W kroku 4 przedstawimy zagadnienia związane z tej opcji bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="fd51e-168">In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="fd51e-169">Przy użyciu istniejących oficjalnego obrazu Docker w programie .NET</span><span class="sxs-lookup"><span data-stu-id="fd51e-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="fd51e-170">Zazwyczaj Tworzenie niestandardowego obrazu kontenera na podstawie obrazu podstawowego, otrzymasz od oficjalnego repozytorium, takiego jak [usługi Docker Hub](https://hub.docker.com/) rejestru.</span><span class="sxs-lookup"><span data-stu-id="fd51e-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="fd51e-171">To jest dokładnie co się dzieje w tle po włączeniu obsługi platformy Docker w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fd51e-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="fd51e-172">Z pliku Dockerfile użyje istniejącej `aspnetcore` obrazu.</span><span class="sxs-lookup"><span data-stu-id="fd51e-172">Your Dockerfile will use an existing `aspnetcore` image.</span></span>

<span data-ttu-id="fd51e-173">Wcześniej opisano firma Microsoft, które obrazów platformy Docker i repozytoriów, można użyć w zależności od framework i systemu operacyjnego zostały wybrane.</span><span class="sxs-lookup"><span data-stu-id="fd51e-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="fd51e-174">Na przykład, jeśli chcesz użyć programu ASP.NET Core (Linux lub Windows), jest obrazu do użycia `mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="fd51e-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="fd51e-175">W związku z tym wystarczy określić, jakie podstawowego obrazu platformy Docker, który będzie używany dla kontenera.</span><span class="sxs-lookup"><span data-stu-id="fd51e-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="fd51e-176">Można to zrobić, dodając `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` do Twojego pliku Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="fd51e-176">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` to your Dockerfile.</span></span> <span data-ttu-id="fd51e-177">To zostanie przeprowadzona przez program Visual Studio, ale w przypadku zaktualizowania wersji zaktualizuj tę wartość.</span><span class="sxs-lookup"><span data-stu-id="fd51e-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="fd51e-178">Oficjalna repozytorium obrazów platformy .NET z usługi Docker Hub przy użyciu numeru wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym programowanie, testowanie i produkcja).</span><span class="sxs-lookup"><span data-stu-id="fd51e-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="fd51e-179">Poniższy kod przedstawia przykładowy plik Dockerfile dla kontenera platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="fd51e-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="fd51e-180">W tym przypadku obraz, który zależy od wersji 2.2 oficjalny obraz platformy Docker programu ASP.NET Core (wielu arch dla systemów Linux i Windows).</span><span class="sxs-lookup"><span data-stu-id="fd51e-180">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="fd51e-181">Jest to ustawienie `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="fd51e-181">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="fd51e-182">(Aby uzyskać więcej informacji na temat tego obrazu podstawowego zobacz [obrazu platformy Docker programu .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) strony.) W pliku Dockerfile trzeba będzie również poinstruować platformy Docker do nasłuchiwania na porcie TCP, używane w czasie wykonywania (w tym przypadku port 80, zgodnie z konfiguracją z ustawieniem UDOSTĘPNIAJĄ).</span><span class="sxs-lookup"><span data-stu-id="fd51e-182">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="fd51e-183">Można określić dodatkowe ustawienia konfiguracji w pliku Dockerfile, w zależności od języka i struktury, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="fd51e-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="fd51e-184">Na przykład wiersz punktu wejścia z `["dotnet", "MySingleContainerWebApp.dll"]` platformy docker, aby uruchomić aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fd51e-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="fd51e-185">Jeśli używasz zestawu SDK i .NET Core interfejsu wiersza polecenia (interfejsu wiersza polecenia platformy dotnet) aby skompilować i uruchomić aplikację .NET, to ustawienie będzie inny.</span><span class="sxs-lookup"><span data-stu-id="fd51e-185">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="fd51e-186">Mierzenie to, że wiersz punktu wejścia i inne ustawienia będą różnić w zależności od języka i platformy, wybrany dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fd51e-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="fd51e-187">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="fd51e-187">Additional resources</span></span>

- <span data-ttu-id="fd51e-188">**Tworzenie obrazów platformy Docker dla aplikacji .NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="fd51e-188">**Building Docker Images for .NET Core Applications** \\</span></span>
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

- <span data-ttu-id="fd51e-189">**Tworzenie własnego obrazu**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-189">**Build your own image**.</span></span> <span data-ttu-id="fd51e-190">W oficjalnej dokumentacji platformy Docker. \\</span><span class="sxs-lookup"><span data-stu-id="fd51e-190">In the official Docker documentation.\\</span></span>
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- <span data-ttu-id="fd51e-191">**Uzyskuje obrazów kontenerów platformy .NET** \\</span><span class="sxs-lookup"><span data-stu-id="fd51e-191">**Staying up-to-date with .NET Container Images** \\</span></span>
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="fd51e-192">**Przy użyciu platformy .NET i Docker wspólnie - DockerCon 2018 Update** \\</span><span class="sxs-lookup"><span data-stu-id="fd51e-192">**Using .NET and Docker Together - DockerCon 2018 Update** \\</span></span>
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="fd51e-193">Przy użyciu repozytoriów wielu architektury obrazu</span><span class="sxs-lookup"><span data-stu-id="fd51e-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="fd51e-194">Jednym repozytorium może zawierać warianty platformy, takich jak obraz systemu Linux i Windows obraz.</span><span class="sxs-lookup"><span data-stu-id="fd51e-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="fd51e-195">Ta funkcja umożliwia dostawców, takich jak Microsoft (obraz podstawowy dla twórców) do utworzenia pojedynczego repozytorium na pokrycie wiele platform (dotyczy to systemów Linux i Windows).</span><span class="sxs-lookup"><span data-stu-id="fd51e-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="fd51e-196">Na przykład [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repozytorium, które są dostępne w rejestrze usługi Docker Hub zapewnia obsługę dla systemów Linux i Windows Nano Server przy użyciu tej samej nazwy repozytorium.</span><span class="sxs-lookup"><span data-stu-id="fd51e-196">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="fd51e-197">Jeśli określony tag, przeznaczonych dla platformy, która jest jawne, takich jak w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="fd51e-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim` \
  <span data-ttu-id="fd51e-198">Cele: .NET Core 2.2 tylko do środowiska uruchomieniowego w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="fd51e-198">Targets: .NET Core 2.2 runtime-only on Linux</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1809` \
  <span data-ttu-id="fd51e-199">Cele: .NET Core 2.2 tylko do środowiska uruchomieniowego na serwerze Windows Nano Server</span><span class="sxs-lookup"><span data-stu-id="fd51e-199">Targets: .NET Core 2.2 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="fd51e-200">Jednak jeśli określisz taką samą nazwę obrazu, nawet w przypadku tego samego tagu wielu architektury obrazów (takich jak `aspnetcore` obrazu) będą używać systemu Linux lub Windows wersji w zależności od systemu operacyjnego hosta platformy Docker jest wdrażany, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fd51e-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnetcore` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime` \
  <span data-ttu-id="fd51e-201">Wiele arch: .NET Core 2.2 w czasie wykonywania tylko w systemie Linux lub Windows Nano Server w zależności od systemu operacyjnego hosta platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fd51e-201">Multi-arch: .NET Core 2.2 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="fd51e-202">Dzięki temu podczas ściągnąć obraz z hosta Windows go każda będzie ściągać wariant Windows i ściągania taką samą nazwę obrazu na hoście z systemem Linux każda będzie ściągać wariantów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="fd51e-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="fd51e-203">Wieloetapowe kompilacje w pliku Dockerfile</span><span class="sxs-lookup"><span data-stu-id="fd51e-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="fd51e-204">Plik Dockerfile jest podobny do skryptu wsadowego.</span><span class="sxs-lookup"><span data-stu-id="fd51e-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="fd51e-205">Podobnie jak co możesz zrobić, jeśli trzeba było skonfigurować na maszynie z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fd51e-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="fd51e-206">Zaczyna się od obraz podstawowy, który konfiguruje początkowe kontekstu, takich jak system plików uruchamiania, który znajduje się na podstawie systemu operacyjnego hosta.</span><span class="sxs-lookup"><span data-stu-id="fd51e-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="fd51e-207">Nie jest system operacyjny, ale można traktować jeśli np. "" system operacyjny w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="fd51e-207">It's not an OS, but you can think of if like "the" OS inside the container.</span></span>

<span data-ttu-id="fd51e-208">Wykonanie każdego wiersza polecenia tworzy nową warstwę w systemie plików z uwzględnieniem zmian od poprzedniej wersji, tak aby w połączeniu, generuje wynikowy systemu plików.</span><span class="sxs-lookup"><span data-stu-id="fd51e-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="fd51e-209">Ponieważ każdy nową warstwę "opiera się" na podstawie poprzedniego i wynikowy rozmiar obrazu zwiększa się wraz z każdego polecenia, obrazy mogą uzyskać bardzo duże, jeśli mają obejmować, na przykład zestaw SDK potrzebne do tworzenia i publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fd51e-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="fd51e-210">Jest to, gdzie uzyskać wieloetapowych kompilacji do kreślenia (z 17.05 platformy Docker i nowszych) w ich magic.</span><span class="sxs-lookup"><span data-stu-id="fd51e-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="fd51e-211">Podstawowe chodzi o to możliwość oddzielenia proces wykonywania pliku Dockerfile w etapach, gdzie etap jest obrazem początkowej następuje co najmniej jedno polecenie, a ostatni etap Określa rozmiar obrazu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fd51e-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="fd51e-212">Krótko mówiąc kompilacje wieloetapowych Zezwalaj na tworzenie różnych "etapach" Dzielenie i zmontować finalnego obrazu przełączania tylko odpowiednich katalogów z etapów pośrednich.</span><span class="sxs-lookup"><span data-stu-id="fd51e-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="fd51e-213">Jest ogólną strategią, aby użyć tej funkcji:</span><span class="sxs-lookup"><span data-stu-id="fd51e-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="fd51e-214">Za pomocą podstawowego obrazu zestawu SDK (nie ma znaczenia, jak duże), ze wszystkim, co jest potrzebne do tworzenia i publikowania aplikacji do folderu i następnie</span><span class="sxs-lookup"><span data-stu-id="fd51e-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="fd51e-215">Korzystanie z obrazu podstawowego, małe, tylko do środowiska uruchomieniowego i skopiowanie folderu publikowania z poprzedniego etapu, aby wygenerować mały obraz końcowego.</span><span class="sxs-lookup"><span data-stu-id="fd51e-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="fd51e-216">Prawdopodobnie najlepszym sposobem, aby dowiedzieć się, że wieloetapowych przechodzi przez plik Dockerfile szczegółowo, wiersz po wierszu, więc zaczyna się od początkowego pliku Dockerfile, tworzone przez program Visual Studio, podczas dodawania Docker obsługują do projektu i uzyskasz do niektóre optymalizacje później.</span><span class="sxs-lookup"><span data-stu-id="fd51e-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="fd51e-217">Początkowy pliku Dockerfile może wyglądać mniej więcej tak:</span><span class="sxs-lookup"><span data-stu-id="fd51e-217">The initial Dockerfile might look something like this:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
 6  WORKDIR /src
 7  COPY src/Services/Catalog/Catalog.API/Catalog.API.csproj …
 8  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.AspNetCore.HealthChecks … 
 9  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions.HealthChecks …
10  COPY src/BuildingBlocks/EventBus/IntegrationEventLogEF/ …
11  COPY src/BuildingBlocks/EventBus/EventBus/EventBus.csproj …
12  COPY src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.csproj …
13  COPY src/BuildingBlocks/EventBus/EventBusServiceBus/EventBusServiceBus.csproj …
14  COPY src/BuildingBlocks/WebHostCustomization/WebHost.Customization …
15  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
16  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
17  RUN dotnet restore src/Services/Catalog/Catalog.API/Catalog.API.csproj
18  COPY . .
19  WORKDIR /src/src/Services/Catalog/Catalog.API
20  RUN dotnet build Catalog.API.csproj -c Release -o /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -o /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app .
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

<span data-ttu-id="fd51e-218">A Oto szczegółowe informacje, wiersz po wierszu:</span><span class="sxs-lookup"><span data-stu-id="fd51e-218">And these are the details, line by line:</span></span>

1. <span data-ttu-id="fd51e-219">Rozpocząć etap za pomocą "małe" obrazu podstawowego tylko do środowiska uruchomieniowego, mu **podstawowy** dla odwołania.</span><span class="sxs-lookup"><span data-stu-id="fd51e-219">Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>
2. <span data-ttu-id="fd51e-220">Tworzenie **App** katalogu na obrazie.</span><span class="sxs-lookup"><span data-stu-id="fd51e-220">Create **/app** directory in the image.</span></span>
3. <span data-ttu-id="fd51e-221">Uwidocznić port **80**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-221">Expose port **80**.</span></span>
<!-- skip -->
5. <span data-ttu-id="fd51e-222">Rozpocznij nowy etap z obrazem "large" Tworzenie/publikowania go wywoływać **kompilacji** dla odwołania.</span><span class="sxs-lookup"><span data-stu-id="fd51e-222">Begin a new stage with "large" image for building/publishing, call it **build** for reference.</span></span>
6. <span data-ttu-id="fd51e-223">Utwórz katalog **/src** na obrazie.</span><span class="sxs-lookup"><span data-stu-id="fd51e-223">Create directory **/src** in the image.</span></span>
7. <span data-ttu-id="fd51e-224">Maksymalnie 16 wiersza, skopiuj przywoływane projekty **.csproj** plików, aby można było później przywrócić pakietów.</span><span class="sxs-lookup"><span data-stu-id="fd51e-224">Up to line 16, copy referenced projects **.csproj** files, to be able to restore packages later.</span></span>
<!-- skip -->
17. <span data-ttu-id="fd51e-225">Przywracanie pakietów dla **Catalog.API** projektów i projektów występujących w odwołaniu.</span><span class="sxs-lookup"><span data-stu-id="fd51e-225">Restore packages for the **Catalog.API** project and the referenced projects.</span></span>
18. <span data-ttu-id="fd51e-226">Kopiowanie **wszystkich drzewo katalogów dla rozwiązania** (z wyjątkiem plików/katalogów, zawarte w **.dockerignore** plik) z do **/src** katalogu na obrazie.</span><span class="sxs-lookup"><span data-stu-id="fd51e-226">Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) from to the **/src** directory in the image.</span></span>
19. <span data-ttu-id="fd51e-227">Zmień bieżący folder do **Catalog.API** projektu.</span><span class="sxs-lookup"><span data-stu-id="fd51e-227">Change current folder to **Catalog.API** project.</span></span>
20. <span data-ttu-id="fd51e-228">Tworzenie projektu (i inne zależności projektu) i dane wyjściowe do **App** katalogu na obrazie.</span><span class="sxs-lookup"><span data-stu-id="fd51e-228">Build project (and other project dependencies) and output to **/app** directory in the image.</span></span>
<!-- skip -->
22. <span data-ttu-id="fd51e-229">Rozpocznij nowy etap, kontynuując kompilacji, wywołać go **publikowania** dla odwołania.</span><span class="sxs-lookup"><span data-stu-id="fd51e-229">Begin a new stage continuing from build, call it **publish** for reference.</span></span>
23. <span data-ttu-id="fd51e-230">Publikowanie projektu (zależności) i dane wyjściowe do **App** katalogu na obrazie.</span><span class="sxs-lookup"><span data-stu-id="fd51e-230">Publish project (and dependencies) and output to **/app** directory in the image.</span></span>
<!-- skip -->
25. <span data-ttu-id="fd51e-231">Rozpocznij nowy etap, kontynuując **podstawowy** i nadać mu **końcowe**</span><span class="sxs-lookup"><span data-stu-id="fd51e-231">Begin a new stage continuing from **base** and call it **final**</span></span>
26. <span data-ttu-id="fd51e-232">Zmień bieżący katalog na **App**</span><span class="sxs-lookup"><span data-stu-id="fd51e-232">Change current directory to **/app**</span></span>
27. <span data-ttu-id="fd51e-233">Kopiuj **App** katalogu od etapu **publikowania** do bieżącego katalogu</span><span class="sxs-lookup"><span data-stu-id="fd51e-233">Copy the **/app** directory from stage **publish** to the current directory</span></span>
28. <span data-ttu-id="fd51e-234">Definiowanie polecenia do uruchomienia po uruchomieniu kontenera.</span><span class="sxs-lookup"><span data-stu-id="fd51e-234">Define the command to run when the container is started.</span></span>

<span data-ttu-id="fd51e-235">Teraz Przyjrzyjmy się niektóre optymalizacje w celu zwiększenia wydajności całego procesu, oznacza to, w przypadku ramach aplikacji eShopOnContainers, około 22 minut lub dłużej tworzyć kompletne rozwiązanie w kontenerach systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="fd51e-235">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="fd51e-236">Będziesz korzystać z platformy Docker warstwy pamięci podręcznej funkcji, która jest dość prosta: Jeśli obrazu podstawowego i polecenia są takie same, jak niektóre wcześniej wykonywanego, wynikowy warstwę, bez potrzeby po prostu można użyć do wykonania polecenia, dzięki czemu można oszczędzić trochę czasu.</span><span class="sxs-lookup"><span data-stu-id="fd51e-236">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="fd51e-237">Dlatego Skupmy się na **kompilacji** etapie linii 5 – 6 są prawie takie same, ale wiersze 7-17 różnią się dla każdej usługi w ramach aplikacji eShopOnContainers, więc można wykonać każdy jeden raz, jednak jeśli zmienisz linii 7-16, aby:</span><span class="sxs-lookup"><span data-stu-id="fd51e-237">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```
COPY . .
```

<span data-ttu-id="fd51e-238">Następnie możesz ją w taki sam dla każdej usługi może spowodować skopiowanie całego rozwiązania i utworzyć większy warstwy, ale:</span><span class="sxs-lookup"><span data-stu-id="fd51e-238">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1) <span data-ttu-id="fd51e-239">Proces kopiowania będzie można wykonać tylko po raz pierwszy (i podczas odbudowywania w przypadku modyfikacji pliku) i użyć pamięci podręcznej dla wszystkich innych usług i</span><span class="sxs-lookup"><span data-stu-id="fd51e-239">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2) <span data-ttu-id="fd51e-240">Ponieważ większy obraz występuje w fazie przejściowej go, nie wpływa na rozmiar obrazu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fd51e-240">Since the larger image occurs in an intermediate stage it, doesn't affect the final image size.</span></span>

<span data-ttu-id="fd51e-241">Obejmuje dalej optymalizacji znaczące `restore` wykonano w wierszu 17, polecenia, który również jest inny dla każdej usługi w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="fd51e-241">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="fd51e-242">Jeśli zmienisz tylko ten wiersz:</span><span class="sxs-lookup"><span data-stu-id="fd51e-242">If you change that line to just:</span></span>

```console
RUN dotnet restore
```

<span data-ttu-id="fd51e-243">Będzie ona przywrócenia pakietów dla całego rozwiązania, ale następnie ponownie go samo jak tylko raz zamiast 15 razy dzięki strategii w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="fd51e-243">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="fd51e-244">Jednak `dotnet restore` tylko działa w przypadku pojedynczego projektu lub pliku rozwiązania w folderze, więc realizacji tego jest nieco bardziej skomplikowane i o sposobie jego rozwiązania, bez pobierania do zbyt wiele szczegółów, to:</span><span class="sxs-lookup"><span data-stu-id="fd51e-244">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1) <span data-ttu-id="fd51e-245">Dodaj następujące wiersze do **.dockerignore**:</span><span class="sxs-lookup"><span data-stu-id="fd51e-245">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="fd51e-246">`*.sln`, aby ignorować wszystkie pliki rozwiązania w drzewie folderów głównych</span><span class="sxs-lookup"><span data-stu-id="fd51e-246">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="fd51e-247">`!eShopOnContainers-ServicesAndWebApps.sln`, aby uwzględnić ten plik rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="fd51e-247">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2) <span data-ttu-id="fd51e-248">Obejmują `/ignoreprojectextensions:.dcproj` argument `dotnet restore`, więc ignoruje także projektu docker-compose i przywrócenie tylko pakiety dla rozwiązania w ramach aplikacji eShopOnContainers ServicesAndWebApps.</span><span class="sxs-lookup"><span data-stu-id="fd51e-248">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="fd51e-249">Końcowe optymalizacji te rzeczy dzieją wierszu 20 jest nadmiarowa, jako wiersz 23 również tworzy aplikację i powróci do trybu, w zasadzie bezpośrednio po wierszu 20, dzięki czemu przechodzi innego polecenia czasochłonne.</span><span class="sxs-lookup"><span data-stu-id="fd51e-249">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="fd51e-250">Wynikowy plik jest następnie:</span><span class="sxs-lookup"><span data-stu-id="fd51e-250">The resulting file is then:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="fd51e-251">Tworzenie obrazu podstawowego od podstaw</span><span class="sxs-lookup"><span data-stu-id="fd51e-251">Creating your base image from scratch</span></span>

<span data-ttu-id="fd51e-252">Można utworzyć własny obraz podstawowy platformy Docker, od podstaw.</span><span class="sxs-lookup"><span data-stu-id="fd51e-252">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="fd51e-253">W tym scenariuszu nie jest zalecane w przypadku osobą, która jest uruchamiana przy użyciu rozwiązania Docker, ale jeśli chcesz ustawić bity określonego obrazu podstawowego, możesz to zrobić.</span><span class="sxs-lookup"><span data-stu-id="fd51e-253">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="fd51e-254">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="fd51e-254">Additional resources</span></span>

- <span data-ttu-id="fd51e-255">**Wielu architektury obrazów platformy .NET Core**. \\</span><span class="sxs-lookup"><span data-stu-id="fd51e-255">**Multi-arch .NET Core images**.\\</span></span>
  <https://github.com/dotnet/announcements/issues/14>

- <span data-ttu-id="fd51e-256">**Tworzenie obrazu podstawowego**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-256">**Create a base image**.</span></span> <span data-ttu-id="fd51e-257">Oficjalna dokumentacja platformy Docker. \\</span><span class="sxs-lookup"><span data-stu-id="fd51e-257">Official Docker documentation.\\</span></span>
  <https://docs.docker.com/develop/develop-images/baseimages/>

![3 — Tworzenie obrazów zdefiniowany z numerem plików Dockerfile](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="fd51e-259">Krok 3.</span><span class="sxs-lookup"><span data-stu-id="fd51e-259">Step 3.</span></span> <span data-ttu-id="fd51e-260">Tworzenie niestandardowych obrazów platformy Docker i osadzanie aplikacji lub usługi w nich</span><span class="sxs-lookup"><span data-stu-id="fd51e-260">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="fd51e-261">Dla każdej usługi w aplikacji należy utworzyć obraz powiązane.</span><span class="sxs-lookup"><span data-stu-id="fd51e-261">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="fd51e-262">Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, wystarczy pojedynczego obrazu.</span><span class="sxs-lookup"><span data-stu-id="fd51e-262">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="fd51e-263">Należy pamiętać, że obrazy platformy Docker są tworzone automatycznie dla Ciebie w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fd51e-263">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="fd51e-264">Poniższe kroki są tylko potrzebne dla przepływu pracy edytorze/interfejsu wiersza polecenia i wyjaśnione w celu uściślenia, o co się stanie, poniżej.</span><span class="sxs-lookup"><span data-stu-id="fd51e-264">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="fd51e-265">Jako deweloper musisz opracowywać i testować lokalnie, przed wypchnięciem ukończonych funkcji lub zmień wartość na system kontroli źródła (na przykład w usłudze GitHub).</span><span class="sxs-lookup"><span data-stu-id="fd51e-265">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="fd51e-266">Oznacza to, że trzeba tworzenie obrazów platformy Docker i wdrażanie kontenerów do lokalnego hosta platformy Docker (Windows lub maszyny Wirtualnej systemu Linux) i uruchamianie, testowanie i debugowanie względem tych kontenerów lokalnego.</span><span class="sxs-lookup"><span data-stu-id="fd51e-266">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="fd51e-267">Aby utworzyć niestandardowy obraz w środowisku lokalnym przy użyciu interfejsu wiersza polecenia platformy Docker i z pliku Dockerfile, można użyć polecenia kompilacji platformy docker, tak jak rysunek 5-5.</span><span class="sxs-lookup"><span data-stu-id="fd51e-267">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Ekran postępu tworzenia obrazu platformy Docker](./media/image8.png)

<span data-ttu-id="fd51e-269">**Rysunek 5-5**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-269">**Figure 5-5**.</span></span> <span data-ttu-id="fd51e-270">Tworzenie niestandardowego obrazu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fd51e-270">Creating a custom Docker image</span></span>

<span data-ttu-id="fd51e-271">Opcjonalnie, zamiast bezpośredniego uruchamiania kompilacji platformy docker z folderu projektu, można najpierw wygenerować folder do wdrożenia z wymaganych bibliotek .NET i pliki binarne, uruchamiając `dotnet publish`, a następnie użyj `docker build` polecenia.</span><span class="sxs-lookup"><span data-stu-id="fd51e-271">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="fd51e-272">Spowoduje to utworzenie obrazu platformy Docker o nazwie `cesardl/netcore-webapi-microservice-docker:first`.</span><span class="sxs-lookup"><span data-stu-id="fd51e-272">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="fd51e-273">W tym przypadku: pierwszy to znacznik reprezentujący określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="fd51e-273">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="fd51e-274">Za Powtórz ten krok dla każdego obrazu niestandardowego, potrzebne do tworzenia aplikacji platformy Docker złożone.</span><span class="sxs-lookup"><span data-stu-id="fd51e-274">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="fd51e-275">Jeśli aplikacja składa się z wielu kontenerów (czyli jest aplikację obsługującą wiele kontenerów), możesz również użyć `docker-compose up --build` polecenie, aby skompilować wszystkie obrazy powiązane z jednym poleceniem, posługując się metadanymi ujawnione w pliki docker-compose.yml pokrewne .</span><span class="sxs-lookup"><span data-stu-id="fd51e-275">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="fd51e-276">Można znaleźć istniejących obrazów w repozytorium lokalnym za pomocą platformy docker polecenie obrazów, jak pokazano w rysunek 5 – 6.</span><span class="sxs-lookup"><span data-stu-id="fd51e-276">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Wyświetl ekran obrazów z polecenia obrazów platformy docker](./media/image9.png)

<span data-ttu-id="fd51e-278">**Rysunek 5 – 6.**</span><span class="sxs-lookup"><span data-stu-id="fd51e-278">**Figure 5-6.**</span></span> <span data-ttu-id="fd51e-279">Wyświetlanie istniejących obrazów za pomocą polecenia obrazów platformy docker</span><span class="sxs-lookup"><span data-stu-id="fd51e-279">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="fd51e-280">Tworzenie obrazów platformy Docker za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd51e-280">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="fd51e-281">Podczas tworzenia projektu z obsługą platformy Docker przy użyciu programu Visual Studio, nie są jawnie tworzone obrazu.</span><span class="sxs-lookup"><span data-stu-id="fd51e-281">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="fd51e-282">Zamiast tego obrazu zostanie utworzony po naciśnięciu klawisza **F5** (lub **Ctrl-F5**) do uruchamiania dockerized aplikacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="fd51e-282">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="fd51e-283">Ten krok jest automatycznie w programie Visual Studio i nie będziesz widzieć praca, ale jest ważne, że wiesz, co się dzieje na dole.</span><span class="sxs-lookup"><span data-stu-id="fd51e-283">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![4 — (opcjonalnie) usług Compose w pliku docker-compose.yml](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="fd51e-285">Krok 4.</span><span class="sxs-lookup"><span data-stu-id="fd51e-285">Step 4.</span></span> <span data-ttu-id="fd51e-286">Zdefiniuj swoje usługi w docker-compose.yml, podczas kompilowania aplikacji platformy Docker z wieloma kontenerami</span><span class="sxs-lookup"><span data-stu-id="fd51e-286">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="fd51e-287">[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) pliku pozwala zdefiniować zestaw powiązanych usług, który można wdrożyć jako złożone aplikacji za pomocą poleceń wdrażania.</span><span class="sxs-lookup"><span data-stu-id="fd51e-287">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="fd51e-288">Konfiguruje również jego relacji zależności i konfiguracji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fd51e-288">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="fd51e-289">Aby użyć pliku docker-compose.yml, musisz utworzyć głównego pliku lub folderu głównego rozwiązania z zawartością, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fd51e-289">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3.4'

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
      - ConnectionString=Server=sql.data;Port=1433;Database=CatalogDB;…
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

<span data-ttu-id="fd51e-290">Ten plik docker-compose.yml jest nieco uproszczona i scalone.</span><span class="sxs-lookup"><span data-stu-id="fd51e-290">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="fd51e-291">Zawiera on statyczne dane konfiguracji dla każdego kontenera (na przykład nazwa obrazu niestandardowego), który jest zawsze wymagany i informacje o konfiguracji, które mogą być zależne od środowiska wdrażania, takie jak parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="fd51e-291">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="fd51e-292">W kolejnych sekcjach dowiesz się, jak do podziału docker-compose.yml konfiguracji na wiele docker-compose plików i zastąpienie wartości w zależności od typu środowiska i wykonywanie (debugowanie lub wydanie).</span><span class="sxs-lookup"><span data-stu-id="fd51e-292">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="fd51e-293">Przykład pliku docker-compose.yml definiuje czterema usługami: `webmvc` usługi (aplikacja sieci web), dwie mikrousługi (`ordering.api` i `basket.api`) i danych z jednego źródła, `sql.data`zgodnie z programu SQL Server dla systemu Linux uruchomiony jako kontener.</span><span class="sxs-lookup"><span data-stu-id="fd51e-293">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering.api` and `basket.api`), and one data source container, `sql.data`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="fd51e-294">Każda usługa zostanie wdrożony jako kontener, dzięki czemu obraz platformy Docker jest wymagana dla każdego.</span><span class="sxs-lookup"><span data-stu-id="fd51e-294">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="fd51e-295">Plik docker-compose.yml określa nie tylko jakie kontenery są używane, ale ich indywidualnie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fd51e-295">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="fd51e-296">Na przykład `webmvc` definicja kontenera w plik yml:</span><span class="sxs-lookup"><span data-stu-id="fd51e-296">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="fd51e-297">Używa wstępnie utworzonych `eshop/web:latest` obrazu.</span><span class="sxs-lookup"><span data-stu-id="fd51e-297">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="fd51e-298">Jednakże można także skonfigurować obraz, który ma zostać utworzony jako część narzędzia docker compose wykonywania bez dodatkowej konfiguracji oparte na kompilację: sekcji w pliku docker-compose.</span><span class="sxs-lookup"><span data-stu-id="fd51e-298">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="fd51e-299">Inicjuje dwóch zmiennych środowiskowych (adres URL katalogu i OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="fd51e-299">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="fd51e-300">Przekazuje narażonych port 80 w kontenerze na zewnętrzny port 80 na maszynie hosta.</span><span class="sxs-lookup"><span data-stu-id="fd51e-300">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="fd51e-301">Linki w aplikacji sieci web do wykazu i kolejność usługi z ustawieniem depends_on.</span><span class="sxs-lookup"><span data-stu-id="fd51e-301">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="fd51e-302">Powoduje to, że usługa poczekaj, aż te usługi są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="fd51e-302">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="fd51e-303">Firma Microsoft będzie ponownie plik docker-compose.yml w dalszej części tego tematu, gdy opisujemy sposób implementacji aplikacji obsługującej wiele kontenerów i mikrousług.</span><span class="sxs-lookup"><span data-stu-id="fd51e-303">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="fd51e-304">Praca z docker-compose.yml w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fd51e-304">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="fd51e-305">Oprócz dodawania pliku Dockerfile do projektu, jak wspomniano wcześniej, Visual Studio 2017 (z 15.8 na) można dodać obsługę programu orchestrator narzędzia Docker Compose do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="fd51e-305">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="fd51e-306">Podczas dodawania obsługi orkiestratora kontenerów, jak pokazano w rysunek 5 – 7 po raz pierwszy, Visual Studio tworzy plik Dockerfile dla projektu i tworzy nowy projekt (sekcja service) w Twoim rozwiązaniu przy użyciu kilku globalnego `docker-compose*.yml` pliki, a następnie dodanie Projekt do tych plików.</span><span class="sxs-lookup"><span data-stu-id="fd51e-306">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="fd51e-307">Następnie można otworzyć pliki docker-compose.yml i zaktualizować je z dodatkowymi funkcjami.</span><span class="sxs-lookup"><span data-stu-id="fd51e-307">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="fd51e-308">Należy powtórzyć ten formularz, działania każdego projektu, które mają zostać uwzględnione w pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="fd51e-308">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="fd51e-309">W momencie pisania tego dokumentu program Visual Studio obsługuje koordynatorów narzędzia Docker Compose i Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="fd51e-309">At the time of this writing, Visual Studio supports Docker Compose and Service Fabric orchestrators.</span></span>

![Opcja menu kontekstowego, aby dodać obsługę programu orchestrator do projektu programu ASP.NET Core](./media/image21.png)

<span data-ttu-id="fd51e-311">**Rysunek 5 – 7**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-311">**Figure 5-7**.</span></span> <span data-ttu-id="fd51e-312">Dodanie obsługi platformy Docker w programie Visual Studio 2017, klikając prawym przyciskiem myszy projekt ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fd51e-312">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="fd51e-313">Po dodaniu obsługi orkiestratora do rozwiązania w programie Visual Studio, pojawi się także nowy węzeł (w `docker-compose.dcproj` pliku projektu) w Eksploratorze rozwiązań, który zawiera pliki docker-compose.yml dodano, jak pokazano w rysunek 5 – 8.</span><span class="sxs-lookup"><span data-stu-id="fd51e-313">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![docker-compose węzła w Eksploratorze rozwiązań](./media/image11.png)

<span data-ttu-id="fd51e-315">**Rysunek 5 – 8**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-315">**Figure 5-8**.</span></span> <span data-ttu-id="fd51e-316">**Narzędzia docker compose** węzła drzewa dodane w Eksploratorze rozwiązań 2017 r. w usłudze Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd51e-316">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="fd51e-317">Można wdrożyć aplikację obsługującą wiele kontenerów za pomocą pliku docker-compose.yml pojedynczego przy użyciu `docker-compose up` polecenia.</span><span class="sxs-lookup"><span data-stu-id="fd51e-317">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="fd51e-318">Jednak program Visual Studio dodaje grupę z nich, dzięki czemu można zastąpić wartości w zależności od środowiska (programowania lub produkcji) i typ wykonywania (wydania lub debugowania).</span><span class="sxs-lookup"><span data-stu-id="fd51e-318">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="fd51e-319">Ta funkcja zostaną wyjaśnione w kolejnych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="fd51e-319">This capability will be explained in later sections.</span></span>

![5 — uruchamianie kontenerów lub złożony aplikacji](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="fd51e-321">Krok 5.</span><span class="sxs-lookup"><span data-stu-id="fd51e-321">Step 5.</span></span> <span data-ttu-id="fd51e-322">Kompilowanie i uruchamianie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fd51e-322">Build and run your Docker application</span></span>

<span data-ttu-id="fd51e-323">Jeśli aplikacja ma tylko jeden kontener, możesz uruchomić go przez wdrożenie jej do hosta platformy Docker (maszyny Wirtualnej lub serwera fizycznego).</span><span class="sxs-lookup"><span data-stu-id="fd51e-323">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="fd51e-324">Jednak jeśli aplikacja zawiera wiele usług, możesz go wdrożyć jako złożone aplikacji, za pomocą jednego polecenia interfejsu wiersza polecenia (docker-compose się), lub za pomocą programu Visual Studio, które korzystają z tego polecenia w sposób niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="fd51e-324">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="fd51e-325">Przyjrzyjmy się różne opcje.</span><span class="sxs-lookup"><span data-stu-id="fd51e-325">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="fd51e-326">Option A: Uruchamianie aplikacji jednego kontenera</span><span class="sxs-lookup"><span data-stu-id="fd51e-326">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="fd51e-327">Za pomocą interfejsu wiersza polecenia platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fd51e-327">Using Docker CLI</span></span>

<span data-ttu-id="fd51e-328">Można uruchomić kontener platformy Docker przy użyciu `docker run` polecenia, jak pokazano w rysunek 5-9:</span><span class="sxs-lookup"><span data-stu-id="fd51e-328">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="fd51e-329">Powyższe polecenie spowoduje utworzenie nowego wystąpienia kontenera z określonego obrazu, za każdym razem, gdy jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="fd51e-329">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="fd51e-330">Możesz użyć `--name` parametr nadaj nazwę kontenera, a następnie użyć `docker start {name}` (lub kontenerze o identyfikatorze lub nazwie automatyczne) w celu uruchomienia istniejącego wystąpienia kontenera.</span><span class="sxs-lookup"><span data-stu-id="fd51e-330">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container id or automatic name) to run an existing container instance.</span></span>

![Wyświetl ekran podczas uruchamiania kontenera platformy Docker za pomocą platformy docker, uruchom polecenie](./media/image13.png)

<span data-ttu-id="fd51e-332">**Rysunek 5-9**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-332">**Figure 5-9**.</span></span> <span data-ttu-id="fd51e-333">Uruchamianie kontenera platformy Docker za pomocą platformy docker, uruchom polecenie</span><span class="sxs-lookup"><span data-stu-id="fd51e-333">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="fd51e-334">W takim przypadku polecenie wiąże wewnętrznego portu 5000 kontenera do portu 80 maszyny hosta.</span><span class="sxs-lookup"><span data-stu-id="fd51e-334">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="fd51e-335">Oznacza to, że host jest nasłuchuje na porcie 80 i przekazywania do portu 5000 kontenera.</span><span class="sxs-lookup"><span data-stu-id="fd51e-335">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="fd51e-336">Wartość skrótu, wyświetlany jest identyfikator kontenera i również został przypisany losowe czytelna nazwa Jeśli `--name` opcja nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="fd51e-336">The hash shown is the container id and it’s also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="fd51e-337">Za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd51e-337">Using Visual Studio</span></span>

<span data-ttu-id="fd51e-338">Jeśli jeszcze nie została dodana obsługa orkiestratora kontenerów, można również uruchomić aplikację jeden kontener w programie Visual Studio, naciskając klawisz **Ctrl-F5** i można również użyć **F5** do debugowania aplikacji w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="fd51e-338">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="fd51e-339">Kontener działa lokalnie przy użyciu platformy docker, uruchom.</span><span class="sxs-lookup"><span data-stu-id="fd51e-339">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="fd51e-340">Opcja B: Uruchamianie aplikacji z wieloma kontenerami</span><span class="sxs-lookup"><span data-stu-id="fd51e-340">Option B: Running a multi-container application</span></span>

<span data-ttu-id="fd51e-341">W większości przypadków enterprise aplikację platformy Docker będzie składać się z wielu usług, co oznacza, że należy uruchomić aplikację obsługującą wiele kontenerów, jak pokazano na rysunku 5-10.</span><span class="sxs-lookup"><span data-stu-id="fd51e-341">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![Maszyny Wirtualnej za pomocą wielu kontenerów platformy Docker](./media/image14.png)

<span data-ttu-id="fd51e-343">**Rysunek 5 – 10**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-343">**Figure 5-10**.</span></span> <span data-ttu-id="fd51e-344">Maszyny Wirtualnej przy użyciu kontenerów Docker wdrożonych</span><span class="sxs-lookup"><span data-stu-id="fd51e-344">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="fd51e-345">Za pomocą interfejsu wiersza polecenia platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fd51e-345">Using Docker CLI</span></span>

<span data-ttu-id="fd51e-346">Aby uruchomić aplikację obsługującą wiele kontenerów za pomocą interfejsu wiersza polecenia platformy Docker, należy użyć `docker-compose up` polecenia.</span><span class="sxs-lookup"><span data-stu-id="fd51e-346">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="fd51e-347">To polecenie używa **docker-compose.yml** pliku, że masz na poziomie rozwiązania, aby wdrożyć aplikację obsługującą wiele kontenerów.</span><span class="sxs-lookup"><span data-stu-id="fd51e-347">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="fd51e-348">Rysunek 5 – 11 przedstawia wyniki przy uruchamianiu polecenia z katalogiem głównym rozwiązania, który zawiera plik docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="fd51e-348">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Ekranu widoku podczas uruchamiania narzędzia docker compose się polecenia](./media/image15.png)

<span data-ttu-id="fd51e-350">**Rysunek 5 – 11**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-350">**Figure 5-11**.</span></span> <span data-ttu-id="fd51e-351">Przykład powoduje podczas uruchamiania narzędzia docker compose się polecenia</span><span class="sxs-lookup"><span data-stu-id="fd51e-351">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="fd51e-352">Po platformy docker-compose się polecenia uruchomienia, aplikacji i jej powiązane kontenery są wdrażane w sieci hosta platformy Docker, jak pokazano na rysunku 5-10.</span><span class="sxs-lookup"><span data-stu-id="fd51e-352">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="fd51e-353">Za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd51e-353">Using Visual Studio</span></span>

<span data-ttu-id="fd51e-354">Uruchamianie aplikacji z wieloma kontenerami za pomocą programu Visual Studio 2017 nie można pobrać wszystkie prostsze.</span><span class="sxs-lookup"><span data-stu-id="fd51e-354">Running a multi-container application using Visual Studio 2017 can't get any simpler.</span></span> <span data-ttu-id="fd51e-355">Wystarczy nacisnąć klawisz **Ctrl-F5** do uruchomienia lub **F5** do debugowania, jak zwykle — Konfigurowanie **narzędzia docker compose** projekt jako projekt startowy.</span><span class="sxs-lookup"><span data-stu-id="fd51e-355">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="fd51e-356">Visual Studio obsługuje wszystkie ustawienia potrzebne, aby można było utworzyć punktów przerwania w zwykły sposób i debugowania, co ostatecznie stają się niezależnych procesy działające w "serwerów zdalnych", po prostu taką jak ta.</span><span class="sxs-lookup"><span data-stu-id="fd51e-356">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", just like that.</span></span>

<span data-ttu-id="fd51e-357">Jak wspomniano wcześniej, podczas dodawania każdego kolejnego obsługę rozwiązań platformy Docker do projektu w ramach rozwiązania, projektu jest skonfigurowany w pliku globalnego docker-compose.yml (poziomie rozwiązania), który umożliwia uruchamiania lub debugowania całego rozwiązania tylko raz.</span><span class="sxs-lookup"><span data-stu-id="fd51e-357">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="fd51e-358">Program Visual Studio uruchomi jeden kontener dla każdego projektu, który ma włączoną obsługę rozwiązań platformy Docker i wykonaj wszystkie kroki wewnętrznego dla Ciebie (dotnet publikowania, docker kompilacji itd.).</span><span class="sxs-lookup"><span data-stu-id="fd51e-358">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="fd51e-359">Jeśli chcesz wykonać rzut oka na wszystkich drudgery, zapoznaj się z pliku:</span><span class="sxs-lookup"><span data-stu-id="fd51e-359">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="fd51e-360">Istotną kwestią jest, jak pokazano na rysunku 5-12, w programie Visual Studio 2017 dodatkowego **Docker** polecenie, aby uzyskać kluczowe działania F5.</span><span class="sxs-lookup"><span data-stu-id="fd51e-360">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="fd51e-361">Ta opcja pozwala uruchomić lub debugować aplikację obsługującą wiele kontenerów przez uruchomienie wszystkich kontenerów, które są zdefiniowane w plikach docker-compose.yml na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="fd51e-361">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="fd51e-362">Możliwość debugowania rozwiązań do obsługi wielu kontenerów oznacza, że można ustawić kilka punktów przerwania, w każdym punkcie przerwania, które znajdują się w innym projekcie (kontenera), a podczas debugowania w programie Visual Studio przestanie w punktach przerwania, zdefiniowane w różnych projektach i uruchomiona na różnych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="fd51e-362">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Visual Studio debugowania narzędzi systemem-projektów docker compose](./media/image16.png)

<span data-ttu-id="fd51e-364">**Rysunek 5 – 12**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-364">**Figure 5-12**.</span></span> <span data-ttu-id="fd51e-365">Uruchamianie aplikacji obsługującej wiele kontenerów w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fd51e-365">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="fd51e-366">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="fd51e-366">Additional resources</span></span>

- <span data-ttu-id="fd51e-367">**Wdrażanie kontenera platformy ASP.NET ha zdalnym hoście platformy Docker** \\</span><span class="sxs-lookup"><span data-stu-id="fd51e-367">**Deploy an ASP.NET container to a remote Docker host** \\</span></span>
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="fd51e-368">Uwaga dotycząca testowanie i wdrażanie przy użyciu koordynatorów</span><span class="sxs-lookup"><span data-stu-id="fd51e-368">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="fd51e-369">Narzędzia docker compose się i platformy docker, Uruchom polecenia (lub uruchamianie i debugowanie kontenerów w programie Visual Studio) są odpowiednie do testowania kontenerów w środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="fd51e-369">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="fd51e-370">Jednak to podejście nie należy używać w przypadku wdrożeń produkcyjnych, w którym powinien dotyczyć koordynatorów, takich jak [Kubernetes](https://kubernetes.io/) lub [usługi Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span><span class="sxs-lookup"><span data-stu-id="fd51e-370">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="fd51e-371">Jeśli używasz usługi Kubernetes, trzeba użyć [zasobników](https://kubernetes.io/docs/concepts/workloads/pods/pod/) do organizowania kontenerów i [usług](https://kubernetes.io/docs/concepts/services-networking/service/) do ich sieci.</span><span class="sxs-lookup"><span data-stu-id="fd51e-371">If you're using Kubernetes you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="fd51e-372">Możesz także użyć [wdrożeń](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) do organizowania zasobnika tworzenia i modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="fd51e-372">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![6 — testowanie aplikacji sieci Web lub mikrousług](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="fd51e-374">Krok 6.</span><span class="sxs-lookup"><span data-stu-id="fd51e-374">Step 6.</span></span> <span data-ttu-id="fd51e-375">Testowanie aplikacji platformy Docker za pomocą lokalnego hosta platformy Docker</span><span class="sxs-lookup"><span data-stu-id="fd51e-375">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="fd51e-376">W tym kroku różnią się w zależności od tego, co robi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fd51e-376">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="fd51e-377">W prostej aplikacji sieci Web platformy .NET Core, który jest wdrażany jako jeden kontener lub usługi uzyskać dostęp do usługi, otwierając przeglądarki na hoście platformy Docker i przechodząc do tej lokacji, jak pokazano w rysunek 5-13.</span><span class="sxs-lookup"><span data-stu-id="fd51e-377">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="fd51e-378">(Jeśli konfiguracji w pliku Dockerfile kontenera jest mapowany na port na hoście, który jest inna niż 80, obejmuje port hosta w adresie URL).</span><span class="sxs-lookup"><span data-stu-id="fd51e-378">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Widok przeglądarki odpowiedzi HTTP punktu końcowego interfejsu API](./media/image18.png)

<span data-ttu-id="fd51e-380">**Rysunek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-380">**Figure 5-13**.</span></span> <span data-ttu-id="fd51e-381">Przykład testowanie aplikacji platformy Docker lokalnie przy użyciu localhost</span><span class="sxs-lookup"><span data-stu-id="fd51e-381">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="fd51e-382">Adres IP hosta w przypadku platformy Docker nie wskazuje localhost (domyślnie, gdy za pomocą platformy Docker CE, powinien), aby przejść do usługi, użyj adresu IP karty sieciowej komputera.</span><span class="sxs-lookup"><span data-stu-id="fd51e-382">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="fd51e-383">Należy pamiętać, że ten adres URL w przeglądarce korzysta z portu 80 na przykład kontenerem omawiana.</span><span class="sxs-lookup"><span data-stu-id="fd51e-383">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="fd51e-384">Jednak wewnętrznie żądania nastąpi przekierowanie do portu 5000, ponieważ było jak miała być wdrożona przy użyciu rozwiązania docker, uruchom polecenie, zgodnie z opisem w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="fd51e-384">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="fd51e-385">Możesz również przetestować aplikację przy użyciu programu curl w terminalu, jak pokazano w rysunek 5-14.</span><span class="sxs-lookup"><span data-stu-id="fd51e-385">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="fd51e-386">W przypadku instalacji platformy Docker na Windows domyślny adres IP hosta platformy Docker jest zawsze 10.0.75.1 Oprócz rzeczywistego adresu IP tego komputera.</span><span class="sxs-lookup"><span data-stu-id="fd51e-386">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Wyświetl ekran odpowiedzi punktu końcowego interfejsu API za pomocą programu curl](./media/image19.png)

<span data-ttu-id="fd51e-388">**Rysunek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-388">**Figure 5-14**.</span></span> <span data-ttu-id="fd51e-389">Przykład testowanie aplikacji platformy Docker lokalnie przy użyciu programu curl</span><span class="sxs-lookup"><span data-stu-id="fd51e-389">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="fd51e-390">Testowanie i debugowanie kontenerów przy użyciu programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fd51e-390">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="fd51e-391">Gdy uruchamianie i debugowanie kontenerów za pomocą programu Visual Studio 2017, tak jak w przypadku braku pojemników można debugować aplikację platformy .NET w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="fd51e-391">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="fd51e-392">Testowanie i debugowanie bez programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd51e-392">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="fd51e-393">Jeżeli projektujesz przy użyciu podejścia edytora/CLI debugowanie kontenerów jest trudniejsze, i chcesz debugować, generując ślady.</span><span class="sxs-lookup"><span data-stu-id="fd51e-393">If you're developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="fd51e-394">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="fd51e-394">Additional resources</span></span>

- <span data-ttu-id="fd51e-395">**Debugowanie aplikacji w lokalnym kontenerze Docker** \\</span><span class="sxs-lookup"><span data-stu-id="fd51e-395">**Debugging apps in a local Docker container** \\</span></span>
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- <span data-ttu-id="fd51e-396">**Steve Lasker. Kompilowanie, debugowanie, wdrażanie aplikacji platformy ASP.NET Core przy użyciu platformy Docker.**</span><span class="sxs-lookup"><span data-stu-id="fd51e-396">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="fd51e-397">Film wideo.</span><span class="sxs-lookup"><span data-stu-id="fd51e-397">Video.</span></span> \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="fd51e-398">Uproszczone przepływu pracy podczas tworzenia kontenerów przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd51e-398">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="fd51e-399">Skutecznie przepływ pracy przy użyciu programu Visual Studio jest znacznie prostsze niż w przypadku użycia podejście edytora/interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fd51e-399">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="fd51e-400">Większość czynności wymagane przez platformę Docker związane z pliku Dockerfile i pliki docker-compose.yml są ukryte lub uproszczone przez program Visual Studio, jak pokazano w rysunek 5 – 15.</span><span class="sxs-lookup"><span data-stu-id="fd51e-400">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![Uproszczony przepływu pracy opracowywania kontenera za pomocą programu Visual Studio: 1 — kodu aplikacji, 2 - Obsługa Dodaj platformy Docker do projektów (tylko raz), 3 - uruchomienia kontenera lub rozwiązania docker-compose aplikacji, 4 - Test aplikacji sieci Web lub mikrousług, 5 - wypychania do repozytorium i powtórz tę czynność.](./media/image20.png)

<span data-ttu-id="fd51e-402">**Rysunek 5 – 15**.</span><span class="sxs-lookup"><span data-stu-id="fd51e-402">**Figure 5-15**.</span></span> <span data-ttu-id="fd51e-403">Uproszczone przepływu pracy podczas tworzenia w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd51e-403">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="fd51e-404">Ponadto należy wykonać tylko raz w kroku 2 (Dodawanie obsługę platformy Docker do swoich projektów).</span><span class="sxs-lookup"><span data-stu-id="fd51e-404">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="fd51e-405">W związku z tym przepływ pracy jest podobne do zadań rozwoju zwykle, gdy przy użyciu platformy .NET do tworzenia innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fd51e-405">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="fd51e-406">Musisz wiedzieć, co się dzieje dzieje się w tle (procesu tworzenia obrazu, jakie obrazy podstawowe korzystasz, wdrażanie kontenerów, itp.) i czasami również należy edytować plik Dockerfile lub docker-compose.yml dostosowywania zachowania.</span><span class="sxs-lookup"><span data-stu-id="fd51e-406">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="fd51e-407">Jednak większość pracy jest znacznie uproszczone przy użyciu programu Visual Studio, co możesz o wiele bardziej produktywne.</span><span class="sxs-lookup"><span data-stu-id="fd51e-407">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="fd51e-408">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="fd51e-408">Additional resources</span></span>

- <span data-ttu-id="fd51e-409">**Steve Lasker. Programowanie na platformie .NET platformy docker przy użyciu programu Visual Studio 2017** \\</span><span class="sxs-lookup"><span data-stu-id="fd51e-409">**Steve Lasker. .NET Docker Development with Visual Studio 2017** \\</span></span>
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="fd51e-410">Używanie poleceń programu PowerShell w pliku Dockerfile do konfigurowania kontenerów Windows</span><span class="sxs-lookup"><span data-stu-id="fd51e-410">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="fd51e-411">[Kontenery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) umożliwiają konwertowanie istniejących aplikacji Windows obrazów platformy Docker i wdrożyć je przy użyciu tych samych narzędzi, jak w pozostałych ekosystemie Docker.</span><span class="sxs-lookup"><span data-stu-id="fd51e-411">[Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="fd51e-412">Aby użyć kontenery Windows, możesz uruchomić poleceń programu PowerShell w pliku Dockerfile, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fd51e-412">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="fd51e-413">W tym przypadku jesteśmy przy użyciu obrazu podstawowego systemu Windows Server Core (ustawienie FROM) i instalowanie usług IIS za pomocą polecenia programu PowerShell (Ustawienie Uruchom).</span><span class="sxs-lookup"><span data-stu-id="fd51e-413">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="fd51e-414">W podobny sposób można również użyć poleceń programu PowerShell do skonfigurowania dodatkowych składników, takich jak ASP.NET 4.x, .NET 4.6 lub innego oprogramowania Windows.</span><span class="sxs-lookup"><span data-stu-id="fd51e-414">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="fd51e-415">Na przykład następujące polecenie w pliku Dockerfile konfiguruje ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="fd51e-415">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="fd51e-416">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="fd51e-416">Additional resources</span></span>

- <span data-ttu-id="fd51e-417">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="fd51e-417">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="fd51e-418">Przykładowe polecenia programu PowerShell do uruchamiania z plików dockerfile w celu uwzględnienia funkcji Windows. \\</span><span class="sxs-lookup"><span data-stu-id="fd51e-418">Example PowerShell commands to run from dockerfiles to include Windows features.\\</span></span>
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
><span data-ttu-id="fd51e-419">[Poprzednie](index.md)
>[dalej](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="fd51e-419">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
