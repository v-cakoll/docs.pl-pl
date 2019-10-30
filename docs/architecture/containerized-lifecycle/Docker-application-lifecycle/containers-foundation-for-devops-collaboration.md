---
title: Kontenery jako podstawa współpracy w metodyce DevOps
description: Poznaj kluczową rolę kontenerów w celu usprawnienia DevOps.
ms.date: 02/15/2019
ms.openlocfilehash: 8258f4331212d92376d64fef318adcdff492f61f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094497"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Kontenery jako podstawa współpracy w metodyce DevOps

Za pomocą bardzo dużej natury kontenerów i technologii platformy Docker deweloperzy mogą łatwo udostępniać swoje oprogramowanie i zależności przy użyciu operacji IT i środowisk produkcyjnych, jednocześnie eliminując typowy "działający na mojej maszynie" wymówką. Kontenery rozwiązują konflikty aplikacji między różnymi środowiskami. Pośrednie, kontenery i platforma Docker umożliwiają deweloperom i pracę nad nimi bliżej siebie, co ułatwia ich efektywne współdziałanie. Wdrożenie przepływu pracy kontenera zapewnia wielu klientom nieprzerwane DevOps, które wcześniej wymagały wdrożenia przy użyciu bardziej złożonej konfiguracji dla potoków wydania i kompilacji. Kontenery upraszczają potoki kompilowania/testowania/wdrażania w DevOps.

![Diagram przedstawiający własność cyklu życia aplikacji platformy Docker.](./media/containers-foundation-for-devops-collaboration/persona-workloads-docker-container-lifecycle.png)

**Rysunek 2-1.** Główne obciążenia na "osób" w cyklu życia dla kontenerów aplikacji platformy Docker

W przypadku kontenerów platformy Docker deweloperzy są własnością tego, co znajduje się w kontenerze (aplikacji i usługi, oraz zależności od struktur i składników) oraz jak kontenery i usługi działają razem jako aplikacja składająca się z kolekcji usług. Wzajemne zależności wielu kontenerów są zdefiniowane w pliku `docker-compose.yml` lub co może być nazywane *manifestem wdrożenia*. Tymczasem zespoły operacyjne IT (specjaliści IT i zarządzanie) mogą skupić się na zarządzaniu środowiskami produkcyjnymi. pozostając względem kontrolą i ostatecznie, dzięki czemu aplikacje są dostarczane prawidłowo dla użytkowników końcowych, bez konieczności znajomości zawartości różnych kontenerów. W związku z tym nazwa "kontener" polega na odproszeniu analogowego do rzeczywistych kontenerów wysyłkowych. W ten sposób właściciele zawartości kontenera nie muszą odnosi się do sposobu dostarczania kontenera, a firma żeglugi transportuje kontener z punktu pochodzenia do miejsca docelowego bez znajomości lub Caring o zawartości. W podobny sposób deweloperzy mogą tworzyć i własnością zawartość w kontenerze platformy Docker bez konieczności zapoznania się z mechanizmami "transport".

W filarzie po lewej stronie rysunku 2-1 deweloperzy zapisują i uruchamiają kod lokalnie w kontenerach platformy Docker przy użyciu Docker for Windows lub Mac. Definiują one środowisko operacyjne dla kodu przy użyciu pliku dockerfile, który określa podstawowy system operacyjny do uruchomienia, a także kroki kompilacji do kompilowania kodu do obrazu platformy Docker. Deweloperzy definiują, jak co najmniej jeden obraz będzie współdziałać przy użyciu powyższego manifestu wdrażania plików `docker-compose.yml`. Gdy ukończyją swoje lokalne programowanie, wypychanie kodu aplikacji oraz plików konfiguracji platformy Docker do wybranego przez siebie repozytorium kodu (to jest repozytorium Git).

Filar DevOps definiuje potok kompilacji — ciągłej integracji (CI) przy użyciu pliku dockerfile w repozytorium kodu. System CI pobiera podstawowe obrazy kontenerów z wybranego rejestru platformy Docker i tworzy niestandardowe obrazy platformy Docker dla aplikacji. Obrazy są następnie weryfikowane i wypychane do rejestru platformy Docker używanego do wdrożeń w wielu środowiskach.

