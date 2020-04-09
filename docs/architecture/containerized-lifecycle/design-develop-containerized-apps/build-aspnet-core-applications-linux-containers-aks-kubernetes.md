---
title: Tworzenie aplikacji core ASP.NET 2.2 wdrożonych jako kontenery systemu Linux w klastrach AKS/Kubernetes
description: Cykl życia konteneryzowanych aplikacji platformy Docker korzystających z platformy i narzędzi firmy Microsoft
ms.date: 02/25/2019
ms.openlocfilehash: 83d4d0a60db4bdc112bb35bfbf61c0396646ad31
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989028"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="6a467-103">Tworzenie aplikacji core ASP.NET core 2.2 wdrożonych jako kontenery Systemu Linux w aranżatorze AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="6a467-103">Build ASP.NET Core 2.2 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="6a467-104">Usługi Kubernetes platformy Azure (AKS) to zarządzane przez platformę Azure usługi aranżacji Kubernetes, które upraszczają wdrażanie kontenerów i zarządzanie nimi.</span><span class="sxs-lookup"><span data-stu-id="6a467-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="6a467-105">Główne funkcje AKS to:</span><span class="sxs-lookup"><span data-stu-id="6a467-105">AKS main features are:</span></span>

- <span data-ttu-id="6a467-106">Płaszczyzna sterowania hostowana na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="6a467-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="6a467-107">Automatyczne uaktualnienia</span><span class="sxs-lookup"><span data-stu-id="6a467-107">Automated upgrades</span></span>
- <span data-ttu-id="6a467-108">mechanizm samonaprawiania</span><span class="sxs-lookup"><span data-stu-id="6a467-108">Self-healing</span></span>
- <span data-ttu-id="6a467-109">Skalowanie konfigurowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="6a467-109">User configurable scaling</span></span>
- <span data-ttu-id="6a467-110">Prostsze środowisko użytkownika dla deweloperów i operatorów klastrów.</span><span class="sxs-lookup"><span data-stu-id="6a467-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="6a467-111">Poniższe przykłady eksplorują tworzenie aplikacji ASP.NET Core 2.2, która działa w systemie Linux i wdraża w klastrze AKS na platformie Azure, podczas tworzenia odbywa się przy użyciu programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="6a467-111">The following examples explore the creation of an ASP.NET Core 2.2 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a><span data-ttu-id="6a467-112">Tworzenie projektu ASP.NET Core 2.2 przy użyciu programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="6a467-112">Creating the ASP.NET Core 2.2 Project using Visual Studio 2017</span></span>

<span data-ttu-id="6a467-113">ASP.NET Core to uniwersalna platforma programistyzawę utrzymywana przez firmę Microsoft i społeczność .NET w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="6a467-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="6a467-114">Jest wieloplatformowy, obsługuje systemy Windows, macOS i Linux i może być używany w scenariuszach urządzeń, chmury i osadzonych/IoT.</span><span class="sxs-lookup"><span data-stu-id="6a467-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="6a467-115">W tym przykładzie użyto prostego projektu, który jest oparty na szablonie interfejsu API sieci Web programu Visual Studio, więc nie potrzebujesz dodatkowej wiedzy do utworzenia przykładu.</span><span class="sxs-lookup"><span data-stu-id="6a467-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="6a467-116">Projekt należy utworzyć tylko przy użyciu standardowego szablonu, który zawiera wszystkie elementy do uruchomienia małego projektu za pomocą interfejsu API REST przy użyciu technologii ASP.NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="6a467-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.2 technology.</span></span>

![Dodaj nowe okno projektu w programie Visual Studio, wybierając ASP.NET podstawową aplikację sieci Web.](media/create-aspnet-core-application.png)

