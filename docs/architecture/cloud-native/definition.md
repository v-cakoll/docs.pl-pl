---
title: Definiowanie rozwiązań natywnych dla chmury
description: Poznaj filary podstawowe, które zapewniają nimi dla systemów natywnych w chmurze
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: ba11cb1cf0d9d7ef9734ad49aee1df22f285fc4c
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199784"
---
# <a name="defining-cloud-native"></a>Definiowanie natywnego chmury

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Zatrzymywanie czynności i tekstu dziesięciu współpracowników. Poproś ich o zdefiniowanie terminu "natywne w chmurze". Z pewnością uzyskasz osiem różnych odpowiedzi.

W chmurze wszystkie informacje na temat zmieniania sposobu konstruowania krytycznych systemów firmy.

Systemy natywne w chmurze zostały zaprojektowane w celu przeprowadzenia szybkiej zmiany, dużej skali i odporności.

Natywna platforma obliczeniowa w chmurze zapewnia [oficjalną definicję](https://github.com/cncf/foundation/blob/master/charter.md):

> *Technologie natywne w chmurze umożliwiają organizacjom tworzenie i uruchamianie skalowalnych aplikacji w nowoczesnych, dynamicznych środowiskach, takich jak chmury publiczne, prywatne i hybrydowe. Kontenery, siatki usług, mikrousługi, niezmienne infrastruktury i deklaracyjne interfejsy API exemplify te podejście.*

> *Techniki te umożliwiają swobodnie sprzężone systemy, które są odporne, zarządzane i zauważalne. W połączeniu z niezawodną automatyzacją pozwalają inżynierom wprowadzać zmiany o dużym wpływie i przewidzieć je w minimalnym stopniu Toil.*

Aplikacje stają się coraz bardziej skomplikowane z użytkownikami wymagającymi więcej i więcej. Użytkownicy oczekują szybkiego reagowania, innowacyjnych funkcji i zerowego przestoju. Problemy z wydajnością, błędy cykliczne i niezdolność do przenoszenia szybko nie są już akceptowalne. Użytkownicy będą mogli w łatwy sposób przejść do konkurencji.

Natywna Chmura zapewnia dużą *szybkość* i *elastyczność*. Systemy biznesowe są rozwijane z możliwością korzystania z funkcji firmy w celu wyróżnienia strategii strategicznej, przyspieszania i zwiększania szybkości działania firmy. Koniecznie należy natychmiast uzyskać pomysły na rynek.

Oto kilka firm, które wdrożyły te techniki. Pomyśl o szybkości, elastyczności i skalowalności, które zostały osiągnięte.

| Firma | Środowisko użytkownika |
| :-------- | :-------- |
| [Netflix](https://www.infoq.com/news/2013/06/netflix/) | Ma ponad 600 usług w środowisku produkcyjnym. Wdraża setki razy dziennie. |
| [Uber](https://eng.uber.com/micro-deploy/) | Ma 1000 usług przechowywanych w środowisku produkcyjnym. Wdraża kilka tysięcy kompilacji w każdym tygodniu. |
| [WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf) | Obejmuje 300 usług w środowisku produkcyjnym. Wykonuje niemal 1 000 zmian dziennie. |

Jak widzisz, Netflix, Uber i WeChat uwidaczniają systemy, które składają się z setek niezależnych mikrousług. Ten styl architektoniczny umożliwia im szybkie reagowanie na warunki rynkowe. Mogą natychmiast aktualizować małe obszary aplikacji działającej na żywo, złożonej i indywidualnie skalować te obszary zgodnie z wymaganiami.

Szybkość i elastyczność natywnych postanowień w chmurze na podstawie różnych czynników. Na przedniej rolę infrastruktury chmurowej. Pięć dodatkowych filarów podstawowych przedstawionych na rysunku 1-3 udostępnia również nimi dla systemów natywnych w chmurze.

![Natywne filary w chmurze](./media/cloud-native-foundational-pillars.png)

**Rysunek 1-3**. Natywne filary w chmurze

Poświęć trochę czasu, aby lepiej zrozumieć znaczenie każdego filaru.

## <a name="the-cloud"></a>Chmura...

Systemy natywne w chmurze w pełni wykorzystują model usługi w chmurze.

Systemy, które zaprojektowano w celu rozbudowania w dynamicznym, zwirtualizowanym środowisku chmurowym, umożliwiają rozległe wykorzystanie infrastruktury obliczeniowej [platformy jako usługi (PaaS)](https://azure.microsoft.com/overview/what-is-paas/) i usług zarządzanych. Potraktują podstawową infrastrukturę jako *jednorazową* i w ciągu kilku minut, przeskalowane, przenoszone lub zniszczone na żądanie — za pośrednictwem automatyzacji.

Rozważmy powszechnie zaakceptowaną koncepcję DevOps [zwierząt domowych a bydłem](https://medium.com/@Joachim8675309/devops-concepts-pets-vs-cattle-2380b5aab313). W tradycyjnym centrum danych serwery są traktowane jako *zwierzęta domowe*: maszyna fizyczna, z uwzględnieniem zrozumiałej nazwy i jej stanowiska. Możesz skalować, dodając więcej zasobów do tego samego komputera (skalowanie w górę). Jeśli serwer stanie się chory, użytkownik zostanie powracał do kondycji. Czy serwer stanie się niedostępny, wszystkie powiadomienia.

Model usługi *bydła* jest inny. Każde wystąpienie jest inicjowane w ramach maszyny wirtualnej lub kontenera. Są one identyczne i mają przypisane identyfikatory systemu, takie jak Service-01, Service-02 i tak dalej. Skalowanie następuje przez utworzenie większej liczby z nich (skalowanie w poziomie). Gdy jedna z nich jest niedostępna, nikt nie zauważy.

Model bydła obejmuje *niezmienne infrastruktury*. Serwery nie są naprawiane ani modyfikowane. Jeśli jeden z nich ulegnie awarii lub wymaga aktualizacji, zostanie zniszczony i zostanie zainicjowana Nowa obsługa administracyjna — wszystko to wykonywane za pośrednictwem automatyzacji.

Systemy natywne w chmurze uwzględniają model usługi bydła. Są one nadal uruchamiane, ponieważ infrastruktura jest skalowana lub wypada bez względu na maszyny, na których są uruchomione.

Platforma Azure Cloud Platform obsługuje ten typ wysoce elastycznej infrastruktury z automatycznym skalowaniem, samonaprawianiem i możliwościami monitorowania.

## <a name="modern-design"></a>Nowoczesny projekt

Jak można zaprojektować aplikację natywną w chmurze? Jak będzie wyglądać Twoja architektura? Do jakich zasad, wzorców i najlepszych rozwiązań będzie się przestrzegać? Jakie kwestie dotyczące infrastruktury i działania są ważne?

### <a name="the-twelve-factor-application"></a>Aplikacja 12-czynnikowa

Powszechnie zaakceptowaną metodologią konstruowania aplikacji opartych na chmurze jest [aplikacja 12-Factor](https://12factor.net/). Opisano w nim zestaw zasad i praktyk, które deweloperzy obserwują w celu konstruowania aplikacji zoptymalizowanych pod kątem nowoczesnych środowisk chmurowych. Szczególną uwagę można uzyskać w odróżnieniu od środowisk i deklaracyjnej automatyzacji.

W przypadku aplikacji opartych na sieci Web wiele lekarzy traktuje ją jako solidną podstawę do tworzenia aplikacji natywnych w chmurze. Systemy utworzone na podstawie tych zasad mogą szybko wdrażać i skalować funkcje umożliwiające szybkie reagowanie na zmiany rynkowe.

W poniższej tabeli przedstawiono metodologię 12-czynnikową:

|    |  1U | Wyjaśnienie  |
| :-------- | :-------- | :-------- |
| 1 | Baza kodu | Pojedyncza baza kodu dla każdej mikrousługi, przechowywana we własnym repozytorium. Śledzone przy użyciu kontroli wersji, można je wdrożyć w wielu środowiskach (pytań i odpowiedzi, w środowisku produkcyjnym). |
| 2 | Zależności | Każda mikrousługa izoluje i pakuje własne zależności, wdrażając zmiany bez wpływu na cały system. |
| 3 | Konfiguracje  | Informacje o konfiguracji są przenoszone z mikrousługi i zewnętrznie za pomocą narzędzia do zarządzania konfiguracją poza kodem. To samo wdrożenie może być propagowane między środowiskami przy użyciu poprawnej konfiguracji.  |
| 4 | Usługi zapasowe | Zasoby pomocnicze (magazyny danych, pamięci podręczne, brokery komunikatów) powinny być udostępniane za pośrednictwem adresu URL z adresami. W ten sposób można oddzielić zasób od aplikacji, umożliwiając jego zmianę.  |
| 5 | Kompilacja, wydanie, uruchomienie | Każda wersja musi wymusić ścisłe oddzielenie między kompilacją, wydaniem i etapami uruchamiania. Każdy z nich powinien być oznaczony unikatowym IDENTYFIKATORem i obsługiwać możliwość wycofywania. Nowoczesne systemy ciągłej integracji/ciągłego wdrażania pomagają spełnić tę zasadę. |
| 6 | Procesy | Każda mikrousługa powinna być wykonywana we własnym procesie, odizolowana od innych uruchomionych usług. Externalize stan wymagany do usługi zapasowej, na przykład rozproszonej pamięci podręcznej lub magazynu danych. |
| 7 | Powiązanie portu | Każda mikrousługa powinna być samodzielna z interfejsami i funkcjami udostępnianymi na własnym porcie. To zapewnia izolację z innych mikrousług. |
| 8 | Współbieżność | Usługi są skalowane w ramach dużej liczby niewielkich identycznych procesów (kopii), a nie do skalowania pojedynczego dużego wystąpienia na najbardziej wydajny dostępnym komputerze. |
| 9 | Disposability | Wystąpienia usługi powinny być jednorazowe, dzięki czemu można uzyskać szybkie uruchomienia w celu zwiększenia możliwości skalowalności i bezpiecznego zamykania systemu, aby pozostawić system w prawidłowym stanie. Kontenery platformy Docker wraz z koordynatorem są niezgodne z tym wymaganiem. |
| 10 | Tworzenie i produkcja — parzystość | Przechowuj środowiska w całym cyklu życia aplikacji tak jak to możliwe, unikając kosztownych skrótów. W tym miejscu wdrażanie kontenerów może znacznie przyczynić się przez promowanie tego samego środowiska wykonawczego. |
| 11 | Rejestrowanie | Traktuj dzienniki generowane przez mikrousługi jako strumienie zdarzeń. Przetwarzaj je za pomocą agregatora zdarzeń i Propaguj dane do narzędzi do zarządzania danymi/dziennika, takich jak Azure Monitor lub Splunk i ostatecznie długoterminowe archiwizowanie. |
| 12 | Procesy administracyjne | Uruchamiaj zadania administracyjne/Zarządzanie jako procesy jednorazowe. Zadania mogą obejmować czyszczenie danych i ściąganie analiz dla raportu. Narzędzia wykonujące te zadania powinny być wywoływane ze środowiska produkcyjnego, ale niezależnie od aplikacji. |

W książce [poza aplikacją 12-składnikową](https://content.pivotal.io/blog/beyond-the-twelve-factor-app), autor: Jan Hoffman szczegóły każdego z oryginalnych 12 czynników (napisane w 2011). Ponadto książka zawiera trzy dodatkowe czynniki odzwierciedlające współczesny współczesny projekt aplikacji w chmurze.

|    |  Nowy czynnik | Wyjaśnienie  |
| :-------- | :-------- | :-------- |
| 13 | Najpierw interfejs API | Utwórz wszystko jako usługę. Załóżmy, że kod będzie używany przez klienta frontonu, bramę lub inną usługę. |
| 14 | Telemetria | Na stacji roboczej masz wgląd w aplikację i jej zachowanie. W chmurze nie masz. Upewnij się, że projekt zawiera kolekcję monitorowanie, specyficzne dla domeny i kondycję/dane systemowe. |
| 15 | Uwierzytelnianie/autoryzacja  | Zaimplementuj tożsamość z poziomu uruchomienia. Zapoznaj się z funkcjami [RBAC (kontrola dostępu opartą na rolach)](https://docs.microsoft.com/azure/role-based-access-control/overview) dostępnymi w chmurach publicznych.  |

Odwołujemy się do wielu czynników 12 + w tym rozdziale i w całej książce.

### <a name="critical-design-considerations"></a>Krytyczne zagadnienia dotyczące projektowania

Poza wskazówkami podanymi w ramach metodologii dwunastego czynnika istnieje kilka krytycznych decyzji projektowych, które należy wykonać podczas konstruowania systemów rozproszonych.

*Komunikacja*

Jak aplikacje klienckie frontonu komunikują się z podstawowymi usługami zaplecza. Czy zezwolisz na bezpośrednią komunikację? Lub, może być abstrakcją usług zaplecza z bramą fasady, która zapewnia elastyczność, kontrolę i bezpieczeństwo?

Jak usługa zaplecza będzie komunikować się ze sobą. Czy dozwolone są bezpośrednie wywołania HTTP, które prowadzą do odłączenia i wydajności oraz elastyczność? Lub można rozważyć oddzielenie wiadomości z użyciem technologii kolejkowania i tematów?

Komunikacja obejmuje szczegółowo rozdział 4, *natywne wzorce komunikacji w chmurze*.

*Odporność*

Architektura mikrousług przenosi system z procesu na proces do pozaprocesowej komunikacji sieciowej. Co się stanie w architekturze rozproszonej, co się dzieje, gdy usługa B nie odpowiada na wywołanie sieciowe z usługi A? Lub co się stanie, gdy usługa C stanie się tymczasowo niedostępna, a inne usługi wywołujące ją są blokowane?

Odporność dotyczy szczegółowo rozdziału 6, *odporności natywnej w chmurze*.

*Rozproszone dane*

Zgodnie z projektem każda mikrousług hermetyzuje własne dane, ujawniając operacje za pośrednictwem interfejsu publicznego. Jeśli tak, jak wykonywać zapytania dotyczące danych lub zaimplementować transakcję w wielu usługach?

Dane rozproszone są szczegółowo omówione w rozdziale 5, *wzorce danych w chmurze*.

*Tożsamość*

Jak usługa będzie identyfikować użytkowników, którzy mają do nich dostęp i jakie posiadane uprawnienia?

Tożsamość jest szczegółowo omówione w rozdziale 8, *tożsamość*.

## <a name="microservices"></a>Mikrousługi

Systemy natywne w chmurze uwzględniają mikrousługi, popularny styl architektoniczny służący do konstruowania nowoczesnych aplikacji.

Zbudowany jako rozproszony zestaw małych, niezależnych usług, które współpracują ze wspólną siecią szkieletową, mikrousługi mają następujące cechy:

- Każdy implementuje określoną możliwość biznesową w ramach większego kontekstu domeny.

- Każda z nich jest opracowywana autonomicznie i można ją wdrożyć niezależnie.

- Każda z nich to samodzielna obudowa z technologią magazynowania danych (SQL, NoSQL) i platformą programowania.

- Każda z nich jest uruchamiana we własnym procesie i komunikuje się z innymi osobami przy użyciu standardowych protokołów komunikacyjnych, takich jak HTTP/HTTPS, WebSockets lub [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).

- Składają się one ze sobą, tworząc aplikację.

Rysunek 1-4 kontrast podejścia aplikacji monolitycznej z podejściem mikrousług. Należy zauważyć, jak monolitu składa się ze architektury warstwowej, która jest wykonywana w pojedynczym procesie. Zwykle zużywa relacyjną bazę danych. Podejście mikrousługowe umożliwia jednak segregowanie funkcji w niezależnych usługach obejmujących logikę i dane. Każda mikrousługa hostuje swój własny magazyn danych.

![Niemonolityczne wdrożenie a mikrousługi](./media/monolithic-vs-microservices.png)

**Rysunek 1-4.** Niemonolityczne wdrożenie a mikrousługi

Należy zauważyć, jak mikrousługi promują zasadę "jedna baza kodu, jedna aplikacja" z [aplikacji 12-składnikowej](https://12factor.net/)omówionej wcześniej w rozdziale.

> *Współczynnik \#1 określa "pojedynczą bazę kodu dla każdej mikrousługi, która jest przechowywana we własnym repozytorium. Śledzone przy użyciu kontroli wersji, można je wdrożyć w wielu środowiskach ".*

### <a name="why-microservices"></a>Dlaczego mikrousługi?

Mikrousługi zapewniają elastyczność.

Wcześniej w rozdziale porównano aplikację handlu elektronicznego utworzoną jako monolitu z mikrousługami. W tym przykładzie znaleźliśmy jasne korzyści:

- Każda mikrousługa ma autonomiczny cykl życia i może się od siebie samodzielnie rozwijać i wdrażać. Nie musisz czekać na wydanie kwartalne, aby wdrożyć nowe funkcje lub aktualizację. Możesz zaktualizować niewielki obszar złożonej aplikacji z mniejszym ryzykiem zakłócenia całego systemu.

- Każda mikrousługa może być skalowana niezależnie. Zamiast skalować całą aplikację jako pojedynczą jednostkę, można skalować tylko te usługi, które wymagają większej mocy obliczeniowej lub przepustowości sieci. To precyzyjne podejście do skalowania zapewnia większą kontrolę nad systemem i pomaga w zmniejszeniu kosztów ogólnych podczas skalowania części systemu, a nie wszystkich.

Doskonały przewodnik dotyczący znajomości mikrousług to [.NET mikrousługi: architektura dla kontenerów aplikacji .NET](https://docs.microsoft.com/dotnet/standard/microservices-architecture/). Książka omówieniach głębokie projektowanie i architektura mikrousług. Jest to pomocnik dla [architektury referencyjnej mikrousług](https://github.com/dotnet-architecture/eShopOnContainers) , dostępnej bezpłatnie do pobrania od firmy Microsoft.

### <a name="developing-microservices"></a>Tworzenie mikrousług

Mikrousługi można tworzyć przy użyciu dowolnej nowoczesnej platformy programistycznej.

Platforma Microsoft .NET Core to doskonały wybór. Bezpłatna i open source ma wiele wbudowanych funkcji upraszczających programowanie mikrousług. Platforma .NET Core jest dla wielu platform. Aplikacje można budować i uruchamiać w systemach Windows, macOS i większości systemów Linux.

Program .NET Core jest wysoce wydajny i został dobrze oceniony w porównaniu do środowiska Node. js i innych konkurujących platform. Z tego względu [TechEmpower](https://www.techempower.com/) przeprowadził rozbudowany zestaw [testów wydajności](https://www.techempower.com/benchmarks/#section=data-r17&hw=ph&test=plaintext) na wielu platformach aplikacji sieci Web i strukturach. Platforma .NET Core została oceniona w 10 najlepszych ponad platformie Node. js i innych konkurencyjnych platformach.

Platforma .NET Core jest obsługiwana przez firmę Microsoft i społeczność programu .NET w witrynie GitHub.

## <a name="containers"></a>Containers

Obecnie, że jest to naturalne, aby poznać termin *kontenera* wymieniony w dowolnej konwersacji dotyczącej *natywnej chmury*. W książce, [wzorce natywne chmury](https://www.manning.com/books/cloud-native-patterns), autor Cornelia Davis obserwuje, że "kontenery są doskonałym rozwiązaniem w przypadku oprogramowania natywnego w chmurze". Natywna platforma obliczeniowa w chmurze wprowadza mikrousługi kontenerach jako pierwszy krok w swojej [natywnej mapie w chmurze](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) — wskazówki dla przedsiębiorstw, które rozpoczynają podróż w chmurze.

Konteneryzowania mikrousługa jest prosta i prosta. Kod, jego zależności i środowisko uruchomieniowe są pakowane w plik binarny o nazwie [obraz kontenera](https://docs.docker.com/glossary/?term=image). Obrazy są przechowywane w [rejestrze kontenerów](https://caylent.com/container-registries/), który działa jako repozytorium lub biblioteka dla obrazów. Rejestr może znajdować się na komputerze deweloperskim, w centrum danych lub w chmurze publicznej. Platforma Docker utrzymuje rejestr publiczny za pośrednictwem narzędzia [Docker Hub](https://hub.docker.com/). Usługa Azure Cloud zawiera [Rejestr kontenerów](https://azure.microsoft.com/services/container-registry/) w celu przechowywania obrazów kontenerów blisko aplikacji w chmurze, które będą je uruchamiać.

W razie konieczności można przekształcić obraz w uruchomione wystąpienie kontenera. Wystąpienie jest uruchamiane na dowolnym komputerze, na którym jest zainstalowany aparat [środowiska uruchomieniowego kontenera](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) . W razie konieczności można korzystać z dowolnej liczby wystąpień usługi kontenera.

Rysunek 1-5 przedstawia trzy różne mikrousługi, z których każdy w własnym kontenerze działa na jednym hoście.

![Wiele kontenerów uruchomionych na hoście kontenera](./media/hosting-mulitple-containers.png)

**Rysunek 1-5**. Wiele kontenerów uruchomionych na hoście kontenera

Zwróć uwagę na to, jak każdy kontener utrzymuje własny zestaw zależności i środowiska uruchomieniowego, które mogą być różne. W tym miejscu widzimy różne wersje mikrousługi produktu uruchomione na tym samym hoście. Każdy kontener udostępnia wycinek bazowego systemu operacyjnego hosta, pamięci i procesora, ale jest odizolowany od siebie.

Zwróć uwagę na to, jak dobrze model kontenera obejmuje zasadę "zależności" z [aplikacji 12-składnikowej](https://12factor.net/).

> *Współczynnik \#2 określa, że każda mikrousług izoluje i pakuje własne zależności, wdrażając zmiany bez wpływu na cały system ".*

Kontenery obsługują obciążenia dla systemów Linux i Windows. Chmura platformy Azure jest otwarta jednocześnie. Jest to w ciekawej postaci system Linux, a nie system Windows Server, który stał się najpopularniejszym systemem operacyjnym na platformie Azure.

Chociaż istnieje kilku dostawców kontenerów, platforma Docker przechwyciła udział Lion na rynku. Firma prowadzi do przenoszenia kontenera oprogramowania. Stała się to standardem dla pakowania, wdrażania i uruchamiania aplikacji natywnych w chmurze.

### <a name="why-containers"></a>Dlaczego kontenery?

Kontenery umożliwiają przenoszenie i gwarantowanie spójności w różnych środowiskach. Hermetyzując wszystko w jednym pakiecie, można *izolować* mikrousługę i jej zależności od podstawowej infrastruktury.

Ten sam kontener można wdrożyć w dowolnym środowisku, które ma aparat środowiska uruchomieniowego Docker. Obciążenia kontenerów eliminują również koszty wstępnej konfiguracji każdego środowiska przy użyciu struktur, bibliotek oprogramowania i aparatów środowiska uruchomieniowego.

Udostępniając podstawowy system operacyjny i zasoby hosta, kontenery mają znacznie mniejsze rozmiary niż pełna maszyna wirtualna. Mniejszy rozmiar zwiększa *gęstość*lub liczbę mikrousług, która może być uruchamiana przez dany host w tym samym czasie.

### <a name="container-orchestration"></a>Aranżacja kontenerów

Chociaż narzędzia takie jak Docker umożliwiają tworzenie obrazów i uruchamianie kontenerów, potrzebne są również narzędzia do zarządzania nimi. Zarządzanie kontenerami odbywa się przy użyciu specjalnego programu oprogramowania zwanego koordynatorem kontenera. W przypadku działania na dużą skalę organizacja kontenera jest istotna.

Rysunek 1-6 przedstawia zadania zarządzania, które zapewnia koordynatorów kontenerów.

![Co to są Koordynatory kontenerów](./media/what-container-orchestrators-do.png)

**Rysunek 1-6**. Co to są Koordynatory kontenerów

W poniższej tabeli opisano typowe zadania aranżacji.

|  Zadania | Wyjaśnienie  |
| :-------- | :-------- |
| Planowanie | Automatyczne Inicjowanie obsługi wystąpień kontenerów.|
| Koligacja/ochrona przed koligacją | Udostępniaj kontenery w pobliżu lub daleko od siebie, ułatwiając dostępność i wydajność. |
| Monitorowanie kondycji | Automatycznie wykrywaj i Poprawiaj błędy.|
| Tryb failover | Automatyczne ponowne Inicjowanie obsługi administracyjnej wystąpienia nie powiodło się.|
| Skalowanie | Automatyczne dodanie lub usunięcie wystąpienia kontenera w celu spełnienia wymagań.|
| Networking | Zarządzanie nakładką sieciową na potrzeby komunikacji kontenerowej.|
| Odnajdywanie usług | Włącz kontenery, aby zlokalizować siebie nawzajem.|
| Uaktualnienia stopniowe | Koordynuj uaktualnienia przyrostowe bez przestojów. Automatycznie przywracaj problematyczne zmiany.|

Należy zauważyć, jak usługi Orchestrator wdrażają zasady disposability i współbieżności z [aplikacji 12-składnikowej](https://12factor.net/)omówionej wcześniej w rozdziale.

> *Czynnik \#9 określa, że wystąpienia usługi powinny być jednorazowe, dzięki czemu można uzyskać szybkie uruchomienia w celu zwiększenia możliwości skalowalności i bezpiecznego zamykania systemu, aby pozostawić system w prawidłowym stanie. Kontenery platformy Docker wraz z koordynatorem niezgodne z tym wymaganiem ".*

> *Fabryka \#8 określa, że "usługi są skalowane w ramach dużej liczby niewielkich identycznych procesów (kopii), a nie do skalowania pojedynczego dużego wystąpienia na najbardziej wydajny dostępną maszynę".*

Chociaż istnieje kilka koordynatorów kontenerów, [Kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) stał się de facto standardem dla świata natywnego w chmurze. Jest to przenośna, rozszerzalna platforma typu "open source" do zarządzania obciążeniami kontenera.

Możesz hostować własne wystąpienie Kubernetes, ale następnie ponosisz odpowiedzialność za aprowizacji i zarządzanie swoimi zasobami, które mogą być złożone. Funkcje chmury platformy Azure Kubernetes jako usługa zarządzana, [usługa Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/). Usługa zarządzana umożliwia pełne wykorzystanie jej funkcji bez konieczności instalowania i konserwowania.

Usługa Azure Kubernetes Services zawiera szczegółowy rozdział 2, *skalowanie aplikacji natywnych w chmurze*.

## <a name="backing-services"></a>Usługi zapasowe

Systemy natywne w chmurze zależą od wielu różnych zasobów pomocniczych, takich jak magazyny danych, brokerzy komunikatów, monitorowanie i usługi tożsamości. Te usługi są znane jako [usługi zapasowe](https://12factor.net/backing-services).

 Rysunek 1-7 przedstawia wiele typowych usług zapasowych, których używają systemy natywne w chmurze.

![Wspólne usługi zapasowe](./media/common-backing-services.png)

**Rysunek 1-7**. Wspólne usługi zapasowe

Usługi zapasowe promują zasadę "bezstanowe" z [aplikacji 12-składnikowej](https://12factor.net/)omówionej wcześniej w rozdziale.

>*Współczynnik \#6* określa, że "Każda mikrousługa powinna być wykonywana we własnym procesie, odizolowana od innych uruchomionych usług. Externalize stan wymagany do usługi zapasowej, na przykład rozproszonej pamięci podręcznej lub magazynu danych ".

Możesz obsługiwać własne usługi zapasowe, ale następnie ponosisz odpowiedzialność za Licencjonowanie, Inicjowanie obsługi administracyjnej i zarządzanie tymi zasobami.

Dostawcy chmury oferują rozbudowane, *zarządzane usługi zarządzania zapasami.* Zamiast korzystać z usługi, wystarczy ją wykorzystać. Dostawca obsługuje zasób w odpowiedniej skali i nosi odpowiedzialność za wydajność, bezpieczeństwo i konserwację. Monitorowanie, nadmiarowość i dostępność są wbudowane w usługę. Dostawcy w pełni obsługują swoje zarządzane usługi — otwierają bilet i naprawiają swój problem.

Systemy natywne w chmurze preferują zarządzane usługi zapasowe od dostawców chmury. Oszczędności w czasie i robocizny są wspaniałe. Ryzyko związane z utrzymywaniem własnych i napotykanych problemów może być kosztowne.

Najlepszym rozwiązaniem jest traktowanie usługi zapasowej jako *dołączonego zasobu*, dynamicznie powiązanej z mikrousługą z informacjami (adresem URL i poświadczeniami) przechowywanymi w konfiguracji zewnętrznej. Wskazówki te są opisane w części [12-składnikowej aplikacji](https://12factor.net/)omówionej wcześniej w rozdziale.

>*Fabryka \#4* określa, że usługi zapasowe powinny być udostępniane za pośrednictwem adresu URL z adresami. W ten sposób można oddzielić zasób od aplikacji, co umożliwi jego zmianę.

>*Współczynnik \#3* określa, że "informacje o konfiguracji są przenoszone z mikrousługi i zewnętrznie za pomocą narzędzia do zarządzania konfiguracją poza kodem".

Za pomocą tego wzorca można dołączać i odłączać usługę zapasową bez wprowadzania zmian w kodzie. Mikrousługa można promować z poziomu funkcji pytań i odpowiedzi w środowisku przejściowym. Konfigurację mikrousług należy zaktualizować, aby wskazywała usługi zapasowe w trakcie przemieszczania i wstrzyknąć ustawienia do kontenera za pomocą zmiennej środowiskowej.

Dostawcy chmury dostarczają interfejsy API umożliwiające komunikowanie się z własnymi usługami zapasowymi. Te biblioteki hermetyzują instalację wodociągową i złożoność. Bezpośrednie komunikowanie się z tymi interfejsami API spowoduje ścisłe połączenie kodu z usługą zapasową. Lepszym rozwiązaniem jest izolowanie szczegółów implementacji interfejsu API dostawcy. Wprowadzenie do kodu usługi warstwy biokorekty lub pośredniego interfejsu API. Ten luźny sprzężenie umożliwia zamianę jednej usługi zapasowej na inną lub przeniesienie kodu do innej chmury publicznej bez konieczności wprowadzania zmian w kodzie usługi linii głównej.

Usługi zapasowe zostały omówione szczegółowo w rozdziale 5, *wzorcach danych natywnych w chmurze*i rozdziale 4 w *natywnych wzorcach komunikacji w chmurze*.

## <a name="automation"></a>Automatyzacja

Jak widać, systemy natywne w chmurze uwzględniają mikrousługi, kontenery i nowoczesne projektowanie systemu, aby osiągnąć szybkość i elastyczność. Ale jest to tylko część wątku. Jak można zainicjować obsługę środowisk w chmurze, na których są uruchamiane te systemy? Jak szybko wdrażać funkcje i aktualizacje aplikacji? Jak zaokrąglić pełny obraz?

Wprowadzanie powszechnie zaakceptowanej metody [infrastruktury jako kodu](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)lub IaC.

Przy użyciu IaC można zautomatyzować Inicjowanie obsługi platformy i wdrażanie aplikacji. Zasadniczo stosowane są praktyki inżynieryjne dotyczące oprogramowania, takie jak testowanie i przechowywanie wersji, do Twoich praktyk DevOps. Infrastruktura i wdrożenia są zautomatyzowane, spójne i powtarzalne.

### <a name="automating-infrastructure"></a>Automatyzacja infrastruktury

Narzędzia, takie jak [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/), Terraform i [interfejs wiersza polecenia platformy Azure](https://docs.microsoft.com/cli/azure/), umożliwiają deklaratywne skrypt wymaganej infrastruktury chmurowej. Nazwy zasobów, lokalizacje, pojemności i wpisy tajne są sparametryzowane i dynamiczne. Skrypt ma wersję i zaewidencjonowano kontrolę źródła jako artefakt projektu. Skrypt jest wywoływany w celu zapewnienia spójnej i powtarzalnej infrastruktury w środowiskach systemowych, takich jak pytania i odpowiedzi, przygotowanie i produkcja.

Pod okapem, IaC to idempotentne, co oznacza, że można uruchomić ten sam skrypt w czasie, bez efektów ubocznych. Jeśli zespół musi wprowadzić zmianę, edytuje i ponownie uruchamia skrypt. Dotyczy to tylko zaktualizowanych zasobów.

W artykule [co to jest infrastruktura jako kod](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), autor sam Guckenheimer opisuje, jak "zespoły, które implementują IaC, mogą szybko i w odpowiedniej skali. Zespoły unikają ręcznej konfiguracji środowisk i wymuszania spójności przez odzwierciedlenie żądanego stanu środowiska za pośrednictwem kodu. Wdrożenia infrastruktury za pomocą IaC są powtarzalne i zapobiegają problemom z czasem wykonywania spowodowanym przez dryfowanie konfiguracji lub brakujące zależności. Zespoły DevOps mogą współdziałać z ujednoliconym zestawem praktyk i narzędzi, aby dostarczać aplikacje i obsługiwać infrastrukturę szybko, niezawodnie i na dużą skalę. "

### <a name="automating-deployments"></a>Automatyzacja wdrożeń

[Aplikacja 12-czynnikowa](https://12factor.net/), omówiona wcześniej, wywołuje oddzielne kroki podczas przekształcania wykonanego kodu w uruchomioną aplikację.

> *Współczynnik \#5* określa, że "Każde wydanie musi wymusić ścisłe oddzielenie między kompilacją, wydaniem i etapami uruchomienia. Każdy z nich powinien być oznaczony unikatowym IDENTYFIKATORem i obsługiwać możliwość wycofywania ".

Nowoczesne systemy ciągłej integracji/ciągłego wdrażania pomagają spełnić tę zasadę. Zapewniają one oddzielne kroki wdrażania i zapewniają spójny i jakościowy kod, który jest łatwo dostępny dla użytkowników.

Rysunek 1-8 pokazuje separację w procesie wdrażania.

![Kroki wdrożenia w potoku ciągłej integracji/ciągłego wdrażania](./media/build-release-run-pipeline.png)

**Rysunek 1-8**. Kroki wdrażania w potoku ciągłej integracji/ciągłego dostarczania

Na powyższym rysunku należy zwrócić szczególną uwagę na rozdzielenie zadań.

Deweloper tworzy funkcję w środowisku programistycznym, Iterowanie przez to, co jest nazywane "pętlą wewnętrzną" kodu, uruchomienia i debugowania. Po zakończeniu ten kod jest *wypychany* do repozytorium kodu, takiego jak GitHub, Azure DevOps lub BitBucket.

Wypychanie wyzwala etap kompilacji, który przekształca kod w artefakt binarny. Prace są implementowane za pomocą potoku [ciągłej integracji (ci)](https://martinfowler.com/articles/continuousIntegration.html) . Automatycznie kompiluje, testuje i pakuje aplikację.

Etap wydania pobiera artefakt binarny, stosuje zewnętrzne informacje o konfiguracji aplikacji i środowiska oraz tworzy niezmienne wydanie. Wydanie jest wdrażane w określonym środowisku. Prace są implementowane za pomocą potoku [ciągłego dostarczania (CD)](https://martinfowler.com/bliki/ContinuousDelivery.html) . Każde wydanie powinno być możliwe do zidentyfikowania. Możesz powiedzieć, "to wdrożenie działa w wersji 2.1.1 aplikacji".

Na koniec wydana funkcja jest uruchamiana w docelowym środowisku wykonawczym. Wersje są niezmienne, co oznacza, że jakakolwiek zmiana musi utworzyć nową wersję.

Stosując te praktyki, organizacje mają radykalnie rozwój oprogramowania. Wiele przeniesiono od kwartalnych wersji do aktualizacji na żądanie. Celem jest przechwycenie problemów wczesnych w cyklu programowania, gdy są one tańsze do naprawienia. Im dłuższy czas między integracją, tym bardziej kosztowne problemy mają być rozwiązywane.  Ze spójnością w procesie integracji zespoły mogą częściej zatwierdzić zmiany kodu, co prowadzi do lepszej współpracy i jakości oprogramowania.

### <a name="azure-pipelines"></a>Azure Pipelines

Chmura platformy Azure obejmuje nową usługę ciągłej integracji/ciągłego dostarczania [Azure Pipelines](https://azure.microsoft.com/services/devops/pipelines/), która jest częścią oferty [usługi Azure DevOps](https://azure.microsoft.com/services/devops/) pokazanej na rysunku 1-9.

![Azure Pipelines w DevOps](./media/devops-components.png)

**Rysunek 1-9**. Oferty usługi Azure DevOps

Azure Pipelines to usługa w chmurze, która łączy ciągłą integrację (CI) i ciągłe dostarczanie (CD). Możesz automatycznie testować, kompilować i dostarczać kod do dowolnego celu.

Możesz zdefiniować potok w kodzie w pliku YAML, obok pozostałej części kodu aplikacji.

- Potok jest zgodny z kodem i ma tę samą strukturę rozgałęziania.
- Sprawdzanie poprawności zmian odbywa się za poorednictwem przeglądów kodu w ramach żądań ściągnięcia i zasad tworzenia gałęzi.
- Wszystkie używane gałęzie mogą dostosować zasady kompilacji, modyfikując plik Azure-Pipelines. yml.
- Plik potoku jest sprawdzany w kontroli wersji i można go zbadać, jeśli wystąpił problem.

Usługa Azure Pipelines obsługuje większość dostawców git i może generować potoki wdrożenia dla aplikacji pisanych na platformach Linux, macOS lub Windows. Obejmuje to obsługę języków Java, .NET, JavaScript, Python, PHP, go, XCode i C++.

>[!div class="step-by-step"]
>[Poprzedni](introduction.md)
>[Następny](candidate-apps.md)
