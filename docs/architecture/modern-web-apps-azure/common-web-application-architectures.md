---
title: Typowe architektury aplikacji internetowych
description: Architekt nowoczesne aplikacje internetowe z ASP.NET Core i Azure | Poznaj typowe architektury aplikacji sieci Web
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 7ec0d9cece40ba8a99e8ab5e028f7ac491ed6f4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77450189"
---
# <a name="common-web-application-architectures"></a>Typowe architektury aplikacji internetowych

> "Jeśli uważasz, że dobra architektura jest droga, spróbuj złej architektury."  
> _- Brian Foote i Joseph Yoder_

Większość tradycyjnych aplikacji .NET są wdrażane jako pojedyncze jednostki odpowiadające plikowi wykonywalnemu lub pojedynczej aplikacji sieci web działającej w jednej domenie aplikacji usług IIS. Jest to najprostszy model wdrażania i bardzo dobrze obsługuje wiele wewnętrznych i mniejszych aplikacji publicznych. Jednak nawet biorąc pod uwagę tę pojedynczą jednostkę wdrożenia, większość nietrywialnych aplikacji biznesowych korzysta z pewnego logicznego rozdzielenia na kilka warstw.

## <a name="what-is-a-monolithic-application"></a>Co to jest aplikacja monolityczna?

Monolityczne aplikacji jest taki, który jest całkowicie niezależne, pod względem jego zachowania. Może wchodzić w interakcje z innymi usługami lub magazynami danych w trakcie wykonywania swoich operacji, ale rdzeń jego zachowania działa w ramach własnego procesu, a cała aplikacja jest zazwyczaj wdrażana jako pojedyncza jednostka. Jeśli taka aplikacja musi skalować poziomo, zazwyczaj cała aplikacja jest duplikowana na wielu serwerach lub maszynach wirtualnych.

## <a name="all-in-one-applications"></a>Aplikacje all-in-one

Najmniejsza możliwa liczba projektów dla architektury aplikacji jest jeden. W tej architekturze cała logika aplikacji jest zawarta w jednym projekcie, skompilowana do pojedynczego zestawu i wdrożona jako pojedyncza jednostka.

Nowy projekt ASP.NET Core, czy utworzony w programie Visual Studio lub z wiersza polecenia, rozpoczyna się jako prosty monolit "all-in-one". Zawiera wszystkie zachowania aplikacji, w tym logiki prezentacji, biznesu i dostępu do danych. Rysunek 5-1 przedstawia strukturę plików aplikacji z jednym projektem.

![Pojedyncza aplikacja ASP.NET projektu Core](./media/image5-1.png)

**Rysunek 5-1.** Pojedynczy projekt ASP.NET aplikacji Core.

W scenariuszu jednego projektu separacji problemów osiąga się za pomocą folderów. Domyślny szablon zawiera oddzielne foldery dla obowiązków wzorca MVC modeli, widoków i kontrolerów, a także dodatkowe foldery dla danych i usług. W tym układzie szczegóły prezentacji powinny być ograniczone w jak największym stopniu do folderu Widoki, a szczegóły implementacji dostępu do danych powinny być ograniczone do klas przechowywanych w folderze Data. Logika biznesowa powinna znajdować się w usługach i klasach w folderze Modele.

