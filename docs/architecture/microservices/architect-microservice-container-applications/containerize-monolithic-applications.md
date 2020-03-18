---
title: Umieszczanie aplikacji monolitycznych w kontenerze
description: Konteneryzowanie aplikacji monolitycznych, mimo że nie uotrzymasz wszystkich korzyści z architektury mikrousług, ma ważne korzyści wdrożenia, które mogą być dostarczane od razu.
ms.date: 01/30/2020
ms.openlocfilehash: 0e6f7504a91d2b1a89193471746168fc34f50956
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503288"
---
# <a name="containerizing-monolithic-applications"></a>Umieszczanie aplikacji monolitycznych w kontenerze

Można utworzyć jedną, monolitycznie wdrożonej aplikacji sieci web lub usługi sieci web i wdrożyć go jako kontenera. Sama aplikacja może nie być wewnętrznie monolityczna, ale skonstruowana jako kilka bibliotek, komponentów, a nawet warstw (warstwa aplikacji, warstwa domeny, warstwa dostępu do danych itp.). Zewnętrznie jednak jest to pojedynczy kontener — pojedynczy proces, pojedyncza aplikacja sieci web lub pojedyncza usługa.

Aby zarządzać tym modelem, należy wdrożyć pojedynczy kontener do reprezentowania aplikacji. Aby zwiększyć pojemność, można skalować w sposób skalowany, to znaczy po prostu dodać więcej kopii z modułem równoważenia obciążenia z przodu. Prostota pochodzi z zarządzania jednym wdrożeniem w jednym kontenerze lub maszynie wirtualnej.

![Diagram przedstawiający składniki aplikacji konteneryzowanej monolityczną konteneryzowaną.](./media/containerize-monolithic-applications/monolithic-containerized-application.png)

**Rysunek 4-1**. Przykład architektury konteneryzowanej aplikacji monolitycznej

W każdym kontenerze można uwzględnić wiele składników, bibliotek lub warstw wewnętrznych, jak pokazano na rysunku 4-1. Monolityczne konteneryzowane aplikacji ma większość swoich funkcji w jednym kontenerze, z wewnętrznych warstw lub bibliotek i skalowane przez klonowanie kontenera na wielu serwerach/maszynach wirtualnych. Jednak ten monolityczny wzorzec może być w konflikcie z zasadą kontenera "kontener robi jedną rzecz i robi to w jednym procesie", ale może być ok w niektórych przypadkach.

Wadą tego podejścia staje się oczywiste, jeśli aplikacja rośnie, wymagając go do skalowania. Jeśli cała aplikacja może skalować, to naprawdę nie jest problemem. Jednak w większości przypadków tylko kilka części aplikacji są punkty ssania, które wymagają skalowania, podczas gdy inne składniki są używane mniej.

Na przykład w typowej aplikacji e-commerce prawdopodobnie trzeba skalować podsystem informacji o produkcie, ponieważ znacznie więcej klientów przegląda produkty niż je kupuje. Więcej klientów korzysta z koszyka niż z potoku płatności. Mniej klientów dodaje komentarze lub przegląda historię zakupów. I może mieć tylko garstkę pracowników, którzy muszą zarządzać treścii i kampanii marketingowych. Jeśli skalowanie monolitycznego projektu, cały kod dla tych różnych zadań jest wdrażany wiele razy i skalowane w tym samym gatunku.

Istnieje wiele sposobów skalowania duplikacji poziomej aplikacji, dzielenia różnych obszarów aplikacji i dzielenia na partycje podobnych pojęć biznesowych lub danych. Jednak oprócz problemu skalowania wszystkich składników zmiany w jednym składniku wymagają pełnego ponownego testowania całej aplikacji i pełnego ponownego wdrożenia wszystkich wystąpień.

Jednak monolityczne podejście jest wspólne, ponieważ rozwój aplikacji jest początkowo łatwiejsze niż dla metod mikrousług. W ten sposób wiele organizacji rozwija się przy użyciu tego podejścia architektonicznego. Podczas gdy niektóre organizacje miały wystarczająco dobre wyniki, inne osiągają limity. Wiele organizacji zaprojektowało swoje aplikacje przy użyciu tego modelu, ponieważ narzędzia i infrastruktura zbyt trudne do tworzenia architektur zorientowanych na usługi (SOA) lat temu, a oni nie widzą potrzeby, dopóki aplikacja wzrosła.

Z punktu widzenia infrastruktury każdy serwer może uruchamiać wiele aplikacji w obrębie tego samego hosta i mieć akceptowalny stosunek wydajności w użyciu zasobów, jak pokazano na rysunku 4-2.

![Diagram przedstawiający jeden host z wieloma aplikacjami w kontenerach.](./media/containerize-monolithic-applications/host-multiple-apps-containers.png)

**Rysunek 4-2**. Monolityczne podejście: Host z uruchomionymi wieloma aplikacjami, każda aplikacja działa jako kontener