<span data-ttu-id="6a467-118">**Rysunek 4-36**.</span><span class="sxs-lookup"><span data-stu-id="6a467-118">**Figure 4-36**.</span></span> <span data-ttu-id="6a467-119">Tworzenie ASP.NET podstawowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="6a467-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="6a467-120">Aby utworzyć przykładowy projekt w programie Visual Studio, wybierz **pozycję Plik** > **nowego** > **projektu**, wybierz typy projektów sieci **Web** w lewym okienku, a następnie **ASP.NET podstawową aplikację sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="6a467-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="6a467-121">Visual Studio wyświetla szablony projektów sieci web.</span><span class="sxs-lookup"><span data-stu-id="6a467-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="6a467-122">W naszym przykładzie wybierz **interfejs API,** aby utworzyć ASP.NET aplikacji interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6a467-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="6a467-123">Sprawdź, czy wybrano ASP.NET Core 2.2 jako strukturę.</span><span class="sxs-lookup"><span data-stu-id="6a467-123">Verify that you've selected ASP.NET Core 2.2 as the framework.</span></span> <span data-ttu-id="6a467-124">Program .NET Core 2.2 znajduje się w ostatniej wersji programu Visual Studio 2017 i jest automatycznie instalowany i konfigurowany podczas instalowania programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="6a467-124">.NET Core 2.2 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![Okno dialogowe programu Visual Studio do wybierania typu ASP.NET podstawowej aplikacji sieci Web z wybraną opcją interfejsu API.](media/create-web-api-application.png)

<span data-ttu-id="6a467-126">**Rysunek 4-37**.</span><span class="sxs-lookup"><span data-stu-id="6a467-126">**Figure 4-37**.</span></span> <span data-ttu-id="6a467-127">Wybieranie ASP.NET typu projektu CORE 2.2 i Web API</span><span class="sxs-lookup"><span data-stu-id="6a467-127">Selecting ASP.NET CORE 2.2 and Web API project type</span></span>

<span data-ttu-id="6a467-128">Jeśli masz jakąś poprzednią wersję programu .NET Core, możesz pobrać <https://dotnet.microsoft.com/download>i zainstalować wersję 2.2 z .</span><span class="sxs-lookup"><span data-stu-id="6a467-128">If you have any previous version of .NET Core, you can download and install the 2.2 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="6a467-129">Można dodać obsługę platformy Docker podczas tworzenia projektu lub później, dzięki czemu można "Dockerize" projektu w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="6a467-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="6a467-130">Aby dodać obsługę platformy Docker po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz polecenie **Dodaj** > **obsługę platformy Docker** w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="6a467-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Opcja menu kontekstowego, aby dodać obsługę platformy Docker do istniejącego projektu: kliknij prawym przyciskiem myszy (na projekcie) > Dodaj > docker support.](media/add-docker-support-to-project.png)

<span data-ttu-id="6a467-132">**Rysunek 4-38**.</span><span class="sxs-lookup"><span data-stu-id="6a467-132">**Figure 4-38**.</span></span> <span data-ttu-id="6a467-133">Dodawanie obsługi platformy Docker do istniejącego projektu</span><span class="sxs-lookup"><span data-stu-id="6a467-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="6a467-134">Aby zakończyć dodawanie obsługi platformy Docker, można wybrać system Windows lub Linux.</span><span class="sxs-lookup"><span data-stu-id="6a467-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="6a467-135">W takim przypadku wybierz **Linux**, ponieważ AKS nie obsługuje kontenerów systemu Windows (od końca 2018 r.).</span><span class="sxs-lookup"><span data-stu-id="6a467-135">In this case, select **Linux**, because AKS doesn't support Windows Containers (as of late 2018).</span></span>

![Okno dialogowe Opcji, aby wybrać docelowy system operacyjny dla pliku dockerfile.](media/select-linux-docker-support.png)

<span data-ttu-id="6a467-137">**Rysunek 4-39**.</span><span class="sxs-lookup"><span data-stu-id="6a467-137">**Figure 4-39**.</span></span> <span data-ttu-id="6a467-138">Wybieranie kontenerów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="6a467-138">Selecting Linux containers.</span></span>

