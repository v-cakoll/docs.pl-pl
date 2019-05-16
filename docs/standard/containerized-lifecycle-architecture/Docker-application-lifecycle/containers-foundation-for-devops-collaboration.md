---
title: Kontenery jako podstawa współpracy w metodyce DevOps
description: Poznaj kluczowe rolę kontenerów, aby usprawnić metodyki DevOps.
ms.date: 02/15/2019
ms.openlocfilehash: 37faf00f270414df363f36894317f31f81a2937e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641318"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Kontenery jako podstawa współpracy w metodyce DevOps

Przez charakter kontenerów i technologii platformy Docker deweloperzy mogą udostępniać ich oprogramowania i zależności łatwo operacji IT i środowisk produkcyjnych eliminuje typowe usprawiedliwienia "działa na komputerze". Kontenery rozwiązać konflikty aplikacji między różnymi środowiskami. Pośrednio kontenery i Docker Połącz deweloperów i operacji IT bliżej, ułatwiając użytkownikom efektywną współpracę. Wdrażanie kontenera przepływu pracy zapewnia klientom wiele ciągłości metodyki DevOps po poszukiwane, ale wcześniej było zaimplementować bardziej złożonych konfiguracji dla wersji oraz tworzenia potoków. Kontenery upraszczają potoki kompilacji/Testowanie/wdrażania w metodyce DevOps.

![Docker ułatwia tworzenie mostków między dla deweloperów i architektów na obciążenie programowanie/projektowanie i działu operacji IT w przypadku obciążenia Uruchom/monitorowania/zarządzania](./media/image1.png)

**Rysunek 2-1.** Główne obciążeń na "osób" w cyklu życia konteneryzowanych aplikacji platformy Docker

Z kontenerami aparatu Docker, deweloperzy własnych co mieści się w kontenerze (aplikacji i usług i zależności, aby struktury i składników) i kontenerów i usług zachowaniem ze sobą jako aplikacja zawiera zbiór usług. Współzależności wiele kontenerów są zdefiniowane w `docker-compose.yml` pliku lub co może być nazwane *manifest wdrożenia*. W tym samym czasie zespołów operacyjnych IT (specjaliści IT i zarządzania) mogą skupić się na zarządzanie środowisk produkcyjnych; infrastruktury. skalowalność; monitorowanie; i ostatecznie zapewnienie, że aplikacje są dostarczane prawidłowo dla użytkowników końcowych bez znajomości zawartość kontenerów różne. Dlatego nazwy "kontener," przywołując analogię do świata rzeczywistego wysyła kontenery. W związku z tym właściciele zawartość kontenerów nie musi dotyczyć samodzielnie przy użyciu jak kontenera zostanie wysłane i wysyłanie transportów firmy kontenera z punktu pochodzenia do miejsca docelowego bez znajomości lub opiekowanie dotyczących zawartości. W podobny sposób deweloperzy mogą tworzyć i właścicielem treści w kontenerze platformy Docker, bez konieczności zajmowania się mechanizmy "transportu".

Pillar po lewej stronie rysunku 2-1 deweloperom pisać i uruchomienia kodu lokalnie w kontenerach platformy Docker przy użyciu platformy Docker for Windows i Mac. Określają one środowisko operacyjne dla kodu za pomocą pliku Dockerfile, który określa podstawowego systemu operacyjnego do uruchomienia, a także kroków kompilacji do tworzenia kodu do obrazu platformy Docker. Deweloperzy zdefiniować sposób jeden lub więcej obrazów mogą współdziałać za pomocą wyżej wymienionych `docker-compose.yml` pliku manifestu wdrożenia. Po ich zakończeniu ich rozwoju lokalnych, ich Wypchnij swój kod aplikacji oraz pliki konfiguracji platformy Docker do repozytorium kodu wybranych przez nich (czyli repozytorium Git).

Filaru DevOps definiuje potoki ciągłej integracji kompilacji — ciągłe przy użyciu plik Dockerfile znajdujący się w repozytorium kodu. System ciągłej integracji ściąga obrazów kontenerów podstawowej z wybranym rejestrem platformy Docker i tworzy niestandardowe obrazy platformy Docker dla aplikacji. Obrazy są następnie zweryfikowane i wypchnięte do rejestru platformy Docker używana w przypadku wdrożeń w wielu środowiskach.

