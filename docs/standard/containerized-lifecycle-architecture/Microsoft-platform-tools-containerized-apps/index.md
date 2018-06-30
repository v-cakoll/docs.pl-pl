---
title: Wprowadzenie do platformy firmy Microsoft i narzędzia dla aplikacji konteneryzowanych
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: b14d361fb93b98de68b828514c7ea72811075fb8
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106194"
---
# <a name="introduction-to-the-microsoft-platform-and-tools-for-containerized-apps"></a>Wprowadzenie do platformy firmy Microsoft i narzędzia dla aplikacji konteneryzowanych


Główne słupków przedstawiono na rysunku 3-1 w cyklu życia aplikacji Docker według rodzaju pracy realizowane przez kilka zespołów (Tworzenie aplikacji, procesów opracowywania oprogramowania infrastruktury i zarządzania IT oraz działań). Zazwyczaj w przedsiębiorstwie, profile "osoba" odpowiedzialny za każdego obszaru są różne. Dlatego są umiejętności ich.

![](./media/image1.png)

Rysunek 3-1: główne słupków w cyklu życia dla konteneryzowanych Docker aplikacji za pomocą platformy firmy Microsoft i narzędzia

A konteneryzowanych Docker cyklu przepływu pracy można początkowo przetestowanego na podstawie "domyślnie produktu możliwości wyboru," ułatwia deweloperom szybsza, ale jest podstawą, że pod maską musi istnieć otwartej struktury, dzięki czemu będzie ona elastyczne przepływu pracy możliwość dostosowania do różnych kontekstach z każdej organizacji lub przedsiębiorstwa. Infrastruktura przepływu pracy (składnikami i produktami) musi być wystarczająco elastyczny, aby obejmować każda firma będzie miała w przyszłości, nawet zdolność wymiany rozwoju lub DevOps produktów do innych użytkowników w środowisku. To elastyczność, przejrzystości i szeroki wybór technologii platformy i infrastruktury są dokładnie priorytetów firmy Microsoft dla konteneryzowanych Docker aplikacji, zgodnie z objaśnieniem w kolejnych rozdziałach.

Tabela 3-1 pokazuje, że zamiar DevOps Microsoft konteneryzowanych aplikacji Docker ma na celu dostarczenie Otwieranie przepływu pracy DevOps, w którym można wybrać jakie produktów dla każdej fazy (Microsoft lub innych firm) zapewniają uproszczoną przepływu pracy która zawiera już połączony "przez domyślny produktów"; w związku z tym należy można szybko rozpocząć przedsiębiorstw DevOps przepływu pracy dla aplikacji Docker.

Tabela 3-1: Otwórz DevOps przepływu pracy innych technologii

| Host | Technologii firmy Microsoft | Innych firm — podłączany Azure |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Platformy Docker aplikacji   | • Programu Microsoft Visual Studio i kodu programu Visual Studio<br /> • .NET<br /> Usługa kontenera platformy Microsoft Azure •<br /> • Usługi azure Service Fabric<br /> • Rejestru kontenera platformy azure<br /> | • Dowolnego edytora kodu (na przykład Sublime)<br /> • Dowolnego języka (Node.js, Java, przejdź itp.)<br /> • Wszelkie orchestrator i harmonogramu<br /> • Dowolnego rejestru Docker<br /> |
| Opracowywania oprogramowania dla aplikacji Docker     | • Visual Studio Team Services<br /> • Microsoft Team Foundation Server<br /> • Usługi kontenera platformy azure<br /> • Usługi azure Service Fabric<br /> | • GitHub, Git, Subversion, etc.<br /> • Jenkins, Chef, Puppet, Velocity, CircleCI, TravisCI, etc.<br /> • Lokalnego centrum danych Docker, Docker Swarm, Mesos DC/OS, Kubernetes, itp.<br /> |
| Zarządzanie i monitorowanie  | • Operations Management Suite<br /> • Applications Insights<br /> | • Marathon, Chronos itp.<br />

Platforma firmy Microsoft i narzędzia dla aplikacji Docker konteneryzowanych, zgodnie z definicją w tabeli 3-1, obejmuje następujące składniki:

