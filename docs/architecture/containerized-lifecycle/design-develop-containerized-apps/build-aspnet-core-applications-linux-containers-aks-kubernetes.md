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
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Tworzenie ASP.NET aplikacji Core 2.2 wdrożonych jako kontenery systemu Linux w koordynatorze AKS/Kubernetes

Usługi Azure Kubernetes (AKS) to zarządzane przez platformę Azure usługi aranżacji kubernetes, które upraszczają wdrażanie kontenerów i zarządzanie nimi.

Główne cechy AKS to:

- Płaszczyzna sterowania hostowana przez platformę Azure
- Automatyczne uaktualnienia
- mechanizm samonaprawiania
- Skalowanie konfigurowalne przez użytkownika
- Prostsze środowisko użytkownika zarówno dla deweloperów, jak i operatorów klastrów.

W poniższych przykładach eksploruj tworzenie aplikacji ASP.NET Core 2.2, która działa w systemie Linux i wdraża w klastrze Usługi AKS na platformie Azure, podczas gdy programowanie odbywa się przy użyciu programu Visual Studio 2017.

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a>Tworzenie projektu ASP.NET Core 2.2 przy użyciu programu Visual Studio 2017

ASP.NET Core to platforma deweloperska ogólnego przeznaczenia obsługiwana przez firmę Microsoft i społeczność .NET w usłudze GitHub. Jest wieloplatformowy, obsługuje systemy Windows, macOS i Linux i może być używany w scenariuszach urządzeń, chmury i osadzonych/IoT.

W tym przykładzie użyto prostego projektu, który jest oparty na szablonie interfejsu API sieci Web programu Visual Studio, więc nie trzeba żadnej dodatkowej wiedzy, aby utworzyć przykład. Wystarczy utworzyć projekt przy użyciu standardowego szablonu, który zawiera wszystkie elementy do uruchomienia małego projektu z interfejsem API REST, przy użyciu technologii ASP.NET Core 2.2.

![Dodaj nowe okno projektu w programie Visual Studio, wybierając ASP.NET Core Web Application.](media/create-aspnet-core-application.png)

**Rysunek 4-36**. Tworzenie ASP.NET podstawowej aplikacji

Aby utworzyć przykładowy projekt w programie Visual Studio, wybierz **pozycję Nowy** > **New** > **projekt**pliku , wybierz typy projektów **sieci Web** w lewym okienku, a następnie ASP.NET **Podstawowa aplikacja sieci Web**.

Visual Studio wyświetla listę szablonów dla projektów sieci Web. W naszym przykładzie wybierz **interfejs API,** aby utworzyć ASP.NET aplikacji interfejsu API sieci Web.

Sprawdź, czy jako ramach wybrano ASP.NET Core 2.2. Program .NET Core 2.2 znajduje się w ostatniej wersji programu Visual Studio 2017 i jest automatycznie instalowany i konfigurowany podczas instalowania programu Visual Studio 2017.

![Okno dialogowe programu Visual Studio służące do wybierania typu ASP.NET podstawowej aplikacji sieci Web z wybraną opcją interfejsu API.](media/create-web-api-application.png)

**Rysunek 4-37**. Wybieranie ASP.NET core 2.2 i typu projektu interfejsu API sieci Web

Jeśli masz poprzednią wersję programu .NET Core, możesz pobrać i <https://dotnet.microsoft.com/download>zainstalować wersję 2.2 z programu .

Podczas tworzenia projektu lub później można dodać obsługę platformy Docker, aby w dowolnym momencie można było utworzyć "dockerize" projektu. Aby dodać obsługę platformy Docker po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz polecenie **Dodaj** > **obsługę platformy Docker** w menu kontekstowym.

![Opcja menu kontekstowego, aby dodać obsługę platformy Docker do istniejącego projektu: kliknij prawym przyciskiem myszy (w projekcie) > Dodaj > doplatformy.](media/add-docker-support-to-project.png)

**Rysunek 4-38**. Dodawanie obsługi platformy Docker do istniejącego projektu

Aby zakończyć dodawanie obsługi platformy Docker, można wybrać system Windows lub Linux. W takim przypadku wybierz **Linux**, ponieważ Usługa AKS nie obsługuje kontenerów systemu Windows (od końca 2018 r.).

![Okno dialogowe opcji, aby wybrać docelowy system operacyjny dla pliku Dockerfile.](media/select-linux-docker-support.png)

**Rysunek 4-39**. Wybór kontenerów Linuksa.

Dzięki tym prostym krokom masz ASP.NET aplikacji Core 2.2 uruchomionej w kontenerze systemu Linux.

Jak widać, integracja między programem Visual Studio 2017 i platformą Docker jest całkowicie zorientowana na produktywność dewelopera.

Teraz możesz uruchomić aplikację za pomocą klawisza **F5** lub za pomocą przycisku **Odtwórz.**

Po uruchomieniu projektu można wyświetlić listę `docker images` obrazów za pomocą polecenia. Powinien zostać `mssampleapplication` wyświetlony obraz utworzony przez automatyczne wdrożenie naszego projektu za pomocą programu Visual Studio 2017.

```console
docker images
```

![Dane wyjściowe konsoli z polecenia docker images, pokazuje listę z: Repozytorium, Tag, Identyfikator obrazu, Utworzone (data) i Rozmiar.](media/docker-images-command.png)

**Rysunek 4-40**. Wyświetlanie obrazów platformy Docker

## <a name="register-the-solution-in-the-azure-container-registry"></a>Rejestrowanie rozwiązania w rejestrze kontenerów platformy Azure