<span data-ttu-id="6a467-139">Dzięki tym prostym krokom masz aplikację ASP.NET Core 2.2 działającą na kontenerze systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="6a467-139">With these simple steps, you have your ASP.NET Core 2.2 application running on a Linux container.</span></span>

<span data-ttu-id="6a467-140">Jak widać integracja między programem Visual Studio 2017 i docker jest całkowicie zorientowana na produktywność dewelopera.</span><span class="sxs-lookup"><span data-stu-id="6a467-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer's productivity.</span></span>

<span data-ttu-id="6a467-141">Teraz możesz uruchomić aplikację za pomocą klawisza **F5** lub za pomocą przycisku **Odtwórz.**</span><span class="sxs-lookup"><span data-stu-id="6a467-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="6a467-142">Po uruchomieniu projektu można wyświetlić listę `docker images` obrazów za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="6a467-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="6a467-143">Powinien zostać `mssampleapplication` wyświetlony obraz utworzony przez automatyczne wdrożenie naszego projektu za pomocą programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="6a467-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Dane wyjściowe konsoli z polecenia obrazy platformy docker, pokazuje listę z: Repozytorium, Tag, Identyfikator obrazu, Utworzony (data) i Rozmiar.](media/docker-images-command.png)

<span data-ttu-id="6a467-145">**Rysunek 4-40**.</span><span class="sxs-lookup"><span data-stu-id="6a467-145">**Figure 4-40**.</span></span> <span data-ttu-id="6a467-146">Wyświetlanie obrazów platformy Docker</span><span class="sxs-lookup"><span data-stu-id="6a467-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="6a467-147">Zarejestruj rozwiązanie w rejestrze kontenerów platformy Azure</span><span class="sxs-lookup"><span data-stu-id="6a467-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="6a467-148">Przekaż obraz do dowolnego rejestru platformy Docker, takiego jak [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) lub Docker Hub, aby obrazy można było wdrożyć w klastrze AKS z tego rejestru.</span><span class="sxs-lookup"><span data-stu-id="6a467-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="6a467-149">W takim przypadku przekazujemy obraz do rejestru kontenerów platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="6a467-149">In this case, we're uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="6a467-150">Tworzenie obrazu w trybie wydania</span><span class="sxs-lookup"><span data-stu-id="6a467-150">Create the image in Release mode</span></span>

<span data-ttu-id="6a467-151">Teraz utworzymy obraz w trybie **wydania** (gotowy do produkcji), zmieniając na **Release**, jak pokazano na rysunku 4-41, i uruchamiając aplikację tak jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="6a467-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![Opcja paska narzędzi w programie VS do tworzenia w trybie zwalniania.](media/select-release-mode.png)

<span data-ttu-id="6a467-153">**Rysunek 4-41**.</span><span class="sxs-lookup"><span data-stu-id="6a467-153">**Figure 4-41**.</span></span> <span data-ttu-id="6a467-154">Wybór trybu zwalniania</span><span class="sxs-lookup"><span data-stu-id="6a467-154">Selecting Release Mode</span></span>

<span data-ttu-id="6a467-155">Jeśli wykonasz `docker image` polecenie, zobaczysz oba utworzone obrazy, `debug` jeden dla, a drugi dla `release` trybu.</span><span class="sxs-lookup"><span data-stu-id="6a467-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="6a467-156">Tworzenie nowego znacznika dla obrazu</span><span class="sxs-lookup"><span data-stu-id="6a467-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="6a467-157">Każdy obraz kontenera musi być `loginServer` oznaczony nazwą rejestru.</span><span class="sxs-lookup"><span data-stu-id="6a467-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="6a467-158">Ten tag jest używany na potrzeby kierowania podczas wypychania obrazów kontenerów do rejestru obrazów.</span><span class="sxs-lookup"><span data-stu-id="6a467-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="6a467-159">Możesz wyświetlić `loginServer` nazwę z witryny Azure portal, biorąc informacje z rejestru kontenerów platformy Azure</span><span class="sxs-lookup"><span data-stu-id="6a467-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Widok przeglądarki nazwy rejestru kontenerów platformy Azure w prawym górnym rogu.](media/loginServer-name.png)

