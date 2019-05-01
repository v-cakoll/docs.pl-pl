---
title: Tworzenie aplikacji platformy ASP.NET Core 2.1 wdrażane jako kontenery systemu Linux w klastrach usługi AKS/Kubernetes
description: Cykl życia konteneryzowanych aplikacji platformy Docker korzystających z platformy i narzędzi firmy Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/25/2019
ms.openlocfilehash: c6d778d345466b1b852d06bc01ce40ccfdebf964
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052754"
---
# <a name="build-aspnet-core-21-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="26f0b-103">Tworzenie aplikacji platformy ASP.NET Core 2.1 wdrażane jako kontenery systemu Linux do programu orchestrator AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="26f0b-103">Build ASP.NET Core 2.1 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="26f0b-104">Usługa Azure Kubernetes usługi (AKS) to usługi platformy Azure zarządzanego rozwiązania Kubernetes mechanizmów, które upraszczają wdrażanie kontenerów i zarządzanie nimi.</span><span class="sxs-lookup"><span data-stu-id="26f0b-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="26f0b-105">Główne funkcje usługi AKS to:</span><span class="sxs-lookup"><span data-stu-id="26f0b-105">AKS main features are:</span></span>

- <span data-ttu-id="26f0b-106">Płaszczyznę sterowania hostowaną na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="26f0b-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="26f0b-107">Automatyczne uaktualnienia</span><span class="sxs-lookup"><span data-stu-id="26f0b-107">Automated upgrades</span></span>
- <span data-ttu-id="26f0b-108">Samodzielnej naprawy.</span><span class="sxs-lookup"><span data-stu-id="26f0b-108">Self-healing</span></span>
- <span data-ttu-id="26f0b-109">Użytkownika można skonfigurować skalowanie</span><span class="sxs-lookup"><span data-stu-id="26f0b-109">User configurable scaling</span></span>
- <span data-ttu-id="26f0b-110">Prostsze środowisko użytkownika dla deweloperów i operatorów klastra.</span><span class="sxs-lookup"><span data-stu-id="26f0b-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="26f0b-111">Poniższe przykłady zapoznaj się z tworzenia aplikacji platformy ASP.NET Core 2.1, która działa w systemie Linux i wdraża klaster AKS na platformie Azure, podczas gdy projektowanie odbywa się przy użyciu programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="26f0b-111">The following examples explore the creation of an ASP.NET Core 2.1 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-21-project-using-visual-studio-2017"></a><span data-ttu-id="26f0b-112">Tworzenie projektu 2.1 platformy ASP.NET Core przy użyciu programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="26f0b-112">Creating the ASP.NET Core 2.1 Project using Visual Studio 2017</span></span>

<span data-ttu-id="26f0b-113">Platforma ASP.NET Core to platforma deweloperska ogólnego przeznaczenia obsługiwane przez firmę Microsoft i społeczności platformy .NET w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="26f0b-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="26f0b-114">Jest dla wielu platform, obsługi Windows, macOS i Linux i mogą być używane w urządzeń, chmury i scenariuszach osadzonych IoT.</span><span class="sxs-lookup"><span data-stu-id="26f0b-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="26f0b-115">W tym przykładzie użyto prostego projektu, który opiera się na szablon interfejsu API sieci Web programu Visual Studio, więc nie potrzebujesz żadnej wiedzy dodatkowe do tworzenia przykładu.</span><span class="sxs-lookup"><span data-stu-id="26f0b-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="26f0b-116">Musisz utworzyć projekt przy użyciu standardowego szablonu, który zawiera wszystkie elementy, aby uruchomić małych projektów za pomocą interfejsu API REST, przy użyciu technologii ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="26f0b-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.1 technology.</span></span>

![Dodaj okno nowego projektu w programie Visual Studio, wybierając aplikację sieci Web programu ASP.NET Core.](media/create-aspnet-core-application.png)

<span data-ttu-id="26f0b-118">**Rysunek 4-36**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-118">**Figure 4-36**.</span></span> <span data-ttu-id="26f0b-119">Tworzenie aplikacji platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="26f0b-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="26f0b-120">Aby utworzyć przykładowy projekt w programie Visual Studio, wybierz **pliku** > **New** > **projektu**, wybierz opcję **Web**typów projektów w okienku po lewej stronie, a następnie **aplikacji sieci Web programu ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="26f0b-121">Program Visual Studio Wyświetla listę szablonów dla projektów sieci web.</span><span class="sxs-lookup"><span data-stu-id="26f0b-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="26f0b-122">W tym przykładzie wybierz **API** do tworzenia aplikacji interfejsu API sieci Web programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="26f0b-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="26f0b-123">Sprawdź, czy zostało wybrane platformy ASP.NET Core 2.1 jako platformę.</span><span class="sxs-lookup"><span data-stu-id="26f0b-123">Verify that you've selected ASP.NET Core 2.1 as the framework.</span></span> <span data-ttu-id="26f0b-124">.NET core 2.1 znajduje się w najnowszej wersji programu Visual Studio 2017 i jest automatycznie zainstalowane i skonfigurowane podczas instalacji programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="26f0b-124">.NET Core 2.1 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![Visual Studio okno dialogowe Wybieranie typu aplikacji sieci Web programu ASP.NET Core z wybraną opcją interfejsu API.](media/create-web-api-application.png)

