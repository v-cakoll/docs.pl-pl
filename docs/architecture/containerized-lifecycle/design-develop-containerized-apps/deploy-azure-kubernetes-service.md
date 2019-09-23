---
title: Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności
description: Dowiedz się, jak wdrożyć aplikację przy użyciu usługi Azure Kubernetes Service.
ms.date: 02/15/2019
ms.openlocfilehash: 0aa2f83fbf8f9a8815d65730002943cca748643d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182374"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="f3b7a-103">Wdrażanie w usłudze Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="f3b7a-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="f3b7a-104">Możesz korzystać z usługi AKS przy użyciu preferowanego systemu operacyjnego klienta. w tym miejscu pokazano, jak to zrobić za pomocą systemu Microsoft Windows i osadzonej wersji Ubuntu Linux w systemie Windows przy użyciu poleceń bash.</span><span class="sxs-lookup"><span data-stu-id="f3b7a-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="f3b7a-105">Przed użyciem AKS są spełnione wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="f3b7a-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="f3b7a-106">Komputer deweloperski z systemem Linux lub Mac</span><span class="sxs-lookup"><span data-stu-id="f3b7a-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="f3b7a-107">Komputer deweloperski systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f3b7a-107">Windows development machine</span></span>
  - <span data-ttu-id="f3b7a-108">Tryb dewelopera włączony w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="f3b7a-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="f3b7a-109">Podsystem Windows dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="f3b7a-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="f3b7a-110">Azure — interfejs wiersza polecenia zainstalowany w [systemie Windows, Mac lub Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span><span class="sxs-lookup"><span data-stu-id="f3b7a-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span></span>

> [!NOTE]
> <span data-ttu-id="f3b7a-111">Aby uzyskać pełne informacje na temat:</span><span class="sxs-lookup"><span data-stu-id="f3b7a-111">To find complete information about:</span></span>
>
> <span data-ttu-id="f3b7a-112">Azure — interfejs wiersza polecenia:<https://docs.microsoft.com/cli/azure/index></span><span class="sxs-lookup"><span data-stu-id="f3b7a-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index></span></span>
>
> <span data-ttu-id="f3b7a-113">Podsystem Windows dla systemu Linux:<https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="f3b7a-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="f3b7a-114">Tworzenie środowiska AKS na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="f3b7a-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="f3b7a-115">Istnieje kilka sposobów tworzenia środowiska AKS.</span><span class="sxs-lookup"><span data-stu-id="f3b7a-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="f3b7a-116">Można to zrobić za pomocą poleceń interfejsu wiersza polecenia platformy Azure lub przy użyciu Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="f3b7a-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="f3b7a-117">W tym miejscu możesz zapoznać się z przykładami za pomocą interfejsu wiersza polecenia platformy Azure, aby utworzyć klaster i Azure Portal, aby przejrzeć wyniki.</span><span class="sxs-lookup"><span data-stu-id="f3b7a-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="f3b7a-118">Musisz również mieć polecenia kubectl i Docker na komputerze deweloperskim.</span><span class="sxs-lookup"><span data-stu-id="f3b7a-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="f3b7a-119">Tworzenie klastra AKS</span><span class="sxs-lookup"><span data-stu-id="f3b7a-119">Create the AKS cluster</span></span>

<span data-ttu-id="f3b7a-120">Utwórz klaster AKS przy użyciu tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="f3b7a-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="f3b7a-121">Po zakończeniu zadania tworzenia można zobaczyć AKS utworzone w Azure Portal:</span><span class="sxs-lookup"><span data-stu-id="f3b7a-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="f3b7a-122">Grupa zasobów:</span><span class="sxs-lookup"><span data-stu-id="f3b7a-122">The resource group:</span></span>

![Widok przeglądarki grupy zasobów usługi Azure AKS.](media/aks-resource-group-view.png)

<span data-ttu-id="f3b7a-124">**Rysunek 4-17**.</span><span class="sxs-lookup"><span data-stu-id="f3b7a-124">**Figure 4-17**.</span></span> <span data-ttu-id="f3b7a-125">AKS widok grupy zasobów na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="f3b7a-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="f3b7a-126">Klaster AKS:</span><span class="sxs-lookup"><span data-stu-id="f3b7a-126">The AKS cluster:</span></span>

![Widok przeglądarki grupy zasobów AKS.](media/aks-cluster-view.png)

<span data-ttu-id="f3b7a-128">**Rysunek 4-18**.</span><span class="sxs-lookup"><span data-stu-id="f3b7a-128">**Figure 4-18**.</span></span> <span data-ttu-id="f3b7a-129">Widok AKS na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="f3b7a-129">AKS view from Azure.</span></span>

<span data-ttu-id="f3b7a-130">Można również wyświetlić węzeł utworzony przy użyciu `Azure-CLI` i. `Kubectl`</span><span class="sxs-lookup"><span data-stu-id="f3b7a-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="f3b7a-131">Po pierwsze, pobieranie poświadczeń:</span><span class="sxs-lookup"><span data-stu-id="f3b7a-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Dane wyjściowe konsoli z powyższego polecenia: Scalono "MsSampleK8Cluster jako bieżący kontekst w/root/.Kube/config.](media/get-credentials-command-result.png)

<span data-ttu-id="f3b7a-133">**Rysunek 4-19**.</span><span class="sxs-lookup"><span data-stu-id="f3b7a-133">**Figure 4-19**.</span></span> <span data-ttu-id="f3b7a-134">`aks get-credentials`wynik polecenia.</span><span class="sxs-lookup"><span data-stu-id="f3b7a-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="f3b7a-135">A następnie pobieranie węzłów z polecenia kubectl:</span><span class="sxs-lookup"><span data-stu-id="f3b7a-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Dane wyjściowe konsoli z powyższego polecenia: Lista węzłów o stanie, wieku (czasie wykonywania) i wersji](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="f3b7a-137">**Rysunek 4-20**.</span><span class="sxs-lookup"><span data-stu-id="f3b7a-137">**Figure 4-20**.</span></span> <span data-ttu-id="f3b7a-138">`kubectl get nodes`wynik polecenia.</span><span class="sxs-lookup"><span data-stu-id="f3b7a-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f3b7a-139">[Poprzedni](orchestrate-high-scalability-availability.md)
>[Następny](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="f3b7a-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