-   **Platforma do tworzenia aplikacji Docker** rozwoju usług lub kolekcję usług, które tworzą "aplikacji". Platformy programistycznej udostępnia deweloperom pracy wymaga przed wypychanie ich kod do repozytorium kodu udostępnionego. Tworzenie usług, wdrożony jako kontenery, są bardzo podobne do rozwoju o tej samej aplikacji lub usług bez Docker. Nadal preferowany język (.NET, Node.js, przejdź itp.) i preferowany edytor lub środowiska IDE programu Visual Studio lub Visual Studio Code. Zamiast wziąć pod uwagę Docker lokalizację docelową wdrożenia, jednak opracowanie usług w środowisku Docker. Tworzenia, uruchamiania, testowania i debugowania kodu w kontenerach lokalnie, zapewniając środowisko docelowe w czasie opracowywania. Zapewniając środowisko docelowe lokalnie, kontenery Docker zdefiniować co znacząco pomoże Ci zwiększyć cykl życia DevOps. Visual Studio i Visual Studio Code są rozszerzenia do integracji kontenery Docker w procesie tworzenia aplikacji.

-   **Opracowywania oprogramowania dla aplikacji Docker** deweloperom tworzenie aplikacji platformy Docker można używać programu Visual Studio Team Services (VSTS) lub inny produkt innej firmy, takich jak Wpięć, budować zaawansowane automatycznego zarządzania cyklem życia aplikacji (ALM).

Z programu VSTS, deweloperzy mogą tworzyć ukierunkowane kontenera DevOps dla procesu szybkie, iteracyjną, która obejmuje kodu źródłowego kontroli z dowolnego miejsca (VSTS Git, GitHub, wszelkie zdalnego repozytorium Git lub Podwersją), ciągłej integracji (CI), testy jednostkowe wewnętrznego, między kontener/usługi integracji testy, ciągłego dostarczania (CD) i zarządzania zleceniami (RM). Deweloperzy mogą również zautomatyzować ich Docker aplikacji wersji w usłudze kontenera platformy Azure, od projektowania do środowisk przemieszczania i produkcji.

-   IT produkcji zarządzania i monitorowania.

**Zarządzanie** IT mogą zarządzać aplikacji produkcyjnych i usługi na kilka sposobów:

-   **Azure portal** Jeśli używasz orchestrators open source, usługi kontenera platformy Azure (ACS) oraz klastra narzędzia do zarządzania, takich jak Docker Datacenter i Mesosphere Marathon ułatwiają konfigurowanie i obsługa środowiska Docker. Jeśli używasz usługi Azure Service Fabric narzędzia Service Fabric Explorer umożliwia wizualizowanie i skonfigurować klaster.

-   **Narzędzia docker** można zarządzać aplikacjami kontenera za pomocą znanych narzędzi. Nie istnieje potrzeba zmiany istniejących rozwiązań dotyczących zarządzania Docker, aby przenieść kontenera obciążeń do chmury. Użyj narzędzi zarządzania aplikacji jest już znanych i połączenia za pomocą standardowych punktów końcowych interfejsu API programu orchestrator wybranych przez użytkownika. Za pomocą innych narzędzi innych firm można również Zarządzaj aplikacjami Docker, takich jak Docker centrum danych lub nawet narzędzi interfejsu wiersza polecenia Docker.

-   **Narzędzia open source** ACS ponieważ ujawnia standardowe punkty końcowe interfejsu API aparat aranżacji, najbardziej popularnych narzędzi są zgodne z ACS oraz, w większości przypadków będzie działać bez — wizualizatorów, monitorowania, w tym narzędzia wiersza polecenia, a nawet przyszłych narzędzia, gdy będą one dostępne.

**Monitorowanie** podczas uruchamiania środowisk produkcyjnych, można monitorować każdy kąt za pomocą następujących:

-   **Operations Management Suite (OMS)** "OMS kontenera rozwiązanie" można zarządzać i monitorować hostów Docker i kontenery poprzez wyświetlenie informacji o Twojej kontenery i hosty kontenera skutkującej, kontenery, które są uruchomione lub nie powiodło się, i dzienniki demona i kontener Docker. Przedstawia on także metryki wydajności, np. Procesora, pamięci, sieci i magazynu dla kontenera i hostów ułatwiające rozwiązywanie problemów i znaleźć zakłócenia sąsiada kontenerów.

-   **Usługa Application Insights** umożliwia monitorowanie aplikacji Docker produkcji, konfigurując po prostu jej zestawu SDK do usługi tak, aby uzyskać dane telemetryczne z aplikacji.

W związku z tym firma Microsoft oferuje pełną podstawę dla end-to-end konteneryzowanych Docker cyklu życia aplikacji. Jest jednak *kolekcji produktów i technologii, które umożliwiają opcjonalnie wybierz i zintegrować z istniejącym narzędzi i przetwarza*. Elastyczność w szerokie podejście wraz z siły szczegółowo funkcji umieszczania firmy Microsoft w położeniu silne konteneryzowanych tworzenie aplikacji platformy Docker.

>[!div class="step-by-step"]
[Poprzednie](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
[dalej](../design-develop-containerized-apps/index.md)