<span data-ttu-id="26f0b-126">**Rysunek 4-37**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-126">**Figure 4-37**.</span></span> <span data-ttu-id="26f0b-127">Wybieranie platformy ASP.NET CORE 2.1 i interfejsu API sieci Web typu projektu</span><span class="sxs-lookup"><span data-stu-id="26f0b-127">Selecting ASP.NET CORE 2.1 and Web API project type</span></span>

<span data-ttu-id="26f0b-128">W przypadku poprzednich wersji programu .NET Core, można go pobrać i zainstalować wersja 2.1 z <https://www.microsoft.com/net/download/core#/sdk>.</span><span class="sxs-lookup"><span data-stu-id="26f0b-128">If you have any previous version of .NET Core, you can download and install the 2.1 version from <https://www.microsoft.com/net/download/core#/sdk>.</span></span>

<span data-ttu-id="26f0b-129">Podczas tworzenia projektu, można dodać obsługę platformy Docker lub później, więc użytkownik może "przekształcać" projektu w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="26f0b-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="26f0b-130">Aby dodać obsługę platformy Docker, po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań, a następnie wybierz **Dodaj** > **obsługę platformy Docker** w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="26f0b-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Opcja menu kontekstowego, aby dodać obsługę platformy Docker do istniejącego projektu: Kliknij prawym przyciskiem myszy (projekt) > Dodaj > obsługę platformy Docker.](media/add-docker-support-to-project.png)

<span data-ttu-id="26f0b-132">**Rysunek 4-38**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-132">**Figure 4-38**.</span></span> <span data-ttu-id="26f0b-133">Dodawanie obsługi platformy Docker do istniejącego projektu</span><span class="sxs-lookup"><span data-stu-id="26f0b-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="26f0b-134">Aby ukończyć dodawanie obsługę platformy Docker, możesz wybrać Windows lub Linux.</span><span class="sxs-lookup"><span data-stu-id="26f0b-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="26f0b-135">W takim przypadku wybierz **Linux**, ponieważ AKS nie obsługuje kontenery Windows (jako późnego 2018 r.).</span><span class="sxs-lookup"><span data-stu-id="26f0b-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Okno dialogowe opcji aby wybrać docelowy system operacyjny do pliku Dockerfile.](media/select-linux-docker-support.png)

<span data-ttu-id="26f0b-137">**Rysunek 4-39**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-137">**Figure 4-39**.</span></span> <span data-ttu-id="26f0b-138">Wybieranie kontenerów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="26f0b-138">Selecting Linux containers.</span></span>

<span data-ttu-id="26f0b-139">Te proste kroki masz aplikacji platformy ASP.NET Core 2.1, uruchomionej w kontenerze systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="26f0b-139">With these simple steps, you have your ASP.NET Core 2.1 application running on a Linux container.</span></span>

<span data-ttu-id="26f0b-140">Jak widać, integrację między usługą Visual Studio 2017 i platformy Docker jest całkowicie ukierunkowana na produktywność dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="26f0b-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="26f0b-141">Teraz można uruchomić aplikacji za pomocą **F5** klucza lub przy użyciu **Odtwórz** przycisku.</span><span class="sxs-lookup"><span data-stu-id="26f0b-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="26f0b-142">Po uruchomieniu projektu, możesz wyświetlić listę obrazów przy użyciu `docker images` polecenia.</span><span class="sxs-lookup"><span data-stu-id="26f0b-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="26f0b-143">Powinien zostać wyświetlony `mssampleapplication` obrazów utworzonych przez automatyczne wdrażanie naszego projektu za pomocą programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="26f0b-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Konsola danych wyjściowych polecenia obrazów platformy docker, wyświetla listę przy użyciu: Repozytorium, tagów, identyfikator obrazu, utworzony (Data) i rozmiar.](media/docker-images-command.png)

