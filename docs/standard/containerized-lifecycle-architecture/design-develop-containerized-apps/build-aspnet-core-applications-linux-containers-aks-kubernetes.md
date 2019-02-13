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
# <a name="build-aspnet-core-21-applications-deployed-as-linux-containers-into-akskubernetes-orchestrator"></a>Tworzenie aplikacji platformy ASP.NET Core 2.1 wdrażane jako kontenery systemu Linux do programu orchestrator AKS/Kubernetes

Usługa Azure Kubernetes usługi (AKS) to usługi platformy Azure zarządzanego rozwiązania Kubernetes mechanizmów, które upraszczają wdrażanie kontenerów i zarządzanie nimi.

Główne funkcje usługi AKS to:

- Płaszczyznę sterowania hostowaną na platformie Azure
- Automatyczne uaktualnienia
- Samodzielnej naprawy.
- Użytkownika można skonfigurować skalowanie
- Prostsze środowisko użytkownika dla deweloperów i operatorów klastra.

Poniższe przykłady zapoznaj się z tworzenia aplikacji platformy ASP.NET Core 2.1, która działa w systemie Linux i wdraża klaster AKS na platformie Azure, podczas gdy projektowanie odbywa się przy użyciu programu Visual Studio 2017.

## <a name="creating-the-aspnet-core-21-project-using-visual-studio-2017"></a>Tworzenie projektu 2.1 platformy ASP.NET Core przy użyciu programu Visual Studio 2017

Platforma ASP.NET Core to platforma deweloperska ogólnego przeznaczenia obsługiwane przez firmę Microsoft i społeczności platformy .NET w witrynie GitHub. Jest dla wielu platform, obsługi Windows, macOS i Linux i mogą być używane w urządzeń, chmury i scenariuszach osadzonych IoT.

W tym przykładzie użyto prosty projekt oparty na podstawie interfejsu API sieci Web programu Visual Studio szablonu, więc nie potrzebujesz żadnej wiedzy dodatkowe do utworzenia przykładu. Musisz utworzyć projekt przy użyciu standardowego szablonu, który zawiera wszystkie elementy, aby uruchomić małych projektów za pomocą interfejsu API REST, przy użyciu technologii ASP.NET Core 2.1.

![Dodaj okno nowego projektu w programie Visual Studio, wybierając aplikację sieci Web programu ASP.NET Core.](media/create-aspnet-core-application.png)

**Rysunek 4-36**. Tworzenie aplikacji platformy ASP.NET Core

Aby utworzyć przykładowy projekt, musisz wybrać **pliku** > **New** > **projektu** w programie Visual Studio. A następnie pojawi się lista szablonów dla kilku typów projektów, których należy szukać **Web** > **platformy .NET Core** w panelu po lewej stronie. W tym przykładzie wybierz **aplikacji sieci Web programu ASP.NET Core**.

W następnym oknie dialogowym upewnij się, wybrane platformy .NET Core i ASP.NET Core 2.1 jako platformę docelową w górnym pulldowns, jak pokazano na rysunku 4-37, a następnie wybierz pozycję opcji interfejsu API, aby utworzyć aplikację internetowego interfejsu API platformy ASP.NET Core.

.NET Core 2.1 jest dostępne w ramach programu Visual Studio 2017, wersja 15.7.0 lub nowszej i zostanie automatycznie zainstalowany i skonfigurowany dla Ciebie, po wybraniu **programowanie dla wielu platform .NET Core** obciążenie podczas instalacji.

![Visual Studio okno dialogowe Wybieranie typu aplikacji sieci Web programu ASP.NET Core z wybraną opcją interfejsu API.](media/create-web-api-application.png)

**Rysunek 4-37**. Wybieranie platformy ASP.NET CORE 2.1 i interfejsu API sieci Web typu projektu

W przypadku poprzednich wersji programu .NET Core, można go pobrać i zainstalować wersja 2.1 z <https://www.microsoft.com/net/download/core#/sdk>.

