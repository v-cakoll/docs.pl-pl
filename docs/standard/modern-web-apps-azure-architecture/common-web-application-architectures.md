---
title: Typowe architekturach aplikacji sieci web
description: Projektowania nowoczesnych aplikacji sieci web platformy ASP.NET Core i Microsoft Azure | Typowe architekturach aplikacji sieci web
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dc5580d38ac29a5e923a4b7d84f9d7e077d5cdb2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
#<a name="common-web-application-architectures"></a>Typowe architekturach aplikacji sieci Web

> "Jeśli uważasz, że architektura dobrej jest kosztowna, spróbuj zły architektury".  
> _-Brianowi Środkowa i Joseph Yoder_

## <a name="summary"></a>Podsumowanie

Najbardziej tradycyjne aplikacje .NET są wdrażane jako sztuk odpowiadający plik wykonywalny lub aplikacja sieci web jednej wewnątrz jednej appdomain usług IIS. To jest najprostszym modelem wdrożenia i bardzo dobrze służy wiele aplikacji wewnętrznych i mniejszych publicznego. Jednak najbardziej nieuproszczony aplikacji biznesowych nawet podana tego pojedynczą jednostkę wdrożenia, korzystać z niektórych separacji logicznej do kilku warstw.

## <a name="what-is-a-monolithic-application"></a>Co to jest wbudowanymi aplikacji?

Wbudowanymi aplikacji to taki, który jest całkowicie niezależne pod względem jego zachowania. Może współpracować z innymi magazynami usług lub danych w trakcie wykonywania operacji, ale podstawowe jego działania jest uruchamiany w ramach własnym procesie i całej aplikacji jest zwykle wdrażane jako pojedyncza jednostka. Jeśli takiej aplikacji musi skalowanie w poziomie, zwykle całej aplikacji jest zduplikowany w wielu serwerów lub maszyn wirtualnych.

## <a name="all-in-one-applications"></a>Aplikacje w jednym

Najmniejsza liczba projektów dla architektury aplikacji jest jednym. W ramach tej architektury całą logikę aplikacji jest zawarty w jednym projekcie skompilowany w jednym zestawie i wdrożony jako pojedyncza jednostka.

Nowy projekt platformy ASP.NET Core, czy utworzono w programie Visual Studio lub z wiersza polecenia, rozpoczyna się jako proste monolityczna "wszystkie w jednym". Zawiera wszystkie zachowania aplikacji, w tym logika dostępu do prezentacji, biznesowych i danych. Struktura pliku aplikacji pojedynczych projektów przedstawiono na rysunku 5-1.

**Rysunek 5-1.** Jeden projekt aplikacji platformy ASP.NET Core

![](./media/image5-1.png)

W przypadku pojedynczego projektu separacji odbywa się przy użyciu folderów. Szablon domyślny zawiera osobne foldery dla obowiązki wzorzec MVC modele, widoki i kontrolery, a także dodatkowe foldery dla danych i usług. W tym przypadku prezentacji szczegóły powinny być ograniczone największego możliwego do folderu widoki i szczegóły implementacji danych dostęp powinien być ograniczony do klasy znajdującej się w folderze z danymi. Logika biznesowa powinien znajdować się w usługach i klas w ramach folderu modeli.

