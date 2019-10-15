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
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Scenariusze migracji do chmury hybrydowej

Niektóre organizacje i przedsiębiorstwa nie mogą migrować niektórych aplikacji do chmur publicznych, takich jak Microsoft Azure lub jakakolwiek inna chmura publiczna ze względu na przepisy lub ich własne zasady. Istnieje jednak możliwość, że każda organizacja może korzystać z niektórych aplikacji w chmurze publicznej i innych aplikacjach lokalnych. Jednak środowisko mieszane może prowadzić do nadmiernej złożoności w środowiskach ze względu na różne platformy i technologie używane w chmurach publicznych i w środowiskach lokalnych.

Firma Microsoft oferuje najlepsze rozwiązanie w chmurze hybrydowej, w którym można zoptymalizować istniejące zasoby lokalnie i w chmurze publicznej, zapewniając spójność w chmurze hybrydowej platformy Azure. Możesz zmaksymalizować istniejące umiejętności i uzyskać elastyczne, ujednolicone podejście do tworzenia aplikacji, które mogą być uruchamiane w chmurze lub lokalnie, dzięki Azure Stack (lokalnie) i na platformie Azure (w chmurze publicznej).

W przypadku bezpieczeństwa można scentralizować zarządzanie i zabezpieczenia w chmurze hybrydowej. Możesz uzyskać kontrolę nad wszystkimi zasobami, od centrum danych do chmury, zapewniając Logowanie jednokrotne do aplikacji lokalnych i w chmurze. Można to osiągnąć, rozszerzając Active Directory na chmurę hybrydową oraz używając usługi Identity Management.

Na koniec możesz bezproblemowo rozpowszechniać i analizować dane, używać tych samych języków zapytań dla zasobów w chmurze i lokalnych, a także stosować analizy i uczenie głębokie na platformie Azure, aby wzbogacać dane niezależnie od ich źródła.

## <a name="azure-stack"></a>Azure Stack

Azure Stack to platforma chmury hybrydowej, która umożliwia dostarczanie usług platformy Azure z centrum danych organizacji. Azure Stack zaprojektowano w celu obsługi nowych opcji dla nowoczesnych aplikacji w kluczowych scenariuszach, takich jak Edge i niepołączone środowiska, lub spełniających określone wymagania w zakresie zabezpieczeń i zgodności.

Rysunek 4-13 zawiera omówienie prawdziwej platformy chmury hybrydowej oferowanej przez firmę Microsoft.

![Diagram platformy firmy Microsoft w chmurze hybrydowej z Azure Stack i platformą Azure.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

**Rysunek 4-13.** Platforma firmy Microsoft w chmurze hybrydowej z Azure Stack i platformą Azure

Azure Stack jest oferowana w dwóch opcjach wdrażania, aby zaspokoić Twoje potrzeby:

- Systemy Azure Stack zintegrowane

- Azure Stack Development Kit

### <a name="azure-stack-integrated-systems"></a>Systemy Azure Stack zintegrowane

Systemy Azure Stack zintegrowane są oferowane przez partnerstwo partnerów firmy Microsoft i sprzętu. Partnerstwo tworzy rozwiązanie, które oferuje innowacyjność w chmurze, która jest zrównoważona prostoty zarządzania. Ponieważ Azure Stack jest oferowana jako zintegrowany system sprzętu i oprogramowania, uzyskuje się odpowiednią ilość elastyczności i kontroli, a jednocześnie wdraża innowacje z chmury. Azure Stack zakres zintegrowanych systemów w rozmiarze od 4 do 12 węzłów i są wspólnie obsługiwane przez partnera sprzętowego i firmę Microsoft. Użyj Azure Stack zintegrowanych systemów, aby zaimplementować nowe scenariusze dla obciążeń produkcyjnych.

### <a name="azure-stack-development-kit"></a>Azure Stack Development Kit

Microsoft Azure Stack Development Kit to wdrożenie z jednym węzłem Azure Stack, którego można użyć do obliczenia i poznania Azure Stack. Możesz również użyć Azure Stack Development Kit jako środowiska deweloperskiego, w którym można opracowywać przy użyciu interfejsów API i narzędzi, które są spójne z platformą Azure. Azure Stack Development Kit nie jest przeznaczona do użycia w środowisku produkcyjnym.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Chmura hybrydowa platformy Azure**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Active Directory kont usługi dla kontenerów systemu Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **Tworzenie kontenera z obsługą Active Directory**

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- **Licencjonowanie Korzyść użycia hybrydowego platformy Azure**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[Poprzedni](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[Następny](../walkthroughs-technical-get-started-overview.md)
