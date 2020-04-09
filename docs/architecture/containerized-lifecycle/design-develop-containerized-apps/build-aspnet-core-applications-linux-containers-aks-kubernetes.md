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
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Tworzenie aplikacji core ASP.NET core 2.2 wdrożonych jako kontenery Systemu Linux w aranżatorze AKS/Kubernetes

Usługi Kubernetes platformy Azure (AKS) to zarządzane przez platformę Azure usługi aranżacji Kubernetes, które upraszczają wdrażanie kontenerów i zarządzanie nimi.

Główne funkcje AKS to:

- Płaszczyzna sterowania hostowana na platformie Azure
- Automatyczne uaktualnienia
- mechanizm samonaprawiania
- Skalowanie konfigurowane przez użytkownika
- Prostsze środowisko użytkownika dla deweloperów i operatorów klastrów.

Poniższe przykłady eksplorują tworzenie aplikacji ASP.NET Core 2.2, która działa w systemie Linux i wdraża w klastrze AKS na platformie Azure, podczas tworzenia odbywa się przy użyciu programu Visual Studio 2017.

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a>Tworzenie projektu ASP.NET Core 2.2 przy użyciu programu Visual Studio 2017

ASP.NET Core to uniwersalna platforma programistyzawę utrzymywana przez firmę Microsoft i społeczność .NET w usłudze GitHub. Jest wieloplatformowy, obsługuje systemy Windows, macOS i Linux i może być używany w scenariuszach urządzeń, chmury i osadzonych/IoT.

W tym przykładzie użyto prostego projektu, który jest oparty na szablonie interfejsu API sieci Web programu Visual Studio, więc nie potrzebujesz dodatkowej wiedzy do utworzenia przykładu. Projekt należy utworzyć tylko przy użyciu standardowego szablonu, który zawiera wszystkie elementy do uruchomienia małego projektu za pomocą interfejsu API REST przy użyciu technologii ASP.NET Core 2.2.

![Dodaj nowe okno projektu w programie Visual Studio, wybierając ASP.NET podstawową aplikację sieci Web.](media/create-aspnet-core-application.png)

**Rysunek 4-36**. Tworzenie ASP.NET podstawowej aplikacji

Aby utworzyć przykładowy projekt w programie Visual Studio, wybierz **pozycję Plik** > **nowego** > **projektu**, wybierz typy projektów sieci **Web** w lewym okienku, a następnie **ASP.NET podstawową aplikację sieci Web**.

Visual Studio wyświetla szablony projektów sieci web. W naszym przykładzie wybierz **interfejs API,** aby utworzyć ASP.NET aplikacji interfejsu API sieci Web.

Sprawdź, czy wybrano ASP.NET Core 2.2 jako strukturę. Program .NET Core 2.2 znajduje się w ostatniej wersji programu Visual Studio 2017 i jest automatycznie instalowany i konfigurowany podczas instalowania programu Visual Studio 2017.

![Okno dialogowe programu Visual Studio do wybierania typu ASP.NET podstawowej aplikacji sieci Web z wybraną opcją interfejsu API.](media/create-web-api-application.png)

**Rysunek 4-37**. Wybieranie ASP.NET typu projektu CORE 2.2 i Web API

Jeśli masz jakąś poprzednią wersję programu .NET Core, możesz pobrać <https://dotnet.microsoft.com/download>i zainstalować wersję 2.2 z .

Można dodać obsługę platformy Docker podczas tworzenia projektu lub później, dzięki czemu można "Dockerize" projektu w dowolnym momencie. Aby dodać obsługę platformy Docker po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz polecenie **Dodaj** > **obsługę platformy Docker** w menu kontekstowym.

![Opcja menu kontekstowego, aby dodać obsługę platformy Docker do istniejącego projektu: kliknij prawym przyciskiem myszy (na projekcie) > Dodaj > docker support.](media/add-docker-support-to-project.png)

**Rysunek 4-38**. Dodawanie obsługi platformy Docker do istniejącego projektu

Aby zakończyć dodawanie obsługi platformy Docker, można wybrać system Windows lub Linux. W takim przypadku wybierz **Linux**, ponieważ AKS nie obsługuje kontenerów systemu Windows (od końca 2018 r.).

![Okno dialogowe Opcji, aby wybrać docelowy system operacyjny dla pliku dockerfile.](media/select-linux-docker-support.png)

**Rysunek 4-39**. Wybieranie kontenerów systemu Linux.

Dzięki tym prostym krokom masz aplikację ASP.NET Core 2.2 działającą na kontenerze systemu Linux.

Jak widać integracja między programem Visual Studio 2017 i docker jest całkowicie zorientowana na produktywność dewelopera.

Teraz możesz uruchomić aplikację za pomocą klawisza **F5** lub za pomocą przycisku **Odtwórz.**

Po uruchomieniu projektu można wyświetlić listę `docker images` obrazów za pomocą polecenia. Powinien zostać `mssampleapplication` wyświetlony obraz utworzony przez automatyczne wdrożenie naszego projektu za pomocą programu Visual Studio 2017.

```console
docker images
```

![Dane wyjściowe konsoli z polecenia obrazy platformy docker, pokazuje listę z: Repozytorium, Tag, Identyfikator obrazu, Utworzony (data) i Rozmiar.](media/docker-images-command.png)

**Rysunek 4-40**. Wyświetlanie obrazów platformy Docker

## <a name="register-the-solution-in-the-azure-container-registry"></a>Zarejestruj rozwiązanie w rejestrze kontenerów platformy Azure

