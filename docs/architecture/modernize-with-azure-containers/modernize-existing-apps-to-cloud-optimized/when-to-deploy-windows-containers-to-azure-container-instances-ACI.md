---
title: Kiedy wdrażać kontenery systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Kiedy wdrażać kontenery systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676908"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="13c4b-103">Kiedy wdrażać kontenery systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)</span><span class="sxs-lookup"><span data-stu-id="13c4b-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="13c4b-104">Propozycja głównej wartości wystąpień kontenera azure polega na tym, że można od razu wdrożyć kontenery i nie trzeba utrzymywać tego środowiska, nie trzeba uaktualniać/łatać podstawowego systemu operacyjnego lub maszyn wirtualnych, wszystko, co jest przezroczyste i po prostu wdrożyć kontenery w środowisku gotowy do użycia.</span><span class="sxs-lookup"><span data-stu-id="13c4b-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="13c4b-105">Przyczyny i scenariusze, gdy chcesz użyć usługi ACI są podobne do głównych scenariuszy podczas korzystania z maszyn wirtualnych platformy Azure z kontenerami, więc w zasadzie główne scenariusze korzystania z wystąpień usługi Azure Container są:</span><span class="sxs-lookup"><span data-stu-id="13c4b-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="13c4b-106">**Scenariusze tworzenia/testowania**</span><span class="sxs-lookup"><span data-stu-id="13c4b-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="13c4b-107">**Automatyzacja zadań**</span><span class="sxs-lookup"><span data-stu-id="13c4b-107">**Task automation**</span></span>
- <span data-ttu-id="13c4b-108">**Agenci CI/CD**</span><span class="sxs-lookup"><span data-stu-id="13c4b-108">**CI/CD agents**</span></span>
- <span data-ttu-id="13c4b-109">**Przetwarzanie wsadowe na małą skalę**</span><span class="sxs-lookup"><span data-stu-id="13c4b-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="13c4b-110">**Proste aplikacje internetowe**</span><span class="sxs-lookup"><span data-stu-id="13c4b-110">**Simple web apps**</span></span>

<span data-ttu-id="13c4b-111">Prosty scenariusz aplikacji sieci web jest uczciwy scenariusz dla usługi ACI, ale należy wziąć pod uwagę, że ponieważ w aci można mieć tylko jedno wystąpienie kontenera na obraz kontenera, nie będzie miał wysoką dostępność i mają tylko ograniczoną skalowalność.</span><span class="sxs-lookup"><span data-stu-id="13c4b-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="13c4b-112">Jednak nawet wtedy, gdy usługa ACI jest uważana za infrastrukturę, ponieważ zapewnia tylko pojedyncze wystąpienia kontenera, istnieje ogromna korzyść w porównaniu do zwykłych maszyn wirtualnych platformy Azure z systemem Windows Server.</span><span class="sxs-lookup"><span data-stu-id="13c4b-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="13c4b-113">Dzięki aci wystarczy wdrożyć kontenery w środowisku samoobsługowym i po prostu zapłacić za te kontenery.</span><span class="sxs-lookup"><span data-stu-id="13c4b-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="13c4b-114">Nie trzeba obsługiwać/aktualizować/łatamaszyn wirtualnych, więc jest to znacznie lepsza platforma dla większości scenariuszy, w których może być przy użyciu maszyn wirtualnych z kontenerami.</span><span class="sxs-lookup"><span data-stu-id="13c4b-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="13c4b-115">Za pomocą ACI jest prosto do przodu, po prostu wdrożyć kontenera, nie ma potrzeby tworzenia środowiska maszyn wirtualnych po prostu wdrożyć kontenery.</span><span class="sxs-lookup"><span data-stu-id="13c4b-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="13c4b-116">Główne zalety wystąpienia kontenera platformy Azure (ACI) to:</span><span class="sxs-lookup"><span data-stu-id="13c4b-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="13c4b-117">Uruchamianie kontenerów bez zarządzania serwerami</span><span class="sxs-lookup"><span data-stu-id="13c4b-117">Run containers without managing servers</span></span>
- <span data-ttu-id="13c4b-118">Zwiększ elastyczność dzięki kontenerom na żądanie</span><span class="sxs-lookup"><span data-stu-id="13c4b-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="13c4b-119">Wdrażaj kontenery w chmurze z niespotykaną dotąd prostotą i szybkością — za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="13c4b-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="13c4b-120">Bezpieczne aplikacje dzięki izolacji hiperwizorowej</span><span class="sxs-lookup"><span data-stu-id="13c4b-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="13c4b-121">Krótko mówiąc, dzięki ACI możesz szybko tworzyć aplikacje bez zarządzania maszynami wirtualnymi lub konieczności uczenia się nowych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="13c4b-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="13c4b-122">To tylko aplikacja, w kontenerze, uruchomiony w chmurze.</span><span class="sxs-lookup"><span data-stu-id="13c4b-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="13c4b-123">[Poprzedni](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [następny](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="13c4b-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