Mimo że jest to prosty, rozwiązanie wbudowanymi pojedynczych projektów ma niektóre wady. Wraz z rozwojem rozmiar i złożoność projektu, liczbę plików i folderów będzie również powiększania. Dotyczy interfejsu użytkownika (modele, widoki, kontrolery) znajdują się w wielu folderów, które nie są grupowane razem alfabetycznie. Ten problem tylko pobiera pogarsza się wraz z po dodaniu dodatkowych konstrukcje poziomu interfejsu użytkownika, takie jak filtry lub ModelBinders, w swoich własnych folderów. Reguły biznesowe są rozproszone między folderami modeli i usług, i nie ma żadnych jednoznacznie zidentyfikować, którego klas w foldery, które powinny są zależne od które. Ten brak organizacji na poziomie projektu często prowadzi do [kod postaci spaghetti](http://deviq.com/spaghetti-code/).

W celu rozwiązania tych problemów, aplikacje często rozwijać do rozwiązań dotyczących wielu projektów, gdzie każdy projekt jest uznawany za znajdują się w szczególności *warstwy* aplikacji.

## <a name="what-are-layers"></a>Co to są warstwy?

Wzrostem aplikacji złożonością jednym ze sposobów zarządzać tym złożoności ma podzielić aplikacji zgodnie z jego obowiązki lub problemy. Następuje rozdzielenie zasady problemy i zabezpieczyć rosnącym codebase organizacji, dzięki czemu deweloperzy mogą łatwiej znaleźć którym zaimplementowano niektórych funkcji. Warstwowa architektura oferuje wiele zalet poza tylko kod organizacji, mimo że.

Poprzez organizowanie kodu do warstwy, często używane funkcje niższego poziomu mogą być ponownie używane w całej aplikacji. Ta ponownemu jest korzystne, ponieważ oznacza to, że trzeba napisać mniejsza ilość kodu i umożliwia aplikacji normalizacji w pojedynczej implementacji, zgodnie z zasadą suchej.

Z architekturą warstwowych aplikacje można wymuszać ograniczenia, na których warstwy może komunikować się z innych warstw. Pozwala to osiągnąć hermetyzacji. Podczas zmiany warstwy lub zastąpione, powinny mieć wpływ na tylko warstwy, które współpracują z nim. Poprzez ograniczenie, które warstwy zależą od, na których można zminimalizować innych warstw wpływ zmian, aby pojedynczej zmiany bez wpływu na całej aplikacji.

Warstwy (i encapsulation) ułatwiają znacznie Zastąp funkcjonalności aplikacji. Na przykład aplikacja trwałości początkowo użyć własną bazę danych programu SQL Server, ale później można użyć strategii opartej na chmurze trwałości lub jeden za interfejsu API sieci web. Jeśli aplikacja ma prawidłowo hermetyzowany jej implementacja trwałości w ramach logicznego warstwy, tej warstwy określonego programu SQL Server może zostać zastąpiona nową wykonania tego samego interfejsu publicznego.

Oprócz możliwości wymienić implementacji w odpowiedzi na przyszłe zmiany wymagań dotyczących warstwy aplikacji może również ułatwić wymienić implementacje do celów testowych. Nie trzeba napisać testy, które pracują z warstwy danych rzeczywistych lub interfejsu użytkownika aplikacji, tych warstw może zastąpione w czasie testu fałszywych implementacje, które zapewniają znane odpowiedzi na żądania. To zwykle sprawia, że testy znacznie łatwiejsze do zapisu i znacznie szybsze uruchamianie w porównaniu do uruchomienia testów ponownie rzeczywistych infrastruktury aplikacji.

Logiczne Tworzenie warstw to technika typowe dla poprawy organizacji kodu w aplikacjach dla przedsiębiorstw oprogramowania, a istnieje kilka sposobów, w których kodu można organizować w warstwy.

> [!NOTE]
> *Warstwy* reprezentują separacji logicznej w aplikacji. W przypadku, gdy logiki aplikacji jest fizycznie rozproszone na oddzielnych serwerach lub procesy, te cele oddzielne fizyczne wdrożenia są określane jako *warstw*. Jest to możliwe i dość często, aby korzystać z aplikacji N warstwy, która została wdrożona w pojedynczej warstwie.

## <a name="traditional-n-layer-architecture-applications"></a>Tradycyjne aplikacje architektury "N warstwy"

Najbardziej typowe organizacji aplikacji logiki do warstwy go pokazano na rysunku 5-2.

**Rysunek 5-2.** Typowa aplikacja warstwy.

![](./media/image5-2.png)

Te warstwy interfejsu użytkownika, są często skrót logiki warstwy Biznesowej (warstwy logiki biznesowej) i warstwy DAL (Warstwa dostępu do danych). Przy użyciu tej architektury, użytkownikom wysyłanie żądań za pośrednictwem warstwy interfejsu użytkownika, która współdziała tylko z logiki warstwy Biznesowej. Logiki warstwy Biznesowej, z kolei może wywołać warstwy DAL dla żądań dostępu do danych. Warstwy interfejsu użytkownika, nie należy wprowadzać żadnych żądań z warstwą dal bezpośrednio, ani powinien interakcję z trwałości bezpośrednio w inny sposób. Podobnie logiki warstwy Biznesowej powinien komunikować się tylko z trwałości za pośrednictwem warstwy DAL. Dzięki temu każda warstwa ma własną odpowiedzialność dobrze znane.

Jeden wadą tego rozwiązania tradycyjnych Tworzenie warstw jest uruchamianie zależności kompilacji od góry do dołu. Oznacza to, że warstwy interfejsu użytkownika zależy od logiki warstwy Biznesowej, która jest zależna od warstwy DAL. Oznacza to, że logiki warstwy Biznesowej, zawierający zwykle najważniejszych logikę w aplikacji, ma zależnych na szczegóły implementacji dostępu do danych (i często na istnienie bazy danych). Testowanie logiki biznesowej w takich architektura często jest trudne i wymaga testowej bazy danych. Zasada odwracanie zależności może służyć do rozwiązania tego problemu, zobaczysz w następnej sekcji.

Rysunek 5-3 pokazano, dzielenie aplikacji na trzy projekty odpowiedzialność (lub layer).

**Rysunek 5-3.** Prostą aplikację wbudowanymi z trzy projekty.

![](./media/image5-3.png)

Mimo że ta aplikacja używa kilku projektów na potrzeby organizacyjne, nadal jest wdrożona jako pojedyncza jednostka i klientów będzie korzystać z niego jako aplikacji sieci web jednej. Dzięki temu proces wdrażania bardzo proste. Rysunek 5-4 przedstawia sposób takich aplikacji może być hostowany przy użyciu systemu Windows Azure.

![](./media/image5-4.png)

**Rysunek 5-4.** Proste wdrożenie aplikacji sieci Web Azure

Jak aplikacja wymaga powiększania, bardziej złożone i niezawodne rozwiązania wdrożenia może być wymagane. Rysunek 5-5 przedstawiono przykład bardziej złożonych plan wdrożenia, który obsługuje dodatkowe funkcje.

![](./media/image5-5.png)

**Rysunek 5-5.** Wdrażanie aplikacji sieci web w usłudze Azure App Service

Wewnętrznie tego projektu organizacji do wielu projektów opartych na odpowiedzialność zwiększa łatwość konserwacji aplikacji.

Ta jednostka można skalować w górę lub w poziomie przeprowadzać oparte na chmurze skalowalności na żądanie. Skalowanie w oznacza dodanie dodatkowych procesora CPU, pamięci, miejsca na dysku lub innych zasobów na serwery hosting aplikacji. Skalowanie w poziomie oznacza, że dodawanie dodatkowe wystąpienia takich serwerów, czy są to serwerów fizycznych lub maszynach wirtualnych. Kiedy aplikacja znajduje się w wielu wystąpieniach, usługi równoważenia obciążenia jest używana do przypisywania żądania wystąpień poszczególnych aplikacji.

Najprostsza metoda skalowanie aplikacji sieci web na platformie Azure jest konfigurowanie skalowania ręcznie w planie usługi aplikacji w aplikacji. Rysunek 5 i 6-Pokaż ekran odpowiednie pulpitu nawigacyjnego platformy Azure do skonfigurowania służy liczbę wystąpień aplikacji.

![](./media/image5-6.png)

**Rysunek 5-6.** Plan usługi App Service skalowanie na platformie Azure.

## <a name="clean-architecture"></a>Architektura czyste

Zwykle aplikacje, które postępuj zgodnie z zasadą odwracanie zależności, a także zasady Domain-Driven projektu (DDD) na podobną architekturę. Taka architektura został przekazany przez wiele nazw latach. Jeden z imiona jest gniazdo sześciokątne architektury, następuje portów i karty. Niedawno, jest ono cytowane jako [architektura przenikanie](http://jeffreypalermo.com/blog/the-onion-architecture-part-1/) lub [czystej architektury](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). Jest to nazwa ostatniego czystą architektury, która jest używana jako podstawa dla opisu architektury w Książka elektroniczna.

> [!NOTE]
> Określenie czystej architektury może odnosić się do aplikacji, które są tworzone przy użyciu zasad DDD, jak również do tych, które nie zostały skompilowane przy użyciu DDD. W przypadku pierwszej, ta kombinacja może określane jako "Czystej architektury DDD".

Architektura czystą umieszcza modelu logiki i aplikacji biznesowych w Centrum aplikacji. Zamiast logiki biznesowej, które są zależne od dostęp do danych lub inne problemy infrastruktury jest odwrócony tej zależności: szczegóły infrastruktury i implementacji są zależne od podstawowej aplikacji. Jest to osiągane przez zdefiniowanie abstrakcje lub interfejsów w podstawowej aplikacji, które następnie są implementowane przez typy zdefiniowane w warstwie infrastrukturze. Typowy sposób przedstawiania tej architektury jest szereg koncentrycznych, podobnie jak przenikanie. Rysunek 5 X przedstawiono przykład tego stylu reprezentacja architektury.

![](./media/image5-7.png)

**Rysunek 5-7.** Czystej architektury; przenikanie widoku

Na tym diagramie zależności przepływać kierunku najbardziej okręgu. W związku z tym widać, że podstawowe aplikacji (przyjmująca nazwy z jego położenie fundament ten diagram) nie ma żadnych zależności na inne warstwy aplikacji. W bardzo center są jednostek i interfejsów aplikacji. Tylko poza, ale nadal w podstawowej aplikacji są domeny usług, które zwykle implementować interfejsów zdefiniowane w wewnętrznym okręgu. Poza rdzeniem aplikacji zarówno w interfejsie użytkownika, jak i warstwy infrastruktury zależą od Core aplikacji, ale nie na siebie (niekoniecznie).

Rysunek 5 X zawiera bardziej tradycyjnej diagramu warstwy w poziomie, który lepiej odzwierciedla zależność między interfejsu użytkownika i innych warstw.

![](./media/image5-8.png)

**Rysunek 5 – 8.** Czystej architektury; Widok warstwy w poziomie

Należy pamiętać, że stałe strzałki reprezentują zależności kompilacji podczas przerywaną strzałką reprezentuje zależność tylko do środowiska wykonawczego. Używanie czystej architektury, warstwy interfejsu użytkownika działa z interfejsami zdefiniowane w podstawowej aplikacji w czasie kompilacji, a w idealnym przypadku należy znać typów wdrożenia zdefiniowano w warstwie infrastrukturze. W czasie wykonywania jednak te typy wdrożenia będzie wymagane dla aplikacji, które można wykonać, więc muszą być obecne i przewodowej do interfejsów podstawowych aplikacji za pomocą iniekcji zależności.

Rysunek 5 – 9 przedstawiono bardziej szczegółowe architektury aplikacji platformy ASP.NET Core podczas tworzenia następujących te zalecenia.

![Architektura Core ASPNET](./media/image5-9.png)

**Rysunek 5 – 9.** Diagram architektury platformy ASP.NET Core następującego czystej architektury.

Ponieważ Core aplikacji nie są zależne od infrastruktury, jest bardzo proste do pisania testów jednostkowych automatycznych dla tej warstwy. Rysunki 5 – 10 i 5 11 pokazać, jak testy mieści się w tej architekturze.

![UnitTestCore](./media/image5-10.png)

**Rysunek 5-10.** Jednostka testowania podstawowej aplikacji w izolacji.

![IntegrationTests](./media/image5-11.png)

**Rysunek 5-11.** Testowanie integracji, implementacje infrastruktury z zależnościami zewnętrznymi.

Ponieważ warstwy interfejsu użytkownika nie ma żadnych zależności bezpośrednich dla typów zdefiniowanych w projekcie infrastruktury, również jest bardzo proste wymiany implementacji, albo w celu ułatwienia testowania lub w odpowiedzi na zmieniające się wymagania aplikacji. Wbudowane korzystanie z platformy ASP.NET Core i pomoc techniczna dla iniekcji zależności sprawia, że tej architektury najbardziej stosownego sposobu struktury nieuproszczony wbudowanymi aplikacjami.

Dla aplikacji wbudowanymi projektów aplikacji Core, infrastruktury i interfejs użytkownika są wszystkie Uruchom jako pojedynczej aplikacji. Architektura środowiska uruchomieniowego może wyglądać podobnie jak rysunek 5 – 12.

![Architektura Core ASPNET 2](./media/image5-12.png)

**Rysunek 5 – 12.** Architektura środowiska uruchomieniowego przykładowej aplikacji platformy ASP.NET Core.

### <a name="organizing-code-in-clean-architecture"></a>Organizowanie kodu w czystej architektury

W rozwiązaniu czystej architektury każdy projekt ma wyczyść obowiązki. Tak niektóre typy będą należeć w każdym projekcie i często znajdują się foldery odpowiadający tych typów w projekcie odpowiednich.

Podstawowe aplikacji przechowuje modelu biznesowej, w tym jednostki, usług i interfejsów. Te interfejsy zawierają obiektów abstrakcyjnych odpowiadających operacje, które będą wykonywane przy użyciu infrastruktury, takich jak dostęp do danych, dostępu do systemu plików, połączeń sieciowych, itp. Czasami usług lub interfejsów zdefiniowanych w tej warstwie będzie konieczna współpraca z innego niż jednostka typów, które mają nie zależne od infrastruktury i interfejsu użytkownika. Te można zdefiniować jako proste przenieść obiekty danych (DTOs).

> ### <a name="application-core-types"></a>Typy podstawowe aplikacji
> -   Jednostek (business modelu klasy, które są zachowywane)
> -   Interfejsy
> -   Usługi
> -   DTOs

Projekt infrastruktury zazwyczaj uwzględnia implementacje dostępu do danych. W typowej aplikacji sieci web platformy ASP.NET Core to obejmować Entity Framework DbContext, wszelkie migracje Core EF, które zostały zdefiniowane i klasy implementacji dostępu do danych. Jest najczęściej abstrakcji kod implementacji dostępu do danych za pośrednictwem [wzorca projektowego repozytorium](http://deviq.com/repository-pattern/).

Oprócz implementacji dostępu do danych projektu infrastruktury powinien zawierać implementacje usług, które musi współdziałać z zastrzeżenia co do infrastruktury. Te usługi powinny implementować interfejsów zdefiniowanych w podstawowej aplikacji, a więc infrastruktury powinny mieć odwołanie do projektu aplikacji Core.

> ### <a name="infrastructure-types"></a>Typy infrastruktury
> -   Typy podstawowe EF (DbContext, migracje)
> -   Typy wdrożenia (repozytoria) dostępu do danych
> -   Usługi specyficzne dla infrastruktury (FileLogger, SmtpNotifier itp.)

Warstwę interfejsu użytkownika w aplikacji platformy ASP.NET Core MVC będzie punkt wejścia dla aplikacji, a musi być projekt platformy ASP.NET Core MVC. Ten projekt powinien odwołania do projektu aplikacji rdzeni i jego typów powinien Praca z infrastruktury wyłącznie za pośrednictwem interfejsów zdefiniowanych w aplikacji Core. Nie bezpośrednie tworzenie wystąpienia elementu (lub statyczne wywołania) powinno być dozwolone typy warstwę infrastruktury warstwy interfejsu użytkownika.

> ### <a name="ui-layer-types"></a>Typy warstwy interfejsu użytkownika
> -   Kontrolery
> -   Filtry
> -   Widoki
> -   ViewModels
> -   Uruchamianie

Klasa początkowa jest odpowiedzialny za konfigurowanie aplikacji i okablowania typów implementacji interfejsów, dzięki czemu iniekcji zależności do poprawnego działania w czasie wykonywania.

> [!NOTE]
> Aby okablować się iniekcji zależności w ConfigureServices w pliku Startup.cs projektu interfejsu użytkownika, projekt może być konieczne odwołania do projektu infrastruktury. Ta zależność mogą zostać usunięte, najłatwiej przy użyciu niestandardowych kontenera Podpisane. Na potrzeby tego przykładu najprostsza metoda jest umożliwienie projekt interfejsu użytkownika do odwołania do projektu infrastruktury.

## <a name="monolithic-applications-and-containers"></a>Wbudowanymi aplikacjami i kontenerów 

Można utworzyć jedno- i wbudowanymi wdrożenia aplikacji sieci Web lub usługi i wdróż je jako kontener. W aplikacji może nie być wbudowanymi, ale organizowane w kilku bibliotek, składniki lub warstwy. Zewnętrznie jest jeden kontener jednego procesu, aplikacji sieci web jednej lub pojedynczą usługę.

Aby zarządzać tego modelu, możesz wdrożyć jeden kontener do reprezentowania aplikacji. Aby skalować, wystarczy dodać dodatkowe kopie z modułem równoważenia obciążenia z przodu. Łatwość pochodzi z zarządzania pojedynczego wdrożenia w jeden kontener lub maszyny Wirtualnej.

![](./media/image5-13.png)

Jak pokazano na rysunku 5 X może zawierać wiele składników/biblioteki lub wewnętrzny warstw w ramach każdego kontenera. Jednak po podmiot zabezpieczeń kontenera *"kontener nie rzecz i jest w jednym procesie*", wbudowanymi wzorzec może być konflikt.

Wadą interfejsu tego podejścia jest dostarczany, jeśli/podczas rozwoju aplikacji wymaganiem go do skalowania. W przypadku zmiany skali całej aplikacji nie jest naprawdę problem. Jednak w większości przypadków kilka części aplikacji są punkty urządzenie rozruchowe wymagające skalowania, podczas gdy inne składniki są używane mniejsze.

W przykładzie typowe handlu elektronicznego; prawdopodobnie potrzebnych do skalowania jest składnikiem informacji produktu. Wielu klientów więcej Przeglądanie produktów, niż ich zakupu. Więcej klientów użyj koszyka niż używanie potoku płatności. Mniejszą liczbę klientów Dodawanie komentarzy i wyświetlanie ich historii zakupów. I prawdopodobnie masz tylko grupy pracowników w pojedynczym regionie, które są potrzebne do zarządzania zawartością i kampanii marketingowych. Przez skalowanie wbudowanymi projektu, całego kodu jest wdrażany wiele razy.

Oprócz skali problem, wszystkie zmiany pojedynczego składnika wymagają pełne ponowne całej aplikacji i pełne ponowne wdrożenie wszystkich wystąpień.

W wielu organizacjach są programowania z użyciem tej architektury rozwiązania i wbudowanymi podejście jest. Wiele występują dobre za mało wyników, podczas gdy inne czy osiągnięto limity. Wiele zaprojektowane swoich aplikacji, w tym modelu ponieważ infrastruktura i narzędzia było zbyt trudne do kompilacji na usługach architektury (SOA) i dopóki aplikacja zwiększył nie zobaczy konieczność —. Jeśli okaże się, że jest naciśnięcie limity wbudowanymi podejścia podzielenie aplikacji, aby umożliwić lepsze wykorzystanie kontenerów i mikrousług może być następnego kroku logiczne.

![](./media/image5-14.png)

Wdrażanie aplikacji wbudowanymi na platformie Microsoft Azure można osiągnąć za pomocą dedykowanych maszyn wirtualnych dla poszczególnych wystąpień. Przy użyciu [zestawy skalowania maszyny Wirtualnej Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), można łatwo skalować maszyn wirtualnych. [Usługa Azure App Service](https://azure.microsoft.com/services/app-service/) można uruchamiać aplikacje wbudowanymi i łatwego skalowania wystąpienia bez konieczności zarządzania maszynami wirtualnymi. Usługa Azure App Service można uruchomić pojedynczego wystąpienia Docker kontenerów, jak również uprościć wdrażanie. Przy użyciu rozwiązania Docker, można wdrożyć jeden maszynę Wirtualną jako hosta Docker i uruchomić wiele wystąpień. Przy użyciu równoważenia Azure, jak pokazano w rysunek 5-14, można zarządzać skalowania.

Wdrożenia na różnych hostach można zarządzać za pomocą techniki tradycyjnego wdrażania. Hostach Docker można zarządzać za pomocą poleceń, takich jak **docker Uruchom** wykonać ręcznie lub za pomocą automatyzacji, takie jak potoków ciągłego dostarczania (CD).

### <a name="monolithic-application-deployed-as-a-container"></a>Wbudowanymi aplikacji wdrożonych jako kontener

Istnieją korzyści kontenery Zarządzaj wdrożeniami aplikacji wbudowanymi. Skalowanie wystąpienia kontenery jest znacznie szybsze i łatwiejsze niż wdrażanie dodatkowych maszyn wirtualnych. Nawet w przypadku używania zestawy skalowania maszyny Wirtualnej do skalowania maszyn wirtualnych, ich trwać do wystąpienia. Po wdrożeniu jako wystąpienia aplikacji Konfiguracja aplikacji jest zarządzana w ramach maszyny wirtualnej.

Wdrażanie aktualizacji, jak obrazy usługi Docker jest znacznie szybsze i wydajność sieci. Obrazy usługi docker zazwyczaj rozpoczyna się w sekundach, przyspieszania wdrożeniach. Przerwanie w dół wystąpienia Docker jest tak proste, jak wystawianie **docker stop** polecenia zwykle kończonych w mniej niż 1 sekunda.

Jak kontenery są z założenia niezmienne zgodnie z projektem, nigdy nie musisz martwić uszkodzony maszyn wirtualnych, natomiast skryptów aktualizacji może zapomnij konta dla niektórych określonej konfiguracji lub w lewo pliku na dysku.

Wbudowanymi aplikacje mogą korzystać z Docker podzielenie wbudowanymi aplikacji w systemach sub, które mogą być skalowane, opracowany i wdrażane pojedynczo może być punktem wejścia do obszaru z mikrousług.

> ### <a name="references--common-web-architectures"></a>Odwołania — typowe architektury sieci Web
> - **Architektura czyste**  
> <https://8thlight.com/blog/uncle-Bob/2012/08/13/the-clean-Architecture.HTML>
> - **Architektura przenikanie**  
> <http://jeffreypalermo.com/blog/the-onion-Architecture-Part-1/>
> - **Wzorzec repozytorium**  
> <http://deviq.com/Repository-pattern/>
> - **Przykładowe rozwiązanie czystej architektury**  
> <https://github.com/ardalis/cleanarchitecture>
> - **Zaprojektowanie Mikrousług e-book** <http://aka.ms/MicroservicesEbook>

>[!div class="step-by-step"]
[Poprzednie] (architektury principles.md) [dalej] (typowe klienta-po stronie web-technologies.md)
