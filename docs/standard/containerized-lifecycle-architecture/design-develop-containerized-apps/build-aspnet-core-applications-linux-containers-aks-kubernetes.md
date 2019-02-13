---
title: Tworzenie aplikacji platformy ASP.NET Core 2.1 wdrażane jako kontenery systemu Linux w klastrach usługi AKS/Kubernetes
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: b03b6fab9dcd53e97c2bc4d7e5c958ca4b931077
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221394"
---
# <a name="build-aspnet-core-21-applications-deployed-as-linux-containers-into-akskubernetes-orchestrator"></a><span data-ttu-id="d27a2-103">Tworzenie aplikacji platformy ASP.NET Core 2.1 wdrażane jako kontenery systemu Linux do programu orchestrator AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d27a2-103">Build ASP.NET Core 2.1 applications deployed as Linux containers into AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="d27a2-104">Usługa Azure Kubernetes usługi (AKS) to usługi platformy Azure zarządzanego rozwiązania Kubernetes mechanizmów, które upraszczają wdrażanie kontenerów i zarządzanie nimi.</span><span class="sxs-lookup"><span data-stu-id="d27a2-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="d27a2-105">Główne funkcje usługi AKS to:</span><span class="sxs-lookup"><span data-stu-id="d27a2-105">AKS main features are:</span></span>

- <span data-ttu-id="d27a2-106">Płaszczyznę sterowania hostowaną na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="d27a2-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="d27a2-107">Automatyczne uaktualnienia</span><span class="sxs-lookup"><span data-stu-id="d27a2-107">Automated upgrades</span></span>
- <span data-ttu-id="d27a2-108">Samodzielnej naprawy.</span><span class="sxs-lookup"><span data-stu-id="d27a2-108">Self-healing</span></span>
- <span data-ttu-id="d27a2-109">Użytkownika można skonfigurować skalowanie</span><span class="sxs-lookup"><span data-stu-id="d27a2-109">User configurable scaling</span></span>
- <span data-ttu-id="d27a2-110">Prostsze środowisko użytkownika dla deweloperów i operatorów klastra.</span><span class="sxs-lookup"><span data-stu-id="d27a2-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="d27a2-111">Poniższe przykłady zapoznaj się z tworzenia aplikacji platformy ASP.NET Core 2.1, która działa w systemie Linux i wdraża klaster AKS na platformie Azure, podczas gdy projektowanie odbywa się przy użyciu programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="d27a2-111">The following examples explore the creation of an ASP.NET Core 2.1 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-21-project-using-visual-studio-2017"></a><span data-ttu-id="d27a2-112">Tworzenie projektu 2.1 platformy ASP.NET Core przy użyciu programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d27a2-112">Creating the ASP.NET Core 2.1 Project using Visual Studio 2017</span></span>

<span data-ttu-id="d27a2-113">Platforma ASP.NET Core to platforma deweloperska ogólnego przeznaczenia obsługiwane przez firmę Microsoft i społeczności platformy .NET w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="d27a2-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="d27a2-114">Jest dla wielu platform, obsługi Windows, macOS i Linux i mogą być używane w urządzeń, chmury i scenariuszach osadzonych IoT.</span><span class="sxs-lookup"><span data-stu-id="d27a2-114">It is cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="d27a2-115">W tym przykładzie użyto prosty projekt oparty na podstawie interfejsu API sieci Web programu Visual Studio szablonu, więc nie potrzebujesz żadnej wiedzy dodatkowe do utworzenia przykładu.</span><span class="sxs-lookup"><span data-stu-id="d27a2-115">This example uses a simple project that's based based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="d27a2-116">Musisz utworzyć projekt przy użyciu standardowego szablonu, który zawiera wszystkie elementy, aby uruchomić małych projektów za pomocą interfejsu API REST, przy użyciu technologii ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="d27a2-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.1 technology.</span></span>

![Dodaj okno nowego projektu w programie Visual Studio, wybierając aplikację sieci Web programu ASP.NET Core.](media/create-aspnet-core-application.png)

