---
title: Aplikacje monolityczne
description: Zapoznaj się z podstawowymi pojęciami konteneryzującymi aplikacje monolityczne.
ms.date: 02/15/2019
ms.openlocfilehash: 8664153ee2e9d1d253164e43ac13105f6dbf476c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771032"
---
# <a name="monolithic-applications"></a>Aplikacje monolityczne

W tym scenariuszu jest tworzenie pojedynczej i monolityczne aplikacji sieci web lub usługi i wdrażanie go jako kontenera. W aplikacji struktura może nie być monolityczna; może składać się z kilku bibliotek, komponentów, a nawet warstw (warstwa aplikacji, warstwa domeny, warstwa dostępu do danych itp.). Zewnętrznie jest to pojedynczy kontener, taki jak pojedynczy proces, pojedyncza aplikacja sieci web lub pojedyncza usługa.

Aby zarządzać tym modelem, należy wdrożyć pojedynczy kontener do reprezentowania aplikacji. Aby go skalować, wystarczy dodać kilka kopii z modułem równoważenia obciążenia z przodu. Prostota pochodzi z zarządzania jednym wdrożeniem w jednym kontenerze lub maszynie wirtualnej (VM).

Po głównym, że kontener robi tylko jedną rzecz i robi to w jednym procesie, monolityczny wzorzec jest w konflikcie. W każdym kontenerze można dołączyć wiele składników/bibliotek lub warstw wewnętrznych, jak pokazano na rysunku 4-1.

![Diagram przedstawiający monolityczną aplikację, która skaluje się przez klonowanie aplikacji.](./media/monolithic-applications/monolithic-application-architecture-example.png)

**Rysunek 4-1.** Przykład monolitycznearchitektury aplikacji

Monolityczne aplikacja ma wszystkie lub większość swoich funkcji w ramach jednego procesu lub kontenera i jest składowane w wewnętrznych warstw lub bibliotek. Minusem tego podejścia jest, jeśli lub gdy aplikacja rośnie, wymagając go do skalowania. Jeśli cała aplikacja skalowane, to naprawdę nie jest problemem. Jednak w większości przypadków kilka części aplikacji są punkty ssania, które wymagają skalowania, podczas gdy inne składniki są używane mniej.

Korzystając z typowego przykładu handlu elektronicznego, prawdopodobnie potrzebujesz skalowania składnika informacji o produkcie. Znacznie więcej klientów przegląda produkty niż je kupuje. Więcej klientów korzysta z koszyka niż z potoku płatności. Mniej klientów dodaje komentarze lub przegląda historię zakupów. I prawdopodobnie masz tylko garstkę pracowników, w jednym regionie, którzy muszą zarządzać treścią i kampaniami marketingowymi. Skalowanie monolitycznego projektu, cały kod jest wdrażany wiele razy.

Oprócz problemu "skala-wszystko" zmiany w jednym składniku wymagają pełnego ponownego testowania całej aplikacji, a także pełnego ponownego wdrożenia wszystkich wystąpień.

Monolityczne podejście jest powszechne, a wiele organizacji rozwija się za pomocą tej metody architektonicznej. Wielu z nich cieszy się wystarczająco dobrymi wynikami, podczas gdy inni napotykają ograniczenia. Wiele z nich zaprojektowało swoje aplikacje w tym modelu, ponieważ narzędzia i infrastruktura były zbyt trudne do zbudowania soa, a oni nie widzą potrzeby , dopóki aplikacja wzrosła.

Z punktu widzenia infrastruktury każdy serwer może uruchamiać wiele aplikacji w obrębie tego samego hosta i mieć akceptowalny stosunek wydajności w użyciu zasobów, jak pokazano na rysunku 4-2.

![Diagram przedstawiający jeden host z wieloma aplikacjami w oddzielnych kontenerach.](./media/monolithic-applications/host-with-multiple-apps-containers.png)

**Rysunek 4-2.** Host z wieloma aplikacjami/kontenerami

Wreszcie, z punktu widzenia dostępności, monolityczne aplikacje muszą być wdrażane jako całość; oznacza to, że w przypadku, gdy należy *zatrzymać i uruchomić*, wszystkie funkcje i wszyscy użytkownicy zostaną naruszone w oknie wdrażania. W niektórych sytuacjach korzystanie z platformy Azure i kontenerów można zminimalizować te sytuacje i zmniejszyć prawdopodobieństwo przestoju aplikacji, jak widać na rysunku 4-3.

Można wdrożyć aplikacje monolityczne na platformie Azure przy użyciu dedykowanych maszyn wirtualnych dla każdego wystąpienia. Za pomocą [zestawów skalowania maszyn wirtualnych platformy Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), można łatwo skalować maszyn wirtualnych.

