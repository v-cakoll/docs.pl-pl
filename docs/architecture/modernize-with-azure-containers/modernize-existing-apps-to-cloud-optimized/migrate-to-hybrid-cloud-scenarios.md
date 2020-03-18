---
title: Scenariusze migracji do chmury hybrydowej
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Migracja do scenariuszy chmury hybrydowej
ms.date: 04/30/2018
ms.openlocfilehash: dcbb799a45609f8bb811866c4041951abf1fda8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937362"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="c3610-103">Scenariusze migracji do chmury hybrydowej</span><span class="sxs-lookup"><span data-stu-id="c3610-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="c3610-104">Niektóre organizacje i przedsiębiorstwa nie mogą migrować niektórych swoich aplikacji do chmur publicznych, takich jak Microsoft Azure lub inna chmura publiczna z powodu przepisów lub własnych zasad.</span><span class="sxs-lookup"><span data-stu-id="c3610-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="c3610-105">Jest jednak prawdopodobne, że każda organizacja może skorzystać z posiadania niektórych swoich aplikacji w chmurze publicznej i innych aplikacji lokalnych.</span><span class="sxs-lookup"><span data-stu-id="c3610-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="c3610-106">Jednak środowisko mieszane może prowadzić do nadmiernej złożoności w środowiskach ze względu na różne platformy i technologie używane w chmurach publicznych w porównaniu ze środowiskami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="c3610-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="c3610-107">Firma Microsoft zapewnia najlepsze rozwiązanie chmury hybrydowej, w którym można zoptymalizować istniejące zasoby lokalnie i w chmurze publicznej, zapewniając jednocześnie spójność w chmurze hybrydowej platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="c3610-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="c3610-108">Możesz zmaksymalizować istniejące umiejętności i uzyskać elastyczne, ujednolicone podejście do tworzenia aplikacji, które można uruchamiać w chmurze lub lokalnie, dzięki usłudze Azure Stack (lokalnie) i platformie Azure (chmura publiczna).</span><span class="sxs-lookup"><span data-stu-id="c3610-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="c3610-109">Jeśli chodzi o bezpieczeństwo, możesz scentralizować zarządzanie i bezpieczeństwo w chmurze hybrydowej.</span><span class="sxs-lookup"><span data-stu-id="c3610-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="c3610-110">Możesz uzyskać kontrolę nad wszystkimi zasobami, od centrum danych po chmurę, udostępniając logowanie jednoosobowe do aplikacji lokalnych i w chmurze.</span><span class="sxs-lookup"><span data-stu-id="c3610-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="c3610-111">Można to osiągnąć, rozszerzając usługę Active Directory do chmury hybrydowej i za pomocą zarządzania tożsamościami.</span><span class="sxs-lookup"><span data-stu-id="c3610-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="c3610-112">Na koniec można bezproblemowo rozpowszechniać i analizować dane, używać tych samych języków zapytań dla zasobów w chmurze i środowiska lokalnego oraz zastosować analizy i głębokie uczenie na platformie Azure, aby wzbogacić dane, niezależnie od ich źródła.</span><span class="sxs-lookup"><span data-stu-id="c3610-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="c3610-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="c3610-113">Azure Stack</span></span>

<span data-ttu-id="c3610-114">Usługa Azure Stack to hybrydowa platforma w chmurze, która umożliwia dostarczanie usług platformy Azure z centrum danych organizacji.</span><span class="sxs-lookup"><span data-stu-id="c3610-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="c3610-115">Usługa Azure Stack jest przeznaczona do obsługi nowych opcji dla nowoczesnych aplikacji w kluczowych scenariuszach, takich jak środowiska brzegowe i niepołączone lub spełniające określone wymagania dotyczące zabezpieczeń i zgodności.</span><span class="sxs-lookup"><span data-stu-id="c3610-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="c3610-116">Rysunek 4-13 przedstawia przegląd prawdziwej platformy chmury hybrydowej, którą oferuje firma Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c3610-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Diagram platformy chmury hybrydowej firmy Microsoft z usługą Azure Stack i platformą Azure.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