Podczas tworzenia projektu w poprzednim kroku lub nowszy, jeśli zajdzie taka potrzeba, po uruchomieniu projektu można dodać obsługę platformy Docker. Aby dodać obsługę platformy Docker po utworzeniu projektu, kliknij prawym przyciskiem myszy plik projektu w **Eksploratora rozwiązań** i wybierz **Dodaj** > **obsługę platformy Docker** na menu kontekstowe.

![Opcja menu kontekstowego, aby dodać obsługę platformy Docker do istniejącego projektu: Kliknij prawym przyciskiem myszy (projekt) > Dodaj > obsługę platformy Docker.](media/add-docker-support-to-project.png)

**Rysunek 4-38**. Dodawanie obsługi platformy Docker do istniejącego projektu

Aby ukończyć dodawanie obsługę platformy Docker, użytkownik może Windows lub Linux. W takim przypadku wybierz **Linux**, ponieważ AKS nie obsługuje kontenery Windows (jako późnego 2018 r.).

![Okno dialogowe opcji aby wybrać docelowy system operacyjny do pliku Dockerfile.](media/select-linux-docker-support.png)

**Rysunek 4-39**. Wybieranie kontenerów systemu Linux.

Z tych prostych kroków będziesz mieć aplikacji platformy ASP.NET Core 2.1, uruchomionej w kontenerze systemu Linux.

Jak widać, integrację między usługą Visual Studio 2017 i platformy Docker jest całkowicie ukierunkowana na produktywność dla deweloperów.

Teraz możesz nacisnąć przycisk **F5** Aby skompilować i uruchomić aplikację.

Po uruchomieniu projektu, możesz wyświetlić listę obrazów przy użyciu `docker images` polecenia. Powinien zostać wyświetlony `mssampleapplication` obrazu utworzonego za pomocą automatycznego wdrażania naszej projektu programu Visual Studio 2017.

```console
docker images
```

![Konsola danych wyjściowych polecenia obrazów platformy docker, wyświetla listę przy użyciu: Repozytorium, tagów, identyfikator obrazu, utworzony (Data) i rozmiar.](media/docker-images-command.png)

**Rysunek 4 do 40**. Wyświetl obrazy platformy Docker

## <a name="register-the-solution-in-the-azure-container-registry"></a>Zarejestruj rozwiązania w usłudze Azure Container Registry

Przekazanie obrazu do dowolnego rejestru platformy Docker, takie jak [usługi Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) lub usługi Docker Hub, dzięki czemu obrazy, którą można wdrożyć klaster usługi AKS z tego rejestru. W tym przypadku firma Microsoft jest przekazywanie obrazu do usługi Azure Container Registry.

### <a name="create-the-image-in-release-mode"></a>Tworzenie obrazu w trybie przygotowania do wydania

Tworzenie obrazu w **wersji** zmiana trybu (gotowe do produkcji) do wersji, jak pokazano poniżej i naciśnij klawisz F5, aby uruchomić ponownie aplikację.

![Opcja narzędzi w programie VS można tworzyć w trybie wydania.](media/select-release-mode.png)

**Rysunek 4-41**. Wybierając tryb wersji

Jeśli zostanie wykonana `docker image` polecenia zostaną wyświetlone zarówno obrazy utworzone. Jeden dla `debug` i inne `release` trybu.

### <a name="create-a-new-tag-for-the-image"></a>Tworzenie nowego tagu obrazu

Każdy obraz kontenera musi być oznakowane za pomocą `loginServer` nazwa rejestru. Ten tag jest używany na potrzeby kierowania podczas wypychania obrazów kontenera do rejestru obrazów.

Możesz wyświetlić `loginServer` nazwa w witrynie Azure portal, korzystając z informacji od usługi Azure Container Registry

![Widok przeglądarki nazwy rejestru kontenerów platformy Azure, w prawym górnym rogu.](media/loginServer-name.png)

**Rysunek 4-42**. Wyświetl nazwę rejestru

Lub uruchamiając następujące polecenie:

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Konsola danych wyjściowych z powyższego polecenia.](media/az-cli-loginServer-name.png)

**Rysunek 4-43**. Pobierz nazwę rejestru przy użyciu programu PowerShell

