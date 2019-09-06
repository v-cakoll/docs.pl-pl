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
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Kompilowanie aplikacji ASP.NET Core 2,2 wdrożonych jako kontenery systemu Linux w programie Orchestrator AKS/Kubernetes

Usługa Azure Kubernetes Services (AKS) to zarządzane przez platformę Azure usługi, które upraszczają wdrażanie kontenerów i zarządzanie nimi.

Główne funkcje AKS są następujące:

- Oparta na platformie Azure płaszczyzna kontroli
- Automatyczne uaktualnienia
- Samonaprawianie
- Konfigurowalne skalowanie użytkownika
- Prostsze środowisko użytkownika dla deweloperów i operatorów klastrów.

W poniższych przykładach pokazano, jak utworzyć aplikację ASP.NET Core 2,2 działającą w systemie Linux i wdrożyć ją w klastrze AKS na platformie Azure, podczas gdy programowanie odbywa się przy użyciu programu Visual Studio 2017.

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a>Tworzenie projektu ASP.NET Core 2,2 przy użyciu programu Visual Studio 2017

ASP.NET Core jest platformą programistyczną ogólnego przeznaczenia obsługiwaną przez firmę Microsoft i społeczność programu .NET w witrynie GitHub. Jest to międzyplatformowe, pomocnicze systemy Windows, macOS i Linux oraz mogą być używane w scenariuszach urządzeń, chmur i osadzonych/IoT.

Ten przykład używa prostego projektu, który jest oparty na szablonie interfejsu API sieci Web programu Visual Studio, więc nie potrzebujesz dodatkowej wiedzy do utworzenia przykładu. Wystarczy utworzyć projekt przy użyciu standardowego szablonu, który zawiera wszystkie elementy, aby uruchomić niewielki projekt z interfejsem API REST przy użyciu technologii ASP.NET Core 2,2.

![Dodaj nowe okno projektu w programie Visual Studio, wybierając ASP.NET Core aplikacji sieci Web.](media/create-aspnet-core-application.png)

**Rysunek 4-36**. Tworzenie aplikacji ASP.NET Core

Aby utworzyć przykładowy projekt w programie Visual Studio, wybierz pozycję **plik** > **Nowy** > **projekt**, wybierz typy projektu **sieci Web** w lewym okienku, a następnie **ASP.NET Core aplikacji sieci Web**.

Program Visual Studio Wyświetla listę szablonów dla projektów sieci Web. W naszym przykładzie wybierz pozycję **interfejs API** , aby utworzyć aplikację interfejsu API sieci Web ASP.NET.

Upewnij się, że wybrano ASP.NET Core 2,2 jako strukturę. Program .NET Core 2,2 jest dołączony do najnowszej wersji programu Visual Studio 2017 i jest automatycznie instalowany i konfigurowany podczas instalowania programu Visual Studio 2017.

![Okno dialogowe programu Visual Studio, w którym można wybrać typ aplikacji sieci Web ASP.NET Core przy użyciu opcji API.](media/create-web-api-application.png)

**Rysunek 4-37**. Wybieranie ASP.NET CORE 2,2 i typ projektu interfejsu API sieci Web

Jeśli masz poprzednią wersję programu .NET Core, możesz pobrać i zainstalować wersję 2,2 z <https://www.microsoft.com/net/download/core#/sdk>programu.

Możesz dodać obsługę platformy Docker podczas tworzenia projektu lub później, aby w dowolnym momencie można było "przekształcać". Aby dodać obsługę platformy Docker po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań a następnie wybierz polecenie **Dodaj** > **obsługę platformy Docker** w menu kontekstowym.

![Opcja menu kontekstowego umożliwiająca dodanie obsługi platformy Docker do istniejącego projektu: Kliknij prawym przyciskiem myszy (na projekcie) > Dodaj > obsłudze platformy Docker.](media/add-docker-support-to-project.png)

**Rysunek 4-38**. Dodawanie obsługi platformy Docker do istniejącego projektu

Aby ukończyć Dodawanie obsługi platformy Docker, możesz wybrać system Windows lub Linux. W takim przypadku wybierz pozycję **Linux**, ponieważ usługa AKS nie obsługuje kontenerów systemu Windows (z opóźnieniem 2018).

![Opcja okna dialogowego umożliwiającego wybranie docelowego systemu operacyjnego dla pliku dockerfile.](media/select-linux-docker-support.png)

**Rysunek 4-39**. Wybieranie kontenerów systemu Linux.

Dzięki tym prostym krokom aplikacja ASP.NET Core 2,2 działa w kontenerze systemu Linux.

Jak widać, integracja między programem Visual Studio 2017 i platformą Docker jest całkowicie ukierunkowana na produktywność dewelopera.

Teraz możesz uruchomić aplikację przy użyciu klawisza **F5** lub przycisku **Odtwórz** .

Po uruchomieniu projektu można wyświetlić listę obrazów przy użyciu `docker images` polecenia. Powinien zostać wyświetlony `mssampleapplication` obraz utworzony przez automatyczne wdrażanie naszego projektu przy użyciu programu Visual Studio 2017.

```console
docker images
```

![Dane wyjściowe konsoli z polecenia Docker images pokazują listę z: Repozytorium, tag, identyfikator obrazu, utworzony (Date) i rozmiar.](media/docker-images-command.png)

**Rysunek 4-40**. Widok obrazów platformy Docker

## <a name="register-the-solution-in-the-azure-container-registry"></a>Zarejestruj rozwiązanie w Azure Container Registry

