---
title: Wdrażanie kontenerów na platformie Azure
description: Wdrażanie kontenerów na platformie Azure przy użyciu Azure Container Registry, usługi Azure Kubernetes i Azure Dev Spaces.
ms.date: 06/30/2019
ms.openlocfilehash: 6d95db26b6a45dd6825c88693308ffe90d1ed071
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183267"
---
# <a name="deploying-containers-in-azure"></a>Wdrażanie kontenerów na platformie Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kontenery zapewniają wiele korzyści, z których jeden jest przenośności. Można z łatwością korzystać z tego samego kontenera, który został wcześniej opracowany i przetestowany, i wdrożyć go na platformie Azure, gdzie może uruchamiać aplikację w środowiskach przejściowych i produkcyjnych. Platforma Azure udostępnia wiele opcji hostingu aplikacji opartych na kontenerach, a także obsługuje kilka różnych metod wdrażania. Najbardziej typowym i najbardziej elastycznym podejściem jest wdrożenie kontenerów do Azure Container Registry (ACR), gdzie są one dostępne dla usług, które mają być używane do ich hostowania. Usługa Azure Web App for Containers, usługa Azure Kubernetes Services (AKS) i usługa Azure Container Instance (ACI) mogą uzyskać dostęp do obrazów kontenerów, które zostały wypchnięte do programu ACR.

## <a name="azure-container-registry"></a>Azure Container Registry

Azure Container Registry (ACR) umożliwia tworzenie i przechowywanie obrazów we wszystkich wdrożeniach kontenerów oraz zarządzanie nimi. Istnieją inne rejestry kontenerów — zarówno publiczne, jak i prywatne, do których można wdrożyć kontenery. Zaletą ACR nad innymi opcjami jest możliwość przechowywania obrazów blisko środowiska produkcyjnego, poprawiania czasu kompilowania i wdrażania. Można je również zabezpieczyć przy użyciu tych samych procedur zabezpieczeń, które są używane w pozostałej części zasobów platformy Azure, co zwiększa bezpieczeństwo i zmniejsza nakłady pracy związane z zarządzaniem zasobami.

Można [utworzyć rejestr kontenerów za pomocą witryny Azure Portal](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal) lub [za pomocą interfejsu wiersza polecenia platformy Azure](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli) lub [narzędzi programu PowerShell](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell). Utworzenie nowego rejestru kontenerów wymaga jedynie subskrypcji platformy Azure, grupy zasobów i unikatowej nazwy. Na rysunku 3-11 przedstawiono podstawowe opcje tworzenia rejestru, które będą hostowane w *rejestrzename*. azurecr.IO.

![Utwórz kontener rejestru](./media/create-container-registry.png)
Container**3-11**. Utwórz rejestr kontenerów

Po utworzeniu rejestru należy przeprowadzić jego uwierzytelnienie przed użyciem. Zazwyczaj należy zalogować się do rejestru przy użyciu polecenia interfejsu CLI platformy Azure:

```azurecli
az acr login --name *registryname*
```

Po utworzeniu rejestru w Azure Container Registry można użyć poleceń platformy Docker do wypychania do niego obrazów kontenerów. Przed wykonaniem tej czynności należy jednak najpierw oznaczyć obraz za pomocą w pełni kwalifikowanej nazwy (URL) serwera logowania ACR. Będzie to miał format *registryname*. azurecr.IO.

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

