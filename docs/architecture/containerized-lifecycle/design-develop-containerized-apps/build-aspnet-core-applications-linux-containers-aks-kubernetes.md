---
title: Tworzenie ASP.NET aplikacji Core 2.2 wdrożonych jako kontenery systemu Linux w klastrach AKS/Kubernetes
description: Cykl życia konteneryzowanych aplikacji platformy Docker korzystających z platformy i narzędzi firmy Microsoft
ms.date: 02/25/2019
ms.openlocfilehash: ab64a0423ceceb8285c159af276d6d97e12379d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70848754"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="c4b96-103">Tworzenie ASP.NET aplikacji Core 2.2 wdrożonych jako kontenery systemu Linux w koordynatorze AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="c4b96-103">Build ASP.NET Core 2.2 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="c4b96-104">Usługi Azure Kubernetes (AKS) to zarządzane przez platformę Azure usługi aranżacji kubernetes, które upraszczają wdrażanie kontenerów i zarządzanie nimi.</span><span class="sxs-lookup"><span data-stu-id="c4b96-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="c4b96-105">Główne cechy AKS to:</span><span class="sxs-lookup"><span data-stu-id="c4b96-105">AKS main features are:</span></span>

- <span data-ttu-id="c4b96-106">Płaszczyzna sterowania hostowana przez platformę Azure</span><span class="sxs-lookup"><span data-stu-id="c4b96-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="c4b96-107">Automatyczne uaktualnienia</span><span class="sxs-lookup"><span data-stu-id="c4b96-107">Automated upgrades</span></span>
- <span data-ttu-id="c4b96-108">mechanizm samonaprawiania</span><span class="sxs-lookup"><span data-stu-id="c4b96-108">Self-healing</span></span>
- <span data-ttu-id="c4b96-109">Skalowanie konfigurowalne przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="c4b96-109">User configurable scaling</span></span>
- <span data-ttu-id="c4b96-110">Prostsze środowisko użytkownika zarówno dla deweloperów, jak i operatorów klastrów.</span><span class="sxs-lookup"><span data-stu-id="c4b96-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="c4b96-111">W poniższych przykładach eksploruj tworzenie aplikacji ASP.NET Core 2.2, która działa w systemie Linux i wdraża w klastrze Usługi AKS na platformie Azure, podczas gdy programowanie odbywa się przy użyciu programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c4b96-111">The following examples explore the creation of an ASP.NET Core 2.2 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a><span data-ttu-id="c4b96-112">Tworzenie projektu ASP.NET Core 2.2 przy użyciu programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c4b96-112">Creating the ASP.NET Core 2.2 Project using Visual Studio 2017</span></span>

<span data-ttu-id="c4b96-113">ASP.NET Core to platforma deweloperska ogólnego przeznaczenia obsługiwana przez firmę Microsoft i społeczność .NET w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="c4b96-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="c4b96-114">Jest wieloplatformowy, obsługuje systemy Windows, macOS i Linux i może być używany w scenariuszach urządzeń, chmury i osadzonych/IoT.</span><span class="sxs-lookup"><span data-stu-id="c4b96-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="c4b96-115">W tym przykładzie użyto prostego projektu, który jest oparty na szablonie interfejsu API sieci Web programu Visual Studio, więc nie trzeba żadnej dodatkowej wiedzy, aby utworzyć przykład.</span><span class="sxs-lookup"><span data-stu-id="c4b96-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="c4b96-116">Wystarczy utworzyć projekt przy użyciu standardowego szablonu, który zawiera wszystkie elementy do uruchomienia małego projektu z interfejsem API REST, przy użyciu technologii ASP.NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c4b96-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.2 technology.</span></span>

![Dodaj nowe okno projektu w programie Visual Studio, wybierając ASP.NET Core Web Application.](media/create-aspnet-core-application.png)

<span data-ttu-id="c4b96-118">**Rysunek 4-36**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-118">**Figure 4-36**.</span></span> <span data-ttu-id="c4b96-119">Tworzenie ASP.NET podstawowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="c4b96-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="c4b96-120">Aby utworzyć przykładowy projekt w programie Visual Studio, wybierz **pozycję Nowy** > **New** > **projekt**pliku , wybierz typy projektów **sieci Web** w lewym okienku, a następnie ASP.NET **Podstawowa aplikacja sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="c4b96-121">Visual Studio wyświetla listę szablonów dla projektów sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c4b96-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="c4b96-122">W naszym przykładzie wybierz **interfejs API,** aby utworzyć ASP.NET aplikacji interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c4b96-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="c4b96-123">Sprawdź, czy jako ramach wybrano ASP.NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c4b96-123">Verify that you've selected ASP.NET Core 2.2 as the framework.</span></span> <span data-ttu-id="c4b96-124">Program .NET Core 2.2 znajduje się w ostatniej wersji programu Visual Studio 2017 i jest automatycznie instalowany i konfigurowany podczas instalowania programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c4b96-124">.NET Core 2.2 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![Okno dialogowe programu Visual Studio służące do wybierania typu ASP.NET podstawowej aplikacji sieci Web z wybraną opcją interfejsu API.](media/create-web-api-application.png)

