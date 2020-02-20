---
title: Umieszczanie aplikacji monolitycznych w kontenerze
description: Konteneryzowania monolityczne aplikacje, chociaż nie uzyskują wszystkich korzyści z architektury mikrousług, mają ważne korzyści z wdrożenia, które mogą być od razu dostarczone.
ms.date: 01/30/2020
ms.openlocfilehash: 0e6f7504a91d2b1a89193471746168fc34f50956
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503288"
---
# <a name="containerizing-monolithic-applications"></a>Umieszczanie aplikacji monolitycznych w kontenerze

Możesz chcieć utworzyć jedną, niemonolityczną aplikację sieci Web lub usługę i wdrożyć ją jako kontener. Sama aplikacja może nie być w sposób wewnętrzny monolityczny, ale ma strukturę jak kilka bibliotek, składników, a nawet warstw (warstwa aplikacji, warstwa domeny, warstwa dostępu do danych itp.). Jednak jest to jeden kontener — pojedynczy proces, pojedyncza aplikacja internetowa lub jedna usługa.

Aby zarządzać tym modelem, należy wdrożyć pojedynczy kontener do reprezentowania aplikacji. Aby zwiększyć pojemność, można skalować w poziomie, czyli po prostu dodać więcej kopii przy użyciu modułu równoważenia obciążenia. Prostota pochodzi z zarządzania pojedynczym wdrożeniem w jednym kontenerze lub maszynie wirtualnej.

![Diagram przedstawiający monolityczne składniki aplikacji w kontenerze.](./media/containerize-monolithic-applications/monolithic-containerized-application.png)

**Rysunek 4-1**. Przykład architektury aplikacji monolitycznej z kontenerem

W każdym kontenerze można uwzględnić wiele składników, bibliotek lub warstw wewnętrznych, jak pokazano na rysunku 4-1. Monolityczna aplikacja kontenera ma większość funkcji w ramach jednego kontenera z warstwami wewnętrznymi lub bibliotekami, a także skaluje się przez klonowanie kontenera na wielu serwerach/maszynach wirtualnych. Jednak ten wzór monolityczny może powodować konflikt z zasadą kontenera "kontener wykonuje jedną czynność i wykonuje go w jednym procesie", ale w niektórych przypadkach może być to OK.

Minusem tego podejścia staje się oczywisty, gdy aplikacja rośnie, wymagając do skalowania. Jeśli cała aplikacja może być skalowana, nie jest to problem. Jednak w większości przypadków zaledwie kilka części aplikacji są punktami podlewkami wymagającymi skalowania, a inne składniki są mniej używane.

Na przykład w typowej aplikacji handlu elektronicznego prawdopodobnie trzeba będzie skalować podsystem informacji o produkcie, ponieważ wielu klientów przegląda produkty od ich zakupu. Więcej klientów korzysta z koszyka niż w przypadku korzystania z potoku płatności. Mniejsza liczba klientów umożliwia dodanie komentarzy lub wyświetlenie ich historii zakupów. Może istnieć tylko kilku pracowników, którzy muszą zarządzać kampaniami i marketingami. W przypadku skalowania wzoru monolitycznego cały kod dla tych różnych zadań zostanie wdrożony wiele razy i przeskalowany w tej samej klasie.

Istnieje wiele sposobów skalowania duplikacji w poziomie aplikacji, dzielenia różnych obszarów aplikacji oraz partycjonowania podobnych koncepcji i danych firmy. Jednak oprócz problemu ze skalowaniem wszystkich składników, zmiany w pojedynczym składniku wymagają pełnego przetestowania całej aplikacji i kompletnego ponownego wdrożenia wszystkich wystąpień.

Jednak podejście monolityczne jest wspólne, ponieważ Programowanie aplikacji jest początkowo łatwiejsze niż w przypadku podejścia mikrousług. W rezultacie wiele organizacji opracowuje się przy użyciu tego podejścia do architektury. Mimo że niektóre organizacje mają wystarczającą ilość wyników, inne są ograniczone. Wiele organizacji zaprojektowali swoje aplikacje przy użyciu tego modelu, ponieważ narzędzia i infrastruktura zbyt trudne do kompilowania w latach i architektury zorientowanej na usługi (SOA) wcześniej i nie widzą potrzebnych aplikacji.

Z punktu widzenia infrastruktury każdy serwer może uruchamiać wiele aplikacji na tym samym hoście i mieć akceptowalny współczynnik wydajności w przypadku użycia zasobów, jak pokazano na rysunku 4-2.

![Diagram przedstawiający jeden host z wieloma aplikacjami w kontenerach.](./media/containerize-monolithic-applications/host-multiple-apps-containers.png)

**Rysunek 4-2**. Podejście monolityczne: Host uruchamiający wiele aplikacji, każda aplikacja uruchamiana jako kontener

