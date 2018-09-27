---
title: Visual Studio Tools for Docker na Windows
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: cd140c12ef4a0187cce096e013937d5c98cd4b39
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235718"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a><span data-ttu-id="b44d0-103">Za pomocą narzędzi Visual Studio Tools for Docker (Visual Studio Windows)</span><span class="sxs-lookup"><span data-stu-id="b44d0-103">Using Visual Studio Tools for Docker (Visual Studio on Windows)</span></span>

<span data-ttu-id="b44d0-104">Visual Studio Tools dla przepływu pracy dla deweloperów platformy Docker jest podobny do przy użyciu programu Visual Studio Code i interfejsu wiersza polecenia Docker (opiera się na tym samym interfejsu wiersza polecenia platformy Docker).</span><span class="sxs-lookup"><span data-stu-id="b44d0-104">The Visual Studio Tools for Docker developer workflow is similar to using Visual Studio Code and Docker CLI (it is based on the same Docker CLI).</span></span> <span data-ttu-id="b44d0-105">Program Visual Studio Tools dla platformy Docker sprawia, że jeszcze łatwiej rozpocząć pracę, upraszcza i zapewnia większą produktywność dla kompilacji, uruchamianie i redagowania zadań.</span><span class="sxs-lookup"><span data-stu-id="b44d0-105">Visual Studio Tools for Docker makes it even easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="b44d0-106">Wykonywanie i Debuguj swoje kontenery za pomocą prostego akcji, takich jak **F5** i **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="b44d0-106">Execute and debug your containers via simple actions like **F5** and **Ctrl**+**F5**.</span></span>

> [!NOTE]
> <span data-ttu-id="b44d0-107">Ten artykuł dotyczy programu Visual Studio w Windows, a nie programu Visual Studio dla komputerów Mac.</span><span class="sxs-lookup"><span data-stu-id="b44d0-107">This article applies to Visual Studio on Windows, and not Visual Studio for Mac.</span></span>

## <a name="configure-your-local-environment"></a><span data-ttu-id="b44d0-108">Konfigurowanie środowiska lokalnego</span><span class="sxs-lookup"><span data-stu-id="b44d0-108">Configure your local environment</span></span>

<span data-ttu-id="b44d0-109">Najnowsze wersje platformy Docker for Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), proste Instalatora ułatwia tworzenie aplikacji platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="b44d0-109">With the latest versions of Docker for Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), the straightforward setup makes it easy to develop Docker applications.</span></span>

<span data-ttu-id="b44d0-110">Obsługę platformy docker znajduje się w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b44d0-110">Docker support is included in Visual Studio 2017.</span></span> <span data-ttu-id="b44d0-111">Pobierz program Visual Studio 2017 w tym miejscu: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="b44d0-111">Download Visual Studio 2017 here: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span></span>

## <a name="use-docker-tools-in-visual-studio-2017"></a><span data-ttu-id="b44d0-112">Korzystanie z narzędzi platformy Docker w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b44d0-112">Use Docker Tools in Visual Studio 2017</span></span>

<span data-ttu-id="b44d0-113">Istnieją dwa poziomy obsługę platformy Docker, które można dodać do projektu.</span><span class="sxs-lookup"><span data-stu-id="b44d0-113">There are two levels of Docker support you can add to a project.</span></span> <span data-ttu-id="b44d0-114">W projektach aplikacji sieci web platformy .NET Core, można po prostu dodać *pliku Dockerfile* pliku do projektu, należy włączyć obsługę platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="b44d0-114">In .NET Core web app projects, you can just add a *Dockerfile* file to the project by enabling Docker support.</span></span> <span data-ttu-id="b44d0-115">Następny poziom to obsługi orkiestratora kontenerów, który dodaje *pliku Dockerfile* do projektu (jeśli jeszcze nie istnieje) i *docker-compose.yml* pliku na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b44d0-115">The next level is container orchestrator support, which adds a *Dockerfile* to the project (if it doesn't already exist) and a *docker-compose.yml* file at the solution level.</span></span>