Przekaż obraz do dowolnego rejestru platformy Docker, takiego jak [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) lub Docker Hub, aby obrazy można było wdrożyć w klastrze Usługi AKS z tego rejestru. W takim przypadku przekazujemy obraz do rejestru kontenerów platformy Azure.

### <a name="create-the-image-in-release-mode"></a>Tworzenie obrazu w trybie zwalniania

Teraz utworzymy obraz w trybie **wydania** (gotowy do produkcji), zmieniając się na **Release**, jak pokazano na rysunku 4-41, i uruchamiając aplikację tak, jak poprzednio.

![Opcja paska narzędzi w vs do tworzenia w trybie wydania.](media/select-release-mode.png)

**Rysunek 4-41**. Wybieranie trybu wydania

Jeśli wykonasz `docker image` polecenie, zobaczysz oba obrazy utworzone, jeden dla, `debug` a drugi dla `release` trybu.

### <a name="create-a-new-tag-for-the-image"></a>Tworzenie nowego tagu dla obrazu

Każdy obraz kontenera musi być `loginServer` oznaczony nazwą rejestru. Ten tag jest używany na potrzeby kierowania podczas wypychania obrazów kontenerów do rejestru obrazów.

Można wyświetlić `loginServer` nazwę z witryny Azure portal, biorąc informacje z rejestru kontenerów platformy Azure

![Widok przeglądarki nazwy rejestru kontenera platformy Azure w prawym górnym rogu.](media/loginServer-name.png)

**Rysunek 4-42**. Widok nazwy rejestru

Lub uruchamiając następujące polecenie:

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Wyjście konsoli z powyższego polecenia.](media/az-cli-loginServer-name.png)

**Rysunek 4-43**. Pobierz nazwę rejestru przy użyciu programu PowerShell

W obu przypadkach otrzymasz nazwę. W naszym `mssampleacr.azurecr.io`przykładzie .

Teraz możesz oznaczyć obraz, robiąc najnowszy obraz (obraz z wersji), za pomocą polecenia:

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Po uruchomieniu `docker tag` polecenia wymień obrazy za pomocą `docker images` polecenia, a obraz powinien być wyświetlony z nowym tagiem.

![Dane wyjściowe konsoli z polecenia docker images.](media/tagged-docker-images-list.png)

**Rysunek 4-44**. Widok oznakowanych obrazów

### <a name="push-the-image-into-the-azure-acr"></a>Wypchnij obraz do usługi Azure ACR

Zaloguj się do rejestru kontenerów platformy Azure

```console
az acr login --name mssampleacr
```

Wypchnij obraz do usługi Azure ACR, używając następującego polecenia:

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

To polecenie zajmuje trochę czasu, przesyłając obrazy, ale daje opinię w procesie.

![Dane wyjściowe konsoli z polecenia wypychania platformy dokującej: pokazuje pasek postępu oparty na znakach dla każdej warstwy.](media/uploading-image-to-acr.png)

**Rysunek 4-45**. Przesyłanie obrazu do acr

Poniżej możesz zobaczyć wynik, który powinieneś uzyskać po zakończeniu procesu:

![Dane wyjściowe konsoli z polecenia wypychania dok, zakończone, pokazujące wszystkie warstwy lub węzły.](media/uploading-docker-images-complete.png)

**Rysunek 4-46**. Widok węzłów

Następnym krokiem jest wdrożenie kontenera w klastrze AKS Kubernetes. W tym celu potrzebny jest plik **(plik wdrażania yml),** który zawiera następujące elementy:

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
> Aby uzyskać więcej informacji na temat wdrażania z Kubernetes zobacz:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

Teraz możesz być prawie gotowy do wdrożenia przy użyciu **Kubectl**, ale najpierw musisz uzyskać poświadczenia do klastra AKS za pomocą tego polecenia:

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Dane wyjściowe konsoli z powyższego polecenia: Scalono "MSSampleK8Cluster jako bieżący kontekst w /root/.kube/config](media/getting-aks-credentials.png)

**Rysunek 4-47**. uzyskiwanie poświadczeń

Następnie użyj `kubectl create` polecenia, aby uruchomić wdrożenie.

```console
kubectl create -f mssample-deploy.yml
```

![Wyjście konsoli z powyższego polecenia: utworzono wdrożenie "mssamplesbook". usługa "mssample-kub-app" utworzona.](media/kubectl-create-command.png)

**Rysunek 4-48**. Wdrażanie na platformie Kubernetes

Po zakończeniu wdrażania można uzyskać dostęp do konsoli Kubernetes za pomocą lokalnego serwera proxy, do którego można uzyskać dostęp w czasie za pomocą tego polecenia:

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

I dostęp do `http://127.0.0.1:8001`adresu URL .

![Widok przeglądarki pulpitu nawigacyjnego Kubernetes, pokazujący wdrożenia, zasobniki, zestawy replik i usługi.](media/kubernetes-cluster-information.png)

**Rysunek 4-49**. Wyświetlanie informacji o klastrze Kubernetes

Teraz masz aplikację wdrożoną na platformie Azure przy użyciu kontenera systemu Linux i klastra Kubernetes AKS. Możesz uzyskać dostęp do przeglądania aplikacji do publicznego adresu IP usługi, który można uzyskać z witryny Azure portal.

> [!NOTE]
> Możesz zobaczyć, jak utworzyć klaster AKS dla tego przykładu w sekcji [**Wdrażanie usługi Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) w tym przewodniku.

>[!div class="step-by-step"]
>[Poprzedni](set-up-windows-containers-with-powershell.md)
>[następny](../docker-devops-workflow/index.md)
