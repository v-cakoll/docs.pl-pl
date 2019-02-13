---
title: Organizowanie mikrousług i wielokontenerowych aplikacji o wysokiej skalowalności i dostępności
description: Dowiedz się, jak wdrożyć aplikację przy użyciu usługi Azure Kubernetes Service.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 984a72c9ca8883b338d10fdaa826a6007580372d
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221398"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Wdrażanie w usłudze Azure Kubernetes Service (AKS)

Możesz wchodzić w interakcje za pomocą usługi AKS, korzystając z preferowanego klienta systemu operacyjnego, w tym miejscu przedstawiono, jak to zrobić za pomocą programu Microsoft Windows i osadzone wersję Ubuntu Linux w Windows, za pomocą poleceń powłoki Bash.

Dostępne są następujące wymagania wstępne, aby przed rozpoczęciem korzystania z usługi AKS:

- Komputerze deweloperskim systemu Linux lub Mac
- Komputer deweloperski Windows
  - Tryb dewelopera, włączone na Windows
  - Podsystem Windows dla systemu Linux
- Azure-CLI zainstalowana na [Windows, Mac lub Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)

> [!NOTE]
> Aby uzyskać pełne informacje na temat:
>
> Wiersza polecenia platformy Azure: [https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest](https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest)
>
> Podsystem Windows dla systemu Linux: [https://docs.microsoft.com/windows/wsl/about](https://docs.microsoft.com/windows/wsl/about)

## <a name="create-the-aks-environment-in-azure"></a>Tworzenie środowiska usługi AKS na platformie Azure

Istnieje kilka sposobów, aby utworzyć środowisko usługi AKS. Można zrobić za pomocą poleceń interfejsu wiersza polecenia Azure lub za pomocą witryny Azure portal.

W tym miejscu możesz eksplorować przykłady przy użyciu interfejsu wiersza polecenia platformy Azure platformy do utworzenia klastra i witryny Azure portal, aby przejrzeć wyniki. Musisz również mieć Kubectl i platformy Docker w komputerze deweloperskim.  

## <a name="create-the-aks-cluster"></a>Tworzenie klastra AKS

Tworzenie klastra AKS, za pomocą tego polecenia:

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

Po zakończeniu zadania tworzenia, możesz zobaczyć AKS utworzone w witrynie Azure portal:

Grupa zasobów:

![Widok grupy zasobów platformy Azure w usłudze AKS w przeglądarce.](media/aks-resource-group-view.png)

**Rysunek 4-17**. Widok grupy zasobów usługi AKS z platformy Azure.

Klaster AKS:

![Widok grupy zasobów usługi AKS w przeglądarce.](media/aks-cluster-view.png)

**Rysunek 4-18**. Widok AKS z platformy Azure.

Można również wyświetlić węzeł utworzone za pomocą `Azure-CLI` i `Kubectl`.

Po pierwsze Uzyskiwanie poświadczeń:

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Dane wyjściowe z powyższego polecenia konsoli: Scalone "MsSampleK8Cluster jako /root/.kube/config bieżącym kontekście.](media/get-credentials-command-result.png)

**Rysunek 4-19**. `aks get-credentials` wynik polecenia.

Następnie wyszukaj pobieranie węzłów z narzędzia Kubectl:

```console
kubectl get nodes
```

![Dane wyjściowe powyższej polecenia konsoli: Lista węzłów o stanie, wiek (czas uruchamiania) i wersji](media/kubectl-get-nodes-command-result.png)

**Rysunek 4-20**. `kubectl get nodes` wynik polecenia.

>[!div class="step-by-step"]
>[Poprzednie](orchestrate-high-scalability-availability.md)
>[dalej](docker-apps-development-environment.md)