<span data-ttu-id="6a467-161">**Rysunek 4-42**.</span><span class="sxs-lookup"><span data-stu-id="6a467-161">**Figure 4-42**.</span></span> <span data-ttu-id="6a467-162">Widok nazwy rejestru</span><span class="sxs-lookup"><span data-stu-id="6a467-162">View of the name of the Registry</span></span>

<span data-ttu-id="6a467-163">Lub uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="6a467-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Wyjście konsoli z powyższego polecenia.](media/az-cli-loginServer-name.png)

<span data-ttu-id="6a467-165">**Rysunek 4-43**.</span><span class="sxs-lookup"><span data-stu-id="6a467-165">**Figure 4-43**.</span></span> <span data-ttu-id="6a467-166">Pobierz nazwę rejestru przy użyciu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a467-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="6a467-167">W obu przypadkach otrzymasz nazwę.</span><span class="sxs-lookup"><span data-stu-id="6a467-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="6a467-168">W naszym `mssampleacr.azurecr.io`przykładzie .</span><span class="sxs-lookup"><span data-stu-id="6a467-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="6a467-169">Teraz możesz oznaczyć obraz, biorąc najnowszy obraz (release image), za pomocą polecenia:</span><span class="sxs-lookup"><span data-stu-id="6a467-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="6a467-170">Po uruchomieniu `docker tag` polecenia wymień `docker images` obrazy za pomocą polecenia, a obraz powinien być widoczny z nowym tagiem.</span><span class="sxs-lookup"><span data-stu-id="6a467-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Dane wyjściowe konsoli z polecenia obrazy platformy docker.](media/tagged-docker-images-list.png)

<span data-ttu-id="6a467-172">**Rysunek 4-44**.</span><span class="sxs-lookup"><span data-stu-id="6a467-172">**Figure 4-44**.</span></span> <span data-ttu-id="6a467-173">Wyświetlanie oznakowanych obrazów</span><span class="sxs-lookup"><span data-stu-id="6a467-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="6a467-174">Wypychanie obrazu do usługi Azure ACR</span><span class="sxs-lookup"><span data-stu-id="6a467-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="6a467-175">Zaloguj się do rejestru kontenerów platformy Azure</span><span class="sxs-lookup"><span data-stu-id="6a467-175">Log in to the Azure Container Registry</span></span>

```console
az acr login --name mssampleacr
```

<span data-ttu-id="6a467-176">Wypchnij obraz do usługi Azure ACR, używając następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="6a467-176">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="6a467-177">To polecenie zajmuje trochę czasu przekazywania obrazów, ale daje opinię w procesie.</span><span class="sxs-lookup"><span data-stu-id="6a467-177">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Dane wyjściowe konsoli z polecenia wypychania docker: pokazuje pasek postępu oparty na znakach dla każdej warstwy.](media/uploading-image-to-acr.png)

<span data-ttu-id="6a467-179">**Rysunek 4-45**.</span><span class="sxs-lookup"><span data-stu-id="6a467-179">**Figure 4-45**.</span></span> <span data-ttu-id="6a467-180">Przesyłanie obrazu do ACR</span><span class="sxs-lookup"><span data-stu-id="6a467-180">Uploading the image to the ACR</span></span>

<span data-ttu-id="6a467-181">Poniżej możesz zobaczyć wynik, który powinieneś uzyskać po zakończeniu procesu:</span><span class="sxs-lookup"><span data-stu-id="6a467-181">You can see below the result you should get when the process completes:</span></span>

![Wyjście konsoli z polecenia wypychania platformy docker, zakończone, pokazujące wszystkie warstwy lub węzły.](media/uploading-docker-images-complete.png)

