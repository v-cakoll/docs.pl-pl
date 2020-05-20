---
title: Wdrażanie kontenerów na platformie Azure
description: Wdrażanie kontenerów na platformie Azure przy użyciu Azure Container Registry, usługi Azure Kubernetes i Azure Dev Spaces.
ms.date: 04/13/2020
ms.openlocfilehash: ba2854323ee0f1394a3cff0dd3756cb3c7c32d5b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614152"
---
# <a name="deploying-containers-in-azure"></a>Wdrażanie kontenerów na platformie Azure

W tym rozdziale omówiono kontenery oraz rozdział 1. Wiemy, że kontenery oferują wiele korzyści dla aplikacji natywnych w chmurze, w tym przenośność. W chmurze platformy Azure można wdrożyć te same usługi kontenerów w środowiskach przejściowych i produkcyjnych. Platforma Azure oferuje kilka opcji hostowania obciążeń kontenerowych:

- Usługi Azure Kubernetes Services (AKS)
- Wystąpienie kontenera platformy Azure (ACI)
- Web Apps platformy Azure dla kontenerów

## <a name="azure-container-registry"></a>Azure Container Registry

Podczas konteneryzowania mikrousługi, najpierw należy utworzyć kontener "Image". Obraz to binarna reprezentacja kodu usługi, zależności i środowiska uruchomieniowego. Mimo że można ręcznie utworzyć obraz przy użyciu `Docker Build` polecenia z interfejsu API platformy Docker, lepszym rozwiązaniem jest utworzenie go w ramach zautomatyzowanego procesu kompilacji.

Po utworzeniu obrazy kontenerów są przechowywane w rejestrach kontenerów. Umożliwiają one tworzenie i przechowywanie obrazów kontenerów oraz zarządzanie nimi. Istnieje wiele dostępnych rejestrów — zarówno publicznych, jak i prywatnych. Azure Container Registry (ACR) to w pełni zarządzana usługa rejestru kontenerów w chmurze platformy Azure. Obrazy są utrwalane w sieci platformy Azure, co skraca czas wdrażania ich na hostach kontenerów platformy Azure. Można je również zabezpieczyć przy użyciu tych samych procedur zabezpieczeń i tożsamości, które są używane dla innych zasobów platformy Azure.

Azure Container Registry można utworzyć przy użyciu [Azure Portal](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal), [interfejsu wiersza polecenia platformy Azure](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli)lub [narzędzi programu PowerShell](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell). Tworzenie rejestru na platformie Azure jest proste. Wymaga subskrypcji platformy Azure, grupy zasobów i unikatowej nazwy. Na rysunku 3-11 przedstawiono podstawowe opcje tworzenia rejestru, które będą obsługiwane w programie `registryname.azurecr.io` .

![Tworzenie rejestru kontenerów](./media/create-container-registry.png)

**Rysunek 3-11**. Tworzenie rejestru kontenerów

Po utworzeniu rejestru należy przeprowadzić jego uwierzytelnienie przed użyciem. Zazwyczaj należy zalogować się do rejestru przy użyciu polecenia interfejsu CLI platformy Azure:

```azurecli
az acr login --name *registryname*
```

Po uwierzytelnieniu można użyć poleceń platformy Docker do wypychania do niego obrazów kontenerów. Przed wykonaniem tej czynności należy jednak oznaczyć obraz za pomocą w pełni kwalifikowanej nazwy (URL) serwera logowania ACR. Będzie on miał format *registryname*. azurecr.IO.

```console
docker tag mycontainer myregistry.azurecr.io/mycontainer:v1
```

Po oznakowaniu obrazu Użyj `docker push` polecenia, aby wypchnąć obraz do wystąpienia ACR.

```console
docker push myregistry.azurecr.io/mycontainer:v1
```

Po wypchnięciu obrazu do rejestru dobrym pomysłem jest usunięcie obrazu z lokalnego środowiska Docker, za pomocą tego polecenia:

```console
docker rmi myregistry.azurecr.io/mycontainer:v1
```

