---
title: Typowe architektury aplikacji internetowych
description: Architekt nowoczesnych aplikacji sieci Web z ASP.NET Core i Azure | Poznaj typowe architektury aplikacji sieci web
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: c9a8e9450d81ac2e63a8c8ea54592ed81e646e05
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988131"
---
# <a name="common-web-application-architectures"></a>Typowe architektury aplikacji internetowych

> "Jeśli uważasz, że dobra architektura jest kosztowna, spróbuj złej architektury."  
> _- Brian Foote i Joseph Yoder_

Większość tradycyjnych aplikacji platformy .NET jest wdrażana jako pojedyncze jednostki odpowiadające wykonywalnej lub pojedynczej aplikacji sieci web działającej w ramach jednej domeny aplikacji usług IIS. Jest to najprostszy model wdrażania i bardzo dobrze obsługuje wiele wewnętrznych i mniejszych aplikacji publicznych. Jednak nawet biorąc pod uwagę tę pojedynczą jednostkę wdrożenia, większość nietrywialnych aplikacji biznesowych korzysta z pewnej logicznej separacji na kilka warstw.

## <a name="what-is-a-monolithic-application"></a>Co to jest aplikacja monolityczna?

Monolityczne aplikacji jest taki, który jest całkowicie samodzielny, pod względem jego zachowania. Może wchodzić w interakcje z innymi usługami lub magazynami danych w trakcie wykonywania swoich operacji, ale rdzeń jego zachowania działa w ramach własnego procesu, a cała aplikacja jest zazwyczaj wdrażana jako pojedyncza jednostka. Jeśli taka aplikacja musi skalować poziomo, zazwyczaj cała aplikacja jest duplikowana na wielu serwerach lub maszynach wirtualnych.

## <a name="all-in-one-applications"></a>Aplikacje typu "wszystko w jednym"

Najmniejsza możliwa liczba projektów dla architektury aplikacji jest jeden. W tej architekturze cała logika aplikacji jest zawarta w jednym projekcie, skompilowana do pojedynczego zestawu i wdrożona jako pojedyncza jednostka.

Nowy projekt ASP.NET Core, utworzony w programie Visual Studio lub z wiersza polecenia, rozpoczyna się jako prosty monolit "all-in-one". Zawiera wszystkie zachowanie aplikacji, w tym logiki dostępu do prezentacji, firmy i danych. Rysunek 5-1 przedstawia strukturę plików aplikacji pojedynczego projektu.

![Pojedynczy projekt ASP.NET aplikacji Core](./media/image5-1.png)

**Rysunek 5-1.** Pojedynczy projekt ASP.NET aplikacji Core.

W scenariuszu pojedynczego projektu oddzielenie problemów jest osiągane za pomocą folderów. Szablon domyślny zawiera oddzielne foldery dla obowiązków wzorca MVC modeli, widoków i kontrolerów, a także dodatkowe foldery dla danych i usług. W tym układzie szczegóły prezentacji powinny być ograniczone w miarę możliwości do folderu Widoki, a szczegóły implementacji dostępu do danych powinny być ograniczone do klas przechowywanych w folderze Dane. Logika biznesowa powinna znajdować się w usługach i klasach w folderze Modele.

