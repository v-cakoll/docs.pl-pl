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
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="9e05e-103">Wdrażanie w usłudze Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="9e05e-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="9e05e-104">Możesz wchodzić w interakcje z AKS za pomocą preferowanego systemu operacyjnego klienta, tutaj pokazujemy, jak to zrobić z Microsoft Windows i osadzoną wersją Ubuntu Linux w systemie Windows, za pomocą poleceń Bash.</span><span class="sxs-lookup"><span data-stu-id="9e05e-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="9e05e-105">Wymagania wstępne, które mają przed użyciem AKS są:</span><span class="sxs-lookup"><span data-stu-id="9e05e-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="9e05e-106">Maszyna deweloperska Linux lub Mac</span><span class="sxs-lookup"><span data-stu-id="9e05e-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="9e05e-107">Maszyna deweloperska systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9e05e-107">Windows development machine</span></span>
  - <span data-ttu-id="9e05e-108">Tryb dewelopera włączony w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="9e05e-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="9e05e-109">Podsystem Windows dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="9e05e-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="9e05e-110">Usługa Azure-CLI zainstalowana w [systemach Windows, Mac lub Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span><span class="sxs-lookup"><span data-stu-id="9e05e-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span></span>

> [!NOTE]
> <span data-ttu-id="9e05e-111">Aby znaleźć pełne informacje na temat:</span><span class="sxs-lookup"><span data-stu-id="9e05e-111">To find complete information about:</span></span>
>
> <span data-ttu-id="9e05e-112">Azure-CLI:<https://docs.microsoft.com/cli/azure/index></span><span class="sxs-lookup"><span data-stu-id="9e05e-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index></span></span>
>
> <span data-ttu-id="9e05e-113">Podsystem Windows dla systemu Linux:<https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="9e05e-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="9e05e-114">Tworzenie środowiska AKS na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="9e05e-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="9e05e-115">Istnieje kilka sposobów tworzenia środowiska AKS.</span><span class="sxs-lookup"><span data-stu-id="9e05e-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="9e05e-116">Można to zrobić za pomocą poleceń azure-CLI lub za pomocą witryny Azure portal.</span><span class="sxs-lookup"><span data-stu-id="9e05e-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="9e05e-117">W tym miejscu można zapoznać się z przykładami przy użyciu interfejsu azure-CLI do tworzenia klastra i witryny Azure portal do przeglądania wyników.</span><span class="sxs-lookup"><span data-stu-id="9e05e-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="9e05e-118">W komputerze deweloperskim musisz również mieć Kubectl i Docker.</span><span class="sxs-lookup"><span data-stu-id="9e05e-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="9e05e-119">Tworzenie klastra AKS</span><span class="sxs-lookup"><span data-stu-id="9e05e-119">Create the AKS cluster</span></span>

<span data-ttu-id="9e05e-120">Utwórz klaster AKS za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="9e05e-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="9e05e-121">Po zakończeniu zadania tworzenia można zobaczyć usługi AKS utworzone w witrynie Azure portal:</span><span class="sxs-lookup"><span data-stu-id="9e05e-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="9e05e-122">Grupa zasobów:</span><span class="sxs-lookup"><span data-stu-id="9e05e-122">The resource group:</span></span>

![Widok przeglądarki grupy zasobów usługi Azure AKS.](media/aks-resource-group-view.png)

<span data-ttu-id="9e05e-124">**Rysunek 4-17**.</span><span class="sxs-lookup"><span data-stu-id="9e05e-124">**Figure 4-17**.</span></span> <span data-ttu-id="9e05e-125">Widok grupy zasobów Usługi AKS z platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="9e05e-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="9e05e-126">Klaster AKS:</span><span class="sxs-lookup"><span data-stu-id="9e05e-126">The AKS cluster:</span></span>

![Widok przeglądarki grupy zasobów AKS.](media/aks-cluster-view.png)

<span data-ttu-id="9e05e-128">**Rysunek 4-18**.</span><span class="sxs-lookup"><span data-stu-id="9e05e-128">**Figure 4-18**.</span></span> <span data-ttu-id="9e05e-129">Widok AKS z platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="9e05e-129">AKS view from Azure.</span></span>

<span data-ttu-id="9e05e-130">Można również wyświetlić węzeł utworzony `Azure-CLI` przy `Kubectl`użyciu i .</span><span class="sxs-lookup"><span data-stu-id="9e05e-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="9e05e-131">Najpierw pobieranie poświadczeń:</span><span class="sxs-lookup"><span data-stu-id="9e05e-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Dane wyjściowe konsoli z powyższego polecenia: Scalono "MsSampleK8Cluster jako bieżący kontekst w /root/.kube/config.](media/get-credentials-command-result.png)

<span data-ttu-id="9e05e-133">**Rysunek 4-19**.</span><span class="sxs-lookup"><span data-stu-id="9e05e-133">**Figure 4-19**.</span></span> <span data-ttu-id="9e05e-134">`aks get-credentials`wynik polecenia.</span><span class="sxs-lookup"><span data-stu-id="9e05e-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="9e05e-135">A potem, coraz węzłów z Kubectl:</span><span class="sxs-lookup"><span data-stu-id="9e05e-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Dane wyjściowe konsoli z powyższego polecenia: Lista węzłów ze stanem, wiekiem (czas pracy) i wersją](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="9e05e-137">**Rysunek 4-20**.</span><span class="sxs-lookup"><span data-stu-id="9e05e-137">**Figure 4-20**.</span></span> <span data-ttu-id="9e05e-138">`kubectl get nodes`wynik polecenia.</span><span class="sxs-lookup"><span data-stu-id="9e05e-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9e05e-139">[Poprzedni](orchestrate-high-scalability-availability.md)
>[następny](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="9e05e-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
