---
title: Typowe architektury aplikacji internetowych
description: Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure | Poznaj typowe architektury aplikacji internetowych
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 68f88d29a6c88f4ce261a0a2794035d43db1fc0c
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921107"
---
# <a name="common-web-application-architectures"></a>Typowe architektury aplikacji internetowych

> "Jeśli Twoim zdaniem dobry architektury jest kosztowne, spróbuj zły architektury".  
> _— Brian Środkowa i Joseph Yoder_

Tradycyjnych aplikacji platformy .NET są wdrażane jako pojedynczej jednostki odpowiadający plik wykonywalny lub aplikacji jednej sieci web, w ramach pojedynczego elementu appdomain usług IIS. To jest najprostszym modelem wdrażania i obsługuje wiele aplikacji wewnętrznych i mniejsze publicznych bardzo dobrze. Jednak nawet biorąc pod uwagę ta pojedyncza jednostka wdrożenia, najbardziej nietrywialnymi aplikacji biznesowych korzystają z niektórych logicznie rozdzielić na kilka warstwy.

## <a name="what-is-a-monolithic-application"></a>Co to jest aplikacją monolityczną?

Monolitycznych aplikacji to taki, który jest całkowicie niezależne pod względem jego zachowanie. Może współpracować z innymi magazynami usług lub danych w trakcie wykonywania jego operacji, ale podstawowe jego zachowanie jest uruchamiany w swoim własnym procesie i całej aplikacji jest zwykle wdrażane jako pojedyncza jednostka. Jeśli takiej aplikacji wymaga skalowanie w poziomie, zwykle całej aplikacji występuje na wielu serwerach lub maszynach wirtualnych.

## <a name="all-in-one-applications"></a>Aplikacje w jednym

Najmniejsza możliwa liczba projektów dla architektury aplikacji jest jednym. W tej architekturze całej logiki aplikacji znajdujących się w jednym projekcie, skompilowany w jednym zestawie i wdrażane jako pojedyncza jednostka.

Nowy projekt ASP.NET Core, czy utworzony w programie Visual Studio lub z wiersza polecenia, rozpoczyna się jako prosty monolitu "All-in-one". Zawiera ono wszystkie zachowanie aplikacji, w tym logiką dostępu do prezentacji, biznesowych i danych. Rysunek 5-1 przedstawia strukturę pliku aplikacji pojedynczego projektu.

![](./media/image5-1.png)

**Rysunek 5-1.** Pojedynczego projektu aplikacji platformy ASP.NET Core.

W przypadku pojedynczego projektu separacji odbywa się za pomocą folderów. Szablon domyślny zawiera osobne foldery dla obowiązków wzorzec MVC modeli, widoków i kontrolerów, a także dodatkowe foldery dla danych i usług. W tym przypadku prezentacji szczegóły powinny być ograniczone w najszerszym możliwym do folderu, widoki i szczegółów implementacji dostępu do danych powinny być ograniczone do klasy, przechowywane w folderze danych. Logika biznesowa powinien znajdować się w usługach i klas w folderze modeli.

