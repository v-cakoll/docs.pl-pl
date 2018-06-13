---
title: Kontenery jako podstawa współpracy opracowywania oprogramowania
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 0fa43263e789bba5b720792e7e8dc5321af795b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576223"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Kontenery jako podstawa współpracy opracowywania oprogramowania

Przez charakter kontenery i technologii Docker deweloperzy mogą udostępniać ich oprogramowania i zależności łatwo operacji IT i środowisk produkcyjnych dzięki czemu typowe usprawiedliwienia "działa na komputerze". Kontenery rozwiązać konflikty aplikacji między różnych środowiskach. Pośrednio kontenery i Docker zebrać deweloperów i operacji IT bliżej razem, ułatwiając mu współpracy. Przyjmowanie przepływu pracy kontenera zapewnia wielu klientów ciągłości DevOps zostały poszukiwane, ale wcześniej było zaimplementować za pomocą bardziej złożonych konfiguracji wydania i tworzenie potoków. Kontenery uprościć potoków kompilacji/Testowanie/wdrażania w DevOps.

![](./media/image1.png)

Rysunek 2 — 1: główny obciążeń na "osoby" w cyklu życia aplikacji Docker konteneryzowanych

Z kontenerami Docker, deweloperzy własnych nowości w ramach kontenera (aplikacji i usług i zależności do struktury i składników) i kontenery i usług zachowanie razem jako składane przez kolekcję usług aplikacji. Zależnościami wielu kontenerów są definiowane w plik docker-compose.yml lub co może być nazwane *manifest rozmieszczenia*. W tym samym czasie zespoły operacje IT (ZAWODOWYM informatykom i zarządzania) mogą skupić się na zarządzanie środowisk produkcyjnych; infrastruktury. skalowalność; monitorowanie; i ostatecznie zapewnienie, że aplikacje są dostarczane prawidłowo dla użytkowników końcowych, bez konieczności zawartość z różnych kontenerów. W związku z tym nazwy "kontenera," odwołująca odpowiednio do kontenerów wysyłanie rzeczywistych. W związku z tym Właściciele zawartości kontenera nie musi dotyczyć się z sposób zostanie dostarczona kontenera i wysyłanie transportów firmy kontener z punktu pochodzenia do miejsca docelowego bez uprzedniego uzyskania informacji o lub opiekowanie dotyczące zawartości. W podobny sposób deweloperzy można tworzyć i właścicielem treści w kontenerze Docker, bez konieczności zajmować się mechanizmów "transportu".

Słupka po lewej stronie rysunku 2-1 deweloperzy pisać i wykonuje kod lokalnie w kontenerach Docker przy użyciu rozwiązania Docker dla systemu Windows lub na komputerach Mac. Określają one środowisku operacyjnym kodu za pomocą plik Dockerfile, który określa podstawowego systemu operacyjnego do uruchomienia, a także kroków kompilacji do tworzenia kodu ich w obrazie Docker. Deweloperzy zdefiniuj, jak jeden lub więcej obrazów mogą współdziałać, przy użyciu wyżej wymienionych *docker-compose.yml* manifest wdrażania pliku. W chwili zakończenia ich lokalne działania projektowe, ich Wypchnij ich kodu aplikacji i Docker pliki konfiguracji do repozytorium kodu wybranych przez nich (czyli repozytorium Git).

Słupka DevOps definiuje potoki integracji (CI) kompilacji — ciągły przy użyciu plik Dockerfile w repozytorium kodu. CI system pobiera obrazy kontenera podstawowej z wybranych rejestru Docker i tworzy niestandardowe obrazy Docker dla aplikacji. Obrazy następnie weryfikacji i przypisany do rejestru Docker używany we wdrożeniach w wielu środowiskach.

W słupka po prawej stronie Operacje, które zespoły Zarządzanie wdrożenie aplikacji i infrastruktury w środowisku produkcyjnym, podczas monitorowania środowiska i aplikacji, dzięki czemu zapewniają opinie i szczegółowe informacje o jak aplikacja może być zespół deweloperów Ulepszona. Aplikacje kontenera są zazwyczaj uruchamiane w środowisku produkcyjnym za pomocą orchestrators kontenera.

Dwóch zespołach współpracują za pośrednictwem podstawowych platforma (kontenery Docker), która zapewnia separacji jako kontraktu, podczas znacznie poprawia dwóch zespołach współpraca w cyklu życia aplikacji. Deweloperzy właścicielem zawartości kontenera, jego środowisku operacyjnym i zależnościami kontenera zespołów operacyjnych zająć obrazów zbudowanych wraz z manifestu i uruchamia je w ich systemie aranżacji.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Wprowadzenie do ogólnego przepływu cyklu życia aplikacji Docker end-to-end