W filarzie po prawej stronie zespoły ds. operacji zarządzają wdrożonymi aplikacjami i infrastrukturą w środowisku produkcyjnym, podczas gdy monitorują środowisko i aplikacje, dzięki czemu mogą one dostarczać Opinie i szczegółowe informacje dotyczące zespołu deweloperów dotyczące sposobu, w jaki aplikacja może być poprawienie. Aplikacje kontenera są zwykle uruchamiane w środowisku produkcyjnym przy użyciu koordynatorów kontenerów.

Dwa zespoły współpracują za pośrednictwem podstawowej platformy (kontenerów platformy Docker), która zapewnia oddzielenie problemów jako kontraktu, a jednocześnie znacznie ulepsza współpracę obu zespołów w cyklu życia aplikacji. Deweloperzy są właścicielami zawartości kontenera, jego środowiska operacyjnego oraz współzależności między kontenerami, podczas gdy zespoły operacji pobierają utworzone obrazy wraz z manifestem i uruchamiają je w systemie aranżacji.

## <a name="challenges-in-application-life-cycle-when-using-docker"></a>Wyzwania związane z cyklem życia aplikacji podczas korzystania z platformy Docker.

Istnieje wiele przyczyn, które spowodują zwiększenie liczby aplikacji kontenerowych w nadchodzących latach, a jednym z tych powodów jest tworzenie aplikacji na podstawie mikrousług.

W ciągu ostatnich 15 lat korzystanie z usług sieci Web była podstawą tysięcy aplikacji i prawdopodobnie po kilku latach będzie można znaleźć taką samą sytuację w przypadku aplikacji opartych na mikrousługach działających w kontenerach platformy Docker.

Należy również zauważyć, że można również użyć kontenerów platformy Docker dla aplikacji monolitycznych, a mimo to uzyskać większość zalet platformy Docker. Kontenery nie mają tylko mikrousług.

Korzystanie z rozwiązań Docker kontenerach i mikrousług powoduje nowe wyzwania w procesie opracowywania organizacji, dlatego potrzebna jest jednolita strategia do obsługi wielu kontenerów i mikrousług działających w systemach produkcyjnych. Ostatecznie aplikacje dla przedsiębiorstw będą mieć setki lub tysiące kontenerów/wystąpień działających w środowisku produkcyjnym.

Te wyzwania pozwalają utworzyć nowe wymagania w przypadku korzystania z narzędzi DevOps, aby móc definiować nowe procesy w działaniach DevOps i znajdować odpowiedzi na pytania tego typu:

- Których narzędzi można używać do programowania, w przypadku ciągłej integracji/ciągłego wdrażania, zarządzania i operacji?

- Jak moja firma może zarządzać błędami w kontenerach podczas pracy w środowisku produkcyjnym?

- Jak można zmienić fragmenty naszego oprogramowania w środowisku produkcyjnym z minimalnym czasem przestoju?

- Jak możemy skalować i jak można monitorować nasz system produkcyjny?

- Jak możemy uwzględnić testowanie i wdrażanie kontenerów w naszym potoku wydania?

- Jak można używać narzędzi/platform Open Source dla kontenerów w Microsoft Azure?

Jeśli możesz odpowiedzieć na wszystkie pytania, możesz lepiej przystąpić do przenoszenia aplikacji (istniejących lub nowych aplikacji) do kontenerów platformy Docker.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Wprowadzenie do ogólnego przepływu pracy cyklu życia aplikacji platformy Docker

Rysunek 2-2 przedstawia bardziej szczegółowy przepływ pracy dla cyklu życia aplikacji platformy Docker, koncentrując się na tym wystąpieniu w określonych działaniach i zasobach DevOps.

![Diagram przedstawiający ogólny cykl życiowy aplikacji platformy Docker.](./media/containers-foundation-for-devops-collaboration/generic-end-to-enddpcker-app-life-cycle.png)

**Rysunek 2-2.** Przepływ pracy wysokiego poziomu dla cyklu życia aplikacji kontenera platformy Docker