Mimo że jest to prosty, rozwiązanie monolityczny projekt pojedynczego ma pewne wady. Wzrostem wielkości i złożoności projektu, liczbę plików i folderów będą nadal rosnąć, jak również. Dotyczy interfejsu użytkownika (modele, widoki, kontrolery) znajdują się w wielu folderach, które nie są zgrupowane razem alfabetycznie. Ten problem tylko pobiera niższa po dodaniu dodatkowych konstrukcji poziomu interfejsu użytkownika, takie jak filtry lub ModelBinders, we własnym folderze. Reguły biznesowe są rozproszone między folderami modeli i usług, a nie ma żadnego wskazania Wyczyść, z których klas w foldery, które powinny zależeć od które. Ten brak organizacji na poziomie projektu często prowadzi do [kodu w postaci spaghetti](https://deviq.com/spaghetti-code/).

Aby rozwiązać te problemy, aplikacje często się rozwijać, w rozwiązaniach dotyczących wielu projektów, gdzie każdy projekt jest uważany za znajdują się w szczególności _warstwy_ aplikacji.

## <a name="what-are-layers"></a>Co to są warstwy?

Jak aplikacje zwiększanie się stopnia skomplikowania, jednym ze sposobów, aby zarządzać tym złożoność jest dzielenia aplikacji zgodnie z jego obowiązki lub wątpliwości. Następuje oddzielenie obaw zasady i może pomóc zachować rosnącej bazy kodu, przeprowadzane tak, aby deweloperzy mogą łatwo znaleźć, gdzie niektóre funkcje są zaimplementowane. Architektury warstwowej oferuje szereg zalet poza tylko kod organizacji, mimo że.

Przez organizowanie kodu w warstwach, typowych funkcji niższego poziomu mogą zostać ponownie użyte w całej aplikacji. To ponowne użycie jest korzystne, ponieważ oznacza to, musi być napisany mniejszej ilości kodu i umożliwia aplikacji standaryzuj pojedynczą implementacją następujące [nie powtarzaj samodzielnie (PRÓBNEGO)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) zasady.

Za pomocą architektury warstwowej aplikacji może wymusić ograniczenia, które warstwy mogą komunikować się z innymi warstwami. Pozwala to osiągnąć hermetyzacji. Gdy warstwa jest zmieniane ani zastąpiona, powinny mieć wpływ tylko te warstwy, współpracujących z nią. Poprzez ograniczenie, które warstwy zależą od innych warstw wpływ zmian na których można zminimalizować tak, aby pojedynczej zmiany nie ma wpływu na całej aplikacji.

Warstwy (i hermetyzacji) stał się znacznie łatwiejsze do zastąpienia funkcji w obrębie aplikacji. Na przykład aplikacja początkowo użyć własną bazę danych programu SQL Server dla trwałości, ale później można wybrać do użycia strategii opartej na chmurze trwałości lub przy użyciu jednej za interfejs API sieci web. Jeśli aplikacja ma prawidłowo hermetyzowane implementacji trwałości w obrębie warstwy logiczne, tej konkretnej warstwy programu SQL Server może zostać zastąpiona nową wdrażanie tego samego interfejsu publicznego.

Oprócz możliwości wymienić implementacji w odpowiedzi na przyszłe zmiany w wymaganiach warstw aplikacji może również ułatwić wymienić implementacje dla celów testowych. Zamiast pisać testy, które działają względem rzeczywiste dane warstwy lub warstwy interfejsu użytkownika aplikacji, można zastąpić te warstwy w czasie testu z fałszywego implementacji, które zapewniają znanych odpowiedzi na żądania. To zwykle sprawia, że testy znacznie łatwiejsze do zapisu i znacznie szybciej wykonywania w porównaniu do uruchamiania testów ponownie infrastruktury rzeczywistych aplikacji.

Logiczne warstw jest typową techniką dla poprawy organizacji kodu w aplikacjach dla przedsiębiorstw oprogramowania, a istnieje kilka sposobów, w których kodu mogą być organizowane w warstwy.

> [!NOTE]
 > _Warstwy_ reprezentują separacji logicznej w ramach aplikacji. W przypadku, gdy aplikacja logiki jest fizycznie rozproszone do oddzielnych serwerów lub procesy, te obiekty docelowe wdrażane pojedynczo fizyczne są określane jako _warstwy_. Jest to możliwe i dość często, aby korzystać z aplikacji N-warstwy, który jest wdrożony w pojedynczej warstwie.

## <a name="traditional-n-layer-architecture-applications"></a>Tradycyjne aplikacje architektury "N-warstwa"

Najczęściej organizacji aplikacji logiki do warstwy jest wyświetlana w rysunek 5-2.

![](./media/image5-2.png)

**Rysunek 5-2.** Typowa aplikacja warstwy.

Te warstwy to nazwa często skracana jako interfejsu użytkownika, LOGIKI (warstwy logiki biznesowej) i warstwy DAL (Warstwa dostępu do danych). Za pomocą tej architektury, użytkownikom wysyłanie żądań za pośrednictwem warstwy Interfejsu, która współdziała tylko z LOGIKI. LOGIKI, z kolei wywołać warstwę DAL dla żądań dostępu do danych. Warstwy interfejsu użytkownika nie należy wprowadzać żadnych żądań warstwy DAL bezpośrednio, ani nie powinny korzystać z trwałością bezpośrednio za pomocą innych środków. Podobnie LOGIKI powinien komunikować się tylko z trwałością, przechodząc przez warstwę DAL. W ten sposób każda warstwa ma swoje własne dobrze znane odpowiedzialności.

To podejście warstwowe tradycyjnych jedną wadą jest to, uruchom zależności kompilacji od góry do dołu. Oznacza to, że warstwy Interfejsu zależy od LOGIKI, która zależy od warstwy DAL. Oznacza to, że LOGIKI, która zwykle zawiera najważniejsze logikę w aplikacji, zależy od szczegółów implementacji dostępu do danych (i często na istnienie bazy danych). Testowanie logikę biznesową w ramach architektury często trudno jest wymaganie test bazy danych. Zasada odwrócenie zależności może służyć do rozwiązania tego problemu, jak zobaczysz w następnej sekcji.

Rysunek 5-3 przedstawiono przykładowe rozwiązanie, podzielenie aplikacji na trzy projekty przez odpowiedzialność (lub warstwy).

![](./media/image5-3.png)

**Rysunek 5-3.** Prostych aplikacji monolitycznej o trzy projekty.

Mimo że ta aplikacja używa kilku projektów do celów organizacji, wciąż jest wdrażane jako pojedyncza jednostka i jego klienci będą korzystać z niego jako pojedynczej aplikacji sieci web. Pozwala to na proces wdrażania bardzo proste. Rysunek 5-4 pokazano, jak takiej aplikacji może być hostowany przy użyciu platformy Azure.

![](./media/image5-4.png)

**Rysunek 5-4.** Proste wdrożenie aplikacji sieci Web platformy Azure

Jak wzrostem wymagań aplikacji bardziej złożone i niezawodnych rozwiązań wdrażania mogą być wymagane. Rysunek 5-5 przedstawia przykład bardziej złożonych planu wdrożenia, który obsługuje dodatkowe funkcje.

![](./media/image5-5.png)

**Rysunek 5-5.** Wdrażanie aplikacji sieci web usługi Azure App Service

Wewnętrznie organizacji tego projektu na wiele projektów, w oparciu o odpowiedzialności zwiększa łatwość konserwacji aplikacji.

Tej jednostki mogą być skalowane w górę lub w poziomie z zalet skalowania na żądanie oparte na chmurze. Skalowanie w górę oznacza dodawanie dodatkowych procesora CPU, pamięci, miejsca na dysku lub inne zasoby do serwerów hostującego twoją aplikację. Skalowanie w poziomie oznaczają dodanie dodatkowych wystąpień takie serwery są serwerów fizycznych, maszyn wirtualnych lub kontenerów. Gdy aplikacja jest hostowana w wielu wystąpieniach, moduł równoważenia obciążenia służy do przypisywania żądania do wystąpień poszczególnych aplikacji.

Najprostszym sposobem skalowanie aplikacji sieci web na platformie Azure jest skonfigurować skalowanie ręczne w planie usług aplikacji w aplikacji. Rysunek 5 – 6 przedstawia ekranu odpowiedniego pulpitu nawigacyjnego platformy Azure, aby skonfigurować liczbę wystąpień obsługujących aplikację.

![](./media/image5-6.png)

**Rysunek 5 – 6.** Plan usługi App Service skalowania na platformie Azure.

## <a name="clean-architecture"></a>Wyczyść architektury

Aplikacje, postępuj zgodnie z zasadą odwrócenie zależności, a także zasady projektowania driven (DDD), które zwykle na podobną architekturę. Ta architektura stała się różnymi nazwami przez lata. Jeden z imiona był architektury (sześciokąt), następuje portów i kart. Niedawno, jest ono cytowane jako [architektury przenikanie](https://jeffreypalermo.com/blog/the-onion-architecture-part-1/) lub [czystej architektury](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). Ta nazwa czystej architektury, jest używana jako nazwa dla tej architektury w tej książce elektronicznej.

> [!NOTE]
> Termin czystej architektury mogą być stosowane do aplikacji, które zostały utworzone przy użyciu zasad DDD, jak również do tych, które są kompilowane przy użyciu DDD. W przypadku pierwsze, ta kombinacja mogą być określone jako "Czyste architektura DDD".

Architektura czyste umieszcza model biznesowy logiki i aplikacji w Centrum aplikacji. Zamiast logiki biznesowej, które są zależne od dostęp do danych lub innych czynników infrastruktury, zostaje odwrócony tej zależności: infrastruktury oraz szczegóły jej implementacji zależą od podstawowych aplikacji. Jest to osiągane przez zdefiniowanie abstrakcje lub interfejsów w obszarach podstawowych aplikacji, które następnie są implementowane przez typy zdefiniowane w warstwie infrastruktury. Często stosowaną metodą zwizualizować tej architektury jest szereg koncentrycznych, podobnie jak przenikanie. Rysunek 5 – 7 przedstawiono przykład ten styl architektury reprezentacji.

![](./media/image5-7.png)

**Rysunek 5 – 7.** Wyczyść architektury; przenikanie widoku

W tym diagramie węzeł zależności przepływu kierunku najbardziej wewnętrznego okręgu. Podstawowa aplikacja pobiera jego nazwę jego pozycja w samym sercu ten diagram. I będzie widoczny na diagramie, Core aplikacji nie ma zależności w innych warstwach aplikacji. Jednostki i interfejsy aplikacji znajdują się w bardzo Centrum. Tuż powyżej, ale nadal w obszarach podstawowych aplikacji są usługi domenowe, które zazwyczaj implementują interfejsy, zdefiniowane w wewnętrznego okręgu. Poza podstawowych aplikacji zarówno w Interfejsie użytkownika, jak i warstwy infrastruktury zależeć na podstawowych aplikacji, ale nie na siebie nawzajem (zawsze).

Rysunek 5 – 8 przedstawia bardziej tradycyjny diagramu warstwowego poziomy, które lepiej odzwierciedla zależność między interfejsu użytkownika i innych warstw.

![](./media/image5-8.png)

**Rysunek 5 – 8.** Wyczyść architektury; Wyświetl warstwy poziome

Należy pamiętać, stałe strzałki reprezentują zależności kompilacji, natomiast kreskowaną Strzałka reprezentuje zależności tylko do środowiska uruchomieniowego. Przy użyciu czystej architektury warstwy Interfejsu współpracuje z interfejsów zdefiniowanych w obszarach podstawowych aplikacji w czasie kompilacji, a najlepiej nie powinna wiedzieć o typach wdrożenia, zdefiniowane w warstwie infrastruktury. W czasie wykonywania jednak te typy wdrożenia są wymagane dla aplikacji, które można wykonać, więc musi być obecny i przewodowych połączeń do interfejsów podstawowych aplikacji za pomocą iniekcji zależności.

Rysunek 5-9 przedstawiono bardziej szczegółowy widok architektury aplikacji platformy ASP.NET Core podczas kompilowania następujące tych zaleceń.

![ASPNET Podstawowa architektura](./media/image5-9.png)

**Rysunek 5-9.** Diagram architektury programu ASP.NET Core zgodnie z czystej architektury.

Ponieważ podstawowych aplikacji nie są zależne od infrastruktury, jest bardzo ułatwia pisanie zautomatyzowanych testów jednostek dla tej warstwy. Rysunki 5 – 10 i 5 11 pokazują, jak testy mieści się w tej architekturze.

![UnitTestCore](./media/image5-10.png)

**Rysunek 5 – 10.** Testowanie jednostek podstawowych aplikacji w izolacji.

![IntegrationTests](./media/image5-11.png)

**Rysunek 5 – 11.** Integracja testowania implementacji infrastruktury z zależnościami zewnętrznymi.

Ponieważ warstwy interfejsu użytkownika nie ma żadnych zależności bezpośrednich dla typów zdefiniowanych w projekcie infrastruktury, podobnie jest bardzo proste, można zamienić implementacji, albo w celu ułatwienia badania lub w odpowiedzi na zmieniające się wymagania aplikacji. Wbudowane korzystanie z platformy ASP.NET Core i pomoc techniczna dla wstrzykiwanie zależności sprawia, że w tej architekturze najbardziej stosownego sposobu struktury nietrywialnymi monolitycznych aplikacji.

W przypadku aplikacji monolitycznych projektów podstawowych aplikacji, infrastruktury i interfejs użytkownika wszystkie działają jako pojedynczą aplikacją. Architektura aplikacji środowiska uruchomieniowego może wyglądać jak rysunek 5 – 12.

![Architektura platformy ASP.NET Core 2](./media/image5-12.png)

**Rysunek 5 – 12.** Architektura środowiska uruchomieniowego z przykładowej aplikacji platformy ASP.NET Core.

### <a name="organizing-code-in-clean-architecture"></a>Organizowanie kodu w czystej architektury

W rozwiązaniu czystej architektury każdy projekt ma wyczyść obowiązki. W efekcie niektóre typy należy w każdym projekcie i można często znaleźć odpowiadające typy w projekcie odpowiednie foldery.

Podstawowa aplikacja przechowuje model biznesowy, który zawiera jednostki, usługi i interfejsy. Interfejsy te obejmują elementy abstrakcji dla operacji, które będą wykonywane przy użyciu infrastruktury, takich jak dostęp do danych, dostęp do systemu plików, wywołań sieci itp. Czasami usług lub interfejsy zdefiniowane w tej warstwie będzie konieczna współpraca z typami innego niż jednostka, które mają nie zależności dotyczące interfejsu użytkownika lub infrastruktury. Te mogą być definiowane jako prosty transferu obiektów danych (dto).

### <a name="application-core-types"></a>Typy podstawowe aplikacji

- Jednostki (business modelu klas, które są zachowywane)
- Interfejsy
- Usługi
- Dto

Projekt infrastruktury zwykle zawiera implementacje dostępu do danych. W typowej aplikacji sieci web platformy ASP.NET Core, te implementacje to DbContext Entity Framework (EF), wszelkie programu EF Core `Migration` obiekty, które zostały zdefiniowane i dostępu do danych klasy implementacji. Najczęstszym sposobem abstrakcyjny kod implementacji dostępu do danych jest za pośrednictwem [wzorzec projektowy repozytorium](https://deviq.com/repository-pattern/).

Oprócz implementacji dostępu do danych projektu infrastruktury powinna zawierać implementacji usług, które muszą współdziałać z uwagi infrastrukturze. Te usługi powinny implementować interfejsów zdefiniowanych w obszarach podstawowych aplikacji, a więc infrastruktury powinny mieć odwołanie do projektu aplikacji Core.

### <a name="infrastructure-types"></a>Typy infrastruktury

- EF Core typów (`DbContext`, `Migration`)
- Typy implementacji (repozytoriów) dostępu do danych
- Usługi specyficzne dla infrastruktury (na przykład `FileLogger` lub `SmtpNotifier`)

Warstwa interfejsu użytkownika w aplikacji ASP.NET Core MVC jest punkt wejścia dla aplikacji. Ten projekt powinien odwoływać się do projektu podstawowych aplikacji, a jego typy powinny wchodzić w interakcje z infrastrukturą wyłącznie za pośrednictwem interfejsów zdefiniowane w podstawowej aplikacji. Nie bezpośrednie wystąpienia lub statycznych wywołania typom warstwę infrastruktury powinien być dozwolony w warstwie interfejsu użytkownika.

### <a name="ui-layer-types"></a>Typy warstwy interfejsu użytkownika

- Kontrolery
- Filtry
- Widoki
- Modele widoków
- Uruchamianie

Klasa początkowa jest odpowiedzialny za konfigurowanie aplikacji i okablowania typów implementacji interfejsów, dzięki czemu wstrzykiwanie zależności zapewnić prawidłowe działanie w czasie wykonywania.

> [!NOTE]
> Aby powiązać wstrzykiwanie zależności w ConfigureServices w pliku Startup.cs projektu interfejsu użytkownika, projekt może być konieczne odwoływać się do projektu infrastruktury. Ta zależność można wyeliminować najłatwiej przy użyciu niestandardowego kontenera DI. Na potrzeby tego przykładu najprostszą metodą jest umożliwienie projekt interfejsu użytkownika, aby odwoływać się do projektu infrastruktury.

## <a name="monolithic-applications-and-containers"></a>Aplikacje monolityczne i kontenerów

Można utworzyć pojedyncze i monolityczne wdrożenia na podstawie aplikacji sieci Web lub usługi i wdrożyć go jako kontener. W tej aplikacji nie może być monolityczne, ale zorganizowanym w kilku bibliotek, składników lub warstwy. Zewnętrznie jest jeden kontener, takich jak pojedynczego procesu, aplikacji sieci web jednej lub jednej usługi.

Aby zarządzać tym modelu, możesz wdrożyć jeden kontener, do reprezentowania aplikacji. Skalowanie, wystarczy dodać dodatkowe kopie z modułem równoważenia obciążenia z przodu. Prostotę pochodzi z zarządzania pojedyncze wdrożenie w ramach jednego kontenera lub maszyny Wirtualnej.

![](./media/image5-13.png)

Jak pokazano w rysunek 5-13 może zawierać wiele składniki i biblioteki lub wewnętrzny warstwy w ramach każdego kontenera. Jednak zgodnie z zasadą kontenera _"kontener nie jedno i zrobi to w jednym procesie_", monolitycznych wzorzec może być konflikt.

Wadą tego podejścia jest dostarczany, jeśli/gdy aplikację wzrośnie, wymaganiem go do skalowania. Jeśli jest skalowana w całej aplikacji, nie jest tak naprawdę problem. Jednak w większości przypadków kilka części aplikacji są punkty urządzenie rozruchowe, wymagających skalowania, podczas gdy inne składniki są używane, mniejsze.

Przy użyciu typowego handlu elektronicznego, co prawdopodobnie należy skalować jest składnikiem informacji produktu. Wielu klientów więcej Przeglądaj produktów, niż je zakupić. Większej liczby klientów użyj koszyka, niż korzystanie z potoku płatności. Dodaj komentarze lub mniejszej liczby klientów, w którym zostanie wyświetlanie ich historii zakupów. I prawdopodobnie masz tylko grupy pracowników w jednym regionie, musisz zarządzać zawartości i kampanii marketingowych. Przy użyciu skalowania monolityczny projekt, cały kod jest wdrażany wiele razy.

Oprócz problem "skalować wszystko" zmiany pojedynczego składnika wymagają, pełne ponowne przetestowanie całej aplikacji i pełne ponowne wdrożenie wszystkich wystąpień.

Podejścia monolitycznego jest wspólny, a w wielu organizacjach opracowujesz w tym podejściu architektury. Wiele występują dobra wystarczającej liczby wyników, podczas gdy inne osiągnięcia limitów. Wiele zaprojektowane swoich aplikacji, w tym modelu, ponieważ infrastruktura i narzędzia zostały zbyt trudne do tworzenia architektury zorientowanej na usługi (SOA), a nie był widoczny potrzebę, dopóki zwiększył aplikacji. Jeśli okaże się, że występują limity podejścia monolitycznego, następnym logicznym krokiem może być podzielenie aplikacji, aby umożliwić lepiej korzystać z kontenerów oraz mikrousług.

![](./media/image5-14.png)

Wdrażanie aplikacji monolitycznych w systemie Microsoft Azure można osiągnąć przy użyciu dedykowanych maszyn wirtualnych dla poszczególnych wystąpień. Za pomocą [Azure Virtual Machine Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), można łatwo skalować maszyny wirtualne. [Usługi Azure App Services](https://azure.microsoft.com/services/app-service/) uruchamiać aplikacje monolityczne i łatwo skalować wystąpień bez konieczności zarządzania maszynami wirtualnymi. Usługi Azure App Services można uruchomić jednego wystąpienia kontenerów platformy Docker, co upraszcza wdrożenie. Za pomocą platformy Docker, można wdrożyć jedną maszynę Wirtualną jako hosta Docker i uruchomić wiele wystąpień. Za pomocą równoważenie Azure, jak pokazano w rysunek 5-14, można zarządzać skalowania.

Wdrażanie na różnych hostach można zarządzać za pomocą techniki wdrażania tradycyjnych. Hostów platformy Docker można zarządzać za pomocą poleceń, takich jak **platformy docker, uruchom** wykonać ręcznie lub za pomocą automatyzacji, takie jak potoki ciągłe dostarczanie (CD).

### <a name="monolithic-application-deployed-as-a-container"></a>Monolitycznych wdrożone jako kontener

Istnieją korzyści z używania kontenerów, aby zarządzać wdrożeniami aplikacji monolitycznej. Skalowanie wystąpienia kontenerów jest znacznie szybsze i prostsze wdrażania dodatkowych maszyn wirtualnych. Nawet wtedy, gdy za pomocą skalowania maszyn wirtualnych zestawy skalowania maszyn wirtualnych, ich potrwać do wystąpienia. Po wdrożeniu jako wystąpień aplikacji, konfiguracji aplikacji odbywa się w ramach maszyny wirtualnej.

Wdrażanie aktualizacji zgodnie z obrazów platformy Docker jest znacznie szybszy i wydajność sieci. Obrazy platformy docker zazwyczaj rozpoczyna się w ciągu kilku sekund, skracając wdrożeniach. Zniszczenia wystąpienia platformy Docker jest równie proste jak wystawianie `docker stop` polecenia, zwykle Kończenie pracy w ciągu niecałej sekundy.

Kontenery są założenia niezmienne, zgodnie z projektem, nigdy nie musisz się martwić o uszkodzony maszyn wirtualnych, natomiast skryptów aktualizacji może zapomniano konto niektóre konkretnej konfiguracji lub po lewej stronie w pliku na dysku.

Korzystaj z kontenerów platformy Docker, monolitycznych wdrożenia aplikacji sieci web, prostsze. Zwiększa to ciągłej integracji i ciągłego wdrażania potoków i pomaga osiągnąć sukces wdrażania do produkcji. Nie ma więcej "działa w mojej maszynie, dlaczego nie działa w środowisku produkcyjnym?"

Architektura mikrousług ma wiele zalet, ale te korzyści pochodzą kosztem wzrostu złożoności. W niektórych przypadkach koszty przeważają korzyści, dlatego lepszym rozwiązaniem nie jest aplikacją monolityczną wdrożenia uruchomionych w jednym kontenerze, lub w kilku kontenerów.

Aplikacji monolitycznej może nie być w prosty sposób decomposable na mikrousługi dobrze rozdzielone. Mikrousługi powinny działać niezależnie od siebie, aby zapewnić lepszą odporność aplikacji. Jeśli nie można dostarczyć wycinki funkcji niezależnie od aplikacji, oddzielając tylko zwiększa złożoność.

Aplikacja nie może jeszcze wymagać niezależne przeskalowywanie się funkcje. Wiele aplikacji, kiedy ich potrzebują skalować poza pojedyncze wystąpienie, to zrobić za pomocą stosunkowo prosty proces klonowania całego wystąpienia. Dodatkowej pracy do rozdzielania aplikacji na osobne usługi zapewnia korzyści z minimalnym przypadku skalowanie pełną wystąpienia aplikacji jest proste i ekonomiczne.

Na wczesnym etapie tworzenia aplikacji możesz nie mieć dalsze których naturalnych funkcjonalności. Podczas opracowywania minimalne produktu możliwego do użycia fizyczne rozdzielenie może nie jeszcze związane. Niektóre z tych warunków, mogą być tymczasowe. Może rozpocząć od utworzenia aplikacji monolitycznej, a później oddzielić niektórymi funkcjami, które zostaną wdrożone i wdrażane jako mikrousług. Inne warunki mogą być niezbędne do przestrzeni problem aplikacji, co oznacza, że aplikacja może nigdy nie można podzielić na wiele mikrousług.

Oddzielenie aplikacji w wielu procesach dyskretnych wprowadza również obciążenie. Istnieje więcej złożoności w podziale funkcji w różnych procesach. Protokoły komunikacyjne są coraz bardziej złożone. Zamiast wywołania metody należy użyć komunikacji asynchronicznej między usługami. Po przeniesieniu do architektury mikrousług, musisz dodać wiele bloków konstrukcyjnych zaimplementowane w wersji mikrousługi aplikacji w ramach aplikacji eShopOnContainers: Obsługa magistrali zdarzeń, odporności komunikat i ponownych prób i spójności ostatecznej.

Znacznie prostsze [aplikacji referencyjnej eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) obsługuje użycie pojedynczej kontenerami monolitycznego. Aplikacja zawiera jednej aplikacji sieci web, która obejmuje tradycyjnych widoków MVC, internetowe interfejsy API i stron Razor. Tę aplikację można uruchomić z katalogu głównego rozwiązania przy użyciu `docker-compose build` i `docker-compose up` poleceń. To polecenie umożliwia skonfigurowanie kontenera sieci Web wystąpienia, za pomocą `Dockerfile` znalezione w katalogu głównym projektu sieci web i uruchamia kontener na określonym porcie. Można pobrać źródła dla tej aplikacji z witryny GitHub i uruchomić go lokalnie. Nawet tej aplikacji monolitycznej korzysta z wdrażana w środowisku kontenera.

Do jednego wdrażania konteneryzowanych oznacza, że każde wystąpienie aplikacji działa w tym samym środowisku. Dotyczy to również Środowisko deweloperskie, gdzie odbywać się wcześnie środowisk testowych i programistycznych. Zespół opracowujący można uruchomić aplikację w środowisku konteneryzowanych, który odpowiada środowisku produkcyjnym.

Ponadto kontenerowych nimi aplikacje skalowanie przy niskich kosztach. Przy użyciu środowiska kontenera umożliwia udostępnianie niż tradycyjnych środowisk maszyny Wirtualnej większą zasobów.

Na koniec konteneryzowania aplikacji powoduje oddzielenie logiki biznesowej i storage server. Ponieważ aplikacja jest skalowana w poziomie, wiele kontenerów będzie wszystkie zależny od średniej lub jednego magazynu fizycznego. Ten nośnik magazynowania będzie zazwyczaj wysokiej dostępności serwera z systemem bazy danych programu SQL Server.

## <a name="docker-support"></a>Obsługę platformy docker

`eShopOnWeb` Uruchomienia projektu na platformie .NET Core. W związku z tym może działać w kontenerach opartych na systemie Linux albo systemem Windows. Należy pamiętać, wdrożenie platformy Docker, chcesz używać tego samego typu hosta dla programu SQL Server. Kontenery opartych na systemie Linux Zezwalaj na mniejszych rozmiarów i są preferowane.

Można użyć programu Visual Studio 2017 r. lub nowszej można dodać obsługę platformy Docker do istniejącej aplikacji, klikając prawym przyciskiem myszy nad projektem w **Eksploratora rozwiązań** i wybierając pozycję **Dodaj** > **platformy Docker Obsługa**. Dodaje pliki wymagane i modyfikuje projekt, aby umożliwić ich używanie. Bieżący `eShopOnWeb` przykładowe ma już tych plików w miejscu.

Poziom rozwiązania `docker-compose.yml` plik zawiera informacje o jakie obrazy do tworzenia i jakie kontenery do uruchomienia. Plik umożliwia `docker-compose` polecenie w celu uruchomienia wielu aplikacji w tym samym czasie. W tym przypadku jest tylko uruchamianie projektu sieci Web. Można również użyć do konfigurowania zależności, takich jak kontener oddzielnej bazy danych.

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

`docker-compose.yml` Pliku odwołania `Dockerfile` w `Web` projektu. `Dockerfile` Służy do określania kontener, którego podstawowy, który będzie używany, i konfiguracji aplikacji w nim. `Web`" `Dockerfile`:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
WORKDIR /app

COPY *.sln .
COPY . .
WORKDIR /app/src/Web
RUN dotnet restore

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS runtime
WORKDIR /app
COPY --from=build /app/src/Web/out ./

# Optional: Set this here if not setting it from docker-compose.yml
# ENV ASPNETCORE_ENVIRONMENT Development

ENTRYPOINT ["dotnet", "Web.dll"]
```

### <a name="troubleshooting-docker-problems"></a>Rozwiązywanie problemów z platformy Docker

Po jego uruchomieniu konteneryzowanej aplikacji będzie nadal działać, dopóki nie zostanie zatrzymana. Można wyświetlić, kontenery, które działają z `docker ps` polecenia. Można zatrzymać działający kontener za pomocą `docker stop` polecenia i określając identyfikator kontenera.

Należy pamiętać, że uruchamianie kontenerów platformy Docker może być powiązany z portów, które w przeciwnym razie spróbuj do użycia w środowisku programistycznym. Jeśli spróbujesz uruchomić ani debugować aplikację jako działający kontener platformy Docker przy użyciu tego samego portu, zostanie wyświetlony komunikat o błędzie informujący, że serwer nie może utworzyć powiązanie do tego portu. Jeszcze raz zatrzymywanie kontenera powinno rozwiązać problem.

Jeśli chcesz dodać obsługę platformy Docker do aplikacji za pomocą programu Visual Studio, upewnij się, że pulpitu platformy Docker jest uruchomiona, po wykonaniu tej czynności. Kreator nie będzie działać poprawnie, jeśli pulpitu platformy Docker nie jest uruchomiona, po uruchomieniu kreatora. Ponadto Kreator sprawdza, czy bieżący wybór kontenera można dodać poprawną obsługę platformy Docker. Aby dodać obsługę kontenerów Windows, musisz uruchomić kreatora, gdy masz pulpitu platformy Docker z kontenerów Windows skonfigurowany. Jeśli chcesz dodać obsługę kontenerów systemu Linux, uruchom kreatora, gdy masz platformy Docker z kontenerów systemu Linux skonfigurowany.

### <a name="references--common-web-architectures"></a>Odwołania — typowych architektur w sieci web
> - **Wyczyść architektury**  
>   <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
> - **Architektura przenikanie**  
>   <https://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
> - **Wzorzec repozytorium**  
>   <https://deviq.com/repository-pattern/>
> - **Przykładowe rozwiązanie czystej architektury**  
>   <https://github.com/ardalis/cleanarchitecture>
> - **Projektowanie Mikrousług książki elektronicznej**  
>   <https://aka.ms/MicroservicesEbook>

>[!div class="step-by-step"]
>[Poprzednie](architectural-principles.md)
>[dalej](common-client-side-web-technologies.md)
