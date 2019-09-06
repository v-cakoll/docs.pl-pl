---
title: Kompiluj ASP.NET Core 2,2 aplikacje wdrożone jako kontenery systemu Linux w klastrach AKS/Kubernetes
description: Cykl życia konteneryzowanych aplikacji platformy Docker korzystających z platformy i narzędzi firmy Microsoft
ms.date: 02/25/2019
ms.openlocfilehash: 89843e0041c12f001f974360da2e5903499155d1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295354"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="f79cb-103">Kompilowanie aplikacji ASP.NET Core 2,2 wdrożonych jako kontenery systemu Linux w programie Orchestrator AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f79cb-103">Build ASP.NET Core 2.2 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="f79cb-104">Usługa Azure Kubernetes Services (AKS) to zarządzane przez platformę Azure usługi, które upraszczają wdrażanie kontenerów i zarządzanie nimi.</span><span class="sxs-lookup"><span data-stu-id="f79cb-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="f79cb-105">Główne funkcje AKS są następujące:</span><span class="sxs-lookup"><span data-stu-id="f79cb-105">AKS main features are:</span></span>

- <span data-ttu-id="f79cb-106">Oparta na platformie Azure płaszczyzna kontroli</span><span class="sxs-lookup"><span data-stu-id="f79cb-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="f79cb-107">Automatyczne uaktualnienia</span><span class="sxs-lookup"><span data-stu-id="f79cb-107">Automated upgrades</span></span>
- <span data-ttu-id="f79cb-108">Samonaprawianie</span><span class="sxs-lookup"><span data-stu-id="f79cb-108">Self-healing</span></span>
- <span data-ttu-id="f79cb-109">Konfigurowalne skalowanie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f79cb-109">User configurable scaling</span></span>
- <span data-ttu-id="f79cb-110">Prostsze środowisko użytkownika dla deweloperów i operatorów klastrów.</span><span class="sxs-lookup"><span data-stu-id="f79cb-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="f79cb-111">W poniższych przykładach pokazano, jak utworzyć aplikację ASP.NET Core 2,2 działającą w systemie Linux i wdrożyć ją w klastrze AKS na platformie Azure, podczas gdy programowanie odbywa się przy użyciu programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="f79cb-111">The following examples explore the creation of an ASP.NET Core 2.2 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a><span data-ttu-id="f79cb-112">Tworzenie projektu ASP.NET Core 2,2 przy użyciu programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f79cb-112">Creating the ASP.NET Core 2.2 Project using Visual Studio 2017</span></span>

<span data-ttu-id="f79cb-113">ASP.NET Core jest platformą programistyczną ogólnego przeznaczenia obsługiwaną przez firmę Microsoft i społeczność programu .NET w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="f79cb-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="f79cb-114">Jest to międzyplatformowe, pomocnicze systemy Windows, macOS i Linux oraz mogą być używane w scenariuszach urządzeń, chmur i osadzonych/IoT.</span><span class="sxs-lookup"><span data-stu-id="f79cb-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="f79cb-115">Ten przykład używa prostego projektu, który jest oparty na szablonie interfejsu API sieci Web programu Visual Studio, więc nie potrzebujesz dodatkowej wiedzy do utworzenia przykładu.</span><span class="sxs-lookup"><span data-stu-id="f79cb-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="f79cb-116">Wystarczy utworzyć projekt przy użyciu standardowego szablonu, który zawiera wszystkie elementy, aby uruchomić niewielki projekt z interfejsem API REST przy użyciu technologii ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="f79cb-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.2 technology.</span></span>

![Dodaj nowe okno projektu w programie Visual Studio, wybierając ASP.NET Core aplikacji sieci Web.](media/create-aspnet-core-application.png)

<span data-ttu-id="f79cb-118">**Rysunek 4-36**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-118">**Figure 4-36**.</span></span> <span data-ttu-id="f79cb-119">Tworzenie aplikacji ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f79cb-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="f79cb-120">Aby utworzyć przykładowy projekt w programie Visual Studio, wybierz pozycję **plik** > **Nowy** > **projekt**, wybierz typy projektu **sieci Web** w lewym okienku, a następnie **ASP.NET Core aplikacji sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="f79cb-121">Program Visual Studio Wyświetla listę szablonów dla projektów sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f79cb-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="f79cb-122">W naszym przykładzie wybierz pozycję **interfejs API** , aby utworzyć aplikację interfejsu API sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f79cb-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="f79cb-123">Upewnij się, że wybrano ASP.NET Core 2,2 jako strukturę.</span><span class="sxs-lookup"><span data-stu-id="f79cb-123">Verify that you've selected ASP.NET Core 2.2 as the framework.</span></span> <span data-ttu-id="f79cb-124">Program .NET Core 2,2 jest dołączony do najnowszej wersji programu Visual Studio 2017 i jest automatycznie instalowany i konfigurowany podczas instalowania programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="f79cb-124">.NET Core 2.2 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![Okno dialogowe programu Visual Studio, w którym można wybrać typ aplikacji sieci Web ASP.NET Core przy użyciu opcji API.](media/create-web-api-application.png)

