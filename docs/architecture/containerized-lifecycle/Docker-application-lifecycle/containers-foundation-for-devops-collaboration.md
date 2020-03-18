---
title: Kontenery jako podstawa współpracy w metodyce DevOps
description: Zrozumienie kluczowej roli kontenerów w celu usprawnienia devops.
ms.date: 02/15/2019
ms.openlocfilehash: 8258f4331212d92376d64fef318adcdff492f61f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73094497"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Kontenery jako podstawa współpracy w metodyce DevOps

Ze względu na sam charakter kontenerów i technologii Platformy Docker deweloperzy mogą łatwo udostępniać swoje oprogramowanie i zależności z operacjami IT i środowiskami produkcyjnymi, eliminując jednocześnie typową wymówkę "działa na mojej maszynie". Kontenery rozwiązują konflikty aplikacji między różnymi środowiskami. Pośrednio kontenery i platformy Docker zbliżają deweloperów i operacje IT do siebie, ułatwiając im efektywną współpracę. Przyjęcie przepływu pracy kontenera zapewnia wielu klientom ciągłość DevOps, którą szukali, ale wcześniej musieli zaimplementować za pomocą bardziej złożonej konfiguracji dla potoków wydania i kompilacji. Kontenery upraszczają kompilacji/testowania/wdrażania potoków w DevOps.

![Diagram przedstawiający własność cyklu życia aplikacji platformy Docker.](./media/containers-foundation-for-devops-collaboration/persona-workloads-docker-container-lifecycle.png)

**Rysunek 2-1.** Główne obciążenia na "persony" w cyklu życia dla konteneryzowanych aplikacji platformy Docker

Z kontenerów platformy Docker deweloperzy są właścicielami tego, co znajduje się w kontenerze (aplikacji i usługi i zależności do struktur i składników) i jak kontenery i usługi zachowują się razem jako aplikacja składa się z kolekcji usług. Współzależności wielu kontenerów są zdefiniowane w `docker-compose.yml` pliku lub co można nazwać *manifestem wdrażania.* Tymczasem zespoły operacyjne IT (it specjalistów i zarządzania) może skupić się na zarządzaniu środowiskami produkcyjnymi; infrastruktury; skalowalność; monitorowanie; i, ostatecznie, zapewnienie, że aplikacje są dostarczane prawidłowo dla użytkowników końcowych, bez konieczności poznania zawartości różnych kontenerów. Stąd nazwa "kontener", przypominając analogię do rzeczywistych kontenerów wysyłkowych. W związku z tym właściciele zawartości kontenera nie muszą zajmować się tym, w jaki sposób kontener zostanie wysłany, a firma spedycyjna przewozi kontener z miejsca jego pochodzenia do miejsca przeznaczenia, nie znając ani nie dbając o zawartość. W podobny sposób deweloperzy mogą tworzyć i posiadać zawartość w kontenerze platformy Docker bez konieczności zajmowania się mechanizmami "transport".

W filarze po lewej stronie rysunku 2-1 deweloperzy zapisują i uruchamiają kod lokalnie w kontenerach platformy Docker przy użyciu platformy Docker dla systemu Windows lub Mac. Definiują one środowisko operacyjne dla kodu przy użyciu pliku Dockerfile, który określa podstawowy system operacyjny do uruchomienia, a także kroki kompilacji do tworzenia kodu w obrazplatformie Docker. Deweloperzy definiują, jak jeden lub więcej obrazów będzie `docker-compose.yml` współdziałać przy użyciu wyżej wymienionego manifestu wdrażania plików. Po zakończeniu lokalnego rozwoju wypychają swój kod aplikacji oraz pliki konfiguracyjne platformy Docker do wybranego repozytorium kodu (czyli repozytorium Git).

DevOps filar definiuje kompilacji ciągłej integracji (CI) potoków przy użyciu pliku Dockerfile dostarczone w repozytorium kodu. System ci pobiera obrazy kontenera podstawowego z wybranego rejestru platformy Docker i tworzy niestandardowe obrazy platformy Docker dla aplikacji. Obrazy są następnie sprawdzane i wypychane do rejestru platformy Docker używanego do wdrożeń w wielu środowiskach.