<span data-ttu-id="d27a2-118">**Rysunek 4-36**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-118">**Figure 4-36**.</span></span> <span data-ttu-id="d27a2-119">Tworzenie aplikacji platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d27a2-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="d27a2-120">Aby utworzyć przykładowy projekt, musisz wybrać **pliku** > **New** > **projektu** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d27a2-120">To create the sample project, you have to select **File** > **New** > **Project** on Visual Studio.</span></span> <span data-ttu-id="d27a2-121">A następnie pojawi się lista szablonów dla kilku typów projektów, których należy szukać **Web** > **platformy .NET Core** w panelu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="d27a2-121">Then you'll see a list of templates for several types of projects, where you have to look for **Web** > **.NET Core** on the left panel.</span></span> <span data-ttu-id="d27a2-122">W tym przykładzie wybierz **aplikacji sieci Web programu ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-122">For this example select **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="d27a2-123">W następnym oknie dialogowym upewnij się, wybrane platformy .NET Core i ASP.NET Core 2.1 jako platformę docelową w górnym pulldowns, jak pokazano na rysunku 4-37, a następnie wybierz pozycję opcji interfejsu API, aby utworzyć aplikację internetowego interfejsu API platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d27a2-123">In the next dialog ensure that you have selected .NET Core and ASP.NET Core 2.1 as the target framework in the top pulldowns, as shown in figure 4-37, and then select the API option, to create an ASP.NET Core Web API application.</span></span>

<span data-ttu-id="d27a2-124">.NET Core 2.1 jest dostępne w ramach programu Visual Studio 2017, wersja 15.7.0 lub nowszej i zostanie automatycznie zainstalowany i skonfigurowany dla Ciebie, po wybraniu **programowanie dla wielu platform .NET Core** obciążenie podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="d27a2-124">The .NET Core 2.1 is included in Visual Studio 2017 version 15.7.0 or higher and is automatically installed and configured for you when you select the **.NET Core cross-platform development** workload during installation.</span></span>

![Visual Studio okno dialogowe Wybieranie typu aplikacji sieci Web programu ASP.NET Core z wybraną opcją interfejsu API.](media/create-web-api-application.png)

<span data-ttu-id="d27a2-126">**Rysunek 4-37**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-126">**Figure 4-37**.</span></span> <span data-ttu-id="d27a2-127">Wybieranie platformy ASP.NET CORE 2.1 i interfejsu API sieci Web typu projektu</span><span class="sxs-lookup"><span data-stu-id="d27a2-127">Selecting ASP.NET CORE 2.1 and Web API project type</span></span>

<span data-ttu-id="d27a2-128">W przypadku poprzednich wersji programu .NET Core, można go pobrać i zainstalować wersja 2.1 z <https://www.microsoft.com/net/download/core#/sdk>.</span><span class="sxs-lookup"><span data-stu-id="d27a2-128">If you have any previous version of .NET Core, you can download and install the 2.1 version from <https://www.microsoft.com/net/download/core#/sdk>.</span></span>

<span data-ttu-id="d27a2-129">Podczas tworzenia projektu w poprzednim kroku lub nowszy, jeśli zajdzie taka potrzeba, po uruchomieniu projektu można dodać obsługę platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="d27a2-129">You can add Docker support when creating the project in the previous step, or later, if the need arises after starting the project.</span></span> <span data-ttu-id="d27a2-130">Aby dodać obsługę platformy Docker po utworzeniu projektu, kliknij prawym przyciskiem myszy plik projektu w **Eksploratora rozwiązań** i wybierz **Dodaj** > **obsługę platformy Docker** na menu kontekstowe.</span><span class="sxs-lookup"><span data-stu-id="d27a2-130">To add the Docker support after the project creation, right-click on the project file in the **Solution Explorer** and select **Add** > **Docker support** on the context menu.</span></span>

![Opcja menu kontekstowego, aby dodać obsługę platformy Docker do istniejącego projektu: Kliknij prawym przyciskiem myszy (projekt) > Dodaj > obsługę platformy Docker.](media/add-docker-support-to-project.png)

