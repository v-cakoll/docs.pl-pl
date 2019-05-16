---
title: Kiedy należy wdrażać kontenery Windows do usługi Azure Container Instances (ACI)
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Kiedy należy wdrażać kontenery Windows do usługi Azure Container Instances (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 9bfa0688d07bd04964a1b28f688f125b5bcd2299
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638924"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="c6bad-103">Kiedy należy wdrażać kontenery Windows do usługi Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="c6bad-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="c6bad-104">Usługa Azure Container Instances, jest główne korzyści, że można następnie od razu wdrażać kontenery do niego, i nie trzeba utrzymywać w tym środowisku, nie trzeba uaktualnianie/poprawianie w systemie operacyjnym lub maszyn wirtualnych, wszystkie, które jest przejrzysta i po prostu wdrażasz kontenery w środowisku z gotowych do użycia.</span><span class="sxs-lookup"><span data-stu-id="c6bad-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="c6bad-105">Przyczyny i scenariusze, jeśli chcesz użyć usługi ACI są podobne do główne scenariusze, w przypadku użycia maszyn wirtualnych platformy Azure z kontenerów, więc po prostu, główne scenariusze dotyczące korzystania z usługi Azure Container Instances są:</span><span class="sxs-lookup"><span data-stu-id="c6bad-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="c6bad-106">**Scenariusze tworzenia i testowania**</span><span class="sxs-lookup"><span data-stu-id="c6bad-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="c6bad-107">**Automatyzacja zadań**</span><span class="sxs-lookup"><span data-stu-id="c6bad-107">**Task automation**</span></span>
- <span data-ttu-id="c6bad-108">**Ciągła Integracja/ciągłe wdrażanie agentów**</span><span class="sxs-lookup"><span data-stu-id="c6bad-108">**CI/CD agents**</span></span>
- <span data-ttu-id="c6bad-109">**Przetwarzanie wsadowe małych/skalowanie**</span><span class="sxs-lookup"><span data-stu-id="c6bad-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="c6bad-110">**Prostych aplikacji sieci web**</span><span class="sxs-lookup"><span data-stu-id="c6bad-110">**Simple web apps**</span></span>

<span data-ttu-id="c6bad-111">Scenariusz aplikacji prostą jest uczciwe scenariusz dotyczący usługi ACI, ale weź pod uwagę, że od czasu w usłudze ACI może mieć tylko wystąpienie jednego kontenera dla obrazu kontenera, nie będziesz mieć wysokiej dostępności i ma ograniczoną skalowalność.</span><span class="sxs-lookup"><span data-stu-id="c6bad-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="c6bad-112">Jednak nawet wtedy, gdy ACI zostanie uznany za infrastrukturę, ponieważ zawiera ono tylko jeden kontener wystąpień, ma ogromne korzyści w porównaniu do regularnego maszyn wirtualnych platformy Azure z systemem Windows Server.</span><span class="sxs-lookup"><span data-stu-id="c6bad-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="c6bad-113">Za pomocą usługi ACI po prostu wdrażanie kontenerów w środowisku z własnym utrzymywane w dobrym stanie, i płacisz tylko za tych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="c6bad-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="c6bad-114">Nie trzeba utrzymywać/aktualizacji/poprawek maszyn wirtualnych, więc jest znacznie lepszą platformę dla większości scenariuszy, w którym może być używany maszyn wirtualnych za pomocą kontenerów.</span><span class="sxs-lookup"><span data-stu-id="c6bad-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="c6bad-115">Za pomocą usługi ACI jest bardzo proste, po prostu wdrażanie kontenera, trzeba utworzyć środowisko maszyny Wirtualnej, po prostu wdrażanie kontenerów.</span><span class="sxs-lookup"><span data-stu-id="c6bad-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="c6bad-116">Dostępne są następujące główne korzyści z usługi Azure Container Instances (ACI):</span><span class="sxs-lookup"><span data-stu-id="c6bad-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="c6bad-117">Uruchamiaj kontenery bez potrzeby zarządzania serwerami</span><span class="sxs-lookup"><span data-stu-id="c6bad-117">Run containers without managing servers</span></span>
- <span data-ttu-id="c6bad-118">Zwiększ elastyczność dzięki użyciu kontenerów na żądanie</span><span class="sxs-lookup"><span data-stu-id="c6bad-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="c6bad-119">Wdrażanie kontenerów do chmury dzięki niezrównaną prostotą i szybkością — za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="c6bad-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="c6bad-120">Zabezpieczaj aplikacje za pomocą izolacji funkcji hypervisor</span><span class="sxs-lookup"><span data-stu-id="c6bad-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="c6bad-121">Krótko mówiąc za pomocą usługi ACI możesz opracowywać aplikacje szybko bez zarządzania maszynami wirtualnymi oraz konieczności korzystania z nowych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="c6bad-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="c6bad-122">To właśnie aplikacja w kontenerze uruchomiona w chmurze.</span><span class="sxs-lookup"><span data-stu-id="c6bad-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="c6bad-123">[Poprzednie](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [dalej](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="c6bad-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