<span data-ttu-id="c3610-118">**Rysunek 4-13.**</span><span class="sxs-lookup"><span data-stu-id="c3610-118">**Figure 4-13.**</span></span> <span data-ttu-id="c3610-119">Hybrydowa platforma chmury firmy Microsoft z usługą Azure Stack i platformą Azure</span><span class="sxs-lookup"><span data-stu-id="c3610-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="c3610-120">Usługa Azure Stack jest oferowana w dwóch opcjach wdrażania, aby spełnić Twoje potrzeby:</span><span class="sxs-lookup"><span data-stu-id="c3610-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="c3610-121">Zintegrowane systemy usługi Azure Stack</span><span class="sxs-lookup"><span data-stu-id="c3610-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="c3610-122">Zestaw deweloperski usługi Azure Stack</span><span class="sxs-lookup"><span data-stu-id="c3610-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="c3610-123">Zintegrowane systemy usługi Azure Stack</span><span class="sxs-lookup"><span data-stu-id="c3610-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="c3610-124">Zintegrowane systemy usługi Azure Stack są oferowane w ramach partnerstwa firmy Microsoft i partnerów sprzętowych.</span><span class="sxs-lookup"><span data-stu-id="c3610-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="c3610-125">Partnerstwo tworzy rozwiązanie, które oferuje innowacje w chmurze, które jest zrównoważone z prostotą w zarządzaniu.</span><span class="sxs-lookup"><span data-stu-id="c3610-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="c3610-126">Ponieważ usługa Azure Stack jest oferowana jako zintegrowany system sprzętu i oprogramowania, otrzymujesz odpowiednią elastyczność i kontrolę, jednocześnie przyjmując innowacje z chmury.</span><span class="sxs-lookup"><span data-stu-id="c3610-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="c3610-127">Zintegrowane systemy usługi Azure Stack mają rozmiar od 4 do 12 węzłów i są obsługiwane wspólnie przez partnera sprzętowego i firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c3610-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="c3610-128">Użyj zintegrowanych systemów usługi Azure Stack, aby zaimplementować nowe scenariusze dla obciążeń produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="c3610-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="c3610-129">Zestaw deweloperski usługi Azure Stack</span><span class="sxs-lookup"><span data-stu-id="c3610-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="c3610-130">Microsoft Azure Stack Development Kit to wdrożenie usługi Azure Stack z jednym węzłem, za pomocą którego można oceniać usługę Azure Stack i dowiedzieć się więcej o niej.</span><span class="sxs-lookup"><span data-stu-id="c3610-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="c3610-131">Możesz również użyć zestawu Azure Stack Development Kit jako środowiska deweloperskiego, w którym można tworzyć przy użyciu interfejsów API i narzędzi zgodnych z platformą Azure.</span><span class="sxs-lookup"><span data-stu-id="c3610-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="c3610-132">Zestaw azure stack development kit nie jest przeznaczony do użycia jako środowisko produkcyjne.</span><span class="sxs-lookup"><span data-stu-id="c3610-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c3610-133">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="c3610-133">Additional resources</span></span>

- <span data-ttu-id="c3610-134">**Chmura hybrydowa platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="c3610-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="c3610-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="c3610-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="c3610-136">**Konta usług Active Directory dla kontenerów systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="c3610-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="c3610-137">**Tworzenie kontenera z obsługą usługi Active Directory**</span><span class="sxs-lookup"><span data-stu-id="c3610-137">**Create a container with Active Directory support**</span></span>

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- <span data-ttu-id="c3610-138">**Licencjonowanie korzyści hybrydowych platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="c3610-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="c3610-139">[Poprzedni](life-cycle-ci-cd-pipelines-devops-tools.md)
>[następny](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="c3610-139">[Previous](life-cycle-ci-cd-pipelines-devops-tools.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
