---
title: Scenariusze migracji do chmury hybrydowej
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Migrowanie do scenariuszy chmury hybrydowej
ms.date: 04/30/2018
ms.openlocfilehash: 5f0819495080bc29ed1239b4a7ab8af31141881b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318465"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="2871f-103">Scenariusze migracji do chmury hybrydowej</span><span class="sxs-lookup"><span data-stu-id="2871f-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="2871f-104">Niektóre organizacje i przedsiębiorstwa nie mogą migrować niektórych aplikacji do chmur publicznych, takich jak Microsoft Azure lub jakakolwiek inna chmura publiczna ze względu na przepisy lub ich własne zasady.</span><span class="sxs-lookup"><span data-stu-id="2871f-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="2871f-105">Istnieje jednak możliwość, że każda organizacja może korzystać z niektórych aplikacji w chmurze publicznej i innych aplikacjach lokalnych.</span><span class="sxs-lookup"><span data-stu-id="2871f-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="2871f-106">Jednak środowisko mieszane może prowadzić do nadmiernej złożoności w środowiskach ze względu na różne platformy i technologie używane w chmurach publicznych i w środowiskach lokalnych.</span><span class="sxs-lookup"><span data-stu-id="2871f-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="2871f-107">Firma Microsoft oferuje najlepsze rozwiązanie w chmurze hybrydowej, w którym można zoptymalizować istniejące zasoby lokalnie i w chmurze publicznej, zapewniając spójność w chmurze hybrydowej platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="2871f-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="2871f-108">Możesz zmaksymalizować istniejące umiejętności i uzyskać elastyczne, ujednolicone podejście do tworzenia aplikacji, które mogą być uruchamiane w chmurze lub lokalnie, dzięki Azure Stack (lokalnie) i na platformie Azure (w chmurze publicznej).</span><span class="sxs-lookup"><span data-stu-id="2871f-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="2871f-109">W przypadku bezpieczeństwa można scentralizować zarządzanie i zabezpieczenia w chmurze hybrydowej.</span><span class="sxs-lookup"><span data-stu-id="2871f-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="2871f-110">Możesz uzyskać kontrolę nad wszystkimi zasobami, od centrum danych do chmury, zapewniając Logowanie jednokrotne do aplikacji lokalnych i w chmurze.</span><span class="sxs-lookup"><span data-stu-id="2871f-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="2871f-111">Można to osiągnąć, rozszerzając Active Directory na chmurę hybrydową oraz używając usługi Identity Management.</span><span class="sxs-lookup"><span data-stu-id="2871f-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="2871f-112">Na koniec możesz bezproblemowo rozpowszechniać i analizować dane, używać tych samych języków zapytań dla zasobów w chmurze i lokalnych, a także stosować analizy i uczenie głębokie na platformie Azure, aby wzbogacać dane niezależnie od ich źródła.</span><span class="sxs-lookup"><span data-stu-id="2871f-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="2871f-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="2871f-113">Azure Stack</span></span>

<span data-ttu-id="2871f-114">Azure Stack to platforma chmury hybrydowej, która umożliwia dostarczanie usług platformy Azure z centrum danych organizacji.</span><span class="sxs-lookup"><span data-stu-id="2871f-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="2871f-115">Azure Stack zaprojektowano w celu obsługi nowych opcji dla nowoczesnych aplikacji w kluczowych scenariuszach, takich jak Edge i niepołączone środowiska, lub spełniających określone wymagania w zakresie zabezpieczeń i zgodności.</span><span class="sxs-lookup"><span data-stu-id="2871f-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="2871f-116">Rysunek 4-13 zawiera omówienie prawdziwej platformy chmury hybrydowej oferowanej przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2871f-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Diagram platformy firmy Microsoft w chmurze hybrydowej z Azure Stack i platformą Azure.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

<span data-ttu-id="2871f-118">**Rysunek 4-13.**</span><span class="sxs-lookup"><span data-stu-id="2871f-118">**Figure 4-13.**</span></span> <span data-ttu-id="2871f-119">Platforma firmy Microsoft w chmurze hybrydowej z Azure Stack i platformą Azure</span><span class="sxs-lookup"><span data-stu-id="2871f-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="2871f-120">Azure Stack jest oferowana w dwóch opcjach wdrażania, aby zaspokoić Twoje potrzeby:</span><span class="sxs-lookup"><span data-stu-id="2871f-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="2871f-121">Systemy Azure Stack zintegrowane</span><span class="sxs-lookup"><span data-stu-id="2871f-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="2871f-122">Azure Stack Development Kit</span><span class="sxs-lookup"><span data-stu-id="2871f-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="2871f-123">Systemy Azure Stack zintegrowane</span><span class="sxs-lookup"><span data-stu-id="2871f-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="2871f-124">Systemy Azure Stack zintegrowane są oferowane przez partnerstwo partnerów firmy Microsoft i sprzętu.</span><span class="sxs-lookup"><span data-stu-id="2871f-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="2871f-125">Partnerstwo tworzy rozwiązanie, które oferuje innowacyjność w chmurze, która jest zrównoważona prostoty zarządzania.</span><span class="sxs-lookup"><span data-stu-id="2871f-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="2871f-126">Ponieważ Azure Stack jest oferowana jako zintegrowany system sprzętu i oprogramowania, uzyskuje się odpowiednią ilość elastyczności i kontroli, a jednocześnie wdraża innowacje z chmury.</span><span class="sxs-lookup"><span data-stu-id="2871f-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="2871f-127">Azure Stack zakres zintegrowanych systemów w rozmiarze od 4 do 12 węzłów i są wspólnie obsługiwane przez partnera sprzętowego i firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2871f-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="2871f-128">Użyj Azure Stack zintegrowanych systemów, aby zaimplementować nowe scenariusze dla obciążeń produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="2871f-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="2871f-129">Azure Stack Development Kit</span><span class="sxs-lookup"><span data-stu-id="2871f-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="2871f-130">Microsoft Azure Stack Development Kit to wdrożenie z jednym węzłem Azure Stack, którego można użyć do obliczenia i poznania Azure Stack.</span><span class="sxs-lookup"><span data-stu-id="2871f-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="2871f-131">Możesz również użyć Azure Stack Development Kit jako środowiska deweloperskiego, w którym można opracowywać przy użyciu interfejsów API i narzędzi, które są spójne z platformą Azure.</span><span class="sxs-lookup"><span data-stu-id="2871f-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="2871f-132">Azure Stack Development Kit nie jest przeznaczona do użycia w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="2871f-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2871f-133">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="2871f-133">Additional resources</span></span>

- <span data-ttu-id="2871f-134">**Chmura hybrydowa platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="2871f-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="2871f-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="2871f-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="2871f-136">**Active Directory kont usługi dla kontenerów systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="2871f-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="2871f-137">**Tworzenie kontenera z obsługą Active Directory**</span><span class="sxs-lookup"><span data-stu-id="2871f-137">**Create a container with Active Directory support**</span></span>

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- <span data-ttu-id="2871f-138">**Licencjonowanie Korzyść użycia hybrydowego platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="2871f-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="2871f-139">[Poprzedni](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[Następny](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="2871f-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
