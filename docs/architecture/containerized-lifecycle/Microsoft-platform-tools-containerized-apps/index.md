---
title: Wprowadzenie do platformy i narzędzi firmy Microsoft dla aplikacji konteneryzowanych
description: Poznaj oferty firmy Microsoft do obsługi cyklu życia aplikacji Platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 9c8c0f5688bf226351abfc7bf52d4ace05f8c6d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73738088"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Wprowadzenie do platformy i narzędzi firmy Microsoft dla aplikacji konteneryzowanych

*Wizja: Tworzenie elastycznego, klasy korporacyjnej, konteneryzowanego cyklu życia aplikacji, który obejmuje rozwój, operacje IT i zarządzanie produkcją.*

Rysunek 3-1 przedstawia główne filary w cyklu życia aplikacji platformy Docker sklasyfikowanych według typu pracy dostarczanej przez wiele zespołów (tworzenie aplikacji, procesy infrastruktury DevOps oraz zarządzanie i operacje IT). Zazwyczaj w przedsiębiorstwie profile "persona" odpowiedzialne za każdy obszar są różne. Tak samo jak ich umiejętności.

:::image type="complex" source="./media/index/microsoft-tools-contanerized-docker-app.png" alt-text="Diagram przedstawiający narzędzia firmy Microsoft potrzebne do obsługi aplikacji platformy Docker.":::
Narzędzia firmy Microsoft. Dla obciążenia opracowania/projektowania: Aparat platformy Docker dla systemu Windows, VS i VS Code, .NET Core, Usługi Azure Kubernetes. Dla obciążenia kompilacji/testowania/wysyłki: Azure DevOps, Team Foundation Server, Docker CLI, Azure Kubernetes Service. W przypadku uruchamiania/monitorowania/zarządzania obciążeniem: Azure Monitor, usługi Azure Azure Kubernetes Usługi Azure azure, sieć szkieletowa usług, inne koordynatory.
:::image-end:::

**Rysunek 3-1.** Główne filary cyklu życia konteneryzowanych aplikacji Docker z platformą i narzędziami firmy Microsoft

Konteneryzowany przepływ pracy cyklu życia platformy Docker może być początkowo nakazowy w oparciu o "domyślnie domyślne wybory produktów", co ułatwia deweloperom szybsze rozpoczęcie pracy, ale jest fundamentalne, że pod maską musi istnieć otwarta struktura, aby była to elastyczny przepływ pracy umożliwiający dostosowanie się do różnych kontekstów z każdej organizacji lub przedsiębiorstwa. Infrastruktura przepływu pracy (składniki i produkty) musi być wystarczająco elastyczna, aby objąć środowisko, które każda firma będzie miała w przyszłości, nawet będąc w stanie zamienić produkty deweloperów lub DevOps na inne. Ta elastyczność, otwartość i szeroki wybór technologii w platformie i infrastrukturze są właśnie priorytetami firmy Microsoft dla konteneryzowanych aplikacji platformy Docker, jak wyjaśniono w kolejnych rozdziałach.

Tabela 3-1 pokazuje, że intencją microsoft devops dla konteneryzowanych aplikacji platformy Docker jest zapewnienie otwartego przepływu pracy DevOps, dzięki czemu można wybrać produkty do użycia dla każdej fazy (Firmy Microsoft lub innej firmy) przy jednoczesnym zapewnieniu uproszczonego przepływu pracy który zapewnia "produkty domyślnie" już połączone; w związku z tym można szybko rozpocząć pracę z devops na poziomie przedsiębiorstwa dla aplikacji platformy Docker.

**Tabela 3-1.** Obiegi pracy DevOps, otwarte dla każdej technologii

| Host | Technologie firmy Microsoft | Strona trzecia — podłączane do platformy Azure |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Platforma dla aplikacji platformy Docker   | • Microsoft Visual Studio i Visual Studio Code<br /> • .NET<br /> • Usługa Kubernetes platformy Microsoft Azure (AKS)<br /> • Sieć szkieletowa usług Platformy Azure<br /> • Rejestr kontenerów platformy Azure<br /> | • Dowolny edytor kodu (na przykład Sublime)<br /> • Dowolny język (Node.js, Java, Go, itp.)<br /> • Każdy koordynator i harmonogram<br /> • Dowolny rejestr platformy Docker<br /> |
| DevOps dla aplikacji platformy Docker     | • Usługi Azure DevOps<br /> • Serwer Microsoft Team Foundation<br /> • Usługa Azure Kubernetes (AKS)<br /> • Sieć szkieletowa usług Platformy Azure<br /> | • GitHub, Git, Subversion, itp.<br /> • Jenkins, Szef Kuchni, Marionetka, Prędkość, CircleCI, TravisCI, itp.<br /> • Lokalne centrum danych docker, docker swarm, Mesos DC/OS, Kubernetes itp.<br /> |
| Zarządzanie i monitorowanie  | • Monitor Platformy Azure | • Maraton, Chronos, itp.<br />|

Platforma firmy Microsoft i narzędzia dla konteneryzowanych aplikacji platformy Docker, zgodnie z definicją w tabeli 3-1, składają się z następujących składników:

- **Platforma do tworzenia aplikacji platformy Docker** Tworzenie usługi lub kolekcja usług, które tworzą "aplikację". Platforma deweloperska zapewnia wszystkie prace deweloperzy wymaga przed wypchnięciem kodu do repozytorium kodu udostępnionego. Tworzenie usług, wdrożonych jako kontenery, są podobne do tworzenia tych samych aplikacji lub usług bez platformy Docker. Nadal używasz preferowanego języka (.NET, Node.js, Go itp.) i preferowanego edytora lub IDE, takiego jak Visual Studio lub Visual Studio Code. Jednak zamiast rozważyć docker miejsce docelowe wdrożenia, można opracować swoje usługi w środowisku platformy Docker. Tworzenie, uruchamianie, testowanie i debugowanie kodu w kontenerach lokalnie, zapewniając środowisko docelowe w czasie rozwoju. Udostępniając środowisko docelowe lokalnie, kontenery platformy Docker skonfigurować, co drastycznie pomoże Ci poprawić cykl życia DevOps. Visual Studio i Visual Studio Code mają rozszerzenia do integracji kontenerów platformy Docker w procesie tworzenia.

- **DevOps dla aplikacji platformy Docker** Deweloperzy tworzący aplikacje Platformy Docker mogą korzystać z [usług Azure DevOps Services](https://azure.microsoft.com/services/devops/) lub innych produktów innych firm, takich jak Jenkins, w celu utworzenia kompleksowego zautomatyzowanego zarządzania cyklem życia aplikacji (ALM).

  Dzięki usłudze Azure DevOps Services deweloperzy mogą tworzyć devops skoncentrowane na kontenerach dla szybkiego, iteracyjnego procesu, który obejmuje kontrolę kodu źródłowego z dowolnego miejsca (Azure DevOps Services-Git, GitHub, dowolne zdalne repozytorium Git lub Subversion), ciągłą integrację (CI), wewnętrzne testy jednostkowe, testy integracji między kontenerami/usługami, ciągłe dostarczanie (CD) i zarządzanie wersjami (RM). Deweloperzy mogą również zautomatyzować swoje wersje aplikacji Platformy Docker w usłudze Azure Kubernetes Service (AKS), od środowiska deweloperów do środowisk przejściowych i produkcyjnych.

- **Zarządzanie i monitorowanie** It może zarządzać i monitorować aplikacje i usługi produkcyjne na kilka sposobów, integrując obie perspektywy w skonsolidowanym środowisku.

  - **Portal Azure** Jeśli używasz koordynatorów typu open source, usługa Azure Kubernetes Service (AKS), sieć szkieletowa usług i inne moduły koordynatorów pomagają skonfigurować i obsługiwać środowiska platformy Docker. Jeśli używasz sieci szkieletowej usług Azure, narzędzie Eksplorator akcesorii sieci szkieletowej usług umożliwia wizualizację i skonfigurowanie klastra.

  - **Narzędzia do platformy** Docker Zarządzanie aplikacjami kontenerów za pomocą znanych narzędzi. Nie ma potrzeby, aby zmienić istniejące rozwiązania do zarządzania platformą Docker, aby przenieść obciążeń kontenerów do chmury. Użyj narzędzi do zarządzania aplikacjami, które już znasz i połączyć się za pomocą standardowych punktów końcowych interfejsu API dla wybranego koordynatora. Do zarządzania aplikacjami platformy Docker, takimi jak docker Datacenter, a nawet narzędzia dodocker, można również używać innych narzędzi innych firm.

    Nawet jeśli znasz polecenia systemu Linux, możesz zarządzać aplikacjami kontenerów przy użyciu systemów Microsoft Windows i PowerShell za pomocą wiersza polecenia Podsystemu Linux i klientów produktów (Docker, Kubernetes...) działających na tej możliwości podsystemu Linux. Dowiesz się więcej na temat korzystania z tych narzędzi w podsystemie Linux przy użyciu ulubionego systemu operacyjnego Microsoft Windows w dalszej części tej książki.

  - **Narzędzia typu open source** Ponieważ usługi AKS udostępniają standardowe punkty końcowe interfejsu API dla aparatu aranżacji, najpopularniejsze narzędzia są zgodne z systemem AKS i w większości przypadków będą działać po wyjęciu z pudełka — w tym wizualizatorów, monitorowania, narzędzi wiersza polecenia, a nawet przyszłych narzędzi w miarę ich udostępniania.

  - **Monitor platformy Azure** Jest rozwiązaniem platformy Azure do monitorowania każdego kąta środowiska produkcyjnego. Można monitorować aplikacje platformy Docker produkcji, po prostu konfigurując jego zestaw SDK do usług, dzięki czemu można uzyskać dane dziennika generowane przez system z aplikacji.

W związku z tym firma Microsoft oferuje pełną podstawę dla end-to-end konteneryzowany cykl życia aplikacji platformy Docker. Jest to jednak *zbiór produktów i technologii, które umożliwiają opcjonalne wybieranie i integrowanie z istniejącymi narzędziami i procesami.* Elastyczność w szerokim podejściu wraz z siłą w głębi możliwości umieścić microsoft w silnej pozycji dla konteneryzowanych aplikacji platformy Docker rozwoju.

>[!div class="step-by-step"]
>[Poprzedni](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[następny](../design-develop-containerized-apps/index.md)
