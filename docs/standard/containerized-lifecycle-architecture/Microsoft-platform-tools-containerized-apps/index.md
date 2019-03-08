---
title: Wprowadzenie do platformy firmy Microsoft oraz narzędzi dla aplikacji konteneryzowanych
description: 'Ustal, jakimi oferty firmy Microsoft do obsługi cykl życia aplikacji platformy Docker.'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Wprowadzenie do platformy firmy Microsoft oraz narzędzi dla aplikacji konteneryzowanych

*Wizja: Utwórz potężnej, przeznaczonych dla przedsiębiorstw, kontenerowych nimi cyklu życia aplikacji, która obejmuje projektowania, operacji IT i zarządzania środowiska produkcji.*

Rysunek 3-1 przedstawiono głównych filarach w cyklu życia aplikacji platformy Docker według rodzaju pracy dostarczane przez wiele zespołów (Tworzenie aplikacji, procesy infrastruktury DevOps i zarządzanie infrastrukturą IT i operacje). Zazwyczaj w przedsiębiorstwie, profile "osoby" odpowiada za dla każdego obszaru są różne. Dlatego są umiejętności.

![Narzędzia firmy Microsoft. W przypadku obciążeń programowanie/projektu: Aparat platformy docker for Windows, VS i VS Code, .NET Core usługi Azure Kubernetes Service. W przypadku obciążeń statku-kompilacji/Test: Usługa Azure DevOps, Team Foundation Server, Docker CLI, Azure Kubernetes Service. Uruchom/Monitor/Zarządzanie obciążenia: Application Insights, Azure Portal usługi Azure Kubernetes usługi Service Fabric, innych orkiestratorów.](./media/image1.png)

**Rysunek 3-1.** Głównych filarach w cykl życia konteneryzowanych aplikacji platformy Docker przy użyciu platformy firmy Microsoft i narzędzi

Konteneryzowane przepływu pracy cyklu życia Docker może być początkowo przetestowanego rozwiązania ze szczegółami na podstawie "domyślnie produktu możliwości wyboru," ułatwia deweloperom szybciej, Rozpocznij pracę, ale jest podstawą, że kulisy musi być otwartej struktury tak, aby go elastyczne przepływ pracy, możliwość dostosowania do różnych kontekstach z każdej organizacji lub przedsiębiorstwie. Infrastruktura przepływu pracy (składnikami i produktami) musi być wystarczająco elastyczny, aby obejmować środowisko, w którym każda firma będzie miała w przyszłości, nawet zdolność zamianę rozwoju lub produktów DevOps do innych osób. Ta elastyczność, otwartości i szeroki wybór technologii platforma i infrastruktura są dokładnie priorytetów firmy Microsoft dla konteneryzowanych aplikacji platformy Docker, jak wyjaśniono w rozdziałach, które należy wykonać.

Tabela 3-1 pokazuje, czy zamiar metodyki DevOps firmy Microsoft dla konteneryzowanych aplikacji platformy Docker ma na celu dostarczenie Otwórz przepływ pracy DevOps tak, aby można było wybrać jakie produkty do użycia dla każdej fazy (Microsoft lub innych firm) przy jednoczesnym zapewnieniu uproszczonego przepływu pracy zapewniający, że podłączony "przez — domyślna produkty"; w związku z tym możesz szybko rozpocząć pracę z przepływem pracy DevOps klasy korporacyjnej dla aplikacji platformy Docker.

**Tabela 3-1.** Otwórz przepływów pracy metodyki DevOps, dowolna Technologia

| Host | Technologie firmy Microsoft | Innych firm — podłączanych platformy Azure |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Platforma dla aplikacji platformy Docker   | • Microsoft Visual Studio i Visual Studio Code<br /> • .NET<br /> • Platformy Microsoft Azure Container Service<br /> • Usługi azure Service Fabric<br /> • Usługi azure Container Registry<br /> | • Dowolnego edytora kodu (na przykład Sublime)<br /> • Dowolnego języka (Node.js, Java, Go, itp.)<br /> • Dowolnego programu orchestrator i harmonogramu<br /> • Dowolnego rejestru platformy Docker<br /> |
| Metodyka DevOps na potrzeby aplikacji platformy Docker     | Usługi azure DevOps •<br /> • Microsoft Team Foundation Server<br /> • Usługi azure Container Service<br /> • Usługi azure Service Fabric<br /> | • GitHub, Git, Subversion, etc.<br /> • Jenkins, Chef, Puppet, Velocity, CircleCI, TravisCI, etc.<br /> • W środowisku lokalnym Mesos Docker Datacenter, Docker Swarm, DC/OS, Kubernetes, itp.<br /> |
| Zarządzanie i monitorowanie  | • Operations Management Suite<br /> • Applications Insights<br /> | • Platformy Marathon, Chronos itp.<br />

Platformy firmy Microsoft oraz narzędzi dla konteneryzowanych aplikacji platformy Docker, zgodnie z definicją w tabeli 3-1, obejmują następujące składniki:

