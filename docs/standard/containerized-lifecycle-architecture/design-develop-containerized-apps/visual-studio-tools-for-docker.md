---
title: "Za pomocą narzędzi Visual Studio Tools for Docker (Visual Studio w systemie Windows)"
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 717675170f19f18fb48c4cea3ddd15bcd9648d71
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a><span data-ttu-id="017f8-104">Za pomocą narzędzi Visual Studio Tools for Docker (Visual Studio w systemie Windows)</span><span class="sxs-lookup"><span data-stu-id="017f8-104">Using Visual Studio Tools for Docker (Visual Studio on Windows)</span></span>

<span data-ttu-id="017f8-105">Przepływ pracy deweloperów, gdy za pomocą narzędzi Visual Studio Tools dla Docker jest podobny do przepływu pracy, korzystając z programu Visual Studio Code i interfejsu wiersza polecenia Docker (w rzeczywistości go opiera się na tym samym interfejsu wiersza polecenia Docker), ale jest łatwiej rozpocząć pracę, upraszcza proces i zapewnia większą wydajność dla kompilacji, uruchomić i tworzą zadania.</span><span class="sxs-lookup"><span data-stu-id="017f8-105">The developer workflow when using Visual Studio Tools for Docker is similar to the workflow when using Visual Studio Code and Docker CLI (in fact, it is based on the same Docker CLI), but it is easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="017f8-106">Istnieje również możliwość wykonania i debugowanie kontenerów za pomocą prostego akcji, takich jak F5 i Ctrl + F5 w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="017f8-106">It's also able to execute and debug your containers via simple actions like F5 and Ctrl+F5 from Visual Studio.</span></span> <span data-ttu-id="017f8-107">Jeszcze bardziej z programu Visual Studio 2017 r, oprócz możliwości by przeprowadzić debugowanie jeden kontener, również można uruchomić i debugowania grupy kontenerów (całe rozwiązanie) w tym samym czasie, jeśli są one zdefiniowane w ten sam plik docker-compose.yml na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="017f8-107">Even more, with Visual Studio 2017, in addition to being able to run and debug a single container, you also can run and debug a group of containers (a whole solution) at the same time if they are defined in the same docker-compose.yml file at the solution level.</span></span>

## <a name="configuring-your-local-environment"></a><span data-ttu-id="017f8-108">Konfigurowanie środowiska lokalnego</span><span class="sxs-lookup"><span data-stu-id="017f8-108">Configuring your local environment</span></span>

<span data-ttu-id="017f8-109">Najnowsze wersje Docker dla systemu Windows jest łatwiejsze niż kiedykolwiek do opracowywania aplikacji Docker ponieważ Instalator jest proste, jak opisano w następujących odwołań.</span><span class="sxs-lookup"><span data-stu-id="017f8-109">With the latest versions of Docker for Windows, it is easier than ever to develop Docker applications because the setup is straightforward, as explained in the following references.</span></span>

<span data-ttu-id="017f8-110">**Aby dowiedzieć się więcej:** Aby dowiedzieć się więcej na temat instalowania Docker dla systemu Windows, przejdź do <https://docs.docker.com/docker-for-windows/>.</span><span class="sxs-lookup"><span data-stu-id="017f8-110">**More info:** To learn more about installing Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>

<span data-ttu-id="017f8-111">Jeśli używasz programu Visual Studio 2015, musi mieć aktualizacji 3 lub nowszym oraz programu Visual Studio Tools for Docker.</span><span class="sxs-lookup"><span data-stu-id="017f8-111">If you're using Visual Studio 2015, you must have Update 3 or a later version plus the Visual Studio Tools for Docker.</span></span>