<span data-ttu-id="d27a2-132">**Rysunek 4-38**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-132">**Figure 4-38**.</span></span> <span data-ttu-id="d27a2-133">Dodawanie obsługi platformy Docker do istniejącego projektu</span><span class="sxs-lookup"><span data-stu-id="d27a2-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="d27a2-134">Aby ukończyć dodawanie obsługę platformy Docker, użytkownik może Windows lub Linux.</span><span class="sxs-lookup"><span data-stu-id="d27a2-134">To complete adding Docker support, you have the choice of Windows or Linux.</span></span> <span data-ttu-id="d27a2-135">W takim przypadku wybierz **Linux**, ponieważ AKS nie obsługuje kontenery Windows (jako późnego 2018 r.).</span><span class="sxs-lookup"><span data-stu-id="d27a2-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Okno dialogowe opcji aby wybrać docelowy system operacyjny do pliku Dockerfile.](media/select-linux-docker-support.png)

<span data-ttu-id="d27a2-137">**Rysunek 4-39**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-137">**Figure 4-39**.</span></span> <span data-ttu-id="d27a2-138">Wybieranie kontenerów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="d27a2-138">Selecting Linux containers.</span></span>

<span data-ttu-id="d27a2-139">Z tych prostych kroków będziesz mieć aplikacji platformy ASP.NET Core 2.1, uruchomionej w kontenerze systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="d27a2-139">With these simple steps, you will have your ASP.NET Core 2.1 application running on a Linux container.</span></span>

<span data-ttu-id="d27a2-140">Jak widać, integrację między usługą Visual Studio 2017 i platformy Docker jest całkowicie ukierunkowana na produktywność dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="d27a2-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="d27a2-141">Teraz możesz nacisnąć przycisk **F5** Aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="d27a2-141">Now you can press **F5** to build and run your application.</span></span>

<span data-ttu-id="d27a2-142">Po uruchomieniu projektu, możesz wyświetlić listę obrazów przy użyciu `docker images` polecenia.</span><span class="sxs-lookup"><span data-stu-id="d27a2-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="d27a2-143">Powinien zostać wyświetlony `mssampleapplication` obrazu utworzonego za pomocą automatycznego wdrażania naszej projektu programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="d27a2-143">You should see the `mssampleapplication` image created with the automatic deploy of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Konsola danych wyjściowych polecenia obrazów platformy docker, wyświetla listę przy użyciu: Repozytorium, tagów, identyfikator obrazu, utworzony (Data) i rozmiar.](media/docker-images-command.png)

<span data-ttu-id="d27a2-145">**Rysunek 4 do 40**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-145">**Figure 4-40**.</span></span> <span data-ttu-id="d27a2-146">Wyświetl obrazy platformy Docker</span><span class="sxs-lookup"><span data-stu-id="d27a2-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="d27a2-147">Zarejestruj rozwiązania w usłudze Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="d27a2-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="d27a2-148">Przekazanie obrazu do dowolnego rejestru platformy Docker, takie jak [usługi Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) lub usługi Docker Hub, dzięki czemu obrazy, którą można wdrożyć klaster usługi AKS z tego rejestru.</span><span class="sxs-lookup"><span data-stu-id="d27a2-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="d27a2-149">W tym przypadku firma Microsoft jest przekazywanie obrazu do usługi Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="d27a2-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="d27a2-150">Tworzenie obrazu w trybie przygotowania do wydania</span><span class="sxs-lookup"><span data-stu-id="d27a2-150">Create the image in Release mode</span></span>

<span data-ttu-id="d27a2-151">Tworzenie obrazu w **wersji** zmiana trybu (gotowe do produkcji) do wersji, jak pokazano poniżej i naciśnij klawisz F5, aby uruchomić ponownie aplikację.</span><span class="sxs-lookup"><span data-stu-id="d27a2-151">Create the image in **Release** Mode (ready for production) changing to Release as shown here and press F5 to run the application again.</span></span>

![Opcja narzędzi w programie VS można tworzyć w trybie wydania.](media/select-release-mode.png)

<span data-ttu-id="d27a2-153">**Rysunek 4-41**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-153">**Figure 4-41**.</span></span> <span data-ttu-id="d27a2-154">Wybierając tryb wersji</span><span class="sxs-lookup"><span data-stu-id="d27a2-154">Selecting Release Mode</span></span>

<span data-ttu-id="d27a2-155">Jeśli zostanie wykonana `docker image` polecenia zostaną wyświetlone zarówno obrazy utworzone.</span><span class="sxs-lookup"><span data-stu-id="d27a2-155">If you execute the `docker image` command, you'll see both images created.</span></span> <span data-ttu-id="d27a2-156">Jeden dla `debug` i inne `release` trybu.</span><span class="sxs-lookup"><span data-stu-id="d27a2-156">One for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="d27a2-157">Tworzenie nowego tagu obrazu</span><span class="sxs-lookup"><span data-stu-id="d27a2-157">Create a new Tag for the Image</span></span>

