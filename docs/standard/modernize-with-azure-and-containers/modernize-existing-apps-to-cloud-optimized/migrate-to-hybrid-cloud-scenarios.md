---
title: Migrowanie do scenariuszy hybrydowych chmury
description: Modernizacji istniejących aplikacji .NET z kontenerami chmury Azure i systemu Windows | Migrowanie do scenariuszy hybrydowych chmury
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 8885ee8fce4f8c11c14ee8936f3ee0ffd89ece04
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958207"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="010af-103">Migrowanie do scenariuszy hybrydowych chmury</span><span class="sxs-lookup"><span data-stu-id="010af-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="010af-104">Niektóre organizacje i przedsiębiorstwa nie może przeprowadzić migracji niektórych aplikacji do chmur publicznych, takich jak Microsoft Azure lub innych chmur publicznych ze względu na przepisy lub ich własnych zasad.</span><span class="sxs-lookup"><span data-stu-id="010af-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="010af-105">Istnieje prawdopodobieństwo, że każda organizacja może korzystać z o niektórych aplikacji w chmurze publicznej i innych aplikacji lokalnych.</span><span class="sxs-lookup"><span data-stu-id="010af-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="010af-106">Ale środowisku mieszanym może prowadzić do nadmiernej złożoności w środowiskach z powodu różnych platform i technologii używanych w chmur publicznych i lokalnych środowisk.</span><span class="sxs-lookup"><span data-stu-id="010af-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="010af-107">Firma Microsoft udostępnia najlepsze rozwiązanie chmury hybrydowej, jeden, w którym można zoptymalizować istniejących zasobów lokalnych i w chmurze publicznej, gdy zapewnienia spójności w chmurze hybrydowe platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="010af-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="010af-108">Można zmaksymalizować posiadane umiejętności i uzyskać elastyczną i ujednoliconego podejście do tworzenia aplikacji, które można uruchomić w chmurze lub lokalnie, dzięki użyciu stosu Azure (lokalnego) i Azure (w chmurze publicznej).</span><span class="sxs-lookup"><span data-stu-id="010af-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="010af-109">Jeśli chodzi o zabezpieczeń, można scentralizować zarządzania i bezpieczeństwo w chmurze hybrydowej.</span><span class="sxs-lookup"><span data-stu-id="010af-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="010af-110">Możesz uzyskać kontrolę nad wszystkie zasoby z centrum danych w chmurze, zapewniając rejestracji jednokrotnej do lokalnego i aplikacji w chmurze.</span><span class="sxs-lookup"><span data-stu-id="010af-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="010af-111">Można to zrobić przez rozszerzenie usługi Active Directory do chmury hybrydowej i za pomocą zarządzania tożsamościami.</span><span class="sxs-lookup"><span data-stu-id="010af-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="010af-112">Na koniec można dystrybuować i bezproblemowo analizowanie danych, użyj te same języki zapytania dla zasobów w chmurze i lokalnie i stosować analizy i bezpośrednie learning na platformie Azure wzbogacić, niezależnie od tego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="010af-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="010af-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="010af-113">Azure Stack</span></span>

<span data-ttu-id="010af-114">Stos Azure jest hybrydowe platformy w chmurze, który pozwala dostarczyć usług platformy Azure z centrum danych w organizacji.</span><span class="sxs-lookup"><span data-stu-id="010af-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="010af-115">Stos Azure umożliwia obsługę nowych opcji dla nowoczesnych aplikacji w różnych kluczowych scenariuszy, takich jak edge i środowisk odłączony lub spotkania szczególne wymagania zabezpieczeń i zgodności.</span><span class="sxs-lookup"><span data-stu-id="010af-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="010af-116">Rysunek 4-13 przedstawiono przegląd platformy chmury hybrydowego wartość true, które firma Microsoft oferuje.</span><span class="sxs-lookup"><span data-stu-id="010af-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Platforma firmy Microsoft hybrydowego chmurze ze stosu Azure i na platformie Azure](./media/image13.jpg)

> <span data-ttu-id="010af-118">**Rysunek 4-13.**</span><span class="sxs-lookup"><span data-stu-id="010af-118">**Figure 4-13.**</span></span> <span data-ttu-id="010af-119">Platforma firmy Microsoft hybrydowego chmurze ze stosu Azure i na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="010af-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="010af-120">Azure stosu jest oferowany dwie opcje wdrażania, dostosowane do potrzeb:</span><span class="sxs-lookup"><span data-stu-id="010af-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

-   <span data-ttu-id="010af-121">Stos Azure zintegrowanych systemów</span><span class="sxs-lookup"><span data-stu-id="010af-121">Azure Stack integrated systems</span></span>

-   <span data-ttu-id="010af-122">Azure stosu Development Kit</span><span class="sxs-lookup"><span data-stu-id="010af-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="010af-123">Stos Azure zintegrowanych systemów</span><span class="sxs-lookup"><span data-stu-id="010af-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="010af-124">Azure stosu zintegrowanych systemów są oferowane przez powiązanie partnerów firmy Microsoft i sprzętu.</span><span class="sxs-lookup"><span data-stu-id="010af-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="010af-125">Powiązanie tworzy rozwiązania, które oferuje innowacje realizowanych chmury na konto uproszczenie procesu zarządzania.</span><span class="sxs-lookup"><span data-stu-id="010af-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="010af-126">Ponieważ stos Azure jest oferowany jako zintegrowany system sprzętu i oprogramowania, należy pobrać jednostkom elastyczność i kontroli, podczas nadal przyjmowanie innowacji z chmury.</span><span class="sxs-lookup"><span data-stu-id="010af-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="010af-127">Azure stosu zintegrowanych systemów należeć do zakresu o rozmiarze od 4 do 12 węzłów i wspólnie są obsługiwane przez partnera sprzętu i firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="010af-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="010af-128">Użycie stosu Azure zintegrowanych systemów do zaimplementowania nowych scenariuszy dla obciążeń produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="010af-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="010af-129">Azure stosu Development Kit</span><span class="sxs-lookup"><span data-stu-id="010af-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="010af-130">Microsoft Azure stosu Development Kit to wdrożenie jednowęzłowej stosu Azure, której można użyć do oceny i Dowiedz się więcej o stosu Azure.</span><span class="sxs-lookup"><span data-stu-id="010af-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="010af-131">Umożliwia także zestaw deweloperski stosu Azure jako Środowisko deweloperskie, w którym można tworzyć przy użyciu interfejsów API i narzędzi, które są zgodne z platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="010af-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="010af-132">Azure stosu Development Kit nie jest przeznaczony do użycia jako środowiska produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="010af-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="010af-133">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="010af-133">Additional resources</span></span>

-   <span data-ttu-id="010af-134">**Chmura hybrydowa Azure**</span><span class="sxs-lookup"><span data-stu-id="010af-134">**Azure hybrid cloud**</span></span>

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   <span data-ttu-id="010af-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="010af-135">**Azure Stack**</span></span>

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   <span data-ttu-id="010af-136">**Konta usługi Active Directory dla Windows kontenerów**</span><span class="sxs-lookup"><span data-stu-id="010af-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   <span data-ttu-id="010af-137">**Tworzenie kontenera z obsługą usługi Active Directory**</span><span class="sxs-lookup"><span data-stu-id="010af-137">**Create a container with Active Directory support**</span></span>

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   <span data-ttu-id="010af-138">**Azure licencjonowania korzyści hybrydowego**</span><span class="sxs-lookup"><span data-stu-id="010af-138">**Azure Hybrid Benefit licensing**</span></span>

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
<span data-ttu-id="010af-139">[Poprzednie](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[dalej](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="010af-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