<span data-ttu-id="f79cb-126">**Rysunek 4-37**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-126">**Figure 4-37**.</span></span> <span data-ttu-id="f79cb-127">Wybieranie ASP.NET CORE 2,2 i typ projektu interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="f79cb-127">Selecting ASP.NET CORE 2.2 and Web API project type</span></span>

<span data-ttu-id="f79cb-128">Jeśli masz poprzednią wersję programu .NET Core, możesz pobrać i zainstalować wersję 2,2 z <https://www.microsoft.com/net/download/core#/sdk>programu.</span><span class="sxs-lookup"><span data-stu-id="f79cb-128">If you have any previous version of .NET Core, you can download and install the 2.2 version from <https://www.microsoft.com/net/download/core#/sdk>.</span></span>

<span data-ttu-id="f79cb-129">Możesz dodać obsługę platformy Docker podczas tworzenia projektu lub później, aby w dowolnym momencie można było "przekształcać".</span><span class="sxs-lookup"><span data-stu-id="f79cb-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="f79cb-130">Aby dodać obsługę platformy Docker po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań a następnie wybierz polecenie **Dodaj** > **obsługę platformy Docker** w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="f79cb-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Opcja menu kontekstowego umożliwiająca dodanie obsługi platformy Docker do istniejącego projektu: Kliknij prawym przyciskiem myszy (na projekcie) > Dodaj > obsłudze platformy Docker.](media/add-docker-support-to-project.png)

<span data-ttu-id="f79cb-132">**Rysunek 4-38**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-132">**Figure 4-38**.</span></span> <span data-ttu-id="f79cb-133">Dodawanie obsługi platformy Docker do istniejącego projektu</span><span class="sxs-lookup"><span data-stu-id="f79cb-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="f79cb-134">Aby ukończyć Dodawanie obsługi platformy Docker, możesz wybrać system Windows lub Linux.</span><span class="sxs-lookup"><span data-stu-id="f79cb-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="f79cb-135">W takim przypadku wybierz pozycję **Linux**, ponieważ usługa AKS nie obsługuje kontenerów systemu Windows (z opóźnieniem 2018).</span><span class="sxs-lookup"><span data-stu-id="f79cb-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Opcja okna dialogowego umożliwiającego wybranie docelowego systemu operacyjnego dla pliku dockerfile.](media/select-linux-docker-support.png)

<span data-ttu-id="f79cb-137">**Rysunek 4-39**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-137">**Figure 4-39**.</span></span> <span data-ttu-id="f79cb-138">Wybieranie kontenerów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="f79cb-138">Selecting Linux containers.</span></span>

<span data-ttu-id="f79cb-139">Dzięki tym prostym krokom aplikacja ASP.NET Core 2,2 działa w kontenerze systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="f79cb-139">With these simple steps, you have your ASP.NET Core 2.2 application running on a Linux container.</span></span>

<span data-ttu-id="f79cb-140">Jak widać, integracja między programem Visual Studio 2017 i platformą Docker jest całkowicie ukierunkowana na produktywność dewelopera.</span><span class="sxs-lookup"><span data-stu-id="f79cb-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="f79cb-141">Teraz możesz uruchomić aplikację przy użyciu klawisza **F5** lub przycisku **Odtwórz** .</span><span class="sxs-lookup"><span data-stu-id="f79cb-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="f79cb-142">Po uruchomieniu projektu można wyświetlić listę obrazów przy użyciu `docker images` polecenia.</span><span class="sxs-lookup"><span data-stu-id="f79cb-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="f79cb-143">Powinien zostać wyświetlony `mssampleapplication` obraz utworzony przez automatyczne wdrażanie naszego projektu przy użyciu programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="f79cb-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Dane wyjściowe konsoli z polecenia Docker images pokazują listę z: Repozytorium, tag, identyfikator obrazu, utworzony (Date) i rozmiar.](media/docker-images-command.png)

