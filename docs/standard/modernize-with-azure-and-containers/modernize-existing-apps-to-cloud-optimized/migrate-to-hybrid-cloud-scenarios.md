---
title: Scenariusze migracji do chmury hybrydowej
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Migrowanie do scenariuszy hybrydowych w chmurze
ms.date: 04/30/2018
ms.openlocfilehash: 04c618681c61f5584e641e0a4735e1261ab34fa3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643718"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="113fa-103">Scenariusze migracji do chmury hybrydowej</span><span class="sxs-lookup"><span data-stu-id="113fa-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="113fa-104">Niektóre organizacje i przedsiębiorstwa, nie można migrować niektóre aplikacje do chmur publicznych, takich jak Microsoft Azure lub innej chmury publicznej ze względu na przepisy lub własnych zasad.</span><span class="sxs-lookup"><span data-stu-id="113fa-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="113fa-105">Jednak jest prawdopodobne, że każda organizacja może korzyści z posiadania niektóre z ich aplikacji w chmurze publicznej i innych aplikacji lokalnych.</span><span class="sxs-lookup"><span data-stu-id="113fa-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="113fa-106">Jednak, w środowisku mieszanym może prowadzić do nadmiernej złożoności w środowiskach ze względu na różne platformy i technologie używane w chmurach publicznych i środowiskach lokalnych.</span><span class="sxs-lookup"><span data-stu-id="113fa-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="113fa-107">Firma Microsoft oferuje najlepsze rozwiązanie hybrydowe w chmurze, jeden w którym można zoptymalizować posiadane zasoby w środowisku lokalnym i w chmurze publicznej, podczas gdy zapewnienia spójności w chmurze hybrydowej platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="113fa-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="113fa-108">Możesz zmaksymalizować posiadane umiejętności i Uzyskaj elastyczne, jednolite podejście do tworzenia aplikacji, które można uruchomić w chmurze lub lokalnie, dzięki usłudze Azure Stack (lokalnie) i Azure (w chmurze publicznej).</span><span class="sxs-lookup"><span data-stu-id="113fa-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="113fa-109">Jeśli chodzi o zabezpieczeń, można scentralizować zarządzania i zabezpieczeń między chmury hybrydowej.</span><span class="sxs-lookup"><span data-stu-id="113fa-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="113fa-110">Można uzyskać kontrolę nad wszystkimi zasobami z centrum danych w chmurze, udostępniając logowanie jednokrotne do środowiska lokalnego i aplikacje w chmurze.</span><span class="sxs-lookup"><span data-stu-id="113fa-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="113fa-111">Można to zrobić przez rozszerzenie usługi Active Directory do chmury hybrydowej i za pomocą zarządzania tożsamościami.</span><span class="sxs-lookup"><span data-stu-id="113fa-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="113fa-112">Na koniec można dystrybuować i bezproblemowo analizowanie danych, ten sam język zapytań na użytek zasoby w chmurze i lokalnych i stosować analizy i głębokiego uczenia na platformie Azure w celu wzbogacenia swoich danych, niezależnie od jej źródła.</span><span class="sxs-lookup"><span data-stu-id="113fa-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="113fa-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="113fa-113">Azure Stack</span></span>

<span data-ttu-id="113fa-114">Usługa Azure Stack to hybrydowa platforma w chmurze, która umożliwia dostarczanie usług platformy Azure z centrum danych Twojej organizacji.</span><span class="sxs-lookup"><span data-stu-id="113fa-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="113fa-115">Usługa Azure Stack jest przeznaczony do obsługi nowych opcji dla nowoczesnych aplikacji w kluczowych scenariuszy, takich jak krawędź i niepołączonych środowisk lub spełniając określone wymagania zabezpieczeń i zgodności.</span><span class="sxs-lookup"><span data-stu-id="113fa-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="113fa-116">Rysunek 4 — 13 przedstawiono omówienie platformy chmury hybrydowej, które firma Microsoft oferuje.</span><span class="sxs-lookup"><span data-stu-id="113fa-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Platforma chmury hybrydowej firmy Microsoft przy użyciu usługi Azure Stack i platformą Azure](./media/image13.jpg)

