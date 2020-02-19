---
title: Wzorce wglądu
description: Wzorce zauważalne dla aplikacji natywnych w chmurze
ms.date: 02/05/2020
ms.openlocfilehash: a821235835b4553760b19887d500a29ca75e133e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448533"
---
# <a name="observability-patterns"></a>Wzorce wglądu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Podobnie jak wzorce zostały opracowane w celu pomocy w układzie kodu w aplikacjach, istnieją wzorce dla aplikacji operacyjnych w niezawodny sposób. Zakryto trzy przydatne wzorce w utrzymywaniu aplikacji: **Rejestrowanie**, **monitorowanie**i **alerty**.

## <a name="when-to-use-logging"></a>Kiedy należy używać rejestrowania

Bez względu na to, jak dokładnie jesteśmy, aplikacje niemal zawsze zachowują się w nieoczekiwany sposób w środowisku produkcyjnym. Gdy użytkownicy zgłaszają problemy z aplikacją, niezwykle przydatna jest możliwość sprawdzenia, co się dzieje z aplikacją, gdy wystąpił problem. Jednym z najpopularniejszych i prawdziwych sposobów przechwytywania informacji na temat działania aplikacji, gdy jest uruchomiona, jest zapisanie przez aplikację co robi. Ten proces jest nazywany rejestrowaniem. Wszelkie błędy czasu lub problemy występujące w środowisku produkcyjnym należy wykonać w celu odtworzenia warunków, w których wystąpiły awarie, w środowiskach nieprodukcyjnych. Jeśli dobre miejsce do zarejestrowania zawiera Przewodnik dla deweloperów, w celu duplikowania problemów w środowisku, które mogą być testowane i eksperymentować.

### <a name="challenges-when-logging-with-cloud-native-applications"></a>Wyzwania podczas rejestrowania w aplikacjach natywnych w chmurze

W tradycyjnych aplikacjach pliki dziennika są zwykle przechowywane na komputerze lokalnym. W rzeczywistości w systemach operacyjnych działających w systemie UNIX istnieje struktura folderów zdefiniowana do przechowywania dzienników, zwykle w obszarze `/var/log`.

![logowanie do pliku w aplikacji monolitycznej.](./media/single-monolith-logging.png)
**rysunek 7-1**. Logowanie do pliku w aplikacji monolitycznej.

Użyteczność rejestrowania w pliku prostym na pojedynczym komputerze jest znacznie ograniczona w środowisku chmury. Dzienniki wyprodukowania aplikacji mogą nie mieć dostępu do dysku lokalnego lub dysk lokalny może być wysoce przejściowy, ponieważ kontenery są rozwiązane na maszynach fizycznych. Nawet proste skalowanie aplikacji monolitycznych w wielu węzłach może być trudne do zlokalizowania odpowiedniego pliku dziennika opartego na plikach.

![logowanie do plików w skalowanej aplikacji monolitycznej.](./media/multiple-node-monolith-logging.png)
**rysunek 7-2**. Rejestrowanie w plikach w skalowanej aplikacji monolitycznej.

Aplikacje natywne w chmurze opracowane przy użyciu architektury mikrousług również stanowią pewne wyzwania dotyczące rejestratorów opartych na plikach. Żądania użytkowników mogą teraz obejmować wiele usług, które są uruchamiane na różnych komputerach i mogą zawierać funkcje bezserwerowe bez dostępu do lokalnego systemu plików. Bardzo trudne jest skorelowanie dzienników od użytkownika lub sesji przez te wiele usług i maszyn.

![rejestrowanie w plikach lokalnych w aplikacji mikrousług.](./media/local-log-file-per-service.png)
**rysunek 7-3**. Rejestrowanie w plikach lokalnych w aplikacji mikrousług.

Na koniec liczba użytkowników w niektórych aplikacjach natywnych w chmurze jest wysoka. Załóżmy, że każdy użytkownik generuje setki wierszy komunikatów dziennika podczas logowania do aplikacji. W izolacji, którą można zarządzać, ale należy pomnożyć, że ponad 100 000 użytkowników i ilość dzienników są wystarczająco duże, że specjalne narzędzia są wymagane do obsługi efektywnego korzystania z dzienników.

### <a name="logging-in-cloud-native-applications"></a>Logowanie w aplikacjach natywnych w chmurze