Monolityczne aplikacje na platformie Microsoft Azure można wdrożyć przy użyciu dedykowanych maszyn wirtualnych dla każdego wystąpienia. Ponadto przy użyciu [zestawów skalowania maszyn wirtualnych platformy Azure,](https://azure.microsoft.com/documentation/services/virtual-machine-scale-sets/)można łatwo skalować maszyn wirtualnych. [Usługa Azure App Service](https://azure.microsoft.com/services/app-service/) może również uruchamiać aplikacje monolityczne i łatwo skalować wystąpienia bez konieczności zarządzania maszynami wirtualnymi. Od 2016 r. usługi Azure App Services mogą również uruchamiać pojedyncze wystąpienia kontenerów platformy Docker, co upraszcza wdrażanie.

Jako środowisko kontroli jakości lub ograniczone środowisko produkcyjne można wdrożyć wiele maszyn wirtualnych hosta platformy Docker i zrównoważyć je przy użyciu balansu platformy Azure, jak pokazano na rysunku 4-3. Dzięki temu można zarządzać skalowanie z podejściem gruboziarniste, ponieważ cała aplikacja znajduje się w jednym kontenerze.

![Diagram przedstawiający kilka hostów z monolitycznymi kontenerami aplikacji.](./media/containerize-monolithic-applications/docker-infrastructure-monolithic-application.png)

**Rysunek 4-3**. Przykład wielu hostów skalowania w górę aplikacji pojedynczego kontenera

Wdrażanie na różnych hostach można zarządzać za pomocą tradycyjnych technik wdrażania. Hostami platformy Docker można `docker run` `docker-compose` zarządzać za pomocą poleceń, takich jak lub wykonywanych ręcznie, lub za pomocą automatyzacji, takich jak potoki ciągłego dostarczania (CD).

## <a name="deploying-a-monolithic-application-as-a-container"></a>Wdrażanie aplikacji monolitycznych jako kontenera

Istnieją korzyści z używania kontenerów do zarządzania wdrożeniami aplikacji monolitycznych. Skalowanie wystąpień kontenera jest znacznie szybsze i łatwiejsze niż wdrażanie dodatkowych maszyn wirtualnych. Nawet jeśli używasz zestawów skalowania maszyn wirtualnych, maszyny wirtualne zajmują trochę czasu, aby rozpocząć. Po wdrożeniu jako wystąpienia tradycyjnych aplikacji zamiast kontenerów, konfiguracja aplikacji jest zarządzana jako część maszyny Wirtualnej, która nie jest idealna.

Wdrażanie aktualizacji jako obrazów platformy Docker jest znacznie szybsze i wydajne w sieci. Obrazy platformy Docker zazwyczaj rozpoczynają się w ciągu kilku sekund, co przyspiesza wdrażanie. Niszczanie wystąpienia obrazu platformy Docker `docker stop` jest tak proste, jak wydawanie polecenia i zazwyczaj kończy się w mniej niż sekundę.

Ponieważ kontenery są niezmienne zgodnie z projektem, nigdy nie musisz się martwić o uszkodzone maszyny wirtualne. Z drugiej strony skrypty aktualizacji maszyny Wirtualnej mogą zapomnieć o uwzględnieniu określonej konfiguracji lub pliku pozostawionego na dysku.

Podczas gdy monolityczne aplikacje mogą korzystać z platformy Docker, dotykamy tylko korzyści. Dodatkowe korzyści z zarządzania kontenerami pochodzą z wdrażania z koordynatorami kontenerów, które zarządzają różnymi wystąpieniami i cyklem życia każdego wystąpienia kontenera. Podział monolityczne aplikacji na podsystemy, które mogą być skalowane, opracowywane i wdrażane indywidualnie jest punktem wejścia do sfery mikrousług.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Publikowanie aplikacji opartej na jednym kontenerze w usłudze Azure App Service

Niezależnie od tego, czy chcesz uzyskać weryfikację kontenera wdrożonego na platformie Azure, czy gdy aplikacja jest po prostu aplikacją z jednym kontenerem, usługa Azure App Service zapewnia świetny sposób na zapewnienie skalowalnych usług opartych na jednym kontenerze. Korzystanie z usługi Azure App Service jest proste. Zapewnia doskonałą integrację z Git, aby ułatwić zabrać kod, skompilować go w programie Visual Studio i wdrożyć go bezpośrednio na platformie Azure.

![Zrzut ekranu przedstawiający okno dialogowe Tworzenie usługi aplikacji z rejestrem kontenerów.](./media/containerize-monolithic-applications/publish-azure-app-service-container.png)

**Rysunek 4-4**. Publikowanie aplikacji z jednym kontenerem w usłudze Azure App Service z programu Visual Studio 2019

Bez platformy Docker, jeśli potrzebujesz innych funkcji, struktur lub zależności, które nie są obsługiwane w usłudze Azure App Service, trzeba było poczekać, aż zespół platformy Azure zaktualizował te zależności w usłudze App Service. Albo trzeba było przełączyć się do innych usług, takich jak usługi w chmurze azure lub maszyn wirtualnych, gdzie miał eś dalszą kontrolę i można zainstalować wymagany składnik lub framework dla aplikacji.

Obsługa kontenerów w programie Visual Studio 2017 i nowszych zapewnia możliwość uwzględnienia dowolnych elementów w środowisku aplikacji, jak pokazano na rysunku 4–4. Ponieważ używasz go w kontenerze, jeśli dodasz zależność do aplikacji, można dołączyć zależność w obrazie dockerfile lub docker.

Jak pokazano również na rysunku 4-4, przepływ publikowania wypycha obraz przez rejestr kontenerów. Może to być rejestr kontenerów platformy Azure (rejestr w pobliżu wdrożeń na platformie Azure i zabezpieczony przez grupy i konta usługi Azure Active Directory) lub dowolny inny rejestr platformy Docker, taki jak Centrum docker lub rejestr lokalny.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](docker-application-state-data.md)
