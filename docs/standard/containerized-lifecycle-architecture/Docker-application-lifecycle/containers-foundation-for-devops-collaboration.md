---
title: Kontenery jako podstawa współpracy w metodyce DevOps
description: Poznaj kluczowe rolę kontenerów, aby usprawnić metodyki DevOps.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: d0339199092304dd6c91707d8cf4da213f110b58
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219294"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Kontenery jako podstawa współpracy w metodyce DevOps

Przez charakter kontenerów i technologii platformy Docker deweloperzy mogą udostępniać ich oprogramowania i zależności łatwo operacji IT i środowisk produkcyjnych eliminuje typowe usprawiedliwienia "działa na komputerze". Kontenery rozwiązać konflikty aplikacji między różnymi środowiskami. Pośrednio kontenery i Docker Połącz deweloperów i operacji IT bliżej, ułatwiając użytkownikom efektywną współpracę. Wdrażanie kontenera przepływu pracy zapewnia klientom wiele ciągłości metodyki DevOps po poszukiwane, ale wcześniej było zaimplementować bardziej złożonych konfiguracji dla wersji oraz tworzenia potoków. Kontenery upraszczają potoki kompilacji/Testowanie/wdrażania w metodyce DevOps.

![](./media/image1.png)

Rysunek 2-1. Główne obciążeń na "osób" w cyklu życia konteneryzowanych aplikacji platformy Docker

Z kontenerami aparatu Docker, deweloperzy własnych co mieści się w kontenerze (aplikacji i usług i zależności, aby struktury i składników) i kontenerów i usług zachowaniem ze sobą jako aplikacja zawiera zbiór usług. Współzależności wiele kontenerów są zdefiniowane w pliku docker-compose.yml lub co może być nazwane *manifest wdrożenia*. W tym samym czasie zespołów operacyjnych IT (specjaliści IT i zarządzania) mogą skupić się na zarządzanie środowisk produkcyjnych; infrastruktury. skalowalność; monitorowanie; i ostatecznie zapewnienie, że aplikacje są dostarczane prawidłowo dla użytkowników końcowych bez znajomości zawartość kontenerów różne. Dlatego nazwy "kontener," przywołując analogię do świata rzeczywistego wysyła kontenery. W związku z tym właściciele zawartość kontenerów nie musi dotyczyć samodzielnie przy użyciu jak kontenera zostanie wysłane i wysyłanie transportów firmy kontenera z punktu pochodzenia do miejsca docelowego bez znajomości lub opiekowanie dotyczących zawartości. W podobny sposób deweloperzy mogą tworzyć i właścicielem treści w kontenerze platformy Docker, bez konieczności zajmowania się mechanizmy "transportu".

Pillar po lewej stronie rysunku 2-1 deweloperom pisać i uruchomienia kodu lokalnie w kontenerach platformy Docker przy użyciu platformy Docker for Windows i Mac. Określają one środowisko operacyjne dla kodu za pomocą pliku Dockerfile, który określa podstawowego systemu operacyjnego do uruchomienia, a także kroków kompilacji do tworzenia kodu do obrazu platformy Docker. Deweloperzy zdefiniowanie, jak jeden lub więcej obrazów mogą współdziałać za pomocą wyżej wymienionych *docker-compose.yml* pliku manifestu wdrożenia. Po ich zakończeniu ich rozwoju lokalnych, ich Wypchnij swój kod aplikacji oraz pliki konfiguracji platformy Docker do repozytorium kodu wybranych przez nich (czyli repozytorium Git).

Filaru DevOps definiuje potoki ciągłej integracji kompilacji — ciągłe przy użyciu plik Dockerfile znajdujący się w repozytorium kodu. System ciągłej integracji ściąga obrazów kontenerów podstawowej z wybranym rejestrem platformy Docker i tworzy niestandardowe obrazy platformy Docker dla aplikacji. Obrazy są następnie zweryfikowane i wypchnięte do rejestru platformy Docker używana w przypadku wdrożeń w wielu środowiskach.

W pillar po prawej stronie Operacje, które zespoły zarządzać wdrożonych aplikacji i infrastruktury w środowisku produkcyjnym podczas monitorowania środowiska i aplikacji, dzięki czemu zapewniają opinie i szczegółowych informacji o jak aplikacja może być zespołowi opracowującemu Ulepszona. Aplikacje kontenera są zazwyczaj uruchamiane w środowisku produkcyjnym przy użyciu koordynatorów kontenerów.

Dwa zespoły współpracują za pośrednictwem platformy podstawowe (kontenery platformy Docker), zapewniająca separacji zagadnień jako kontraktu, znacznie zwiększając współpracy dwa zespoły w cyklu życia aplikacji jednocześnie. Deweloperzy właścicielem zawartość kontenerów, jego środowisko operacyjne i współzależnościach kontenera, natomiast zespołów operacyjnych zająć utworzone obrazy wraz z manifestu i wykonuje na nich w ich systemie aranżacji.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Wprowadzenie do ogólnego przepływu cyklu życia aplikacji platformy Docker end-to-end