<span data-ttu-id="c4b96-126">**Rysunek 4-37**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-126">**Figure 4-37**.</span></span> <span data-ttu-id="c4b96-127">Wybieranie ASP.NET core 2.2 i typu projektu interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="c4b96-127">Selecting ASP.NET CORE 2.2 and Web API project type</span></span>

<span data-ttu-id="c4b96-128">Jeśli masz poprzednią wersję programu .NET Core, możesz pobrać i <https://dotnet.microsoft.com/download>zainstalować wersję 2.2 z programu .</span><span class="sxs-lookup"><span data-stu-id="c4b96-128">If you have any previous version of .NET Core, you can download and install the 2.2 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="c4b96-129">Podczas tworzenia projektu lub później można dodać obsługę platformy Docker, aby w dowolnym momencie można było utworzyć "dockerize" projektu.</span><span class="sxs-lookup"><span data-stu-id="c4b96-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="c4b96-130">Aby dodać obsługę platformy Docker po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz polecenie **Dodaj** > **obsługę platformy Docker** w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="c4b96-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Opcja menu kontekstowego, aby dodać obsługę platformy Docker do istniejącego projektu: kliknij prawym przyciskiem myszy (w projekcie) > Dodaj > doplatformy.](media/add-docker-support-to-project.png)

<span data-ttu-id="c4b96-132">**Rysunek 4-38**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-132">**Figure 4-38**.</span></span> <span data-ttu-id="c4b96-133">Dodawanie obsługi platformy Docker do istniejącego projektu</span><span class="sxs-lookup"><span data-stu-id="c4b96-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="c4b96-134">Aby zakończyć dodawanie obsługi platformy Docker, można wybrać system Windows lub Linux.</span><span class="sxs-lookup"><span data-stu-id="c4b96-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="c4b96-135">W takim przypadku wybierz **Linux**, ponieważ Usługa AKS nie obsługuje kontenerów systemu Windows (od końca 2018 r.).</span><span class="sxs-lookup"><span data-stu-id="c4b96-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Okno dialogowe opcji, aby wybrać docelowy system operacyjny dla pliku Dockerfile.](media/select-linux-docker-support.png)

<span data-ttu-id="c4b96-137">**Rysunek 4-39**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-137">**Figure 4-39**.</span></span> <span data-ttu-id="c4b96-138">Wybór kontenerów Linuksa.</span><span class="sxs-lookup"><span data-stu-id="c4b96-138">Selecting Linux containers.</span></span>

<span data-ttu-id="c4b96-139">Dzięki tym prostym krokom masz ASP.NET aplikacji Core 2.2 uruchomionej w kontenerze systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="c4b96-139">With these simple steps, you have your ASP.NET Core 2.2 application running on a Linux container.</span></span>

<span data-ttu-id="c4b96-140">Jak widać, integracja między programem Visual Studio 2017 i platformą Docker jest całkowicie zorientowana na produktywność dewelopera.</span><span class="sxs-lookup"><span data-stu-id="c4b96-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="c4b96-141">Teraz możesz uruchomić aplikację za pomocą klawisza **F5** lub za pomocą przycisku **Odtwórz.**</span><span class="sxs-lookup"><span data-stu-id="c4b96-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="c4b96-142">Po uruchomieniu projektu można wyświetlić listę `docker images` obrazów za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="c4b96-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="c4b96-143">Powinien zostać `mssampleapplication` wyświetlony obraz utworzony przez automatyczne wdrożenie naszego projektu za pomocą programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c4b96-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Dane wyjściowe konsoli z polecenia docker images, pokazuje listę z: Repozytorium, Tag, Identyfikator obrazu, Utworzone (data) i Rozmiar.](media/docker-images-command.png)

<span data-ttu-id="c4b96-145">**Rysunek 4-40**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-145">**Figure 4-40**.</span></span> <span data-ttu-id="c4b96-146">Wyświetlanie obrazów platformy Docker</span><span class="sxs-lookup"><span data-stu-id="c4b96-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="c4b96-147">Rejestrowanie rozwiązania w rejestrze kontenerów platformy Azure</span><span class="sxs-lookup"><span data-stu-id="c4b96-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="c4b96-148">Przekaż obraz do dowolnego rejestru platformy Docker, takiego jak [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) lub Docker Hub, aby obrazy można było wdrożyć w klastrze Usługi AKS z tego rejestru.</span><span class="sxs-lookup"><span data-stu-id="c4b96-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="c4b96-149">W takim przypadku przekazujemy obraz do rejestru kontenerów platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="c4b96-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="c4b96-150">Tworzenie obrazu w trybie zwalniania</span><span class="sxs-lookup"><span data-stu-id="c4b96-150">Create the image in Release mode</span></span>