W pillar po prawej stronie Operacje, które zespoły zarządzać wdrożonych aplikacji i infrastruktury w środowisku produkcyjnym podczas monitorowania środowiska i aplikacji, dzięki czemu zapewniają opinie i szczegółowych informacji o jak aplikacja może być zespołowi opracowującemu Ulepszona. Aplikacje kontenera są zazwyczaj uruchamiane w środowisku produkcyjnym przy użyciu koordynatorów kontenerów.

Dwa zespoły współpracują za pośrednictwem platformy podstawowe (kontenery platformy Docker), zapewniająca separacji zagadnień jako kontraktu, znacznie zwiększając współpracy dwa zespoły w cyklu życia aplikacji jednocześnie. Deweloperzy właścicielem zawartość kontenerów, jego środowisko operacyjne i współzależnościach kontenera, natomiast zespołów operacyjnych zająć utworzone obrazy wraz z manifestu i wykonuje na nich w ich systemie aranżacji.

## <a name="challenges-in-application-life-cycle-when-using-docker"></a>Wyzwaniom związanym z życia aplikacji cyklu, korzystając z platformy Docker.

Istnieje wiele przyczyn, które spowoduje zwiększenie liczby konteneryzowanych aplikacji w ciągu przyszłych lat, a jeden z następujących powodów jest tworzenie aplikacji opartych na mikrousługach.

W ciągu ostatnich 15 lat korzystanie z usług sieci web jest podstawą tysiące aplikacji, i prawdopodobnie po kilku latach będzie znaleźliśmy tej samej sytuacji przy użyciu opartych na mikrousługach działających w kontenerach platformy Docker.

Warto również wspomnieć o czy umożliwia również kontenery platformy Docker dla aplikacji monolitycznych i będzie nadal się pojawiać większości korzyści z platformy Docker. Kontenery nie są przeznaczone dla tylko mikrousług.

Korzystanie z platformy Docker obsługi kontenerów i mikrousług powoduje, że nowe wyzwania w procesie rozwoju Twojej organizacji i w związku z tym, należy dobrze zdefiniowaną strategię do obsługi wielu kontenerów i mikrousług działających w systemach produkcyjnych. Po pewnym czasie aplikacje dla przedsiębiorstw mają setek lub tysięcy kontenerów/wystąpień działających w środowisku produkcyjnym.

Te wyzwania tworzenie nowych wymagań, korzystając z narzędzi DevOps, dzięki czemu będziesz mieć do definiowania nowych procesów w działaniach DevOps i odpowiedzi dla tego typu pytania:

- Narzędzia, których można używać do tworzenia aplikacji, ciągłej integracji/ciągłego wdrażania, zarządzania i operacji?

- Jak Moja firma zarządzać błędami w kontenerach podczas uruchamiania w środowisku produkcyjnym?

- Jak możemy zmienić nasze oprogramowanie w środowisku produkcyjnym z minimalnym przestojem

- Jak możemy skalować i jak możemy monitorować naszego systemu produkcji?

- Jak można uwzględnić testowanie i wdrażanie kontenerów w nasz potok wersji?

- Jak można użyć narzędzia/platform typu Open Source dla kontenerów w systemie Microsoft Azure?

Jeśli odpowiesz te pytania, można lepiej wiedzy, aby przejść do aplikacji (aplikacje do istniejącego lub nowego) w kontenerach platformy Docker. 

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Wprowadzenie do ogólnego przepływu cyklu życia aplikacji platformy Docker end-to-end

Rysunek 2-2 przedstawia informacje o bardziej szczegółowy przepływ pracy dla cyklu życia aplikacji platformy Docker, koncentrując się w tym wystąpieniu na określonych działań metodyki DevOps i zasoby.

![Ten diagram przedstawia "zewnętrzna pętla" metodyki DevOps. Wypchnięcie kodu do repozytorium potoku ciągłej integracji jest uruchomiona, a następnie rozpoczyna się potok ciągłego wdrażania, w którym aplikacja zostanie wdrożona. Metryki zebrane z wdrożonych aplikacji są podawane na obciążenie programowanie, w którym występuje "wewnętrzną pętlę", więc zespoły programistyczne rzeczywistych danych, aby odpowiedzieć na użytkownika oraz o potrzebach biznesowych.](./media/image2.png)

