---
title: "Projektowanie zorientowane na DDD mikrousługi"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Projektowanie zorientowane na DDD mikrousługi"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 38b65bc6752dd8b6ed4083c0bc5a5eccabcffbcc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="designing-a-ddd-oriented-microservice"></a>Projektowanie zorientowane na DDD mikrousługi

Projektowanie oparte na domenie (DDD) zaleca modelowania w oparciu firm jako istotne dla Twojej przypadki użycia zasobów rzeczywistymi. W kontekście tworzenia aplikacji DDD zawiera informacje o problemach jako domeny. Opisuje obszarów problemów niezależne jako kontekstów ograniczone (każdy kontekst ograniczone skorelowany mikrousługi) i jest kładzie nacisk wspólnego języka aby porozmawiać na temat tych problemów. Podano tu także wiele zagadnienia techniczne i wzorców, takich jak jednostki domeny przy użyciu zaawansowanych modeli (nie [modelu domeny anemic](https://martinfowler.com/bliki/AnemicDomainModel.html)), wartość obiektów, agreguje i agregacji główny (lub podmiot główny) reguły do obsługi wewnętrznej implementacji. W tej sekcji przedstawiono projekt i implementację wewnętrzne zaczną obowiązywać.

Czasami te reguły techniczne DDD i wzorce są postrzegane jako przeszkód, które mają problemy z ich opanowaniem nauki implementacji metod DDD. Ale ważnym elementem jest nie wzorców, ale organizowania kodu, więc jest wyrównywany do problemów biznesowych i przy użyciu tych samych warunków biznesowych (powszechny language). Ponadto podejścia DDD powinny być stosowane tylko wtedy, gdy wdraża mikrousług złożonych reguł biznesowych znaczące. Obowiązki prostszy, takich jak usługi CRUD, można zarządzać za pomocą metod prostsze.

Gdzie ma zostać narysowany granice jest klucza zadań podczas projektowania i definiowania mikrousługi. Wzorce DDD pomaga w zrozumieniu złożoności w domenie. Dla modelu domeny dla każdego z ograniczonym kontekstu identyfikowanie i definiowanie jednostek, obiekty wartości i wartości zagregowane, które modelu domeny. Skompiluj i Dostosuj modelu domeny, który znajduje się w obrębie granicy, który definiuje kontekstu. I jest bardzo jawne w formie mikrousługi. Składniki w tych granicach przechodzili są Twoje mikrousług, chociaż w niektórych przypadkach a BC lub mikrousług biznesowych może składać się z kilku usług fizycznych. DDD dotyczy granice i są mikrousług.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Zachowaj mikrousługi granice kontekstu stosunkowo mały

Określanie, gdzie umieścić granicę między ograniczone kontekstów równoważy dwóch celów konkurencyjnych. Najpierw chcesz początkowo utworzyć najmniejsza możliwa mikrousług, chociaż nie powinny zostać sterownik main; należy utworzyć obramowanie rzeczy, które wymagają spójności. Po drugie chce się uniknąć chatty komunikacji między mikrousług. Tych celów mogą być sprzeczne z sobą. Należy je równoważenie przez decomposing systemu na tyle mały mikrousług, jak to możliwe, aż zostanie wyświetlony granice komunikacji szybko rośnie z każdego dodatkowych prób do oddzielania nowy kontekst ograniczone. Spójności jest klucz w pojedynczym kontekście ograniczone.

Jest on podobny do [Intimacy nieodpowiedni kod zapachu](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) podczas implementowania klas. Jeśli dwa mikrousług potrzeba znacznie współpracują ze sobą, prawdopodobnie powinny być tym samym mikrousługi.

Innym sposobem na niego jest autonomiczne. Jeśli mikrousługi należy zależą od innej usługi bezpośrednio obsługi żądania, nie jest rzeczywiście autonomicznego.

## <a name="layers-in-ddd-microservices"></a>Warstwy mikrousług DDD

Większość aplikacji przedsiębiorstwa firma i złożonością techniczne wynika z wielu warstw. Warstwy są artefaktu logicznych i nie są związane z wdrożenia usługi. Istnieją one pomóc deweloperom w zarządzaniu złożonością w kodzie. Różnych warstwach (na przykład warstwy modelu domeny i warstwę prezentacji, itp.) może być różnych typów, które ma tłumaczenie między tymi typami.

Na przykład jednostki można załadować z bazy danych. Następnie część informacji lub zagregowane informacje dodatkowe dane z innymi obiektami, mogą być wysyłane do klienta Interfejsu API sieci Web REST. Punkt, w tym miejscu jest jednostką domeny znajduje się w ramach warstwy modelu domeny oraz nie powinien propagowane do innych obszarów, które nie należy ona do, tak samo, jak do warstwy prezentacji.

Ponadto musisz mieć zawsze prawidłowe jednostki (zobacz [projektowania poprawności warstwy modelu domeny](#designing-validations-in-the-domain-model-layer) sekcji) kontrolowane przez korzenie agregacji (jednostek głównego). W związku z tym jednostki powinien nie można powiązać z widokami klienta, ponieważ na poziomie interfejsu użytkownika część danych może nadal nie można sprawdzić poprawności. Jest to co ViewModel dla. ViewModel to model danych wyłącznie na potrzeby warstwy prezentacji. Jednostek domeny nie należy bezpośrednio do ViewModel. Zamiast tego potrzebne jest tłumaczenie między jednostkami ViewModels i domeny i na odwrót.

Kiedy realizowanie złożoności, ważne jest, aby mieć modelu domeny kontrolowane przez katalogi agregacji upewnij się, że wszystkie invariants i reguły związane z tej grupy jednostek (agregacji) są wykonywane za pośrednictwem punktu pojedynczy wpis lub bramy, głównego agregacji.

Rysunek 9-5 zawiera implementowania warstwowego projektu w aplikacji eShopOnContainers.

![](./media/image6.png)

**Rysunek 9-5**. Warstwy DDD porządkowania mikrousługi w eShopOnContainers

Chcesz zaprojektować system tak, aby każda warstwa komunikuje się tylko z niektórych innych warstw. Może to być łatwiejsze do wymuszania Jeśli warstwy są zaimplementowane jako biblioteki inną klasę, ponieważ wyraźnie określenie, jakie zależności są ustawione między bibliotekami. Na przykład warstwy modelu domeny nie powinna przyjmować zależności na inną warstwę (klasy modelu domeny powinien być zwykłym stare obiekty CLR lub [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), klasy). Jak pokazano w rysunku 9-6 **Ordering.Domain** Biblioteka warstwy ma zależności tylko w przypadku bibliotek .NET Core i pakiety NuGet, ale nie na inne niestandardowe biblioteki, takich jak dane biblioteki lub biblioteki trwałości.

![](./media/image7.PNG)

**Rysunek 9 – 6**. Warstwy zaimplementowana bibliotek zapewnić lepszą kontrolę zależności między warstwami

### <a name="the-domain-model-layer"></a>Warstwa modelu domeny

Marek Evans znakomity książki [konstrukcyjnych domeny](http://domainlanguage.com/ddd/) mówi następujące o warstwy modelu domeny i warstwy aplikacji.

**Warstwa modelu domeny**: odpowiedzialny za reprezentujący założeń biznesowych, informacje dotyczące sytuacji i reguł biznesowych. Stanu, które odzwierciedla sytuacji jest kontrolowany i używane w tym miejscu, mimo że szczegóły techniczne jego przechowywania mają delegowane do infrastruktury. Ta warstwa jest centralnym oprogramowanie firm.

Warstwa modelu domeny jest, gdzie jest wyrażone biznesowe. Po zaimplementowaniu mikrousługi warstwy modelu domeny w środowisku .NET tej warstwie jest zakodowane jako biblioteki klas z jednostkami domeny, które przechwytują dane oraz zachowanie (metody z logiką).

Po [nieznajomości trwałości](http://deviq.com/persistence-ignorance/) i [nieznajomości infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) zasady, tej warstwy należy całkowicie Ignoruj szczegóły trwałość danych. Te zadania trwałości powinny być wykonywane przez warstwę infrastruktury. W związku z tym ta warstwa nie powinna przyjmować zależności bezpośrednich w infrastrukturze, co oznacza, że reguła ważne jest należy klas entity model domeny [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Jednostek domeny nie powinien mieć żadnych zależności bezpośrednich (np. wynikające z klasy podstawowej) w dowolnej architektury infrastruktury dostępu do danych Entity Framework lub NHibernate. Najlepiej, jeśli obiekty domeny powinien nie implementować lub pochodzić od dowolnego typu zdefiniowanego w dowolnej architektury infrastruktury.

Większość nowoczesnych struktur ORM, takich jak Entity Framework Core Zezwalaj takie podejście, tak, aby w klasach modeli domeny nie są powiązane infrastruktury. Jednak po jednostki POCO nie zawsze jest możliwe podczas korzystania z niektórych baz danych NoSQL i platform, takich jak złośliwych użytkowników i niezawodne kolekcji w sieci szkieletowej usług Azure.

Nawet wtedy, gdy jest to ważne jest, aby postępuj zgodnie z zasadą nieznajomości trwałości dla modelu domeny, nie należy zignorować dotyczy trwałości. Nadal jest bardzo ważne zrozumieć modelu danych fizycznych i sposób mapowania modelu obiektu jednostki. W przeciwnym razie można tworzyć projektów niemożliwe.

Ponadto oznacza to, możesz pobrać model przeznaczony do relacyjnej bazy danych i bezpośrednio Przenieś go do NoSQL lub zorientowane na dokument bazy danych. W niektórych modeli entity model mogą mieścić, ale zwykle nie. Ograniczenia, które modelu jednostki musi być zgodne, na podstawie zarówno na technologii magazynowania i technologii ORM nadal istnieją.

### <a name="the-application-layer"></a>Warstwa aplikacji

Przechodzi do warstwy aplikacji, możemy ponownie cytowanych książki marek Evans [konstrukcyjnych domeny](http://domainlanguage.com/ddd/):

**Warstwa aplikacji:** definiuje zadań oprogramowania powinien wykonać i kieruje obiektów domeny obszerne opracowywanie problemów. Zadania, które ta warstwa jest odpowiedzialny za są przydatne w firmie lub niezbędne do interakcji z warstwy aplikacji innych systemów. Ta warstwa jest przechowywana elastycznej. Nie zawiera reguły biznesowe lub wiedzy, ale tylko współrzędne zadań i delegatów pracy definicje współpracy obiektów domeny w warstwie dalej w dół. Nie ma stanu w czasie wykonywania odbicia sytuacji, ale może mieć stanu, które odzwierciedla postęp zadania użytkownika lub programu.

Mikrousługi warstwy aplikacji w środowisku .NET jest często zakodowane jako projekt interfejsu API platformy ASP.NET Core sieci Web. Projekt implementuje mikrousługi interakcji, zdalny dostęp do sieci i użycia w aplikacji klienta lub interfejsu użytkownika zewnętrznego interfejsów API sieci Web. Obejmuje on zapytania, jeśli przy użyciu CQRS podejścia polecenia zaakceptowane mikrousługi, a nawet sterowane zdarzeniami komunikację między mikrousług (integracji zdarzeń). ASP.NET interfejsu API sieci Web Core, który reprezentuje warstwy aplikacji nie może zawierać reguł biznesowych lub wiedzy domeny (szczególnie zasad domeny dla transakcji lub aktualizacji); te powinny należeć do biblioteki klas modelu domeny. Współrzędna tylko musi warstwy aplikacji zadania i nie może przechowywania ani zdefiniować każdy stan domeny (model domeny). Deleguje ona wykonywanie reguły biznesowe do domeny modelu klas sami (łączny katalogów głównych i jednostek domeny), które ostatecznie spowoduje zaktualizowanie danych w ramach tych jednostek domeny.

Zasadniczo logiki aplikacji jest, gdzie wdrożenia wszystkich przypadków użycia, które są zależne od danego frontonu. Na przykład implementacja związane z usługą sieci Web interfejsu API.

Celem jest, że logikę domeny warstwy modelu domeny, jego invariants, model danych i reguły biznesowe pokrewnych musi być całkowicie niezależna od warstwy prezentacji i aplikacji. Najbardziej, warstwy modelu domeny nie bezpośrednio zależy od dowolnej architektury infrastruktury.

### <a name="the-infrastructure-layer"></a>Warstwa infrastruktury

Warstwa infrastruktury jest, jak dane, które jest początkowo utrzymywana w domenie jednostki (w pamięci) jest trwały z baz danych lub innego magazynu trwałego. Przykładem jest przy użyciu kodu programu Entity Framework Core do zaimplementowania klasy wzorca repozytorium, korzystających z elementu DBContext do utrwalenia danych relacyjnej bazy danych.

Zgodnie z wcześniej wspomniano [nieznajomości trwałości](http://deviq.com/persistence-ignorance/) i [nieznajomości infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) zasad, warstwie infrastrukturze musi nie "skażenia" warstwy modelu domeny. Funkcja klasy entity model domeny od infrastruktury używanej do utrwalenia danych (EF lub innych framework) muszą być stale nie biorąc pod uwagę twardych zależności struktury. Biblioteki klas warstwy modelu domeny powinien mieć tylko kod domeny, po prostu [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) jednostki klasy Implementowanie Puls oprogramowania i całkowicie całkowicie niezależna od technologii infrastruktury.

W związku z tym z warstwy lub bibliotek klas i projektów ostatecznie zależy od warstwą modelu domeny (biblioteki), nie odwrotnie, jak pokazano w rysunek 9-7.

![](./media/image8.png)

**Rysunek 9-7**. Zależności między warstwami w DDD

W tym projekcie warstwy powinny być niezależne dla każdego mikrousługi. Jak wspomniano wcześniej, można zaimplementować najbardziej złożonych mikrousług po wzorce DDD podczas implementowania prostsze opartych na danych mikrousług (proste CRUD w pojedynczej warstwie) w prostszy sposób.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **DevIQ. Zasada nieznajomości trwałości**
    [*http://deviq.com/persistence-ignorance/*](http://deviq.com/persistence-ignorance/)

-   **Oren Eini. Infrastruktura nieznajomości**
    [*https://ayende.com/blog/3137/infrastructure-ignorance*](https://ayende.com/blog/3137/infrastructure-ignorance)

-   **Angel Lopez. Architektura w projekcie oparte na domenie z warstwami**
    [*https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/*](https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/)


>[!div class="step-by-step"]
[Poprzednie] (cqrs mikrousługi reads.md) [dalej] (ruch model.md mikrousługi domeny)