Chociaż proste, jednoprojektowe rozwiązanie monolityczne ma pewne wady. Wraz ze wzrostem rozmiaru i złożoności projektu liczba plików i folderów będzie nadal rosnąć. Problemy interfejsu użytkownika (modele, widoki, kontrolery) znajdują się w wielu folderach, które nie są zgrupowane alfabetycznie. Ten problem tylko pogarsza się, gdy dodatkowe konstrukcje na poziomie interfejsu użytkownika, takie jak filtry lub ModelBinders, są dodawane w ich własnych folderach. Logika biznesowa jest rozproszona między modelami i usług folderami i nie ma wyraźnego wskazania, w których klasach, w których folderach powinny zależeć inne. Ten brak organizacji na poziomie projektu często prowadzi do [kodu spaghetti](https://deviq.com/spaghetti-code/).

Aby rozwiązać te problemy, aplikacje często ewoluują w rozwiązania wieloprojektowe, gdzie każdy projekt jest uważany za miejsce w określonej _warstwie_ aplikacji.

## <a name="what-are-layers"></a>Co to są warstwy logiczne?

W miarę jak aplikacje stają się coraz bardziej złożone, jednym ze sposobów zarządzania tą złożonością jest rozbicie aplikacji zgodnie z jej obowiązkami lub obawami. Wynika to z zasady separacji problemów i może pomóc utrzymać rosnącą bazę kodu zorganizowaną, dzięki czemu deweloperzy mogą łatwo znaleźć, gdzie niektóre funkcje są implementowane. Architektura warstwowa oferuje jednak wiele zalet wykraczających poza organizację kodu.

Organizując kod na warstwy, wspólne funkcje niskiego poziomu mogą być ponownie za pomocą całej aplikacji. To ponowne użycie jest korzystne, ponieważ oznacza mniej kodu musi być napisane i ponieważ może umożliwić aplikacji standaryzować na jednej implementacji, zgodnie z [zasadą don't repeat yourself (DRY).](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)

Dzięki architekturze warstwowej aplikacje mogą wymuszać ograniczenia, na których warstwy mogą komunikować się z innymi warstwami. Pomaga to osiągnąć hermetyzację. Po zmianie lub wymianie warstwy należy mieć wpływ tylko na te warstwy, które z nią współpracują. Ograniczając warstwy, które zależą od innych warstw, wpływ zmian można złagodzić, tak aby pojedyncza zmiana nie wpływała na całą aplikację.

Warstwy (i hermetyzacja) znacznie ułatwiają zastępowanie funkcji w aplikacji. Na przykład aplikacja może początkowo używać własnej bazy danych programu SQL Server dla trwałości, ale później można użyć strategii trwałości opartej na chmurze lub jeden za interfejsem API sieci web. Jeśli aplikacja prawidłowo hermetyzuje jego trwałości implementacji w warstwie logicznej, że SQL Server określonewarstwy mogą być zastąpione przez nowy implementując ten sam interfejs publiczny.

Oprócz możliwości wymiany implementacji w odpowiedzi na przyszłe zmiany w wymaganiach, warstwy aplikacji mogą również ułatwić wymianę implementacji do celów testowych. Zamiast pisać testy, które działają względem warstwy danych rzeczywistych lub warstwy interfejsu użytkownika aplikacji, warstwy te można zastąpić w czasie testowania fałszywymi implementacjami, które zapewniają znane odpowiedzi na żądania. Zazwyczaj sprawia to, że testy znacznie łatwiejsze do zapisu i znacznie szybciej uruchomić w porównaniu do uruchamiania testów w rzeczywistej infrastruktury aplikacji.

Warstw logicznych jest powszechną techniką poprawy organizacji kodu w aplikacjach dla przedsiębiorstw i istnieje kilka sposobów, w którym kod może być zorganizowany w warstwy.

> [!NOTE]
 > _Warstwy_ reprezentują logiczne oddzielenie w aplikacji. W przypadku, gdy logika aplikacji jest fizycznie dystrybuowana do oddzielnych serwerów lub procesów, te oddzielne obiekty docelowe wdrożenia fizycznego są określane jako _warstwy_. Jest możliwe i dość powszechne, aby mieć N-Layer aplikacji, która jest wdrażana w jednej warstwie.

## <a name="traditional-n-layer-architecture-applications"></a>Tradycyjne aplikacje architektury "N-Layer"

Najbardziej powszechna organizacja logiki aplikacji na warstwy jest pokazana na rysunku 5-2.

![Typowe warstwy aplikacji](./media/image5-2.png)

**Rysunek 5-2.** Typowe warstwy aplikacji.

Warstwy te są często skracane jako UI, BLL (Business Logic Layer) i DAL (Data Access Layer). Korzystając z tej architektury, użytkownicy żądają za pośrednictwem warstwy interfejsu użytkownika, która współdziała tylko z biblioteką BLL. Logika logiki z kolei można wywołać dal dla żądań dostępu do danych. Warstwa interfejsu użytkownika nie należy bezpośrednio żądać żadnych żądań do warstwy DAL, ani nie powinien wchodzić w interakcje z trwałości bezpośrednio za pomocą innych środków. Podobnie logiki biznesowej należy wchodzić w interakcje z trwałości, przechodząc przez dal. W ten sposób każda warstwa ma swoją dobrze znaną odpowiedzialność.

Jedną z wad tego tradycyjnego podejścia warstwowego jest to, że zależności w czasie kompilacji są uruchamiane od góry do dołu. Oznacza to, że warstwa interfejsu użytkownika zależy od logiki biznesowej, która zależy od warstwy DAL. Oznacza to, że logika logiki, która zwykle posiada najważniejszą logikę w aplikacji, zależy od szczegółów implementacji dostępu do danych (i często od istnienia bazy danych). Testowanie logiki biznesowej w takiej architekturze jest często trudne, wymagające testowej bazy danych. Zasada inwersji zależności może służyć do rozwiązania tego problemu, jak zobaczysz w następnej sekcji.

Rysunek 5-3 przedstawia przykładowe rozwiązanie, rozbijając aplikację na trzy projekty według odpowiedzialności (lub warstwy).

![Prosta monolityczna aplikacja z trzema projektami](./media/image5-3.png)

**Rysunek 5-3.** Prosta aplikacja monolityczna z trzema projektami.

Mimo że ta aplikacja używa kilku projektów do celów organizacyjnych, nadal jest wdrażana jako pojedyncza jednostka, a jej klienci będą z nią współpracować jako pojedyncza aplikacja sieci web. Pozwala to na bardzo prosty proces wdrażania. Rysunek 5-4 pokazuje, jak taka aplikacja może być hostowana przy użyciu platformy Azure.

![Proste wdrażanie aplikacji Azure Web App](./media/image5-4.png)

**Rysunek 5-4.** Proste wdrażanie aplikacji Azure Web App

Wraz ze wzrostem potrzeb aplikacji mogą być wymagane bardziej złożone i niezawodne rozwiązania wdrożeniowe. Rysunek 5-5 przedstawia przykład bardziej złożonego planu wdrażania, który obsługuje dodatkowe możliwości.

![Wdrażanie aplikacji sieci web w usłudze Azure App Service](./media/image5-5.png)

**Rysunek 5-5.** Wdrażanie aplikacji sieci web w usłudze Azure App Service

Wewnętrznie organizacja tego projektu w wielu projektach opartych na odpowiedzialności poprawia łatwość konserwacji aplikacji.

To urządzenie można skalować w górę lub na zewnątrz, aby korzystać ze skalowalności opartej na chmurze na żądanie. Skalowanie w górę oznacza dodanie dodatkowego procesora CPU, pamięci, miejsca na dysku lub innych zasobów do serwerów obsługujących aplikację. Skalowanie w poziomie oznacza dodanie dodatkowych wystąpień takich serwerów, niezależnie od tego, czy są to serwery fizyczne, maszyny wirtualne czy kontenery. Gdy aplikacja jest hostowana w wielu wystąpieniach, moduł równoważenia obciążenia jest używany do przypisywania żądań do poszczególnych wystąpień aplikacji.

Najprostszym podejściem do skalowania aplikacji sieci web na platformie Azure jest skonfigurowanie skalowania ręcznie w planie usługi app service aplikacji. Rysunek 5-6 przedstawia odpowiedni ekran pulpitu nawigacyjnego platformy Azure, aby skonfigurować liczbę wystąpień obsługujących aplikację.

![Skalowanie planu usługi app service na platformie Azure](./media/image5-6.png)

**Rysunek 5-6.** Skalowanie planu usługi app service na platformie Azure.

## <a name="clean-architecture"></a>Czysta architektura

Aplikacje zgodne z zasadą inwersji zależności, a także zasadami projektowania opartego na domenie (DDD) mają tendencję do dotarć do podobnej architektury. Ta architektura przeszła przez wiele nazw na przestrzeni lat. Jednym z pierwszych nazwisk była architektura sześciokątna, a następnie porty i adaptery. Ostatnio, to był cytowany jako [Architektura Cebula](https://jeffreypalermo.com/blog/the-onion-architecture-part-1/) lub [Clean Architecture](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). Ta ostatnia nazwa, Clean Architecture, jest używana jako nazwa tej architektury w tym e-booku.

Aplikacja referencyjna eShopOnWeb używa podejścia Clean Architecture w organizowaniu kodu w projektach. Możesz znaleźć szablon rozwiązania, którego można użyć jako punktu wyjścia dla własnego ASP.NET Core na repozytorium [GitHub ardalis/cleanarchitecture.](https://github.com/ardalis/cleanarchitecture)

Czysta architektura umieszcza logikę biznesową i model aplikacji w centrum aplikacji. Zamiast logiki biznesowej zależy od dostępu do danych lub innych problemów z infrastrukturą, ta zależność jest odwrócona: szczegóły infrastruktury i implementacji zależą od rdzenia aplikacji. Osiąga się to poprzez definiowanie abstrakcji lub interfejsów w rdzeniu aplikacji, które są następnie implementowane przez typy zdefiniowane w warstwie Infrastruktura. Typowym sposobem wizualizacji tej architektury jest użycie serii koncentrycznych okręgów, podobnych do cebuli. Rysunek 5-7 przedstawia przykład tego stylu reprezentacji architektonicznej.

![Czysta architektura; widok cebuli](./media/image5-7.png)

**Rysunek 5-7.** Czysta architektura; widok cebuli

Na tym diagramie zależności przepływu w kierunku najbardziej wewnętrznego okręgu. Rdzeń aplikacji bierze swoją nazwę od jego pozycji w centrum tego diagramu. I widać na diagramie, że rdzeń aplikacji nie ma zależności od innych warstw aplikacji. Jednostki i interfejsy aplikacji znajdują się w samym centrum. Tylko na zewnątrz, ale nadal w rdzeniu aplikacji, są usługi domeny, które zazwyczaj implementują interfejsy zdefiniowane w kręgu wewnętrznym. Poza rdzeniem aplikacji warstwy interfejsu użytkownika i infrastruktury zależą od rdzenia aplikacji, ale nie od siebie nawzajem (koniecznie).

Rysunek 5-8 przedstawia bardziej tradycyjny diagram warstwy poziomej, który lepiej odzwierciedla zależność między interfejsem użytkownika a innymi warstwami.

![Czysta architektura; widok warstwy poziomej](./media/image5-8.png)

**Rysunek 5-8.** Czysta architektura; widok warstwy poziomej

Należy zauważyć, że strzałki stałe reprezentują zależności w czasie kompilacji, podczas gdy strzałka przerywana reprezentuje zależność tylko do środowiska uruchomieniowego. Dzięki czystej architekturze warstwa interfejsu użytkownika współpracuje z interfejsami zdefiniowanymi w rdzeniu aplikacji w czasie kompilacji i idealnie nie powinna wiedzieć o typach implementacji zdefiniowanych w warstwie Infrastruktura. W czasie wykonywania jednak te typy implementacji są wymagane do wykonania aplikacji, więc muszą być obecne i podłączone do interfejsów rdzenia aplikacji za pośrednictwem iniekcji zależności.

Rysunek 5-9 przedstawia bardziej szczegółowy widok architektury aplikacji ASP.NET Core podczas tworzenia zgodnie z tymi zaleceniami.

![ASP.NET diagram architektury Core po czystej architekturze](./media/image5-9.png)

**Rysunek 5-9.** ASP.NET diagram architektury Core po czystej architekturze.

Ponieważ rdzeń aplikacji nie zależy od infrastruktury, jest bardzo łatwo napisać zautomatyzowane testy jednostkowe dla tej warstwy. Rysunki 5-10 i 5-11 pokazują, jak testy pasują do tej architektury.

![Wynik testu jednostkowego](./media/image5-10.png)

**Rysunek 5-10.** Badanie jednostkowe Application Core w izolacji.

![Testy integracji](./media/image5-11.png)

**Rysunek 5-11.** Integracja testowania implementacji infrastruktury z zależności zewnętrznych.

Ponieważ warstwa interfejsu użytkownika nie ma żadnej bezpośredniej zależności od typów zdefiniowanych w projekcie infrastruktury, jest również bardzo łatwo zamienić implementacje, w celu ułatwienia testowania lub w odpowiedzi na zmieniające się wymagania aplikacji. ASP.NET wbudowane użycie i obsługa iniekcji zależności sprawia, że ta architektura jest najbardziej odpowiednim sposobem struktury nietrywialnych aplikacji monolitycznych.

W przypadku aplikacji monolitycznych projekty rdzenia aplikacji, infrastruktury i interfejsu użytkownika są uruchamiane jako pojedyncza aplikacja. Architektura aplikacji środowiska wykonawczego może wyglądać mniej więcej jak rysunek 5-12.

![architektura ASP.NET Core 2](./media/image5-12.png)

**Rysunek 5-12.** Przykładowa ASP.NET architektura środowiska wykonawczego aplikacji Core.

### <a name="organizing-code-in-clean-architecture"></a>Organizowanie kodu w czystej architekturze

W rozwiązaniu Czystej architektury każdy projekt ma jasne obowiązki. W związku z tym niektóre typy należą do każdego projektu i często znajdziesz foldery odpowiadające tym typom w odpowiednim projekcie.

W programie Application Core znajduje się model biznesowy, który obejmuje jednostki, usługi i interfejsy. Interfejsy te obejmują abstrakcje dla operacji, które będą wykonywane przy użyciu infrastruktury, takich jak dostęp do danych, dostęp do systemu plików, wywołania sieciowe itp. Czasami usługi lub interfejsy zdefiniowane w tej warstwie będą musiały współpracować z typami niebędącymi encjami, które nie mają zależności od interfejsu użytkownika lub infrastruktury. Można je zdefiniować jako proste obiekty transferu danych (DTO).

### <a name="application-core-types"></a>Typy rdzeni aplikacji

- Jednostki (klasy modelu biznesowego, które są utrwalone)
- Interfejsy
- Usługi
- OTO

Projekt Infrastruktura zazwyczaj obejmuje implementacje dostępu do danych. W typowej aplikacji sieci web ASP.NET Core te implementacje obejmują Entity Framework (EF) DbContext, wszystkie obiekty EF Core, `Migration` które zostały zdefiniowane i klasy implementacji dostępu do danych. Najczęstszym sposobem na abstrakcyjne kod implementacji dostępu do danych jest użycie [wzorca projektu repozytorium.](https://deviq.com/repository-pattern/)

Oprócz wdrożeń dostępu do danych projekt infrastrukturalny powinien zawierać implementacje usług, które muszą współdziałać z problemami dotyczącymi infrastruktury. Te usługi należy implementować interfejsy zdefiniowane w rdzeniu aplikacji, a więc infrastruktura powinna mieć odwołanie do projektu Core aplikacji.

### <a name="infrastructure-types"></a>Typy infrastruktury

- Typy rdzeni`DbContext` `Migration`EF ( , )
- Typy implementacji dostępu do danych (repozytoria)
- Usługi specyficzne dla infrastruktury `FileLogger` (np. `SmtpNotifier`

Warstwa interfejsu użytkownika w ASP.NET podstawowej aplikacji MVC jest punktem wejścia dla aplikacji. Ten projekt powinien odwoływać się do projektu Application Core, a jego typy powinny współdziałać z infrastrukturą ściśle za pośrednictwem interfejsów zdefiniowanych w programie Application Core. W warstwie interfejsu użytkownika nie powinno być dozwolone żadne bezpośrednie tworzenie wystąpienia lub statyczne wywołania typów warstw infrastruktury.

### <a name="ui-layer-types"></a>Typy warstw interfejsu użytkownika

- Kontrolery
- Filtry
- Widoki
- ViewModelki
- Uruchamianie

Startup Klasa jest odpowiedzialny za konfigurowanie aplikacji i okablowanie typów implementacji do interfejsów, dzięki czemu iniekcja zależności działać poprawnie w czasie wykonywania.

> [!NOTE]
> Aby wire up iniekcji zależności w ConfigureServices w pliku Startup.cs projektu interfejsu użytkownika, projekt może być konieczne odwołanie projektu infrastruktury. Ta zależność można wyeliminować, najłatwiej przy użyciu niestandardowego kontenera DI. Na potrzeby tego przykładu najprostszym podejściem jest umożliwienie projektu interfejsu użytkownika odwoływać się do projektu infrastruktury.

## <a name="monolithic-applications-and-containers"></a>Monolityczne zastosowania i pojemniki

Można utworzyć pojedynczą i monolityczną aplikację sieci Web opartą na wdrożeniu sieci Web lub usługę i wdrożyć ją jako kontener. W aplikacji może nie być monolityczne, ale zorganizowane w kilka bibliotek, składników lub warstw. Zewnętrznie jest to pojedynczy kontener, taki jak pojedynczy proces, pojedyncza aplikacja sieci web lub pojedyncza usługa.

Aby zarządzać tym modelem, należy wdrożyć pojedynczy kontener do reprezentowania aplikacji. Aby skalować, wystarczy dodać dodatkowe kopie z modułem równoważenia obciążenia z przodu. Prostota pochodzi z zarządzania pojedynczym wdrożeniem w jednym kontenerze lub maszynie wirtualnej.

![Rysunek 5-13](./media/image5-13.png)

W każdym kontenerze można dołączyć wiele składników/bibliotek lub warstw wewnętrznych, jak pokazano na rysunku 5-13. Ale zgodnie z _zasadą kontenera "kontener robi jedną rzecz i robi to w jednym procesie_", monolityczny wzorzec może być konfliktem.

Wadą tego podejścia jest, jeśli/gdy aplikacja rośnie, wymagając go do skalowania. Jeśli cała aplikacja jest skalowana, nie stanowi to problemu. Jednak w większości przypadków kilka części aplikacji są punkty dławienia wymagające skalowania, podczas gdy inne składniki są używane mniej.

Korzystając z typowego przykładu eCommerce, to, co prawdopodobnie trzeba skalować, to składnik informacji o produkcie. O wiele więcej klientów przegląda produkty niż je kupuje. Więcej klientów korzysta z koszyka niż z potoku płatności. Mniej klientów dodawać komentarze lub wyświetlić ich historii zakupów. I prawdopodobnie masz tylko garstkę pracowników, w jednym regionie, którzy muszą zarządzać treściami i kampaniami marketingowymi. Skalując projekt monolityczny, cały kod jest wdrażany wiele razy.

Oprócz problemu "skaluj wszystko", zmiany w jednym składniku wymagają pełnego ponownego przetestowania całej aplikacji i pełnego ponownego rozmieszczenia wszystkich wystąpień.

Podejście monolityczne jest powszechne, a wiele organizacji rozwija się z tym podejściem architektonicznym. Wiele z nich ma wystarczająco dobre wyniki, podczas gdy inni są uderzanie limity. Wiele zaprojektowanych aplikacji w tym modelu, ponieważ narzędzia i infrastruktura były zbyt trudne do tworzenia architektur zorientowanych na usługi (SOA), i nie widzą potrzeby, dopóki aplikacja wzrosła. Jeśli okaże się, że widzisz limity podejścia monolitycznego, rozbicie aplikacji, aby włączyć ją do lepszego wykorzystania kontenerów i mikrousług może być następnym logicznym krokiem.

![Rysunek 5-14](./media/image5-14.png)

Wdrażanie aplikacji monolitycznych na platformie Microsoft Azure można osiągnąć przy użyciu dedykowanych maszyn wirtualnych dla każdego wystąpienia. Za pomocą [zestawów skalowania maszyny wirtualnej platformy Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)można łatwo skalować maszyny wirtualne. [Usługi Azure App Services](https://azure.microsoft.com/services/app-service/) mogą uruchamiać aplikacje monolityczne i łatwo skalować wystąpienia bez konieczności zarządzania maszynami wirtualnymi. Usługi Azure App Services można uruchomić pojedyncze wystąpienia kontenerów platformy Docker, jak również, upraszczając wdrożenie. Za pomocą platformy Docker można wdrożyć pojedynczą maszynę wirtualną jako host platformy Docker i uruchomić wiele wystąpień. Za pomocą balanseru platformy Azure, jak pokazano na rysunku 5-14, można zarządzać skalowania.

Wdrożeniem różnych hostów można zarządzać za pomocą tradycyjnych technik wdrażania. Hostami platformy Docker można zarządzać za pomocą poleceń, takich jak **uruchamianie platformy docker** wykonywane ręcznie lub za pomocą automatyzacji, takich jak potoki ciągłego dostarczania (CD).

### <a name="monolithic-application-deployed-as-a-container"></a>Aplikacja monolityczna wdrożona jako kontener

Istnieją korzyści z używania kontenerów do zarządzania wdrożeniami aplikacji monolitycznych. Skalowanie wystąpień kontenerów jest znacznie szybsze i łatwiejsze niż wdrażanie dodatkowych maszyn wirtualnych. Nawet w przypadku używania zestawów skalowania maszyny wirtualnej do skalowania maszyn wirtualnych, zajmują one czas na wystąpienie. Po wdrożeniu jako wystąpienia aplikacji konfiguracja aplikacji jest zarządzana jako część maszyny Wirtualnej.

Wdrażanie aktualizacji jako obrazów platformy Docker jest znacznie szybsze i wydajne w sieci. Obrazy platformy Docker zazwyczaj rozpoczynają się w ciągu kilku sekund, przyspieszając wdrażanie. Burzenie wystąpienia platformy Docker jest tak `docker stop` proste, jak wydawanie polecenia, zazwyczaj ukończenie w mniej niż sekundę.

Ponieważ kontenery są z natury niezmienne z założenia, nigdy nie musisz się martwić o uszkodzone maszyny wirtualne, podczas gdy skrypty aktualizacji mogą zapomnieć o uwzględnienie określonej konfiguracji lub pliku pozostawionego na dysku.

Kontenery platformy Docker można używać do monolitycznego wdrażania prostszych aplikacji sieci web. Poprawia to ciągłą integrację i ciągłe wdrażanie potoków i pomaga osiągnąć sukces wdrażania do produkcji. Nie więcej "To działa na moim komputerze, dlaczego nie działa w produkcji?"

Architektura oparta na mikrousługach ma wiele zalet, ale te korzyści są kosztem zwiększonej złożoności. W niektórych przypadkach koszty przewyższają korzyści, więc monolityczne aplikacji wdrażania uruchomiony w jednym kontenerze lub w zaledwie kilku kontenerach jest lepszym rozwiązaniem.

Aplikacja monolityczne nie może być łatwo rozkładanych na dobrze oddzielone mikrousług. Mikrousługi powinny działać niezależnie od siebie, aby zapewnić bardziej odporną aplikację. Jeśli nie można dostarczyć niezależnych wycinków funkcji aplikacji, oddzielenie go tylko zwiększa złożoność.

Aplikacja może jeszcze nie trzeba skalować funkcji niezależnie. Wiele aplikacji, gdy trzeba skalować poza pojedyncze wystąpienie, można to zrobić za pomocą stosunkowo prostego procesu klonowania tego wystąpienia całego. Dodatkowa praca, aby oddzielić aplikację na dyskretne usługi zapewnia minimalne korzyści podczas skalowania pełnych wystąpień aplikacji jest proste i ekonomiczne.

Na początku rozwoju aplikacji, może nie mieć jasnego pojęcia, gdzie są naturalne granice funkcjonalne. W miarę opracowywania minimalnego opłacalnego produktu, naturalna separacja może jeszcze nie pojawiły się. Niektóre z tych warunków mogą być tymczasowe. Można rozpocząć od utworzenia aplikacji monolityczne, a później oddzielić niektóre funkcje, które mają być opracowane i wdrożone jako mikrousługi. Inne warunki mogą być istotne dla miejsca problem aplikacji, co oznacza, że aplikacja nigdy nie może być podzielona na wiele mikrousług.

Oddzielenie aplikacji do wielu procesów dyskretnych również wprowadza obciążenie. Istnieje większa złożoność w rozdzielaniu funkcji na różne procesy. Protokoły komunikacyjne stają się bardziej złożone. Zamiast wywołania metody, należy użyć komunikacji asynchroniczne między usługami. Podczas przenoszenia do architektury mikrousług, należy dodać wiele bloków konstrukcyjnych zaimplementowanych w wersji mikrousług aplikacji eShopOnContainers: obsługa magistrali zdarzeń, odporność komunikatów i ponownych prób, spójność ostateczna i więcej.

Znacznie prostsza [aplikacja referencyjna eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) obsługuje użycie kontenera monolitycznego z jednym kontenerem. Aplikacja zawiera jedną aplikację internetową, która zawiera tradycyjne widoki MVC, interfejsy API sieci Web i strony Razor. Ta aplikacja może być uruchomiona z `docker-compose build` `docker-compose up` katalogu głównego rozwiązania za pomocą i poleceń. To polecenie konfiguruje kontener dla wystąpienia `Dockerfile` sieci web przy użyciu znajdującego się w katalogu głównym projektu sieci web i uruchamia kontener na określonym porcie. Możesz pobrać źródło tej aplikacji z gitHub i uruchomić ją lokalnie. Nawet ta monolityczna aplikacja korzysta z wdrażania w środowisku kontenera.

Po pierwsze, wdrożenie konteneryzowane oznacza, że każde wystąpienie aplikacji jest uruchamiane w tym samym środowisku. Obejmuje to środowisko deweloperskie, w którym odbywają się wczesne testowanie i rozwój. Zespół deweloperów można uruchomić aplikację w środowisku konteneryzowanym, który pasuje do środowiska produkcyjnego.

Ponadto aplikacje konteneryzowane są skalowane w poziomie przy niższych kosztach. Korzystanie ze środowiska kontenera umożliwia większe udostępnianie zasobów niż tradycyjne środowiska maszyn wirtualnych.

Na koniec konteneryzacji aplikacji wymusza oddzielenie logiki biznesowej i serwera magazynu. Jak aplikacja jest skalowana w poziomie, wiele kontenerów będzie polegać na jednym nośniku magazynu fizycznego. Ten nośnik magazynu zazwyczaj jest serwerem o wysokiej dostępności z bazą danych programu SQL Server.

## <a name="docker-support"></a>Pomoc techniczna firmy Docker

Projekt `eShopOnWeb` jest uruchamiany na programie .NET Core. W związku z tym można uruchomić w kontenerach opartych na systemie Linux lub Windows. Należy zauważyć, że w przypadku wdrożenia platformy Docker chcesz użyć tego samego typu hosta dla programu SQL Server. Kontenery oparte na systemie Linux umożliwiają mniejszą powierzchnię i są preferowane.

Za pomocą programu Visual Studio 2017 lub nowszego można dodać obsługę platformy Docker do istniejącej aplikacji, klikając prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierając pozycję **Dodaj** > **obsługę platformy Docker.** Spowoduje to dodanie wymaganych plików i modyfikuje projekt, aby z nich korzystać. Bieżąca `eShopOnWeb` próbka ma już te pliki w miejscu.

Plik na `docker-compose.yml` poziomie rozwiązania zawiera informacje o tym, jakie obrazy do utworzenia i jakie kontenery do uruchomienia. Plik umożliwia użycie polecenia `docker-compose` do uruchamiania wielu aplikacji w tym samym czasie. W takim przypadku jest tylko uruchomienie projektu sieci Web. Można również użyć go do konfigurowania zależności, takich jak oddzielny kontener bazy danych.

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

Plik `docker-compose.yml` odwołuje się `Dockerfile` do `Web` projektu. Jest `Dockerfile` używany do określenia, który kontener podstawowy będzie używany i jak aplikacja będzie skonfigurowana na nim. " `Web` `Dockerfile`:

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

### <a name="troubleshooting-docker-problems"></a>Rozwiązywanie problemów z docker

Po uruchomieniu aplikacji konteneryzowane, kontynuuje uruchamianie, dopóki go zatrzymać. Można wyświetlić, które kontenery są uruchomione za `docker ps` pomocą polecenia. Uruchomiony kontener można zatrzymać za `docker stop` pomocą polecenia i określając identyfikator kontenera.

Należy zauważyć, że uruchomione kontenery platformy Docker mogą być powiązane z portami, które w przeciwnym razie można spróbować użyć w środowisku programistycznym. Jeśli spróbujesz uruchomić lub debugować aplikację przy użyciu tego samego portu co uruchomiony kontener platformy Docker, zostanie wyświetlony błąd informujący, że serwer nie może powiązać z tym portem. Po raz kolejny zatrzymanie kontenera należy rozwiązać problem.

Jeśli chcesz dodać obsługę platformy Docker do aplikacji przy użyciu programu Visual Studio, upewnij się, że program Docker Desktop jest uruchomiony po wykonaniu tej funkcji. Kreator nie będzie działać poprawnie, jeśli pulpit platformy Docker nie jest uruchomiony po uruchomieniu kreatora. Ponadto kreator sprawdza bieżący wybór kontenera, aby dodać poprawną obsługę platformy Docker. Jeśli chcesz dodać obsługę kontenerów systemu Windows, musisz uruchomić kreatora, gdy masz skonfigurowany pulpit platformy Docker z skonfigurowaną konfiguracją Kontenery systemu Windows. Jeśli chcesz dodać obsługę kontenerów systemu Linux, uruchom kreatora, gdy masz docker uruchomiony z kontenerami systemu Linux skonfigurowane.

### <a name="references--common-web-architectures"></a>Odwołania — typowe architektury sieci web

- **Czysta architektura**  
  <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
- **Architektura cebuli**  
  <https://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
- **Wzorzec repozytorium**  
  <https://deviq.com/repository-pattern/>
- **Szablon rozwiązania czystej architektury**  
  <https://github.com/ardalis/cleanarchitecture>
- **Architekcja Mikrousługi e-book**  
  <https://aka.ms/MicroservicesEbook>
- **DDD (projekt oparty na domenie)**  
  <https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/>

>[!div class="step-by-step"]
>[Poprzedni](architectural-principles.md)
>[następny](common-client-side-web-technologies.md)