<span data-ttu-id="d27a2-158">Każdy obraz kontenera musi być oznakowane za pomocą `loginServer` nazwa rejestru.</span><span class="sxs-lookup"><span data-stu-id="d27a2-158">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="d27a2-159">Ten tag jest używany na potrzeby kierowania podczas wypychania obrazów kontenera do rejestru obrazów.</span><span class="sxs-lookup"><span data-stu-id="d27a2-159">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="d27a2-160">Możesz wyświetlić `loginServer` nazwa w witrynie Azure portal, korzystając z informacji od usługi Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="d27a2-160">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Widok przeglądarki nazwy rejestru kontenerów platformy Azure, w prawym górnym rogu.](media/loginServer-name.png)

<span data-ttu-id="d27a2-162">**Rysunek 4-42**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-162">**Figure 4-42**.</span></span> <span data-ttu-id="d27a2-163">Wyświetl nazwę rejestru</span><span class="sxs-lookup"><span data-stu-id="d27a2-163">View of the name of the Registry</span></span>

<span data-ttu-id="d27a2-164">Lub uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d27a2-164">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Konsola danych wyjściowych z powyższego polecenia.](media/az-cli-loginServer-name.png)

<span data-ttu-id="d27a2-166">**Rysunek 4-43**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-166">**Figure 4-43**.</span></span> <span data-ttu-id="d27a2-167">Pobierz nazwę rejestru przy użyciu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="d27a2-167">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="d27a2-168">W obu przypadkach będzie uzyskać nazwę.</span><span class="sxs-lookup"><span data-stu-id="d27a2-168">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="d27a2-169">W naszym przykładzie `mssampleacr.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="d27a2-169">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="d27a2-170">Teraz możesz oznaczyć obrazu, biorąc najnowszego obrazu (wersja obrazu), za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="d27a2-170">Now you can tag the image, taking the latest image (Release image), with the following command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="d27a2-171">Po uruchomieniu `docker tag` polecenia, listy obrazów za pomocą `docker images` polecenia.</span><span class="sxs-lookup"><span data-stu-id="d27a2-171">After running the `docker tag` command, list the images with the `docker images` command.</span></span> <span data-ttu-id="d27a2-172">Powinien zostać wyświetlony obraz za pomocą nowego tagu.</span><span class="sxs-lookup"><span data-stu-id="d27a2-172">You should see the image with the new tag.</span></span>

![Dane wyjściowe z polecenia obrazów platformy docker z konsoli.](media/tagged-docker-images-list.png)

<span data-ttu-id="d27a2-174">**Rysunek 4-44**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-174">**Figure 4-44**.</span></span> <span data-ttu-id="d27a2-175">Wyświetlanie otagowanych obrazów</span><span class="sxs-lookup"><span data-stu-id="d27a2-175">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="d27a2-176">Wypychanie obrazu do rejestru Azure container Registry w platformie Azure</span><span class="sxs-lookup"><span data-stu-id="d27a2-176">Push the image into the Azure ACR</span></span>

<span data-ttu-id="d27a2-177">Wypychanie obrazu do usługi Azure ACR za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="d27a2-177">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="d27a2-178">To polecenie wymaga pewnego czasu przesyłania obrazów, ale udostępnia informacje zwrotne w procesie.</span><span class="sxs-lookup"><span data-stu-id="d27a2-178">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Dane wyjściowe polecenia docker push konsoli: Wyświetla pasek postępu opartego na znakach dla każdej warstwy.](media/uploading-image-to-acr.png)

<span data-ttu-id="d27a2-180">**Rysunek 4-45**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-180">**Figure 4-45**.</span></span> <span data-ttu-id="d27a2-181">Przekazywanie obrazu do usługi ACR</span><span class="sxs-lookup"><span data-stu-id="d27a2-181">Uploading the image to the ACR</span></span>

<span data-ttu-id="d27a2-182">Można zobaczyć poniżej wynik, że powinna pojawić się po zakończeniu procesu:</span><span class="sxs-lookup"><span data-stu-id="d27a2-182">You can see below the result you should get when the process completes:</span></span>

