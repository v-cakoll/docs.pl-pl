---
title: Wprowadzenie do platformy i narzędzi firmy Microsoft dla aplikacji konteneryzowanych
description: Uzyskaj informacje o ofertach firmy Microsoft w celu obsługi cyklu życia aplikacji platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 84f4136c6b6c284dd5ecb3fc174ac825857a567e
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158505"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Wprowadzenie do platformy i narzędzi firmy Microsoft dla aplikacji konteneryzowanych

*Wizja: Utwórz dostosowywalny cykl życia aplikacji klasy korporacyjnej, który obejmuje rozwój, operacje IT i zarządzanie produkcyjne.*

Rysunek 3-1 przedstawia główne filary w cyklu życia aplikacji platformy Docker sklasyfikowane według typu pracy dostarczonej przez wiele zespołów (Programowanie aplikacji, procesy infrastruktury DevOps oraz zarządzanie i operacje IT). Zwykle w przedsiębiorstwie profile "osoba" odpowiadające za poszczególne obszary są różne. Są to ich umiejętności.

:::image type="complex" source="./media/index/microsoft-tools-contanerized-docker-app.png" alt-text="Diagram przedstawiający narzędzia firmy Microsoft, które są konieczne do obsługi aplikacji platformy Docker.":::
Narzędzia firmy Microsoft. W przypadku obciążeń opracowywania/projektowania: aparat platformy Docker dla systemu Windows, Visual Studio i Visual Studio Code, .NET Core, Azure Kubernetes Service. W przypadku obciążeń kompilowania/testowania/dostarczania: Azure DevOps, Team Foundation Server, interfejsu wiersza polecenia platformy Docker i usługi Azure Kubernetes. W przypadku uruchamiania/monitorowania/zarządzania obciążeniem: Azure Monitor, Azure Portal, Azure Kubernetes Services, Service Fabric i innych koordynatorów.
:::image-end:::

**Rysunek 3-1.** Główne filary w cyklu życia dla kontenerów platformy Docker z platformą i narzędziami firmy Microsoft

Przepływ pracy platformy Docker w ramach cyklu życia może być wstępnie zadawany w oparciu o "według domyślnych produktów", co ułatwia deweloperom szybkie rozpoczynanie pracy, ale jest to istotne w przypadku, gdy jest to konieczne, aby można było korzystać z różnych kontekstów z każdej organizacji lub przedsiębiorstwa. Infrastruktura przepływu pracy (składniki i produkty) musi być elastyczna, aby pokryć środowisko, w którym każda firma będzie w przyszłości, nawet z możliwością zamiany produktów programistycznych lub DevOps na inne. Ta elastyczność, otwartość i szeroki wybór technologii na platformie i infrastrukturze to dokładne priorytety firmy Microsoft dla kontenerów aplikacji platformy Docker, jak wyjaśniono w kolejnych rozdziałach.

Tabela 3-1 pokazuje, że zamiarem programu Microsoft DevOps dla kontenerów platformy Docker jest udostępnienie otwartego przepływu pracy DevOps, dzięki czemu można wybrać produkty, które mają być używane dla każdej fazy (firmy Microsoft lub innej firmy), a jednocześnie zapewnić uproszczony przepływ pracy, który zapewnia już połączone produkty "według domyślnych"; Dzięki temu możesz szybko rozpocząć pracę z przepływem pracy DevOps na poziomie przedsiębiorstwa dla aplikacji platformy Docker.

**Tabela 3-1.** Przepływy pracy DevOps, otwarte dla dowolnej technologii

| Host | Technologie firmy Microsoft | Inne firmy — Podłączanie platformy Azure |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Platforma dla aplikacji platformy Docker   | • Microsoft Visual Studio i Visual Studio Code<br /> • .NET<br /> • Microsoft Azure Kubernetes Service (AKS)<br /> • Service Fabric platformy Azure<br /> • Azure Container Registry<br /> | • Dowolny edytor kodu (na przykład subwapno)<br /> • Dowolny język (Node. js, Java, go itp.)<br /> • Wszystkie usługi Orchestrator i Scheduler<br /> • Dowolny rejestr platformy Docker<br /> |
| DevOps dla aplikacji platformy Docker     | • Azure DevOps Services<br /> • Microsoft Team Foundation Server<br /> • Usługa Azure Kubernetes Service (AKS)<br /> • Service Fabric platformy Azure<br /> | • GitHub, Git, Subversion itp.<br /> • Jenkins, Chef, Puppet, prędkość, CircleCI, TravisCI itd.<br /> • Lokalne centrum danych platformy Docker, Docker Swarm, Mesos DC/OS, Kubernetes itd.<br /> |
| Zarządzanie i monitorowanie  | • Azure Monitor | • Marathon, Chronos itp.<br />|

Platforma i narzędzia firmy Microsoft dla kontenerów platformy Docker, zgodnie z definicją w tabeli 3-1, składają się z następujących składników:

- **Platforma do tworzenia aplikacji platformy Docker** Tworzenie usługi lub zbieranie usług, które tworzą "aplikację". Platforma programistyczna zapewnia wszystkim deweloperom pracującym przed wypchnięciem ich kodu do udostępnionego repozytorium kodu. Opracowywanie usług, wdrożonych jako kontenery, są podobne do rozwoju tych samych aplikacji lub usług, które nie są zadokowane. Będziesz nadal korzystać z preferowanego języka (.NET, Node. js, go itp.) i preferowanego edytora lub środowiska IDE, takiego jak Visual Studio lub Visual Studio Code. Jednak zamiast rozważać rozwiązanie Docker jako miejsce docelowe wdrożenia, można opracowywać usługi w środowisku Docker. Kompiluj, uruchamiaj, Testuj i Debuguj swój kod w kontenerach lokalnie, dostarczając środowisko docelowe w czasie projektowania. Dostarczając środowisko docelowe lokalnie, kontenery platformy Docker skonfigurują co radykalnie pomożesz ulepszyć cykl życia DevOps. Program Visual Studio i Visual Studio Code mają rozszerzenia umożliwiające integrację kontenerów platformy Docker w ramach procesu tworzenia oprogramowania.

- **DevOps dla aplikacji platformy Docker** Deweloperzy tworzący aplikacje platformy Docker mogą używać [Azure DevOps Services](https://azure.microsoft.com/services/devops/) lub innych produktów innych firm, takich jak Jenkins, aby tworzyć kompleksowe zautomatyzowane zarządzanie cyklem życia aplikacji (ALM).

  Dzięki Azure DevOps Services deweloperzy mogą tworzyć DevOps ukierunkowane na kontenery dla szybkiego, iteracyjnego procesu, który obejmuje kontrolę kodu źródłowego z dowolnego miejsca (Azure DevOps Services-git, GitHub, dowolne zdalne repozytorium Git lub Podwersja), ciągłą integrację (CI), wewnętrzne testy jednostkowe, testy integracji między kontenerami/usługami, ciągłe dostarczanie (CD) i Zarządzanie wersjami (RM). Deweloperzy mogą również zautomatyzować swoje wydania aplikacji platformy Docker w usłudze Azure Kubernetes Service (AKS), od projektowania do środowiska przejściowego i produkcyjnego.

- **Zarządzanie i monitorowanie** Umożliwia ona zarządzanie i monitorowanie aplikacji i usług produkcyjnych na kilka sposobów, co umożliwia integrację obu perspektyw w skonsolidowanym środowisku.

  - **Azure Portal** w przypadku korzystania z programów Orchestrator-source, Azure Kubernetes Service (AKS), Service Fabric i innych koordynatorów ułatwiają konfigurowanie i konserwowanie środowisk platformy Docker. Jeśli używasz usługi Azure Service Fabric, narzędzie Service Fabric Explorer umożliwia wizualizację i konfigurację klastra.

  - **Narzędzia platformy Docker** umożliwiają zarządzanie aplikacjami kontenera za pomocą znanych narzędzi. Nie trzeba zmieniać istniejących praktyk zarządzania platformy Docker, aby przenosić obciążenia kontenerów do chmury. Skorzystaj z narzędzi do zarządzania aplikacjami, które są już znane, i Połącz się za pośrednictwem standardowych punktów końcowych interfejsu API dla wybranego koordynatora. Możesz również użyć innych narzędzi innych firm do zarządzania aplikacjami platformy Docker, takimi jak centrum danych platformy Docker lub narzędzia Docker interfejsu wiersza polecenia.

    Nawet jeśli znasz polecenia systemu Linux, możesz zarządzać aplikacjami kontenera przy użyciu systemu Microsoft Windows i programu PowerShell z systemem operacyjnym z systemem Linux oraz z systemami (Docker, Kubernetes...) uruchomionymi w tej funkcji podsystemu Linux. Dowiesz się więcej na temat używania tych narzędzi w podsystemie Linux przy użyciu ulubionego systemu operacyjnego Microsoft Windows w dalszej części tego podręcznika.

  - **Narzędzia typu "open source"** , ponieważ AKS uwidacznia standardowe punkty końcowe interfejsu API dla aparatu aranżacji, najpopularniejsze narzędzia są zgodne z AKS i, w większości przypadków, będą wyłączane z tego pola — w tym Wizualizatory, monitorowanie, narzędzia wiersza polecenia, a nawet przyszłe narzędzia, gdy staną się dostępne.

  - **Azure monitor** To rozwiązanie platformy Azure do monitorowania każdego kąta w środowisku produkcyjnym. Aby monitorować produkcyjne aplikacje platformy Docker, wystarczy skonfigurować swój zestaw SDK w swoich usługach, aby można było uzyskać dane dziennika generowane przez system z aplikacji.

W związku z tym firma Microsoft oferuje kompletną podstawę do kompleksowego cyklu życia aplikacji platformy Docker. Jest to jednak *zbiór produktów i technologii, które umożliwiają opcjonalne Wybieranie i integrację z istniejącymi narzędziami i procesami*. Elastyczność w szerokim podejściu wraz z siłą na głębokości funkcji umieszczaj firmę Microsoft w silnym położeniu dla tworzenia kontenerów aplikacji platformy Docker.

>[!div class="step-by-step"]
>[Poprzedni](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[Następny](../design-develop-containerized-apps/index.md)