Przekaż obraz do dowolnego rejestru platformy Docker, takiego jak [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) lub Docker Hub, aby obrazy można wdrożyć w klastrze AKS z tego rejestru. W tym przypadku przekazujemy obraz do Azure Container Registry.

### <a name="create-the-image-in-release-mode"></a>Tworzenie obrazu w trybie wydania

Teraz utworzysz obraz w trybie **wydania** (gotowy do produkcji), zmieniając do **wersji**, jak pokazano na rysunku 4-41 i uruchamiając aplikację tak jak wcześniej.

![Opcja paska narzędzi w programie VS do kompilowania w trybie wydania.](media/select-release-mode.png)

**Rysunek 4-41**. Wybieranie trybu wydania

Jeśli wykonasz `docker image` polecenie, zobaczysz obu utworzonych obrazów, jeden dla `debug` i drugi dla `release` trybu.

### <a name="create-a-new-tag-for-the-image"></a>Utwórz nowy tag dla obrazu

Każdy obraz kontenera musi być oznaczony `loginServer` nazwą rejestru. Ten tag jest używany do routingu podczas wypychania obrazów kontenera do rejestru obrazów.

Można wyświetlić `loginServer` nazwę z Azure Portal, pobierając informacje z Azure Container Registry

![Widok w przeglądarce Nazwa rejestru kontenerów platformy Azure znajduje się w prawym górnym rogu.](media/loginServer-name.png)

**Rysunek 4-42**. Wyświetl nazwę rejestru

Lub uruchamiając następujące polecenie:

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Dane wyjściowe konsoli z powyższego polecenia.](media/az-cli-loginServer-name.png)

**Rysunek 4-43**. Pobieranie nazwy rejestru przy użyciu programu PowerShell

W obu przypadkach należy uzyskać nazwę. W naszym przykładzie `mssampleacr.azurecr.io`.

Teraz możesz oznaczyć obraz, pobierając najnowszą wersję obrazu (obraz wersji) za pomocą polecenia:

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Po uruchomieniu `docker tag` polecenia należy wyświetlić listę obrazów `docker images` za pomocą polecenia, a obraz z nowym tagiem.

![Dane wyjściowe konsoli z polecenia Docker images.](media/tagged-docker-images-list.png)

**Rysunek 4-44**. Widok obrazów oznakowanych

### <a name="push-the-image-into-the-azure-acr"></a>Wypchnij obraz do usługi Azure ACR

Zaloguj się do Azure Container Registry

```console
az acr login --name mssampleacr
```

Wypchnij obraz do usługi Azure ACR za pomocą następującego polecenia:

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

To polecenie pobiera obrazy, ale zawiera informacje zwrotne w procesie.

![Dane wyjściowe konsoli z polecenia Docker push: pokazuje pasek postępu oparty na znakach dla każdej warstwy.](media/uploading-image-to-acr.png)

**Rysunek 4-45**. Przekazywanie obrazu do ACR

Poniżej można zobaczyć wynik, który powinien zostać wyświetlony po zakończeniu procesu:

![Dane wyjściowe konsoli z polecenia Docker push, zakończone, pokazujące wszystkie warstwy lub węzły.](media/uploading-docker-images-complete.png)

**Rysunek 4-46**. Widok węzłów

Następnym krokiem jest wdrożenie kontenera w klastrze AKS Kubernetes. W takim przypadku potrzebny jest plik ( **. yml Deploy**), który zawiera następujące elementy:

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
> Aby uzyskać więcej informacji na temat wdrażania przy użyciu usługi Kubernetes, zobacz:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

Teraz wszystko jest już prawie gotowe do wdrożenia przy użyciu **polecenia kubectl**, ale najpierw należy uzyskać poświadczenia do klastra AKS za pomocą tego polecenia:

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Dane wyjściowe konsoli z powyższego polecenia: Scalono "MSSampleK8Cluster jako bieżący kontekst w/root/.Kube/config](media/getting-aks-credentials.png)

**Rysunek 4-47**. pobieranie poświadczeń

Następnie użyj `kubectl create` polecenia, aby uruchomić wdrożenie.

```console
kubectl create -f mssample-deploy.yml
```

![Dane wyjściowe konsoli z powyższego polecenia: wdrożenie "mssamplesbook" zostało utworzone. utworzono usługę "mssample-kub-App".](media/kubectl-create-command.png)

**Rysunek 4-48**. Wdróż w usłudze Kubernetes

Po zakończeniu wdrażania można uzyskać dostęp do konsoli Kubernetes z lokalnym serwerem proxy, do którego można okresowo uzyskać dostęp za pomocą tego polecenia:

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

I uzyskując dostęp `http://127.0.0.1:8001`do adresu URL.

![Widok przeglądarki pulpitu nawigacyjnego Kubernetes, przedstawiający wdrożenia, zbiory, zestawy replik i usługi.](media/kubernetes-cluster-information.png)

**Rysunek 4-49**. Wyświetlanie informacji o klastrze Kubernetes

Teraz aplikacja została wdrożona na platformie Azure, przy użyciu kontenera systemu Linux i klastra AKS Kubernetes. Możesz uzyskać dostęp do przeglądania aplikacji w publicznym adresie IP usługi, którą można uzyskać z Azure Portal.

> [!NOTE]
> Aby dowiedzieć się, jak utworzyć klaster AKS dla tego przykładu, w sekcji [**wdrażanie w usłudze Azure Kubernetes Service (AKS)** ](deploy-azure-kubernetes-service.md) w tym przewodniku.

>[!div class="step-by-step"]
>[Poprzedni](set-up-windows-containers-with-powershell.md)Następny
>[](../docker-devops-workflow/index.md)