Wszystko zaczyna się od programisty, który rozpoczyna pisanie kodu w przepływie pracy z pętlą wewnętrzną. Etap wewnętrznej pętli polega na tym, że deweloperzy definiują wszystkie elementy, które są wykonywane przed wypchnięciem kodu do repozytorium kodu (na przykład system kontroli źródła, taki jak Git). Po jego zatwierdzeniu repozytorium wyzwala ciągłą integrację (CI) i resztę przepływu pracy.

Pętla wewnętrzna zasadniczo składa się z typowych kroków, takich jak "Code", "Run" "test" i "debug" oraz dodatkowe czynności wymagane bezpośrednio przed uruchomieniem aplikacji lokalnie. Jest to proces programisty służący do uruchamiania i testowania aplikacji jako kontenera Docker. Przepływ pracy w pętli wewnętrznej zostanie wyjaśniony w poniższych sekcjach.

Po przełączeniu się z powrotem do końca przepływu pracy DevOps przepływ pracy jest większy niż technologia lub zestaw narzędzi: jest to sposób myślenia, który wymaga ewolucji kulturowej. Są one osobami, procesami i odpowiednimi narzędziami, dzięki którym cykl życia aplikacji jest szybszy i bardziej przewidywalny. Przedsiębiorstwa, które przyjmują kontenerowy przepływ pracy, zwykle restrukturyzacją organizacji w celu reprezentowania osób i procesów, które pasują do kontenera przepływu pracy.

Praktyczne DevOpse mogą pomóc zespołom szybciej reagować wraz z naciskiem na konkurencyjność, zastępując procesy ręczne podatne na błędy dzięki automatyzacji, co pozwala na ulepszone śledzenie i powtarzalne przepływy pracy. Organizacje mogą również bardziej wydajnie zarządzać środowiskami i zwiększać oszczędności kosztów dzięki połączeniu zasobów lokalnych i w chmurze oraz ściśle zintegrowanych narzędzi.

Podczas wdrażania przepływu pracy DevOps dla aplikacji platformy Docker zobaczysz, że technologie platformy Docker są obecne w prawie każdym etapie przepływu pracy, z poziomu pola deweloperskiego podczas pracy w pętli wewnętrznej (kod, Uruchom, Debuguj), faza Build-test-CI i, na koniec wdrażanie tych kontenerów w środowiskach przejściowych i produkcyjnych.

Poprawa praktyk dotyczących jakości pomaga identyfikować wady przed wczesnym cyklem rozwoju, co zmniejsza koszt ich rozwiązania. Dzięki dołączeniu środowiska i zależności w obrazie i przyjęciu informacji o wdrażaniu tego samego obrazu w wielu środowiskach podwyższasz dyscyplinę wyodrębniania konfiguracji specyficznych dla środowiska, co sprawia, że wdrożenia są bardziej niezawodne.

Bogate dane uzyskane za poorednictwem efektywnej Instrumentacji (monitorowanie i Diagnostyka) zapewniają wgląd w problemy z wydajnością i zachowanie użytkowników w celu zaplanowania przyszłych priorytetów i inwestycji.

DevOps powinna być uważana za podróż, a nie miejsce docelowe. Powinien być wdrażany przyrostowo za pośrednictwem odpowiednich projektów o określonym zakresie, z których można przedstawić sukces, uczyć się i rozwijać.

## <a name="benefits-of-devops-for-containerized-applications"></a>Zalety DevOps dla aplikacji kontenerowych

Poniżej przedstawiono niektóre z najważniejszych korzyści zapewnianych przez pełny przepływ pracy DevOps:

- Zapewniaj lepszą jakość oprogramowania, szybsze i bardziej zgodne.

- Ciągłe ulepszanie i wprowadzanie zmian w sposób ciągły i bardziej ekonomiczny.

- Zwiększ przejrzystość i współpracę między uczestnikami zaangażowanymi w dostarczanie i oprogramowanie operacyjne.

- Kontroluj koszty i wydajniej Wykorzystuj zasoby z obsługą administracyjną, jednocześnie minimalizując zagrożenia bezpieczeństwa.

- Usługa Plug and Play z wieloma istniejącymi inwestycjami DevOps, w tym inwestycje w funkcję Open Source.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[Następny](../Microsoft-platform-tools-containerized-apps/index.md)
