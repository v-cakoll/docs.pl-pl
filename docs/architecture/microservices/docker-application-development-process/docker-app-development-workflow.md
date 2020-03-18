---
title: Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker
description: Zapoznaj się ze szczegółami przepływu pracy do tworzenia aplikacji opartych na platformie Docker. Rozpocznij krok po kroku i dostać się do niektórych szczegółów, aby zoptymalizować Pliki Dockerfiles i zakończyć uproszczony przepływ pracy dostępny podczas korzystania z programu Visual Studio.
ms.date: 01/30/2020
ms.openlocfilehash: c58ea2436027968143777a19286a1a0a72107717
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401642"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="9579a-104">Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="9579a-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="9579a-105">Cykl rozwoju aplikacji rozpoczyna się na komputerze, jako deweloper, gdzie kod aplikacji przy użyciu preferowanego języka i przetestować go lokalnie.</span><span class="sxs-lookup"><span data-stu-id="9579a-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="9579a-106">Dzięki temu przepływowi pracy, niezależnie od wybranego języka, struktury i platformy, zawsze tworzysz i testujesz kontenery platformy Docker, ale robisz to lokalnie.</span><span class="sxs-lookup"><span data-stu-id="9579a-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="9579a-107">Każdy kontener (wystąpienie obrazu platformy Docker) zawiera następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="9579a-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="9579a-108">Wybór systemu operacyjnego, na przykład dystrybucja systemu Linux, Windows Nano Server lub Windows Server Core.</span><span class="sxs-lookup"><span data-stu-id="9579a-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="9579a-109">Pliki dodawane podczas tworzenia, na przykład kod źródłowy i pliki binarne aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9579a-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="9579a-110">Informacje o konfiguracji, takie jak ustawienia środowiska i zależności.</span><span class="sxs-lookup"><span data-stu-id="9579a-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="9579a-111">Przepływ pracy do tworzenia aplikacji opartych na kontenerach platformy Docker</span><span class="sxs-lookup"><span data-stu-id="9579a-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="9579a-112">W tej sekcji *opisano* przepływ pracy tworzenia pętli wewnętrznej dla aplikacji opartych na kontenerach platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="9579a-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="9579a-113">Przepływ pracy w pętli wewnętrznej oznacza, że nie uwzględnia szerszego przepływu pracy DevOps, który może obejmować do wdrożenia produkcyjnego i po prostu koncentruje się na pracach rozwojowych wykonywanych na komputerze dewelopera.</span><span class="sxs-lookup"><span data-stu-id="9579a-113">The inner-loop workflow means it's not considering the broader DevOps workflow, which can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="9579a-114">Początkowe kroki konfigurowania środowiska nie są uwzględniane, ponieważ te kroki są wykonywane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="9579a-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="9579a-115">Aplikacja składa się z własnych usług oraz dodatkowych bibliotek (zależności).</span><span class="sxs-lookup"><span data-stu-id="9579a-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="9579a-116">Poniżej przedstawiono podstawowe kroki, które zwykle wykonuje się podczas tworzenia aplikacji platformy Docker, jak pokazano na rysunku 5-1.</span><span class="sxs-lookup"><span data-stu-id="9579a-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram przedstawiający 7 kroków potrzebnych do utworzenia aplikacji konteneryzowanej.":::
<span data-ttu-id="9579a-118">Proces tworzenia aplikacji platformy Docker: 1 - Kod aplikacji, 2 - Pisanie dockerfile/s, 3 - Tworzenie obrazów zdefiniowanych w dockerfile/s, 4 - (opcjonalnie) Compose usługi w pliku docker-compose.yml, 5 - Uruchom kontener lub docker-compose aplikacji, 6 - Testowanie aplikacji lub mikrousług, 7 - Push to repo i powtórz.</span><span class="sxs-lookup"><span data-stu-id="9579a-118">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="9579a-119">**Rysunek 5-1.**</span><span class="sxs-lookup"><span data-stu-id="9579a-119">**Figure 5-1.**</span></span> <span data-ttu-id="9579a-120">Przepływ pracy krok po kroku do tworzenia aplikacji konteneryzowanych platformy Docker</span><span class="sxs-lookup"><span data-stu-id="9579a-120">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="9579a-121">W tej sekcji cały ten proces jest szczegółowy i każdy ważny krok jest wyjaśniony przez skupienie się na środowisku programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9579a-121">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="9579a-122">Korzystając z metody tworzenia edytora/wiersza wiersza wiersza (na przykład Visual Studio Code plus Docker CLI w systemie macOS lub Windows), musisz znać każdy krok, zazwyczaj bardziej szczegółowo niż w przypadku korzystania z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9579a-122">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="9579a-123">Aby uzyskać więcej informacji na temat pracy w środowisku interfejsów firm cli, zobacz [cykl życia aplikacji dokowania konteneryzowanego e-booka z platformami i narzędziami firmy Microsoft](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="9579a-123">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="9579a-124">Gdy używasz programu Visual Studio 2019, wiele z tych kroków jest obsługiwanych dla Ciebie, co znacznie zwiększa produktywność.</span><span class="sxs-lookup"><span data-stu-id="9579a-124">When you're using Visual Studio 2019, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="9579a-125">Jest to szczególnie ważne, gdy używasz programu Visual Studio 2019 i jest przeznaczony dla aplikacji wielokontenerowych.</span><span class="sxs-lookup"><span data-stu-id="9579a-125">This is especially true when you're using Visual Studio 2019 and targeting multi-container applications.</span></span> <span data-ttu-id="9579a-126">Na przykład za pomocą jednego kliknięcia `Dockerfile` myszy `docker-compose.yml` program Visual Studio dodaje plik i plik do projektów z konfiguracją dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9579a-126">For instance, with just one mouse click, Visual Studio adds the `Dockerfile` and `docker-compose.yml` file to your projects with the configuration for your application.</span></span> <span data-ttu-id="9579a-127">Po uruchomieniu aplikacji w programie Visual Studio tworzy obraz platformy Docker i uruchamia aplikację wielokontenerową bezpośrednio w platformie Docker; umożliwia nawet debugowanie kilku kontenerów jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="9579a-127">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="9579a-128">Te funkcje zwiększą szybkość rozwoju.</span><span class="sxs-lookup"><span data-stu-id="9579a-128">These features will boost your development speed.</span></span>

<span data-ttu-id="9579a-129">Jednak tylko dlatego, że visual studio sprawia, że te kroki automatyczne nie oznacza, że nie trzeba wiedzieć, co się dzieje pod platformą Docker.</span><span class="sxs-lookup"><span data-stu-id="9579a-129">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="9579a-130">W związku z tym następujące wskazówki szczegółowo co krok.</span><span class="sxs-lookup"><span data-stu-id="9579a-130">Therefore, the following guidance details every step.</span></span>

![Obraz dla kroku 1.](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="9579a-132">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="9579a-132">Step 1.</span></span> <span data-ttu-id="9579a-133">Rozpoczynanie kodowania i tworzenie początkowej aplikacji lub linii bazowej usługi</span><span class="sxs-lookup"><span data-stu-id="9579a-133">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="9579a-134">Tworzenie aplikacji platformy Docker jest podobny do sposobu tworzenia aplikacji bez platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="9579a-134">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="9579a-135">Różnica polega na tym, że podczas opracowywania dla platformy Docker wdrażasz i testujesz aplikację lub usługi uruchomione w kontenerach platformy Docker w środowisku lokalnym (konfiguracja maszyny Wirtualnej systemu Linux przez platformę Docker lub bezpośrednio system Windows, jeśli używasz kontenerów systemu Windows).</span><span class="sxs-lookup"><span data-stu-id="9579a-135">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="9579a-136">Konfigurowanie środowiska lokalnego za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9579a-136">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="9579a-137">Aby rozpocząć, upewnij się, że masz zainstalowaną [wersję Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) dla systemu Windows, jak wyjaśniono w poniższych instrukcjach:</span><span class="sxs-lookup"><span data-stu-id="9579a-137">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="9579a-138">Wprowadzenie do platformy Docker CE dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9579a-138">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="9579a-139">Ponadto potrzebne jest program Visual Studio 2019 w wersji 16.4 lub nowszej, z zainstalowanym obciążeniem **programistycznym .NET Core dla wielu platform,** jak pokazano na rysunku 5-2.</span><span class="sxs-lookup"><span data-stu-id="9579a-139">In addition, you need Visual Studio 2019 version 16.4 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![Zrzut ekranu przedstawiający wybór rozwoju wielu platform .NET Core.](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

<span data-ttu-id="9579a-141">**Rysunek 5-2**.</span><span class="sxs-lookup"><span data-stu-id="9579a-141">**Figure 5-2**.</span></span> <span data-ttu-id="9579a-142">Wybieranie **wieloplatformowego obciążenia programistycznego programu .NET Core** podczas instalacji programu Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="9579a-142">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2019 setup</span></span>

<span data-ttu-id="9579a-143">Można rozpocząć kodowanie aplikacji w zwykły .NET (zwykle w .NET Core, jeśli planujesz używać kontenerów) nawet przed włączeniem platformy Docker w aplikacji i wdrażania i testowania w platformie Docker.</span><span class="sxs-lookup"><span data-stu-id="9579a-143">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="9579a-144">Zaleca się jednak, aby rozpocząć pracę nad platformą Docker tak szybko, jak to możliwe, ponieważ będzie to rzeczywiste środowisko i wszelkie problemy mogą być wykrywane tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="9579a-144">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="9579a-145">Jest to zalecane, ponieważ visual studio sprawia, że tak łatwo pracować z platformą Docker, że prawie czuje się przezroczysty — najlepszym przykładem podczas debugowania aplikacji wielokontenerowych z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9579a-145">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9579a-146">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="9579a-146">Additional resources</span></span>

- <span data-ttu-id="9579a-147">**Wprowadzenie do platformy Docker CE dla systemu Windows** </span><span class="sxs-lookup"><span data-stu-id="9579a-147">**Get started with Docker CE for Windows** </span></span>\
  <https://docs.docker.com/docker-for-windows/>

- <span data-ttu-id="9579a-148">**Studio Wizualne 2019** </span><span class="sxs-lookup"><span data-stu-id="9579a-148">**Visual Studio 2019** </span></span>\
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

![Obraz dla kroku 2.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="9579a-150">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="9579a-150">Step 2.</span></span> <span data-ttu-id="9579a-151">Tworzenie pliku Dockerfile powiązanego z istniejącym obrazem podstawowym platformy .NET</span><span class="sxs-lookup"><span data-stu-id="9579a-151">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="9579a-152">Potrzebny jest plik Dockerfile dla każdego niestandardowego obrazu, który chcesz zbudować; potrzebny jest również plik Dockerfile dla każdego kontenera do wdrożenia, niezależnie od tego, czy wdrażasz automatycznie z programu Visual Studio, czy ręcznie przy użyciu polecenia docker CLI (docker run i docker-compose).</span><span class="sxs-lookup"><span data-stu-id="9579a-152">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="9579a-153">Jeśli aplikacja zawiera jedną usługę niestandardową, potrzebujesz jednego pliku Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="9579a-153">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="9579a-154">Jeśli aplikacja zawiera wiele usług (jak w architekturze mikrousług), potrzebujesz jednego pliku Dockerfile dla każdej usługi.</span><span class="sxs-lookup"><span data-stu-id="9579a-154">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="9579a-155">Plik Dockerfile jest umieszczany w folderze głównym aplikacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="9579a-155">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="9579a-156">Zawiera polecenia, które informują platformę Docker, jak skonfigurować i uruchomić aplikację lub usługę w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="9579a-156">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="9579a-157">Można ręcznie utworzyć plik Dockerfile w kodzie i dodać go do projektu wraz z zależnościami .NET.</span><span class="sxs-lookup"><span data-stu-id="9579a-157">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="9579a-158">Dzięki programowi Visual Studio i jego narzędziom do platformy Docker to zadanie wymaga tylko kilku kliknięć myszą.</span><span class="sxs-lookup"><span data-stu-id="9579a-158">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="9579a-159">Podczas tworzenia nowego projektu w programie Visual Studio 2019 istnieje opcja o nazwie **Włącz obsługę platformy Docker**, jak pokazano na rysunku 5-3.</span><span class="sxs-lookup"><span data-stu-id="9579a-159">When you create a new project in Visual Studio 2019, there's an option named **Enable Docker Support**, as shown in Figure 5-3.</span></span>

![Zrzut ekranu przedstawiający pole wyboru Włącz obsługę platformy Docker.](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

<span data-ttu-id="9579a-161">**Rysunek 5-3**.</span><span class="sxs-lookup"><span data-stu-id="9579a-161">**Figure 5-3**.</span></span> <span data-ttu-id="9579a-162">Włączanie obsługi platformy Docker podczas tworzenia nowego projektu ASP.NET Core w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="9579a-162">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2019</span></span>

<span data-ttu-id="9579a-163">Obsługę platformy Docker można również włączyć w istniejącym projekcie aplikacji sieci Web ASP.NET Core, klikając projekt prawym przyciskiem myszy w **Eksploratorze rozwiązań** i wybierając polecenie **Dodaj** > **obsługę platformy Docker...**, jak pokazano na rysunku 5-4.</span><span class="sxs-lookup"><span data-stu-id="9579a-163">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support...**, as shown in Figure 5-4.</span></span>

![Zrzut ekranu przedstawiający opcję Docker Support w menu Dodaj.](./media/docker-app-development-workflow/add-docker-support-option.png)

<span data-ttu-id="9579a-165">**Rysunek 5-4**.</span><span class="sxs-lookup"><span data-stu-id="9579a-165">**Figure 5-4**.</span></span> <span data-ttu-id="9579a-166">Włączanie obsługi platformy Docker w istniejącym projekcie programu Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="9579a-166">Enabling Docker support in an existing Visual Studio 2019 project</span></span>

<span data-ttu-id="9579a-167">Ta akcja dodaje *plik Dockerfile* do projektu z wymaganą konfiguracją i jest dostępna tylko w ASP.NET projektów Core.</span><span class="sxs-lookup"><span data-stu-id="9579a-167">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="9579a-168">W podobny sposób program Visual Studio `docker-compose.yml` może również dodać plik dla całego rozwiązania z opcją **Dodaj > Obsługę koordynatora kontenerów...**. W kroku 4 przeanalizujemy tę opcję bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="9579a-168">In a similar fashion, Visual Studio can also add a `docker-compose.yml` file for the whole solution with the option **Add > Container Orchestrator Support...**. In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="9579a-169">Korzystanie z istniejącego oficjalnego obrazu platformy Docker platformy .NET</span><span class="sxs-lookup"><span data-stu-id="9579a-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="9579a-170">Zazwyczaj tworzysz niestandardowy obraz dla kontenera na obrazie bazowym uzyskanym z oficjalnego repozytorium, takiego jak rejestr [docker hub.](https://hub.docker.com/)</span><span class="sxs-lookup"><span data-stu-id="9579a-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="9579a-171">To jest dokładnie to, co dzieje się w ramach obejmuje po włączeniu obsługi platformy Docker w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9579a-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="9579a-172">Plik Dockerfile użyje `dotnet/core/aspnet` istniejącego obrazu.</span><span class="sxs-lookup"><span data-stu-id="9579a-172">Your Dockerfile will use an existing `dotnet/core/aspnet` image.</span></span>

<span data-ttu-id="9579a-173">Wcześniej wyjaśniliśmy, które obrazy platformy Docker i repozytorów można użyć, w zależności od struktury i os wybrałeś.</span><span class="sxs-lookup"><span data-stu-id="9579a-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="9579a-174">Na przykład, jeśli chcesz użyć ASP.NET Core (Linux lub `mcr.microsoft.com/dotnet/core/aspnet:3.1`Windows), obraz do użycia jest .</span><span class="sxs-lookup"><span data-stu-id="9579a-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="9579a-175">W związku z tym wystarczy określić, jaki podstawowy obraz platformy Docker będzie używany dla kontenera.</span><span class="sxs-lookup"><span data-stu-id="9579a-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="9579a-176">Można to zrobić, dodając `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` do pliku Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="9579a-176">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` to your Dockerfile.</span></span> <span data-ttu-id="9579a-177">To będzie wykonywane automatycznie przez program Visual Studio, ale jeśli chcesz zaktualizować wersję, należy zaktualizować tę wartość.</span><span class="sxs-lookup"><span data-stu-id="9579a-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="9579a-178">Przy użyciu oficjalnego repozytorium obrazów .NET z usługi Docker Hub z numerem wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym rozwoju, testowania i produkcji).</span><span class="sxs-lookup"><span data-stu-id="9579a-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="9579a-179">W poniższym przykładzie przedstawiono przykładowy plik Dockerfile dla kontenera ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9579a-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="9579a-180">W tym przypadku obraz jest oparty na wersji 3.1 oficjalnego ASP.NET obrazu core docker (multi-arch dla Linuksa i Windows).</span><span class="sxs-lookup"><span data-stu-id="9579a-180">In this case, the image is based on version 3.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="9579a-181">Jest to `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`ustawienie .</span><span class="sxs-lookup"><span data-stu-id="9579a-181">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="9579a-182">(Aby uzyskać więcej informacji na temat tego obrazu podstawowego, zobacz stronę [obrazu docker .NET).](https://hub.docker.com/_/microsoft-dotnet-core/) W pliku Dockerfile należy również poinstruować platformę Docker, aby nasłuchiwać na porcie TCP, którego będziesz używać w czasie wykonywania (w tym przypadku port 80, zgodnie z ustawieniem EXPOSE).</span><span class="sxs-lookup"><span data-stu-id="9579a-182">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="9579a-183">Można określić dodatkowe ustawienia konfiguracji w pliku Dockerfile, w zależności od języka i struktury, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="9579a-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="9579a-184">Na przykład wiersz ENTRYPOINT `["dotnet", "MySingleContainerWebApp.dll"]` z nakazem platformy Docker o uruchomieniu aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9579a-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="9579a-185">Jeśli używasz sdk i .NET Core CLI (dotnet CLI) do tworzenia i uruchamiania aplikacji .NET, to ustawienie będzie inna.</span><span class="sxs-lookup"><span data-stu-id="9579a-185">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="9579a-186">Najważniejsze jest to, że linia ENTRYPOINT i inne ustawienia będą się różnić w zależności od języka i platformy wybranej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9579a-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9579a-187">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="9579a-187">Additional resources</span></span>

- <span data-ttu-id="9579a-188">**Tworzenie obrazów platformy Docker dla aplikacji .NET Core** </span><span class="sxs-lookup"><span data-stu-id="9579a-188">**Building Docker Images for .NET Core Applications** </span></span>\
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- <span data-ttu-id="9579a-189">**Zbuduj swój własny obraz**.</span><span class="sxs-lookup"><span data-stu-id="9579a-189">**Build your own image**.</span></span> <span data-ttu-id="9579a-190">W oficjalnej dokumentacji platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="9579a-190">In the official Docker documentation.</span></span>\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- <span data-ttu-id="9579a-191">**Aktualizowanie obrazów kontenerów .NET** </span><span class="sxs-lookup"><span data-stu-id="9579a-191">**Staying up-to-date with .NET Container Images** </span></span>\
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="9579a-192">**Korzystanie z platformy .NET i platformy Docker Razem — aktualizacja dockerCon 2018** </span><span class="sxs-lookup"><span data-stu-id="9579a-192">**Using .NET and Docker Together - DockerCon 2018 Update** </span></span>\
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="9579a-193">Korzystanie z repozytoriów obrazów wielołukowych</span><span class="sxs-lookup"><span data-stu-id="9579a-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="9579a-194">Pojedyncze reppo może zawierać warianty platformy, takie jak obraz systemu Linux i obraz systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9579a-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="9579a-195">Ta funkcja umożliwia dostawcom takim jak Microsoft (twórcy obrazów bazowych) tworzenie jednego reponu na wiele platform (czyli Linux i Windows).</span><span class="sxs-lookup"><span data-stu-id="9579a-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="9579a-196">Na przykład repozytorium [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) dostępne w rejestrze docker hub zapewnia obsługę systemów Linux i Windows Nano Server przy użyciu tej samej nazwy repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9579a-196">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="9579a-197">Jeśli określisz tag, kierowanie na platformę, która jest jawna, jak w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="9579a-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim` \
  <span data-ttu-id="9579a-198">Obiekty docelowe: tylko w czasie wykonywania programu .NET Core 3.1 w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="9579a-198">Targets: .NET Core 3.1 runtime-only on Linux</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1909` \
  <span data-ttu-id="9579a-199">Obiekty docelowe: tylko środowisko uruchomieniowe programu .NET Core 3.1 w systemie Windows Nano Server</span><span class="sxs-lookup"><span data-stu-id="9579a-199">Targets: .NET Core 3.1 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="9579a-200">Jeśli jednak określisz tę samą nazwę obrazu, nawet w przypadku `aspnet` tego samego tagu, obrazy wielołukowe (takie jak obraz) będą używać wersji systemu Linux lub Windows w zależności od wdrażanego systemu operacyjnego hosta platformy Docker, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9579a-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnet` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1` \
  <span data-ttu-id="9579a-201">Wielołukowy: tylko środowisko uruchomieniowe programu .NET Core 3.1 w systemie Linux lub Windows Nano Server w zależności od systemu operacyjnego hosta platformy Docker</span><span class="sxs-lookup"><span data-stu-id="9579a-201">Multi-arch: .NET Core 3.1 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="9579a-202">W ten sposób, gdy wyciągniesz obraz z hosta systemu Windows, wyciągnie wariant systemu Windows, a pociągnięcie tej samej nazwy obrazu z hosta Linuksa pociągnie wariant Linuksa.</span><span class="sxs-lookup"><span data-stu-id="9579a-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="9579a-203">Kompilacje wieloetapowe w pliku Dockerfile</span><span class="sxs-lookup"><span data-stu-id="9579a-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="9579a-204">Plik Dockerfile jest podobny do skryptu wsadowego.</span><span class="sxs-lookup"><span data-stu-id="9579a-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="9579a-205">Podobnie jak w przypadku konieczności skonfigurowania komputera z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9579a-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="9579a-206">Zaczyna się od obrazu podstawowego, który konfiguruje kontekst początkowy, to jak system plików startowych, który znajduje się na górze systemu operacyjnego hosta.</span><span class="sxs-lookup"><span data-stu-id="9579a-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="9579a-207">To nie jest system operacyjny, ale można myśleć o tym jak "" OS wewnątrz pojemnika.</span><span class="sxs-lookup"><span data-stu-id="9579a-207">It's not an OS, but you can think of it like "the" OS inside the container.</span></span>

<span data-ttu-id="9579a-208">Wykonanie każdego wiersza polecenia tworzy nową warstwę w systemie plików ze zmianami z poprzedniego, tak, że po połączeniu, produkować wynikowy system plików.</span><span class="sxs-lookup"><span data-stu-id="9579a-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="9579a-209">Ponieważ każda nowa warstwa "opiera się" na poprzedniej, a wynikowy rozmiar obrazu zwiększa się z każdym poleceniem, obrazy mogą być bardzo duże, jeśli muszą zawierać, na przykład, zestaw SDK potrzebny do utworzenia i opublikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9579a-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="9579a-210">To jest, gdy wieloetapowe kompilacje dostać się do działki (z Docker 17.05 i wyższe), aby zrobić swoją magię.</span><span class="sxs-lookup"><span data-stu-id="9579a-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="9579a-211">Podstawową ideą jest to, że można oddzielić proces wykonywania dockerfile etapami, gdzie etap jest obrazem początkowym, po którym następuje jedno lub więcej poleceń, a ostatni etap określa ostateczny rozmiar obrazu.</span><span class="sxs-lookup"><span data-stu-id="9579a-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="9579a-212">Krótko mówiąc, kompilacje wieloetapowe umożliwiają dzielenie kreacji w różnych "fazach", a następnie montaż końcowego obrazu, biorąc tylko odpowiednie katalogi z etapów pośrednich.</span><span class="sxs-lookup"><span data-stu-id="9579a-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="9579a-213">Ogólna strategia korzystania z tej funkcji jest:</span><span class="sxs-lookup"><span data-stu-id="9579a-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="9579a-214">Użyj podstawowego obrazu SDK (nie ma znaczenia, jak duży), ze wszystkim, co potrzebne do tworzenia i publikowania aplikacji w folderze, a następnie</span><span class="sxs-lookup"><span data-stu-id="9579a-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="9579a-215">Użyj obrazu podstawowego, małego, tylko do wykonywania i skopiuj folder publikowania z poprzedniego etapu, aby utworzyć mały obraz końcowy.</span><span class="sxs-lookup"><span data-stu-id="9579a-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="9579a-216">Prawdopodobnie najlepszym sposobem, aby zrozumieć wielostopniowy przechodzi przez Dockerfile w szczegółach, wiersz po wierszu, więc zacznijmy od początkowego Dockerfile utworzone przez program Visual Studio podczas dodawania obsługi platformy Docker do projektu i dostanie się do niektórych optymalizacji później.</span><span class="sxs-lookup"><span data-stu-id="9579a-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="9579a-217">Początkowy Plik Dockerfile może wyglądać mniej więcej tak:</span><span class="sxs-lookup"><span data-stu-id="9579a-217">The initial Dockerfile might look something like this:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
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

<span data-ttu-id="9579a-218">I to są szczegóły, wiersz po wierszu:</span><span class="sxs-lookup"><span data-stu-id="9579a-218">And these are the details, line by line:</span></span>

- <span data-ttu-id="9579a-219">**#1 liniowy:** Rozpocznij etap z "małym" obrazem podstawowym tylko w czasie wykonywania, nazwij go **bazą** referencyjną.</span><span class="sxs-lookup"><span data-stu-id="9579a-219">**Line #1:** Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>

- <span data-ttu-id="9579a-220">**#2 liniowy:** Utwórz katalog **/app** na obrazie.</span><span class="sxs-lookup"><span data-stu-id="9579a-220">**Line #2:** Create the **/app** directory in the image.</span></span>

- <span data-ttu-id="9579a-221">**#3 liniowy:** Udostępnij port **80**.</span><span class="sxs-lookup"><span data-stu-id="9579a-221">**Line #3:** Expose port **80**.</span></span>

- <span data-ttu-id="9579a-222">**#5 liniowy:** Rozpocznij nowy etap z "dużym" obrazem do budowania/publikowania.</span><span class="sxs-lookup"><span data-stu-id="9579a-222">**Line #5:** Begin a new stage with the "large" image for building/publishing.</span></span> <span data-ttu-id="9579a-223">Wywołaj **kompilację** w celach informacyjnych.</span><span class="sxs-lookup"><span data-stu-id="9579a-223">Call it **build** for reference.</span></span>

- <span data-ttu-id="9579a-224">**#6 liniowy:** Utwórz katalog **/src** na obrazie.</span><span class="sxs-lookup"><span data-stu-id="9579a-224">**Line #6:** Create directory **/src** in the image.</span></span>

- <span data-ttu-id="9579a-225">**#7 liniowy:** Do linii 16, kopiuj odwołuje się do plików projektu **csproj,** aby móc przywrócić pakiety później.</span><span class="sxs-lookup"><span data-stu-id="9579a-225">**Line #7:** Up to line 16, copy referenced **.csproj** project files to be able to restore packages later.</span></span>

- <span data-ttu-id="9579a-226">**#17 liniowy:** Przywracanie pakietów dla projektu **Catalog.API** i projektów, do których istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="9579a-226">**Line #17:** Restore packages for the **Catalog.API** project and the referenced projects.</span></span>

- <span data-ttu-id="9579a-227">**#18 liniowy:** Skopiuj **całe drzewo katalogów dla rozwiązania** (z wyjątkiem plików/katalogów zawartych w pliku **.dockerignore)** do katalogu **/src** w obrazie.</span><span class="sxs-lookup"><span data-stu-id="9579a-227">**Line #18:** Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) to the **/src** directory in the image.</span></span>

- <span data-ttu-id="9579a-228">**#19 liniowy:** Zmień bieżący folder na projekt **Catalog.API.**</span><span class="sxs-lookup"><span data-stu-id="9579a-228">**Line #19:** Change the current folder to the **Catalog.API** project.</span></span>

- <span data-ttu-id="9579a-229">**#20 liniowy:** Skompiluj projekt (i inne zależności projektu) i dane wyjściowe do katalogu **/app** na obrazie.</span><span class="sxs-lookup"><span data-stu-id="9579a-229">**Line #20:** Build the project (and other project dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="9579a-230">**#22 liniowy:** Rozpocznij nowy etap kontynuując od kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9579a-230">**Line #22:** Begin a new stage continuing from the build.</span></span> <span data-ttu-id="9579a-231">Wywołaj **to opublikować** w celach informacyjnych.</span><span class="sxs-lookup"><span data-stu-id="9579a-231">Call it **publish** for reference.</span></span>

- <span data-ttu-id="9579a-232">**#23 liniowy:** Opublikuj projekt (i zależności) i dane wyjściowe do katalogu **/app** na obrazie.</span><span class="sxs-lookup"><span data-stu-id="9579a-232">**Line #23:** Publish the project (and dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="9579a-233">**#25 linii:** Rozpocznij nowy etap kontynuując od **bazy** i nazwij go **ostatnim**.</span><span class="sxs-lookup"><span data-stu-id="9579a-233">**Line #25:** Begin a new stage continuing from **base** and call it **final**.</span></span>

- <span data-ttu-id="9579a-234">**#26 liniowy:** Zmień bieżący katalog na **/app**.</span><span class="sxs-lookup"><span data-stu-id="9579a-234">**Line #26:** Change the current directory to **/app**.</span></span>

- <span data-ttu-id="9579a-235">**#27 liniowy:** Skopiuj katalog **/app** z etapu **publikowania** do bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="9579a-235">**Line #27:** Copy the **/app** directory from stage **publish** to the current directory.</span></span>

- <span data-ttu-id="9579a-236">**#28 liniowy:** Zdefiniuj polecenie do uruchomienia po uruchomieniu kontenera.</span><span class="sxs-lookup"><span data-stu-id="9579a-236">**Line #28:** Define the command to run when the container is started.</span></span>

<span data-ttu-id="9579a-237">Teraz przeanalizujmy niektóre optymalizacje, aby poprawić wydajność całego procesu, który w przypadku eShopOnContainers oznacza około 22 minut lub więcej, aby utworzyć kompletne rozwiązanie w kontenerach systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="9579a-237">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="9579a-238">Skorzystasz z funkcji pamięci podręcznej warstwy platformy Docker, co jest dość proste: jeśli obraz podstawowy i polecenia są takie same jak niektóre wcześniej wykonane, może po prostu użyć warstwy wynikowej bez konieczności wykonywania poleceń, oszczędzając w ten sposób trochę czasu.</span><span class="sxs-lookup"><span data-stu-id="9579a-238">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="9579a-239">Skupmy się więc na etapie **kompilacji,** linie 5-6 są w większości takie same, ale linie 7-17 są różne dla każdej usługi z eShopOnContainers, więc muszą wykonać za każdym razem, jednak jeśli zmieniłeś linie 7-16 na:</span><span class="sxs-lookup"><span data-stu-id="9579a-239">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```Dockerfile
COPY . .
```

<span data-ttu-id="9579a-240">Wtedy byłoby tak samo dla każdej usługi, to skopiować całe rozwiązanie i stworzyłby większą warstwę, ale:</span><span class="sxs-lookup"><span data-stu-id="9579a-240">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1. <span data-ttu-id="9579a-241">Proces kopiowania zostanie wykonany tylko po raz pierwszy (i podczas przebudowy, jeśli plik zostanie zmieniony) i będzie używać pamięci podręcznej dla wszystkich innych usług i</span><span class="sxs-lookup"><span data-stu-id="9579a-241">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2. <span data-ttu-id="9579a-242">Ponieważ większy obraz występuje na etapie pośrednim, nie ma to wpływu na ostateczny rozmiar obrazu.</span><span class="sxs-lookup"><span data-stu-id="9579a-242">Since the larger image occurs in an intermediate stage it, doesn't affect the final image size.</span></span>

<span data-ttu-id="9579a-243">Następna optymalizacja `restore` znacząca obejmuje polecenie wykonywane w wierszu 17, który jest również inny dla każdej usługi eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="9579a-243">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="9579a-244">Jeśli zmienisz ten wiersz na sprawiedliwy:</span><span class="sxs-lookup"><span data-stu-id="9579a-244">If you change that line to just:</span></span>

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="9579a-245">Przywróciłby pakiety dla całego rozwiązania, ale potem znowu zrobiłby to tylko raz, zamiast 15 razy z obecną strategią.</span><span class="sxs-lookup"><span data-stu-id="9579a-245">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="9579a-246">Jednak `dotnet restore` uruchamia się tylko wtedy, gdy w folderze znajduje się jeden plik projektu lub rozwiązania, więc osiągnięcie tego jest nieco bardziej skomplikowane, a sposób jego rozwiązania, bez wchodzenia w zbyt wiele szczegółów, jest następujące:</span><span class="sxs-lookup"><span data-stu-id="9579a-246">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1. <span data-ttu-id="9579a-247">Dodaj następujące wiersze do **.dockerignore:**</span><span class="sxs-lookup"><span data-stu-id="9579a-247">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="9579a-248">`*.sln`, aby zignorować wszystkie pliki rozwiązania w drzewie folderów głównych</span><span class="sxs-lookup"><span data-stu-id="9579a-248">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="9579a-249">`!eShopOnContainers-ServicesAndWebApps.sln`, aby uwzględnić tylko ten plik rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9579a-249">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2. <span data-ttu-id="9579a-250">Dołącz `/ignoreprojectextensions:.dcproj` argument `dotnet restore`do , więc ignoruje również projekt docker-compose i przywraca tylko pakiety dla rozwiązania eShopOnContainers-ServicesAndWebApps.</span><span class="sxs-lookup"><span data-stu-id="9579a-250">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="9579a-251">Dla ostatecznej optymalizacji, to po prostu zdarza się, że linia 20 jest zbędne, jak linia 23 również buduje aplikację i przychodzi, w istocie, zaraz po wierszu 20, więc nie idzie kolejne czasochłonne polecenie.</span><span class="sxs-lookup"><span data-stu-id="9579a-251">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="9579a-252">Wynikowym plikiem jest wtedy:</span><span class="sxs-lookup"><span data-stu-id="9579a-252">The resulting file is then:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS publish
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

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="9579a-253">Tworzenie obrazu bazowego od podstaw</span><span class="sxs-lookup"><span data-stu-id="9579a-253">Creating your base image from scratch</span></span>

<span data-ttu-id="9579a-254">Można utworzyć własny obraz podstawowy platformy Docker od podstaw.</span><span class="sxs-lookup"><span data-stu-id="9579a-254">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="9579a-255">Ten scenariusz nie jest zalecany dla osoby, która zaczyna się od platformy Docker, ale jeśli chcesz ustawić określone bity własnego obrazu podstawowego, możesz to zrobić.</span><span class="sxs-lookup"><span data-stu-id="9579a-255">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9579a-256">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="9579a-256">Additional resources</span></span>

- <span data-ttu-id="9579a-257">**Wielołukowe obrazy .NET Core**.</span><span class="sxs-lookup"><span data-stu-id="9579a-257">**Multi-arch .NET Core images**.</span></span>\
  <https://github.com/dotnet/announcements/issues/14>

- <span data-ttu-id="9579a-258">**Utwórz obraz podstawowy**.</span><span class="sxs-lookup"><span data-stu-id="9579a-258">**Create a base image**.</span></span> <span data-ttu-id="9579a-259">Oficjalna dokumentacja platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="9579a-259">Official Docker documentation.</span></span>\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![Obraz dla kroku 3.](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="9579a-261">Krok 3.</span><span class="sxs-lookup"><span data-stu-id="9579a-261">Step 3.</span></span> <span data-ttu-id="9579a-262">Tworzenie niestandardowych obrazów platformy Docker i osadzanie w nich aplikacji lub usługi</span><span class="sxs-lookup"><span data-stu-id="9579a-262">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="9579a-263">Dla każdej usługi w aplikacji należy utworzyć powiązany obraz.</span><span class="sxs-lookup"><span data-stu-id="9579a-263">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="9579a-264">Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, wystarczy jeden obraz.</span><span class="sxs-lookup"><span data-stu-id="9579a-264">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="9579a-265">Należy zauważyć, że obrazy platformy Docker są tworzone automatycznie dla Ciebie w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9579a-265">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="9579a-266">Poniższe kroki są potrzebne tylko dla przepływu pracy edytora/interfejsu i wyjaśnione dla jasności co do tego, co dzieje się pod spodem.</span><span class="sxs-lookup"><span data-stu-id="9579a-266">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="9579a-267">Jako deweloper musisz opracowywać i testować lokalnie, dopóki nie wypchniesz ukończonej funkcji lub nie zmienisz systemu kontroli źródła (na przykład na GitHub).</span><span class="sxs-lookup"><span data-stu-id="9579a-267">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="9579a-268">Oznacza to, że należy utworzyć obrazy platformy Docker i wdrożyć kontenery na lokalnym hoście platformy Docker (Windows lub Linux VM) i uruchomić, przetestować i debugować względem tych kontenerów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="9579a-268">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="9579a-269">Aby utworzyć obraz niestandardowy w środowisku lokalnym przy użyciu polecenia docker CLI i pliku Dockerfile, można użyć polecenia kompilacji platformy docker, jak na rysunku 5-5.</span><span class="sxs-lookup"><span data-stu-id="9579a-269">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Zrzut ekranu przedstawiający dane wyjściowe konsoli polecenia kompilacji platformy docker.](./media/docker-app-development-workflow/run-docker-build-command.png)

<span data-ttu-id="9579a-271">**Rysunek 5-5**.</span><span class="sxs-lookup"><span data-stu-id="9579a-271">**Figure 5-5**.</span></span> <span data-ttu-id="9579a-272">Tworzenie niestandardowego obrazu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="9579a-272">Creating a custom Docker image</span></span>

<span data-ttu-id="9579a-273">Opcjonalnie zamiast bezpośrednio uruchamiać kompilację docker z folderu projektu, można najpierw wygenerować folder z możliwością wdrożenia z wymaganymi bibliotekami i plikami binarnymi .NET, uruchamiając , `dotnet publish`a następnie użyć `docker build` polecenia.</span><span class="sxs-lookup"><span data-stu-id="9579a-273">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="9579a-274">Spowoduje to utworzenie obrazu platformy `cesardl/netcore-webapi-microservice-docker:first`Docker o nazwie .</span><span class="sxs-lookup"><span data-stu-id="9579a-274">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="9579a-275">W takim przypadku :first jest tagreprezentujący określoną wersję.</span><span class="sxs-lookup"><span data-stu-id="9579a-275">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="9579a-276">Ten krok można powtórzyć dla każdego niestandardowego obrazu, który należy utworzyć dla skomponowanej aplikacji platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="9579a-276">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="9579a-277">Gdy aplikacja jest wykonana z wielu kontenerów (oznacza to, że jest `docker-compose up --build` aplikacją wielokontenerową), można również użyć polecenia do tworzenia wszystkich powiązanych obrazów za pomocą jednego polecenia przy użyciu metadanych uwidacznianych w powiązanych plikach docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="9579a-277">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="9579a-278">Istniejące obrazy można znaleźć w lokalnym repozytorium za pomocą polecenia obrazy dokowane, jak pokazano na rysunku 5-6.</span><span class="sxs-lookup"><span data-stu-id="9579a-278">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Wyjście konsoli z obrazów dokatki poleceń, pokazujące istniejące obrazy.](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="9579a-280">**Rysunek 5-6.**</span><span class="sxs-lookup"><span data-stu-id="9579a-280">**Figure 5-6.**</span></span> <span data-ttu-id="9579a-281">Wyświetlanie istniejących obrazów za pomocą polecenia Obrazy dokowane</span><span class="sxs-lookup"><span data-stu-id="9579a-281">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="9579a-282">Tworzenie obrazów platformy Docker za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9579a-282">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="9579a-283">Korzystając z programu Visual Studio do tworzenia projektu z obsługą platformy Docker, nie jawnie utworzyć obraz.</span><span class="sxs-lookup"><span data-stu-id="9579a-283">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="9579a-284">Zamiast tego obraz jest tworzony po naciśnięciu **klawisza F5** (lub **Ctrl-F5),** aby uruchomić dockerized aplikacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="9579a-284">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="9579a-285">Ten krok jest automatyczny w programie Visual Studio i nie zobaczysz, że tak się stanie, ale ważne jest, aby wiedzieć, co się dzieje pod spodem.</span><span class="sxs-lookup"><span data-stu-id="9579a-285">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![Obraz dla opcjonalnego kroku 4.](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="9579a-287">Krok 4.</span><span class="sxs-lookup"><span data-stu-id="9579a-287">Step 4.</span></span> <span data-ttu-id="9579a-288">Definiowanie usług w pliku docker-compose.yml podczas tworzenia aplikacji platformy Docker dla wielu kontenerów</span><span class="sxs-lookup"><span data-stu-id="9579a-288">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="9579a-289">Plik [docker-compose.yml](https://docs.docker.com/compose/compose-file/) umożliwia zdefiniowanie zestawu powiązanych usług, które mają zostać wdrożone jako skomponowana aplikacja z poleceniami wdrażania.</span><span class="sxs-lookup"><span data-stu-id="9579a-289">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="9579a-290">Konfiguruje również relacje zależności i konfigurację w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9579a-290">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="9579a-291">Aby użyć pliku docker-compose.yml, należy utworzyć plik w głównym lub głównym folderze rozwiązania, z zawartością podobną do tej w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9579a-291">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
    ports:
      - "80:80"
    depends_on:
      - catalog-api
      - ordering-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sqldata

  sqldata:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

<span data-ttu-id="9579a-292">Ten plik docker-compose.yml jest wersją uproszczoną i scaloną.</span><span class="sxs-lookup"><span data-stu-id="9579a-292">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="9579a-293">Zawiera statyczne dane konfiguracyjne dla każdego kontenera (takie jak nazwa obrazu niestandardowego), który jest zawsze wymagany, oraz informacje o konfiguracji, które mogą zależeć od środowiska wdrażania, takie jak parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="9579a-293">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="9579a-294">W kolejnych sekcjach dowiesz się, jak podzielić konfigurację docker-compose.yml na wiele plików docker-compose i zastąpić wartości w zależności od środowiska i typu wykonywania (debugowania lub wydania).</span><span class="sxs-lookup"><span data-stu-id="9579a-294">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="9579a-295">Przykład pliku docker-compose.yml definiuje cztery `webmvc` usługi: usługę (aplikację sieci`ordering-api` web), dwie mikrousługi ( i `basket-api`) i jeden kontener źródła danych, `sqldata`oparty na programie SQL Server dla systemu Linux uruchomionym jako kontener.</span><span class="sxs-lookup"><span data-stu-id="9579a-295">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering-api` and `basket-api`), and one data source container, `sqldata`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="9579a-296">Każda usługa zostanie wdrożona jako kontener, więc obraz platformy Docker jest wymagany dla każdego.</span><span class="sxs-lookup"><span data-stu-id="9579a-296">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="9579a-297">Plik docker-compose.yml określa nie tylko, jakie kontenery są używane, ale sposób ich indywidualnej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9579a-297">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="9579a-298">Na przykład `webmvc` definicja kontenera w pliku yml:</span><span class="sxs-lookup"><span data-stu-id="9579a-298">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="9579a-299">Używa wstępnie utworzonego `eshop/web:latest` obrazu.</span><span class="sxs-lookup"><span data-stu-id="9579a-299">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="9579a-300">Można jednak również skonfigurować obraz, który ma być zbudowany jako część wykonywania docker-compose z dodatkową konfiguracją opartą na kompilacji: sekcja w pliku docker-compose.</span><span class="sxs-lookup"><span data-stu-id="9579a-300">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="9579a-301">Inicjuje dwie zmienne środowiskowe (CatalogUrl i OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="9579a-301">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="9579a-302">Przesyła dalej odsłonięty port 80 na kontenerze do portu zewnętrznego 80 na komputerze hosta.</span><span class="sxs-lookup"><span data-stu-id="9579a-302">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="9579a-303">Łączy aplikację internetową z usługą katalogową i zamawiania z ustawieniem depends_on.</span><span class="sxs-lookup"><span data-stu-id="9579a-303">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="9579a-304">Powoduje to, że usługa czekać, aż te usługi są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="9579a-304">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="9579a-305">Będziemy ponownie plik docker-compose.yml w dalszej sekcji, gdy omówimy sposób implementowania mikrousług i aplikacji wielokontenerowych.</span><span class="sxs-lookup"><span data-stu-id="9579a-305">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2019"></a><span data-ttu-id="9579a-306">Praca z docker-compose.yml w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="9579a-306">Working with docker-compose.yml in Visual Studio 2019</span></span>

<span data-ttu-id="9579a-307">Oprócz dodawania pliku Dockerfile do projektu, jak wspomnieliśmy wcześniej, Visual Studio 2017 (od wersji 15.8 na) można dodać obsługę koordynatora docker Compose do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9579a-307">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from version 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="9579a-308">Po dodaniu obsługi koordynatora kontenerów, jak pokazano na rysunku 5-7, po raz pierwszy program Visual Studio tworzy plik Dockerfile `docker-compose*.yml` dla projektu i tworzy nowy (sekcja usługi) projektu w rozwiązaniu z kilku plików globalnych, a następnie dodaje projekt do tych plików.</span><span class="sxs-lookup"><span data-stu-id="9579a-308">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="9579a-309">Następnie można otworzyć pliki docker-compose.yml i zaktualizować je za pomocą dodatkowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="9579a-309">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="9579a-310">Musisz powtórzyć ten formularz operacji każdego projektu, który chcesz uwzględnić w pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="9579a-310">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="9579a-311">W czasie tego pisania visual studio obsługuje **Docker Compose** i **Kubernetes/Helm** koordynatorów.</span><span class="sxs-lookup"><span data-stu-id="9579a-311">At the time of this writing, Visual Studio supports **Docker Compose** and **Kubernetes/Helm** orchestrators.</span></span>

![Zrzut ekranu przedstawiający opcję Obsługa koordynatora kontenerów w menu kontekstowym projektu.](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

<span data-ttu-id="9579a-313">**Rysunek 5-7**.</span><span class="sxs-lookup"><span data-stu-id="9579a-313">**Figure 5-7**.</span></span> <span data-ttu-id="9579a-314">Dodawanie obsługi platformy Docker w programie Visual Studio 2019 przez kliknięcie prawym przyciskiem myszy projektu ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9579a-314">Adding Docker support in Visual Studio 2019 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="9579a-315">Po dodaniu obsługi koordynatora do rozwiązania w programie Visual Studio zostanie wyświetlony `docker-compose.dcproj` nowy węzeł (w pliku projektu) w Eksploratorze rozwiązań zawierający dodane pliki docker-compose.yml, jak pokazano na rysunku 5-8.</span><span class="sxs-lookup"><span data-stu-id="9579a-315">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![Zrzut ekranu przedstawiający węzeł docker-compose w Eksploratorze rozwiązań.](./media/docker-app-development-workflow/docker-compose-tree-node.png)

<span data-ttu-id="9579a-317">**Rysunek 5-8**.</span><span class="sxs-lookup"><span data-stu-id="9579a-317">**Figure 5-8**.</span></span> <span data-ttu-id="9579a-318">Węzeł drzewa **docker-compose** dodany w Eksploratorze rozwiązań programu Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="9579a-318">The **docker-compose** tree node added in Visual Studio 2019 Solution Explorer</span></span>

<span data-ttu-id="9579a-319">Można wdrożyć aplikację wielokontenerową z pojedynczym plikiem docker-compose.yml za pomocą `docker-compose up` polecenia.</span><span class="sxs-lookup"><span data-stu-id="9579a-319">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="9579a-320">Program Visual Studio dodaje jednak grupę z nich, dzięki czemu można zastąpić wartości w zależności od środowiska (rozwoju lub produkcji) i typu wykonywania (wydania lub debugowania).</span><span class="sxs-lookup"><span data-stu-id="9579a-320">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="9579a-321">Ta funkcja zostanie wyjaśniona w kolejnych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="9579a-321">This capability will be explained in later sections.</span></span>

![Obraz dla kroku 5.](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="9579a-323">Krok 5.</span><span class="sxs-lookup"><span data-stu-id="9579a-323">Step 5.</span></span> <span data-ttu-id="9579a-324">Tworzenie i uruchamianie aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="9579a-324">Build and run your Docker application</span></span>

<span data-ttu-id="9579a-325">Jeśli aplikacja ma tylko jeden kontener, można go uruchomić, wdrażając go na hoście platformy Docker (maszyna wirtualna lub serwer fizyczny).</span><span class="sxs-lookup"><span data-stu-id="9579a-325">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="9579a-326">Jeśli jednak aplikacja zawiera wiele usług, można ją wdrożyć jako złożoną aplikację, używając jednego polecenia wiersza polecenia (lub`docker-compose up)`programu Visual Studio, które użyje tego polecenia pod osłonami.</span><span class="sxs-lookup"><span data-stu-id="9579a-326">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (`docker-compose up)`, or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="9579a-327">Spójrzmy na różne opcje.</span><span class="sxs-lookup"><span data-stu-id="9579a-327">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="9579a-328">Opcja A: Uruchamianie aplikacji z jednym kontenerem</span><span class="sxs-lookup"><span data-stu-id="9579a-328">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="9579a-329">Korzystanie z funkcji CLI platformy Docker</span><span class="sxs-lookup"><span data-stu-id="9579a-329">Using Docker CLI</span></span>

<span data-ttu-id="9579a-330">Kontener platformy Docker można `docker run` uruchomić za pomocą polecenia, jak pokazano na rysunku 5-9:</span><span class="sxs-lookup"><span data-stu-id="9579a-330">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="9579a-331">Powyższe polecenie utworzy nowe wystąpienie kontenera z określonego obrazu, za każdym razem, gdy jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="9579a-331">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="9579a-332">Parametr służy `--name` do nadania nazwy kontenerowi, `docker start {name}` a następnie użyć (lub użyć identyfikatora kontenera lub nazwy automatycznej) do uruchomienia istniejącego wystąpienia kontenera.</span><span class="sxs-lookup"><span data-stu-id="9579a-332">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container ID or automatic name) to run an existing container instance.</span></span>

![Zrzut ekranu przedstawiający kontener platformy Docker przy użyciu polecenia docker run.](./media/docker-app-development-workflow/use-docker-run-command.png)

<span data-ttu-id="9579a-334">**Rysunek 5-9**.</span><span class="sxs-lookup"><span data-stu-id="9579a-334">**Figure 5-9**.</span></span> <span data-ttu-id="9579a-335">Uruchamianie kontenera platformy Docker przy użyciu polecenia uruchamiania platformy dokowane</span><span class="sxs-lookup"><span data-stu-id="9579a-335">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="9579a-336">W takim przypadku polecenie wiąże port wewnętrzny 5000 kontenera do portu 80 komputera hosta.</span><span class="sxs-lookup"><span data-stu-id="9579a-336">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="9579a-337">Oznacza to, że host nasłuchuje na porcie 80 i przekazuje do portu 5000 w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="9579a-337">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="9579a-338">Wyświetlany skrót jest identyfikatorem kontenera i jest również przypisany losową czytelną nazwę, `--name` jeśli opcja nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="9579a-338">The hash shown is the container ID and it’s also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="9579a-339">Korzystanie z programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9579a-339">Using Visual Studio</span></span>

<span data-ttu-id="9579a-340">Jeśli nie dodano obsługę koordynatora kontenerów, można również uruchomić aplikację pojedynczego kontenera w programie Visual Studio, naciskając **klawisze Ctrl-F5** i można również użyć **f5** do debugowania aplikacji w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="9579a-340">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="9579a-341">Kontener jest uruchamiany lokalnie przy użyciu platformy docker run.</span><span class="sxs-lookup"><span data-stu-id="9579a-341">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="9579a-342">Opcja B: Uruchamianie aplikacji wielokontenerowej</span><span class="sxs-lookup"><span data-stu-id="9579a-342">Option B: Running a multi-container application</span></span>

<span data-ttu-id="9579a-343">W większości scenariuszy przedsiębiorstwa aplikacja platformy Docker będzie składać się z wielu usług, co oznacza, że należy uruchomić aplikację wielokontenerową, jak pokazano na rysunku 5-10.</span><span class="sxs-lookup"><span data-stu-id="9579a-343">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![Maszyna wirtualna z kilkoma kontenerami platformy Docker](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="9579a-345">**Rysunek 5-10**.</span><span class="sxs-lookup"><span data-stu-id="9579a-345">**Figure 5-10**.</span></span> <span data-ttu-id="9579a-346">Maszyna wirtualna z wdrożonymi kontenerami platformy Docker</span><span class="sxs-lookup"><span data-stu-id="9579a-346">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="9579a-347">Korzystanie z funkcji CLI platformy Docker</span><span class="sxs-lookup"><span data-stu-id="9579a-347">Using Docker CLI</span></span>

<span data-ttu-id="9579a-348">Aby uruchomić aplikację wielokontenerową za pomocą polecenia CLI platformy Docker, należy użyć tego `docker-compose up` polecenia.</span><span class="sxs-lookup"><span data-stu-id="9579a-348">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="9579a-349">To polecenie używa pliku **docker-compose.yml,** który masz na poziomie rozwiązania do wdrażania aplikacji wielokontenerowej.</span><span class="sxs-lookup"><span data-stu-id="9579a-349">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="9579a-350">Rysunek 5-11 przedstawia wyniki po uruchomieniu polecenia z katalogu głównego rozwiązania, który zawiera plik docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="9579a-350">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Widok ekranu podczas uruchamiania polecenia docker-compose up](./media/docker-app-development-workflow/results-docker-compose-up.png)

<span data-ttu-id="9579a-352">**Rysunek 5-11**.</span><span class="sxs-lookup"><span data-stu-id="9579a-352">**Figure 5-11**.</span></span> <span data-ttu-id="9579a-353">Przykładowe wyniki podczas uruchamiania polecenia docker-compose up</span><span class="sxs-lookup"><span data-stu-id="9579a-353">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="9579a-354">Po uruchomieniu polecenia docker-compose się, aplikacja i powiązane kontenery są wdrażane na hoście platformy Docker, jak przedstawiono na rysunku 5-10.</span><span class="sxs-lookup"><span data-stu-id="9579a-354">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="9579a-355">Korzystanie z programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9579a-355">Using Visual Studio</span></span>

<span data-ttu-id="9579a-356">Uruchomienie aplikacji wielokontenerowej przy użyciu programu Visual Studio 2019 nie może uzyskać żadnych prostsze.</span><span class="sxs-lookup"><span data-stu-id="9579a-356">Running a multi-container application using Visual Studio 2019 can't get any simpler.</span></span> <span data-ttu-id="9579a-357">Wystarczy nacisnąć **klawiszctrl-F5,** aby uruchomić lub **F5** do debugowania, jak zwykle, konfigurowanie projektu **docker-compose** jako projekt uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="9579a-357">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="9579a-358">Visual Studio obsługuje wszystkie potrzebne ustawienia, dzięki czemu można tworzyć punkty przerwania, jak zwykle i debugować, co w końcu stają się niezależne procesy uruchomione w "serwery zdalne", z debugera już dołączone.</span><span class="sxs-lookup"><span data-stu-id="9579a-358">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", with the debugger already attached.</span></span> <span data-ttu-id="9579a-359">właśnie w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="9579a-359">just like that.</span></span>

<span data-ttu-id="9579a-360">Jak wspomniano wcześniej, za każdym razem, gdy dodajesz obsługę rozwiązania platformy Docker do projektu w ramach rozwiązania, ten projekt jest skonfigurowany w pliku docker-compose.yml na poziomie globalnym (na poziomie rozwiązania), który umożliwia jednoczesne uruchamianie lub debugowanie całego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9579a-360">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="9579a-361">Program Visual Studio uruchomi jeden kontener dla każdego projektu, który ma włączoną obsługę rozwiązania platformy Docker i wykonaj wszystkie wewnętrzne kroki (dotnet publish, docker build itp.).</span><span class="sxs-lookup"><span data-stu-id="9579a-361">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="9579a-362">Jeśli chcesz rzucić okiem na wszystkie znoju, spojrzeć na plik:</span><span class="sxs-lookup"><span data-stu-id="9579a-362">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="9579a-363">Ważną kwestią jest to, że, jak pokazano na rysunku 5-12, w programie Visual Studio 2019 istnieje dodatkowe polecenie **platformy Docker** dla akcji klawisza F5.</span><span class="sxs-lookup"><span data-stu-id="9579a-363">The important point here is that, as shown in Figure 5-12, in Visual Studio 2019 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="9579a-364">Ta opcja umożliwia uruchamianie lub debugowanie aplikacji wielokontenerowej przez uruchomienie wszystkich kontenerów zdefiniowanych w plikach docker-compose.yml na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9579a-364">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="9579a-365">Możliwość debugowania rozwiązań z wieloma kontenerami oznacza, że można ustawić kilka punktów przerwania, każdy punkt przerwania w innym projekcie (kontenerze), a podczas debugowania z programu Visual Studio zatrzymasz się w punktach przerwania zdefiniowanych w różnych projektach i uruchomionyna różnych pojemników.</span><span class="sxs-lookup"><span data-stu-id="9579a-365">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Zrzut ekranu przedstawiający pasek narzędzi debugowania z projektem docker-compose.](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

<span data-ttu-id="9579a-367">**Rysunek 5-12**.</span><span class="sxs-lookup"><span data-stu-id="9579a-367">**Figure 5-12**.</span></span> <span data-ttu-id="9579a-368">Uruchamianie aplikacji wielokontenerowych w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="9579a-368">Running multi-container apps in Visual Studio 2019</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9579a-369">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="9579a-369">Additional resources</span></span>

- <span data-ttu-id="9579a-370">**Wdrażanie kontenera ASP.NET na zdalnym hoście platformy Docker** </span><span class="sxs-lookup"><span data-stu-id="9579a-370">**Deploy an ASP.NET container to a remote Docker host** </span></span>\
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="9579a-371">Uwaga dotycząca testowania i wdrażania z koordynatorami</span><span class="sxs-lookup"><span data-stu-id="9579a-371">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="9579a-372">Polecenia docker-compose up i docker run (lub uruchamianie i debugowanie kontenerów w programie Visual Studio) są odpowiednie do testowania kontenerów w środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="9579a-372">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="9579a-373">Nie należy jednak używać tego podejścia do wdrożeń produkcyjnych, gdzie należy kierować koordynatorów, takich jak [Kubernetes](https://kubernetes.io/) lub [sieci szkieletowej usług](https://azure.microsoft.com/services/service-fabric/).</span><span class="sxs-lookup"><span data-stu-id="9579a-373">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="9579a-374">Jeśli używasz Kubernetes, musisz użyć [zasobników](https://kubernetes.io/docs/concepts/workloads/pods/pod/) do organizowania kontenerów i [usług](https://kubernetes.io/docs/concepts/services-networking/service/) do ich sieci.</span><span class="sxs-lookup"><span data-stu-id="9579a-374">If you're using Kubernetes, you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="9579a-375">[Wdrożenia](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) można również użyć do organizowania tworzenia zasobników i modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="9579a-375">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![Obraz dla kroku 6.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="9579a-377">Krok 6.</span><span class="sxs-lookup"><span data-stu-id="9579a-377">Step 6.</span></span> <span data-ttu-id="9579a-378">Testowanie aplikacji platformy Docker przy użyciu lokalnego hosta platformy Docker</span><span class="sxs-lookup"><span data-stu-id="9579a-378">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="9579a-379">Ten krok będzie się różnić w zależności od tego, co aplikacja robi.</span><span class="sxs-lookup"><span data-stu-id="9579a-379">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="9579a-380">W prostej aplikacji sieci Web .NET Core, która jest wdrażana jako pojedynczy kontener lub usługa, można uzyskać dostęp do usługi, otwierając przeglądarkę na hoście platformy Docker i przechodząc do tej witryny, jak pokazano na rysunku 5-13.</span><span class="sxs-lookup"><span data-stu-id="9579a-380">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="9579a-381">(Jeśli konfiguracja w pliku Dockerfile mapuje kontener na port na hoście, który jest inny niż 80, dołącz port hosta w adresie URL).</span><span class="sxs-lookup"><span data-stu-id="9579a-381">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Zrzut ekranu przedstawiający odpowiedź z localhost/API/values.](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="9579a-383">**Rysunek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="9579a-383">**Figure 5-13**.</span></span> <span data-ttu-id="9579a-384">Przykład testowania aplikacji platformy Docker lokalnie przy użyciu localhost</span><span class="sxs-lookup"><span data-stu-id="9579a-384">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="9579a-385">Jeśli host lokalny nie wskazuje adresu IP hosta platformy Docker (domyślnie podczas korzystania z platformy Docker CE), aby przejść do usługi, użyj adresu IP karty sieciowej komputera.</span><span class="sxs-lookup"><span data-stu-id="9579a-385">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="9579a-386">Należy zauważyć, że ten adres URL w przeglądarce używa portu 80 dla danego przykładu kontenera, o których mówi się.</span><span class="sxs-lookup"><span data-stu-id="9579a-386">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="9579a-387">Jednak wewnętrznie żądania są przekierowywane do portu 5000, ponieważ w ten sposób został wdrożony za pomocą polecenia docker run, jak wyjaśniono w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="9579a-387">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="9579a-388">Można również przetestować aplikację za pomocą curl z zacisku, jak pokazano na rysunku 5-14.</span><span class="sxs-lookup"><span data-stu-id="9579a-388">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="9579a-389">W instalacji platformy Docker w systemie Windows domyślny adres IP hosta platformy Docker jest zawsze 10.0.75.1 oprócz rzeczywistego adresu IP komputera.</span><span class="sxs-lookup"><span data-stu-id="9579a-389">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Wyjście konsoli z http://10.0.75.1/API/values coraz z curl.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="9579a-391">**Rysunek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="9579a-391">**Figure 5-14**.</span></span> <span data-ttu-id="9579a-392">Przykład testowania aplikacji Platformy Docker lokalnie za pomocą curl</span><span class="sxs-lookup"><span data-stu-id="9579a-392">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2019"></a><span data-ttu-id="9579a-393">Testowanie i debugowanie kontenerów w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="9579a-393">Testing and debugging containers with Visual Studio 2019</span></span>

<span data-ttu-id="9579a-394">Podczas uruchamiania i debugowania kontenerów za pomocą programu Visual Studio 2019 można debugować aplikację .NET w taki sam sposób, jak podczas uruchamiania bez kontenerów.</span><span class="sxs-lookup"><span data-stu-id="9579a-394">When running and debugging the containers with Visual Studio 2019, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="9579a-395">Testowanie i debugowanie bez programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9579a-395">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="9579a-396">Jeśli tworzysz przy użyciu podejścia editor/CLI, debugowanie kontenerów jest trudniejsze i prawdopodobnie będziesz chciał debugować, generując ślady.</span><span class="sxs-lookup"><span data-stu-id="9579a-396">If you're developing using the editor/CLI approach, debugging containers is more difficult and you'll probably want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9579a-397">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="9579a-397">Additional resources</span></span>

- <span data-ttu-id="9579a-398">**Debugowanie aplikacji w lokalnym kontenerze platformy Docker** </span><span class="sxs-lookup"><span data-stu-id="9579a-398">**Debugging apps in a local Docker container** </span></span>\
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- <span data-ttu-id="9579a-399">**Steve Lasker. Tworzenie, debugowanie, wdrażanie ASP.NET podstawowych aplikacji za pomocą platformy Docker.**</span><span class="sxs-lookup"><span data-stu-id="9579a-399">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="9579a-400">Wideo.</span><span class="sxs-lookup"><span data-stu-id="9579a-400">Video.</span></span> \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="9579a-401">Uproszczony przepływ pracy podczas opracowywania kontenerów za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9579a-401">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="9579a-402">Skutecznie przepływu pracy podczas korzystania z programu Visual Studio jest o wiele prostsze niż w przypadku korzystania z podejścia edytora/interfejsu i biorącego pod niego.</span><span class="sxs-lookup"><span data-stu-id="9579a-402">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="9579a-403">Większość kroków wymaganych przez platformę Docker związane z plikidockerfile i docker-compose.yml są ukryte lub uproszczone przez Visual Studio, jak pokazano na rysunku 5-15.</span><span class="sxs-lookup"><span data-stu-id="9579a-403">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram przedstawiający pięć uproszczonych kroków potrzebnych do utworzenia aplikacji.":::
<span data-ttu-id="9579a-405">Proces tworzenia aplikacji platformy Docker: 1 - Kod aplikacji, 2 - Pisanie dockerfile/s, 3 - Tworzenie obrazów zdefiniowanych w dockerfile/s, 4 - (opcjonalnie) Compose usługi w pliku docker-compose.yml, 5 - Uruchom kontener lub docker-compose aplikacji, 6 - Testowanie aplikacji lub mikrousług, 7 - Push to repo i powtórz.</span><span class="sxs-lookup"><span data-stu-id="9579a-405">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="9579a-406">**Rysunek 5-15**.</span><span class="sxs-lookup"><span data-stu-id="9579a-406">**Figure 5-15**.</span></span> <span data-ttu-id="9579a-407">Uproszczony przepływ pracy podczas tworzenia za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9579a-407">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="9579a-408">Ponadto należy wykonać krok 2 (dodawanie obsługi platformy Docker do projektów) tylko raz.</span><span class="sxs-lookup"><span data-stu-id="9579a-408">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="9579a-409">W związku z tym przepływ pracy jest podobny do zwykłych zadań programistycznych podczas korzystania z .NET dla innych deweloperów.</span><span class="sxs-lookup"><span data-stu-id="9579a-409">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="9579a-410">Musisz wiedzieć, co dzieje się pod okładkami (proces kompilacji obrazu, jakie obrazy podstawowe używasz, wdrażanie kontenerów, itp.), a czasami trzeba będzie również edytować Plik Dockerfile lub docker-compose.yml, aby dostosować zachowania.</span><span class="sxs-lookup"><span data-stu-id="9579a-410">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="9579a-411">Jednak większość pracy jest znacznie uproszczona za pomocą programu Visual Studio, dzięki czemu można o wiele bardziej produktywne.</span><span class="sxs-lookup"><span data-stu-id="9579a-411">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9579a-412">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="9579a-412">Additional resources</span></span>

- <span data-ttu-id="9579a-413">**Steve Lasker. Program .NET Docker Development z visual studio (2017)** </span><span class="sxs-lookup"><span data-stu-id="9579a-413">**Steve Lasker. .NET Docker Development with Visual Studio (2017)** </span></span>\
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="9579a-414">Konfigurowanie kontenerów systemu Windows za pomocą poleceń programu PowerShell w pliku Dockerfile</span><span class="sxs-lookup"><span data-stu-id="9579a-414">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="9579a-415">[Kontenery systemu Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) umożliwiają konwertowanie istniejących aplikacji systemu Windows na obrazy platformy Docker i wdrażanie ich przy tym i w tych samych narzędziach, co pozostałe urządzenia do każdowe.</span><span class="sxs-lookup"><span data-stu-id="9579a-415">[Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="9579a-416">Aby korzystać z kontenerów systemu Windows, w pliku Dockerfile są uruchamiane polecenia programu PowerShell, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9579a-416">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM mcr.microsoft.com/windows/servercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="9579a-417">W takim przypadku używamy obrazu podstawowego windows server core (ustawienia FROM) i instalowania usług IIS za pomocą polecenia PowerShell (ustawienie RUN).</span><span class="sxs-lookup"><span data-stu-id="9579a-417">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="9579a-418">W podobny sposób można również użyć poleceń programu PowerShell do skonfigurowania dodatkowych składników, takich jak ASP.NET 4.x, .NET 4.6 lub innego oprogramowania windows.</span><span class="sxs-lookup"><span data-stu-id="9579a-418">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="9579a-419">Na przykład następujące polecenie w pliku Dockerfile konfiguruje ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="9579a-419">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="9579a-420">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="9579a-420">Additional resources</span></span>

- <span data-ttu-id="9579a-421">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="9579a-421">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="9579a-422">Przykładowe polecenia programu PowerShell do uruchamiania z plików dokparatorów w celu uwzględnienia funkcji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9579a-422">Example PowerShell commands to run from dockerfiles to include Windows features.</span></span>\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
><span data-ttu-id="9579a-423">[Poprzedni](index.md)
>[następny](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="9579a-423">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