Aplikacje monolityczne w Microsoft Azure można wdrożyć przy użyciu dedykowanych maszyn wirtualnych dla każdego wystąpienia. Ponadto przy użyciu [zestawów skalowania maszyn wirtualnych platformy Azure](https://azure.microsoft.com/documentation/services/virtual-machine-scale-sets/)można łatwo skalować maszyny wirtualne. [Azure App Service](https://azure.microsoft.com/services/app-service/) mogą również uruchamiać aplikacje monolityczne i łatwo skalować wystąpienia bez konieczności zarządzania maszynami wirtualnymi. Od 2016 usługa Azure App Services może również uruchamiać pojedyncze wystąpienia kontenerów platformy Docker, upraszczając wdrażanie.

Jako środowisko pytań i odpowiedzi w ograniczonym środowisku produkcyjnym można wdrożyć wiele maszyn wirtualnych hosta platformy Docker i zrównoważyć je przy użyciu modułu równoważenia obciążenia, jak pokazano na rysunku 4-3. Pozwala to na zarządzanie skalowaniem za pomocą podejścia z grubym ziarnem, ponieważ cała aplikacja znajduje się w obrębie jednego kontenera.

![Diagram przedstawiający kilka hostów z systemem monolitycznych kontenerów aplikacji.](./media/containerize-monolithic-applications/docker-infrastructure-monolithic-application.png)

**Rysunek 4-3**. Przykład wielu hostów skalowanie w górę pojedynczej aplikacji kontenera

Wdrożenie na różnych hostach może być zarządzane przy użyciu tradycyjnych technik wdrażania. Hosty platformy Docker mogą być zarządzane za pomocą poleceń takich jak `docker run` lub `docker-compose` wykonywane ręcznie lub za pomocą automatyzacji, takich jak potoki ciągłego dostarczania (CD).

## <a name="deploying-a-monolithic-application-as-a-container"></a>Wdrażanie aplikacji monolitycznej jako kontenera

Korzystanie z kontenerów umożliwia Zarządzanie wdrożeniami aplikacji monolitycznych. Skalowanie wystąpień kontenera jest znacznie szybsze i łatwiejsze niż wdrażanie dodatkowych maszyn wirtualnych. Nawet w przypadku korzystania z zestawów skalowania maszyn wirtualnych należy uruchomić maszyny wirtualne. W przypadku wdrożenia jako tradycyjnego wystąpienia aplikacji zamiast kontenerów konfiguracja aplikacji jest zarządzana w ramach maszyny wirtualnej, która nie jest idealnym rozwiązaniem.

Wdrażanie aktualizacji jako obrazów platformy Docker odbywa się znacznie szybciej i wydajniej. Obrazy platformy Docker zwykle zaczynają się w ciągu sekund, co przyspiesza wprowadzanie. Rozbicie wystąpienia obrazu platformy Docker jest tak proste jak wydawanie `docker stop` polecenia i zwykle kończy się w czasie krótszym niż sekunda.

Ponieważ kontenery są niezmienne przez projektowanie, nigdy nie trzeba martwić się o uszkodzone maszyny wirtualne. W przeciwieństwie do aktualizacji skryptów dla maszyny wirtualnej może być zapomniane uwzględnienie konkretnej konfiguracji lub pliku pozostawionego na dysku.

Chociaż aplikacje monolityczne mogą korzystać z platformy Docker, firma Microsoft dotyka tylko korzyści. Dodatkowe korzyści wynikające z zarządzania kontenerami nie są wdrażane za pomocą koordynatorów kontenerów, które zarządzają różnymi wystąpieniami i cyklem życia każdego wystąpienia kontenera. Rozdzielenie aplikacji monolitycznej na podsystemy, które mogą być skalowane, opracowywane i wdrażane, jest punktem wejścia do obszaru mikrousług.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Publikowanie aplikacji opartej na jednym kontenerze w celu Azure App Service

Bez względu na to, czy chcesz uzyskać walidację kontenera wdrożonego na platformie Azure, czy gdy aplikacja jest po prostu aplikacją jednokontenerową, Azure App Service zapewnia doskonały sposób zapewnienia skalowalnych usług opartych na jednym kontenerze. Używanie Azure App Service jest proste. Zapewnia to doskonałą integrację z usługą git, ułatwiając korzystanie z kodu, kompilowanie go w programie Visual Studio i wdrażanie go bezpośrednio na platformie Azure.

![Zrzut ekranu przedstawiający okno dialogowe Tworzenie App Service z Container Registry.](./media/containerize-monolithic-applications/publish-azure-app-service-container.png)

**Rysunek 4-4**. Publikowanie aplikacji z jednym kontenerem w celu Azure App Service z programu Visual Studio 2019

Bez platformy Docker, jeśli potrzebujesz innych możliwości, struktur lub zależności, które nie są obsługiwane w Azure App Service, musisz poczekać, aż zespół platformy Azure zaktualizował te zależności w programie App Service. Lub trzeba przełączać się do innych usług, takich jak Azure Cloud Services lub VM, w których można było kontynuować kontrolę i zainstalować wymagany składnik lub platformę dla aplikacji.

Obsługa kontenerów w programie Visual Studio 2017 i nowszych umożliwia dołączenie wszelkich potrzeb w środowisku aplikacji, jak pokazano na rysunku 4-4. Ponieważ jest on uruchamiany w kontenerze, jeśli dodasz zależność do aplikacji, możesz dołączyć zależność do obrazu pliku dockerfile lub Docker.

Jak pokazano również na rysunku 4-4, przepływ publikowania wypychanie obrazu za pomocą rejestru kontenerów. Może to być Azure Container Registry (rejestr blisko wdrożeń na platformie Azure i zabezpieczony przez Azure Active Directory grup i kont) lub dowolny inny rejestr platformy Docker, taki jak Docker Hub lub rejestr lokalny.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](docker-application-state-data.md)
