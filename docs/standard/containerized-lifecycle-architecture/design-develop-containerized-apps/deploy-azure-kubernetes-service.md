---
title: Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności
description: Dowiedz się, jak wdrożyć aplikację przy użyciu usługi Azure Kubernetes Service.
ms.date: 02/15/2019
ms.openlocfilehash: 88e76b4b0a3686f4227a6aee1b7fbd2bfe55fdcc
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644644"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="a1064-103">Wdrażanie w usłudze Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="a1064-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="a1064-104">Możesz wchodzić w interakcje za pomocą usługi AKS, korzystając z preferowanego klienta systemu operacyjnego, w tym miejscu przedstawiono, jak to zrobić za pomocą programu Microsoft Windows i osadzone wersję Ubuntu Linux w Windows, za pomocą poleceń powłoki Bash.</span><span class="sxs-lookup"><span data-stu-id="a1064-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="a1064-105">Dostępne są następujące wymagania wstępne, aby przed rozpoczęciem korzystania z usługi AKS:</span><span class="sxs-lookup"><span data-stu-id="a1064-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="a1064-106">Komputerze deweloperskim systemu Linux lub Mac</span><span class="sxs-lookup"><span data-stu-id="a1064-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="a1064-107">Komputer deweloperski Windows</span><span class="sxs-lookup"><span data-stu-id="a1064-107">Windows development machine</span></span>
  - <span data-ttu-id="a1064-108">Tryb dewelopera, włączone na Windows</span><span class="sxs-lookup"><span data-stu-id="a1064-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="a1064-109">Podsystem Windows dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="a1064-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="a1064-110">Azure-CLI zainstalowana na [Windows, Mac lub Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span><span class="sxs-lookup"><span data-stu-id="a1064-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span></span>

> [!NOTE]
> <span data-ttu-id="a1064-111">Aby uzyskać pełne informacje na temat:</span><span class="sxs-lookup"><span data-stu-id="a1064-111">To find complete information about:</span></span>
>
> <span data-ttu-id="a1064-112">Wiersza polecenia platformy Azure: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span><span class="sxs-lookup"><span data-stu-id="a1064-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span></span>
>
> <span data-ttu-id="a1064-113">Podsystem Windows dla systemu Linux: <https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="a1064-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="a1064-114">Tworzenie środowiska usługi AKS na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="a1064-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="a1064-115">Istnieje kilka sposobów, aby utworzyć środowisko usługi AKS.</span><span class="sxs-lookup"><span data-stu-id="a1064-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="a1064-116">Można zrobić za pomocą poleceń interfejsu wiersza polecenia Azure lub za pomocą witryny Azure portal.</span><span class="sxs-lookup"><span data-stu-id="a1064-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="a1064-117">W tym miejscu możesz eksplorować przykłady przy użyciu interfejsu wiersza polecenia platformy Azure platformy do utworzenia klastra i witryny Azure portal, aby przejrzeć wyniki.</span><span class="sxs-lookup"><span data-stu-id="a1064-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="a1064-118">Musisz również mieć Kubectl i platformy Docker w komputerze deweloperskim.</span><span class="sxs-lookup"><span data-stu-id="a1064-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="a1064-119">Tworzenie klastra AKS</span><span class="sxs-lookup"><span data-stu-id="a1064-119">Create the AKS cluster</span></span>

<span data-ttu-id="a1064-120">Tworzenie klastra AKS, za pomocą tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="a1064-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="a1064-121">Po zakończeniu zadania tworzenia, możesz zobaczyć AKS utworzone w witrynie Azure portal:</span><span class="sxs-lookup"><span data-stu-id="a1064-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="a1064-122">Grupa zasobów:</span><span class="sxs-lookup"><span data-stu-id="a1064-122">The resource group:</span></span>

![Widok grupy zasobów platformy Azure w usłudze AKS w przeglądarce.](media/aks-resource-group-view.png)

<span data-ttu-id="a1064-124">**Rysunek 4-17**.</span><span class="sxs-lookup"><span data-stu-id="a1064-124">**Figure 4-17**.</span></span> <span data-ttu-id="a1064-125">Widok grupy zasobów usługi AKS z platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="a1064-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="a1064-126">Klaster AKS:</span><span class="sxs-lookup"><span data-stu-id="a1064-126">The AKS cluster:</span></span>

![Widok grupy zasobów usługi AKS w przeglądarce.](media/aks-cluster-view.png)

<span data-ttu-id="a1064-128">**Rysunek 4-18**.</span><span class="sxs-lookup"><span data-stu-id="a1064-128">**Figure 4-18**.</span></span> <span data-ttu-id="a1064-129">Widok AKS z platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="a1064-129">AKS view from Azure.</span></span>

<span data-ttu-id="a1064-130">Można również wyświetlić węzeł utworzone za pomocą `Azure-CLI` i `Kubectl`.</span><span class="sxs-lookup"><span data-stu-id="a1064-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="a1064-131">Po pierwsze Uzyskiwanie poświadczeń:</span><span class="sxs-lookup"><span data-stu-id="a1064-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Dane wyjściowe z powyższego polecenia konsoli: Scalone "MsSampleK8Cluster jako /root/.kube/config bieżącym kontekście.](media/get-credentials-command-result.png)

<span data-ttu-id="a1064-133">**Rysunek 4-19**.</span><span class="sxs-lookup"><span data-stu-id="a1064-133">**Figure 4-19**.</span></span> <span data-ttu-id="a1064-134">`aks get-credentials` wynik polecenia.</span><span class="sxs-lookup"><span data-stu-id="a1064-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="a1064-135">Następnie wyszukaj pobieranie węzłów z narzędzia Kubectl:</span><span class="sxs-lookup"><span data-stu-id="a1064-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Dane wyjściowe powyższej polecenia konsoli: Lista węzłów o stanie, wiek (czas uruchamiania) i wersji](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="a1064-137">**Rysunek 4-20**.</span><span class="sxs-lookup"><span data-stu-id="a1064-137">**Figure 4-20**.</span></span> <span data-ttu-id="a1064-138">`kubectl get nodes` wynik polecenia.</span><span class="sxs-lookup"><span data-stu-id="a1064-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a1064-139">[Poprzednie](orchestrate-high-scalability-availability.md)
>[dalej](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="a1064-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