<span data-ttu-id="f79cb-145">**Rysunek 4-40**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-145">**Figure 4-40**.</span></span> <span data-ttu-id="f79cb-146">Widok obrazów platformy Docker</span><span class="sxs-lookup"><span data-stu-id="f79cb-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="f79cb-147">Zarejestruj rozwiązanie w Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="f79cb-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="f79cb-148">Przekaż obraz do dowolnego rejestru platformy Docker, takiego jak [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) lub Docker Hub, aby obrazy można wdrożyć w klastrze AKS z tego rejestru.</span><span class="sxs-lookup"><span data-stu-id="f79cb-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="f79cb-149">W tym przypadku przekazujemy obraz do Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="f79cb-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="f79cb-150">Tworzenie obrazu w trybie wydania</span><span class="sxs-lookup"><span data-stu-id="f79cb-150">Create the image in Release mode</span></span>

<span data-ttu-id="f79cb-151">Teraz utworzysz obraz w trybie **wydania** (gotowy do produkcji), zmieniając do **wersji**, jak pokazano na rysunku 4-41 i uruchamiając aplikację tak jak wcześniej.</span><span class="sxs-lookup"><span data-stu-id="f79cb-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![Opcja paska narzędzi w programie VS do kompilowania w trybie wydania.](media/select-release-mode.png)

<span data-ttu-id="f79cb-153">**Rysunek 4-41**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-153">**Figure 4-41**.</span></span> <span data-ttu-id="f79cb-154">Wybieranie trybu wydania</span><span class="sxs-lookup"><span data-stu-id="f79cb-154">Selecting Release Mode</span></span>

<span data-ttu-id="f79cb-155">Jeśli wykonasz `docker image` polecenie, zobaczysz obu utworzonych obrazów, jeden dla `debug` i drugi dla `release` trybu.</span><span class="sxs-lookup"><span data-stu-id="f79cb-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="f79cb-156">Utwórz nowy tag dla obrazu</span><span class="sxs-lookup"><span data-stu-id="f79cb-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="f79cb-157">Każdy obraz kontenera musi być oznaczony `loginServer` nazwą rejestru.</span><span class="sxs-lookup"><span data-stu-id="f79cb-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="f79cb-158">Ten tag jest używany do routingu podczas wypychania obrazów kontenera do rejestru obrazów.</span><span class="sxs-lookup"><span data-stu-id="f79cb-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="f79cb-159">Można wyświetlić `loginServer` nazwę z Azure Portal, pobierając informacje z Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="f79cb-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Widok w przeglądarce Nazwa rejestru kontenerów platformy Azure znajduje się w prawym górnym rogu.](media/loginServer-name.png)

<span data-ttu-id="f79cb-161">**Rysunek 4-42**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-161">**Figure 4-42**.</span></span> <span data-ttu-id="f79cb-162">Wyświetl nazwę rejestru</span><span class="sxs-lookup"><span data-stu-id="f79cb-162">View of the name of the Registry</span></span>

<span data-ttu-id="f79cb-163">Lub uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f79cb-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Dane wyjściowe konsoli z powyższego polecenia.](media/az-cli-loginServer-name.png)

<span data-ttu-id="f79cb-165">**Rysunek 4-43**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-165">**Figure 4-43**.</span></span> <span data-ttu-id="f79cb-166">Pobieranie nazwy rejestru przy użyciu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="f79cb-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="f79cb-167">W obu przypadkach należy uzyskać nazwę.</span><span class="sxs-lookup"><span data-stu-id="f79cb-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="f79cb-168">W naszym przykładzie `mssampleacr.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="f79cb-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="f79cb-169">Teraz możesz oznaczyć obraz, pobierając najnowszą wersję obrazu (obraz wersji) za pomocą polecenia:</span><span class="sxs-lookup"><span data-stu-id="f79cb-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="f79cb-170">Po uruchomieniu `docker tag` polecenia należy wyświetlić listę obrazów `docker images` za pomocą polecenia, a obraz z nowym tagiem.</span><span class="sxs-lookup"><span data-stu-id="f79cb-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Dane wyjściowe konsoli z polecenia Docker images.](media/tagged-docker-images-list.png)

<span data-ttu-id="f79cb-172">**Rysunek 4-44**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-172">**Figure 4-44**.</span></span> <span data-ttu-id="f79cb-173">Widok obrazów oznakowanych</span><span class="sxs-lookup"><span data-stu-id="f79cb-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="f79cb-174">Wypchnij obraz do usługi Azure ACR</span><span class="sxs-lookup"><span data-stu-id="f79cb-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="f79cb-175">Zaloguj się do Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="f79cb-175">Log in to the Azure Container Registry</span></span>

```console
az acr login --name mssampleacr
```

<span data-ttu-id="f79cb-176">Wypchnij obraz do usługi Azure ACR za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="f79cb-176">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="f79cb-177">To polecenie pobiera obrazy, ale zawiera informacje zwrotne w procesie.</span><span class="sxs-lookup"><span data-stu-id="f79cb-177">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Dane wyjściowe konsoli z polecenia Docker push: pokazuje pasek postępu oparty na znakach dla każdej warstwy.](media/uploading-image-to-acr.png)