<span data-ttu-id="b44d0-116">**Dodaj** > **obsługę platformy Docker** i **Dodaj** > **obsługi Orkiestratora kontenerów** polecenia są znajduje się w menu kliknij prawym przyciskiem myszy (lub menu kontekstowego) węzeł projektu dla projektu aplikacji sieci web w **Eksploratora rozwiązań**, jak pokazano w rysunek 4-26:</span><span class="sxs-lookup"><span data-stu-id="b44d0-116">The **Add** > **Docker Support** and **Add** > **Container Orchestrator Support** commands are located on the right-click menu (or context menu) of the project node for a web app project in **Solution Explorer**, as shown in Figure 4-26:</span></span>

![Dodaj opcję menu obsługę platformy Docker w programie Visual Studio](media/add-docker-support-menu.png)

<span data-ttu-id="b44d0-118">Rysunek 4-26: Dodawanie obsługi programu Docker do projektu programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b44d0-118">Figure 4-26: Adding Docker support to a Visual Studio 2017 project</span></span>

### <a name="add-docker-support"></a><span data-ttu-id="b44d0-119">Dodaj obsługę platformy Docker</span><span class="sxs-lookup"><span data-stu-id="b44d0-119">Add Docker support</span></span>

<span data-ttu-id="b44d0-120">Obsługę platformy Docker można dodać do istniejącego projektu aplikacji sieci web platformy .NET Core, wybierając **Dodaj** > **obsługę platformy Docker** w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="b44d0-120">You can add Docker support to an existing .NET Core web app project by selecting **Add** > **Docker Support** in **Solution Explorer**.</span></span> <span data-ttu-id="b44d0-121">Można również włączyć obsługę platformy Docker podczas tworzenia projektu, wybierając **włączyć obsługę platformy Docker** w **Nowa aplikacja internetowa ASP.NET Core** okno dialogowe, które jest otwierane po kliknięciu **OK** w **nowy projekt** okno dialogowe, jak pokazano w rysunek 4-27.</span><span class="sxs-lookup"><span data-stu-id="b44d0-121">You can also enable Docker support during project creation by selecting **Enable Docker Support** in the **New ASP.NET Core Web Application** dialog box that opens after you click **OK** in the **New Project** dialog box, as shown in Figure 4-27.</span></span>

![Włącz obsługę platformy Docker dla nowej aplikacji sieci web platformy ASP.NET Core w programie Visual Studio](./media/enable-docker-support-visual-studio.png)

<span data-ttu-id="b44d0-123">Rysunek 4-27: Włącz obsługę platformy Docker podczas tworzenia projektu w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b44d0-123">Figure 4-27: Enable Docker support during project creation in Visual Studio 2017</span></span>

<span data-ttu-id="b44d0-124">Podczas dodawania lub Włącz obsługę platformy Docker, program Visual Studio dodaje *pliku Dockerfile* pliku do projektu.</span><span class="sxs-lookup"><span data-stu-id="b44d0-124">When you add or enable Docker support, Visual Studio adds a *Dockerfile* file to the project.</span></span>

> [!NOTE]
> <span data-ttu-id="b44d0-125">Po włączeniu obsługi narzędzia Docker Compose podczas tworzenia projektu dla projektu aplikacji sieci web .NET Framework (nie platformy .NET Core projektu aplikacji sieci web), jak pokazano w rysunek 4-28, dodawany jest również obsługa orkiestratora kontenerów.</span><span class="sxs-lookup"><span data-stu-id="b44d0-125">When you enable Docker Compose support during project creation for a .NET Framework web app project (not a .NET Core web app project) as shown in Figure 4-28, container orchestrator support is also added.</span></span>
>
> ![Włącz Docker compose obsługę projektu aplikacji sieci web w języku .NET Framework](media/enable-docker-compose-support.png)

