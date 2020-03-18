---
title: Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności
description: Dowiedz się, jak wdrożyć aplikację przy użyciu usługi Azure Kubernetes Service.
ms.date: 02/15/2019
ms.openlocfilehash: 0aa2f83fbf8f9a8815d65730002943cca748643d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "71182374"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Wdrażanie w usłudze Azure Kubernetes Service (AKS)

Możesz wchodzić w interakcje z AKS za pomocą preferowanego systemu operacyjnego klienta, tutaj pokazujemy, jak to zrobić z Microsoft Windows i osadzoną wersją Ubuntu Linux w systemie Windows, za pomocą poleceń Bash.

Wymagania wstępne, które mają przed użyciem AKS są:

- Maszyna deweloperska Linux lub Mac
- Maszyna deweloperska systemu Windows
  - Tryb dewelopera włączony w systemie Windows
  - Podsystem Windows dla systemu Linux
- Usługa Azure-CLI zainstalowana w [systemach Windows, Mac lub Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)

> [!NOTE]
> Aby znaleźć pełne informacje na temat:
>
> Azure-CLI:<https://docs.microsoft.com/cli/azure/index>
>
> Podsystem Windows dla systemu Linux:<https://docs.microsoft.com/windows/wsl/about>

## <a name="create-the-aks-environment-in-azure"></a>Tworzenie środowiska AKS na platformie Azure

Istnieje kilka sposobów tworzenia środowiska AKS. Można to zrobić za pomocą poleceń azure-CLI lub za pomocą witryny Azure portal.

W tym miejscu można zapoznać się z przykładami przy użyciu interfejsu azure-CLI do tworzenia klastra i witryny Azure portal do przeglądania wyników. W komputerze deweloperskim musisz również mieć Kubectl i Docker.  

## <a name="create-the-aks-cluster"></a>Tworzenie klastra AKS

Utwórz klaster AKS za pomocą tego polecenia:

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

Po zakończeniu zadania tworzenia można zobaczyć usługi AKS utworzone w witrynie Azure portal:

Grupa zasobów:

![Widok przeglądarki grupy zasobów usługi Azure AKS.](media/aks-resource-group-view.png)

**Rysunek 4-17**. Widok grupy zasobów Usługi AKS z platformy Azure.

Klaster AKS:

![Widok przeglądarki grupy zasobów AKS.](media/aks-cluster-view.png)

**Rysunek 4-18**. Widok AKS z platformy Azure.

Można również wyświetlić węzeł utworzony `Azure-CLI` przy `Kubectl`użyciu i .

Najpierw pobieranie poświadczeń:

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Dane wyjściowe konsoli z powyższego polecenia: Scalono "MsSampleK8Cluster jako bieżący kontekst w /root/.kube/config.](media/get-credentials-command-result.png)

**Rysunek 4-19**. `aks get-credentials`wynik polecenia.

A potem, coraz węzłów z Kubectl:

```console
kubectl get nodes
```

![Dane wyjściowe konsoli z powyższego polecenia: Lista węzłów ze stanem, wiekiem (czas pracy) i wersją](media/kubectl-get-nodes-command-result.png)

**Rysunek 4-20**. `kubectl get nodes`wynik polecenia.

>[!div class="step-by-step"]
>[Poprzedni](orchestrate-high-scalability-availability.md)
>[następny](docker-apps-development-environment.md)