- **Platformy opracowywania aplikacji platformy Docker** rozwoju usługi lub kolekcja usług, które tworzą "aplikacja". Platforma programistyczna zawiera wszystkich programistów pracy wymaga przed wypchnięciem swój kod do repozytorium udostępnionego kodu. Tworzenie usług, wdrażane jako kontenery, są podobne do tworzenia tej samej aplikacji lub usług bez platformy Docker. Możesz nadal korzystać z Twojego preferowanego języka (.NET, Node.js, Go, itp.) i preferowanego edytora lub IDE, takie jak Visual Studio lub Visual Studio Code. Jednak zamiast wziąć pod uwagę Docker lokalizację docelową wdrożenia, możesz tworzyć usługi w środowisku platformy Docker. Tworzenie, uruchamianie, Testuj i Debuguj kodu w kontenerach lokalnie, zapewniając środowisko docelowe w czasie tworzenia. Dostarczając lokalnie środowisko docelowe, kontenerów platformy Docker zdefiniować co drastycznie pomoże poprawić swoje cyklu życia operacji deweloperskich. Program Visual Studio i Visual Studio Code ma rozszerzeń do integracji kontenerów platformy Docker w procesie tworzenia aplikacji.

- **Metodyka DevOps na potrzeby aplikacji platformy Docker** umożliwia programistom tworzenie aplikacji platformy Docker [usługom DevOps platformy Azure](https://azure.microsoft.com/services/devops/) lub dowolny inny produkt innej firmy, takich jak Jenkins do rozbudowy cyklu życia kompleksowej aplikacji automatycznych Management (ALM).

  Dzięki usługom DevOps platformy Azure, deweloperzy mogą tworzyć ukierunkowane kontenera metodyka DevOps na potrzeby szybkie, iteracyjne procesu, który obejmuje kod źródłowy sterowania z dowolnego miejsca (Git usług platformy Azure DevOps, GitHub, dowolnym zdalnym repozytorium Git lub Subversion), ciągłej integracji (CI) , testy jednostkowe wewnętrznego, testy integracji inter container/usługi, ciągłe dostarczanie (CD) i rozwiązania release management (RM). Deweloperzy mogą też zautomatyzować ich Docker aplikacji wersji do usługi Azure Container Service, od projektowania do środowiskach przejściowych i produkcyjnych.

- **Zarządzanie i monitorowanie** IT mogą zarządzać i monitorować aplikacje produkcyjne i usług na kilka sposobów, integrowania zarówno perspektywy w skonsolidowane środowisko.

  - **Witryna Azure portal** Jeśli używasz orkiestratorów typu open source usługi Azure Kubernetes Service (AKS), Usługa Service Fabric i innych orkiestratorów ułatwiają konfiguracji i utrzymania środowiska Docker. Jeśli używasz usługi Azure Service Fabric narzędzie Service Fabric Explorer umożliwia wizualizowanie i skonfiguruj klaster.

  - **Narzędzia aparatu docker** zarządzalnych aplikacji kontenerów przy użyciu znanych narzędzi. Istnieje nie trzeba zmieniać istniejących praktyk dotyczących zarządzania platformy Docker, aby przenieść obciążenia kontenerów do chmury. Użyj narzędzi zarządzania aplikacji, które już znasz i Połącz za pośrednictwem standardowych punktów końcowych interfejsu API dla wybranego koordynatora. Możesz również użyć innych narzędzi innych firm można zarządzać aplikacjami platformy Docker, takich jak Docker Datacenter lub nawet narzędzi interfejsu wiersza polecenia platformy Docker. 

    Nawet jeśli znasz polecenia systemu Linux, możesz zarządzać aplikacji kontenerów przy użyciu programu PowerShell i Microsoft Windows przy użyciu wiersza polecenia podsystemu systemu Linux oraz produktów (Docker, Kubernetes...) klientów w tej funkcji w podsystemie systemu Linux. Dowiesz się więcej o korzystaniu z tych narzędzi w podsystemie systemu Linux przy użyciu ulubionym systemie operacyjnym Microsoft Windows dalej w tej sekcji.

  - **Narzędzia typu open-source** AKS ponieważ ujawnia standardowe punkty końcowe interfejsu API dla aparatu aranżacji, że najbardziej popularne narzędzia są zgodne z usługi AKS i w większości przypadków, będą fabrycznie działać — wizualizatorów, monitorowania, w tym narzędzia wiersza polecenia i nawet przyszłych narzędzi w miarę ich udostępniania.

  - **Usługa Application Insights** soution jest Azure do monitorowania sprzedażą evironment sieci produkcyjnych. Aby monitorować aplikacji platformy Docker w środowisku produkcyjnym, należy po prostu konfigurowania tego zestawu SDK do usługi, dzięki czemu można uzyskać dane dzienników generowanych przez system z aplikacji.

W związku z tym firma Microsoft oferuje pełny podstawę dla end-to-end konteneryzowanych Docker cyklu życia aplikacji. Jest jednak *zbiór produkty i technologie umożliwiające opcjonalnie wybierz i zintegrować z istniejącym narzędzi i procesów*. Elastyczność w szerokim podejście wraz z siły szczegółowo możliwości firmy Microsoft należy umieścić w silną pozycję opracowywania konteneryzowanych aplikacji platformy Docker.

>[!div class="step-by-step"]
>[Poprzednie](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[dalej](../design-develop-containerized-apps/index.md)