<span data-ttu-id="26f0b-145">**Rysunek 4 do 40**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-145">**Figure 4-40**.</span></span> <span data-ttu-id="26f0b-146">Wyświetl obrazy platformy Docker</span><span class="sxs-lookup"><span data-stu-id="26f0b-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="26f0b-147">Zarejestruj rozwiązania w usłudze Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="26f0b-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="26f0b-148">Przekazanie obrazu do dowolnego rejestru platformy Docker, takie jak [usługi Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) lub usługi Docker Hub, dzięki czemu obrazy, którą można wdrożyć klaster usługi AKS z tego rejestru.</span><span class="sxs-lookup"><span data-stu-id="26f0b-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="26f0b-149">W tym przypadku firma Microsoft jest przekazywanie obrazu do usługi Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="26f0b-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="26f0b-150">Tworzenie obrazu w trybie przygotowania do wydania</span><span class="sxs-lookup"><span data-stu-id="26f0b-150">Create the image in Release mode</span></span>

<span data-ttu-id="26f0b-151">Teraz utworzymy obrazu w **wersji** trybu (gotowe do produkcji), zmieniając **wersji**, jak pokazano na rysunku 4-41 i uruchamiania aplikacji, ile My mieliśmy przed.</span><span class="sxs-lookup"><span data-stu-id="26f0b-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![Opcja narzędzi w programie VS można tworzyć w trybie wydania.](media/select-release-mode.png)

<span data-ttu-id="26f0b-153">**Rysunek 4-41**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-153">**Figure 4-41**.</span></span> <span data-ttu-id="26f0b-154">Wybierając tryb wersji</span><span class="sxs-lookup"><span data-stu-id="26f0b-154">Selecting Release Mode</span></span>

<span data-ttu-id="26f0b-155">Jeśli zostanie wykonana `docker image` polecenia zostaną wyświetlone zarówno obrazy utworzone, jeden dla `debug` i inne `release` trybu.</span><span class="sxs-lookup"><span data-stu-id="26f0b-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="26f0b-156">Tworzenie nowego tagu obrazu</span><span class="sxs-lookup"><span data-stu-id="26f0b-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="26f0b-157">Każdy obraz kontenera musi być oznakowane za pomocą `loginServer` nazwa rejestru.</span><span class="sxs-lookup"><span data-stu-id="26f0b-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="26f0b-158">Ten tag jest używany na potrzeby kierowania podczas wypychania obrazów kontenera do rejestru obrazów.</span><span class="sxs-lookup"><span data-stu-id="26f0b-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="26f0b-159">Możesz wyświetlić `loginServer` nazwa w witrynie Azure portal, korzystając z informacji od usługi Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="26f0b-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Widok przeglądarki nazwy rejestru kontenerów platformy Azure, w prawym górnym rogu.](media/loginServer-name.png)

<span data-ttu-id="26f0b-161">**Rysunek 4-42**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-161">**Figure 4-42**.</span></span> <span data-ttu-id="26f0b-162">Wyświetl nazwę rejestru</span><span class="sxs-lookup"><span data-stu-id="26f0b-162">View of the name of the Registry</span></span>

<span data-ttu-id="26f0b-163">Lub uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="26f0b-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Konsola danych wyjściowych z powyższego polecenia.](media/az-cli-loginServer-name.png)

<span data-ttu-id="26f0b-165">**Rysunek 4-43**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-165">**Figure 4-43**.</span></span> <span data-ttu-id="26f0b-166">Pobierz nazwę rejestru przy użyciu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="26f0b-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="26f0b-167">W obu przypadkach będzie uzyskać nazwę.</span><span class="sxs-lookup"><span data-stu-id="26f0b-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="26f0b-168">W naszym przykładzie `mssampleacr.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="26f0b-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="26f0b-169">Teraz możesz oznaczyć obrazu, biorąc najnowszego obrazu (obraz wersji), za pomocą polecenia:</span><span class="sxs-lookup"><span data-stu-id="26f0b-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="26f0b-170">Po uruchomieniu `docker tag` polecenia, listy obrazów za pomocą `docker images` polecenia, a powinien zostać wyświetlony obraz za pomocą nowego tagu.</span><span class="sxs-lookup"><span data-stu-id="26f0b-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Dane wyjściowe z polecenia obrazów platformy docker z konsoli.](media/tagged-docker-images-list.png)

<span data-ttu-id="26f0b-172">**Rysunek 4-44**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-172">**Figure 4-44**.</span></span> <span data-ttu-id="26f0b-173">Wyświetlanie otagowanych obrazów</span><span class="sxs-lookup"><span data-stu-id="26f0b-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="26f0b-174">Wypychanie obrazu do rejestru Azure container Registry w platformie Azure</span><span class="sxs-lookup"><span data-stu-id="26f0b-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="26f0b-175">Wypychanie obrazu do usługi Azure ACR za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="26f0b-175">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="26f0b-176">To polecenie wymaga pewnego czasu przesyłania obrazów, ale udostępnia informacje zwrotne w procesie.</span><span class="sxs-lookup"><span data-stu-id="26f0b-176">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Dane wyjściowe polecenia docker push konsoli: Wyświetla pasek postępu opartego na znakach dla każdej warstwy.](media/uploading-image-to-acr.png)

