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
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Scenariusze migracji do chmury hybrydowej

Niektóre organizacje i przedsiębiorstwa nie mogą migrować niektórych swoich aplikacji do chmur publicznych, takich jak Microsoft Azure lub inna chmura publiczna z powodu przepisów lub własnych zasad. Jest jednak prawdopodobne, że każda organizacja może skorzystać z posiadania niektórych swoich aplikacji w chmurze publicznej i innych aplikacji lokalnych. Jednak środowisko mieszane może prowadzić do nadmiernej złożoności w środowiskach ze względu na różne platformy i technologie używane w chmurach publicznych w porównaniu ze środowiskami lokalnymi.

Firma Microsoft zapewnia najlepsze rozwiązanie chmury hybrydowej, w którym można zoptymalizować istniejące zasoby lokalnie i w chmurze publicznej, zapewniając jednocześnie spójność w chmurze hybrydowej platformy Azure. Możesz zmaksymalizować istniejące umiejętności i uzyskać elastyczne, ujednolicone podejście do tworzenia aplikacji, które można uruchamiać w chmurze lub lokalnie, dzięki usłudze Azure Stack (lokalnie) i platformie Azure (chmura publiczna).

Jeśli chodzi o bezpieczeństwo, możesz scentralizować zarządzanie i bezpieczeństwo w chmurze hybrydowej. Możesz uzyskać kontrolę nad wszystkimi zasobami, od centrum danych po chmurę, udostępniając logowanie jednoosobowe do aplikacji lokalnych i w chmurze. Można to osiągnąć, rozszerzając usługę Active Directory do chmury hybrydowej i za pomocą zarządzania tożsamościami.

Na koniec można bezproblemowo rozpowszechniać i analizować dane, używać tych samych języków zapytań dla zasobów w chmurze i środowiska lokalnego oraz zastosować analizy i głębokie uczenie na platformie Azure, aby wzbogacić dane, niezależnie od ich źródła.

## <a name="azure-stack"></a>Azure Stack

Usługa Azure Stack to hybrydowa platforma w chmurze, która umożliwia dostarczanie usług platformy Azure z centrum danych organizacji. Usługa Azure Stack jest przeznaczona do obsługi nowych opcji dla nowoczesnych aplikacji w kluczowych scenariuszach, takich jak środowiska brzegowe i niepołączone lub spełniające określone wymagania dotyczące zabezpieczeń i zgodności.

Rysunek 4-13 przedstawia przegląd prawdziwej platformy chmury hybrydowej, którą oferuje firma Microsoft.

![Diagram platformy chmury hybrydowej firmy Microsoft z usługą Azure Stack i platformą Azure.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

**Rysunek 4-13.** Hybrydowa platforma chmury firmy Microsoft z usługą Azure Stack i platformą Azure

Usługa Azure Stack jest oferowana w dwóch opcjach wdrażania, aby spełnić Twoje potrzeby:

- Zintegrowane systemy usługi Azure Stack

- Zestaw deweloperski usługi Azure Stack

### <a name="azure-stack-integrated-systems"></a>Zintegrowane systemy usługi Azure Stack

Zintegrowane systemy usługi Azure Stack są oferowane w ramach partnerstwa firmy Microsoft i partnerów sprzętowych. Partnerstwo tworzy rozwiązanie, które oferuje innowacje w chmurze, które jest zrównoważone z prostotą w zarządzaniu. Ponieważ usługa Azure Stack jest oferowana jako zintegrowany system sprzętu i oprogramowania, otrzymujesz odpowiednią elastyczność i kontrolę, jednocześnie przyjmując innowacje z chmury. Zintegrowane systemy usługi Azure Stack mają rozmiar od 4 do 12 węzłów i są obsługiwane wspólnie przez partnera sprzętowego i firmę Microsoft. Użyj zintegrowanych systemów usługi Azure Stack, aby zaimplementować nowe scenariusze dla obciążeń produkcyjnych.

### <a name="azure-stack-development-kit"></a>Zestaw deweloperski usługi Azure Stack

Microsoft Azure Stack Development Kit to wdrożenie usługi Azure Stack z jednym węzłem, za pomocą którego można oceniać usługę Azure Stack i dowiedzieć się więcej o niej. Możesz również użyć zestawu Azure Stack Development Kit jako środowiska deweloperskiego, w którym można tworzyć przy użyciu interfejsów API i narzędzi zgodnych z platformą Azure. Zestaw azure stack development kit nie jest przeznaczony do użycia jako środowisko produkcyjne.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Chmura hybrydowa platformy Azure**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Konta usług Active Directory dla kontenerów systemu Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **Tworzenie kontenera z obsługą usługi Active Directory**

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- **Licencjonowanie korzyści hybrydowych platformy Azure**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[Poprzedni](life-cycle-ci-cd-pipelines-devops-tools.md)
>[następny](../walkthroughs-technical-get-started-overview.md)