Rysunek 2-2 przedstawia informacje o bardziej szczegółowy przepływ pracy dla cyklu życia aplikacji platformy Docker, koncentrując się w tym wystąpieniu na określonych działań metodyki DevOps i zasoby.

![](./media/image2.png)

Rysunek 2-2: Ogólny przepływ pracy dla cyklu życia konteneryzowanych aplikacji platformy Docker

Wszystko zaczyna się od deweloperów, który rozpoczyna pisanie kodu w przepływie pracy wewnętrznej pętli. Etapu wewnętrzną pętli jest, gdzie deweloperów zdefiniować wszystko, co ma miejsce przed wypychanie kodu do repozytorium kodu (na przykład systemu kontroli źródła takich jak Git). Po zostanie zatwierdzony, repozytorium wyzwalacze ciągłej integracji (CI) i pozostałej części przepływu pracy.

Wewnętrzną pętlę zasadniczo obejmuje typowe etapy, takich jak "code", "run," "test" i "debug", a także dodatkowe kroki przed uruchamianie aplikacji lokalnie. Jest to, gdy deweloper testuje aplikację jako kontener platformy Docker. Przepływ pracy wewnętrznej pętli zostaną wyjaśnione w kolejnych sekcjach.

Przyjęcie krok z powrotem do wzięcia pod — do zakończenia przepływu pracy, przepływ pracy DevOps jest większa niż technologii lub zestawu narzędzi: jest to sposób myślenia wymagającego ewolucji kultury. Jest to osoby, procesy i odpowiednie narzędzia, aby cyklu życia aplikacji szybsze i bardziej przewidywalne. Przedsiębiorstwa, które przyjęły konteneryzowanych przepływu pracy zwykle restrukturyzacja organizacji do reprezentowania ludzi i procesy, które odpowiadają konteneryzowanych przepływu pracy.

Ćwiczenia, metodyki DevOps może pomóc zespołom szybszego reagowania na razem nacisk konkurencji, zastępując procesów ręcznych podatne automatyzację, co skutkuje ulepszone możliwości śledzenia i powtarzalne przepływy pracy. Organizacje można również efektywniej zarządzać środowiskami i osiągnięcia oszczędności dzięki kombinacji lokalnych i zasobów w chmurze, a także ściśle zintegrowanych narzędzi.

Podczas implementowania przepływ pracy infrastruktury DevOps dla aplikacji platformy Docker, zobaczysz, czy obecne w prawie każdym etapie przepływu pracy, z Twojej pole rozwoju podczas pracy w pętli wewnętrzny (kod, uruchamiania, debugowania), do fazy kompilacji test-CI technologii platformy Docker i Oczywiście na środowiska produkcyjne i tymczasowe i wdrażanie kontenerów w tych środowiskach.

Poprawa jakości rozwiązania pomaga w identyfikacji usterek na wczesnym etapie cyklu projektowania, co zmniejsza koszty ich rozwiązywania. W tym środowisku i zależności w obrazie i przyjęcie filozofia wdrażania tego samego obrazu w wielu środowiskach, podwyższanie poziomu dyscypliny wyodrębniania konfiguracje specyficzne dla środowiska, co bardziej niezawodne wdrożenia.

Danych uzyskanych za pośrednictwem skuteczne Instrumentacji (monitorowania i diagnostyki) zapewnia wgląd w problemy z wydajnością i zachowania użytkowników dotyczące przyszłych priorytetów i inwestycji.

To podróż, a nie miejsca docelowego należy rozważyć metodyki DevOps. Jego należy wdrożyć przyrostowo poprzez projekty odpowiednio o określonym zakresie, z których można pokazują sukces, Dowiedz się więcej i rozwijać.

## <a name="benefits-of-devops-for-containerized-applications"></a>Zalety DevOps dla aplikacji konteneryzowanych

Oto niektóre z najważniejszych zalet pełny przepływ pracy DevOps:

-   Dostarczaj lepiej jakości oprogramowania, szybciej i lepszą zgodność

-   Zadbaj o ciągłego doskonalenia i korekty wcześniej i bardziej ekonomicznie

-   Zwiększenie przejrzystości i współpracę między zainteresowane strony zaangażowane w dostarczanie i działające oprogramowanie

-   Kontrolowanie kosztów i bardziej efektywne wykorzystanie aprowizowane zasoby przy jednoczesnym zmniejszeniu zagrożenia bezpieczeństwa

-   Typu Plug and play dobrze z wieloma istniejące inwestycje metodyki DevOps, łącznie z inwestycji w technologię open source

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](../Microsoft-platform-tools-containerized-apps/index.md)