---
title: Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności
description: Dowiedz się, jak wdrożyć aplikację przy użyciu usługi Azure Kubernetes Service.
ms.date: 02/15/2019
ms.openlocfilehash: 88e76b4b0a3686f4227a6aee1b7fbd2bfe55fdcc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295376"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Wdrażanie w usłudze Azure Kubernetes Service (AKS)

Możesz korzystać z usługi AKS przy użyciu preferowanego systemu operacyjnego klienta. w tym miejscu pokazano, jak to zrobić za pomocą systemu Microsoft Windows i osadzonej wersji Ubuntu Linux w systemie Windows przy użyciu poleceń bash.

Przed użyciem AKS są spełnione wymagania wstępne:

- Komputer deweloperski z systemem Linux lub Mac
- Komputer deweloperski systemu Windows
  - Tryb dewelopera włączony w systemie Windows
  - Podsystem Windows dla systemu Linux
- Azure — interfejs wiersza polecenia zainstalowany w [systemie Windows, Mac lub Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)

> [!NOTE]
> Aby uzyskać pełne informacje na temat:
>
> Azure — interfejs wiersza polecenia:<https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest>
>
> Podsystem Windows dla systemu Linux:<https://docs.microsoft.com/windows/wsl/about>

## <a name="create-the-aks-environment-in-azure"></a>Tworzenie środowiska AKS na platformie Azure

Istnieje kilka sposobów tworzenia środowiska AKS. Można to zrobić za pomocą poleceń interfejsu wiersza polecenia platformy Azure lub przy użyciu Azure Portal.

W tym miejscu możesz zapoznać się z przykładami za pomocą interfejsu wiersza polecenia platformy Azure, aby utworzyć klaster i Azure Portal, aby przejrzeć wyniki. Musisz również mieć polecenia kubectl i Docker na komputerze deweloperskim.  

## <a name="create-the-aks-cluster"></a>Tworzenie klastra AKS

Utwórz klaster AKS przy użyciu tego polecenia:

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

Po zakończeniu zadania tworzenia można zobaczyć AKS utworzone w Azure Portal:

Grupa zasobów:

![Widok przeglądarki grupy zasobów usługi Azure AKS.](media/aks-resource-group-view.png)

**Rysunek 4-17**. AKS widok grupy zasobów na platformie Azure.

Klaster AKS:

![Widok przeglądarki grupy zasobów AKS.](media/aks-cluster-view.png)

**Rysunek 4-18**. Widok AKS na platformie Azure.

Można również wyświetlić węzeł utworzony przy użyciu `Azure-CLI` i. `Kubectl`

Po pierwsze, pobieranie poświadczeń:

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Dane wyjściowe konsoli z powyższego polecenia: Scalono "MsSampleK8Cluster jako bieżący kontekst w/root/.Kube/config.](media/get-credentials-command-result.png)

**Rysunek 4-19**. `aks get-credentials`wynik polecenia.

A następnie pobieranie węzłów z polecenia kubectl:

```console
kubectl get nodes
```

![Dane wyjściowe konsoli z powyższego polecenia: Lista węzłów o stanie, wieku (czasie wykonywania) i wersji](media/kubectl-get-nodes-command-result.png)

**Rysunek 4-20**. `kubectl get nodes`wynik polecenia.

>[!div class="step-by-step"]
>[Poprzedni](orchestrate-high-scalability-availability.md)Następny
>[](docker-apps-development-environment.md)
