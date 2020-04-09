---
title: Projektowanie mikrousługi zorientowanej na wzorzec DDD
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Zrozumieć projekt mikrousługi zamawiania zorientowanych na DDD i jej warstw aplikacji.
ms.date: 10/08/2018
ms.openlocfilehash: 583e103c8bd9d828731a658ea2fd2aa0758e7a12
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988742"
---
# <a name="design-a-ddd-oriented-microservice"></a>Projektowanie mikrousług zorientowanych na DDD

Projektowanie oparte na domenie (DDD) opowiada się za modelowania w oparciu o rzeczywistość działalności, jak istotne dla przypadków użycia. W kontekście tworzenia aplikacji DDD mówi o problemach jako domenach. Opisano w nim niezależne obszary problemów jako ograniczone konteksty (każdy ograniczony kontekst koreluje z mikrousługą) i podkreśla wspólny język, aby porozmawiać o tych problemach. Sugeruje również wiele pojęć technicznych i wzorców, takich jak jednostki domeny z modelami rozszerzonymi (bez [modelu anemii domeny),](https://martinfowler.com/bliki/AnemicDomainModel.html)obiekty wartości, agregacje i agregujące reguły katalogu głównego (lub jednostki głównej) do obsługi implementacji wewnętrznej. W tej sekcji przedstawiono projektowanie i implementację tych wzorców wewnętrznych.

Czasami te zasady techniczne DDD i wzorce są postrzegane jako przeszkody, które mają stromą krzywą uczenia się do wdrażania metod DDD. Ale ważną częścią nie są same wzorce, ale organizowanie kodu, dzięki czemu jest on dostosowany do problemów biznesowych i przy użyciu tych samych terminów biznesowych (wszechobecny język). Ponadto podejścia DDD powinny być stosowane tylko wtedy, gdy implementujesz złożone mikrousługi z istotnych reguł biznesowych. Prostsze obowiązki, takie jak usługa CRUD, można zarządzać za pomocą prostszych podejść.

Gdzie narysować granice jest kluczowym zadaniem podczas projektowania i definiowania mikrousługi. Wzorce DDD pomagają zrozumieć złożoność domeny. Dla modelu domeny dla każdego ograniczonego kontekstu można zidentyfikować i zdefiniować jednostki, obiekty wartości i agreguje, że model domeny. Tworzenie i udoskonalanie modelu domeny, który znajduje się w granicach, która definiuje kontekst. I to jest bardzo wyraźne w postaci mikrousługi. Składniki w tych granicach kończy się mikrousług, chociaż w niektórych przypadkach BC lub mikrousług biznesowych może składać się z kilku usług fizycznych. DDD jest o granicach i tak są mikrousług.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Utrzymuj granice kontekstu mikrousług stosunkowo małe

Określenie, gdzie należy umieścić granice między ograniczonymi kontekstami, równoważy dwa konkurujące ze sobą cele. Najpierw chcesz początkowo utworzyć najmniejsze możliwe mikrousługi, chociaż nie powinno to być głównym sterownikiem; należy stworzyć granicę wokół rzeczy, które wymagają spójności. Po drugie chcesz uniknąć chatty komunikacji między mikrousługami. Cele te mogą być ze sobą sprzeczne. Należy je zrównoważyć przez rozkład systemu na tyle małych mikrousług, jak można, dopóki nie zobaczysz granice komunikacji szybko rośnie z każdej dodatkowej próby oddzielenia nowego ograniczonego kontekstu. Spójność ma kluczowe znaczenie w jednym ograniczonym kontekście.

Jest podobny do [nieodpowiedniego zapachu kodu intymności](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) podczas implementowania klas. Jeśli dwie mikrousługi muszą współpracować dużo ze sobą, powinny one prawdopodobnie być tej samej mikrousługi.

Innym sposobem, aby spojrzeć na to jest autonomia. Jeśli mikrousługa musi polegać na innej usłudze do bezpośredniego obsługi żądania, nie jest prawdziwie autonomiczne.

## <a name="layers-in-ddd-microservices"></a>Warstwy w mikrousługach DDD

Większość aplikacji korporacyjnych o znacznej złożoności biznesowej i technicznej jest definiowana przez wiele warstw. Warstwy są logicznym artefaktem i nie są związane z wdrożeniem usługi. Istnieją one, aby pomóc deweloperom zarządzać złożonością w kodzie. Różne warstwy (takie jak warstwa modelu domeny w porównaniu z warstwą prezentacji itp.) mogą mieć różne typy, które nakazują tłumaczenia między tymi typami.

Na przykład jednostka może być ładowana z bazy danych. Następnie część tych informacji lub agregacja informacji, w tym dodatkowych danych z innych jednostek, mogą być wysyłane do interfejsu użytkownika klienta za pośrednictwem interfejsu API sieci Web REST. Chodzi o to, że encja domeny znajduje się w warstwie modelu domeny i nie powinna być propagowana do innych obszarów, do których nie należy, takich jak warstwa prezentacji.

Ponadto należy mieć zawsze prawidłowe jednostki (zobacz Projektowanie sprawdzania poprawności w sekcji [warstwy modelu domeny)](domain-model-layer-validations.md) kontrolowane przez agregujące katalogi główne (jednostki główne). W związku z tym jednostki nie powinny być powiązane z widokami klienta, ponieważ na poziomie interfejsu użytkownika niektóre dane mogą nadal nie zostać zweryfikowane. To jest to, co ViewModel jest dla. ViewModel jest modelem danych wyłącznie dla potrzeb warstwy prezentacji. Jednostki domeny nie należą bezpośrednio do ViewModel. Zamiast tego należy przetłumaczyć między ViewModels i jednostek domeny i odwrotnie.

Podczas rozwiązywania złożoności, ważne jest, aby model domeny kontrolowane przez zagregowane korzenie, które upewnij się, że wszystkie invariants i reguły związane z tej grupy jednostek (agregacji) są wykonywane za pośrednictwem jednego punktu wejścia lub bramy, agregacji katalogu głównego.

Rysunek 7-5 pokazuje, jak projekt warstwowy jest implementowany w aplikacji eShopOnContainers.

![Diagram przedstawiający warstwy w mikrousługi projektu opartego na domenie.](./media/ddd-oriented-microservice/domain-driven-design-microservice.png)

**Rysunek 7-5**. Warstwy DDD w mikrousługach zamawiania w eShopOnContainers

Trzy warstwy w mikrousługi DDD, takie jak Kolejność. Każda warstwa jest projektem VS: warstwa aplikacji to Ordering.API, Warstwa domeny to Ordering.Domain, a warstwa Infrastruktura to Ordering.Infrastructure. System ma być tak zaprojektowywaniem, aby każda warstwa komunikowały się tylko z niektórymi innymi warstwami. To może być łatwiejsze do wyegzekwowania, jeśli warstwy są implementowane jako biblioteki różnych klas, ponieważ można wyraźnie określić, jakie zależności są ustawione między bibliotekami. Na przykład warstwa modelu domeny nie powinna uwzględniać żadnej innej warstwy (klasy modelu domeny powinny być zwykłymi starymi obiektami CLR lub klasami [POCO).](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) Jak pokazano na rysunku 7-6, biblioteka **warstwy Ordering.Domain** ma zależności tylko od bibliotek .NET Core lub pakietów NuGet, ale nie w żadnej innej bibliotece niestandardowej, takiej jak biblioteka danych lub biblioteka trwałości.

![Zrzut ekranu przedstawiający zależności w zakresie zamawiania.domeny.](./media/ddd-oriented-microservice/ordering-domain-dependencies.png)

**Rysunek 7-6**. Warstwy zaimplementowane jako biblioteki umożliwiają lepszą kontrolę zależności między warstwami

### <a name="the-domain-model-layer"></a>Warstwa modelu domeny

Doskonała książka Erica Evansa [Domain Driven Design](https://domainlanguage.com/ddd/) mówi o warstwie modelu domeny i warstwie aplikacji.

**Warstwa modelu domeny:** Odpowiedzialny za reprezentowanie pojęć firmy, informacji o sytuacji biznesowej i reguł biznesowych. Państwo, które odzwierciedla sytuację biznesową jest kontrolowane i używane w tym miejscu, mimo że szczegóły techniczne przechowywania są delegowane do infrastruktury. Ta warstwa jest sercem oprogramowania biznesowego.

Warstwa modelu domeny jest miejscem, w którym firma jest wyrażana. Po zaimplementowanie warstwy modelu domeny mikrousług w .NET, warstwa ta jest kodowany jako biblioteka klas z jednostek domeny, które przechwytują dane plus zachowanie (metody z logiką).

Zgodnie [z zasadami trwałości i](https://deviq.com/persistence-ignorance/) [ignorancji infrastruktury,](https://ayende.com/blog/3137/infrastructure-ignorance) ta warstwa musi całkowicie ignorować szczegóły trwałości danych. Te zadania trwałości powinny być wykonywane przez warstwę infrastruktury. W związku z tym ta warstwa nie powinna przyjmować bezpośrednich zależności od infrastruktury, co oznacza, że ważną regułą jest to, że klasy jednostek modelu domeny powinny być [poco](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Jednostki domeny nie powinny mieć żadnych bezpośrednich zależności (takich jak pochodne z klasy podstawowej) na żadnej struktury infrastruktury dostępu do danych, takich jak Entity Framework lub NHibernate. W idealnym przypadku jednostki domeny nie powinny pochodzić z lub zaimplementować dowolny typ zdefiniowany w dowolnej ramach infrastruktury.

Większość nowoczesnych struktur ORM, takich jak Entity Framework Core zezwalaj na takie podejście, dzięki czemu klasy modelu domeny nie są powiązane z infrastrukturą. Jednak posiadanie jednostek POCO nie zawsze jest możliwe podczas korzystania z niektórych baz danych i struktur NoSQL, takich jak Aktorzy i niezawodne kolekcje w sieci szkieletowej usługi Azure.

Nawet wtedy, gdy jest ważne, aby przestrzegać zasady ignorancji trwałości dla modelu domeny, nie należy ignorować obawy trwałości. Nadal bardzo ważne jest zrozumienie modelu danych fizycznych i sposobu mapowania go do modelu obiektu jednostki. W przeciwnym razie można tworzyć niemożliwe projekty.

Ponadto nie oznacza to, że można wziąć model przeznaczony dla relacyjnej bazy danych i bezpośrednio przenieść go do bazy danych NoSQL lub zorientowanych na dokument. W niektórych modelach jednostek model może pasować, ale zwykle nie. Nadal istnieją ograniczenia, których model jednostki musi przestrzegać, w oparciu zarówno o technologię pamięci masowej, jak i technologię ORM.

### <a name="the-application-layer"></a>Warstwa aplikacji

Przechodząc do warstwy aplikacji, możemy ponownie przytoczyć książkę Erica Evansa [Domain Driven Design:](https://domainlanguage.com/ddd/)

**Warstwa aplikacji:** Definiuje zadania, które oprogramowanie ma wykonać i kieruje wyraziste obiekty domeny do rozwiązywania problemów. Zadania, za które odpowiedzialna jest ta warstwa, mają znaczenie dla firmy lub są niezbędne do interakcji z warstwami aplikacji innych systemów. Warstwa ta jest cienka. Nie zawiera reguł biznesowych ani wiedzy, ale tylko koordynuje zadania i delegatów pracy do współpracy obiektów domeny w następnej warstwie w dół. Nie ma stanu odzwierciedlającego sytuację biznesową, ale może mieć stan, który odzwierciedla postęp zadania dla użytkownika lub programu.

Warstwa aplikacji mikrousług w .NET jest często kodowany jako projekt ASP.NET Core Web API. Projekt implementuje interakcję mikrousług, zdalny dostęp do sieci i zewnętrzne interfejsy API sieci Web używane z interfejsu użytkownika lub aplikacji klienckich. Zawiera zapytania, jeśli przy użyciu podejścia CQRS, polecenia akceptowane przez mikrousługi, a nawet komunikacji opartej na zdarzeniach między mikrousług (zdarzenia integracji). ASP.NET Core Web API reprezentujący warstwę aplikacji nie może zawierać reguł biznesowych ani wiedzy o domenie (zwłaszcza reguł domeny dla transakcji lub aktualizacji); powinny one być własnością biblioteki klas modelu domeny. Warstwa aplikacji musi koordynować tylko zadania i nie może zawierać ani definiować żadnego stanu domeny (modelu domeny). Deleguje wykonanie reguł biznesowych do samych klas modelu domeny (zagregowane katalogi główne i jednostki domeny), które ostatecznie zaktualizują dane w obrębie tych jednostek domeny.

Zasadniczo logika aplikacji jest, gdzie można zaimplementować wszystkie przypadki użycia, które zależą od danego frontonia. Na przykład implementacja związana z usługą interfejsu API sieci Web.

Celem jest, że logika domeny w warstwie modelu domeny, jego invariants, model danych i powiązanych reguł biznesowych musi być całkowicie niezależne od warstw prezentacji i aplikacji. Przede wszystkim warstwa modelu domeny nie może bezpośrednio zależeć od żadnej struktury infrastruktury.

### <a name="the-infrastructure-layer"></a>Warstwa infrastruktury

Warstwa infrastruktury jest jak dane, które są początkowo przechowywane w jednostkach domeny (w pamięci) jest zachowywany w bazach danych lub innym magazynie trwałym. Przykładem jest użycie kodu Core entity framework do zaimplementowania klas wzorca repozytorium, które używają DBContext do utrwalania danych w relacyjnej bazie danych.

Zgodnie z wcześniej wymienionymi zasadami [ignorancji trwałości](https://deviq.com/persistence-ignorance/) i [ignorancji infrastruktury warstwa](https://ayende.com/blog/3137/infrastructure-ignorance) infrastruktury nie może "zanieczyszczać" warstwy modelu domeny. Należy zachować klasy jednostek modelu domeny niezależnego od infrastruktury, która służy do utrwalania danych (EF lub innych struktur) nie biorąc twardych zależności w ramach. Biblioteka klas warstwy modelu domeny powinna mieć tylko kod domeny, tylko klasy jednostek [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) implementujące serce oprogramowania i całkowicie oddzielone od technologii infrastruktury.

W związku z tym warstwy lub biblioteki klas i projekty powinny ostatecznie zależeć od warstwy modelu domeny (biblioteki), a nie odwrotnie, jak pokazano na rysunku 7-7.

![Diagram przedstawiający zależności istniejące między warstwami usługi DDD.](./media/ddd-oriented-microservice/ddd-service-layer-dependencies.png)

**Rysunek 7-7**. Zależności między warstwami w DDD

Zależności w usłudze DDD warstwa aplikacji zależy od domeny i infrastruktury, a infrastruktura zależy od domeny, ale domena nie zależy od żadnej warstwy. Ten projekt warstwy powinny być niezależne dla każdej mikrousługi. Jak wspomniano wcześniej, można zaimplementować najbardziej złożonych mikrousług po wzorców DDD, podczas wdrażania prostszych mikrousług opartych na danych (proste CRUD w jednej warstwie) w prostszy sposób.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **deviq. Zasada ignorancji trwałości** \
  <https://deviq.com/persistence-ignorance/>

- **Oren Eini. Ignorancja infrastruktury** \
  <https://ayende.com/blog/3137/infrastructure-ignorance>

- **Angel Lopez. Architektura warstwowa w projektowaniu opartym na domenie** \
  <https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/>

>[!div class="step-by-step"]
>[Poprzedni](cqrs-microservice-reads.md)
>[następny](microservice-domain-model.md)
