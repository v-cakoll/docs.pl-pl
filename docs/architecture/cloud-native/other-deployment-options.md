---
title: Inne opcje wdrażania kontenera
description: Inne opcje wdrażania kontenerów korzystających z platformy Azure
ms.date: 05/13/2020
ms.openlocfilehash: acb022e3d4fd4862c592fa571894e1b8ce17f465
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613762"
---
# <a name="other-container-deployment-options"></a>Inne opcje wdrażania kontenera

Oprócz usługi Azure Kubernetes Service (AKS) można również wdrożyć kontenery do Azure App Service na potrzeby kontenerów i Azure Container Instances.

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a>Kiedy warto wdrożyć do App Service dla kontenerów?

Proste aplikacje produkcyjne, które nie wymagają aranżacji, są dobrze dostosowane do Azure App Service kontenerów.

## <a name="how-to-deploy-to-app-service-for-containers"></a>Jak wdrożyć do App Service dla kontenerów

Do wdrożenia w celu [Azure App Service dla kontenerów](https://azure.microsoft.com/services/app-service/containers/)konieczne będzie wystąpienie Azure Container Registry (ACR) i poświadczenia, aby uzyskać do niego dostęp. Wypchnij obraz kontenera do repozytorium ACR, aby umożliwić jego ściąganie do Azure App Service. Po zakończeniu można skonfigurować aplikację do ciągłego wdrażania. Wykonanie tej czynności spowoduje automatyczne wdrożenie aktualizacji przy każdej zmianie obrazu w ACR.

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a>Kiedy warto wdrożyć do Azure Container Instances?

[Azure Container Instances (ACI)](https://azure.microsoft.com/services/container-instances/) umożliwia uruchamianie kontenerów platformy Docker w zarządzanym środowisku chmury bezserwerowym bez konieczności konfigurowania maszyn wirtualnych lub klastrów. Jest to doskonałe rozwiązanie dla krótkoterminowych obciążeń, które mogą być uruchamiane w izolowanym kontenerze. Rozważ ACI dla prostych usług, scenariuszy testowania, automatyzacji zadań i zadań kompilacji. ACI tworzy wystąpienie kontenera, wykonuje zadanie, a następnie obraca je w dół.

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a>Jak wdrożyć aplikację w Azure Container Instances

Do wdrożenia w usłudze [Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/)wymagane jest Azure Container Registry (ACR) i poświadczenia dostępu do nich. Po wypchnięciu obrazu kontenera do repozytorium jest on dostępny do ściągnięcia do ACI. Możesz korzystać z ACI za pomocą Azure Portal lub interfejsu wiersza polecenia. ACR zapewnia ścisłą integrację z ACI. Rysunek 3-14 pokazuje, jak wypchnąć pojedynczy obraz kontenera do ACR.

![Wystąpienie uruchomienia Azure Container Registry](./media/acr-runinstance-contextmenu.png)

**Rysunek 3-14**. Wystąpienie uruchomienia Azure Container Registry

Tworzenie wystąpienia w ACI można wykonać szybko. Określ rejestr obrazu, informacje o grupie zasobów platformy Azure, ilość pamięci do przydzielenia oraz port, na którym nasłuchuje. W tym [przewodniku szybki start pokazano, jak wdrożyć wystąpienie kontenera do ACI przy użyciu Azure Portal](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal).

Po zakończeniu wdrożenia Znajdź nowo wdrożony adres IP kontenera i skontaktuj się z nim za pośrednictwem określonego portu.

Azure Container Instances oferuje najszybszy sposób uruchamiania prostych obciążeń kontenerów na platformie Azure. Nie musisz konfigurować usługi App Service, Orchestrator ani Virtual Machine. W scenariuszach, w których wymagana jest pełna aranżacja kontenerów, odnajdowanie usług, Skalowanie automatyczne lub uaktualnienia skoordynowane, zalecamy korzystanie z usługi Azure Kubernetes Service (AKS).

## <a name="references"></a>Dokumentacja

- [Co to jest Kubernetes?](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Instalowanie Kubernetes z Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube vs Docker](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Visual Studio Tools for Docker](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)
- [Informacje o zimnym uruchomieniu bezserwerowym](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [Wstępnie grzane wystąpienia Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [Tworzenie funkcji w systemie Linux przy użyciu niestandardowego obrazu](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [Uruchamianie Azure Functions w kontenerze platformy Docker](https://markheath.net/post/azure-functions-docker)
- [Tworzenie funkcji w systemie Linux przy użyciu niestandardowego obrazu](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [Azure Functions z funkcją automatycznego skalowania opartego na zdarzeniach Kubernetes](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)
- [Wersja Kanaryjskie](https://martinfowler.com/bliki/CanaryRelease.html)
- [Azure Dev Spaces z VS Code](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore)
- [Azure Dev Spaces z programem Visual Studio](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore-visualstudio)
- [AKS pul wielu węzłów](https://docs.microsoft.com/azure/aks/use-multiple-node-pools)
- [Automatyczne skalowanie klastra AKS](https://docs.microsoft.com/azure/aks/cluster-autoscaler)
- [Samouczek: skalowanie aplikacji w AKS](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale)
- [Skalowanie i hosting usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-scale)
- [Dokumentacja Azure Container Instances](https://docs.microsoft.com/azure/container-instances/)
- [Wdróż wystąpienie kontenera z ACR](https://docs.microsoft.com/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
>[Poprzedni](scale-containers-serverless.md) 
> [Dalej](communication-patterns.md)
