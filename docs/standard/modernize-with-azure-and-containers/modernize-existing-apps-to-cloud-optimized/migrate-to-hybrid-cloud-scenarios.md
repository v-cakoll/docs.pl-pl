---
title: Migrowanie do scenariuszy hybrydowych w chmurze
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Migrowanie do scenariuszy hybrydowych w chmurze
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 3d6fc272854654d890559d5db032b05667627d94
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147349"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Migrowanie do scenariuszy hybrydowych w chmurze

Niektóre organizacje i przedsiębiorstwa, nie można migrować niektóre aplikacje do chmur publicznych, takich jak Microsoft Azure lub innej chmury publicznej ze względu na przepisy lub własnych zasad. Jednak jest prawdopodobne, że każda organizacja może korzyści z posiadania niektóre z ich aplikacji w chmurze publicznej i innych aplikacji lokalnych. Jednak, w środowisku mieszanym może prowadzić do nadmiernej złożoności w środowiskach ze względu na różne platformy i technologie używane w chmurach publicznych i środowiskach lokalnych.

Firma Microsoft oferuje najlepsze rozwiązanie hybrydowe w chmurze, jeden w którym można zoptymalizować posiadane zasoby w środowisku lokalnym i w chmurze publicznej, podczas gdy zapewnienia spójności w chmurze hybrydowej platformy Azure. Możesz zmaksymalizować posiadane umiejętności i Uzyskaj elastyczne, jednolite podejście do tworzenia aplikacji, które można uruchomić w chmurze lub lokalnie, dzięki usłudze Azure Stack (lokalnie) i Azure (w chmurze publicznej).

Jeśli chodzi o zabezpieczeń, można scentralizować zarządzania i zabezpieczeń między chmury hybrydowej. Można uzyskać kontrolę nad wszystkimi zasobami z centrum danych w chmurze, udostępniając logowanie jednokrotne do środowiska lokalnego i aplikacje w chmurze. Można to zrobić przez rozszerzenie usługi Active Directory do chmury hybrydowej i za pomocą zarządzania tożsamościami.

Na koniec można dystrybuować i bezproblemowo analizowanie danych, ten sam język zapytań na użytek zasoby w chmurze i lokalnych i stosować analizy i głębokiego uczenia na platformie Azure w celu wzbogacenia swoich danych, niezależnie od jej źródła.

## <a name="azure-stack"></a>Azure Stack

Usługa Azure Stack to hybrydowa platforma w chmurze, która umożliwia dostarczanie usług platformy Azure z centrum danych Twojej organizacji. Usługa Azure Stack jest przeznaczony do obsługi nowych opcji dla nowoczesnych aplikacji w kluczowych scenariuszy, takich jak krawędź i niepołączonych środowisk lub spełniając określone wymagania zabezpieczeń i zgodności.

Rysunek 4 — 13 przedstawiono omówienie platformy chmury hybrydowej, które firma Microsoft oferuje.

![Platforma chmury hybrydowej firmy Microsoft przy użyciu usługi Azure Stack i platformą Azure](./media/image13.jpg)

> **Rysunek 4 — 13.** Platforma chmury hybrydowej firmy Microsoft przy użyciu usługi Azure Stack i platformą Azure

Usługa Azure Stack jest oferowana w dwóch opcji wdrażania, stosownie do potrzeb:

-   Zintegrowane systemy usługi Azure Stack

-   Zestaw Azure Stack Development Kit

### <a name="azure-stack-integrated-systems"></a>Zintegrowane systemy usługi Azure Stack

Stos zintegrowane systemy usługi Azure są oferowane za pośrednictwem powiązania partnerów firmy Microsoft i sprzętu. Partnerstwo tworzy to rozwiązanie, które oferuje innowacji realizowany w chmurze, która jest równoważone za pomocą łatwość zarządzania. Ponieważ usługi Azure Stack jest oferowany jako system zintegrowany sprzętu i oprogramowania, możesz uzyskać odpowiednim proporcjom elastyczności i kontroli, podczas nadal przyjmowania innowacji w chmurze. Systemy usługi Azure Stack, zintegrowane w zakresie rozmiaru, od 4 do 12 węzłów i wspólnie są obsługiwane przez partnerów sprzętowych i firmy Microsoft. Użyj usługi Azure Stack zintegrowane systemy, aby wdrożyć nowe scenariusze dla obciążeń produkcyjnych.

### <a name="azure-stack-development-kit"></a>Zestaw Azure Stack Development Kit

Microsoft Azure Stack Development Kit jest wdrożenia z pojedynczym węzłem usługi Azure Stack, którego można użyć do oceny i Dowiedz się więcej o usłudze Azure Stack. Azure Stack Development Kit służy również jako środowiska deweloperskiego, w którym można tworzyć przy użyciu interfejsów API i narzędzia, które są zgodne z platformą Azure. Usługa Azure Stack Development Kit nie jest przeznaczona do służyć jako środowisko produkcyjne.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Chmury hybrydowej platformy Azure**

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   **Azure Stack**

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   **Konta usługi Active Directory dla Windows kontenery**

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   **Utwórz kontener z obsługą usługi Active Directory**

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   **Licencjonowanie korzyści użycia hybrydowego platformy Azure**

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
>[Poprzednie](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[dalej](../walkthroughs-technical-get-started-overview.md)