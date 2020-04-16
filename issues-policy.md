---
ms.openlocfilehash: 33178637c4fcfb21e8190c3d2593f09326ea5995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73554849"
---
# <a name="github-issues-process-and-policy"></a>GitHub wydaje proces i zasady

Cele tego procesu to:

1. Upewnij się, że błędy lub pominięcia w naszych docs nie blokują sukcesu klienta.
1. Odpowiadaj na opinie i wątpliwości klientów.
1. Ciągłe doskonalenie obsługi klienta.
1. Dowiedz się więcej o doświadczeniach klientów dzięki otwartej pracy dialogowego na temat wyzwań i rozwiązań.

Proces wykorzystuje dwa etapy, aby zapewnić responsywność podczas ustalania priorytetów pracy. Początkowy etap diagnozuje i klasyfikowa problem. Drugi etap rozwiązuje problem. Gdy problem jest zarówno łatwy, jak i pilny, można połączyć dwa etapy.

Proces obejmuje zadania z przydziałami czasu o ustalonym czasie:

- Każdy członek zespołu spędza do 1/2 godziny każdego dnia [roboczego, klasyfikując przychodzące problemy,](#diagnosis-phase)w tym wstępne odpowiedzi. Dzięki temu reagujemy na nowe problemy.
- Każdy członek zespołu spędza do 1/2 dnia tygodniowo [na aktualizowaniu dokumentów](#resolution-phase) w celu rozwiązania problemów z githubem generowanym przez klientów.

## <a name="diagnosis-phase"></a>Faza diagnostyczna

Każdy członek zespołu spędza do 30 minut dziennie na kategoryzowaniu nowych problemów. Odpowiadamy na następujące pytania:

- Czy problem jest problemem dokumentów lub produktu?
- Czy nie jest to problem, ale pytanie lepiej nadaje się na forum lub stronie wsparcia?
- Jaki jest problem priorytetowy?
- Jaki obszar zarządza tym problemem?

Jeśli nie można odpowiedzieć na te pytania w wstępnym badaniu, zadajemy pytania wyjaśniające w komentarzach.

Istnieją rodzaje problemów, które są zamknięte podczas fazy diagnostyki i klasyfikacji:

- **kudos**: Wyrażamy podziękowania i zamykamy sprawę.
- **problem z produktem**: Problemy związane z produktem, a nie z jego dokumentacją, są zamykane. Możemy również podjąć dodatkowe działania, jak opisano poniżej.
- **Naruszenia CoC**: Te problemy są zamykane i zgłaszane, jeśli [naruszenie CoC](https://dotnetfoundation.org/code-of-conduct) zasługuje na zgłoszenie i zablokowanie.
- **duplikaty:** Duplikaty są zamykane komentarzem odwołującym się do istniejącego problemu.
- **doc-ok**: Klient jest niepoprawny, a doc jest poprawny.
- **forum**: Problemy, które są wsparcie lub żądania forum są kierowane do przepełnienia stosu lub innych witryn pomocy technicznej i zamknięte.

### <a name="actions-on-product-issues"></a>Działania w zakresie problemów z produktem

W zależności od charakteru problemu z produktem możemy zdecydować się na:

- Przenieś problem do odpowiedniego repozytorium produktów.
- Zamknij problem jako duplikat istniejących żądań produktu.
- Zamknij problem z zaleceniem otwarcia repozytorium produktów.

Ocena prawidłowego postępowania jest subiektywna. Członkowie zespołu używają swojej oceny na prawidłowe działanie.

### <a name="actions-on-content-issues"></a>Działania dotyczące problemów z zawartością

W przypadku innych problemów zespół:

- Przypisuje priorytet
- Przypisuje punkt kontrolny, zwykle "Zaległości"
- Ocenia, czy problem jest dobrym problemem "do zgarnięcia", czy [projektami dla współautorów społeczności .NET](https://github.com/dotnet/docs/projects/35)

Poziomy priorytetów są oparte na poniższych wytycznych, ale są subiektywne. Kamienie milowe są również subiektywne i są oparte na innych priorytetach, takich jak aktualne harmonogramy wydań produktów i nadchodzące premiery.

- **P0**: Pominięcie lub błąd dokumentów uniemożliwia klientom pomyślne w typowym scenariuszu.
  - **Problemy P0** są rozwiązywane w ciągu najbliższych trzech tygodni, co ma pierwszeństwo przed wcześniej zaplanowaną pracą.
- **P1**: Pominięcie lub błąd dokumentów sprawia, że typowy scenariusz jest znacznie trudniejszy lub blokuje inne dobrze znane scenariusze.
  - **Problemy P1** są planowane w odpowiednim czasie. Często problemy P1 są planowane na nadchodzący kamień milowy.
- **P2**: Problemy, które powodują drobne niedogodności lub wpływają na niski poziom wyświetlania strony.
  - **Problemy P2** są zazwyczaj rozwiązywane, gdy artykuł jest aktualizowany ze względów o wyższym priorytecie.
- **P3**: Problemy, które są żądania dla scenariuszy przypadków krawędzi.
  - **Problemy P3** są umieszczane w zaległości i są uważane za aktualizację, gdy artykuły są aktualizowane ze względów o wyższym priorytecie.

Członkowie zespołu spędzają ograniczoną ilość czasu na diagnozę i klasyfikowanie, aby mogli poczynić postępy w zaplanowanych zadaniach. Każdy członek zespołu spędza co najwyżej 30 minut dziennie w diagnostyce i klasyfikacji.

Etykieta **up-for-grabs** jest stosowana, gdy problem jest dobrym kandydatem dla członka społeczności (ewentualnie autora) do przesłania poprawki. Członek zespołu, który stosuje etykietę **up-for-grabs,** pomoże lub znajdzie kogoś, kto pomoże członkom społeczności w pracy nad procesem tworzenia środowiska. Kwestie, które są "do zgarnięcia" są często dodawane do [projektów wkładu wspólnoty](https://github.com/dotnet/docs/projects/35)

> UWAGA: Dopiero niedawno przyjęliśmy poprzednią konwencję. Osoba, która dodała etykietę, może skierować Cię do innego członka zespołu, który pomoże.

## <a name="resolution-phase"></a>Faza restrukturyzacji i uporządkowanej likwidacj

Problemy generowane przez klienta są ważone w ramach planowania zaplanowanych zadań. Każdy członek zespołu przydziela 4 godziny tygodniowo na rozwiązywanie problemów klientów o najwyższym priorytecie.

Rozwiązywanie problemów wynika z poziomu priorytetu ustawionego podczas diagnozy. Przychodzące problemy klientów są traktowane priorytetowo z innymi zaplanowanymi pracami o podobnym priorytecie

- **P0**: Tak szybko, jak to jest uzasadnione, w ciągu najbliższych trzech tygodni.
- **P1**: Zaplanowane z innymi planowanymi pracami P1. Zwykle oznacza to, że w ciągu najbliższych trzech miesięcy.
- **P2**: Zaplanowane z innymi planowanymi pracami P2. Problemy P2 są regularnie planowane w oparciu o obszar i widoczność. Częściej problemy P2 będą rozwiązywane po zaktualizowaniu artykułu.
- **P3**: Brak gwarancji w dniu ustalenia. Po zaktualizowaniu artykułu, możemy zbadać zaległości dla innych problemów w tym samym artykule.

Problemy mogą być przeszywnienia na podstawie nowych opinii i danych dotyczących widoczności artykułu.
