---
title: Projektowanie mikrousługi zorientowanej na wzorzec DDD
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Dowiedz się, projekt szeregowania mikrousługi zorientowanej na wzorzec DDD i warstwy aplikacji.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 65a1a58d0c70c7e788aea420006c1ad617628f93
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145611"
---
# <a name="design-a-ddd-oriented-microservice"></a>Projektowanie mikrousługi zorientowanej na wzorzec DDD

Projektowania opartego na domenach (DDD) promuje modelowania oparte na rzeczywistości firm jako istotne dla Twojej przypadki użycia. W kontekście tworzenia aplikacji DDD opowiada o problemach jako domeny. Opisano w nim obszarów problemów niezależnych jako ograniczone konteksty (każdego kontekstu ograniczonego skorelowany mikrousługi) oraz podkreśla języka wspólnego, aby porozmawiać na temat tych problemów. Podano tu także wiele zagadnienia techniczne i wzorców, takich jak jednostki domeny przy użyciu zaawansowanych modeli (nie [modelu domeny anemic](https://martinfowler.com/bliki/AnemicDomainModel.html)), wartość obiektów, agregacje i agregacji głównego (lub jednostkę główną) reguły do obsługi wewnętrznej implementacji. Ta sekcja wprowadza projektowania i implementacji tych wzorców wewnętrznego.

Czasami te reguły techniczne DDD i wzorce są postrzegane jako wąskich gardeł mających intensywnego szkolenia dotyczące implementowania DDD podejścia. Jednak ważnym elementem jest nie wzorów, ale organizowania kodu, dzięki czemu jest wyrównany do problemów biznesowych i przy użyciu tych samych warunków firmy (wszechobecne language). Ponadto podejścia DDD powinny być stosowane tylko wtedy, gdy w przypadku wdrażania złożonych mikrousługach reguły biznesowe znaczące. Prostsze odpowiedzialności, takim jak usługa CRUD, można zarządzać za pomocą metod prostsze.

Gdzie mają być wyznaczone granice to kluczowe zadania podczas projektowania i definiowania mikrousługi. Wzorców DDD ułatwiają zrozumienie złożoności w domenie. W przypadku modelu domeny dla każdego kontekstu ograniczonego identyfikować i definiowanie jednostek, obiekty wartości i wartości zagregowane, które modelują domenę. Twórz i uściślić modelu domeny, który znajduje się w granicach, który definiuje kontekst. I to już bardzo jawne w postaci mikrousług. Składniki w tych granicach znajdą się są mikrousługi, chociaż w niektórych przypadkach a BC lub mikrousług firmy może składać się z kilku usług fizycznych. DDD dotyczy granice i dlatego są mikrousług.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Zachowaj mikrousług granic kontekstowych stosunkowo mały

Określanie miejsca umieszczenia granic między ograniczone konteksty równoważy dwóch celów konkurencyjnych. Najpierw chcesz utworzyć początkowo najmniejsza możliwa mikrousług, ale który nie powinien być sterownik main; należy utworzyć obramowanie wokół rzeczy, które wymagają spójności. Po drugie chcesz uniknąć duża liczba komunikacji między mikrousługami. Cele te mogą być siebie nawzajem. Należy je saldo przez podzielenie systemu na tyle mały mikrousługi, jak to możliwe, aż zobaczysz granice komunikacji szybko rośnie z kolejnymi próbami dodatkowe do oddzielania nowy kontekst ograniczone. Spójności jest kluczem w ramach pojedynczego kontekstach.

Jest on podobny do [Intimacy nieodpowiedni kod zapachu](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) podczas implementowania klas. Jeśli potrzebujesz mikrousług dwóch znacznie współpracować ze sobą, należy prawdopodobnie będzie tego samego mikrousług.

Innym sposobem na niego jest autonomii. Jeśli mikrousługi muszą polegać na inną usługę bezpośrednio zrealizować żądania, nie jest naprawdę autonomicznego.

## <a name="layers-in-ddd-microservices"></a>Warstwy w mikrousługach DDD

Większość aplikacji przedsiębiorstwa znaczące biznesowe i techniczne złożonością są definiowane przez wiele warstw. Warstwy są logicznej artefaktów i nie są związane z wdrożeniem usługi. Istnieją one w celu ułatwienia deweloperom zarządzanie złożonością w kodzie. Różne warstwy (np. warstwy modelu domeny i Warstwa prezentacji, itp.), może być różnych typów nakładającego obowiązek tłumaczeń między tymi typami.

Na przykład jednostka mogła być załadowana z bazy danych. Następnie część tych informacji lub zagregowane informacje w tym dodatkowe dane z innymi jednostkami mogą być wysyłane do klienta interfejsu użytkownika za pośrednictwem internetowego interfejsu API REST. Punkt, w tym miejscu jest, że jednostka domeny znajduje się w warstwie modelu domeny i nie powinien propagowane do innych obszarów, które go nie należy do, takie jak do warstwy prezentacji.

Ponadto musisz mieć zawsze prawidłowe jednostki (zobacz [projektowanie reguł weryfikacji w warstwie modelu domeny](domain-model-layer-validations.md) sekcji) w wartości clientauthtrustmode korzenie agregacji (jednostki głównej). W związku z tym jednostek powinna nie można powiązać z widokami klienta, ponieważ na poziomie interfejsu użytkownika niektóre dane mogą nadal nie można sprawdzić poprawności. Jest to, co to jest ViewModel. ViewModel jest model danych, wyłącznie na potrzeby warstwy prezentacji. Jednostki domeny nie należy bezpośrednio do ViewModel. Zamiast tego należy do tłumaczenia między jednostkami modele widoków i domeny i na odwrót.

Kiedy realizowanie złożoność, ważne jest, aby mieć modelu domeny w wartości clientauthtrustmode agregacji elementy główne, które upewnij się, że invariants i reguły związane z tej grupy jednostek (agregacji) są wykonywane za pośrednictwem punktem pojedynczy wpis lub bramy, głównego agregacji.

Rysunek 7-5 zawiera implementacji warstwowej projektu w ramach aplikacji eShopOnContainers aplikacji.

![Trzy warstwy w mikrousługach DDD, takie jak porządkowanie. Każda warstwa jest projektem programu VS: Warstwa aplikacji jest Ordering.API, warstwa domeny jest Ordering.Domain i warstwy infrastruktury jest Ordering.Infrastructure.](./media/image6.png)

**Rysunek 7-5**. Warstwy DDD w mikrousługach sortowania, w ramach aplikacji eShopOnContainers

Użytkownik chce zaprojektować systemu, tak, aby każda warstwa komunikuje się tylko w przypadku niektórych innych warstw. Może to być łatwiejsze do wymuszania Jeśli warstwy są implementowane jako biblioteki innej klasy, ponieważ jednoznacznie zidentyfikować, jakie zależności są ustawione między bibliotekami. Na przykład warstwie modelu domeny nie powinna przyjmować zależności na wszystkich innych warstwach (klasy modelu domeny powinny być zwykłych starych obiektów CLR lub [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), klasy). Jak pokazano w rysunek 7 – 6 **Ordering.Domain** biblioteki warstwy ma zależności tylko w bibliotekach .NET Core lub pakiety NuGet, ale nie w innych niestandardową biblioteką, takich jak dane biblioteki lub bibliotekę trwałości.

![Widok Eksploratora rozwiązań Ordering.Domain zależności, tylko wyświetleniem zależy od biblioteki .NET Core.](./media/image7.png)

**Rysunek 7 – 6**. Warstwy zaimplementowane dopuszcza bibliotek lepszą kontrolę nad zależności między warstwami

### <a name="the-domain-model-layer"></a>Warstwie modelu domeny

Eric Evans doskonałą książki [projektowania opartego na domenie](https://domainlanguage.com/ddd/) mówi następujące o warstwie modelu domeny i warstwy aplikacji.

**Warstwie modelu domeny**: Odpowiada za reprezentujący koncepcji biznesowych, informacje o sytuacja biznesowa i reguł biznesowych. Stan, który odzwierciedla sytuacja biznesowa jest kontrolowany i używane w tym miejscu, mimo że szczegóły techniczne jego przechowywania są delegowane do infrastruktury. Ta warstwa jest Sercem oprogramowania dla firm.

Warstwie modelu domeny jest, gdzie jest wyrażone firmy. Podczas implementowania warstwie modelu domeny mikrousługi na platformie .NET, warstwa ta jest zakodowane jako bibliotekę klas przy użyciu jednostek domeny, które zbierają dane, a także zachowanie (metody z logiką).

Następujące [nieznajomości trwałości](https://deviq.com/persistence-ignorance/) i [nieznajomości infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) zasady, tej warstwy należy całkowicie Ignoruj Szczegóły stanu trwałego danych. Te zadania trwałości powinna być wykonywana przez warstwę infrastruktury. Dlatego ta warstwa nie powinna przyjmować zależności bezpośrednich w infrastrukturę, która oznacza, że regułę ważne jest, należy klasach jednostki modeli domeny [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Jednostki domeny nie powinna mieć żadnych zależności bezpośrednich (na przykład pochodząca z klasy bazowej) w dowolnej architektury infrastruktury dostępu do danych Entity Framework lub NHibernate. W idealnym przypadku jednostki domeny powinien nie implementować lub pochodzić od dowolnego typu zdefiniowane w dowolnej architektury infrastruktury.

Większość nowoczesnych środowisk ORM, takich jak Entity Framework Core zezwala na takie podejście, tak, aby w klasach modeli domeny nie są powiązane w infrastrukturze. Jednak posiadanie jednostki POCO nie zawsze jest możliwe podczas korzystania z niektórych baz danych NoSQL i struktur, takich jak aktorów i elementów Reliable Collections w usłudze Azure Service Fabric.

Nawet w przypadku, gdy jest to ważne, aby zasadę nieznajomości stan trwały modelu domeny, możesz nie zignorować wątpliwości trwałości. Nadal jest bardzo ważne poznać model danych fizycznych i sposób mapowania modelu obiektu jednostki. W przeciwnym razie można tworzyć projekty niemożliwe.

Ponadto nie oznacza to, możesz wykonać model przeznaczony do relacyjnej bazy danych i przenieś ją bezpośrednio NoSQL lub korzystający z dokumentów bazy danych. W niektórych modelach jednostki może spełniać modelu, ale zazwyczaj tak nie jest. Nadal występują ograniczenia, które modelu entity muszą być zgodne, oparte na technologii magazynowania i technologii ORM.

### <a name="the-application-layer"></a>Warstwa aplikacji

Przejście do warstwy aplikacji, firma Microsoft może ponownie zacytować książki Eric Evans [projektowania opartego na domenie](https://domainlanguage.com/ddd/):

**Warstwa aplikacji:** Definiuje zadań oprogramowania powinien zrobić i kieruje obiektów ekspresyjny domeny, aby sprawdzić problemy. Zadania, które ta warstwa jest odpowiedzialny za są zrozumiałe dla firmy lub niezbędne do interakcji z warstw aplikacji z innymi systemami. Ta warstwa jest przechowywana alokowania elastycznego. Zawiera reguły biznesowe lub wiedzy przedsiębiorstwa, ale tylko zadania współrzędnych i delegatów działa współpraca obiektów domeny w następnej warstwie w dół. Nie ma stanu odzwierciedlający sytuacja biznesowa, ale może mieć stan, który będzie odzwierciedlać postęp zadania dla użytkownika lub programu.

Warstwy aplikacji mikrousług na platformie .NET jest często zakodowane jako projekt internetowego interfejsu API platformy ASP.NET Core. Projekt implementuje interakcji mikrousług, zdalny dostęp do sieci i zewnętrzne interfejsy API sieci Web użycia w aplikacji interfejsu użytkownika lub klienta. W przypadku używania podejścia CQRS podejście poleceń akceptowanych przez mikrousług, a nawet oparte na zdarzeniach komunikację między mikrousługami (zdarzenia integracji), zawiera kwerendy. ASP.NET Core internetowy interfejs API reprezentujący warstwy aplikacji nie może zawierać reguł biznesowych lub wiedzy specjalistycznej (szczególnie zasad domeny dla transakcji lub aktualizacji); te powinny należeć do biblioteki klas modelu domeny. Współrzędna tylko musi warstwy aplikacji zadań i musi nie przechowują i zdefiniuj dowolny stan domeny (model domeny). Deleguje ona wykonywanie reguły biznesowe modelu klas domeny samodzielnie (agregacji katalogów głównych i jednostki domeny), które ostatecznie spowoduje zaktualizowanie danych w tych jednostkach domeny.

Po prostu logika aplikacji jest, gdzie możesz wdrożyć wszystkie przypadki użycia, które są zależne od danego frontonu. Na przykład implementacja związane z usługą internetowego interfejsu API.

Celem jest, że logika domeny w warstwie modelu domeny, jego invariants, modelu danych i reguł biznesowych powiązane musi być całkowicie niezależne od warstwy prezentacji i aplikacji. Przede wszystkim warstwie modelu domeny nie może bezpośrednio zależeć od dowolnej architektury infrastruktury.

### <a name="the-infrastructure-layer"></a>Warstwa infrastruktury

Warstwa infrastruktury jest o tym, jak dane, które początkowo są przechowywane w jednostkach domeny (w pamięci) są utrwalane w bazach danych lub innym magazynie trwałym. Przykładem jest za pomocą kodu platformy Entity Framework Core do zaimplementowania klasy wzorzec repozytorium, które umożliwia utrwalanie danych w relacyjnej bazie danych typu DBContext.

Zgodnie z wymienionych wcześniej [nieznajomości trwałości](https://deviq.com/persistence-ignorance/) i [nieznajomości infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) zasad, warstwy infrastruktury musi nie "skażenie" warstwie modelu domeny. Pochodzącego od dowolnego domeny modelu jednostki klasy musi przechowywać z infrastruktury, która umożliwia utrwalanie danych (EF lub innych framework), nie biorąc pod uwagę zależności twardych struktur. Biblioteki klas warstwy modelu domeny powinien mieć tylko Twój kod domeny, po prostu [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) jednostki klasy Implementowanie serce oprogramowania i całkowicie całkowicie niezależna od technologii infrastruktury.

W związku z warstwy lub biblioteki klas i projekty ostatecznie powinna zależeć od warstwie modelu domeny (biblioteki), nie na odwrót, jak pokazano w rysunek 7 – 7.

![Zależności usługi DDD, warstwy aplikacji zależy od domeny i infrastruktury i infrastruktury jest zależny od domeny, ale domeny nie zależy od żadnej warstwy.](./media/image8.png)

**Rysunek 7-7**. Zależności między warstwami w DDD

W tym projekcie warstwy powinny być niezależne dla poszczególnych mikrousług. Jak wspomniano wcześniej, można zaimplementować mikrousługi najbardziej złożonych następujące wzorców DDD podczas implementowania prostsze opartych na danych mikrousługi (proste CRUD w pojedynczej warstwie) w prostszy sposób.

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **DevIQ. Zasada nieznajomości trwałości** \
  [*https://deviq.com/persistence-ignorance/*](https://deviq.com/persistence-ignorance/)

- **Oren Eini. Nieznajomości infrastruktury** \
  [*https://ayende.com/blog/3137/infrastructure-ignorance*](https://ayende.com/blog/3137/infrastructure-ignorance)

- **Angel Lopez. Architektury warstwowej w projektowania opartego na domenie** \
  [*https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/*](https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/)

>[!div class="step-by-step"]
>[Poprzednie](cqrs-microservice-reads.md)
>[dalej](microservice-domain-model.md)