<span data-ttu-id="c4b96-151">Teraz utworzymy obraz w trybie **wydania** (gotowy do produkcji), zmieniając się na **Release**, jak pokazano na rysunku 4-41, i uruchamiając aplikację tak, jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="c4b96-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![Opcja paska narzędzi w vs do tworzenia w trybie wydania.](media/select-release-mode.png)

<span data-ttu-id="c4b96-153">**Rysunek 4-41**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-153">**Figure 4-41**.</span></span> <span data-ttu-id="c4b96-154">Wybieranie trybu wydania</span><span class="sxs-lookup"><span data-stu-id="c4b96-154">Selecting Release Mode</span></span>

<span data-ttu-id="c4b96-155">Jeśli wykonasz `docker image` polecenie, zobaczysz oba obrazy utworzone, jeden dla, `debug` a drugi dla `release` trybu.</span><span class="sxs-lookup"><span data-stu-id="c4b96-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="c4b96-156">Tworzenie nowego tagu dla obrazu</span><span class="sxs-lookup"><span data-stu-id="c4b96-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="c4b96-157">Każdy obraz kontenera musi być `loginServer` oznaczony nazwą rejestru.</span><span class="sxs-lookup"><span data-stu-id="c4b96-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="c4b96-158">Ten tag jest używany na potrzeby kierowania podczas wypychania obrazów kontenerów do rejestru obrazów.</span><span class="sxs-lookup"><span data-stu-id="c4b96-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="c4b96-159">Można wyświetlić `loginServer` nazwę z witryny Azure portal, biorąc informacje z rejestru kontenerów platformy Azure</span><span class="sxs-lookup"><span data-stu-id="c4b96-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Widok przeglądarki nazwy rejestru kontenera platformy Azure w prawym górnym rogu.](media/loginServer-name.png)

<span data-ttu-id="c4b96-161">**Rysunek 4-42**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-161">**Figure 4-42**.</span></span> <span data-ttu-id="c4b96-162">Widok nazwy rejestru</span><span class="sxs-lookup"><span data-stu-id="c4b96-162">View of the name of the Registry</span></span>

<span data-ttu-id="c4b96-163">Lub uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c4b96-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Wyjście konsoli z powyższego polecenia.](media/az-cli-loginServer-name.png)

<span data-ttu-id="c4b96-165">**Rysunek 4-43**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-165">**Figure 4-43**.</span></span> <span data-ttu-id="c4b96-166">Pobierz nazwę rejestru przy użyciu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4b96-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="c4b96-167">W obu przypadkach otrzymasz nazwę.</span><span class="sxs-lookup"><span data-stu-id="c4b96-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="c4b96-168">W naszym `mssampleacr.azurecr.io`przykładzie .</span><span class="sxs-lookup"><span data-stu-id="c4b96-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="c4b96-169">Teraz możesz oznaczyć obraz, robiąc najnowszy obraz (obraz z wersji), za pomocą polecenia:</span><span class="sxs-lookup"><span data-stu-id="c4b96-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="c4b96-170">Po uruchomieniu `docker tag` polecenia wymień obrazy za pomocą `docker images` polecenia, a obraz powinien być wyświetlony z nowym tagiem.</span><span class="sxs-lookup"><span data-stu-id="c4b96-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Dane wyjściowe konsoli z polecenia docker images.](media/tagged-docker-images-list.png)

<span data-ttu-id="c4b96-172">**Rysunek 4-44**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-172">**Figure 4-44**.</span></span> <span data-ttu-id="c4b96-173">Widok oznakowanych obrazów</span><span class="sxs-lookup"><span data-stu-id="c4b96-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="c4b96-174">Wypchnij obraz do usługi Azure ACR</span><span class="sxs-lookup"><span data-stu-id="c4b96-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="c4b96-175">Zaloguj się do rejestru kontenerów platformy Azure</span><span class="sxs-lookup"><span data-stu-id="c4b96-175">Log in to the Azure Container Registry</span></span>

```console
az acr login --name mssampleacr
```

<span data-ttu-id="c4b96-176">Wypchnij obraz do usługi Azure ACR, używając następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c4b96-176">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="c4b96-177">To polecenie zajmuje trochę czasu, przesyłając obrazy, ale daje opinię w procesie.</span><span class="sxs-lookup"><span data-stu-id="c4b96-177">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Dane wyjściowe konsoli z polecenia wypychania platformy dokującej: pokazuje pasek postępu oparty na znakach dla każdej warstwy.](media/uploading-image-to-acr.png)