Deweloperzy muszą rzadko wypychane bezpośrednio z maszyn do rejestru kontenerów. Zamiast tego potoku kompilacji zdefiniowany w narzędziu, takim jak Azure DevOps, powinny być odpowiedzialne za ten proces. Więcej informacji znajduje się w [rozdziale DevOps Native Cloud](devops.md).

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Jeśli aplikacja oparta na kontenerach obejmuje wiele kontenerów, najprawdopodobniej chcesz zdefiniować interakcje między kontenerami i zarządzać nimi, korzystając z programu *Orchestrator* , takiego jak Kubernetes. Po wdrożeniu obrazów kontenerów w usłudze ACR można łatwo skonfigurować usługi Azure Kubernetes, aby automatycznie wdrażać zaktualizowane obrazy z usługi ACR. Mając pełny potok ciągłej integracji/ciągłego wdrażania, można skonfigurować strategię [wydania](https://martinfowler.com/bliki/CanaryRelease.html) w systemie Kanaryjskie, aby zminimalizować ryzyko związane z szybkim wdrażaniem aktualizacji. Nowa wersja aplikacji została wstępnie skonfigurowana w środowisku produkcyjnym, w której nie są kierowane żadne ruchy, a następnie niewielka liczba użytkowników jest kierowana do nowo wdrożonej wersji aplikacji. Gdy zespół uzyska zaufanie do nowej wersji oprogramowania, zostaną wdrożone więcej wystąpień nowej wersji, a wystąpienia poprzedniej wersji zostaną wycofane. AKS łatwo obsługuje ten styl wdrożenia.

Tak jak w przypadku większości zasobów platformy Azure, możesz tworzyć klastry usługi Azure Kubernetes za pomocą portalu lub narzędzi wiersza polecenia lub narzędzi do automatyzacji infrastruktury, takich jak Helm lub Terraform. Aby rozpocząć pracę z nowym klastrem, należy podać następujące informacje:

- Subskrypcja platformy Azure
- Resource group
- Nazwa klastra Kubernetes
- Region
- Wersja Kubernetes
- Prefiks nazwy DNS
- Rozmiar węzła
- Liczba węzłów

Te informacje są wystarczające, aby rozpocząć pracę. W ramach procesu tworzenia w witrynie Azure Portal można także skonfigurować opcje następujących funkcji klastra:

- Skala
- Uwierzytelnianie
- Obsługa sieci
- Monitorowanie
- Znaczniki

Ten [Przewodnik Szybki Start przeprowadzi Cię przez proces wdrażania klastra AKS przy użyciu Azure Portal](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Złożone klastry Kubernetes mogą wymagać znaczących zasobów do hostowania, co może utrudnić deweloperom uruchamianie całej aplikacji na jednej maszynie (szczególnie w przypadku laptopu). Azure Dev Spaces rozwiązanie tego problemu, dzięki czemu deweloperzy mogą współpracować z własnymi wersjami klastrów usługi Azure Kubernetes hostowanych na platformie Azure. Azure Dev Spaces zaprojektowano w celu ułatwienia tworzenia aplikacji opartych na mikrousługach przy użyciu AKS.

Aby zrozumieć wartość Azure Dev Spaces, pozwól mi udostępnić tę ofertę z Gabe Monroy, wyprowadzać kontenery w Microsoft Azure:

"Załóżmy, że jesteś nowym pracownikiem próbującym naprawić usterkę w złożonej aplikacji mikrousług składającej się z dziesiątek składników, z których każda korzysta z własnych konfiguracji i usług zapasowych. Aby rozpocząć, musisz skonfigurować lokalne środowisko programistyczne, aby można było naśladować produkcję produkcyjną, w tym Konfigurowanie środowiska IDE, łańcucha narzędzi do tworzenia kontenerów, opartych na kontenerach zależności usługi, lokalne środowisko Kubernetes, imitacje usług zapasowych i wiele innych. Za każdym razem, gdy zajmujesz się skonfigurowaniem środowiska programistycznego, naprawianie, że pierwsza usterka może zająć dni.

> Można też użyć funkcji Spaces i AKS ".

Proces pracy z Azure Dev Spaces obejmuje następujące kroki:

1. Utwórz miejsce dev.
2. Skonfiguruj główne miejsce dev.
3. Skonfiguruj podrzędną przestrzeń programistyczną (dla własnej wersji systemu).
4. Nawiąż połączenie z obszarem dev.

Wszystkie te kroki można wykonać przy użyciu interfejsu wiersza polecenia platformy Azure i `azds` nowych narzędzi wiersza poleceń. Na przykład, aby utworzyć nowe miejsce dla deweloperów platformy Azure dla danego klastra Kubernetes, użyj polecenia takiego jak ten:

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

Następnie można użyć `azds prep` polecenia, aby wygenerować niezbędne zasoby platformy Docker i Helm na potrzeby uruchamiania aplikacji. Następnie uruchamiasz kod w AKS przy użyciu `azds up`. Przy pierwszym uruchomieniu tego polecenia Wykres Helm zostanie zainstalowany, a kontenery zostaną skompilowane i wdrożone zgodnie z instrukcjami. Wykonanie tej operacji może potrwać kilka minut po raz pierwszy. Jednak po wprowadzeniu zmian można nawiązać połączenie z własnym podrzędnym miejscem deweloperskim przy użyciu `azds space select` programu, a następnie wdrożyć i debugować aktualizacje w izolowanym obszarze podrzędnym. Po umieszczeniu miejsca na dev i uruchomieniu programu można wysłać do niego aktualizacje, ponownie `azds up` wykonując polecenie lub korzystając z wbudowanych narzędzi w programie Visual Studio lub Visual Studio Code. Za pomocą VS Code używasz palety poleceń do łączenia się z obszarem deweloperskim. Rysunek 3-12 pokazuje, jak uruchomić aplikację sieci Web przy użyciu Azure Dev Spaces w programie Visual Studio.

![Połącz się z Azure dev Spaces w programie](./media/azure-dev-spaces-visual-studio-launchsettings.png)
Visual Studio**rysunek 3-12**. Nawiązywanie połączenia z Azure Dev Spaces w programie Visual Studio

## <a name="references"></a>Odwołania

- [Wersja Kanaryjskie](https://martinfowler.com/bliki/CanaryRelease.html)
- [Azure Dev Spaces z VS Code](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore)
- [Azure Dev Spaces z programem Visual Studio](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore-visualstudio)

>[!div class="step-by-step"]
>[Poprzedni](combine-containers-serverless-approaches.md)
>[Następny](scale-containers-serverless.md)