W filarze po prawej stronie zespoły operacyjne zarządzają wdrożonymi aplikacjami i infrastrukturą w środowisku produkcyjnym, jednocześnie monitorując środowisko i aplikacje, dzięki czemu mogą przekazywać informacje zwrotne i szczegółowe informacje dla zespołu programistów na temat tego, jak aplikacja może być Poprawa. Aplikacje kontenerów są zazwyczaj uruchamiane w środowisku produkcyjnym przy użyciu koordynatorów kontenerów.

Oba zespoły współpracują za pośrednictwem platformy fundamentalnej (kontenery platformy Docker), która zapewnia oddzielenie problemów jako umowy, a jednocześnie znacznie poprawia współpracę obu zespołów w cyklu życia aplikacji. Deweloperzy są właścicielami zawartości kontenera, jego środowiska operacyjnego i współzależności kontenerów, podczas gdy zespoły operacyjne przyjmują zbudowane obrazy wraz z manifestem i uruchamiaje je w systemie aranżacji.

## <a name="challenges-in-application-life-cycle-when-using-docker"></a>Wyzwania w cyklu życia aplikacji podczas korzystania z platformy Docker.

Istnieje wiele powodów, które zwiększą liczbę konteneryzowanych aplikacji w nadchodzących latach, a jednym z tych powodów jest tworzenie aplikacji opartych na mikrousługach.

W ciągu ostatnich 15 lat korzystanie z usług sieci web było podstawą tysięcy aplikacji i prawdopodobnie po kilku latach znajdziemy taką samą sytuację z aplikacjami opartymi na mikrousługach uruchomionymi na kontenerach platformy Docker.

Warto również wspomnieć, że można również używać kontenerów Platformy Docker do zastosowań monolitycznych i nadal uzyskać większość korzyści z platformy Docker. Kontenery nie są przeznaczone tylko mikrousług.

Korzystanie z konteneryzacji platformy Docker i mikrousług powoduje nowe wyzwania w procesie rozwoju organizacji i w związku z tym trzeba solidną strategię, aby utrzymać wiele kontenerów i mikrousług uruchomionych w systemach produkcyjnych. Po pewnym czasie aplikacje dla przedsiębiorstw będą miały setki lub tysiące kontenerów/wystąpień działających w środowisku produkcyjnym.

Te wyzwania tworzą nowe wymagania podczas korzystania z narzędzi DevOps, więc będziesz musiał zdefiniować nowe procesy w działaniach DevOps i znaleźć odpowiedzi na tego typu pytania:

- Jakich narzędzi mogę używać do rozwoju, do CI/CD, zarządzania i operacji?

- Jak moja firma może zarządzać błędami w kontenerach podczas pracy w środowisku produkcyjnym?

- Jak możemy zmienić części naszego oprogramowania w produkcji przy minimalnych przestojach?

- Jak możemy skalować i jak możemy monitorować nasz system produkcji?

- Jak możemy uwzględnić testowanie i wdrażanie kontenerów w naszym potoku wydania?

- Jak możemy używać narzędzi/platform Open Source dla kontenerów na platformie Microsoft Azure?

Jeśli możesz odpowiedzieć na wszystkie te pytania, będziesz lepiej przygotowany do przenoszenia aplikacji (istniejących lub nowych aplikacji) do kontenerów platformy Docker.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Wprowadzenie do ogólnego przepływu pracy cyklu życia aplikacji dokowania typu end-to-end

Rysunek 2-2 przedstawia bardziej szczegółowy przepływ pracy dla cyklu życia aplikacji platformy Docker, koncentrując się w tym wystąpieniu na określonych działaniach i zasobach DevOps.

![Diagram przedstawiający ogólny cykl życia typu end-to-end aplikacji platformy Docker.](./media/containers-foundation-for-devops-collaboration/generic-end-to-enddpcker-app-life-cycle.png)

**Rysunek 2-2.** Wysokopoziomowy przepływ pracy dla cyklu życia aplikacji konteneryzowanej platformą Docker

