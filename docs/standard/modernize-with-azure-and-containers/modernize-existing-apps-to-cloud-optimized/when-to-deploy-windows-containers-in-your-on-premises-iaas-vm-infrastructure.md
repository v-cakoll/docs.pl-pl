---
title: Kiedy należy wdrażać kontenery systemu Windows w lokalnej infrastrukturze maszyn wirtualnych IaaS
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Kiedy należy wdrażać kontenery Windows w lokalnej infrastrukturze maszyn wirtualnych IaaS
ms.date: 04/28/2018
ms.openlocfilehash: 5986073e295eeba5921a2d899b236c68a27251fd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643768"
---
# <a name="when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure"></a><span data-ttu-id="b749c-103">Kiedy należy wdrażać kontenery systemu Windows w lokalnej infrastrukturze maszyn wirtualnych IaaS</span><span class="sxs-lookup"><span data-stu-id="b749c-103">When to deploy Windows Containers in your on-premises IaaS VM infrastructure</span></span>

- <span data-ttu-id="b749c-104">Twoja organizacja może nie być gotowa do przeniesienia do chmury lub może nie być możliwe przeniesienie do chmury z przyczyn biznesowych.</span><span class="sxs-lookup"><span data-stu-id="b749c-104">Your organization might not be ready to move to the cloud, or it might not be able to move to the cloud for a business reason.</span></span> <span data-ttu-id="b749c-105">Ale można nadal uzyskać korzyści z używania kontenerów Windows w własnymi centrami danych.</span><span class="sxs-lookup"><span data-stu-id="b749c-105">But, you can still get the benefits of using Windows Containers in your own datacenters.</span></span>

- <span data-ttu-id="b749c-106">Może mieć inne artefakty, które są używane w środowisku lokalnym i który może spowolnić możesz podczas próby przeniesienia do chmury.</span><span class="sxs-lookup"><span data-stu-id="b749c-106">You might have other artifacts that are being used on-premises, and which might slow you down when you try to move to the cloud.</span></span> <span data-ttu-id="b749c-107">Na przykład zabezpieczeń i uwierzytelniania zależności za pomocą usługi Active Directory lokalnego systemu Windows Server lub innych zasobów w środowisku lokalnym.</span><span class="sxs-lookup"><span data-stu-id="b749c-107">For example, security or authentication dependencies with on-premises Windows Server Active Directory, or any other on-premises asset.</span></span>

- <span data-ttu-id="b749c-108">W przypadku uruchomienia przy użyciu kontenerów Windows już dziś, których wprowadzanie umożliwia stopniowej migracji do chmury jutro znacznie lepszej pozycji.</span><span class="sxs-lookup"><span data-stu-id="b749c-108">If you start using Windows Containers today, you can make a phased migration to the cloud tomorrow from a much better position.</span></span> <span data-ttu-id="b749c-109">Kontenery Windows staje się jednostką wdrożenia dla każdej chmury i z nie blokady.</span><span class="sxs-lookup"><span data-stu-id="b749c-109">Windows Containers is becoming a unit of deployment for any cloud, with no lock-in.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b749c-110">[Poprzednie](when-not-to-deploy-to-windows-containers.md)
>[dalej](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="b749c-110">[Previous](when-not-to-deploy-to-windows-containers.md)
[Next](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)</span></span>
