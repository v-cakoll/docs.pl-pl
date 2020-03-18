---
title: Projektowanie mikrousługi zorientowanej na wzorzec DDD
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się z projektem mikrousługi porządkowej zorientowanej na DDD i jej warstw aplikacji.
ms.date: 10/08/2018
ms.openlocfilehash: c5ac55978ca979a3ae055d9b0cd2d3c6b3187b4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401698"
---
# <a name="design-a-ddd-oriented-microservice"></a>Projektowanie mikrousługi zorientowanej na DDD

Projekt oparty na domenie (DDD) zaleca modelowanie w oparciu o rzeczywistość firmy jako istotne dla przypadków użycia. W kontekście tworzenia aplikacji DDD mówi o problemach jako domenach. Opisuje niezależne obszary problemowe jako ograniczone konteksty (każdy ograniczony kontekst koreluje z mikrousługą) i podkreśla wspólny język, aby porozmawiać o tych problemach. Sugeruje również wiele koncepcji technicznych i wzorców, takich jak jednostki domeny z bogatymi modelami (bez [modelu anemicznego domeny),](https://martinfowler.com/bliki/AnemicDomainModel.html)obiekty wartości, agregacje i zagregowane reguły root (lub jednostki głównej) do obsługi implementacji wewnętrznej. W tej sekcji przedstawiono projektowanie i implementację tych wzorców wewnętrznych.

Czasami te zasady techniczne ddd i wzorce są postrzegane jako przeszkody, które mają stromą krzywą uczenia się do wdrażania podejść DDD. Ale ważną częścią nie są same wzorce, ale organizowanie kodu, aby był on dostosowany do problemów biznesowych i używania tych samych terminów biznesowych (wszechobecny język). Ponadto metody DDD powinny być stosowane tylko wtedy, gdy implementujesz złożone mikrousługi ze znaczącymi regułami biznesowymi. Prostsze obowiązki, takie jak usługa CRUD, można zarządzać za pomocą prostszych podejść.

Gdzie narysować granice jest kluczowym zadaniem podczas projektowania i definiowania mikrousługi. Wzorce DDD pomagają zrozumieć złożoność w domenie. Dla modelu domeny dla każdego ograniczonego kontekstu można zidentyfikować i zdefiniować jednostki, obiekty wartości i agreguje, które modelują domenę. Tworzenie i uściślanie modelu domeny, który jest zawarty w granicach, która definiuje kontekst. I to jest bardzo jawne w postaci mikrousługi. Składniki w tych granicach kończy się mikrousług, chociaż w niektórych przypadkach bc lub mikrousług biznesowych może składać się z kilku usług fizycznych. DDD jest o granice i tak są mikrousług.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Zachować granice kontekstu mikrousług stosunkowo małe

Określanie, gdzie umieścić granice między ograniczone konteksty równoważy dwa konkurujące ze sobą cele. Po pierwsze chcesz początkowo utworzyć najmniejszą możliwą mikrousługę, chociaż nie powinno to być głównym sterownikiem; należy utworzyć granicę wokół rzeczy, które wymagają spójności. Po drugie, chcesz uniknąć chatty komunikacji między mikrousługami. Cele te mogą ze sobą zaprzeczyć. Należy zrównoważyć je, rozkładając system na tyle małych mikrousług, jak to możliwe, dopóki nie zobaczysz granice komunikacji szybko rośnie z każdej dodatkowej próby oddzielenia nowego ograniczonego kontekstu. Spójność ma kluczowe znaczenie w jednym ograniczonym kontekście.

Jest on podobny do [zapachu kodu nieodpowiedniej intymności](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) podczas wykonywania zajęć. Jeśli dwie mikrousługi muszą współpracować dużo ze sobą, prawdopodobnie powinny być tym samym mikrousług.

Innym sposobem spojrzenia na to jest autonomia. Jeśli mikrousługi musi polegać na innej usługi bezpośrednio do obsługi żądania, nie jest naprawdę autonomiczne.

## <a name="layers-in-ddd-microservices"></a>Warstwy w mikrousługach DDD

Większość aplikacji korporacyjnych o znacznej złożoności biznesowej i technicznej jest definiowana przez wiele warstw. Warstwy są artefaktem logicznym i nie są związane z wdrożeniem usługi. Istnieją one, aby pomóc deweloperom zarządzać złożonością w kodzie. Różne warstwy (takie jak warstwa modelu domeny w porównaniu z warstwą prezentacji itp.) mogą mieć różne typy, co nakazuje tłumaczenia między tymi typami.

Na przykład jednostka może być załadowany z bazy danych. Następnie część tych informacji lub agregacja informacji, w tym dodatkowe dane z innych jednostek, mogą być wysyłane do interfejsu klienta za pośrednictwem interfejsu API sieci Web REST. Chodzi o to, że jednostka domeny jest zawarta w warstwie modelu domeny i nie powinna być propagowana do innych obszarów, do których nie należy, takich jak warstwa prezentacji.

Ponadto należy mieć zawsze prawidłowe jednostki (zobacz [Projektowanie sprawdzania poprawności w sekcji warstwy modelu domeny)](domain-model-layer-validations.md) kontrolowane przez agregujące katalogi główne (jednostki główne). W związku z tym jednostki nie powinny być powiązane z widokami klienta, ponieważ na poziomie interfejsu i ze znanie interfejsu, niektóre dane mogą nadal nie zostać zweryfikowane. Jest to, co ViewModel jest dla. ViewModel jest modeldanych wyłącznie dla potrzeb warstwy prezentacji. Jednostki domeny nie należą bezpośrednio do ViewModel. Zamiast tego należy przetłumaczyć między ViewModels i jednostek domeny i na odwrót.

Podczas rozwiązywania złożoności, ważne jest, aby model domeny kontrolowane przez zagregowane katalogi główne, które upewnij się, że wszystkie niezmienne i reguły związane z tej grupy jednostek (agregacji) są wykonywane za pośrednictwem jednego punktu wejścia lub bramy, zagregowanego katalogu głównego.

Rysunek 7-5 pokazuje, jak warstwowy projekt jest implementowany w aplikacji eShopOnContainers.

![Diagram przedstawiający warstwy w mikrousługach projektowania opartych na domenie.](./media/ddd-oriented-microservice/domain-driven-design-microservice.png)

**Rysunek 7-5**. Warstwy DDD w mikrousługach porządkowych w eShopOnContainers

Trzy warstwy w mikrousługach DDD, takie jak zamawianie. Każda warstwa jest projektem VS: Warstwa aplikacji to Ordering.API, Warstwa domeny to Ordering.Domain, a warstwa Infrastruktura to Zamawianie.Infrastruktura. System ma być zaprojektowany tak, aby każda warstwa komunikowała się tylko z niektórymi innymi warstwami. To może być łatwiejsze do wymuszenia, jeśli warstwy są implementowane jako biblioteki różnych klas, ponieważ można wyraźnie określić, jakie zależności są ustawione między bibliotekami. Na przykład warstwa modelu domeny nie powinna być uzależniona od żadnej innej warstwy (klasy modelu domeny powinny być zwykłymi starymi obiektami CLR lub [klasami POCO).](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) Jak pokazano na rysunku 7-6, biblioteka warstwy **Ordering.Domain** ma zależności tylko na bibliotekach .NET Core lub pakietach NuGet, ale nie w żadnej innej bibliotece niestandardowej, takiej jak biblioteka danych lub biblioteka trwałości.

![Zrzut ekranu przedstawiający zależności Ordering.Domain.](./media/ddd-oriented-microservice/ordering-domain-dependencies.png)

**Rysunek 7-6**. Warstwy zaimplementowane jako biblioteki umożliwiają lepszą kontrolę zależności między warstwami

### <a name="the-domain-model-layer"></a>Warstwa modelu domeny

Doskonała książka Erica Evansa [Domain Driven Design](https://domainlanguage.com/ddd/) mówi o warstwie modelu domeny i warstwie aplikacji.

**Warstwa modelu domeny**: Odpowiedzialny za reprezentowanie pojęć firmy, informacji o sytuacji biznesowej i reguł biznesowych. państwo, które odzwierciedla sytuację biznesową, jest tutaj kontrolowane i wykorzystywane, mimo że szczegóły techniczne przechowywania są przekazywane do infrastruktury. Ta warstwa jest sercem oprogramowania biznesowego.

Warstwa modelu domeny jest, gdzie firma jest wyrażona. Podczas implementowania warstwy modelu domeny mikrousług w .NET, ta warstwa jest kodowana jako biblioteka klas z jednostkami domeny, które przechwytują dane plus zachowanie (metody z logiką).

Po [trwałości ignorancji](https://deviq.com/persistence-ignorance/) i zasady [ignorancji infrastruktury,](https://ayende.com/blog/3137/infrastructure-ignorance) ta warstwa musi całkowicie ignorować szczegóły trwałości danych. Te zadania trwałości powinny być wykonywane przez warstwę infrastruktury. W związku z tym ta warstwa nie powinny przyjmować bezpośrednie zależności od infrastruktury, co oznacza, że ważną regułą jest, że klasy jednostek modelu domeny powinny być [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Jednostki domeny nie powinny mieć żadnych bezpośrednich zależności (takich jak wynikające z klasy podstawowej) na wszelkie struktury infrastruktury dostępu do danych, takich jak entity framework lub NHibernate. W idealnym przypadku jednostki domeny nie powinny pochodzić od lub zaimplementować żadnego typu zdefiniowanego w ramach infrastruktury.

Większość nowoczesnych platform ORM, takich jak Entity Framework Core, zezwala na takie podejście, dzięki czemu klasy modelu domeny nie są powiązane z infrastrukturą. Jednak posiadanie jednostek POCO nie zawsze jest możliwe podczas korzystania z niektórych baz danych i struktur NoSQL, takich jak podmioty i niezawodne kolekcje w sieci szkieletowej usług Azure.

Nawet wtedy, gdy jest ważne, aby przestrzegać zasady nieznajomości trwałości dla modelu domeny, nie należy ignorować obawy trwałości. Nadal bardzo ważne jest, aby zrozumieć model danych fizycznych i jak mapuje do modelu obiektu jednostki. W przeciwnym razie można tworzyć niemożliwe projekty.

Ponadto nie oznacza to, że można wziąć model przeznaczony dla relacyjnej bazy danych i bezpośrednio przenieść go do bazy danych NoSQL lub zorientowanej na dokumenty. W niektórych modelach encji model może się zmieścić, ale zwykle nie. Nadal istnieją ograniczenia, których musi przestrzegać model jednostki, zarówno w oparciu o technologię pamięci masowej, jak i technologię ORM.

### <a name="the-application-layer"></a>Warstwa aplikacji

Przechodząc do warstwy aplikacji, możemy ponownie przytoczyć książki Eric Evans [Domain Driven Design:](https://domainlanguage.com/ddd/)

**Warstwa aplikacji:** Definiuje zadania, które oprogramowanie ma wykonywać, i kieruje obiekty domeny ekspresyjnej do wypracowania problemów. Zadania, za które odpowiada ta warstwa, mają znaczenie dla firmy lub są niezbędne do interakcji z warstwami aplikacji innych systemów. Warstwa ta jest cienka. Nie zawiera reguł biznesowych lub wiedzy, ale tylko koordynuje zadania i deleguje pracę do współpracy obiektów domeny w następnej warstwie w dół. Nie ma stanu odzwierciedlającego sytuację biznesową, ale może mieć stan, który odzwierciedla postęp zadania dla użytkownika lub programu.

Warstwa aplikacji mikrousługi w platformie .NET jest często kodowana jako ASP.NET projektu interfejsu API podstawowej sieci Web. Projekt implementuje interakcji mikrousługi, zdalny dostęp do sieci i zewnętrznych interfejsów API sieci Web używanych z interfejsu użytkownika lub aplikacji klienckich. Zawiera zapytania, jeśli przy użyciu podejścia CQRS, polecenia akceptowane przez mikrousługi, a nawet komunikacji opartej na zdarzeniach między mikrousług (zdarzenia integracji). ASP.NET core Web API reprezentujący warstwę aplikacji nie może zawierać reguł biznesowych ani wiedzy o domenie (zwłaszcza reguł domeny dla transakcji lub aktualizacji); powinny one być własnością biblioteki klas modelu domeny. Warstwa aplikacji musi koordynować tylko zadania i nie może zawierać ani definiować żadnego stanu domeny (modelu domeny). Deleguje wykonywanie reguł biznesowych do samych klas modelu domeny (zagregowane katalogi główne i jednostki domeny), które ostatecznie zaktualizują dane w ramach tych jednostek domeny.

Zasadniczo logika aplikacji jest, gdzie można zaimplementować wszystkie przypadki użycia, które zależą od danego frontonu. Na przykład implementacja związana z usługą interfejsu API sieci Web.

Celem jest, że logika domeny w warstwie modelu domeny, jej niezmienne, model danych i powiązanych reguł biznesowych musi być całkowicie niezależna od warstwy prezentacji i aplikacji. Przede wszystkim warstwy modelu domeny nie może bezpośrednio zależeć od żadnych framework infrastruktury.

### <a name="the-infrastructure-layer"></a>Warstwa infrastruktury

Warstwa infrastruktury jest jak dane, które są początkowo przechowywane w jednostkach domeny (w pamięci) jest zachowywany w bazach danych lub innego magazynu trwałego. Przykładem jest użycie kodu core struktury jednostki do implementowania klas wzorca repozytorium, które używają DBContext do utrwalenia danych w relacyjnej bazie danych.

Zgodnie z wcześniej wspomnianymi zasadami [persistence ignorancji](https://deviq.com/persistence-ignorance/) i [infrastruktury niewiedzy,](https://ayende.com/blog/3137/infrastructure-ignorance) warstwa infrastruktury nie może "zanieczyszczać" warstwy modelu domeny. Należy zachować klasy jednostki modelu domeny agnostyk z infrastruktury, która służy do utrwalania danych (EF lub innych ramach), nie biorąc twarde zależności na ramach. Biblioteka klas warstwy modelu domeny powinna mieć tylko kod domeny, tylko klasy jednostek [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) implementujące serce oprogramowania i całkowicie oddzielone od technologii infrastruktury.

W związku z tym warstwy lub biblioteki klas i projekty powinny ostatecznie zależeć od warstwy modelu domeny (biblioteki), a nie odwrotnie, jak pokazano na rysunku 7-7.

![Diagram przedstawiający zależności istniejące między warstwami usługi DDD.](./media/ddd-oriented-microservice/ddd-service-layer-dependencies.png)

**Rysunek 7-7**. Zależności między warstwami w DDD

Zależności w usłudze DDD, warstwa aplikacji zależy od domeny i infrastruktury, a infrastruktura zależy od domeny, ale domena nie zależy od żadnej warstwy. Ten projekt warstwy powinny być niezależne dla każdej mikrousługi. Jak wspomniano wcześniej, można zaimplementować najbardziej złożonych mikrousług po wzorców DDD, podczas implementowania prostsze mikrousług opartych na danych (proste CRUD w jednej warstwie) w prostszy sposób.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **DevIQ. Zasada niewiedzy o trwałości** \
  <https://deviq.com/persistence-ignorance/>

- **Oren Eini. Nieznajomość infrastruktury** \
  <https://ayende.com/blog/3137/infrastructure-ignorance>

- **Angel Lopez. Architektura warstwowa w projekcie opartym na domenie** \
  <https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/>

>[!div class="step-by-step"]
>[Poprzedni](cqrs-microservice-reads.md)
>[następny](microservice-domain-model.md)