**Rysunek 2-2.** Ogólny przepływ pracy dla cyklu życia konteneryzowanych aplikacji platformy Docker

Wszystko zaczyna się od deweloperów, który rozpoczyna pisanie kodu w przepływie pracy wewnętrznej pętli. Etapu wewnętrzną pętli jest, gdzie deweloperów zdefiniować wszystko, co ma miejsce przed wypychanie kodu do repozytorium kodu (na przykład systemu kontroli źródła takich jak Git). Po nim zobowiązał, repozytorium wyzwalacze ciągłej integracji (CI) i pozostałej części przepływu pracy.

Wewnętrzną pętlę zasadniczo obejmuje typowe etapy, takich jak "code", "run", "test" i "debugowanie" oraz dodatkowych czynnościach, bezpośrednio przed uruchamianie aplikacji lokalnie. Jest to proces dewelopera, aby uruchomić i przetestować aplikację w kontenerze aparatu Docker. Przepływ pracy wewnętrznej pętli zostaną wyjaśnione w kolejnych sekcjach.

Przyjęcie krok z powrotem do wzięcia pod — do zakończenia przepływu pracy, przepływ pracy DevOps jest większa niż technologii lub zestawu narzędzi: jest to sposób myślenia wymagającego ewolucji kultury. Jego ludzi, procesów i odpowiednie narzędzia aby cyklu życia aplikacji szybsze i bardziej przewidywalne. Przedsiębiorstwa, które przyjęły konteneryzowanych przepływu pracy zwykle restrukturyzacja organizacji do reprezentowania ludzi i procesy, które odpowiadają konteneryzowanych przepływu pracy.

Ćwiczenia, metodyki DevOps może pomóc zespołom szybszego reagowania na razem nacisk konkurencji, zastępując procesów ręcznych podatne automatyzację, co skutkuje ulepszone możliwości śledzenia i powtarzalne przepływy pracy. Organizacje można również efektywniej zarządzać środowiskami i osiągnięcia oszczędności dzięki kombinacji lokalnych i zasobów w chmurze, a także ściśle zintegrowanych narzędzi.

Podczas implementowania przepływ pracy infrastruktury DevOps dla aplikacji platformy Docker, zobaczysz, że technologii Docker występują w prawie każdym etapie przepływu pracy, z Twojej pole rozwoju podczas pracy w pętli wewnętrzny (kod, uruchamiania, debugowania), fazy kompilacji test-ciągłej integracji i, na koniec wdrażanie tych kontenerów do środowiskach przejściowych i produkcyjnych.

Poprawa jakości rozwiązania pomaga w identyfikacji usterek na wczesnym etapie cyklu projektowania, co zmniejsza koszty ich rozwiązywania. W tym środowisku i zależności w obrazie i przyjęcie filozofia wdrażania tego samego obrazu w wielu środowiskach, podwyższanie poziomu dyscypliny wyodrębniania konfiguracje specyficzne dla środowiska, co bardziej niezawodne wdrożenia.

Danych uzyskanych za pośrednictwem skuteczne Instrumentacji (monitorowania i diagnostyki) zapewnia wgląd w problemy z wydajnością i zachowania użytkowników dotyczące przyszłych priorytetów i inwestycji.

To podróż, a nie miejsca docelowego należy rozważyć metodyki DevOps. Jego należy wdrożyć przyrostowo poprzez projekty odpowiednio o określonym zakresie, z których można pokazują sukces, Dowiedz się więcej i rozwijać.

## <a name="benefits-of-devops-for-containerized-applications"></a>Zalety DevOps dla aplikacji konteneryzowanych

Oto niektóre z najważniejszych zalet pełny przepływ pracy DevOps:

- Dostarczaj lepiej jakości oprogramowania szybciej i lepszą zgodność.

- Dbaj o ciągłego doskonalenia i dostosowania wcześniej i bardziej ekonomicznie.

- Zwiększenie przejrzystości i współpracę między zainteresowane strony zaangażowane w dostarczanie i używania oprogramowania.

- Kontrolowanie kosztów i bardziej efektywne wykorzystanie aprowizowane zasoby przy jednoczesnym zmniejszeniu zagrożenia dla bezpieczeństwa.

- Typu Plug and play dobrze z wieloma istniejące inwestycje metodyki DevOps, łącznie z inwestycjami typu open source.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](../Microsoft-platform-tools-containerized-apps/index.md)