<span data-ttu-id="f79cb-179">**Rysunek 4-45**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-179">**Figure 4-45**.</span></span> <span data-ttu-id="f79cb-180">Przekazywanie obrazu do ACR</span><span class="sxs-lookup"><span data-stu-id="f79cb-180">Uploading the image to the ACR</span></span>

<span data-ttu-id="f79cb-181">Poniżej można zobaczyć wynik, który powinien zostać wyświetlony po zakończeniu procesu:</span><span class="sxs-lookup"><span data-stu-id="f79cb-181">You can see below the result you should get when the process completes:</span></span>

![Dane wyjściowe konsoli z polecenia Docker push, zakończone, pokazujące wszystkie warstwy lub węzły.](media/uploading-docker-images-complete.png)

<span data-ttu-id="f79cb-183">**Rysunek 4-46**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-183">**Figure 4-46**.</span></span> <span data-ttu-id="f79cb-184">Widok węzłów</span><span class="sxs-lookup"><span data-stu-id="f79cb-184">View of nodes</span></span>

<span data-ttu-id="f79cb-185">Następnym krokiem jest wdrożenie kontenera w klastrze AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="f79cb-185">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="f79cb-186">W takim przypadku potrzebny jest plik ( **. yml Deploy**), który zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="f79cb-186">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

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
        - name: mssample-services-app
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
> <span data-ttu-id="f79cb-187">Aby uzyskać więcej informacji na temat wdrażania przy użyciu usługi Kubernetes, zobacz:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="f79cb-187">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="f79cb-188">Teraz wszystko jest już prawie gotowe do wdrożenia przy użyciu **polecenia kubectl**, ale najpierw należy uzyskać poświadczenia do klastra AKS za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="f79cb-188">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Dane wyjściowe konsoli z powyższego polecenia: Scalono "MSSampleK8Cluster jako bieżący kontekst w/root/.Kube/config](media/getting-aks-credentials.png)

<span data-ttu-id="f79cb-190">**Rysunek 4-47**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-190">**Figure 4-47**.</span></span> <span data-ttu-id="f79cb-191">pobieranie poświadczeń</span><span class="sxs-lookup"><span data-stu-id="f79cb-191">getting credentials</span></span>

<span data-ttu-id="f79cb-192">Następnie użyj `kubectl create` polecenia, aby uruchomić wdrożenie.</span><span class="sxs-lookup"><span data-stu-id="f79cb-192">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Dane wyjściowe konsoli z powyższego polecenia: wdrożenie "mssamplesbook" zostało utworzone.](media/kubectl-create-command.png)

<span data-ttu-id="f79cb-195">**Rysunek 4-48**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-195">**Figure 4-48**.</span></span> <span data-ttu-id="f79cb-196">Wdróż w usłudze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f79cb-196">Deploy to Kubernetes</span></span>

<span data-ttu-id="f79cb-197">Po zakończeniu wdrażania można uzyskać dostęp do konsoli Kubernetes z lokalnym serwerem proxy, do którego można okresowo uzyskać dostęp za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="f79cb-197">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="f79cb-198">I uzyskując dostęp `http://127.0.0.1:8001`do adresu URL.</span><span class="sxs-lookup"><span data-stu-id="f79cb-198">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Widok przeglądarki pulpitu nawigacyjnego Kubernetes, przedstawiający wdrożenia, zbiory, zestawy replik i usługi.](media/kubernetes-cluster-information.png)

<span data-ttu-id="f79cb-200">**Rysunek 4-49**.</span><span class="sxs-lookup"><span data-stu-id="f79cb-200">**Figure 4-49**.</span></span> <span data-ttu-id="f79cb-201">Wyświetlanie informacji o klastrze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f79cb-201">View Kubernetes cluster information</span></span>

<span data-ttu-id="f79cb-202">Teraz aplikacja została wdrożona na platformie Azure, przy użyciu kontenera systemu Linux i klastra AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="f79cb-202">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="f79cb-203">Możesz uzyskać dostęp do przeglądania aplikacji w publicznym adresie IP usługi, którą można uzyskać z Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="f79cb-203">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="f79cb-204">Aby dowiedzieć się, jak utworzyć klaster AKS dla tego przykładu, w sekcji [**wdrażanie w usłudze Azure Kubernetes Service (AKS)** ](deploy-azure-kubernetes-service.md) w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="f79cb-204">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f79cb-205">[Poprzedni](set-up-windows-containers-with-powershell.md)Następny
>[](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="f79cb-205">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
