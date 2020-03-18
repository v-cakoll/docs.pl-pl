---
title: Definiowanie rozwiązań natywnych dla chmury
description: Dowiedz się więcej o filarach, które stanowią podstawę dla systemów natywnych dla chmury
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 27191a67b2964ac2e1636a4d7dc55d5314b78439
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401572"
---
# <a name="defining-cloud-native"></a>Definiowanie natywnej chmury

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Zatrzymaj to, co robisz i wyślij SMS-a 10 do współpracowników. Poproś ich, aby zdefiniowali termin "Cloud Native". Duża szansa, że otrzymasz osiem różnych odpowiedzi. Co ciekawe, za sześć miesięcy, w miarę rozwoju technologii i praktyk natywnych dla chmury, ich definicja.

Natywna chmura polega na zmianie sposobu myślenia o tworzeniu krytycznych systemów biznesowych.

Systemy natywne dla chmury są zaprojektowane tak, aby uwzględniać szybkie zmiany, dużą skalę i odporność.

Cloud Native Computing Foundation zawiera [oficjalną definicję:](https://github.com/cncf/foundation/blob/master/charter.md)

> *Technologie natywne dla chmury umożliwiają organizacjom tworzenie i uruchamianie skalowalnych aplikacji w nowoczesnych, dynamicznych środowiskach, takich jak chmury publiczne, prywatne i hybrydowe. Kontenery, siateczek usługi, mikrousług, infrastruktury niezmienne i deklaratywne interfejsy API przykładem tego podejścia.*

> *Techniki te umożliwiają luźno sprzętych systemów, które są odporne, zarządzaniu i obserwowalne. W połączeniu z solidną automatyzacją pozwalają inżynierom na częste i przewidywalne wprowadzanie zmian o dużym wpływie przy minimalnym trudze.*

Aplikacje stają się coraz bardziej złożone, a użytkownicy wymagają coraz więcej. Użytkownicy oczekują szybkiej reakcji, innowacyjnych funkcji i zerowych przestojów. Problemy z wydajnością, powtarzające się błędy i niemożność szybkiego poruszania się nie są już dopuszczalne. Z łatwością przeniosą się do twojego konkurenta.

Chmura native jest dużo o *szybkość* i *zwinność*. Systemy biznesowe ewoluują od włączania zdolności biznesowych do broni strategicznej transformacji, przyspieszając szybkość i wzrost biznesu. Konieczne jest natychmiastowe wprowadzanie pomysłów na rynek.

Oto kilka firm, które wdrożyły te techniki. Pomyśl o szybkości, zwinności i skalowalności, jaką osiągnęli.

| Firma | Środowisko użytkownika |
| :-------- | :-------- |
| [Netflix](https://www.infoq.com/news/2013/06/netflix/) | Ma ponad 600 usług w produkcji. Wdraża sto razy dziennie. |
| [Uber](https://eng.uber.com/micro-deploy/) | Posiada ponad 1000 usług przechowywanych w środowisku produkcyjnym. Wdraża kilka tysięcy kompilacji każdego tygodnia. |
| [WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf) | Ma ponad 300 usług w produkcji. Wprowadza prawie 1000 zmian dziennie. |

Jak widać, Netflix, Uber i WeChat ujawniają systemy, które składają się z setek niezależnych mikrousług. Ten styl architektoniczny pozwala im szybko reagować na warunki rynkowe. Mogą natychmiast aktualizować małe obszary żywej, złożonej aplikacji i indywidualnie skalować te obszary w razie potrzeby.

Szybkość i zwinność chmur rodzimych wynikają z wielu czynników. Przede wszystkim jest infrastruktura chmury. Pięć dodatkowych filarów podstawowych przedstawionych na rysunku 1-3 stanowi również podstawę dla systemów natywnych dla chmury.

![Filary podstawowe opojczyków](./media/cloud-native-foundational-pillars.png)

**Rysunek 1-3**. Filary podstawowe opojczyków

Poświęćmy trochę czasu, aby lepiej zrozumieć znaczenie każdego filaru.

## <a name="the-cloud"></a>Chmura...

Systemy natywne dla chmury w pełni wykorzystują model usługi w chmurze.

Zaprojektowane z myślą o rozwoju w dynamicznym, zwirtualizowanym środowisku chmury systemy te intensywnie korzystają z infrastruktury [obliczeniowej Platform as a Service (PaaS)](https://azure.microsoft.com/overview/what-is-paas/) i usług zarządzanych. Traktują podstawową infrastrukturę jako *jednorazową* - aprowizowaną w ciągu kilku minut i przewymiarowaną, skalowaną, przenoszoną lub zniszczoną na żądanie - za pomocą automatyzacji.

Rozważmy powszechnie akceptowane koncepcji DevOps [zwierzęta vs bydła](https://medium.com/@Joachim8675309/devops-concepts-pets-vs-cattle-2380b5aab313). W tradycyjnym centrum danych serwery są traktowane jako *zwierzęta domowe:* fizyczna maszyna, nadana znacząca nazwa i pod opieką. Skalowanie przez dodanie większej liczby zasobów do tego samego komputera (skalowanie w górę). Jeśli serwer zachoruje, karmisz go z powrotem do zdrowia. Jeśli serwer stanie się niedostępny, wszyscy zauważą.

Model obsługi *bydła* jest inny. Każde wystąpienie jest aprowizowane jako maszyna wirtualna lub kontener. Są one identyczne i przypisane identyfikator systemu, takich jak Service-01, Service-02 i tak dalej. Skalowanie przez utworzenie większej liczby z nich (skalowanie w ycinka). Kiedy ktoś staje się niedostępny, nikt nie zauważa.

Model bydła obejmuje *niezmienną infrastrukturę.* Serwery nie są naprawiane ani modyfikowane. Jeśli ktoś zawiedzie lub wymaga aktualizacji, jest niszczony, a nowy jest aprowizowany - wszystko odbywa się za pomocą automatyzacji.

Systemy natywne dla chmury obejmują model usługi Cattle. Nadal działają w miarę skalowania infrastruktury w lub na zewnątrz, bez względu na maszyny, na których są uruchomione.

Platforma w chmurze platformy Azure obsługuje tego typu wysoce elastyczną infrastrukturę z funkcjami automatycznego skalowania, samonaprawiania się i monitorowania.

## <a name="modern-design"></a>Nowoczesny design

Jak zaprojektować aplikację natywną w chmurze? Jak wyglądałaby Twoja architektura? Do jakich zasad, wzorców i najlepszych praktyk byś przestrzegał? Jaka infrastruktura i kwestie operacyjne byłyby ważne?

### <a name="the-twelve-factor-application"></a>Aplikacja dwunastoczynnikowa

Powszechnie akceptowaną metodologią tworzenia aplikacji opartych na chmurze jest [aplikacja dwunastoczynnikowa.](https://12factor.net/) Opisano zestaw zasad i praktyk, które deweloperzy wykonaj do tworzenia aplikacji zoptymalizowanych dla nowoczesnych środowisk w chmurze. Szczególną uwagę zwraca się na przenośność w różnych środowiskach i automatyzacji deklaratywnej.

Chociaż ma zastosowanie do dowolnej aplikacji internetowej, wielu praktyków uważa ją za solidną podstawę do tworzenia aplikacji natywnych dla chmury. Systemy oparte na tych zasadach mogą szybko wdrażać i skalować oraz dodawać funkcje, aby szybko reagować na zmiany na rynku.

W poniższej tabeli przedstawiono metodologię dwunastoczynników:

|    |  Czynnikiem | Wyjaśnienie  |
| :-------- | :-------- | :-------- |
| 1 | Podstawa kodu | Baza pojedynczego kodu dla każdej mikrousługi, przechowywane we własnym repozytorium. Śledzone za pomocą kontroli wersji, można wdrożyć w wielu środowiskach (QA, Staging, Production). |
| 2 | Zależności | Każda mikrousługa izoluje i pakiety własnych zależności, obejmując zmiany bez wpływu na cały system. |
| 3 | Konfiguracje  | Informacje o konfiguracji są przenoszone z mikrousługi i zewnętrznie za pośrednictwem narzędzia do zarządzania konfiguracją poza kodem. To samo wdrożenie może propagować w różnych środowiskach z zastosowaną poprawną konfiguracją.  |
| 4 | Usługi tworzenia kopii zapasowych | Zasoby pomocnicze (magazyny danych, pamięci podręczne, brokerzy komunikatów) powinny być udostępniane za pośrednictwem adresowego adresu URL. W ten sposób oddziela zasób od aplikacji, umożliwiając mu wymienne.  |
| 5 | Kompilacja, wydanie, uruchomienie | Każda wersja musi wymusić ścisłą separację między etapami kompilacji, wydania i uruchamiania. Każdy z nich powinien być oznaczony unikatowym identyfikatorem i obsługiwać możliwość wycofania. Nowoczesne systemy CI/CD pomagają spełnić tę zasadę. |
| 6 | Procesy | Każda mikrousługa powinna być wykonywana w swoim własnym procesie, izolowane od innych uruchomionych usług. Zewnętrznie zniżanie wymaganego stanu do usługi tworzenia kopii zapasowych, takich jak rozproszona pamięć podręczna lub magazyn danych. |
| 7 | Powiązanie portu | Każda mikrousługa powinna być niezależna z jego interfejsów i funkcji uwidacznianych na własnym porcie. W ten sposób zapewnia izolację od innych mikrousług. |
| 8 | Współbieżność | Usługi skalowane w sposób skalowalny w wielu małych identycznych procesach (kopiach) w przeciwieństwie do skalowania pojedynczego dużego wystąpienia na najpotężniejszej dostępnej maszynie. |
| 9 | Uniechwinność | Wystąpienia usługi powinny być jednorazowe, faworyzując szybkie startupy, aby zwiększyć możliwości skalowalności i łagodne zamknięcia, aby pozostawić system w prawidłowym stanie. Kontenery platformy Docker wraz z koordynatorem z natury spełniają to wymaganie. |
| 10 | Parytet deweloperski/prod | Utrzymuj środowiska w całym cyklu życia aplikacji tak podobne, jak to możliwe, unikając kosztownych skrótów. W tym miejscu przyjęcie kontenerów może znacznie przyczynić się poprzez promowanie tego samego środowiska wykonywania. |
| 11 | Rejestrowanie | Traktuj dzienniki generowane przez mikrousługi jako strumienie zdarzeń. Przetwórz je za pomocą agregatora zdarzeń i propaguj dane do narzędzi do zarządzania wyszukiwaniem/dziennikami danych, takich jak Azure Monitor lub Splunk, a ostatecznie do długoterminowej archiwizacji. |
| 12 | Procesy administracyjne | Uruchamianie zadań administracyjnych/administracyjnych jako procesów jednorazowych. Zadania mogą obejmować oczyszczanie danych i wyciąganie analiz dla raportu. Narzędzia wykonujące te zadania powinny być wywoływane ze środowiska produkcyjnego, ale oddzielnie od aplikacji. |

W książce [Beyond the Twelve-Factor App,](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)autor Kevin Hoffman szczegółowo każdy z oryginalnych 12 czynników (napisany w 2011). Ponadto książka zawiera trzy dodatkowe czynniki, które odzwierciedlają dzisiejszy nowoczesny projekt aplikacji w chmurze.

|    |  Nowy czynnik | Wyjaśnienie  |
| :-------- | :-------- | :-------- |
| 13 | Najpierw interfejs API | Zrób wszystko jako usługę. Załóżmy, że kod będzie używany przez klienta frontonu, bramy lub innej usługi. |
| 14 | Telemetria | Na stacji roboczej masz głęboki wgląd w aplikację i jej zachowanie. W chmurze nie. Upewnij się, że projekt zawiera kolekcję danych monitorowania, danych dotyczących domeny i kondycji/systemu. |
| 15 | Uwierzytelnianie/autoryzacja  | Implementuj tożsamość od samego początku. Należy wziąć pod uwagę [RBAC (role-based kontroli dostępu)](https://docs.microsoft.com/azure/role-based-access-control/overview) funkcje dostępne w chmurach publicznych.  |

Odniesiemy się do wielu z 12+ czynników w tym rozdziale i w całej książce.

### <a name="critical-design-considerations"></a>Krytyczne zagadnienia projektowe

Oprócz wskazówek dostarczonych z metodologii dwunastoskładnikowej, istnieje kilka krytycznych decyzji projektowych, które należy podjąć podczas konstruowania systemów rozproszonych.

*Komunikacja*

W jaki sposób aplikacje klienckie frontonu będą komunikować się z podstawowymi usługami podstawowymi? Czy zezwolisz na bezpośrednią komunikację? Czy można też streszczeć usługi zaplecza za pomocą fasady bramy, która zapewnia elastyczność, kontrolę i bezpieczeństwo?

W jaki sposób podstawowe usługi zaplecza będą się ze sobą komunikować? Czy zezwolisz na bezpośrednie wywołania HTTP, które prowadzą do sprzężenia i wpływu na wydajność i elastyczność? A może rozważyć odsiadki z technologiami kolejki i tematów?

Komunikacja jest szczegółowo opisana rozdział 4, *Cloud-Native Wzorce komunikacji*.

*Odporność*

Architektura mikrousług przenosi system z komunikacji w toku do sieci. W środowisku rozproszonym, co można zrobić, gdy usługa B nie odpowiada na wywołanie z usługi A? Co się stanie, gdy usługa C stanie się tymczasowo niedostępna, a inne usługi wywołujące ją stosu ją i obniżyć wydajność systemu?

Odporność jest szczegółowo omówiona rozdział 6, *Odporność natywna w chmurze*.

*Dane rozproszone*

Zgodnie z projektem każda mikrousługa hermetyzuje własne dane, udostępniając operacje za pośrednictwem interfejsu publicznego. Jeśli tak, w jaki sposób kwerendy danych lub zaimplementować transakcję w wielu usługach?

Dane rozproszone są szczegółowo omówione rozdział 5, *Cloud-Native Wzorce danych*.

*Tożsamość*

W jaki sposób usługa będzie identyfikować, kto uzyskuje do niej dostęp i jakie uprawnienia posiada?

Tożsamość jest szczegółowo opisana Rozdział 8, *Tożsamość*.

## <a name="microservices"></a>Mikrousługi

Systemy natywne dla chmury obejmują mikrousługi, popularny styl architektoniczny do tworzenia nowoczesnych aplikacji.

Zbudowany jako rozproszony zestaw małych, niezależnych usług, które współdziałają za pośrednictwem udostępnionej sieci szkieletowej, mikrousługi mają następujące cechy:

- Każdy implementuje określonej możliwości biznesowych w kontekście większej domeny.

- Każdy z nich jest rozwijany autonomicznie i może być wdrażany niezależnie.

- Każdy z nich jest samodzielnym hermetyzacją własnej technologii przechowywania danych (SQL, NoSQL) i platformą programowania.

- Każdy działa we własnym procesie i komunikuje się z innymi przy użyciu standardowych protokołów komunikacyjnych, takich jak HTTP/HTTPS, WebSockets lub [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).

- Tworzą one razem, aby utworzyć wniosek.

Rysunek 1-4 kontrastuje monolityczne podejście aplikacji z podejściem mikrousług. Należy zauważyć, jak monolit składa się z architektury warstwowej, która jest wykonywana w jednym procesie. Zazwyczaj zużywa relacyjnej bazy danych. Podejście mikrousług, jednak segreguje funkcje do niezależnych usług, które zawierają logikę i dane. Każda mikrousługa obsługuje własny magazyn danych.

![Wdrożenie monolityczne a mikrousługi](./media/monolithic-vs-microservices.png)

**Rysunek 1-4.** Wdrożenie monolityczne a mikrousługi

Należy zauważyć, jak mikrousług promowania "One Codebase, one application" zasady z [aplikacji dwunastu czynników](https://12factor.net/), omówione wcześniej w rozdziale.

> *Czynnik \#1 określa "Pojedyncza baza kodu dla każdej mikrousługi, przechowywana we własnym repozytorium. Śledzony za pomocą kontroli wersji, może być wdrażany w wielu środowiskach."*

### <a name="why-microservices"></a>Dlaczego mikrousługi?

Mikrousługi zapewniają elastyczność.

Wcześniej w rozdziale porównaliśmy aplikację eCommerce skonstruowaną jako monolit z mikrousługami. W tym przykładzie daliśmy pewne wyraźne korzyści:

- Każda mikrousługa ma autonomiczny cykl życia i może rozwijać się niezależnie i często wdrażać. Nie musisz czekać na kwartalną wersję, aby wdrożyć nowe funkcje lub aktualizację. Można zaktualizować mały obszar złożonej aplikacji z mniejszym ryzykiem zakłócenia całego systemu.

- Każda mikrousługa można skalować niezależnie. Zamiast skalować całą aplikację jako pojedynczą jednostkę, można skalować w sposób skalowalny tylko te usługi, które wymagają większej mocy obliczeniowej lub przepustowości sieci. To szczegółowe podejście do skalowania zapewnia większą kontrolę nad systemem i pomaga zmniejszyć ogólne koszty podczas skalowania części systemu, a nie wszystkiego.

Doskonałym przewodnikiem referencyjnym dla zrozumienia mikrousług jest [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/standard/microservices-architecture/). Książka głęboko przechodzi do projektowania mikrousług i architektury. Jest to towarzysz dla [architektury mikrousług pełnego stosu](https://github.com/dotnet-architecture/eShopOnContainers) dostępne do pobrania za darmo od firmy Microsoft.

### <a name="developing-microservices"></a>Tworzenie mikrousług

Mikrousługi można utworzyć za pomocą dowolnej nowoczesnej platformy deweloperskiej.

Platforma Microsoft .NET Core jest doskonałym wyborem. Bezpłatne i open source, ma wiele wbudowanych funkcji, aby uprościć tworzenie mikrousług. .NET Core jest wieloplatformowy. Aplikacje mogą być budowane i uruchamiane na Windows, macOS i większość smaków Linuksa.

.NET Core jest wysoce działać i zdobył również w porównaniu do Node.js i innych konkurencyjnych platform. Co ciekawe, [TechEmpower](https://www.techempower.com/) przeprowadził obszerny zestaw wskaźników wydajności na wielu [platformach](https://www.techempower.com/benchmarks/#section=data-r17&hw=ph&test=plaintext) aplikacji internetowych i platformach. .NET Core zdobył w pierwszej 10 - znacznie powyżej Node.js i innych konkurencyjnych platform.

Program .NET Core jest obsługiwany przez firmę Microsoft i społeczność .NET w witrynie GitHub.

## <a name="containers"></a>Kontenery

W dzisiejszych czasach, to naturalne, aby usłyszeć termin *kontener* wymienionych w każdej rozmowie dotyczącej *chmury rodzimych*. W książce [Cloud Native Patterns](https://www.manning.com/books/cloud-native-patterns), autor Cornelia Davis zauważa, że "Kontenery są doskonałym czynnikiem umożliwiającym oprogramowanie natywne dla chmury." Cloud Native Computing Foundation umieszcza konteneryzacji mikrousług jako pierwszy krok w ich [cloud-native Trail Map](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) — wskazówki dla przedsiębiorstw rozpoczynających swoją podróż natywną w chmurze.

Konteneryzowanie mikrousługi jest proste i proste. Kod, jego zależności i czas wykonywania są pakowane do pliku binarnego o nazwie [obrazu kontenera](https://docs.docker.com/glossary/?term=image). Obrazy są przechowywane w [rejestrze kontenerów,](https://caylent.com/container-registries/)który działa jako repozytorium lub biblioteki obrazów. Rejestr może znajdować się na komputerze deweloperskim, w centrum danych lub w chmurze publicznej. Sam platforma Docker prowadzi rejestr publiczny za pośrednictwem [usługi Docker Hub](https://hub.docker.com/). Chmura platformy Azure oferuje [rejestr kontenerów](https://azure.microsoft.com/services/container-registry/) do przechowywania obrazów kontenerów w pobliżu aplikacji w chmurze, które będą je uruchamiać.

W razie potrzeby można przekształcić obraz w uruchomionej instancji kontenera. Wystąpienie jest uruchamiane na dowolnym komputerze z zainstalowanym aparatem [uruchomieniowym kontenera.](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) Można mieć tyle wystąpień usługi konteneryzowanej zgodnie z potrzebami.

Rysunek 1-5 pokazuje trzy różne mikrousługi, każdy w swoim własnym kontenerze, uruchomiony na jednym hoście.

![Wiele kontenerów działających na hoście kontenera](./media/hosting-mulitple-containers.png)

**Rysunek 1-5**. Wiele kontenerów działających na hoście kontenera

Należy zauważyć, jak każdy kontener utrzymuje własny zestaw zależności i czasu wykonywania, które mogą być różne. W tym miejscu widzimy różne wersje mikrousługi produktu uruchomionej na tym samym hoście. Każdy kontener udostępnia plasterek podstawowego systemu operacyjnego hosta, pamięci i procesora, ale jest odizolowany od siebie.

Zwróć uwagę, jak dobrze model kontenera obejmuje zasadę "Zależności" z [aplikacji dwunastoczynnikowej](https://12factor.net/).

> *Czynnik \#2 określa, że "Każda mikrousługa izoluje i pakuje własne zależności, obejmując zmiany bez wpływu na cały system."*

Kontenery obsługują obciążenia systemu Linux i Windows. Chmura platformy Azure otwarcie obejmuje oba. Co ciekawe, to Linux, a nie Windows Server, stał się najpopularniejszym systemem operacyjnym na platformie Azure.

Podczas gdy istnieje kilku dostawców kontenerów, Docker zdobył lwią część rynku. Firma prowadzi ruch kontenerów oprogramowania. Stał się de facto standardem pakowania, wdrażania i uruchamiania aplikacji natywnych dla chmury.

### <a name="why-containers"></a>Dlaczego kontenery?

Kontenery zapewniają przenośność i gwarantują spójność w różnych środowiskach. Hermetyzując wszystko w jednym pakiecie, można *wyizolować* mikrousługi i jej zależności z podstawowej infrastruktury.

Można wdrożyć tego samego kontenera w dowolnym środowisku, które ma aparat wykonywania platformy Docker. Konteneryzowane obciążenia eliminują również koszty wstępnej konfiguracji każdego środowiska za pomocą struktur, bibliotek oprogramowania i aparatów środowiska uruchomieniowego.

Udostępniając podstawowy system operacyjny i zasoby hosta, kontenery mają znacznie mniejszy rozmiar niż pełna maszyna wirtualna. Mniejszy rozmiar zwiększa *gęstość*lub liczbę mikrousług, które dany host może uruchomić w tym samym czasie.

### <a name="container-orchestration"></a>Aranżacja kontenerów

Narzędzia, takie jak platforma Docker, tworzą obrazy i uruchamiają kontenery, potrzebne są również narzędzia do zarządzania nimi. Zarządzanie kontenerami odbywa się za pomocą specjalnego programu o nazwie koordynator kontenera. Podczas pracy na dużą skalę, aranżacji kontenerów jest niezbędna.

Rysunek 1-6 przedstawia zadania zarządzania, które zapewniają koordynatorzy kontenerów.

![Co robią koordynatorzy kontenerów](./media/what-container-orchestrators-do.png)

**Rysunek 1-6**. Co robią koordynatorzy kontenerów

W poniższej tabeli opisano typowe zadania aranżacji.

|  Zadania | Wyjaśnienie  |
| :-------- | :-------- |
| Planowanie | Automatyczne inicjowanie obsługi administracyjnej wystąpień kontenera.|
| Powinowactwo/antypowinowactwo | Aprowizuj kontenery w pobliżu lub daleko od siebie, pomagając w dostępności i wydajności. |
| Monitorowanie kondycji | Automatyczne wykrywanie i korygowanie błędów.|
| Tryb failover | Automatyczne ponowne aprowizacje wystąpienia do zdrowych maszyn.|
| Skalowanie | Automatyczne dodawanie lub usuwanie wystąpienia kontenera w celu zaspokojenia popytu.|
| Networking | Zarządzanie nakładką sieciową do komunikacji kontenera.|
| Odnajdywanie usług | Włącz kontenery, aby zlokalizować siebie nawzajem.|
| Stopniowe uaktualnienia | Koordynuj uaktualnienia przyrostowe przy wdrażaniu zerowym przestoju. Automatyczne wycofywanie problematycznych zmian.|

Należy zwrócić uwagę, jak koordynatorzy obejmują zasady disposability i współbieżności z [aplikacji dwunastu czynników](https://12factor.net/), omówione wcześniej w rozdziale.

> *Czynnik \#9 określa, że "Wystąpienia usługi powinny być jednorazowe, faworyzując szybkie uruchamianie, aby zwiększyć możliwości skalowalności i łagodne zamknięcia, aby pozostawić system w prawidłowym stanie. Kontenery docker wraz z koordynatorem z natury spełniają to wymagania."*

> *Czynnik \#8 określa, że "Usługi skalowane w sposób skalowalny w dużej liczbie małych identycznych procesów (kopii) w przeciwieństwie do skalowania w górę pojedynczego dużego wystąpienia na najpotężniejszej dostępnej maszynie."*

Podczas gdy istnieje kilka koordynatorów kontenerów, [Kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) stał się de facto standardem dla świata ojczystego chmury. Jest to przenośna, rozszerzalna platforma typu open source do zarządzania konteneryzowanymi obciążeniami.

Możesz hostować własne wystąpienie Kubernetes, ale wtedy będziesz odpowiedzialny za inicjowanie obsługi administracyjnej i zarządzanie jego zasobami - co może być złożone. Chmura platformy Azure oferuje kubernetes jako usługę zarządzaną, [usługa Azure Kubernetes (AKS).](https://azure.microsoft.com/services/kubernetes-service/) Zarządzana usługa pozwala w pełni wykorzystać swoje funkcje, bez konieczności jej instalowania i konserwacji.

Usługi Azure Kubernetes zostały omówione w szczegółowym rozdziale 2, *Skalowanie aplikacji natywnych dla chmury.*

## <a name="backing-services"></a>Usługi podkładowe

Systemy natywne dla chmury zależą od wielu różnych zasobów pomocniczych, takich jak magazyny danych, brokerzy komunikatów, usługi monitorowania i tożsamości. Usługi te są nazywane [usługami zapasowymi](https://12factor.net/backing-services).

 Rysunek 1-7 przedstawia wiele typowych usług tworzenia kopii zapasowych, które zużywają systemy natywne dla chmury.

![Wspólne usługi podkładowe](./media/common-backing-services.png)

**Rysunek 1-7**. Wspólne usługi podkładowe

Usługi wspierające promują zasadę "bezpaństwowości" z [aplikacji dwunastoczynnikowej](https://12factor.net/), omówionej wcześniej w rozdziale.

>*Czynnik \#6* określa, że "Każda mikrousługa powinna być wykonywana we własnym procesie, izolowana od innych uruchomionych usług. Zewnętrznianie wymaganego stanu do usługi tworzenia kopii zapasowych, takich jak rozproszona pamięć podręczna lub magazyn danych."

Możesz hostować własne usługi tworzenia kopii zapasowych, ale wtedy będziesz odpowiedzialny za licencjonowanie, inicjowanie obsługi administracyjnej i zarządzanie tymi zasobami.

Dostawcy chmury oferują bogaty asortyment *zarządzanych usług tworzenia kopii zapasowych.* Zamiast posiadania usługi, po prostu zużywają go. Dostawca obsługuje zasoby na dużą skalę i ponosi odpowiedzialność za wydajność, bezpieczeństwo i konserwację. Monitorowanie, nadmiarowość i dostępność są wbudowane w usługę. Dostawcy w pełni obsługują swoje usługi zarządzane - otwórz bilet i rozwiążą problem.

Systemy natywne dla chmury preferują zarządzane usługi tworzenia kopii zapasowych od dostawców chmury. Oszczędność czasu i pracy są świetne. Ryzyko operacyjne związane z hostowaniem własnych i doświadczaniem kłopotów może szybko stać się kosztowne.

Najlepszym rozwiązaniem jest traktowanie usługi tworzenia kopii zapasowych jako *dołączonego zasobu,* dynamicznie powiązanego z mikrousługą z informacjami (adresami URL i poświadczeniami) przechowywanymi w konfiguracji zewnętrznej. Wytyczne te zostały określone w [aplikacji dwunastoczynnikowej](https://12factor.net/), omówionej wcześniej w rozdziale.

>*Czynnik \#4* określa, że usługi tworzenia kopii zapasowych "powinny być udostępniane za pośrednictwem adresowalnego adresu URL. W ten sposób oddziela zasób od aplikacji, umożliwiając jego wymienne."

>*Czynnik \#3* określa, że "Informacje o konfiguracji są przenoszone z mikrousługi i eksternalizowane za pomocą narzędzia do zarządzania konfiguracją poza kodem".

Za pomocą tego wzorca usługi tworzenia kopii zapasowych można dołączyć i odłączyć bez zmian kodu. Można podwyższyć mikrousługi z kontroli jakości do środowiska przejściowego. Zaktualizować konfigurację mikrousług, aby wskazać usługi tworzenia kopii zapasowych w środowisku przejściowym i wstrzyknąć ustawienia do kontenera za pośrednictwem zmiennej środowiskowej.

Dostawcy chmury udostępniają interfejsy API, aby komunikować się z ich zastrzeżonymi usługami zapasowymi. Biblioteki te hermetyzują instalację wodno-kanalizacyjną i złożoność. Komunikowanie się bezpośrednio z tymi interfejsami API będzie ściśle łączyć kod z usługą tworzenia kopii zapasowych. Jest to lepsza praktyka, aby ocieplić szczegóły implementacji interfejsu API dostawcy. Wprowadzenie warstwy pośrednictwa lub pośredniego interfejsu API, narażając operacje ogólne do kodu usługi. To luźne sprzężenie umożliwia zamianę jednej usługi tworzenia kopii zapasowych dla innej lub przeniesienie kodu do innej chmury publicznej bez konieczności wprowadzania zmian w kodzie usługi linii głównej.

Usługi tworzenia kopii zapasowych są szczegółowo omówione rozdział 5, *wzorce danych natywnych dla chmury*i rozdział 4, *wzorce komunikacji natywnej w chmurze*.

## <a name="automation"></a>Automatyzacja

Jak widać, systemy natywne dla chmury obejmują mikrousługi, kontenery i nowoczesny projekt systemu, aby osiągnąć szybkość i elastyczność. Ale to tylko część historii. Jak aprowizować środowiska chmury, na których działają te systemy? Jak szybko wdrożyć funkcje i aktualizacje aplikacji? Jak dopełnić pełny obraz?

Wprowadź powszechnie przyjętą praktykę [infrastruktury jako Kod](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)lub IaC.

Za pomocą usługi IaC automatyzujesz inicjowanie obsługi administracyjnej platform i wdrażanie aplikacji. Zasadniczo stosuje się praktyki inżynierii oprogramowania, takie jak testowanie i przechowywanie wersji do praktyk DevOps. Infrastruktura i wdrożenia są zautomatyzowane, spójne i powtarzalne.

### <a name="automating-infrastructure"></a>Automatyzacja infrastruktury

Narzędzia, takie jak [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/), Terraform i azure [CLI](https://docs.microsoft.com/cli/azure/), umożliwiają deklaratywne skryptinfrastruktury chmury, której potrzebujesz. Nazwy zasobów, lokalizacje, pojemności i wpisy tajne są parametryzowane i dynamiczne. Skrypt jest wersjonowany i sprawdzany w kontroli źródła jako artefakt projektu. Skrypt wywołuje sprowokować do obsługi administracyjnej spójnej i powtarzalnej infrastruktury w środowiskach systemowych, takich jak QA, przemieszczania i produkcji.

Pod maską, IaC jest idempotentności, co oznacza, że można uruchomić ten sam skrypt w kółko bez skutków ubocznych. Jeśli zespół musi wprowadzić zmiany, edytować i ponownie uruchomić skrypt. Dotyczy to tylko zaktualizowanych zasobów.

W artykule [What is Infrastructure as Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), Author Sam Guckenheimer opisuje, jak, "Zespoły wdrażane IaC mogą szybko i na dużą skalę dostarczać stabilne środowiska. Zespoły unikają ręcznej konfiguracji środowisk i wymuszają spójność, reprezentując żądany stan ich środowisk za pomocą kodu. Wdrożenia infrastruktury z iaC są powtarzalne i zapobiec problemy ze środowiska uruchomieniowego spowodowane przez dryf konfiguracji lub brakujących zależności. Zespoły DevOps mogą współpracować z ujednoliconym zestawem praktyk i narzędzi do szybkiego, niezawodnego i skalowanego dostarczania aplikacji i ich infrastruktury pomocniczej".

### <a name="automating-deployments"></a>Automatyzacja wdrożeń

[Aplikacja dwunastoczynnikowa](https://12factor.net/), omówione wcześniej, wymaga oddzielnych kroków podczas przekształcania ukończonego kodu w uruchomioną aplikację.

> *Czynnik \#5* określa, że "Każda wersja musi wymuszać ścisłe oddzielenie między etapami kompilacji, zwalniania i uruchamiania. Każdy z nich powinien być oznaczony unikatowym identyfikatorem i obsługiwać możliwość wycofania."

Nowoczesne systemy CI/CD pomagają spełnić tę zasadę. Zapewniają one oddzielne kroki wdrażania i zapewniają spójny i wysokiej jakości kod, który jest łatwo dostępny dla użytkowników.

Rysunek 1-8 przedstawia separację w procesie wdrażania.

![Etapy wdrażania w potoku ciągłej integracji/ciągłej integracji](./media/build-release-run-pipeline.png)

**Rysunek 1-8**. Kroki wdrażania w potoku ciągłej integracji/ciągłej integracji

Na poprzedniej rysunku należy zwrócić szczególną uwagę na oddzielenie zadań.

Deweloper tworzy funkcję w środowisku programistycznym, iterując za pomocą tak zwanej "wewnętrznej pętli" kodu, uruchamiania i debugowania. Po zakończeniu ten kod jest *wypychany* do repozytorium kodu, takich jak GitHub, Azure DevOps lub BitBucket.

Wypychanie wyzwala etap kompilacji, który przekształca kod w artefakt binarny. Praca jest implementowana z potoku [ciągłej integracji (CI).](https://martinfowler.com/articles/continuousIntegration.html) Automatycznie tworzy, testuje i pakuje aplikację.

Etap wydania pobiera artefakt binarny, stosuje informacje o konfiguracji aplikacji zewnętrznej i środowiska i tworzy niezmienne wydanie. Wydanie jest wdrażane w określonym środowisku. Praca jest implementowana z [potoku ciągłej dostawy (CD).](https://martinfowler.com/bliki/ContinuousDelivery.html) Każde wydanie powinno być możliwe do zidentyfikowania. Można powiedzieć: "To wdrożenie jest uruchomione wersja 2.1.1 aplikacji."

Na koniec zwolniona funkcja jest uruchamiana w środowisku wykonywania docelowego. Wersje są niezmienne, co oznacza, że każda zmiana musi utworzyć nową wersję.

Stosując te praktyki, organizacje radykalnie ewoluowały, w jaki sposób wysyłają oprogramowanie. Wiele z nich przeszło z kwartalnych wersji do aktualizacji na żądanie. Celem jest złapać problemy na wczesnym etapie cyklu rozwoju, gdy są one tańsze, aby naprawić. Im dłuższy czas trwania między integracjami, tym droższe problemy stają się do rozwiązania.  Dzięki spójności procesu integracji zespoły mogą częściej zatwierdzać zmiany kodu, co prowadzi do lepszej współpracy i jakości oprogramowania.

### <a name="azure-pipelines"></a>Azure Pipelines

Chmura platformy Azure zawiera nową usługę ciągłej integracji/ciągłego dysku CD zatytułowaną [Potoki platformy Azure,](https://azure.microsoft.com/services/devops/pipelines/)która jest częścią oferty [Azure DevOps](https://azure.microsoft.com/services/devops/) przedstawionej na rysunku 1–9.

![Potoki platformy Azure w devops](./media/devops-components.png)

**Rysunek 1-9**. Oferty usługi Azure DevOps

Azure Pipelines to usługa w chmurze, która łączy ciągłą integrację (CI) i ciągłe dostarczanie (CD). Możesz automatycznie testować, budować i wysyłać kod do dowolnego celu.

Potok można zdefiniować w kodzie w pliku YAML wraz z resztą kodu aplikacji.

- Potok jest wersjonowany z kodem i następuje tej samej struktury rozgałęzienia.
- Otrzymasz sprawdzanie poprawności zmian za pomocą przeglądów kodu w żądaniach ściągnięcia i zasad kompilacji gałęzi.
- Każda gałąź, której używasz, może dostosować zasady kompilacji, modyfikując plik azure-pipelines.yml.
- Plik potoku jest sprawdzany w kontroli wersji i może być zbadany, jeśli występuje problem.

Usługa Azure Pipelines obsługuje większość dostawców git i może generować potoki wdrażania dla aplikacji napisanych na platformach Linux, macOS lub Windows. Obejmuje obsługę języków Java, .NET, JavaScript, Python, PHP, Go, XCode i C++.

>[!div class="step-by-step"]
>[Poprzedni](introduction.md)
>[następny](candidate-apps.md)