> <span data-ttu-id="113fa-118">**Rysunek 4 — 13.**</span><span class="sxs-lookup"><span data-stu-id="113fa-118">**Figure 4-13.**</span></span> <span data-ttu-id="113fa-119">Platforma chmury hybrydowej firmy Microsoft przy użyciu usługi Azure Stack i platformą Azure</span><span class="sxs-lookup"><span data-stu-id="113fa-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="113fa-120">Usługa Azure Stack jest oferowana w dwóch opcji wdrażania, stosownie do potrzeb:</span><span class="sxs-lookup"><span data-stu-id="113fa-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="113fa-121">Zintegrowane systemy usługi Azure Stack</span><span class="sxs-lookup"><span data-stu-id="113fa-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="113fa-122">Zestaw Azure Stack Development Kit</span><span class="sxs-lookup"><span data-stu-id="113fa-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="113fa-123">Zintegrowane systemy usługi Azure Stack</span><span class="sxs-lookup"><span data-stu-id="113fa-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="113fa-124">Stos zintegrowane systemy usługi Azure są oferowane za pośrednictwem powiązania partnerów firmy Microsoft i sprzętu.</span><span class="sxs-lookup"><span data-stu-id="113fa-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="113fa-125">Partnerstwo tworzy to rozwiązanie, które oferuje innowacji realizowany w chmurze, która jest równoważone za pomocą łatwość zarządzania.</span><span class="sxs-lookup"><span data-stu-id="113fa-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="113fa-126">Ponieważ usługi Azure Stack jest oferowany jako system zintegrowany sprzętu i oprogramowania, możesz uzyskać odpowiednim proporcjom elastyczności i kontroli, podczas nadal przyjmowania innowacji w chmurze.</span><span class="sxs-lookup"><span data-stu-id="113fa-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="113fa-127">Systemy usługi Azure Stack, zintegrowane w zakresie rozmiaru, od 4 do 12 węzłów i wspólnie są obsługiwane przez partnerów sprzętowych i firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="113fa-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="113fa-128">Użyj usługi Azure Stack zintegrowane systemy, aby wdrożyć nowe scenariusze dla obciążeń produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="113fa-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="113fa-129">Zestaw Azure Stack Development Kit</span><span class="sxs-lookup"><span data-stu-id="113fa-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="113fa-130">Microsoft Azure Stack Development Kit jest wdrożenia z pojedynczym węzłem usługi Azure Stack, którego można użyć do oceny i Dowiedz się więcej o usłudze Azure Stack.</span><span class="sxs-lookup"><span data-stu-id="113fa-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="113fa-131">Azure Stack Development Kit służy również jako środowiska deweloperskiego, w którym można tworzyć przy użyciu interfejsów API i narzędzia, które są zgodne z platformą Azure.</span><span class="sxs-lookup"><span data-stu-id="113fa-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="113fa-132">Usługa Azure Stack Development Kit nie jest przeznaczona do służyć jako środowisko produkcyjne.</span><span class="sxs-lookup"><span data-stu-id="113fa-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="113fa-133">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="113fa-133">Additional resources</span></span>

- <span data-ttu-id="113fa-134">**Chmury hybrydowej platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="113fa-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="113fa-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="113fa-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="113fa-136">**Konta usługi Active Directory dla Windows kontenery**</span><span class="sxs-lookup"><span data-stu-id="113fa-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="113fa-137">**Utwórz kontener z obsługą usługi Active Directory**</span><span class="sxs-lookup"><span data-stu-id="113fa-137">**Create a container with Active Directory support**</span></span>

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- <span data-ttu-id="113fa-138">**Licencjonowanie korzyści użycia hybrydowego platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="113fa-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="113fa-139">[Poprzednie](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[dalej](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="113fa-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
