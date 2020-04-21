---
title: Wprowadzenie do platformy i narzędzi firmy Microsoft dla aplikacji konteneryzowanych
description: Poznaj oferty firmy Microsoft dotyczące obsługi cyklu życia aplikacji platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 8cb7870035003e956ee57684a2a2528732849379
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738449"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Wprowadzenie do platformy i narzędzi firmy Microsoft dla aplikacji konteneryzowanych

*Wizja: Utwórz elastyczny, konteneryzowany cykl życia aplikacji klasy korporacyjnej, który obejmuje rozwój, operacje IT i zarządzanie produkcją.*

Rysunek 3-1 przedstawia główne filary cyklu życia aplikacji platformy Docker sklasyfikowanych według rodzaju pracy dostarczanej przez wiele zespołów (tworzenie aplikacji, procesy infrastruktury DevOps oraz zarządzanie i operacje IT). Zazwyczaj w przedsiębiorstwie profile "persona" odpowiedzialne za każdy obszar są różne. Podobnie jak ich umiejętności.

:::image type="complex" source="./media/index/microsoft-tools-contanerized-docker-app.png" alt-text="Diagram przedstawiający narzędzia firmy Microsoft potrzebne do obsługi aplikacji platformy Docker.":::
narzędzia firmy Microsoft. Dla zadania opracowywania/projektowania: Aparat platformy Docker dla systemu Windows, VS i VS Code, .NET Core, usługa Azure Kubernetes. Dla obciążenia kompilacji/testowania/wysyłki: Azure DevOps, Team Foundation Server, Docker CLI, Usługa Azure Kubernetes. Dla uruchamiania/monitorowania/zarządzania obciążeniem: Azure Monitor, Usługi Azure Portal Azure Kubernetes, sieci szkieletowej usług, innych koordynatorów.
:::image-end:::

**Rysunek 3-1.** Główne filary cyklu życia konteneryzowanych aplikacji platformy Docker za pomocą platformy i narzędzi firmy Microsoft

Konteneryzowany przepływ pracy dockera może być początkowo nakazowy na podstawie "domyślnych wyborów produktów", co ułatwia deweloperom szybsze rozpoczęcie pracy, ale podstawowe jest to, że pod maską musi istnieć otwarta struktura, dzięki czemu będzie elastycznym przepływem pracy umożliwiającym dostosowanie się do różnych kontekstów z każdej organizacji lub przedsiębiorstwa. Infrastruktura przepływu pracy (składniki i produkty) musi być wystarczająco elastyczna, aby objąć środowisko, które każda firma będzie miała w przyszłości, nawet będąc w stanie zamienić produkty deweloperów lub DevOps na inne. Ta elastyczność, otwartość i szeroki wybór technologii w platformie i infrastrukturze są właśnie priorytetami firmy Microsoft dla konteneryzowanych aplikacji platformy Docker, jak wyjaśniono w kolejnych rozdziałach.

Tabela 3-1 pokazuje, że intencją microsoft DevOps dla konteneryzowanych aplikacji platformy Docker jest zapewnienie otwartego przepływu pracy DevOps, dzięki czemu można wybrać, jakie produkty do użycia dla każdej fazy (Microsoft lub innej firmy), zapewniając jednocześnie uproszczony przepływ pracy, który zapewnia "produkty domyślne" już połączone; w związku z tym można szybko rozpocząć pracę z przepływem pracy DevOps na poziomie przedsiębiorstwa dla aplikacji Platformy Docker.

**Tabela 3-1.** Przepływy pracy DevOps, otwarte dla dowolnej technologii

| Host | Technologie firmy Microsoft | Wtyczka platformy Azure innej firmy |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Platforma dla aplikacji platformy Docker   | • Kod programu Microsoft Visual Studio i visual studio<br /> • .NET<br /> • Usługa Microsoft Azure Kubernetes (AKS)<br /> • Sieci szkieletowej usług azure<br /> • Rejestr kontenerów platformy Azure<br /> | • Dowolny edytor kodu (na przykład Sublime)<br /> • Dowolny język (Node.js, Java, Go, itp.)<br /> • Dowolny koordynator i harmonogram<br /> • Dowolny rejestr platformy Docker<br /> |
| DevOps dla aplikacji platformy Docker     | • Usługi Azure DevOps<br /> • Serwer Microsoft Team Foundation<br /> • Usługa Azure Kubernetes (AKS)<br /> • Sieci szkieletowej usług azure<br /> | • GitHub, Git, Subversion, itp.<br /> • Jenkins, Chef, Puppet, Velocity, CircleCI, TravisCI, itp.<br /> • Lokalne centrum danych platformy Docker, Docker Swarm, Mesos DC/OS, Kubernetes itp.<br /> |
| Zarządzanie i monitorowanie  | • Monitor platformy Azure | • Maraton, Chronos, itp.<br />|

Platforma firmy Microsoft i narzędzia dla konteneryzowanych aplikacji platformy Docker, zgodnie z definicją w tabeli 3-1, składają się z następujących składników:

- **Platforma do tworzenia aplikacji platformy Docker** Rozwój usługi lub kolekcji usług, które tworzą "aplikację". Platforma deweloperska udostępnia wszystkie deweloperzy pracy wymaga przed wypchnięcie ich kod do repozytorium udostępnionego kodu. Tworzenie usług, wdrożonych jako kontenery, są podobne do tworzenia tych samych aplikacji lub usług bez platformy Docker. Nadal używasz preferowanego języka (.NET, Node.js, Go itp.) i preferowanego edytora lub IDE, takiego jak Visual Studio lub Visual Studio Code. Jednak zamiast rozważyć docker miejsce docelowe wdrożenia, należy rozwijać swoje usługi w środowisku platformy Docker. Tworzenie, uruchamianie, testowanie i debugowanie kodu w kontenerach lokalnie, zapewniając środowisko docelowe w czasie programowania. Udostępniając środowisko docelowe lokalnie, kontenery platformy Docker skonfigurować, co znacznie pomoże Ci poprawić cykl życia DevOps. Visual Studio i Visual Studio Code mają rozszerzenia do integracji kontenerów platformy Docker w procesie tworzenia.

- **Aplikacje dokowane dla aplikacji docker** Deweloperzy tworzący aplikacje platformy Docker mogą używać [usług Azure DevOps](https://azure.microsoft.com/services/devops/) services lub dowolnego innego produktu innej firmy, takiego jak Jenkins, do tworzenia kompleksowego zautomatyzowanego zarządzania cyklem życia aplikacji (ALM).

  Dzięki usłudze Azure DevOps Services deweloperzy mogą tworzyć devops skoncentrowane na kontenerach dla szybkiego, iteracyjny proces, który obejmuje kontrolę kodu źródłowego z dowolnego miejsca (Usługi Azure DevOps-Git, GitHub, dowolne zdalne repozytorium Git lub Subversion), ciągłą integrację (CI), wewnętrzne testy jednostek, testy integracji między kontenerami/usługami, ciągłe dostarczanie (CD) i zarządzanie wydaniami (RM). Deweloperzy mogą również zautomatyzować ich wersji aplikacji platformy Docker do usługi Azure Kubernetes Service (AKS), od programowania do środowisk przejściowych i produkcyjnych.

- **Zarządzanie i monitorowanie** It może zarządzać i monitorować aplikacje i usługi produkcyjne na kilka sposobów, integrując obie perspektywy w skonsolidowanym doświadczeniu.

  - **Portal Azure** Jeśli używasz koordynatorów open source, usługa Azure Kubernetes Service (AKS), sieć szkieletowa usług i inne koordynatory ułatwiają konfigurowanie i obsługę środowisk platformy Docker. Jeśli używasz usługi Azure Service Fabric, narzędzie Eksploratora sieci szkieletowej usług umożliwia wizualizację i skonfigurowanie klastra.

  - **Narzędzia docker** Można zarządzać aplikacjami kontenerów za pomocą znanych narzędzi. Nie ma potrzeby zmieniania istniejących praktyk zarządzania platformy Docker, aby przenieść obciążenia kontenerów do chmury. Użyj narzędzi do zarządzania aplikacjami, które są już znane i połączyć za pośrednictwem standardowych punktów końcowych interfejsu API dla koordynatora do wyboru. Do zarządzania aplikacjami platformy Docker, takich jak centrum danych platformy Docker, a nawet narzędzia docker, można również używać innych narzędzi innych firm.

    Nawet jeśli znasz polecenia systemu Linux, możesz zarządzać aplikacjami kontenerów przy użyciu systemów Microsoft Windows i PowerShell za pomocą wiersza polecenia Podsystemu Linux i klientów produktów (Docker, Kubernetes...) działających na tej funkcji podsystemu Linux. Dowiesz się więcej na temat korzystania z tych narzędzi w podsystemie Linux przy użyciu ulubionego systemu operacyjnego Microsoft Windows w dalszej części tej książki.

  - **Narzędzia open-source** Ponieważ usługa AKS udostępnia standardowe punkty końcowe interfejsu API dla aparatu aranżacji, najpopularniejsze narzędzia są zgodne z systemem AKS i w większości przypadków będą działać po wyjęciu z pudełka — w tym wizualizatory, monitorowanie, narzędzia wiersza polecenia, a nawet przyszłe narzędzia, gdy tylko staną się dostępne.

  - **Monitor platformy Azure** To rozwiązanie platformy Azure do monitorowania każdego kąta środowiska produkcyjnego. Można monitorować aplikacje platformy Docker produkcji, po prostu konfigurując jego zestaw SDK w usługach, dzięki czemu można uzyskać dane dziennika generowane przez system z aplikacji.

W związku z tym firma Microsoft oferuje pełną podstawę dla kompleksowego cyklu życia aplikacji konteneryzowanej platformy Docker. Jest to jednak *zbiór produktów i technologii, które pozwalają opcjonalnie wybrać i zintegrować z istniejącymi narzędziami i procesami.* Elastyczność w szerokim podejściu wraz z siłą w głębi możliwości miejsce Microsoft w silnej pozycji dla konteneryzowanych tworzenia aplikacji platformy Docker.

>[!div class="step-by-step"]
>[Poprzedni](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[następny](../design-develop-containerized-apps/index.md)
