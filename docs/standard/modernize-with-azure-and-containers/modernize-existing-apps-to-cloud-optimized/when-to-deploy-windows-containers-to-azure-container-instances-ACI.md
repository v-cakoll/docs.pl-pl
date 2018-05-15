---
title: Podczas wdrażania systemu Windows kontenerów do wystąpień kontenera platformy Azure (ACI)
description: Modernizacji istniejących aplikacji .NET z kontenerami chmury Azure i systemu Windows | Podczas wdrażania systemu Windows kontenerów do wystąpień kontenera platformy Azure (ACI)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 3dc23c96543d9611763b571105f52b150dfec06f
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="f8971-103">Podczas wdrażania systemu Windows kontenerów do wystąpień kontenera platformy Azure (ACI)</span><span class="sxs-lookup"><span data-stu-id="f8971-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="f8971-104">Azure wystąpień kontenera głównego wartości oferty jest od razu wdrożeniem kontenerów do niego, a nie trzeba Obsługa tego środowiska, nie ma potrzeby uaktualniania/poprawka systemu operacyjnego underlaying lub maszyn wirtualnych, jest niewidoczny i wdrażać tylko kontenery w środowisku gotowe do użycia.</span><span class="sxs-lookup"><span data-stu-id="f8971-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlaying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="f8971-105">Przyczyny i scenariusze, w których chcesz użyć ACI są podobne do głównych scenariuszy, korzystając z maszyn wirtualnych platformy Azure z kontenerami, więc zasadniczo, są główne scenariusze za pomocą wystąpień kontenera platformy Azure:</span><span class="sxs-lookup"><span data-stu-id="f8971-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

-   <span data-ttu-id="f8971-106">**Scenariusze tworzenia/testowania**</span><span class="sxs-lookup"><span data-stu-id="f8971-106">**Dev/Test scenarios**</span></span>
-   <span data-ttu-id="f8971-107">**Automatyzacja zadań**</span><span class="sxs-lookup"><span data-stu-id="f8971-107">**Task automation**</span></span>
-   <span data-ttu-id="f8971-108">**Agenci CI/CD**</span><span class="sxs-lookup"><span data-stu-id="f8971-108">**CI/CD agents**</span></span>
-   <span data-ttu-id="f8971-109">**Przetwarzanie wsadowe małych/skali**</span><span class="sxs-lookup"><span data-stu-id="f8971-109">**Small/scale batch processing**</span></span>
-   <span data-ttu-id="f8971-110">**Aplikacje sieci web proste**</span><span class="sxs-lookup"><span data-stu-id="f8971-110">**Simple web apps**</span></span>

<span data-ttu-id="f8971-111">Prostego scenariusza aplikacji jest to odpowiedni scenariusz dla ACI, ale wziąć pod uwagę, że od czasu w ACI może zawierać tylko wystąpienia jeden kontener na obraz kontenera, nie będziesz mieć wysokiej dostępności i mają ograniczoną skalowalności.</span><span class="sxs-lookup"><span data-stu-id="f8971-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="f8971-112">Jednak nawet wtedy, gdy ACI jest uważany za infrastruktury, ponieważ zapewnia tylko jeden kontener wystąpień, brak ogromne korzyści w porównaniu do regularnych maszynach wirtualnych platformy Azure z systemem Windows Server.</span><span class="sxs-lookup"><span data-stu-id="f8971-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="f8971-113">ACI po prostu wdrażanie kontenerów do zapewnienia własnym środowiska i płacisz tylko dla tych kontenerach.</span><span class="sxs-lookup"><span data-stu-id="f8971-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="f8971-114">Obsługa/aktualizacji/poprawki maszyn wirtualnych, nie trzeba więc jest znacznie lepszą platformę dla większości scenariuszy, w których możesz używać maszyn wirtualnych z kontenerami.</span><span class="sxs-lookup"><span data-stu-id="f8971-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="f8971-115">Używanie ACI jest wprost do przodu, po prostu wdrożenia kontenera, nie istnieje potrzeba aby utworzyć środowisko maszyny Wirtualnej, po prostu wdrażanie kontenerów.</span><span class="sxs-lookup"><span data-stu-id="f8971-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="f8971-116">Główne zalety z wystąpień kontenera platformy Azure (ACI) to:</span><span class="sxs-lookup"><span data-stu-id="f8971-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

-   <span data-ttu-id="f8971-117">Uruchom kontenery bez zarządzanie serwerami</span><span class="sxs-lookup"><span data-stu-id="f8971-117">Run containers without managing servers</span></span>
-   <span data-ttu-id="f8971-118">Zwiększyć elastyczność z kontenerami na żądanie</span><span class="sxs-lookup"><span data-stu-id="f8971-118">Increase agility with containers on demand</span></span>
-   <span data-ttu-id="f8971-119">Wdrażanie kontenerów do chmury przy Niespotykana prostoty i szybkość — za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="f8971-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span> 
-   <span data-ttu-id="f8971-120">Zabezpieczenia aplikacji przy użyciu funkcji hypervisor izolacji</span><span class="sxs-lookup"><span data-stu-id="f8971-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="f8971-121">Krótko mówiąc z ACI można programować aplikacje fast bez zarządzania maszynami wirtualnymi lub do nowego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="f8971-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="f8971-122">Jest po prostu aplikacji, w kontenerze działającą w chmurze.</span><span class="sxs-lookup"><span data-stu-id="f8971-122">It's just your application, in a container, running in the cloud.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="f8971-123">[Poprzednie](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[dalej](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="f8971-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