<span data-ttu-id="26f0b-178">**Rysunek 4-45**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-178">**Figure 4-45**.</span></span> <span data-ttu-id="26f0b-179">Przekazywanie obrazu do usługi ACR</span><span class="sxs-lookup"><span data-stu-id="26f0b-179">Uploading the image to the ACR</span></span>

<span data-ttu-id="26f0b-180">Można zobaczyć poniżej wynik, że powinna pojawić się po zakończeniu procesu:</span><span class="sxs-lookup"><span data-stu-id="26f0b-180">You can see below the result you should get when the process completes:</span></span>

![Dane wyjściowe z polecenia wypychania platformy docker, zakończone, przedstawiający wszystkie warstwy i węzły konsoli.](media/uploading-docker-images-complete.png)

<span data-ttu-id="26f0b-182">**Rysunek 4-46**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-182">**Figure 4-46**.</span></span> <span data-ttu-id="26f0b-183">Widok węzłów</span><span class="sxs-lookup"><span data-stu-id="26f0b-183">View of nodes</span></span>

<span data-ttu-id="26f0b-184">Następnym krokiem jest do wdrożenia kontenera w klastrze AKS rozwiązania Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="26f0b-184">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="26f0b-185">Do tego niezbędny pliku (**yml wdrażanie pliku**) zawiera następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="26f0b-185">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

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
> <span data-ttu-id="26f0b-186">Aby uzyskać więcej informacji na temat wdrażania przy użyciu rozwiązania Kubernetes, zobacz: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="26f0b-186">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="26f0b-187">Teraz wszystko jest już niemal gotowa do wdrożenia przy użyciu **Kubectl**, ale najpierw należy uzyskać poświadczenia do klastra usługi AKS przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="26f0b-187">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Dane wyjściowe z powyższego polecenia konsoli: Scalone MSSampleK8Cluster"jako bieżący kontekst w /root/.kube/config](media/getting-aks-credentials.png)

<span data-ttu-id="26f0b-189">**Rysunek 4-47**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-189">**Figure 4-47**.</span></span> <span data-ttu-id="26f0b-190">Uzyskiwanie poświadczeń</span><span class="sxs-lookup"><span data-stu-id="26f0b-190">getting credentials</span></span>

<span data-ttu-id="26f0b-191">Następnie należy użyć `kubectl create` polecenie w celu uruchomienia wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="26f0b-191">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Dane wyjściowe z powyższego polecenia konsoli: wdrożenia "mssamplesbook" utworzony.](media/kubectl-create-command.png)

<span data-ttu-id="26f0b-194">**Rysunek 4-48**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-194">**Figure 4-48**.</span></span> <span data-ttu-id="26f0b-195">Wdrażanie rozwiązania Kubernetes</span><span class="sxs-lookup"><span data-stu-id="26f0b-195">Deploy to Kubernetes</span></span>

<span data-ttu-id="26f0b-196">Po zakończeniu wdrożenia można uzyskiwać dostęp konsoli rozwiązania Kubernetes za pomocą lokalnego serwera proxy, która czasowo dostęp za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="26f0b-196">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="26f0b-197">I uzyskiwania dostępu do adresu url `http://127.0.0.1:8001`.</span><span class="sxs-lookup"><span data-stu-id="26f0b-197">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Widok pulpitu nawigacyjnego rozwiązania Kubernetes, wyświetlanie wdrożeń, zasobników, zestawów replik i usługi w przeglądarce.](media/kubernetes-cluster-information.png)

<span data-ttu-id="26f0b-199">**Rysunek 4-49**.</span><span class="sxs-lookup"><span data-stu-id="26f0b-199">**Figure 4-49**.</span></span> <span data-ttu-id="26f0b-200">Wyświetl informacje o klastrze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="26f0b-200">View Kubernetes cluster information</span></span>

<span data-ttu-id="26f0b-201">Masz teraz aplikacji wdrożonych na platformie Azure przy użyciu kontenera systemu Linux i klaster AKS rozwiązania Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="26f0b-201">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="26f0b-202">Możesz uzyskać dostęp do swojej aplikacji, przechodząc do publicznego adresu IP usługi, którą możesz pobrać z witryny Azure portal.</span><span class="sxs-lookup"><span data-stu-id="26f0b-202">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="26f0b-203">Możesz dowiedzieć się, jak do utworzenia klastra usługi AKS dla tego przykładu w sekcji [ **Wdróż na platformie Azure Kubernetes Service (AKS)** ](deploy-azure-kubernetes-service.md) w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="26f0b-203">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="26f0b-204">[Poprzednie](set-up-windows-containers-with-powershell.md)
>[dalej](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="26f0b-204">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