Wszystko zaczyna się od dewelopera, który rozpoczyna pisanie kodu w przepływie pracy w pętli wewnętrznej. Etap pętli wewnętrznej jest, gdzie deweloperzy definiują wszystko, co dzieje się przed wypchnięciem kodu do repozytorium kodu (na przykład system kontroli źródła, takich jak Git). Po jego zatwierdzono repozytorium wyzwala ciągłą integrację (CI) i pozostałej części przepływu pracy.

Pętla wewnętrzna zasadniczo składa się z typowych kroków, takich jak "kod", "uruchom", "test" i "debugowanie", a także dodatkowych kroków potrzebnych tuż przed uruchomieniem aplikacji lokalnie. Jest to proces dewelopera, aby uruchomić i przetestować aplikację jako kontener platformy Docker. Przepływ pracy w pętli wewnętrznej zostaną wyjaśnione w sekcjach, które należy wykonać.

Krok wstecz, aby spojrzeć na przepływ pracy end-to-end, devops przepływu pracy jest czymś więcej niż technologii lub zestawu narzędzi: jest to sposób myślenia, który wymaga ewolucji kulturowej. To ludzie, procesy i odpowiednie narzędzia, aby przyspieszyć i przewidywalność cyklu życia aplikacji. Przedsiębiorstwa, które przyjmują konteneryzowany przepływ pracy zazwyczaj restrukturyzacji swoich organizacji do reprezentowania osób i procesów, które pasują do konteneryzowanego przepływu pracy.

Ćwiczenie devops może pomóc zespołom szybciej reagować razem na presję konkurencyjną, zastępując podatne na błędy procesy ręczne automatyzacją, co skutkuje lepszą identyfikowalnością i powtarzalnymi przepływami pracy. Organizacje mogą również wydajniej zarządzać środowiskami i osiągać oszczędności kosztów dzięki połączeniu zasobów lokalnych i w chmurze, a także ściśle zintegrowanym oprzyrządowaniu.

Podczas implementowania przepływu pracy DevOps dla aplikacji platformy Docker, zobaczysz, że technologie platformy Docker są obecne na prawie każdym etapie przepływu pracy, z pola rozwoju podczas pracy w pętli wewnętrznej (kod, uruchom, debugowania), fazy kompilacji test-CI i, na koniec wdrożenie tych kontenerów do środowisk przejściowych i produkcyjnych.

Poprawa jakości praktyk pomaga zidentyfikować wady na wczesnym etapie cyklu rozwoju, co zmniejsza koszty ich naprawy. Dołączając środowisko i zależności w obrazie i przyjmując filozofię wdrażania tego samego obrazu w wielu środowiskach, promujesz dyscyplinę wyodrębniania konfiguracji specyficznych dla środowiska, dzięki czemu wdrożenia są bardziej niezawodne.

Bogate dane uzyskane dzięki skutecznemu instrumentacji (monitorowaniu i diagnostyce) zapewniają wgląd w problemy z wydajnością i zachowanie użytkownika, aby kierować przyszłymi priorytetami i inwestycjami.

DevOps należy uznać za podróż, a nie miejsce docelowe. Powinien być wdrażany stopniowo za pomocą odpowiednio ookreślonym zakresem projektów, z których można wykazać sukces, uczyć się i ewoluować.

## <a name="benefits-of-devops-for-containerized-applications"></a>Korzyści z DevOps dla aplikacji konteneryzowanych

Oto niektóre z najważniejszych korzyści zapewnianych przez solidny przepływ pracy DevOps:

- Dostarczaj oprogramowanie lepszej jakości, szybciej i z lepszą zgodnością.

- Napędzaj ciągłe doskonalenie i regulacje wcześniej i bardziej ekonomicznie.

- Zwiększenie przejrzystości i współpracy między zainteresowanymi stronami zaangażowanymi w dostarczanie i obsługę oprogramowania.

- Kontroluj koszty i efektywniej korzystaj z aprowizowanego zasobu, minimalizując jednocześnie zagrożenia bezpieczeństwa.

- Podłącz i dobrze grać z wielu istniejących inwestycji DevOps, w tym inwestycje w open-source.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](../Microsoft-platform-tools-containerized-apps/index.md)