> <span data-ttu-id="b44d0-127">Rysunek 4-28: Włączanie narzędzia Docker Compose pomocy technicznej w projekcie aplikacji sieci web .NET Framework w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b44d0-127">Figure 4-28: Enabling Docker Compose support on a .NET Framework web app project in Visual Studio 2017</span></span>

### <a name="add-container-orchestrator-support"></a><span data-ttu-id="b44d0-128">Dodawanie obsługi orkiestratora kontenerów</span><span class="sxs-lookup"><span data-stu-id="b44d0-128">Add container orchestrator support</span></span>

<span data-ttu-id="b44d0-129">W przypadku tworzenia z wieloma kontenerami w celu rozwiązania Dodawanie obsługi orkiestratora kontenerów do swoich projektów.</span><span class="sxs-lookup"><span data-stu-id="b44d0-129">When you want to compose a multicontainer solution, add container orchestrator support to your projects.</span></span> <span data-ttu-id="b44d0-130">Podczas dodawania obsługi orkiestratora kontenerów programu Visual Studio dodaje *pliku Dockerfile* do projektu (jeśli jeszcze nie istnieje) i globalną *docker-compose.yml* pliku na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b44d0-130">When you add container orchestrator support, Visual Studio adds a *Dockerfile* to the project (if it doesn't already exist) and a global *docker-compose.yml* file at the solution level.</span></span> <span data-ttu-id="b44d0-131">Dzięki temu można uruchamiać i debugować grupę kontenerów (całe rozwiązanie) w tym samym czasie, jeśli są one definiowane w tym samym *docker-compose.yml* pliku.</span><span class="sxs-lookup"><span data-stu-id="b44d0-131">This lets you run and debug a group of containers (a whole solution) at the same time if they're defined in the same *docker-compose.yml* file.</span></span> <span data-ttu-id="b44d0-132">Jeśli *docker-compose.yml* już istnieje, program Visual Studio po prostu dodaje wymagane wierszy kodu konfiguracji do niego.</span><span class="sxs-lookup"><span data-stu-id="b44d0-132">If *docker-compose.yml* already exists, Visual Studio just adds the required lines of configuration code to it.</span></span>

<span data-ttu-id="b44d0-133">Po dodaniu obsługi aranżacji kontenerów do projektu, zobacz plik Dockerfile dodane do projektu i **narzędzia docker compose** dodawany do rozwiązania w folderze **Eksploratora rozwiązań**, jak pokazano w rysunek 4-29:</span><span class="sxs-lookup"><span data-stu-id="b44d0-133">After you add container orchestration support to your project, you see a Dockerfile added to the project and a **docker-compose** folder added to the solution in **Solution Explorer**, as shown in Figure 4-29:</span></span>

![Pliki docker w Eksploratorze rozwiązań w programie Visual Studio](media/docker-support-solution-explorer.png)

<span data-ttu-id="b44d0-135">Ilustracja 4-29 plików Docker w Eksploratorze rozwiązań w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b44d0-135">Figure 4-29: Docker files in Solution Explorer in Visual Studio 2017</span></span>

<span data-ttu-id="b44d0-136">**Więcej informacji:** więcej szczegółowych informacji dotyczących wdrażania usług i korzystanie z programu Visual Studio Tools for Docker, przeczytaj następujące artykuły:</span><span class="sxs-lookup"><span data-stu-id="b44d0-136">**More information:** For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>

<span data-ttu-id="b44d0-137">Kompilowanie, debugowanie, aktualizacji i odświeżanie aplikacji w lokalnym kontenerze Docker: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="b44d0-137">Build, debug, update, and refresh apps in a local Docker container: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

<span data-ttu-id="b44d0-138">Wdrażanie kontenera platformy ASP.NET Core Docker do rejestru kontenerów: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="b44d0-138">Deploy an ASP.NET Core Docker container to a container registry: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="b44d0-139">[Poprzednie](docker-apps-inner-loop-workflow.md)
[dalej](set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="b44d0-139">[Previous](docker-apps-inner-loop-workflow.md)
[Next](set-up-windows-containers-with-powershell.md)</span></span>