W obu przypadkach będzie uzyskać nazwę. W naszym przykładzie `mssampleacr.azurecr.io`.

Teraz możesz oznaczyć obrazu, biorąc najnowszego obrazu (wersja obrazu), za pomocą następującego polecenia:

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Po uruchomieniu `docker tag` polecenia, listy obrazów za pomocą `docker images` polecenia. Powinien zostać wyświetlony obraz za pomocą nowego tagu.

![Dane wyjściowe z polecenia obrazów platformy docker z konsoli.](media/tagged-docker-images-list.png)

**Rysunek 4-44**. Wyświetlanie otagowanych obrazów

### <a name="push-the-image-into-the-azure-acr"></a>Wypychanie obrazu do rejestru Azure container Registry w platformie Azure

Wypychanie obrazu do usługi Azure ACR za pomocą następującego polecenia:

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

To polecenie wymaga pewnego czasu przesyłania obrazów, ale udostępnia informacje zwrotne w procesie.

![Dane wyjściowe polecenia docker push konsoli: Wyświetla pasek postępu opartego na znakach dla każdej warstwy.](media/uploading-image-to-acr.png)

**Rysunek 4-45**. Przekazywanie obrazu do usługi ACR

Można zobaczyć poniżej wynik, że powinna pojawić się po zakończeniu procesu:

![Dane wyjściowe z polecenia wypychania platformy docker, zakończone, przedstawiający wszystkie warstwy i węzły konsoli.](media/uploading-docker-images-complete.png)

**Rysunek 4-46**. Widok węzłów

Następnym krokiem jest do wdrożenia kontenera w klastrze AKS rozwiązania Kubernetes. Do tego niezbędny pliku (**yml wdrażanie pliku**), w tym przypadku zawiera:

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
> Aby uzyskać więcej informacji na temat wdrażania przy użyciu rozwiązania Kubernetes, zobacz: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

Teraz wszystko jest już niemal gotowa do wdrożenia przy użyciu **Kubectl**, ale najpierw należy uzyskać poświadczenia do klastra usługi AKS przy użyciu następującego polecenia:

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Dane wyjściowe z powyższego polecenia konsoli: Scalone MSSampleK8Cluster"jako bieżący kontekst w /root/.kube/config](media/getting-aks-credentials.png)

**Rysunek 4-47**. Uzyskiwanie poświadczeń

Następnie należy użyć `kubectl create` polecenie w celu uruchomienia wdrożenia.

```console
kubectl create -f mssample-deploy.yml
```

![Dane wyjściowe z powyższego polecenia konsoli: wdrożenia "mssamplesbook" utworzony. Usługa "mssample-kub-app" utworzony.](media/kubectl-create-command.png)

**Rysunek 4-48**. Wdrażanie rozwiązania Kubernetes

Po zakończeniu wdrożenia można uzyskiwać dostęp konsoli rozwiązania Kubernetes za pomocą lokalnego serwera proxy, która czasowo dostęp za pomocą tego polecenia:

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

I uzyskiwania dostępu do adresu url `http://127.0.0.1:8001`.

![Widok pulpitu nawigacyjnego rozwiązania Kubernetes, wyświetlanie wdrożeń, zasobników, zestawów replik i usługi w przeglądarce.](media/kubernetes-cluster-information.png)

**Rysunek 4-49**. Wyświetl informacje o klastrze Kubernetes

Masz teraz aplikacji wdrożonych na platformie Azure przy użyciu kontenera systemu Linux i klaster AKS rozwiązania Kubernetes. Możesz uzyskać dostęp do swojej aplikacji, przechodząc do publicznego adresu IP usługi, którą możesz pobrać z witryny Azure portal.

> [!NOTE]
> Możesz dowiedzieć się, jak do utworzenia klastra usługi AKS dla tego przykładu w sekcji [ **Wdróż na platformie Azure Kubernetes Service (AKS)** ](deploy-azure-kubernetes-service.md) w tym przewodniku.

>[!div class="step-by-step"]
>[Poprzednie](set-up-windows-containers-with-powershell.md)
>[dalej](../docker-devops-workflow/index.md)