Najlepszym rozwiązaniem jest, aby deweloperzy nie mogli ręcznie wypychania obrazów do rejestru kontenerów. W zamian potok kompilacji zdefiniowany w narzędziu, takim jak GitHub lub Azure DevOps, powinien być odpowiedzialny za ten proces. Więcej informacji znajduje się w [rozdziale DevOps Native Cloud](devops.md).

## <a name="acr-tasks"></a>Zadania usługi ACR

[ACR Tasks](https://docs.microsoft.com/azure/container-registry/container-registry-tasks-overview) to zestaw funkcji dostępnych w Azure Container Registry. Rozszerza [cykl programowania w pętli wewnętrznej](https://docs.microsoft.com/dotnet/architecture/containerized-lifecycle/design-develop-containerized-apps/docker-apps-inner-loop-workflow) przez tworzenie obrazów kontenerów i zarządzanie nimi w chmurze platformy Azure. Zamiast wywoływania a `docker build` i `docker push` lokalnie na komputerze deweloperskim, są one automatycznie obsługiwane przez zadania ACR w chmurze.

Następujące polecenie AZ CLI/kompiluje obraz kontenera i wypchnięcie go do ACR:

```azurecli
# create a container registry
az acr create --resource-group myResourceGroup --name myContainerRegistry008 --sku Basic

# build container image in ACR and push it into your container regsitry
az acr build --image sample/hello-world:v1  --registry myContainerRegistry008 --file Dockerfile .
```

Jak widać w poprzednim bloku poleceń, nie ma potrzeby instalowania pulpitu platformy Docker na komputerze deweloperskim. Ponadto można skonfigurować Wyzwalacze zadań ACR w celu odbudowania obrazów kontenerów zarówno w kodzie źródłowym, jak i na podstawowych aktualizacjach obrazu.

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

W tym rozdziale omówiono usługę Azure Kubernetes Service (AKS). Wiemy, że jest to niefaktyczny koordynator kontenerów zarządzania kontenerami aplikacji natywnych w chmurze.

Po wdrożeniu obrazu do rejestru, takiego jak ACR, można skonfigurować AKS do automatycznego ściągania i wdrażania. W przypadku potoku ciągłej integracji i ciągłego wdrażania można skonfigurować strategię wydania w systemie [Kanaryjskie](https://martinfowler.com/bliki/CanaryRelease.html) , aby zminimalizować ryzyko związane z szybkim wdrażaniem aktualizacji. Nowa wersja aplikacji jest początkowo konfigurowana w środowisku produkcyjnym bez ruchu kierowanego do niego. Następnie system będzie kierować niewielki procent użytkowników do nowo wdrożonej wersji. Gdy zespół uzyska zaufanie do nowej wersji, może wycofać więcej wystąpień i wycofać stary. AKS łatwo obsługuje ten styl wdrożenia.

Podobnie jak w przypadku większości zasobów platformy Azure, można utworzyć klaster usługi Azure Kubernetes Service przy użyciu portalu, wiersza polecenia lub narzędzi do automatyzacji, takich jak Helm lub Terraform. Aby rozpocząć pracę z nowym klastrem, należy podać następujące informacje:

- Subskrypcja platformy Azure
- Grupa zasobów
- Nazwa klastra Kubernetes
- Region
- Wersja Kubernetes
- Prefiks nazwy DNS
- Rozmiar węzła
- Liczba węzłów

Te informacje są wystarczające, aby rozpocząć pracę. W ramach procesu tworzenia w Azure Portal można również skonfigurować opcje następujących funkcji klastra:

- Skalowanie
- Authentication
- Networking
- Monitorowanie
- Tagi

Ten [Przewodnik Szybki Start przeprowadzi Cię przez proces wdrażania klastra AKS przy użyciu Azure Portal](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Aplikacje natywne w chmurze mogą szybko rozwijać duże i złożone, co wymaga znaczących zasobów obliczeniowych. W tych scenariuszach cała aplikacja nie może być hostowana na maszynie deweloperskiej (szczególnie w przypadku laptopu). Azure Dev Spaces zaprojektowano w celu rozwiązania tego problemu przy użyciu AKS. Pozwala to deweloperom na współdziałanie z lokalną wersją swoich usług przy jednoczesnym obsługiwaniu reszty aplikacji w klastrze projektowym AKS.

Deweloperzy mogą korzystać z działającego wystąpienia (Programowanie) w klastrze AKS zawierającym całą zaprojektowaną aplikację. Ale korzystają z miejsc osobistych skonfigurowanych na ich maszynach do lokalnego tworzenia usług. Gdy wszystko będzie gotowe, testuje od końca do końca w klastrze AKS — bez replikowania zależności. Azure Dev Spaces Scala kod z komputera lokalnego z usługami w AKS. Deweloperzy mogą szybko iterować i debugować kod bezpośrednio w Kubernetes przy użyciu programu Visual Studio lub Visual Studio Code.

Aby zrozumieć wartość Azure Dev Spaces, pozwól mi udostępnić tę ofertę z Gabe Monroy, wyprowadzać kontenery w Microsoft Azure:

> "Załóżmy, że jesteś nowym pracownikiem próbującym naprawić usterkę w złożonej aplikacji mikrousług składającej się z dziesiątek składników, z których każda korzysta z własnych konfiguracji i usług zapasowych. Aby rozpocząć, musisz skonfigurować lokalne środowisko programistyczne, aby można było naśladować produkcję produkcyjną, w tym Konfigurowanie środowiska IDE, łańcucha narzędzi do tworzenia kontenerów, opartych na kontenerach zależności usługi, lokalne środowisko Kubernetes, imitacje usług zapasowych i wiele innych. Za każdym razem, gdy zajmujesz się skonfigurowaniem środowiska programistycznego, naprawianie, że pierwsza usterka może zająć dni.
> Można też użyć funkcji Spaces i AKS ".

Proces pracy z Azure Dev Spaces obejmuje następujące kroki:

1. Utwórz miejsce dev.
2. Skonfiguruj główne miejsce dev.
3. Skonfiguruj podrzędną przestrzeń programistyczną (dla własnej wersji systemu).
4. Nawiąż połączenie z obszarem dev.

Wszystkie te kroki można wykonać przy użyciu interfejsu wiersza polecenia platformy Azure i nowych `azds` narzędzi wiersza poleceń. Na przykład, aby utworzyć nowe miejsce dla deweloperów platformy Azure dla danego klastra Kubernetes, użyj polecenia takiego jak ten:

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

Następnie można użyć `azds prep` polecenia, aby wygenerować niezbędne zasoby platformy Docker i Helm na potrzeby uruchamiania aplikacji. Następnie uruchamiasz kod w AKS przy użyciu `azds up` . Przy pierwszym uruchomieniu tego polecenia zostanie zainstalowany wykres Helm. Kontenery zostaną skompilowane i wdrożone zgodnie z instrukcjami. To zadanie może potrwać kilka minut podczas pierwszego uruchomienia. Jednak po wprowadzeniu zmian można nawiązać połączenie z własnym podrzędnym miejscem deweloperskim przy użyciu programu `azds space select` , a następnie wdrożyć i debugować aktualizacje w izolowanym obszarze podrzędnym. Po umieszczeniu miejsca na dev i uruchomieniu programu można wysłać do niego aktualizacje, ponownie wydając `azds up` polecenie lub korzystając z wbudowanych narzędzi w programie Visual Studio lub Visual Studio Code. Za pomocą VS Code używasz palety poleceń do łączenia się z obszarem deweloperskim. Rysunek 3-12 pokazuje, jak uruchomić aplikację sieci Web przy użyciu Azure Dev Spaces w programie Visual Studio.

![Połącz się z Azure Dev Spaces w programie Visual Studio ](./media/azure-dev-spaces-visual-studio-launchsettings.png)
 **rysunek 3-12**. Nawiązywanie połączenia z Azure Dev Spaces w programie Visual Studio

>[!div class="step-by-step"]
>[Poprzedni](combine-containers-serverless-approaches.md) 
> [Dalej](scale-containers-serverless.md)