Można również użyć [usługi Azure App Services](https://azure.microsoft.com/services/app-service/) do uruchamiania aplikacji monolitycznych i łatweskalowanie wystąpień bez konieczności zarządzania maszynami wirtualnymi. Usługi Azure App Services można uruchomić pojedyncze wystąpienia kontenerów platformy Docker, jak również upraszczając wdrożenie.

Można wdrożyć wiele maszyn wirtualnych jako hosty platformy Docker i uruchomić dowolną liczbę kontenerów na maszynę wirtualną. Następnie za pomocą programu Azure Load Balancer, jak pokazano na rysunku 4-3, można zarządzać skalowanie.

![Diagram przedstawiający monolityczną aplikację skalowaną w sposób skalowany do różnych hostów.](./media/monolithic-applications/multiple-hosts-from-single-docker-container.png)

**Rysunek 4-3**. Wiele hostów skalowania w sposób wycofujący pojedynczą aplikację docker

Można zarządzać wdrażaniem hostów samodzielnie za pomocą tradycyjnych technik wdrażania.

Kontenery platformy Docker można zarządzać z `docker run` wiersza polecenia przy użyciu poleceń, takich jak i `docker-compose up`, a także można zautomatyzować go w potokach ciągłego dostarczania (CD) i wdrożyć na hostach platformy Docker z usługi Azure DevOps Services, na przykład.

## <a name="monolithic-application-deployed-as-a-container"></a>Monolityczna aplikacja wdrożona jako kontener

Korzystanie z kontenerów do zarządzania wdrożeniami monolitycznymi ma się korzystnie. Skalowanie wystąpień kontenerów jest znacznie szybsze i łatwiejsze niż wdrażanie dodatkowych maszyn wirtualnych.

Wdrażanie aktualizacji jako obrazów platformy Docker jest znacznie szybsze i wydajne w sieci. Kontenery platformy Docker zazwyczaj rozpoczynają się w ciągu kilku sekund, przyspieszając wdrożenia. Niszczanie kontenera platformy Docker `docker stop` jest tak proste, jak wywoływanie polecenia, zazwyczaj ukończenie w mniej niż sekundę.

Ponieważ kontenery są z natury niezmienne, zgodnie z projektem nigdy nie musisz się martwić o uszkodzone maszyny wirtualne, ponieważ skrypt aktualizacji zapomniał uwzględnić określoną konfigurację lub plik pozostawiony na dysku.

Chociaż monolityczne aplikacje mogą korzystać z platformy Docker, dotykamy tylko wskazówek dotyczących korzyści. Większe korzyści z zarządzania kontenerami pochodzą z wdrażania z koordynatorami kontenerów, które zarządzają różnymi wystąpieniami i cyklem życia każdego wystąpienia kontenera. Podział monolityczne aplikacji na podsystemy, które mogą być skalowane, opracowywane i wdrażane indywidualnie jest punktem wejścia do sfery mikrousług.

Aby dowiedzieć się, jak "podnosić i zmieniać" monolityczne aplikacje za pomocą kontenerów i jak można modernizować aplikacje, możesz przeczytać ten dodatkowy <https://aka.ms/LiftAndShiftWithContainersEbook>przewodnik firmy Microsoft, [Modernizuj istniejące aplikacje .NET za pomocą chmury Platformy Azure i kontenerów systemu Windows](../../modernize-with-azure-containers/index.md), które można również pobrać w formacie PDF z .

## <a name="publish-a-single-docker-container-app-to-azure-app-service"></a>Publikowanie pojedynczej aplikacji kontenera platformy Docker w usłudze Azure App Service

Ponieważ chcesz uzyskać szybkie sprawdzanie poprawności kontenera wdrożonego na platformie Azure lub ponieważ aplikacja jest po prostu aplikacją z jednym kontenerem, usługa Azure App Services zapewnia świetny sposób na zapewnienie skalowalnych usług pojedynczego kontenera.

Korzystanie z usługi Azure App Service jest intuicyjne i można szybko uruchomić, ponieważ zapewnia doskonałą integrację Git do podjęcia kodu, skompilować go w programie Microsoft Visual Studio i bezpośrednio wdrożyć go na platformie Azure. Ale tradycyjnie (bez platformy Docker), jeśli potrzebne są inne funkcje, struktury lub zależności, które nie są obsługiwane w usługach aplikacji, trzeba było poczekać na to, aż zespół platformy Azure zaktualizuje te zależności w usłudze App Service lub przełączyć się na inne usługi, takie jak Sieć szkieletowa usług, usługi w chmurze, a nawet zwykłe maszyny wirtualne, dla których masz dodatkową kontrolę i można zainstalować wymagany składnik lub strukturę dla aplikacji.

Teraz, jak pokazano na rysunku 4-4, podczas korzystania z programu Visual Studio 2017, obsługa kontenerów w usłudze Azure App Service daje możliwość uwzględnienia, co chcesz w środowisku aplikacji. Jeśli dodano zależność do aplikacji, ponieważ używasz go w kontenerze, można uzyskać możliwość dodania tych zależności w obrazie dockerfile lub docker.

![Zrzut ekranu przedstawiający okno dialogowe Tworzenie usługi aplikacji z rejestrem kontenerów.](./media/monolithic-applications/publish-azure-app-service-container.png)

**Rysunek 4-4**. Publikowanie kontenera w usłudze Azure App Service z aplikacji/kontenerów programu Visual Studio

Rysunek 4-4 pokazuje również, że przepływ publikowania wypycha obraz za pośrednictwem rejestru kontenerów, który może być rejestrem kontenerów platformy Azure (rejestrem w pobliżu wdrożeń na platformie Azure i zabezpieczonym przez grupy i konta usługi Azure Active Directory) lub innym rejestrem platformy Docker takich jak docker hub lub rejestrów lokalnych.

>[!div class="step-by-step"]
>[Poprzedni](common-container-design-principles.md)
>[następny](state-and-data-in-docker-applications.md)