<span data-ttu-id="c4b96-179">**Rysunek 4-45**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-179">**Figure 4-45**.</span></span> <span data-ttu-id="c4b96-180">Przesyłanie obrazu do acr</span><span class="sxs-lookup"><span data-stu-id="c4b96-180">Uploading the image to the ACR</span></span>

<span data-ttu-id="c4b96-181">Poniżej możesz zobaczyć wynik, który powinieneś uzyskać po zakończeniu procesu:</span><span class="sxs-lookup"><span data-stu-id="c4b96-181">You can see below the result you should get when the process completes:</span></span>

![Dane wyjściowe konsoli z polecenia wypychania dok, zakończone, pokazujące wszystkie warstwy lub węzły.](media/uploading-docker-images-complete.png)

<span data-ttu-id="c4b96-183">**Rysunek 4-46**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-183">**Figure 4-46**.</span></span> <span data-ttu-id="c4b96-184">Widok węzłów</span><span class="sxs-lookup"><span data-stu-id="c4b96-184">View of nodes</span></span>

<span data-ttu-id="c4b96-185">Następnym krokiem jest wdrożenie kontenera w klastrze AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c4b96-185">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="c4b96-186">W tym celu potrzebny jest plik **(plik wdrażania yml),** który zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="c4b96-186">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

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
> <span data-ttu-id="c4b96-187">Aby uzyskać więcej informacji na temat wdrażania z Kubernetes zobacz:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="c4b96-187">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="c4b96-188">Teraz możesz być prawie gotowy do wdrożenia przy użyciu **Kubectl**, ale najpierw musisz uzyskać poświadczenia do klastra AKS za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c4b96-188">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Dane wyjściowe konsoli z powyższego polecenia: Scalono "MSSampleK8Cluster jako bieżący kontekst w /root/.kube/config](media/getting-aks-credentials.png)

<span data-ttu-id="c4b96-190">**Rysunek 4-47**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-190">**Figure 4-47**.</span></span> <span data-ttu-id="c4b96-191">uzyskiwanie poświadczeń</span><span class="sxs-lookup"><span data-stu-id="c4b96-191">getting credentials</span></span>

<span data-ttu-id="c4b96-192">Następnie użyj `kubectl create` polecenia, aby uruchomić wdrożenie.</span><span class="sxs-lookup"><span data-stu-id="c4b96-192">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Wyjście konsoli z powyższego polecenia: utworzono wdrożenie "mssamplesbook".](media/kubectl-create-command.png)

<span data-ttu-id="c4b96-195">**Rysunek 4-48**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-195">**Figure 4-48**.</span></span> <span data-ttu-id="c4b96-196">Wdrażanie na platformie Kubernetes</span><span class="sxs-lookup"><span data-stu-id="c4b96-196">Deploy to Kubernetes</span></span>

<span data-ttu-id="c4b96-197">Po zakończeniu wdrażania można uzyskać dostęp do konsoli Kubernetes za pomocą lokalnego serwera proxy, do którego można uzyskać dostęp w czasie za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c4b96-197">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="c4b96-198">I dostęp do `http://127.0.0.1:8001`adresu URL .</span><span class="sxs-lookup"><span data-stu-id="c4b96-198">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Widok przeglądarki pulpitu nawigacyjnego Kubernetes, pokazujący wdrożenia, zasobniki, zestawy replik i usługi.](media/kubernetes-cluster-information.png)

<span data-ttu-id="c4b96-200">**Rysunek 4-49**.</span><span class="sxs-lookup"><span data-stu-id="c4b96-200">**Figure 4-49**.</span></span> <span data-ttu-id="c4b96-201">Wyświetlanie informacji o klastrze Kubernetes</span><span class="sxs-lookup"><span data-stu-id="c4b96-201">View Kubernetes cluster information</span></span>

<span data-ttu-id="c4b96-202">Teraz masz aplikację wdrożoną na platformie Azure przy użyciu kontenera systemu Linux i klastra Kubernetes AKS.</span><span class="sxs-lookup"><span data-stu-id="c4b96-202">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="c4b96-203">Możesz uzyskać dostęp do przeglądania aplikacji do publicznego adresu IP usługi, który można uzyskać z witryny Azure portal.</span><span class="sxs-lookup"><span data-stu-id="c4b96-203">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="c4b96-204">Możesz zobaczyć, jak utworzyć klaster AKS dla tego przykładu w sekcji [**Wdrażanie usługi Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="c4b96-204">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c4b96-205">[Poprzedni](set-up-windows-containers-with-powershell.md)
>[następny](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="c4b96-205">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