<span data-ttu-id="6a467-183">**Rysunek 4-46**.</span><span class="sxs-lookup"><span data-stu-id="6a467-183">**Figure 4-46**.</span></span> <span data-ttu-id="6a467-184">Widok węzłów</span><span class="sxs-lookup"><span data-stu-id="6a467-184">View of nodes</span></span>

<span data-ttu-id="6a467-185">Następnym krokiem jest wdrożenie kontenera w klastrze usługi AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="6a467-185">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="6a467-186">W tym celu potrzebny jest plik (**.yml deploy file**), który zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="6a467-186">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

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
> <span data-ttu-id="6a467-187">Aby uzyskać więcej informacji na temat wdrażania za pomocą narzędzia Kubernetes, zobacz:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="6a467-187">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="6a467-188">Teraz jesteś prawie gotowy do wdrożenia przy użyciu **Kubectl**, ale najpierw musisz uzyskać poświadczenia do klastra AKS za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="6a467-188">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Wyjście konsoli z powyższego polecenia: Scalone "MSSampleK8Cluster jako bieżący kontekst w /root/.kube/config](media/getting-aks-credentials.png)

<span data-ttu-id="6a467-190">**Rysunek 4-47**.</span><span class="sxs-lookup"><span data-stu-id="6a467-190">**Figure 4-47**.</span></span> <span data-ttu-id="6a467-191">uzyskiwanie poświadczeń</span><span class="sxs-lookup"><span data-stu-id="6a467-191">getting credentials</span></span>

<span data-ttu-id="6a467-192">Następnie użyj `kubectl create` polecenia, aby uruchomić wdrożenie.</span><span class="sxs-lookup"><span data-stu-id="6a467-192">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Dane wyjściowe konsoli z powyższego polecenia: utworzone wdrożenie "mssamplesbook".](media/kubectl-create-command.png)

<span data-ttu-id="6a467-195">**Rysunek 4-48**.</span><span class="sxs-lookup"><span data-stu-id="6a467-195">**Figure 4-48**.</span></span> <span data-ttu-id="6a467-196">Wdrażanie na platformie Kubernetes</span><span class="sxs-lookup"><span data-stu-id="6a467-196">Deploy to Kubernetes</span></span>

<span data-ttu-id="6a467-197">Po zakończeniu wdrażania można uzyskać dostęp do konsoli Kubernetes za pomocą lokalnego serwera proxy, do którego można czasowo uzyskiwać dostęp za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="6a467-197">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="6a467-198">I dostęp do `http://127.0.0.1:8001`adresu URL .</span><span class="sxs-lookup"><span data-stu-id="6a467-198">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Widok przeglądarki pulpitu nawigacyjnego usługi Kubernetes, przedstawiający wdrożenia, zasobniki, zestawy replik i usługi.](media/kubernetes-cluster-information.png)

<span data-ttu-id="6a467-200">**Rysunek 4-49**.</span><span class="sxs-lookup"><span data-stu-id="6a467-200">**Figure 4-49**.</span></span> <span data-ttu-id="6a467-201">Wyświetlanie informacji klastra kubernetes</span><span class="sxs-lookup"><span data-stu-id="6a467-201">View Kubernetes cluster information</span></span>

<span data-ttu-id="6a467-202">Teraz masz aplikację wdrożoną na platformie Azure, przy użyciu kontenera systemu Linux i klastra Kubernetes AKS.</span><span class="sxs-lookup"><span data-stu-id="6a467-202">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="6a467-203">Dostęp do przeglądania aplikacji można uzyskać na publicznym adresie IP usługi, który można uzyskać z witryny Azure portal.</span><span class="sxs-lookup"><span data-stu-id="6a467-203">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="6a467-204">W tym przewodniku możesz zobaczyć, jak utworzyć klaster AKS dla tego przykładu w sekcji [**Wdrażanie w usłudze Azure Kubernetes Service (AKS).**](deploy-azure-kubernetes-service.md)</span><span class="sxs-lookup"><span data-stu-id="6a467-204">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6a467-205">[Poprzedni](set-up-windows-containers-with-powershell.md)
>[następny](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="6a467-205">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