Każdy język programowania zawiera narzędzia, które pozwalają na zapisywanie dzienników, a zazwyczaj obciążenie związane z zapisywaniem tych dzienników jest niskie. Wiele bibliotek rejestrowania zapewnia rejestrowanie różnych rodzajów krytyczne, które mogą być dostrojone w czasie wykonywania. Na przykład [Biblioteka Serilog](https://serilog.net/) jest popularną biblioteką rejestrowania strukturalnego dla platformy .NET, która zapewnia następujące poziomy rejestrowania:

* Pełny
* Debugowanie
* Informacje
* Ostrzeżenie
* Błąd
* Krytyczn

Te różne poziomy dziennika zapewniają stopień szczegółowości rejestrowania. Gdy aplikacja działa prawidłowo w środowisku produkcyjnym, może być skonfigurowana do rejestrowania tylko ważnych komunikatów. Gdy aplikacja jest błędna, poziom dziennika można zwiększyć, aby zebrać więcej szczegółowych dzienników. Równoważy to wydajność w porównaniu z prostotą debugowania.

Wysoka wydajność narzędzi rejestrowania i tunability szczegółowości powinny zachęcić deweloperów do częstego rejestrowania. Wiele preferuje wzorzec rejestrowania wejścia i wyjścia każdej z tych metod. Takie podejście może być zdrowe, jak zbyt obszerne, ale rzadko nie jest to konieczne, aby deweloperzy chcieli mniej logować się. W rzeczywistości nie zdarza się przeprowadzać wdrożeń wyłącznie w celu dodania rejestrowania do problematycznej metody. Błąd po stronie zbyt dużej liczby dzienników i nie jest on zbyt mały. Niektóre narzędzia mogą służyć do automatycznego udostępniania tego rodzaju rejestrowania.

Ze względu na wyzwania związane z korzystaniem z dzienników opartych na plikach w aplikacjach natywnych w chmurze, preferowane są scentralizowane dzienniki. Dzienniki są zbierane przez aplikacje i wysyłane do centralnej aplikacji do rejestrowania, która indeksuje i przechowuje dzienniki. Ta klasa systemu może codziennie przyjmować dziesiątki gigabajtów dzienników.

Podczas tworzenia rejestrowania obejmującego wiele usług warto również stosować standardowe rozwiązania. Na przykład generowanie [identyfikatora korelacji](https://blog.rapid7.com/2016/12/23/the-value-of-correlation-ids/) na początku interakcji o długim czasie, a następnie rejestrowanie go w każdym komunikacie związanym z tą interakcją ułatwia wyszukiwanie wszystkich powiązanych komunikatów. Jeden z nich musi znaleźć tylko jeden komunikat i wyodrębnić identyfikator korelacji, aby znaleźć wszystkie powiązane komunikaty. Innym przykładem jest upewnienie się, że format dziennika jest taki sam dla każdej usługi, niezależnie od używanej przez niego biblioteki języka lub rejestrowania. Ta Standaryzacja ułatwia znacznie łatwiejsze odczytywanie dzienników. Rysunek 7-4 pokazuje, jak architektura mikrousług może korzystać z scentralizowanego rejestrowania w ramach przepływu pracy.

Dzienniki ![z różnych źródeł są pozyskiwane w scentralizowanym magazynie dzienników.](./media/centralized-logging.png)
**rysunek 7-4**. Dzienniki z różnych źródeł są pozyskiwane w scentralizowanym magazynie dzienników.

## <a name="challenges-with-detecting-and-responding-to-potential-app-health-issues"></a>Wyzwania dotyczące wykrywania potencjalnych problemów z kondycją aplikacji i reagowania na nie

Niektóre aplikacje nie są krytyczne. Może być używany tylko wewnętrznie i w przypadku wystąpienia problemu użytkownik może skontaktować się z zespołem odpowiedzialnym i można ponownie uruchomić aplikację. Jednak klienci często mają wyższe oczekiwania dla aplikacji, których używają. Należy wiedzieć, kiedy występują problemy z aplikacją *przed* użytkownikami lub przed powiadomieniem użytkownika. W przeciwnym razie pierwszy wiesz o problemie może być widoczny, gdy zauważysz, że Angry natłokiem ogłoszeń dotyczących mediów społecznościowych zakłócają swoją aplikację, a nawet organizację.

Niektóre scenariusze, które należy wziąć pod uwagę, obejmują:

- Jedna usługa w aplikacji utrzymuje awarie i ponowne uruchomienie, co powoduje sporadyczne spowolnienie odpowiedzi.
- W niektórych porach dnia czas odpowiedzi aplikacji jest powolny.
- Po zakończeniu ostatniego wdrożenia obciążenie bazy danych jest trzykrotnie.

Wdrożone prawidłowo, monitorowanie może informować o warunkach, które będą prowadzić do problemów, dzięki czemu można rozwiązać podstawowe warunki, zanim spowodują one znaczący wpływ na użytkowników.

### <a name="monitoring-cloud-native-apps"></a>Monitorowanie aplikacji natywnych w chmurze

Niektóre Scentralizowane systemy rejestrowania zajmują dodatkową rolę zbierania danych telemetrycznych poza czystymi dziennikami. Mogą zbierać metryki, takie jak czas uruchamiania kwerendy bazy danych, średni czas odpowiedzi z serwera sieci Web, a nawet średnie obciążenie procesora CPU i wykorzystanie pamięci zgłoszone przez system operacyjny. W połączeniu z dziennikami te systemy mogą zapewnić całościowy wgląd w kondycję węzłów w systemie i aplikacji jako całości.

Możliwości zbierania metryk narzędzi do monitorowania mogą być również wprowadzane ręcznie z poziomu aplikacji. Przepływy biznesowe, które mają szczególne znaczenie, takie jak nowi użytkownicy, którzy tworzą rejestrację lub zamówienia są umieszczane, mogą być instrumentami w taki sposób, że zwiększają one licznik w centralnym systemie monitorowania. Powoduje to odblokowanie narzędzi monitorowania w celu nie tylko monitorowania kondycji aplikacji, ale jego kondycji.

Zapytania można budować w narzędziach agregacji dzienników, aby wyszukać pewne statystyki lub wzorce, które następnie można wyświetlić w formie graficznej na niestandardowych pulpitach nawigacyjnych. Często zespoły będą inwestować w duże, zainstalowane na ścianie ekrany, które obracają dane statystyczne związane z aplikacją. W ten sposób można łatwo zobaczyć problemy w miarę ich występowania.

Natywne narzędzia do monitorowania w chmurze zapewniają dane telemetryczne w czasie rzeczywistym i wgląd w aplikacje, niezależnie od tego, czy są to jednoprocesowe aplikacje monolityczne czy rozproszone architektury mikrousług. Obejmują one narzędzia umożliwiające zbieranie danych z aplikacji, a także narzędzia do wykonywania zapytań i wyświetlania informacji o kondycji aplikacji.

## <a name="challenges-with-reacting-to-critical-problems-in-cloud-native-apps"></a>Wyzwania dotyczące rozwiązywania problemów krytycznych w aplikacjach natywnych w chmurze

Jeśli musisz reagować na problemy z aplikacją, potrzebujesz pewnego sposobu, aby ostrzec właściwy personel. Jest to trzeci wzorzec przestrzegania natywnych aplikacji w chmurze i zależy od rejestrowania i monitorowania. Aplikacja musi mieć zarejestrowanie, aby umożliwić zdiagnozowanie problemów, a w niektórych przypadkach, aby uzyskać dostęp do narzędzi do monitorowania. Wymaga monitorowania do agregowania metryk aplikacji i danych dotyczących kondycji w jednym miejscu. Po jego nawiązaniu można utworzyć reguły, które będą wyzwalać alerty, gdy pewne metryki wykraczają poza akceptowalne poziomy.

Ogólnie rzecz biorąc, alerty są przyłączone do monitorowania w taki sposób, że określone warunki wyzwalają odpowiednie alerty do powiadamiania członków zespołu o nagłych problemach. Niektóre scenariusze, które mogą wymagać alertów, obejmują:

- Jedna z usług aplikacji nie odpowiada po 1 minucie przestoju.
- Aplikacja zwraca odpowiedzi HTTP zakończonych niepowodzeniem do ponad 1% żądań.
- Średni czas odpowiedzi aplikacji dla kluczowych punktów końcowych przekracza 2000 MS.

### <a name="alerts-in-cloud-native-apps"></a>Alerty w aplikacjach natywnych w chmurze

Można nawiązać zapytania względem narzędzi monitorowania, aby wyszukać znane warunki niepowodzeń. Na przykład zapytania mogą przeszukiwać dzienniki przychodzące w poszukiwaniu wskazań kodu stanu HTTP 500, co wskazuje na problem na serwerze sieci Web. Po wykryciu jednego z tych elementów, wiadomość e-mail lub SMS może zostać wysłana do właściciela usługi pochodzącej, która może zacząć zbadać.

Zwykle jednak jeden błąd 500 jest zbyt mały, aby ustalić, czy wystąpił problem. Może to oznaczać, że użytkownik niepoprawnie wpisano hasło lub wprowadził nieprawidłowe dane. Zapytania alertów można przystąpić do uruchamiania tylko wtedy, gdy zostanie wykryta większa niż średnia liczba błędów 500.

Jednym z najbardziej szkodliwych wzorców alertów jest uruchomienie zbyt wielu alertów w celu zbadania ich przez człowieka. Właściciele usług będą szybko stać się Desensitized na błędy, które zostały wcześniej zbadane i okazały się niegroźne. Następnie, gdy wystąpią prawdziwe błędy, zostaną utracone w hałasie setek fałszywych wartości dodatnich. Parable [Boy, kto Cried Wolf](https://en.wikipedia.org/wiki/The_Boy_Who_Cried_Wolf) jest często powiadamiany o elementach podrzędnych, aby ostrzec o tym bardzo niebezpieczeństwie. Ważne jest, aby upewnić się, że alerty, które są uruchamiane, są wskaźnikiem rzeczywistego problemu.

>[!div class="step-by-step"]
>[Poprzednie](monitoring-health.md)
>[dalej](logging-with-elastic-stack.md)