![Dane wyjściowe z polecenia wypychania platformy docker, zakończone, przedstawiający wszystkie warstwy i węzły konsoli.](media/uploading-docker-images-complete.png)

<span data-ttu-id="d27a2-184">**Rysunek 4-46**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-184">**Figure 4-46**.</span></span> <span data-ttu-id="d27a2-185">Widok węzłów</span><span class="sxs-lookup"><span data-stu-id="d27a2-185">View of nodes</span></span>

<span data-ttu-id="d27a2-186">Następnym krokiem jest do wdrożenia kontenera w klastrze AKS rozwiązania Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="d27a2-186">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="d27a2-187">Do tego niezbędny pliku (**yml wdrażanie pliku**), w tym przypadku zawiera:</span><span class="sxs-lookup"><span data-stu-id="d27a2-187">For that you need a file (**.yml deploy file**) that, in this case, contains:</span></span>

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - mane: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> <span data-ttu-id="d27a2-188">Aby uzyskać więcej informacji na temat wdrażania przy użyciu rozwiązania Kubernetes, zobacz: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="d27a2-188">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="d27a2-189">Teraz wszystko jest już niemal gotowa do wdrożenia przy użyciu **Kubectl**, ale najpierw należy uzyskać poświadczenia do klastra usługi AKS przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="d27a2-189">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Dane wyjściowe z powyższego polecenia konsoli: Scalone MSSampleK8Cluster"jako bieżący kontekst w /root/.kube/config](media/getting-aks-credentials.png)

<span data-ttu-id="d27a2-191">**Rysunek 4-47**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-191">**Figure 4-47**.</span></span> <span data-ttu-id="d27a2-192">Uzyskiwanie poświadczeń</span><span class="sxs-lookup"><span data-stu-id="d27a2-192">getting credentials</span></span>

<span data-ttu-id="d27a2-193">Następnie należy użyć `kubectl create` polecenie w celu uruchomienia wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="d27a2-193">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Dane wyjściowe z powyższego polecenia konsoli: wdrożenia "mssamplesbook" utworzony.](media/kubectl-create-command.png)

<span data-ttu-id="d27a2-196">**Rysunek 4-48**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-196">**Figure 4-48**.</span></span> <span data-ttu-id="d27a2-197">Wdrażanie rozwiązania Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d27a2-197">Deploy to Kubernetes</span></span>

<span data-ttu-id="d27a2-198">Po zakończeniu wdrożenia można uzyskiwać dostęp konsoli rozwiązania Kubernetes za pomocą lokalnego serwera proxy, która czasowo dostęp za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="d27a2-198">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="d27a2-199">I uzyskiwania dostępu do adresu url `http://127.0.0.1:8001`.</span><span class="sxs-lookup"><span data-stu-id="d27a2-199">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Widok pulpitu nawigacyjnego rozwiązania Kubernetes, wyświetlanie wdrożeń, zasobników, zestawów replik i usługi w przeglądarce.](media/kubernetes-cluster-information.png)

<span data-ttu-id="d27a2-201">**Rysunek 4-49**.</span><span class="sxs-lookup"><span data-stu-id="d27a2-201">**Figure 4-49**.</span></span> <span data-ttu-id="d27a2-202">Wyświetl informacje o klastrze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d27a2-202">View Kubernetes cluster information</span></span>

<span data-ttu-id="d27a2-203">Masz teraz aplikacji wdrożonych na platformie Azure przy użyciu kontenera systemu Linux i klaster AKS rozwiązania Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="d27a2-203">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="d27a2-204">Możesz uzyskać dostęp do swojej aplikacji, przechodząc do publicznego adresu IP usługi, którą możesz pobrać z witryny Azure portal.</span><span class="sxs-lookup"><span data-stu-id="d27a2-204">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="d27a2-205">Możesz dowiedzieć się, jak do utworzenia klastra usługi AKS dla tego przykładu w sekcji [ **Wdróż na platformie Azure Kubernetes Service (AKS)** ](deploy-azure-kubernetes-service.md) w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="d27a2-205">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d27a2-206">[Poprzednie](set-up-windows-containers-with-powershell.md)
>[dalej](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="d27a2-206">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