Chociaż proste, jednoprojektowe rozwiązanie monolityczne ma pewne wady. Wraz ze wzrostem rozmiaru i złożoności projektu liczba plików i folderów będzie nadal rosnąć. Interfejs użytkownika (UI) dotyczy (modele, widoki, kontrolery) mieszkają w wielu folderach, które nie są zgrupowane alfabetycznie. Ten problem tylko pogarsza się, gdy dodatkowe konstrukcje na poziomie interfejsu i informacji, takich jak filtry lub ModelBinders, są dodawane w ich własnych folderach. Logika biznesowa jest rozproszona między modelami i usługami folderów i nie ma jasnego wskazania, w których klasach, w których folderach powinny zależeć od innych. Ten brak organizacji na poziomie projektu często prowadzi do [kodu spaghetti](https://deviq.com/spaghetti-code/).

Aby rozwiązać te problemy, aplikacje często ewoluują w rozwiązania wieloprojektowe, w których każdy projekt jest uważany za znajduje się w określonej _warstwie_ aplikacji.

## <a name="what-are-layers"></a>Co to są warstwy logiczne?

W miarę jak aplikacje stają się coraz bardziej złożone, jednym ze sposobów zarządzania tą złożonością jest rozbicie aplikacji zgodnie z jej obowiązkami lub obawami. Wynika to z zasady separacji problemów i może pomóc utrzymać rosnącą bazę kodu zorganizowane, dzięki czemu deweloperzy mogą łatwo znaleźć, gdzie niektóre funkcje są implementowane. Architektura warstwowa oferuje jednak wiele zalet nie tylko organizacji kodu.

Organizując kod w warstwy, wspólne funkcje niskiego poziomu mogą być ponownie używane w całej aplikacji. To ponowne użycie jest korzystne, ponieważ oznacza mniej kodu musi być napisane i ponieważ może umożliwić aplikacji do standaryzacji na jednej implementacji, zgodnie z zasadą [nie powtarzaj siebie (DRY).](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)

Dzięki architekturze warstwowej aplikacje mogą wymuszać ograniczenia dotyczące warstw, które mogą komunikować się z innymi warstwami. Pomaga to osiągnąć hermetyzację. Po zmianie lub wymianie warstwy powinny mieć wpływ tylko te warstwy, które z nią współpracują. Ograniczając warstwy zależne od innych warstw, wpływ zmian można złagodzić, aby pojedyncza zmiana nie miała wpływu na całą aplikację.

Warstwy (i hermetyzacja) znacznie ułatwiają zastępowanie funkcji w aplikacji. Na przykład aplikacja może początkowo używać własnej bazy danych programu SQL Server do trwałości, ale później może wybrać użycie strategii trwałości opartej na chmurze lub jednej za interfejsem API sieci Web. Jeśli aplikacja poprawnie hermetyzowane jego implementacji trwałości w warstwie logicznej, że sql Server określonej warstwy może zostać zastąpiony przez nowy implementacji tego samego interfejsu publicznego.

Oprócz potencjału wymiany implementacji w odpowiedzi na przyszłe zmiany wymagań, warstwy aplikacji mogą również ułatwić wymianę implementacji do celów testowych. Zamiast pisać testy, które działają przeciwko warstwy rzeczywistych danych lub warstwy interfejsu interfejsu aplikacji, warstwy te mogą być zastępowane w czasie testu z fałszywych implementacji, które zapewniają znane odpowiedzi na żądania. To zazwyczaj sprawia, że testy znacznie łatwiejsze do zapisu i znacznie szybciej do uruchomienia w porównaniu do uruchamiania testów przeciwko rzeczywistej infrastruktury aplikacji.

Logiczne nakładanie warstw jest powszechną techniką poprawy organizacji kodu w aplikacjach dla przedsiębiorstw i istnieje kilka sposobów, w których kod może być zorganizowany w warstwy.

> [!NOTE]
 > _Warstwy_ reprezentują logiczne rozdzielenie w aplikacji. W przypadku, gdy logika aplikacji jest fizycznie dystrybuowana do oddzielnych serwerów lub procesów, te oddzielne obiekty docelowe wdrażania fizycznego są określane jako _warstwy_. Jest to możliwe i dość powszechne, aby mieć n-warstwowej aplikacji, która jest wdrażana w jednej warstwie.

## <a name="traditional-n-layer-architecture-applications"></a>Tradycyjne aplikacje architektury "N-Layer"

Najczęstsza organizacja logiki aplikacji do warstw jest pokazana na rysunku 5-2.

![Typowe warstwy aplikacji](./media/image5-2.png)

**Rysunek 5-2.** Typowe warstwy aplikacji.

Warstwy te są często skracane jako ui, BLL (Business Logic Layer) i DAL (Data Access Layer). Przy użyciu tej architektury użytkownicy żądań za pośrednictwem warstwy interfejsu użytkownika, który współdziała tylko z bll. BLL, z kolei można wywołać dal dla żądań dostępu do danych. Warstwa interfejsu użytkownika nie należy wysyłać żadnych żądań do warstwy DAL bezpośrednio, ani nie powinny współdziałać z trwałości bezpośrednio za pomocą innych środków. Podobnie bll powinny współdziałać tylko z trwałości, przechodząc przez dal. W ten sposób każda warstwa ma swoją własną, dobrze znaną odpowiedzialność.

Jedną z wad tego tradycyjnego podejścia warstw jest, że zależności w czasie kompilacji uruchomić od góry do dołu. Oznacza to, że warstwa interfejsu i ui zależy od biblioteki BLL, która zależy od warstwy DAL. Oznacza to, że logika logiki logiki, która zwykle posiada najważniejszą logikę w aplikacji, jest zależna od szczegółów implementacji dostępu do danych (i często od istnienia bazy danych). Testowanie logiki biznesowej w takiej architekturze jest często trudne, wymagające testowej bazy danych. Zasada odwrócenia zależności może służyć do rozwiązania tego problemu, jak widać w następnej sekcji.

Rysunek 5-3 przedstawia przykładowe rozwiązanie, podziale aplikacji na trzy projekty według odpowiedzialności (lub warstwy).

![Prosta monolityczna aplikacja z trzema projektami](./media/image5-3.png)

**Rysunek 5-3.** Prosta monolityczna aplikacja z trzema projektami.

Mimo że ta aplikacja używa kilku projektów do celów organizacyjnych, nadal jest wdrażana jako pojedyncza jednostka, a jej klienci będą wchodzić z nią w interakcje jako pojedyncza aplikacja sieci web. Pozwala to na bardzo prosty proces wdrażania. Rysunek 5-4 pokazuje, jak taka aplikacja może być hostowana przy użyciu platformy Azure.

![Proste wdrażanie aplikacji Azure Web App](./media/image5-4.png)

**Rysunek 5-4.** Proste wdrażanie aplikacji Azure Web App

Wraz ze wzrostem potrzeb aplikacji mogą być wymagane bardziej złożone i niezawodne rozwiązania wdrożeniowe. Rysunek 5-5 przedstawia przykład bardziej złożonego planu wdrożenia, który obsługuje dodatkowe możliwości.

![Wdrażanie aplikacji sieci web w usłudze Azure App Service](./media/image5-5.png)

**Rysunek 5-5.** Wdrażanie aplikacji sieci web w usłudze Azure App Service

Wewnętrznie organizacja tego projektu w wielu projektach opartych na odpowiedzialności poprawia łatwość konserwacji aplikacji.

To urządzenie można skalować w górę lub na zewnątrz, aby korzystać ze skalowalności opartej na nośniku w chmurze. Skalowanie w górę oznacza dodanie dodatkowego procesora CPU, pamięci, miejsca na dysku lub innych zasobów do serwerów obsługujących aplikację. Skalowanie w sposób skalowalny oznacza dodawanie dodatkowych wystąpień takich serwerów, niezależnie od tego, czy są to serwery fizyczne, maszyny wirtualne czy kontenery. Gdy aplikacja jest hostowana w wielu wystąpieniach, moduł równoważenia obciążenia jest używany do przypisywania żądań do poszczególnych wystąpień aplikacji.

Najprostszym podejściem do skalowania aplikacji sieci web na platformie Azure jest ręczne konfigurowanie skalowania w planie usługi aplikacji aplikacji. Rysunek 5-6 przedstawia odpowiedni ekran pulpitu nawigacyjnego platformy Azure, aby skonfigurować liczbę wystąpień obsługujących aplikację.

![Skalowanie planu usługi aplikacji na platformie Azure](./media/image5-6.png)

**Rysunek 5-6.** Skalowanie planu usługi aplikacji na platformie Azure.

## <a name="clean-architecture"></a>Czysta architektura

Aplikacje, które są zgodne z zasadą inwersji zależności, a także zasadami projektowania opartego na domenie (DDD), mają tendencję do osiągnięcia podobnej architektury. Ta architektura przeszła przez wiele nazw na przestrzeni lat. Jednym z pierwszych nazw była architektura sześciokątna, a następnie porty i karty. Niedawno, to był cytowany jako [Architektura cebuli](https://jeffreypalermo.com/blog/the-onion-architecture-part-1/) lub [Czystej Architektury](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). Ta ostatnia nazwa, Clean Architecture, jest używana jako nazwa tej architektury w tym e-booku.

Aplikacja referencyjna eShopOnWeb używa metody Czystej architektury w organizowaniu kodu w projekty. Możesz znaleźć szablon rozwiązania, którego można użyć jako punktu wyjścia dla własnego ASP.NET Core w repozytorium [gajów gaithuba ardalis/cleanarchitecture.](https://github.com/ardalis/cleanarchitecture)

Czysta architektura umieszcza logikę biznesową i model aplikacji w centrum aplikacji. Zamiast logiki biznesowej zależy od dostępu do danych lub innych problemów z infrastrukturą, ta zależność jest odwrócona: szczegóły infrastruktury i implementacji zależą od rdzenia aplikacji. Osiąga się to poprzez zdefiniowanie abstrakcji lub interfejsów w rdzeniu aplikacji, które są następnie implementowane przez typy zdefiniowane w warstwie Infrastruktura. Powszechnym sposobem wizualizacji tej architektury jest użycie serii koncentrycznych okręgów, podobnych do cebuli. Rysunek 5-7 przedstawia przykład tego stylu reprezentacji architektonicznej.

![Czysta architektura; widok cebuli](./media/image5-7.png)

**Rysunek 5-7.** Czysta architektura; widok cebuli

Na tym diagramie zależności przepływu w kierunku najgłębszego okręgu. Rdzeń aplikacji bierze swoją nazwę od swojej pozycji w rdzeniu tego diagramu. I widać na diagramie, że rdzeń aplikacji nie ma zależności od innych warstw aplikacji. Jednostki i interfejsy aplikacji znajdują się w samym centrum. Na zewnątrz, ale nadal w rdzeniu aplikacji, są usługi domeny, które zazwyczaj implementują interfejsy zdefiniowane w kręgu wewnętrznym. Poza rdzeniem aplikacji zarówno warstwy interfejsu i infrastruktury zależą od rdzenia aplikacji, ale nie od siebie (koniecznie).

Rysunek 5-8 przedstawia bardziej tradycyjny diagram warstwy poziomej, który lepiej odzwierciedla zależność między unią a innymi warstwami.

![Czysta architektura; widok warstwy poziomej](./media/image5-8.png)

**Rysunek 5-8.** Czysta architektura; widok warstwy poziomej

Należy zauważyć, że strzałki bryłowe reprezentują zależności czasu kompilacji, podczas gdy strzałka przerywana reprezentuje zależność tylko w czasie wykonywania. Z czystej architektury warstwy interfejsu użytkownika współpracuje z interfejsów zdefiniowanych w rdzeniu aplikacji w czasie kompilacji i najlepiej nie powinien wiedzieć o typy implementacji zdefiniowane w warstwie infrastruktury. Jednak w czasie wykonywania te typy implementacji są wymagane do wykonania aplikacji, więc muszą być obecne i przewodowe do interfejsów Rdzenia aplikacji za pomocą iniekcji zależności.

Rysunek 5-9 przedstawia bardziej szczegółowy widok architektury aplikacji ASP.NET Core podczas tworzenia zgodnie z tymi zaleceniami.

![diagram architektury ASP.NET Core po czystej architekturze](./media/image5-9.png)

**Rysunek 5-9.** diagram architektury ASP.NET Core po czystej architekturze.

Ponieważ rdzeń aplikacji nie zależy od infrastruktury, bardzo łatwo jest napisać zautomatyzowane testy jednostkowe dla tej warstwy. Rysunki 5-10 i 5-11 pokazują, jak testy pasują do tej architektury.

![Program UnitTestCore](./media/image5-10.png)

**Rysunek 5-10.** Testowanie jednostkowe Application Core w izolacji.

![Testy integracji](./media/image5-11.png)

**Rysunek 5-11.** Implementacje infrastruktury testowania integracji z zależnościami zewnętrznymi.

Ponieważ warstwa interfejsu i usług interfejsu nie ma żadnych bezpośredniej zależności od typów zdefiniowanych w projekcie infrastruktury, jest również bardzo łatwo zamienić implementacje, aby ułatwić testowanie lub w odpowiedzi na zmieniające się wymagania aplikacji. ASP.NET core wbudowanego użycia i obsługi wstrzykiwania zależności sprawia, że ta architektura najbardziej odpowiedni sposób struktury nietrywialne aplikacje monolityczne.

W przypadku aplikacji monolitycznych projekty Application Core, Infrastructure i UI są uruchamiane jako pojedyncza aplikacja. Architektura aplikacji w czasie wykonywania może wyglądać jak rysunek 5-12.

![ASP.NET Architektura rdzenia 2](./media/image5-12.png)

**Rysunek 5-12.** Przykładowa architektura ASP.NET core aplikacji.

### <a name="organizing-code-in-clean-architecture"></a>Organizowanie kodu w czystej architekturze

W rozwiązaniu czystej architektury każdy projekt ma jasne obowiązki. W związku z tym niektóre typy należą do każdego projektu i często znajdziesz foldery odpowiadające tym typom w odpowiednim projekcie.

Rdzeń aplikacji przechowuje model biznesowy, który obejmuje jednostki, usługi i interfejsy. Interfejsy te obejmują abstrakcje dla operacji, które będą wykonywane przy użyciu infrastruktury, takich jak dostęp do danych, dostęp do systemu plików, wywołania sieciowe itp. Czasami usługi lub interfejsy zdefiniowane w tej warstwie będą musiały pracować z typami innych niż jednostki, które nie mają zależności od interfejsu użytkownika lub infrastruktury. Można je zdefiniować jako proste obiekty transferu danych (DCO).

### <a name="application-core-types"></a>Typy rdzeni aplikacji

- Jednostki (klasy modelu biznesowego, które są utrwalione)
- Interfejsy
- Usługi
- UODO

Projekt infrastruktury zazwyczaj obejmuje implementacje dostępu do danych. W typowej ASP.NET podstawowej aplikacji sieci web te implementacje obejmują `Migration` platformę En Framework (EF) DbContext, wszystkie zdefiniowane obiekty EF Core i klasy implementacji dostępu do danych. Najczęstszym sposobem abstrakcyjnego kodu implementacji dostępu do danych jest użycie [wzorca projektu repozytorium](https://deviq.com/repository-pattern/).

Oprócz implementacji dostępu do danych projekt infrastruktury powinien zawierać implementacje usług, które muszą współdziałać z problemami dotyczącymi infrastruktury. Te usługi powinny implementować interfejsy zdefiniowane w rdzeniu aplikacji, a więc infrastruktura powinna mieć odwołanie do projektu Application Core.

### <a name="infrastructure-types"></a>Typy infrastruktury

- EF Typy`DbContext`rdzeni `Migration`( , )
- Typy implementacji dostępu do danych (repozytoria)
- Usługi specyficzne dla infrastruktury `FileLogger` `SmtpNotifier`(na przykład)

Warstwa interfejsu użytkownika w ASP.NET aplikacji Core MVC jest punktem wejścia dla aplikacji. Ten projekt powinien odwoływać się do projektu Application Core, a jego typy powinny współdziałać z infrastrukturą ściśle za pośrednictwem interfejsów zdefiniowanych w pliku Application Core. W warstwie interfejsu i usług nie należy zezwalać na bezpośrednie tworzenie wystąpienia ani statyczne wywołania typów warstw infrastruktury.

### <a name="ui-layer-types"></a>Typy warstw interfejsu i ui

- Kontrolery
- Filtry
- Widoki
- ViewModele
- Uruchamianie

Startup Klasa jest odpowiedzialny za konfigurowanie aplikacji i okablowania typów implementacji do interfejsów, dzięki czemu iniekcji zależności do poprawnego działania w czasie wykonywania.

> [!NOTE]
> W celu połączenia iniekcji zależności w ConfigureServices w pliku Startup.cs projektu interfejsu i ui, projekt może wymagać odwołania się do projektu infrastruktury. Ta zależność można wyeliminować, najłatwiej przy użyciu niestandardowego kontenera DI. Na potrzeby tego przykładu najprostszym podejściem jest umożliwienie projektowi interfejsu i informacji o projekcie Infrastruktura.

## <a name="monolithic-applications-and-containers"></a>Monolityczne zastosowania i pojemniki

Można utworzyć jedną i monolityczną aplikację sieci Web opartą na wdrażaniu i wdrożyć ją jako kontener. W aplikacji może nie być monolityczne, ale zorganizowane w kilka bibliotek, składników lub warstw. Zewnętrznie jest to pojedynczy kontener, taki jak pojedynczy proces, pojedyncza aplikacja sieci web lub pojedyncza usługa.

Aby zarządzać tym modelem, należy wdrożyć pojedynczy kontener do reprezentowania aplikacji. Aby skalować, wystarczy dodać dodatkowe kopie z modułem równoważenia obciążenia z przodu. Prostota pochodzi z zarządzania jednym wdrożeniem w jednym kontenerze lub maszynie wirtualnej.

![Rysunek 5-13](./media/image5-13.png)

W każdym kontenerze można dołączyć wiele składników/bibliotek lub warstw wewnętrznych, jak pokazano na rysunku 5-13. Ale zgodnie z zasadą kontenera _"kontener robi jedną rzecz i robi to w jednym procesie_", monolityczny wzór może być konfliktem.

Wadą tego podejścia jest if/when aplikacji rośnie, wymagając jej skalowania. Jeśli cała aplikacja jest skalowana, to naprawdę nie jest problemem. Jednak w większości przypadków kilka części aplikacji są punkty ssania wymagające skalowania, podczas gdy inne składniki są używane mniej.

Korzystając z typowego przykładu handlu elektronicznego, prawdopodobnie należy skalować składnik informacji o produkcie. Znacznie więcej klientów przegląda produkty niż je kupuje. Więcej klientów korzysta z koszyka niż z potoku płatności. Mniej klientów dodaje komentarze lub przegląda historię zakupów. I prawdopodobnie masz tylko garstkę pracowników, w jednym regionie, którzy muszą zarządzać treścią i kampaniami marketingowymi. Skalowanie monolitycznego projektu, cały kod jest wdrażany wiele razy.

Oprócz problemu "skalować wszystko" zmiany w jednym składniku wymagają pełnego ponownego testowania całej aplikacji i pełnego ponownego wdrożenia wszystkich wystąpień.

Monolityczne podejście jest powszechne, a wiele organizacji rozwija się z tego podejścia architektonicznego. Wiele z nich ma wystarczająco dobre wyniki, podczas gdy inne uderzają w granice. Wiele zaprojektowane ich aplikacji w tym modelu, ponieważ narzędzia i infrastruktury były zbyt trudne do tworzenia architektur zorientowanych na usługi (SOA), i nie widzą potrzeby, dopóki aplikacja wzrosła. Jeśli okaże się, że osiągasz granice monolitycznego podejścia, rozbicie aplikacji, aby umożliwić jej lepsze wykorzystanie kontenerów i mikrousług, może być następnym logicznym krokiem.

![Rysunek 5-14](./media/image5-14.png)

Wdrażanie aplikacji monolitycznych na platformie Microsoft Azure można osiągnąć przy użyciu dedykowanych maszyn wirtualnych dla każdego wystąpienia. Za pomocą [zestawów skalowania maszyn wirtualnych platformy Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), można łatwo skalować maszyn wirtualnych. [Usługi Azure App Services](https://azure.microsoft.com/services/app-service/) można uruchamiać aplikacje monolityczne i łatwo skalować wystąpienia bez konieczności zarządzania maszynami wirtualnymi. Usługi Azure App Services można uruchomić pojedyncze wystąpienia kontenerów platformy Docker, jak również, upraszczając wdrożenie. Za pomocą platformy Docker można wdrożyć pojedynczą maszynę wirtualną jako hosta platformy Docker i uruchomić wiele wystąpień. Za pomocą balansu platformy Azure, jak pokazano na rysunku 5-14, można zarządzać skalowanie.

Wdrożenie na różnych hostach można zarządzać za pomocą tradycyjnych technik wdrażania. Hostami platformy Docker można zarządzać za pomocą poleceń, takich jak **uruchamianie dokowane** wykonywane ręcznie lub za pomocą automatyzacji, takich jak potoki ciągłego dostarczania (CD).

### <a name="monolithic-application-deployed-as-a-container"></a>Monolityczna aplikacja wdrożona jako kontener

Istnieją zalety używania kontenerów do zarządzania wdrożeniami aplikacji monolitycznych. Skalowanie wystąpień kontenerów jest znacznie szybsze i łatwiejsze niż wdrażanie dodatkowych maszyn wirtualnych. Nawet w przypadku używania zestawów skalowania maszyn wirtualnych do skalowania maszyn wirtualnych, zajmują one czas na wystąpienie. Po wdrożeniu jako wystąpienia aplikacji, konfiguracja aplikacji jest zarządzana jako część maszyny Wirtualnej.

Wdrażanie aktualizacji jako obrazów platformy Docker jest znacznie szybsze i wydajne w sieci. Obrazy dokowane zazwyczaj rozpoczynają się w ciągu kilku sekund, przyspieszając wdrażanie. Niszczanie wystąpienia platformy Docker jest `docker stop` tak proste, jak wydawanie polecenia, zazwyczaj kończy się w mniej niż sekundę.

Ponieważ kontenery są z natury niezmienne przez projekt, nigdy nie musisz się martwić o uszkodzone maszyny wirtualne, podczas gdy skrypty aktualizacji mogą zapomnieć o uwzględnieniu określonej konfiguracji lub pliku pozostawionego na dysku.

Kontenery platformy Docker można używać do monolitycznego wdrażania prostszych aplikacji sieci web. Poprawia to ciągłą integrację i ciągłe wdrażanie potoków i pomaga osiągnąć sukces wdrożenia do produkcji. Nie więcej "To działa na mojej maszynie, dlaczego to nie działa w produkcji?"

Architektura oparta na mikrousługach ma wiele zalet, ale korzyści te są kosztem zwiększonej złożoności. W niektórych przypadkach koszty przewyższają korzyści, więc monolityczną aplikacją wdrożeniową działającą w jednym kontenerze lub w kilku kontenerach jest lepszym rozwiązaniem.

Monolityczne aplikacji nie może być łatwo rozdzielalne na mikrousług dobrze oddzielone. Mikrousługi powinny działać niezależnie od siebie, aby zapewnić bardziej odporną aplikację. Jeśli nie można dostarczyć niezależnych wycinków funkcji aplikacji, oddzielenie go tylko zwiększa złożoność.

Aplikacja może jeszcze nie być konieczne do skalowania funkcji niezależnie. Wiele aplikacji, gdy trzeba skalować poza jednym wystąpieniu, można to zrobić za pośrednictwem stosunkowo prosty proces klonowania tego całego wystąpienia. Dodatkowa praca, aby oddzielić aplikację do dyskretnych usług zapewnia minimalne korzyści, gdy skalowanie pełnych wystąpień aplikacji jest proste i opłacalne.

Na wczesnym etapie opracowywania aplikacji, może nie mieć jasnego pojęcia, gdzie są naturalne granice funkcjonalne. W miarę opracowywania minimalnego opłacalnego produktu, naturalna separacja może jeszcze nie powiodła się. Niektóre z tych warunków mogą być tymczasowe. Można rozpocząć od utworzenia aplikacji monolityczne, a później oddzielić niektóre funkcje, które mają zostać opracowane i wdrożone jako mikrousług. Inne warunki mogą być niezbędne do przestrzeni problem aplikacji, co oznacza, że aplikacja nigdy nie może być podzielona na wiele mikrousług.

Oddzielenie aplikacji na wiele dyskretnych procesów wprowadza również obciążenie. Jest więcej złożoności w oddzielaniu funkcji na różne procesy. Protokoły komunikacyjne stają się bardziej złożone. Zamiast wywołań metody należy użyć komunikacji asynchronicznej między usługami. Podczas przechodzenia do architektury mikrousług należy dodać wiele bloków konstrukcyjnych zaimplementowanych w wersji mikrousług aplikacji eShopOnContainers: obsługa magistrali zdarzeń, odporność wiadomości i ponownych prób, spójność ostateczna i inne.

Znacznie prostsza [aplikacja referencyjna eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) obsługuje użycie kontenera monolitycznego z jednym kontenerem. Aplikacja zawiera jedną aplikację internetową, która zawiera tradycyjne widoki MVC, interfejsy API sieci Web i strony razor. Ta aplikacja może być uruchomiona z `docker-compose build` `docker-compose up` katalogu głównego rozwiązania za pomocą i poleceń. To polecenie konfiguruje kontener dla wystąpienia `Dockerfile` sieci web, przy użyciu znalezionego w katalogu głównym projektu sieci web i uruchamia kontener na określonym porcie. Możesz pobrać źródło tej aplikacji z GitHub i uruchomić go lokalnie. Nawet ta monolityczna aplikacja korzysta z wdrożenia w środowisku kontenera.

Na przykład konteneryzowane wdrożenie oznacza, że każde wystąpienie aplikacji działa w tym samym środowisku. Obejmuje to środowisko deweloperskie, w którym odbywają się wczesne testowanie i rozwój. Zespół programista można uruchomić aplikację w środowisku konteneryzowanym, który pasuje do środowiska produkcyjnego.

Ponadto konteneryzowane aplikacje są skalowane w poziomie przy niższych kosztach. Korzystanie ze środowiska kontenera umożliwia większy udostępnianie zasobów niż tradycyjne środowiska maszyn wirtualnych.

Na koniec konteneryzowanie aplikacji wymusza oddzielenie logiki biznesowej od serwera magazynu. W miarę skalowania aplikacji, wiele kontenerów będzie polegać na jednym nośniku magazynu fizycznego. Ten nośnik pamięci masowej jest zazwyczaj serwerem o wysokiej dostępności z uruchomioną bazą danych programu SQL Server.

## <a name="docker-support"></a>Obsługa platformy Docker

Projekt `eShopOnWeb` jest uruchamiany na programie .NET Core. W związku z tym można uruchomić w kontenerach opartych na systemie Linux lub Windows. Należy zauważyć, że w przypadku wdrażania platformy Docker chcesz użyć tego samego typu hosta dla programu SQL Server. Kontenery oparte na systemie Linux umożliwiają mniejszy rozmiar i są preferowane.

Za pomocą programu Visual Studio 2017 lub nowszego można dodać obsługę platformy Docker do istniejącej aplikacji, klikając prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierając pozycję **Dodaj** > **obsługę platformy Docker**. Spowoduje to dodanie wymaganych plików i modyfikację projektu w celu ich użycia. Bieżący `eShopOnWeb` przykład ma już te pliki w miejscu.

Plik na `docker-compose.yml` poziomie rozwiązania zawiera informacje o tym, jakie obrazy należy utworzyć i jakie kontenery uruchomić. Plik umożliwia użycie polecenia `docker-compose` do uruchamiania wielu aplikacji w tym samym czasie. W takim przypadku jest tylko uruchomienie projektu sieci Web. Można go również użyć do skonfigurowania zależności, takich jak oddzielny kontener bazy danych.

```yml
version: '3'

services:
  eshopwebmvc:
    image: eshopwebmvc
    build:
      context: .
      dockerfile: src/Web/Dockerfile
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
    ports:
      - "5106:5106"

networks:
  default:
    external:
      name: nat
```

Plik `docker-compose.yml` odwołuje `Dockerfile` się `Web` do projektu. Służy `Dockerfile` do określania, który kontener podstawowy będzie używany i jak aplikacja zostanie skonfigurowana na nim. `Web`": `Dockerfile`

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /app

COPY *.sln .
COPY . .
WORKDIR /app/src/Web
RUN dotnet restore

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS runtime
WORKDIR /app
COPY --from=build /app/src/Web/out ./

ENTRYPOINT ["dotnet", "Web.dll"]
```

### <a name="troubleshooting-docker-problems"></a>Rozwiązywanie problemów z platformą Docker

Po uruchomieniu konteneryzowanej aplikacji, nadal działa, dopóki go zatrzymać. Można wyświetlić, które kontenery `docker ps` są uruchomione za pomocą polecenia. Można zatrzymać uruchomiony kontener za `docker stop` pomocą polecenia i określając identyfikator kontenera.

Należy zauważyć, że uruchomione kontenery platformy Docker może być powiązany z portami, które w przeciwnym razie mogą próbować użyć w środowisku programistycznym. Jeśli spróbujesz uruchomić lub debugować aplikację przy użyciu tego samego portu co uruchomiony kontener platformy Docker, zostanie wyświetlany błąd informujący, że serwer nie może powiązać z tym portem. Po raz kolejny zatrzymanie kontenera powinno rozwiązać problem.

Jeśli chcesz dodać obsługę platformy Docker do aplikacji przy użyciu programu Visual Studio, upewnij się, że pulpit platformy Docker jest uruchomiony, gdy to zrobisz. Kreator nie zostanie uruchomiony poprawnie, jeśli pulpit platformy Docker nie jest uruchomiony podczas uruchamiania kreatora. Ponadto kreator sprawdza bieżący wybór kontenera, aby dodać poprawną obsługę platformy Docker. Jeśli chcesz dodać obsługę kontenerów systemu Windows, musisz uruchomić kreatora, gdy masz skonfigurowany pulpit platformy Docker z skonfigurowanymi kontenerami systemu Windows. Jeśli chcesz dodać obsługę kontenerów systemu Linux, uruchom kreatora, gdy masz platformę Docker uruchomioną z skonfigurowanymi kontenerami systemu Linux.

### <a name="references--common-web-architectures"></a>Referencje — typowe architektury internetowe

- **Czysta architektura**  
  <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
- **Architektura cebuli**  
  <https://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
- **Wzór repozytorium**  
  <https://deviq.com/repository-pattern/>
- **Szablon rozwiązania czystej architektury**  
  <https://github.com/ardalis/cleanarchitecture>
- **Architekcjinowanie mikrousług e-book**  
  <https://aka.ms/MicroservicesEbook>
- **DDD (projekt oparty na domenie)**  
  <https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/>

>[!div class="step-by-step"]
>[Poprzedni](architectural-principles.md)
>[następny](common-client-side-web-technologies.md)
