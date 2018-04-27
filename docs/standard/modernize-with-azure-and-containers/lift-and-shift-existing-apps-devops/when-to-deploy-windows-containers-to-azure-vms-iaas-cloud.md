---
title: Kiedy należy wdrożyć kontenery systemu Windows na maszynach wirtualnych platformy Azure (IaaS w chmurze)
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Kiedy należy wdrożyć kontenery systemu Windows na maszynach wirtualnych platformy Azure (IaaS w chmurze)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d1a9f0593b4b84cbe25da9e4164f4ecbe8513831
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="8dd60-103">Kiedy należy wdrożyć kontenery systemu Windows na maszynach wirtualnych platformy Azure (IaaS w chmurze)</span><span class="sxs-lookup"><span data-stu-id="8dd60-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="8dd60-104">Jeśli organizacja używa maszynach wirtualnych platformy Azure, nawet jeśli używana jest również kontenery systemu Windows, to nadal zajmowanie IaaS.</span><span class="sxs-lookup"><span data-stu-id="8dd60-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="8dd60-105">Oznacza to tej obsłudze operacje infrastruktury, poprawek systemu operacyjnego maszyny Wirtualnej i złożoności infrastruktury dla aplikacji o wysokiej skalowalności gdy należy wdrożyć na wiele maszyn wirtualnych w infrastrukturze równoważeniem obciążenia.</span><span class="sxs-lookup"><span data-stu-id="8dd60-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="8dd60-106">Główne scenariusze przy użyciu kontenery systemu Windows w maszynie Wirtualnej platformy Azure są:</span><span class="sxs-lookup"><span data-stu-id="8dd60-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

-   <span data-ttu-id="8dd60-107">**Tworzenie/testowanie środowiska**: A maszyna wirtualna w chmurze jest idealne w przypadku projektowania i testowania w chmurze.</span><span class="sxs-lookup"><span data-stu-id="8dd60-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="8dd60-108">Można szybko utworzyć lub Zatrzymaj środowisko, w zależności od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="8dd60-108">You can rapidly create or stop the environment depending on your needs.</span></span>

-   <span data-ttu-id="8dd60-109">**Skalowalność małych i średnich musi**: W scenariuszach, w którym mogą być wymagane kilka maszyn wirtualnych do środowiska produkcyjnego, zarządzanie niewielkiej liczby maszyn wirtualnych może być ekonomiczny dopóki nie można przenieść do bardziej zaawansowanych środowisk PaaS, takich jak orchestrators.</span><span class="sxs-lookup"><span data-stu-id="8dd60-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

-   <span data-ttu-id="8dd60-110">**Środowisku produkcyjnym z użyciem istniejących narzędzi wdrażania**: użytkownik może przenoszenie ze środowiska lokalnego, w którym zainwestowały w menu Narzędzia, aby złożone wdrożenia maszyn wirtualnych i serwery bez systemu operacyjnego (na przykład Puppet lub podobne narzędzia).</span><span class="sxs-lookup"><span data-stu-id="8dd60-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="8dd60-111">Można przenieść do chmury przy minimalnych zmianach do procedur wdrażania środowiska produkcyjnego, można nadal używać tych narzędzi do wdrażania na maszynach wirtualnych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="8dd60-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="8dd60-112">Jednak należy używanie kontenerów Windows jednostką wdrożenia celu usprawnienie obsługi wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="8dd60-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="8dd60-113">[Poprzednie](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[dalej](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="8dd60-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
