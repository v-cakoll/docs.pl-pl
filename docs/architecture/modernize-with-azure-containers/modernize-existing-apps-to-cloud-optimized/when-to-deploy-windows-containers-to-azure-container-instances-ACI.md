---
title: Kiedy wdrożyć kontenery systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)
description: Modernizacja istniejących aplikacji platformy .NET za pomocą kontenerów usługi Azure Cloud i Windows | Kiedy wdrożyć kontenery systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 6c889db6f0475f24a196144c7fb62faec4c173ed
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989158"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="dd0fd-103">Kiedy wdrożyć kontenery systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)</span><span class="sxs-lookup"><span data-stu-id="dd0fd-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="dd0fd-104">Głównym propozycja wartości wystąpienia kontenerów platformy Azure jest, że można od razu wdrożyć kontenery do niego i nie trzeba utrzymywać tego środowiska, nie trzeba uaktualnić/załatać podstawowy system operacyjny lub maszyn wirtualnych, wszystko, co jest przezroczyste i po prostu wdrożyć kontenery w środowisku gotowym do użycia.</span><span class="sxs-lookup"><span data-stu-id="dd0fd-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don't need to maintain that environment, you don't need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="dd0fd-105">Przyczyny i scenariusze, gdy chcesz użyć usługi ACI są podobne do głównych scenariuszy podczas korzystania z maszyn wirtualnych platformy Azure z kontenerami, więc zasadniczo główne scenariusze dotyczące korzystania z wystąpień kontenera platformy Azure są:</span><span class="sxs-lookup"><span data-stu-id="dd0fd-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="dd0fd-106">**Scenariusze deweloperów/testów**</span><span class="sxs-lookup"><span data-stu-id="dd0fd-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="dd0fd-107">**Automatyzacja zadań**</span><span class="sxs-lookup"><span data-stu-id="dd0fd-107">**Task automation**</span></span>
- <span data-ttu-id="dd0fd-108">**Agenci ciągłej integracji/ciągłego wdrażania**</span><span class="sxs-lookup"><span data-stu-id="dd0fd-108">**CI/CD agents**</span></span>
- <span data-ttu-id="dd0fd-109">**Przetwarzanie wsadowe na małą skalę**</span><span class="sxs-lookup"><span data-stu-id="dd0fd-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="dd0fd-110">**Proste aplikacje internetowe**</span><span class="sxs-lookup"><span data-stu-id="dd0fd-110">**Simple web apps**</span></span>

<span data-ttu-id="dd0fd-111">Scenariusz prostych aplikacji sieci web jest sprawiedliwy scenariusz dla ACI, ale wziąć pod uwagę, że ponieważ w ACI można mieć tylko jedno wystąpienie kontenera na obraz kontenera, nie będzie mieć wysoką dostępność i tylko ograniczoną skalowalność.</span><span class="sxs-lookup"><span data-stu-id="dd0fd-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won't have high availability and only have limited scalability.</span></span>

<span data-ttu-id="dd0fd-112">Jednak nawet wtedy, gdy usługa ACI jest uważana za infrastrukturę, ponieważ udostępnia tylko wystąpienia pojedynczego kontenera, istnieje ogromna korzyść w porównaniu do zwykłych maszyn wirtualnych platformy Azure z systemem Windows Server.</span><span class="sxs-lookup"><span data-stu-id="dd0fd-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="dd0fd-113">Z ACI, po prostu wdrożyć kontenery w środowisku samodzielnej konserwacji i po prostu zapłacić za te kontenery.</span><span class="sxs-lookup"><span data-stu-id="dd0fd-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="dd0fd-114">Nie trzeba obsługiwać/update/patch maszyn wirtualnych, więc jest to znacznie lepsza platforma dla większości scenariuszy, w których może być przy użyciu maszyn wirtualnych z kontenerami.</span><span class="sxs-lookup"><span data-stu-id="dd0fd-114">You don't need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="dd0fd-115">Za pomocą usługi ACI jest prosta, wystarczy wdrożyć kontener, nie ma potrzeby tworzenia środowiska maszyny Wirtualnej, które po prostu wdrożyć kontenery.</span><span class="sxs-lookup"><span data-stu-id="dd0fd-115">Using ACI is straight forward, you just deploy a container, there's no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="dd0fd-116">Główne zalety wystąpień kontenerów platformy Azure (ACI) to:</span><span class="sxs-lookup"><span data-stu-id="dd0fd-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="dd0fd-117">Uruchamianie kontenerów bez zarządzania serwerami</span><span class="sxs-lookup"><span data-stu-id="dd0fd-117">Run containers without managing servers</span></span>
- <span data-ttu-id="dd0fd-118">Zwiększ elastyczność dzięki kontenerom na żądanie</span><span class="sxs-lookup"><span data-stu-id="dd0fd-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="dd0fd-119">Wdrażaj kontenery w chmurze z niespotykaną dotąd prostotą i szybkością — za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="dd0fd-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="dd0fd-120">Zabezpieczanie aplikacji z izolacją hipernadzorcy</span><span class="sxs-lookup"><span data-stu-id="dd0fd-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="dd0fd-121">Krótko mówiąc, dzięki ACI możesz szybko tworzyć aplikacje bez zarządzania maszynami wirtualnymi lub konieczności uczenia się nowych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="dd0fd-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="dd0fd-122">To tylko aplikacja w kontenerze, działająca w chmurze.</span><span class="sxs-lookup"><span data-stu-id="dd0fd-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="dd0fd-123">[Poprzedni](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [następny](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="dd0fd-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