Rysunek 2-2 przedstawia bardziej szczegółowy przepływ pracy dla cyklu życia aplikacji Docker koncentrujących się w tym wystąpieniu na konkretne działania DevOps i zasoby.

![](./media/image2.png)

Rysunek 2-2: ogólny przepływ pracy Docker konteneryzowanych cyklu życia aplikacji

Wszystko, co rozpoczyna się od projektanta, który rozpoczyna się pisanie kodu w przepływie pracy wewnętrzny pętli. Etap wewnętrzny pętli to, gdy deweloperzy zdefiniuj wszystko, co się stanie, przed wypchnięciem kod do repozytorium kodu (na przykład systemu kontroli źródła np. Git). Po zobowiązuje się repozytorium wyzwala ciągłej integracji (CI) i pozostałej części przepływu pracy.

Fragment pętli zasadniczo składa się z typowe etapy, takich jak 'code' "," "test", "debug", a także dodatkowe kroki bezpośrednio przed uruchomieniem uruchomić aplikację lokalnie. Jest to, gdy dewelopera testów aplikacji jako kontener Docker. W poniższych sekcjach opisano pętli wewnętrzny przepływ pracy.

Odebraniem krok aby przyjrzeć się przepływu pracy — do zakończenia, metodyki DevOps przepływu pracy jest większa niż technologii lub zestawu narzędzi: jest mindset, wymagającego ewolucji kultury. Jest osób, procesów i odpowiednie narzędzia, aby cyklu życia aplikacji szybsze i bardziej przewidywalne. Przedsiębiorstw, które przyjmują konteneryzowanych przepływu pracy zwykle restrukturyzacji organizacji do reprezentowania osoby i procesy, które spełniają konteneryzowanych przepływu pracy.

Ćwiczenia opracowywania oprogramowania może pomóc zespoły uwzględniał szybciej razem nacisk konkurencji przez zamianę procesów ręcznych podatnych automatyzacji, co powoduje ulepszona możliwość śledzenia i powtarzalne przepływów pracy. Organizacje można również efektywniej zarządzać środowiskami i osiągnięcia oszczędności z kombinacją lokalnych i dostępnych zasobów w chmurze, a także ściśle zintegrowane narzędzia.

Podczas wykonywania przepływu pracy opracowywania oprogramowania dla aplikacji Docker, zobaczysz, że technologie Docker na znajdują się w niemal każdego etapu przepływu pracy, z Twojego pola programowanie podczas pracy w pętli wewnętrzny (code, uruchamianie, debugowania), do fazy kompilacji test-CI i, Oczywiście w produkcyjne i przejściowe środowisk i wdrażanie kontenerów do tych środowisk.

Poprawa jakości rozwiązania pomaga w identyfikacji wady wczesnym etapie cyklu projektowania, co zmniejsza koszty ich rozwiązywania. W tym środowisku i zależności w obrazie i przyjęcia zasady wdrażania ten sam obraz w wielu środowiskach, podwyższyć poziom dyscypliny wyodrębniania konfiguracje specyficzne dla środowiska wprowadzania wdrożeń bardziej niezawodne.

Zaawansowanych danych uzyskanych przy użyciu Instrumentacji skuteczne (monitorowania i diagnostyki) zapewnia wgląd w problemy z wydajnością i zachowania użytkowników prowadzące przyszłych priorytetów i inwestycji.

Należy rozważyć DevOps podróży, a nie miejsca docelowego. Powinien on implementowane przyrostowo za pośrednictwem odpowiednio zakresie projektów, z których można pokazują sukces, Dowiedz się więcej i rozwijać.

## <a name="benefits-of-devops-for-containerized-applications"></a>Zalety opracowywania oprogramowania dla aplikacji konteneryzowanych

Oto niektóre z najważniejszych zalet stałe DevOps przepływu pracy:

-   Dostarczanie oprogramowania lepszą jakość szybsze i lepszą zgodność

-   Poprawa ciągłych i dostosowania dysków wcześniej i bardziej ekonomicznego

-   Zwiększenia przejrzystości i współpracę uczestników objętego dostarczania i obsługi oprogramowania

-   Kontrolę kosztów i wykorzystania zasobów elastycznie efektywniej przy jednoczesnym zmniejszeniu zagrożenia bezpieczeństwa

-   Plug and play również z wieloma dotychczasowych inwestycji DevOps, w tym inwestycji w typu open source

>[!div class="step-by-step"]
[Poprzednie] (index.md) [dalej] (.. /Microsoft-Platform-Tools-containerized-Apps/index.MD)
