---
title: Definiowanie rozwiązań natywnych dla chmury
description: Dowiedz się więcej o filarach fundamentowych, które stanowią podstawę dla systemów natywnych dla chmury
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 756a2565bd77fcef19a5f15579987836ff0e75a4
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989093"
---
# <a name="defining-cloud-native"></a>Definiowanie natywnego chmury

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Zatrzymaj to, co robisz i wyślij sms-a do dziesięciu swoich współpracowników. Poproś ich, aby zdefiniowali termin "Cloud Native". Duża szansa, że otrzymasz osiem różnych odpowiedzi.

Natywna chmura polega na zmianie sposobu myślenia o konstruowaniu krytycznych systemów biznesowych.

Systemy natywne dla chmury zostały zaprojektowane z myślą o szybkich zmianach, dużej skali i odporności.

Cloud Native Computing Foundation zawiera [oficjalną definicję:](https://github.com/cncf/foundation/blob/master/charter.md)

> *Technologie natywne dla chmury umożliwiają organizacjom tworzenie i uruchamianie skalowalnych aplikacji w nowoczesnych, dynamicznych środowiskach, takich jak chmury publiczne, prywatne i hybrydowe. Kontenery, siatki usług, mikrousługi, infrastruktura niezmienne i deklaratywne interfejsy API przykładem tego podejścia.*

> *Techniki te umożliwiają luźno sprzężone systemy, które są odporne, łatwe w zarządzaniu i obserwowalne. W połączeniu z solidną automatyzacją pozwalają inżynierom na częste i przewidywalne wprowadzanie zmian o dużym wpływie przy minimalnym obciążeniu.*

Aplikacje stają się coraz bardziej złożone, a użytkownicy coraz bardziej wymagają. Użytkownicy oczekują szybkiej reakcji, innowacyjnych funkcji i zerowych przestojów. Problemy z wydajnością, powtarzające się błędy i niemożność szybkiego poruszania się nie są już dopuszczalne. Łatwo przeniosą się do twojego konkurenta.

Natywna chmura jest dużo o *szybkości* i *zwinności*. Systemy biznesowe ewoluują od umożliwienia możliwości biznesowych do broni strategicznej transformacji, przyspieszając prędkość biznesową i wzrost. Konieczne jest natychmiastowe wynajęcie pomysłów na rynek.

Oto kilka firm, które wdrożyły te techniki. Pomyśl o szybkości, zwinności i skalowalności, jaką osiągnęli.

| Firma | Środowisko użytkownika |
| :-------- | :-------- |
| [Netflix](https://www.infoq.com/news/2013/06/netflix/) | Ma ponad 600 usług w produkcji. Wdraża sto razy dziennie. |
| [Uber](https://eng.uber.com/micro-deploy/) | Ma ponad 1000 usług przechowywanych w produkcji. Wdraża kilka tysięcy kompilacji tygodniowo. |
| [WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf) | Ma ponad 300 usług w produkcji. Wprowadza prawie 1000 zmian dziennie. |

Jak widać, Netflix, Uber i WeChat ujawniają systemy, które składają się z setek niezależnych mikrousług. Ten styl architektoniczny pozwala im szybko reagować na warunki rynkowe. Mogą natychmiast aktualizować małe obszary aktywnej, złożonej aplikacji i indywidualnie skalować te obszary w razie potrzeby.

Szybkość i zwinność natywnego chmury wynika z wielu czynników. Przede wszystkim jest infrastruktura chmury. Pięć dodatkowych filarów fundamentowych pokazanych na rysunku 1-3 stanowi również podstawę dla systemów natywnych dla chmury.

![Natywne dla chmury filary fundamentowe](./media/cloud-native-foundational-pillars.png)

**Rysunek 1-3**. Natywne dla chmury filary fundamentowe

Poświęćmy trochę czasu, aby lepiej zrozumieć znaczenie każdego filaru.

## <a name="the-cloud"></a>Chmura...

Systemy natywne dla chmury w pełni wykorzystują model usługi w chmurze.

Zaprojektowane z myślą o dynamicznym, zwirtualizowanym środowisku chmury, systemy te szeroko wykorzystują [infrastrukturę obliczeniową Platformy jako usługi (PaaS)](https://azure.microsoft.com/overview/what-is-paas/) i usługi zarządzane. Traktują podstawową infrastrukturę jako *jednorazową* — aprowizowaną w ciągu kilku minut i zmienioną, skalowaną, przeniesioną lub zniszczoną na żądanie — za pośrednictwem automatyzacji.

Rozważmy powszechnie akceptowane pojęcie DevOps [zwierząt domowych vs bydła](https://medium.com/@Joachim8675309/devops-concepts-pets-vs-cattle-2380b5aab313). W tradycyjnym centrum danych serwery są traktowane jako *zwierzęta domowe*: fizyczna maszyna, nadana znaczącą nazwę i pod opieką. Skalowanie przez dodanie większej ilości zasobów do tego samego komputera (skalowanie w górę). Jeśli serwer zachoruje, pielęgnisz go z powrotem do zdrowia. Jeśli serwer stanie się niedostępny, wszyscy zauważą.

Model usługi *Cattle* jest inny. Aprowizuj każde wystąpienie jako maszynę wirtualną lub kontener. Są identyczne i przypisano identyfikator systemu, takich jak Service-01, Service-02 i tak dalej. Skalowanie przez utworzenie większej liczby z nich (skalowanie w poziomie). Kiedy ktoś staje się niedostępny, nikt nie zauważa.

Model bydła obejmuje *niezmienną infrastrukturę.* Serwery nie są naprawione ani modyfikowane. Jeśli jeden nie powiedzie się lub wymaga aktualizacji, jest niszczony i nowy jest aprowizowana — wszystko odbywa się za pomocą automatyzacji.

Systemy natywne dla chmury obejmują model usługi Cattle. Nadal działają one w miarę skalowania infrastruktury w lub na zewnątrz bez względu na maszyny, na których są one uruchomione.

Platforma chmura Azure obsługuje tego typu wysoce elastyczną infrastrukturę z funkcjami automatycznego skalowania, samonaprawiania i monitorowania.

## <a name="modern-design"></a>Nowoczesny design

Jak zaprojektować aplikację natywną dla chmury? Jak wyglądałaby Twoja architektura? Do jakich zasad, wzorców i najlepszych praktyk należy stosować? Jakie kwestie infrastrukturalne i operacyjne byłyby ważne?

### <a name="the-twelve-factor-application"></a>Aplikacja dwunastoceliowa

Powszechnie akceptowaną metodologią konstruowania aplikacji opartych na chmurze jest [aplikacja Dwunastoceseczna.](https://12factor.net/) Opisano w nim zestaw zasad i praktyk, które deweloperzy stosują w celu konstruowania aplikacji zoptymalizowanych pod kątem nowoczesnych środowisk w chmurze. Szczególną uwagę zwraca się na przenośność między środowiskami i automatyzację deklaratywną.

Chociaż ma zastosowanie do dowolnej aplikacji sieci web, wielu praktyków uważa ją za solidną podstawę do tworzenia aplikacji natywnych dla chmury. Systemy oparte na tych zasadach mogą szybko wdrażać i skalować oraz dodawać funkcje, aby szybko reagować na zmiany na rynku.

W poniższej tabeli przedstawiono metodologię Dwunastu Czynników:

|    |  Czynnikiem | Wyjaśnienie  |
| :-------- | :-------- | :-------- |
| 1 | Podstawa kodu | Pojedyncza baza kodu dla każdej mikrousługi, przechowywana we własnym repozytorium. Śledzone z kontroli wersji, można wdrożyć w wielu środowiskach (QA, Staging, Produkcja). |
| 2 | Zależności | Każda mikrousługa izoluje i pakiety własnych zależności, obejmując zmiany bez wpływu na cały system. |
| 3 | Konfiguracje  | Informacje o konfiguracji są przenoszone z mikrousługi i zewnętrznie za pośrednictwem narzędzia do zarządzania konfiguracją poza kodem. To samo wdrożenie może propagować między środowiskami z zastosowaną poprawną konfiguracją.  |
| 4 | Usługi wspierające | Zasoby pomocnicze (magazyny danych, pamięci podręczne, brokerzy wiadomości) powinny być udostępniane za pośrednictwem adresowalny adres URL. W ten sposób oddziela zasób od aplikacji, umożliwiając jego wymienny.  |
| 5 | Budować, zwalniać, uruchamiać | Każda wersja musi wymusić ścisłe oddzielenie między etapami kompilacji, wydania i uruchamiania. Każdy z nich powinien być oznaczony unikatowym identyfikatorem i obsługiwać możliwość wycofania. Nowoczesne systemy ciągłej integracji/ciągłego wdrażania pomagają spełnić tę zasadę. |
| 6 | Procesy | Każda mikrousługa powinna być wykonywana w swoim własnym procesie, odizolowane od innych uruchomionych usług. Zewnętrznie wymagany stan do usługi kopii zapasowej, takich jak rozproszonej pamięci podręcznej lub magazynu danych. |
| 7 | Powiązanie portu | Każda mikrousługa powinna być niezależna za pomocą interfejsów i funkcji narażonych na własnym porcie. W ten sposób zapewnia izolację od innych mikrousług. |
| 8 | Współbieżność | Usługi skalują się w poziomie w dużej liczbie małych identycznych procesów (kopii), w przeciwieństwie do skalowania w górę pojedynczego dużego wystąpienia na najpotężniejszym dostępnym komputerze. |
| 9 | Możliwość zbycia | Wystąpienia usługi powinny być jednorazowe, faworyzując szybkie uruchamianie, aby zwiększyć możliwości skalowalności i wdzięczne zamknięcia systemu, aby pozostawić system w prawidłowym stanie. Kontenery platformy Docker wraz z orchestrator z natury spełniają to wymaganie. |
| 10 | Parzystość deweloperów/prod | Zachowaj środowiska w całym cyklu życia aplikacji jak najbardziej podobne, unikając kosztownych skrótów. W tym miejscu przyjęcie kontenerów może znacznie przyczynić się poprzez promowanie tego samego środowiska wykonywania. |
| 11 | Rejestrowanie | Traktuj dzienniki generowane przez mikrousług jako strumienie zdarzeń. Przetwórz je za pomocą agregatora zdarzeń i propaguj dane do narzędzi do zarządzania wyszukiwaniem/dziennikami danych, takich jak Azure Monitor lub Splunk, a ostatecznie do archiwizacji długoterminowej. |
| 12 | Procesy administracyjne | Uruchamianie zadań administracyjnych/zarządzania jako procesów jednorazowych. Zadania mogą obejmować oczyszczanie danych i ściąganie analizy dla raportu. Narzędzia wykonujące te zadania powinny być wywoływane ze środowiska produkcyjnego, ale niezależnie od aplikacji. |

W książce [Beyond the Twelve-Factor App,](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)autor Kevin Hoffman szczegółowo każdy z oryginalnych 12 czynników (napisany w 2011). Ponadto książka zawiera trzy dodatkowe czynniki, które odzwierciedlają dzisiejszy nowoczesny projekt aplikacji w chmurze.

|    |  Nowy czynnik | Wyjaśnienie  |
| :-------- | :-------- | :-------- |
| 13 | Interfejs API | Spraw, aby wszystko było usługą. Załóżmy, że kod zostanie wykorzystany przez klienta frontonu, bramy lub innej usługi. |
| 14 | Telemetria | Na stacji roboczej masz głęboki wgląd w aplikacji i jej zachowanie. W chmurze nie. Upewnij się, że projekt zawiera zbieranie danych monitorowania, specyficzne dla domeny i kondycji/systemu. |
| 15 | Uwierzytelnianie/ autoryzacja  | Implementowanie tożsamości od samego początku. Należy wziąć pod uwagę [FUNKCJE RBAC (kontrola dostępu oparta na rolach)](https://docs.microsoft.com/azure/role-based-access-control/overview) dostępne w chmurach publicznych.  |

Będziemy odnosić się do wielu z ponad 12 czynników w tym rozdziale i w całej książce.

### <a name="critical-design-considerations"></a>Krytyczne zagadnienia dotyczące projektu

Poza wytycznymi dostarczonymi z metodologii dwunastu czynników, istnieje kilka krytycznych decyzji projektowych, które należy podjąć podczas konstruowania systemów rozproszonych.

*Komunikacja*

W jaki sposób aplikacje klienckie front-end komunikują się z podstawowymi usługami backed-end? Czy pozwolisz na bezpośrednią komunikację? Lub, można abstrakcji usług zaplecza z fasady bramy, która zapewnia elastyczność, kontroli i bezpieczeństwa?

W jaki sposób podstawowe usługi zaplecza będą się ze sobą komunikować? Czy zezwolisz na bezpośrednie wywołania HTTP, które prowadzą do sprzężenia i wpływu na wydajność i elastyczność? A może rozważyć oddzielenie wiadomości z kolejką i technologiami tematycznych?

Komunikacja jest szczegółowo opisana Rozdział 4, *Cloud-Native Communication Patterns*.

*Odporność*

Architektura mikrousług przenosi system z komunikacji w toku do sieci. Co będzie się działo, gdy usługa B nie odpowiada na połączenie z usługi A w środowisku rozproszonym? Co się stanie, gdy usługa C stanie się tymczasowo niedostępna, a inne usługi wywołujące stos i obniżenie wydajności systemu?

Odporność jest szczegółowo opisana Rozdział 6, *Odporność natywna*dla chmury.

*Dane rozproszone*

Zgodnie z projektem każda mikrousługa hermetyzuje własne dane, ujawniając operacje za pośrednictwem interfejsu publicznego. Jeśli tak, w jaki sposób wysyłasz zapytania do danych lub implementujesz transakcję w wielu usługach?

Dane rozproszone są szczegółowo opisane Rozdział 5, *Natywne wzorce danych w chmurze*.

*Tożsamość*

W jaki sposób usługa określi, kto uzyskuje do niej dostęp i jakie uprawnienia mają?

Tożsamość jest szczegółowo opisana Rozdział 8, *Tożsamość*.

## <a name="microservices"></a>Mikrousługi

Systemy natywne dla chmury obejmują mikrousług, popularny styl architektury do konstruowania nowoczesnych aplikacji.

Mikrousług, utworzony jako rozproszony zestaw małych, niezależnych usług, które współdziałają za pośrednictwem udostępnionej sieci szkieletowej, mają następujące cechy:

- Każdy implementuje określone możliwości biznesowe w kontekście większej domeny.

- Każdy z nich jest rozwijany autonomicznie i może być wdrażany niezależnie.

- Każdy z nich jest samodzielny, hermetyzujący własną technologię przechowywania danych (SQL, NoSQL) i platformę programową.

- Każdy z nich jest uruchamiany we własnym procesie i komunikuje się z innymi osobami przy użyciu standardowych protokołów komunikacyjnych, takich jak HTTP/HTTPS, WebSockets lub [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).

- Tworzą razem, aby utworzyć wniosek.

Rysunek 1-4 kontrastuje podejście aplikacji monolitycznych z podejściem mikrousług. Należy zauważyć, jak monolit składa się z architektury warstwowej, która jest wykonywana w jednym procesie. Zazwyczaj zużywa relacyjnej bazy danych. Podejście mikrousług, jednak segreguje funkcje do niezależnych usług, które zawierają logiki i danych. Każda mikrousługa hostuje własny magazyn danych.

![Wdrożenie monolityczne w porównaniu z mikrousługami](./media/monolithic-vs-microservices.png)

**Rysunek 1-4.** Wdrożenie monolityczne w porównaniu z mikrousługami

Należy zauważyć, jak mikrousługi promować "One Codebase, One Application" zasada z [aplikacji dwunastoskładnik,](https://12factor.net/)omówione wcześniej w rozdziale.

> *Współczynnik \#1 określa "Pojedyncza baza kodu dla każdej mikrousługi, przechowywana we własnym repozytorium. Śledzone z kontrolą wersji, można wdrożyć w wielu środowiskach."*

### <a name="why-microservices"></a>Dlaczego mikrousług?

Mikrousługi zapewniają elastyczność.

Wcześniej w rozdziale porównaliśmy aplikację eCommerce skompilni jako monolit z mikrousługami. W przykładzie zobaczyliśmy pewne wyraźne korzyści:

- Każda mikrousługa ma autonomiczny cykl życia i może ewoluować niezależnie i często wdrażać. Nie musisz czekać na kwartalną wersję, aby wdrożyć nowe funkcje lub aktualizację. Można zaktualizować mały obszar złożonej aplikacji z mniejszym ryzykiem zakłócenia całego systemu.

- Każda mikrousługa można skalować niezależnie. Zamiast skalowania całej aplikacji jako pojedynczej jednostki, można skalować w poziomie tylko te usługi, które wymagają większej mocy obliczeniowej lub przepustowości sieci. To szczegółowe podejście do skalowania zapewnia większą kontrolę nad systemem i pomaga zmniejszyć ogólne koszty podczas skalowania części systemu, a nie wszystkiego.

Doskonałym przewodnikiem referencyjnym do zrozumienia mikrousług jest [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/standard/microservices-architecture/). Książka głęboko zanurza się w projektowanie mikrousług i architektury. Jest to towarzysz architektury [referencyjnej mikrousług w pełnym stosie](https://github.com/dotnet-architecture/eShopOnContainers) dostępnej do bezpłatnego pobrania od firmy Microsoft.

### <a name="developing-microservices"></a>Tworzenie mikrousług

Mikrousług można tworzyć za pomocą dowolnej nowoczesnej platformy programistycznej.

Platforma Microsoft .NET Core to doskonały wybór. Wolne i open source, ma wiele wbudowanych funkcji, aby uprościć rozwój mikrousług. .NET Core jest wieloplatformowy. Aplikacje mogą być tworzone i uruchamiane w systemie Windows, macOS i większości smaków systemu Linux.

.NET Core jest bardzo wydajny i uzyskał dobre wyniki w porównaniu do Node.js i innych konkurencyjnych platform. Co ciekawe, [TechEmpower](https://www.techempower.com/) przeprowadził obszerny zestaw [testów porównawczych wydajności](https://www.techempower.com/benchmarks/#section=data-r17&hw=ph&test=plaintext) na wielu platformach i platformach aplikacji internetowych. .NET Core zdobył w pierwszej dziesiątce - znacznie powyżej Node.js i innych konkurencyjnych platform.

.NET Core jest obsługiwany przez firmę Microsoft i społeczność .NET w usłudze GitHub.

## <a name="containers"></a>Containers

W dzisiejszych czasach naturalne jest, aby usłyszeć termin *kontener* wymieniony w każdej rozmowie dotyczącej *chmury natywnej*. W książce [Cloud Native Patterns](https://www.manning.com/books/cloud-native-patterns), autor Cornelia Davis zauważa, że "Kontenery są doskonałym czynnikiem umożliwiającym oprogramowanie natywne dla chmury." Cloud Native Computing Foundation umieszcza konteneryzacji mikrousług jako pierwszy krok w ich [Cloud-Native Trail Map](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) — wskazówki dla przedsiębiorstw rozpoczynających podróż natywną chmurą.

Konteneryzowanie mikrousług jest proste i proste. Kod, jego zależności i środowisko uruchomieniowe są pakowane w plik binarny o nazwie [obraz kontenera.](https://docs.docker.com/glossary/?term=image) Obrazy są przechowywane w [rejestrze kontenerów,](https://caylent.com/container-registries/)który działa jako repozytorium lub biblioteka obrazów. Rejestr może znajdować się na komputerze deweloperskim, w centrum danych lub w chmurze publicznej. Sam docker prowadzi rejestr publiczny za pośrednictwem [usługi Docker Hub](https://hub.docker.com/). Chmura platformy Azure zawiera [rejestr kontenerów](https://azure.microsoft.com/services/container-registry/) do przechowywania obrazów kontenerów w pobliżu aplikacji w chmurze, które będą je uruchamiać.

W razie potrzeby obraz zostanie przekształcony w uruchomione wystąpienie kontenera. Wystąpienie jest uruchamiane na dowolnym komputerze z zainstalowanym aparatem [środowiska wykonawczego kontenera.](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) Może mieć tyle wystąpień usługi konteneryzowanej, zgodnie z potrzebami.

Rysunek 1-5 przedstawia trzy różne mikrousługi, każdy we własnym kontenerze, uruchomiony na jednym hoście.

![Wiele kontenerów uruchomionych na hoście kontenera](./media/hosting-mulitple-containers.png)

**Rysunek 1-5**. Wiele kontenerów uruchomionych na hoście kontenera

Należy zauważyć, jak każdy kontener zachowuje swój własny zestaw zależności i środowiska uruchomieniowego, które mogą być różne. W tym miejscu widzimy różne wersje product mikrousługi uruchomione na tym samym hoście. Każdy kontener udostępnia wycinek podstawowego systemu operacyjnego hosta, pamięci i procesora, ale jest odizolowany od siebie.

Zwróć uwagę, jak dobrze model kontenera obejmuje zasadę "Zależności" z [aplikacji dwunastocesechechowej.](https://12factor.net/)

> *Czynnik \#2 określa, że "Każda mikrousługi izoluje i pakiety własnych zależności, obejmując zmiany bez wpływu na cały system."*

Kontenery obsługują obciążenia systemu Linux i Windows. Chmura platformy Azure otwarcie obejmuje oba te elementy. Co ciekawe, to Linux, a nie Windows Server, stał się najpopularniejszym systemem operacyjnym na platformie Azure.

Podczas gdy istnieje kilku dostawców kontenerów, firma Docker zdobyła lwią część rynku. Firma prowadzi ruch kontenerów oprogramowania. Stało się de facto standardem pakowania, wdrażania i uruchamiania aplikacji natywnych dla chmury.

### <a name="why-containers"></a>Dlaczego pojemniki?

Kontenery zapewniają przenośność i gwarantują spójność w różnych środowiskach. Hermetyzując wszystko w jednym pakiecie, *izolujesz* mikrousługi i jej zależności od podstawowej infrastruktury.

Można wdrożyć tego samego kontenera w dowolnym środowisku, które ma aparat środowiska uruchomieniowego platformy Docker. Konteneryzowane obciążenia eliminują również koszty wstępnej konfiguracji każdego środowiska za pomocą struktur, bibliotek oprogramowania i aparatów środowiska uruchomieniowego.

Udostępniając podstawowe zasoby systemu operacyjnego i hosta, kontenery mają znacznie mniejszy rozmiar niż pełna maszyna wirtualna. Mniejszy rozmiar zwiększa *gęstość*lub liczbę mikrousług, które dany host można uruchomić w tym samym czasie.

### <a name="container-orchestration"></a>Aranżacja kontenerów

Podczas gdy narzędzia, takie jak platformy Docker, tworzą obrazy i uruchamiają kontenery, potrzebne są również narzędzia do zarządzania nimi. Zarządzanie kontenerem odbywa się za pomocą specjalnego oprogramowania o nazwie orchestrator kontenera. Podczas pracy na dużą skalę, aranżacja kontenera jest niezbędna.

Rysunek 1-6 przedstawia zadania zarządzania, które zapewniają koordynatorzy kontenerów.

![Co robią koordynatorzy kontenerów](./media/what-container-orchestrators-do.png)

**Rysunek 1-6**. Co robią koordynatorzy kontenerów

W poniższej tabeli opisano typowe zadania aranżacji.

|  Zadania | Wyjaśnienie  |
| :-------- | :-------- |
| Planowanie | Automatyczne inicjowania obsługi administracyjnej wystąpień kontenera.|
| Powinowactwo/anty-koligacja | Udostępnianie kontenerów w pobliżu lub daleko od siebie, pomagając w dostępności i wydajności. |
| Monitorowanie kondycji | Automatyczne wykrywanie i korygowanie awarii.|
| Tryb failover | Automatycznie reprovision nie powiodło się wystąpienie do zdrowych maszyn.|
| Skalowanie | Automatyczne dodawanie lub usuwanie wystąpienia kontenera w celu zaspokojenia popytu.|
| Networking | Zarządzanie nakładką sieciową do komunikacji kontenerowej.|
| Odnajdywanie usług | Włącz kontenery, aby zlokalizować siebie nawzajem.|
| Stopniowe uaktualnienia | Współrzęduj przyrostowe uaktualnienia przy zerowym wdrożeniu przestojów. Automatyczne wycofywanie problematycznych zmian.|

Zwróć uwagę, jak koordynatorzy objąć zasady dyspozycyjności i współbieżności z [aplikacji Dwunastu czynników,](https://12factor.net/)omówione wcześniej w rozdziale.

> *Czynnik \#9 określa, że "Wystąpienia usługi powinny być jednorazowe, faworyzując szybkie uruchamianie w celu zwiększenia możliwości skalowalności i wdzięku zamknięcia, aby pozostawić system w prawidłowym stanie. Kontenery platformy Docker wraz z koordynatorem z natury spełniają to wymaganie."*

> *Współczynnik \#8 określa, że "Usługi skalują się w poziomie w dużej liczbie małych identycznych procesów (kopii), w przeciwieństwie do skalowania w górę pojedynczego dużego wystąpienia na najpotężniejszym dostępnym komputerze."*

Chociaż istnieje kilka koordynatorów kontenerów, [Kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) stał się de facto standardem dla świata natywnego dla chmury. Jest to przenośna, rozszerzalna platforma open source do zarządzania konteneryzowanymi obciążeniami.

Możesz hostować własne wystąpienie kubernetes, ale wtedy będziesz odpowiedzialny za inicjowanie obsługi administracyjnej i zarządzanie jego zasobami — co może być złożone. Chmura platformy Azure oferuje usługi Kubernetes jako usługę zarządzaną, [Usługa Azure Kubernetes (AKS)](https://azure.microsoft.com/services/kubernetes-service/). Usługa zarządzana pozwala w pełni wykorzystać swoje funkcje, bez konieczności instalowania i utrzymywania go.

Usługi Kubernetes platformy Azure są szczegółowo opisane Rozdział 2, *Skalowanie aplikacji natywnych dla chmury.*

## <a name="backing-services"></a>Usługi wspierające

Systemy natywne dla chmury zależą od wielu różnych zasobów pomocniczych, takich jak magazyny danych, brokerzy wiadomości, monitorowanie i usługi tożsamości. Usługi te są znane jako [usługi wspierające](https://12factor.net/backing-services).

 Rysunek 1-7 przedstawia wiele typowych usług kopii zapasowych, które zużywają systemy natywne dla chmury.

![Wspólne usługi wsparcia](./media/common-backing-services.png)

**Rysunek 1-7**. Wspólne usługi wsparcia

Usługi wspierające promują zasadę "bezpaństwowości" z [aplikacji dwunastocełowej,](https://12factor.net/)omówionej wcześniej w rozdziale.

>*Współczynnik \#6* określa, że "Każda mikrousługa powinna być wykonywana w swoim własnym procesie, odizolowane od innych uruchomionych usług. Zewnętrznie wymagany stan do usługi kopii zapasowej, takiej jak rozproszona pamięć podręczna lub magazyn danych."

Możesz hostować własne usługi wspierające, ale wtedy będziesz odpowiedzialny za licencjonowanie, inicjowanie obsługi administracyjnej i zarządzanie tymi zasobami.

Dostawcy chmury oferują bogaty asortyment *zarządzanych usług wspierających.* Zamiast posiadać usługę, po prostu ją zużywają. Dostawca obsługuje zasób na dużą skalę i ponosi odpowiedzialność za wydajność, bezpieczeństwo i konserwację. Monitorowanie, nadmiarowość i dostępność są wbudowane w usługę. Dostawcy w pełni wspierają swoje usługi zarządzane — otwórz bilet i naprawią problem.

Systemy natywne dla chmury preferują zarządzane usługi wspierające od dostawców chmury. Oszczędność czasu i pracy jest ogromna. Ryzyko operacyjne związane z hostem własnego i doświadczaniem kłopotów może szybko stać się kosztowne.

Najlepszym rozwiązaniem jest traktowanie usługi kopii zapasowej jako *dołączonego zasobu,* dynamicznie powiązanego z mikrousługą z informacjami (adres URL i poświadczenia) przechowywanymi w konfiguracji zewnętrznej. Wytyczne te zostały określone w [aplikacji dwunastocełowej,](https://12factor.net/)omówionej wcześniej w rozdziale.

>*Współczynnik \#4* określa, że usługi zapasowe "powinny być udostępniane za pośrednictwem adresowalny adres URL. W ten sposób oddziela zasób od aplikacji, dzięki czemu jest wymienny."

>*Współczynnik \#3* określa, że "Informacje o konfiguracji są przenoszone z mikrousługi i zewnętrznie za pomocą narzędzia do zarządzania konfiguracją poza kodem."

Z tego wzorca usługi tworzenia kopii zapasowej mogą być dołączone i odłączone bez zmian kodu. Można promować mikrousługi z kontroli jakości do środowiska przejściowego. Zaktualizować konfigurację mikrousług, aby wskazać usługi zapasowe w przemieszczania i wstrzyknąć ustawienia do kontenera za pośrednictwem zmiennej środowiskowej.

Dostawcy chmury udostępniają interfejsy API do komunikowania się z ich zastrzeżonych usług owych. Biblioteki te hermetyzują instalację wodno-kanalizacyjną i złożoność. Komunikowanie się bezpośrednio z tymi interfejsami API będzie ściśle łączeć kod z usługą kopii zapasowej. Jest to lepsza praktyka, aby ocieplić szczegóły implementacji interfejsu API dostawcy. Wprowadzenie warstwy pośrednictwa lub pośredniego interfejsu API, uwidaczniając ogólne operacje na kodzie usługi. To luźne sprzężenie umożliwia zamianę jednej usługi zapasowej dla innej lub przeniesienie kodu do innej chmury publicznej bez konieczności wprowadzania zmian w kodzie usługi mainline.

Usługi wspierające są szczegółowo omówione rozdział 5, *Natywne wzorce danych w chmurze*i rozdział 4, *wzorce komunikacji natywnej*dla chmury.

## <a name="automation"></a>Automatyzacja

Jak już widać, systemy natywne w chmurze obejmują mikrousług, kontenerów i nowoczesny projekt systemu, aby osiągnąć szybkość i elastyczność. Ale to tylko część historii. Jak aprowizować środowiska w chmurze, na których działają te systemy? Jak szybko wdrożyć funkcje i aktualizacje aplikacji? Jak dopełniać pełny obraz?

Wprowadź powszechnie przyjętą praktykę [infrastruktury jako kod](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)lub IaC.

Za pomocą usługi IaC można zautomatyzować aprowizacji platformy i wdrażania aplikacji. Zasadniczo stosuje się praktyki inżynierii oprogramowania, takie jak testowanie i przechowywanie wersji do praktyk DevOps. Infrastruktura i wdrożenia są zautomatyzowane, spójne i powtarzalne.

### <a name="automating-infrastructure"></a>Automatyzacja infrastruktury

Narzędzia, takie jak [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/), Terraform i azure [cli](https://docs.microsoft.com/cli/azure/), umożliwiają deklaratywnie skrypt infrastruktury chmury, której potrzebujesz. Nazwy zasobów, lokalizacje, pojemności i wpisy tajne są parametryzowane i dynamiczne. Skrypt jest wersjona i sprawdzany w formancie źródła jako artefakt projektu. Wywołanie skryptu do aprowizowania spójnej i powtarzalnej infrastruktury w środowiskach systemowych, takich jak kontrola jakości, przemieszczania i produkcji.

Pod maską, IaC jest idempotentny, co oznacza, że można uruchomić ten sam skrypt w kółko bez skutków ubocznych. Jeśli zespół musi wprowadzić zmiany, edytuje i ponownie uruchom skrypt. Dotyczy to tylko zaktualizowanych zasobów.

W artykule [What is Infrastructure as Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), Autor Sam Guckenheimer opisuje, jak, "Zespoły, które implementują IaC może dostarczyć stabilne środowiska szybko i na dużą skalę. Zespoły uniknąć ręcznej konfiguracji środowisk i wymusić spójność, reprezentując żądany stan ich środowisk za pomocą kodu. Wdrożenia infrastruktury z IaC są powtarzalne i zapobiegają problemom ze środowiska uruchomieniowego spowodowanym przez dryf konfiguracji lub brakujące zależności. Zespoły DevOps mogą współpracować z ujednoliconym zestawem praktyk i narzędzi do dostarczania aplikacji i ich infrastruktury pomocniczej szybko, niezawodnie i na dużą skalę."

### <a name="automating-deployments"></a>Automatyzacja wdrożeń

[Aplikacja Dwunastocełowe,](https://12factor.net/)omówione wcześniej, wymaga oddzielnych kroków podczas przekształcania ukończonego kodu do uruchomionej aplikacji.

> *Współczynnik \#5* określa, że "Każda wersja musi wymusić ścisłe oddzielenie między etapami kompilacji, zwalniania i uruchamiania. Każdy z nich powinien być oznaczony unikalnym identyfikatorem i obsługiwać możliwość wycofania się."

Nowoczesne systemy ciągłej integracji/ciągłego wdrażania pomagają spełnić tę zasadę. Zapewniają one oddzielne kroki wdrażania i zapewniają spójny i wysokiej jakości kod, który jest łatwo dostępny dla użytkowników.

Rysunek 1-8 przedstawia separację w procesie wdrażania.

![Kroki wdrażania w potoku ciągłej integracji/ciągłego wdrażania](./media/build-release-run-pipeline.png)

**Rysunek 1-8**. Kroki wdrażania w potoku ciągłej integracji/ciągłego wdrażania

W poprzednim rysunku należy zwrócić szczególną uwagę na oddzielenie zadań.

Deweloper konstruuje funkcję w ich środowisku programistycznym, iteracji za pośrednictwem tego, co nazywa się "wewnętrzną pętlę" kodu, uruchom i debugowania. Po zakończeniu ten kod jest *wypychany* do repozytorium kodu, takich jak GitHub, Azure DevOps lub BitBucket.

Wypychanie wyzwala etap kompilacji, który przekształca kod w artefakt binarny. Praca jest realizowana za pomocą potoku [ciągłej integracji (CI).](https://martinfowler.com/articles/continuousIntegration.html) Automatycznie tworzy, testuje i pakuje aplikację.

Etap wydania pobiera artefakt binarny, stosuje informacje o konfiguracji aplikacji zewnętrznej i środowiska i tworzy niezmienne zwolnienie. Wydanie jest wdrażane w określonym środowisku. Praca jest realizowana za pomocą potoku [ciągłej dostawy(CD).](https://martinfowler.com/bliki/ContinuousDelivery.html) Każda wersja powinna być identyfikowalna. Można powiedzieć, "To wdrożenie jest uruchomiony w wersji 2.1.1 aplikacji."

Na koniec zwolniona funkcja jest uruchamiana w środowisku wykonywania docelowego. Wersje są niezmienne, co oznacza, że każda zmiana musi utworzyć nową wersję.

Stosując te praktyki, organizacje radykalnie ewoluowały w sposób, w jaki wysyłają oprogramowanie. Wiele z nich przeniosło się z wersji kwartalnych do aktualizacji na żądanie. Celem jest, aby złapać problemy na początku cyklu rozwoju, gdy są one tańsze, aby naprawić. Im dłuższy czas trwania między integracjami, tym droższe problemy stają się rozwiązywać.  Dzięki spójności procesu integracji zespoły mogą częściej zatwierdzać zmiany kodu, co prowadzi do lepszej współpracy i jakości oprogramowania.

### <a name="azure-pipelines"></a>Azure Pipelines

Chmura platformy Azure zawiera nową usługę ciągłej integracji/ciągłego wdrażania o [prawach platformy Azure Pipelines](https://azure.microsoft.com/services/devops/pipelines/), która jest częścią oferty [Azure DevOps](https://azure.microsoft.com/services/devops/) przedstawionej na rysunku 1-9.

![Potoki platformy Azure w programach DevOps](./media/devops-components.png)

**Rysunek 1-9**. Oferta Azure DevOps

Usługa Azure Pipelines to usługa w chmurze, która łączy ciągłą integrację (CI) i ciągłe dostarczanie (CD). Możesz automatycznie przetestować, skompilować i wysłać kod do dowolnego obiektu docelowego.

Definiujesz potok w kodzie w pliku YAML wraz z resztą kodu dla aplikacji.

- Potok jest wersjona z kodem i jest zgodny z tą samą strukturą rozgałęzienia.
- Otrzymasz sprawdzanie poprawności zmian za pośrednictwem przeglądów kodu w żądaniach ściągnięcia i zasad kompilacji gałęzi.
- Każda gałąź, której używasz, można dostosować zasady kompilacji, modyfikując plik azure-pipelines.yml.
- Plik potoku jest sprawdzany w kontroli wersji i można go zbadać, jeśli występuje problem.

Usługa Azure Pipelines obsługuje większość dostawców git i może generować potoki wdrażania dla aplikacji napisanych na platformach Linux, macOS lub Windows. Obejmuje obsługę java, .NET, JavaScript, Python, PHP, Go, XCode i C++.

>[!div class="step-by-step"]
>[Poprzedni](introduction.md)
>[następny](candidate-apps.md)