Przekaż obraz do dowolnego rejestru platformy Docker, takiego jak [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) lub Docker Hub, aby obrazy można było wdrożyć w klastrze AKS z tego rejestru. W takim przypadku przekazujemy obraz do rejestru kontenerów platformy Azure.

### <a name="create-the-image-in-release-mode"></a>Tworzenie obrazu w trybie wydania

Teraz utworzymy obraz w trybie **wydania** (gotowy do produkcji), zmieniając na **Release**, jak pokazano na rysunku 4-41, i uruchamiając aplikację tak jak poprzednio.

![Opcja paska narzędzi w programie VS do tworzenia w trybie zwalniania.](media/select-release-mode.png)

**Rysunek 4-41**. Wybór trybu zwalniania

Jeśli wykonasz `docker image` polecenie, zobaczysz oba utworzone obrazy, `debug` jeden dla, a drugi dla `release` trybu.

### <a name="create-a-new-tag-for-the-image"></a>Tworzenie nowego znacznika dla obrazu

Każdy obraz kontenera musi być `loginServer` oznaczony nazwą rejestru. Ten tag jest używany na potrzeby kierowania podczas wypychania obrazów kontenerów do rejestru obrazów.

Możesz wyświetlić `loginServer` nazwę z witryny Azure portal, biorąc informacje z rejestru kontenerów platformy Azure

![Widok przeglądarki nazwy rejestru kontenerów platformy Azure w prawym górnym rogu.](media/loginServer-name.png)

**Rysunek 4-42**. Widok nazwy rejestru

Lub uruchamiając następujące polecenie:

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Wyjście konsoli z powyższego polecenia.](media/az-cli-loginServer-name.png)

**Rysunek 4-43**. Pobierz nazwę rejestru przy użyciu programu PowerShell

W obu przypadkach otrzymasz nazwę. W naszym `mssampleacr.azurecr.io`przykładzie .

Teraz możesz oznaczyć obraz, biorąc najnowszy obraz (release image), za pomocą polecenia:

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Po uruchomieniu `docker tag` polecenia wymień `docker images` obrazy za pomocą polecenia, a obraz powinien być widoczny z nowym tagiem.

![Dane wyjściowe konsoli z polecenia obrazy platformy docker.](media/tagged-docker-images-list.png)

**Rysunek 4-44**. Wyświetlanie oznakowanych obrazów

### <a name="push-the-image-into-the-azure-acr"></a>Wypychanie obrazu do usługi Azure ACR

Zaloguj się do rejestru kontenerów platformy Azure

```console
az acr login --name mssampleacr
```

Wypchnij obraz do usługi Azure ACR, używając następującego polecenia:

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

To polecenie zajmuje trochę czasu przekazywania obrazów, ale daje opinię w procesie.

![Dane wyjściowe konsoli z polecenia wypychania docker: pokazuje pasek postępu oparty na znakach dla każdej warstwy.](media/uploading-image-to-acr.png)

**Rysunek 4-45**. Przesyłanie obrazu do ACR

Poniżej możesz zobaczyć wynik, który powinieneś uzyskać po zakończeniu procesu:

![Wyjście konsoli z polecenia wypychania platformy docker, zakończone, pokazujące wszystkie warstwy lub węzły.](media/uploading-docker-images-complete.png)

**Rysunek 4-46**. Widok węzłów

Następnym krokiem jest wdrożenie kontenera w klastrze usługi AKS Kubernetes. W tym celu potrzebny jest plik (**.yml deploy file**), który zawiera następujące elementy:

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
> Aby uzyskać więcej informacji na temat wdrażania za pomocą narzędzia Kubernetes, zobacz:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

Teraz jesteś prawie gotowy do wdrożenia przy użyciu **Kubectl**, ale najpierw musisz uzyskać poświadczenia do klastra AKS za pomocą tego polecenia:

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Wyjście konsoli z powyższego polecenia: Scalone "MSSampleK8Cluster jako bieżący kontekst w /root/.kube/config](media/getting-aks-credentials.png)

**Rysunek 4-47**. uzyskiwanie poświadczeń

Następnie użyj `kubectl create` polecenia, aby uruchomić wdrożenie.

```console
kubectl create -f mssample-deploy.yml
```

![Dane wyjściowe konsoli z powyższego polecenia: utworzone wdrożenie "mssamplesbook". usługa "mssample-kub-app".](media/kubectl-create-command.png)

**Rysunek 4-48**. Wdrażanie na platformie Kubernetes

Po zakończeniu wdrażania można uzyskać dostęp do konsoli Kubernetes za pomocą lokalnego serwera proxy, do którego można czasowo uzyskiwać dostęp za pomocą tego polecenia:

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

I dostęp do `http://127.0.0.1:8001`adresu URL .

![Widok przeglądarki pulpitu nawigacyjnego usługi Kubernetes, przedstawiający wdrożenia, zasobniki, zestawy replik i usługi.](media/kubernetes-cluster-information.png)

**Rysunek 4-49**. Wyświetlanie informacji klastra kubernetes

Teraz masz aplikację wdrożoną na platformie Azure, przy użyciu kontenera systemu Linux i klastra Kubernetes AKS. Dostęp do przeglądania aplikacji można uzyskać na publicznym adresie IP usługi, który można uzyskać z witryny Azure portal.

> [!NOTE]
> W tym przewodniku możesz zobaczyć, jak utworzyć klaster AKS dla tego przykładu w sekcji [**Wdrażanie w usłudze Azure Kubernetes Service (AKS).**](deploy-azure-kubernetes-service.md)

>[!div class="step-by-step"]
>[Poprzedni](set-up-windows-containers-with-powershell.md)
>[następny](../docker-devops-workflow/index.md)