<span data-ttu-id="017f8-112">**Aby dowiedzieć się więcej:** instrukcje dotyczące instalowania programu Visual Studio, przejdź do [https://www.visualstudio.com/ \ produkty/vs-2015-— wersje produktu](https://www.visualstudio.com/products/vs-2015-product-editions).</span><span class="sxs-lookup"><span data-stu-id="017f8-112">**More info:** For instructions on installing Visual Studio, go to [https://www.visualstudio.com/\ products/vs-2015-product-editions](https://www.visualstudio.com/products/vs-2015-product-editions).</span></span>

<span data-ttu-id="017f8-113">Aby wyświetlić więcej informacji na temat instalowania programu Visual Studio Tools for Docker, przejdź do <http://aka.ms/vstoolsfordocker> i <https://docs.microsoft.com/dotnet/articles/core/docker/visual-studio-tools-for-docker>.</span><span class="sxs-lookup"><span data-stu-id="017f8-113">To see more about installing Visual Studio Tools for Docker, go to <http://aka.ms/vstoolsfordocker> and <https://docs.microsoft.com/dotnet/articles/core/docker/visual-studio-tools-for-docker>.</span></span>

<span data-ttu-id="017f8-114">Jeśli używasz programu Visual Studio 2017 Docker obsługi jest już dołączony.</span><span class="sxs-lookup"><span data-stu-id="017f8-114">If you're using Visual Studio 2017, Docker support is already included.</span></span>

## <a name="using-docker-tools-in-visual-studio-2015"></a><span data-ttu-id="017f8-115">Za pomocą narzędzi Docker w programie Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="017f8-115">Using Docker Tools in Visual Studio 2015</span></span>

<span data-ttu-id="017f8-116">Visual Studio Tools for Docker zapewnia spójny sposób rozwijać i zweryfikować lokalnie kontenerów Docker dla systemu Linux na hoście systemu Linux Docker lub maszyny Wirtualnej lub kontenerów systemu Windows bezpośrednio w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="017f8-116">The Visual Studio Tools for Docker provides a consistent way to develop and validate locally your Docker containers for Linux in a Linux Docker host or VM, or your Windows Containers directly on Windows.</span></span>

<span data-ttu-id="017f8-117">Jeśli używasz jeden kontener, w pierwszej kolejności należy rozpocząć jest włączenie obsługi Docker do projektu platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="017f8-117">If you're using a single container, the first thing you need to begin is to turn on Docker support into your .NET Core project.</span></span> <span data-ttu-id="017f8-118">Aby to zrobić, kliknij prawym przyciskiem myszy plik projektu, jak pokazano na rysunku 4-25.</span><span class="sxs-lookup"><span data-stu-id="017f8-118">To do this, right-click your project file, as shown in Figure 4-25.</span></span>

![https://i1.visualstudiogallery.msdn.s-msft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4/image/file/205468/1/add-docker-support.png](./media/image31.png)

<span data-ttu-id="017f8-120">Rysunek 4-25: włączania obsługi Docker projektu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="017f8-120">Figure 4-25: Turning on Docker support for your Visual Studio project</span></span>

## <a name="using-docker-tools-in-visual-studio-2017"></a><span data-ttu-id="017f8-121">Za pomocą narzędzi Docker w programie Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="017f8-121">Using Docker Tools in Visual Studio 2017</span></span>

<span data-ttu-id="017f8-122">Po dodaniu obsługi Docker do projektu usługi w rozwiązaniu (zobacz rysunek 4-26) i Visual Studio jest nie tylko można dodać plik DockerFile plik do projektu, jego również jest dodanie usługi sekcji rozwiązania docker-compose.yml plików (lub tworzenia plików, jeśli nie zostały one istnieje).</span><span class="sxs-lookup"><span data-stu-id="017f8-122">When you add Docker support to a service project in your solution (see Figure 4-26), Visual Studio is not just adding a DockerFile file to your project, it also is adding a service section in your solution's docker-compose.yml files (or creating the files if they didn't exist).</span></span> <span data-ttu-id="017f8-123">Jest to prosty sposób, aby rozpocząć tworzenie rozwiązania multicontainer; następnie można otwierać pliki docker-compose.yml i zaktualizować je z dodatkowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="017f8-123">It's an easy way to begin composing your multicontainer solution; you then can open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image32.png)

<span data-ttu-id="017f8-124">Rysunek 4-26: włączania obsługi rozwiązania Docker w projekcie programu Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="017f8-124">Figure 4-26: Turning on Docker Solution support in a Visual Studio 2017 project</span></span>

<span data-ttu-id="017f8-125">Ta akcja dodaje plik DockerFile nie tylko do projektu, dodane również wymagana konfiguracja wiersze kodu do globalnego docker-compose.yml należy ustawić na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="017f8-125">This action not only adds the DockerFile to your project, it also adds the required configuration lines of code to a global docker-compose.yml set at the solution level.</span></span>

<span data-ttu-id="017f8-126">Także można włączyć obsługę Docker podczas tworzenia projektu platformy ASP.NET Core w Visual Studio 2017 r, jak pokazano w rysunek 4-27.</span><span class="sxs-lookup"><span data-stu-id="017f8-126">You also can turn on Docker support when creating an ASP.NET Core project in Visual Studio 2017, as shown in Figure 4-27.</span></span>

![](./media/image33.png)

<span data-ttu-id="017f8-127">Rysunek 4-27: włączania obsługi Docker podczas tworzenia projektu</span><span class="sxs-lookup"><span data-stu-id="017f8-127">Figure 4-27: Turning on Docker support when creating a project</span></span>

<span data-ttu-id="017f8-128">Po dodaniu obsługi Docker do rozwiązania w programie Visual Studio również zobaczysz nowe drzewo węzła w Eksploratorze rozwiązań z plikami dodano docker-compose.yml, jak pokazano w rysunek 4-28.</span><span class="sxs-lookup"><span data-stu-id="017f8-128">After you add Docker support to your solution in Visual Studio, you also will see a new node tree in Solution Explorer with the added docker-compose.yml files, as depicted in Figure 4-28.</span></span>

![](./media/image34.PNG)

<span data-ttu-id="017f8-129">Rysunek 4-28: docker-compose.yml plików jest teraz wyświetlany w Eksploratorze rozwiązań</span><span class="sxs-lookup"><span data-stu-id="017f8-129">Figure 4-28: docker-compose.yml files now display in Solution Explorer</span></span>

<span data-ttu-id="017f8-130">Można wdrożyć multicontainer aplikacji przy użyciu pliku pojedynczego docker-compose.yml po uruchomieniu rozwiązania docker-compose; jednak Visual Studio dodaje grupę, więc można zastąpić wartości w zależności od środowiska (Programowanie i produkcja) i wykonywania typu (wersja i debugowania).</span><span class="sxs-lookup"><span data-stu-id="017f8-130">You could deploy a multicontainer application by using a single docker-compose.yml file when you run docker-compose up; however, Visual Studio adds a group of them, so you can override values depending on the environment (development versus production) and the execution type (release versus debug).</span></span> <span data-ttu-id="017f8-131">Ta funkcja zostanie lepiej wyjaśnione w rozdziałach nowsze.</span><span class="sxs-lookup"><span data-stu-id="017f8-131">This capability will be better explained in later chapters.</span></span>

<span data-ttu-id="017f8-132">**Aby dowiedzieć się więcej:** Aby uzyskać więcej szczegółowych informacji o implementacji usług i korzystanie z programu Visual Studio Tools for Docker, przeczytaj następujące artykuły:</span><span class="sxs-lookup"><span data-stu-id="017f8-132">**More info:** For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>

<span data-ttu-id="017f8-133">Kompilacji, debugowania, aktualizacji i odświeżanie aplikacji w kontenerze Docker lokalnego: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="017f8-133">Build, debug, update, and refresh apps in a local Docker container: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

<span data-ttu-id="017f8-134">Wdrażanie kontenera ASP.NET z hostem zdalnym Docker: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="017f8-134">Deploy an ASP.NET container to a remote Docker host: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="017f8-135">[Poprzednie] (docker aplikacje — wewnętrzny pętli workflow.md) [dalej] (set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="017f8-135">[Previous] (docker-apps-inner-loop-workflow.md) [Next] (set-up-windows-containers-with-powershell.md)</span></span>
