---
title: Projektowanie mikrousługi zorientowanej na wzorzec DDD
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z tematem projektowanie mikrousługi porządkowania zorientowanego na DDD i jej warstw aplikacji.
ms.date: 10/08/2018
ms.openlocfilehash: 303f8909d12dddef93b20604a00b9ea8e8493ee5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295993"
---
# <a name="design-a-ddd-oriented-microservice"></a>Projektowanie mikrousługi zorientowanej na DDD

Projektowanie oparte na domenie (DDD) zaleca modelowanie w oparciu o rzeczywistość biznesową, która jest odpowiednia dla przypadków użycia. W kontekście tworzenia aplikacji DDD rozmowy dotyczące problemów jako domen. Opisuje obszary niezależnych problemów jako konteksty ograniczone (poszczególne konteksty są skorelowane z mikrousługą) i podkreśla typowy język, aby poznać te problemy. Sugeruje również wiele pojęć i wzorców technicznych, takich jak jednostki domeny z rozbudowanymi modelami (brak [modelu Anemic-domeny](https://martinfowler.com/bliki/AnemicDomainModel.html)), obiektów wartości, agregacji i agregacji głównych (lub jednostek głównych) do obsługi wewnętrznej implementacji. W tej części przedstawiono projektowanie i implementację tych wzorców wewnętrznych.

Czasami te reguły techniczne i wzorce są postrzegane jako przeszkody, które mają intensywną krzywą uczenia się do wdrażania podejścia DDD. Jednak ważna część nie jest wzorcem, ale organizując kod, tak aby był wyrównany do problemów z działalnością biznesową i korzystać z tych samych warunków firmy (język powszechny). Ponadto metody DDD powinny być stosowane tylko wtedy, gdy są implementowane złożone mikrousługi z istotnymi regułami biznesowymi. Prostsze obowiązki, takie jak usługa CRUD, mogą być zarządzane przy użyciu prostsze podejścia.

Miejsce, w którym należy narysować granice, to kluczowe zadanie podczas projektowania i definiowania mikrousług. Wzorce DDD pomagają zrozumieć złożoność domeny. Dla modelu domeny dla każdego powiązanego kontekstu identyfikujesz i zdefiniujesz jednostki, obiekty wartości i agregaty modelujące domenę. Tworzysz i udoskonalasz model domeny, który znajduje się w granicach definiujących kontekst. Jest to bardzo jawne w formie mikrousługi. Składniki w tych granicach są kompletne dla mikrousług, ale w niektórych przypadkach mikrousługi BC lub firmowe mogą składać się z kilku usług fizycznych. DDD jest o granicach i dlatego są mikrousługi.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Zachowaj stosunkowo małe granice kontekstu mikrousługi

Określanie, gdzie mają być umieszczane granice między ograniczonymi kontekstami, saldo są dwa konkurencyjne cele. Najpierw należy początkowo utworzyć najmniejsze możliwe mikrousługi, chociaż nie powinien być głównym sterownikiem; należy utworzyć granicę wokół rzeczy, które wymagają spójności. Następnie chcesz uniknąć komunikacji między mikrousługami. Cele te mogą być sprzeczne ze sobą. Należy je zrównoważyć przez odtworzenie systemu jako wielu małych mikrousług, aż do momentu, aż zobaczysz, że granice komunikacji rośnieją szybko przy każdej dodatkowej próbie oddzielenia nowego kontekstu ograniczonego. Spójność jest kluczem w pojedynczym kontekście.

Jest podobny do [nieodpowiedniego zapachu kodu Intimacy](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) podczas implementowania klas. Jeśli dwie mikrousługi muszą współpracować ze sobą nawzajem, powinny być takie same mikrousługi.

Innym sposobem jest to, że jest to autonomia. Jeśli mikrousługa musi być zależna od innej usługi, aby bezpośrednio obsłużyć żądanie, nie jest naprawdę autonomiczna.

## <a name="layers-in-ddd-microservices"></a>Warstwy mikrousług w DDD

Większość aplikacji korporacyjnych z znaczącą złożonością biznesową i techniczną jest definiowana przez wiele warstw. Warstwy są artefaktami logicznymi i nie są powiązane z wdrożeniem usługi. Istnieją one, aby ułatwić deweloperom zarządzanie złożonością w kodzie. Różne warstwy (takie jak warstwa modelu domeny zamiast warstwy prezentacji itp.) mogą mieć różne typy, które są elementami tłumaczenia między tymi typami.

Na przykład jednostka może zostać załadowana z bazy danych. Następnie część tych informacji lub agregacja informacji, w tym dodatkowe dane z innych jednostek, można wysłać do interfejsu użytkownika klienta za pośrednictwem internetowego interfejsu API REST. W tym miejscu jest to, że jednostka domeny jest zawarta w warstwie modelu domeny i nie powinna być propagowana do innych obszarów, do których nie należy, jak w przypadku warstwy prezentacji.

Ponadto konieczne jest posiadanie zawsze prawidłowych jednostek (zobacz temat [projektowanie walidacji w warstwie modelu domeny](domain-model-layer-validations.md) ), kontrolowane przez agregację elementów głównych (jednostki główne). W związku z tym jednostki nie powinny być powiązane z widokami klienta, ponieważ na poziomie interfejsu użytkownika niektóre dane mogą nadal nie być sprawdzane. Jest to ViewModel. ViewModel jest modelem danych wyłącznie dla potrzeb warstwy prezentacji. Jednostki domeny nie należą bezpośrednio do ViewModel. Zamiast tego należy przetłumaczyć między modele widoków a jednostkami domeny i odwrotnie.

Podczas rozwiązywania złożoności należy mieć model domeny kontrolowany przez zagregowane elementy główne, aby upewnić się, że wszystkie niewarianty i reguły związane z tą grupą jednostek (agregacji) są wykonywane za pomocą pojedynczego punktu wejścia lub bramy, zagregowanego elementu głównego.

Rysunek 7-5 pokazuje, w jaki sposób projekt warstwowy jest zaimplementowany w aplikacji eShopOnContainers.

![Trzy warstwy w DDD mikrousługach, takie jak porządkowanie. Każda warstwa jest projektem programu VS: Warstwa aplikacji jest porządkowaniem. interfejsem API, warstwą domeną jest porządkowanie. domena i warstwa infrastruktury to porządkowanie. infrastruktura.](./media/image6.png)

**Rysunek 7-5**. DDD warstwy w mikrousłudze porządkowania w eShopOnContainers

Chcesz zaprojektować system w taki sposób, aby każda warstwa komunikuje się tylko z pewnymi innymi warstwami. Może to być łatwiejsze do wymuszenia, jeśli warstwy są implementowane jako różne biblioteki klas, ponieważ można jasno określić, jakie zależności są ustawiane między bibliotekami. Na przykład warstwa modelu domeny nie powinna przyjmować zależności od żadnej innej warstwy (klasy modelu domeny powinny być zwykłymi obiektami środowiska CLR lub [poco](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), Klasa). Jak pokazano na rysunku 7-6, **uporządkowana** Biblioteka warstw ma zależności tylko od bibliotek .NET Core lub pakietów NuGet, ale nie dla żadnej innej biblioteki niestandardowej, takiej jak biblioteka danych lub biblioteka trwałości.

![Widok Eksplorator rozwiązań uporządkowania zależności domeny, który pokazuje, zależy tylko od bibliotek .NET Core.](./media/image7.png)

**Rysunek 7-6**. Warstwy zaimplementowane jako biblioteki umożliwiają lepszą kontrolę zależności między warstwami

### <a name="the-domain-model-layer"></a>Warstwa modelu domeny

Model [oparty na domenie](https://domainlanguage.com/ddd/) "Eric Evans" zapewnia następujące informacje dotyczące warstwy modelu domeny i warstwy aplikacji.

**Warstwa modelu domeny**: Odpowiedzialny za przedstawianie koncepcji firmy, informacji o sytuacji biznesowej i regułach biznesowych. Stan, który odzwierciedla sytuację biznesową, jest kontrolowany i używany w tym miejscu, mimo że szczegółowe informacje techniczne dotyczące przechowywania są delegowane do infrastruktury. Ta warstwa jest sercem oprogramowania biznesowego.

Warstwa modelu domeny to miejsce, w którym jest wyrażana działalność firmy. W przypadku zaimplementowania warstwy modelu domeny mikrousług w programie .NET warstwa ta jest kodowana jako Biblioteka klas z jednostkami domeny, które przechwytują dane i zachowanie (metody z logiką).

Zgodnie z [Ignorujących trwałości](https://deviq.com/persistence-ignorance/) i zasadami [ignorujących infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) Ta warstwa musi całkowicie ignorować szczegóły trwałości danych. Te zadania trwałości powinny być wykonywane przez warstwę infrastruktury. W związku z tym Ta warstwa nie powinna przyjmować bezpośrednich zależności względem infrastruktury, co oznacza, że ważną regułą jest, że klasy jednostek modelu domeny powinny być [poco](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Jednostki domeny nie powinny mieć żadnej bezpośredniej zależności (na przykład wynikającej z klasy bazowej) w ramach platformy infrastruktury dostępu do danych, takiej jak Entity Framework lub NHibernate. W idealnym przypadku jednostki domeny nie powinny pochodzić ani implementować żadnego typu zdefiniowanego w żadnej strukturze infrastruktury.

Większość nowoczesnych platform ORM, takich jak Entity Framework Core zezwala na takie podejście, tak aby klasy modelu domeny nie były połączone z infrastrukturą. Jednak posiadanie jednostek POCO nie zawsze jest możliwe w przypadku używania niektórych baz danych NoSQL i struktur, takich jak aktorzy i niezawodne kolekcje na platformie Azure Service Fabric.

Nawet jeśli ważne jest przestrzeganie zasady trwałości Ignorujących dla modelu domeny, nie należy ignorować obaw związanych z trwałością. Jest to bardzo ważne, aby zrozumieć model danych fizycznych i sposób mapowania na model obiektów Entity. W przeciwnym razie można tworzyć niemożliwe projekty.

Nie oznacza to również, że można utworzyć model przeznaczony dla relacyjnej bazy danych i bezpośrednio przenieść go do bazy danych NoSQL lub zorientowanej na dokument. W niektórych modelach jednostek model może pasować, ale zazwyczaj nie jest. Nadal istnieją ograniczenia, które muszą być zgodne z modelem jednostki, w oparciu o technologię magazynu i technologię ORM.

### <a name="the-application-layer"></a>Warstwa aplikacji

Po przeniesieniu do warstwy aplikacji możemy ponownie pomieścić projekt Eric Evans książki [opartej na domenie](https://domainlanguage.com/ddd/):

**Warstwa aplikacji:** Definiuje zadania, które oprogramowanie ma wykonać i kieruje obiekty domeny, aby można było z nich korzystać. Zadania, dla których ta warstwa jest odpowiedzialna, mają znaczenie dla działalności firmy lub są niezbędne do interakcji z warstwami aplikacji innych systemów. Ta warstwa jest utrzymywana w postaci cienkiej. Nie zawiera ona reguł lub informacji o firmie, ale tylko koordynuje zadania i delegatów pracuje do współpracy obiektów domeny w następnej warstwie. Nie ma stanu odzwierciedlającego sytuację biznesową, ale może mieć stan, który odzwierciedla postęp zadania dla użytkownika lub programu.

Warstwa aplikacji mikrousług w programie .NET jest zwykle kodowana jako projekt ASP.NET Core interfejsu API sieci Web. Projekt implementuje interakcję mikrousługi, zdalny dostęp do sieci i zewnętrzne interfejsy API sieci Web używane z poziomu interfejsu użytkownika lub aplikacji klienckich. Zawiera zapytania w przypadku użycia podejścia CQRS, poleceń zaakceptowanych przez mikrousługę, a nawet komunikacji opartej na zdarzeniach między mikrousług (zdarzenia integracji). ASP.NET Core internetowy interfejs API, który reprezentuje warstwę aplikacji, nie może zawierać reguł firmy lub informacji o domenie (szczególnie reguł dotyczących domeny dla transakcji lub aktualizacji). powinny one należeć do biblioteki klas modelu domeny. Warstwa aplikacji musi tylko koordynować zadania i nie może zawierać ani definiować żadnego stanu domeny (modelu domeny). Deleguje wykonywanie reguł firmy do samych klas modelu domeny (Agregaty główne i jednostki domeny), co ostatecznie zaktualizuje dane w tych jednostkach domeny.

Zasadniczo logika aplikacji to miejsce, w którym można zaimplementować wszystkie przypadki użycia, które zależą od danego frontonu. Na przykład implementacja związana z usługą interfejsu API sieci Web.

Celem jest, że logika domeny w warstwie modelu domeny, jej niezależność, model danych i powiązane reguły biznesowe muszą być całkowicie niezależne od warstw prezentacji i aplikacji. Większość z nich warstwa modelu domeny nie może bezpośrednio zależeć od żadnej struktury infrastruktury.

### <a name="the-infrastructure-layer"></a>Warstwa infrastruktury

Warstwa infrastruktury to sposób, w jaki dane przechowywane początkowo w jednostkach domeny (w pamięci) są utrwalane w bazach danych lub w innym magazynie trwałym. Przykład korzysta z kodu Entity Framework Core, aby zaimplementować klasy wzorców repozytorium, które używają DbContext do utrwalania danych w relacyjnej bazie danych.

Zgodnie z wcześniej wymienionymi zasadami [trwałości ignorujących](https://deviq.com/persistence-ignorance/) i [infrastruktury ignorujących](https://ayende.com/blog/3137/infrastructure-ignorance) , warstwa infrastruktury nie może "skazić" warstwy modelu domeny. Należy zachować klasy jednostek modelu domeny niezależny od z infrastruktury, która służy do utrwalania danych (EF lub innych platform), ponieważ nie jest to konieczne. Biblioteka klas warstwy modelu domeny powinna mieć tylko kod domeny, tylko klasy jednostek [poco](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) implementujące serce oprogramowania i całkowicie niepowiązane z technologią infrastruktury.

W ten sposób warstwy lub biblioteki klas i projekty powinny ostatecznie zależeć od warstwy modelu domeny (biblioteki), a nie odwrotnie, jak pokazano na rysunku 7-7.

![Zależności w usłudze DDD warstwa aplikacji zależy od domeny i infrastruktury, a infrastruktura zależy od domeny, ale domena nie jest zależna od żadnej warstwy.](./media/image8.png)

**Rysunek 7-7**. Zależności między warstwami w DDD

Ten projekt warstwy powinien być niezależny dla każdej mikrousługi. Jak wspomniano wcześniej, można zaimplementować najbardziej złożone mikrousługi w formie wzorców DDD, jednocześnie implementując prostsze mikrousługi oparte na danych (proste CRUD w jednej warstwie) w prostszy sposób.

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **DevIQ. Zasada Ignorujących trwałości** \
  <https://deviq.com/persistence-ignorance/>

- **Oren Eini. Ignorujących infrastruktury** \
  <https://ayende.com/blog/3137/infrastructure-ignorance>

- **Angel Lopez. Architektura warstwowa w projekcie opartym na domenie** \
  <https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/>

>[!div class="step-by-step"]
>[Poprzedni](cqrs-microservice-reads.md)Następny
>[](microservice-domain-model.md)
