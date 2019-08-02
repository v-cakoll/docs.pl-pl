---
title: Kiedy należy wdrażać kontenery systemu Windows do Azure Container Instances (ACI)
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Kiedy należy wdrażać kontenery systemu Windows do Azure Container Instances (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676908"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="0a6d4-103">Kiedy należy wdrażać kontenery systemu Windows do Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="0a6d4-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="0a6d4-104">Azure Container Instances propozycja wartości głównej polega na tym, że możesz od razu wdrożyć kontenery i nie musisz obsługiwać tego środowiska, nie musisz uaktualniać ani poprawiać bazowego systemu operacyjnego lub maszyn wirtualnych, a wszystko to jest niewidoczne. kontenery w gotowym do użycia środowisku.</span><span class="sxs-lookup"><span data-stu-id="0a6d4-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="0a6d4-105">Przyczyny i scenariusze, które należy stosować ACI, są podobne do głównych scenariuszy w przypadku używania maszyn wirtualnych platformy Azure z kontenerami, dlatego główne scenariusze używania Azure Container Instances są następujące:</span><span class="sxs-lookup"><span data-stu-id="0a6d4-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="0a6d4-106">**Scenariusze tworzenia i testowania**</span><span class="sxs-lookup"><span data-stu-id="0a6d4-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="0a6d4-107">**Automatyzacja zadań**</span><span class="sxs-lookup"><span data-stu-id="0a6d4-107">**Task automation**</span></span>
- <span data-ttu-id="0a6d4-108">**Agenci CI/CD**</span><span class="sxs-lookup"><span data-stu-id="0a6d4-108">**CI/CD agents**</span></span>
- <span data-ttu-id="0a6d4-109">**Małe/skalowane przetwarzanie wsadowe**</span><span class="sxs-lookup"><span data-stu-id="0a6d4-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="0a6d4-110">**Proste aplikacje sieci Web**</span><span class="sxs-lookup"><span data-stu-id="0a6d4-110">**Simple web apps**</span></span>

<span data-ttu-id="0a6d4-111">Scenariusz prostego programu Web Apps jest uczciwym scenariuszem dla ACI, ale należy wziąć pod uwagę, że ponieważ w ACI może istnieć tylko jedno wystąpienie kontenera dla każdego obrazu kontenera, nie ma wysokiej dostępności i ma ograniczoną skalowalność.</span><span class="sxs-lookup"><span data-stu-id="0a6d4-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="0a6d4-112">Jednak nawet jeśli ACI jest uznawany za infrastrukturę, ponieważ tylko zawiera ona pojedyncze wystąpienia kontenera, w porównaniu z regularnymi maszynami wirtualnymi platformy Azure w systemie Windows Server istnieje ogromna korzyść.</span><span class="sxs-lookup"><span data-stu-id="0a6d4-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="0a6d4-113">Dzięki usłudze ACI możesz wdrażać kontenery w środowisku z własnym obsługą i płacisz tylko za te kontenery.</span><span class="sxs-lookup"><span data-stu-id="0a6d4-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="0a6d4-114">Nie musisz obsługiwać ani aktualizować/poprawiać maszyn wirtualnych, więc jest to znacznie lepsza platforma dla większości scenariuszy, w których można używać maszyn wirtualnych z kontenerami.</span><span class="sxs-lookup"><span data-stu-id="0a6d4-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="0a6d4-115">Korzystanie z usługi ACI jest proste — wystarczy wdrożyć kontener, ale nie ma potrzeby tworzenia środowiska maszyny wirtualnej, które wdrażają kontenery.</span><span class="sxs-lookup"><span data-stu-id="0a6d4-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="0a6d4-116">Główne zalety Azure Container Instances (ACI) to:</span><span class="sxs-lookup"><span data-stu-id="0a6d4-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="0a6d4-117">Uruchamianie kontenerów bez zarządzania serwerami</span><span class="sxs-lookup"><span data-stu-id="0a6d4-117">Run containers without managing servers</span></span>
- <span data-ttu-id="0a6d4-118">Zwiększ elastyczność dzięki kontenerom na żądanie</span><span class="sxs-lookup"><span data-stu-id="0a6d4-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="0a6d4-119">Wdrażaj kontenery w chmurze z niepoprzednią prostotą i szybkością — za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="0a6d4-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="0a6d4-120">Zabezpieczanie aplikacji z izolacją funkcji hypervisor</span><span class="sxs-lookup"><span data-stu-id="0a6d4-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="0a6d4-121">Krótko mówiąc, dzięki funkcji ACI można szybko opracowywać aplikacje bez konieczności zarządzania maszynami wirtualnymi ani uczenia się nowych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="0a6d4-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="0a6d4-122">Jest to tylko Twoja aplikacja w kontenerze działającym w chmurze.</span><span class="sxs-lookup"><span data-stu-id="0a6d4-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="0a6d4-123">[Poprzedni](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)Następny
> [](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="0a6d4-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
