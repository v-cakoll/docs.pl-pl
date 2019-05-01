---
title: Suwerenność danych przypadająca na mikrousługę
description: Suwerenność danych przypadająca na mikrousługę jest jednym z punktów kay mikrousług. Każda mikrousługa musi być jedynym właścicielem swojej bazy danych, udostępniając je żadnego innego. Oczywiście wszystkie wystąpienia elementu mikrousługi połączyć z tej samej bazy danych o wysokiej dostępności.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 1b0b1fbb72f759eb337c0c1a9c465cc4088d8eff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909714"
---
# <a name="data-sovereignty-per-microservice"></a>Suwerenność danych przypadająca na mikrousługę

Regułę ważne dla architektury mikrousług jest to, że każda mikrousługa musi być właścicielem swoich danych domeny i logiki. Tak samo, jak Pełna aplikacja jest właścicielem jego logikę i dane, więc należy poszczególne mikrousługi właścicielem jego logikę i dane w ramach autonomicznego cykl życia, niezależnie od wdrożenia na mikrousługach.

Oznacza to, że model koncepcyjny domeny będą się różnić między podsystemów lub mikrousług. Należy wziąć pod uwagę aplikacje dla przedsiębiorstw, gdzie relacji zarządzania (CRM) aplikacji klientów, transakcji zakupu podsystemów i podsystemów pomocy technicznej klienta każdego wywołania w atrybutów jednostki unikatowy klienta i dane, a każda używającego innego Ograniczony kontekst (BC).

Ta zasada jest podobna we [projektowania opartego na domenach (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design), gdzie każdy [ograniczony kontekst](https://martinfowler.com/bliki/BoundedContext.html) lub autonomiczne podsystemu bądź usługi, musi być właścicielem swój model domeny (danych oraz zachowanie i logikę). W każdym kontekście ograniczonych DDD skorelowany jeden mikrousług business (jednej lub kilku usług). Ten punkt o wzorcu ograniczonego kontekstu jest rozwinięte w następnej sekcji.

Z drugiej strony podejście tradycyjnych (dane monolityczną) używane w wielu aplikacjach jest tylko kilka baz danych lub jednym scentralizowanej bazie danych. Często jest znormalizowana bazę danych SQL używaną dla całej aplikacji i wszystkich jego podsystemów wewnętrznego, jak pokazano w rysunek 4 – 7.

![Tradycyjne podejście istnieje pojedynczej bazy danych, udostępnione dla wszystkich usług, zwykle w przypadku architektury warstwowej. W przypadku zastosowania podejścia mikrousług każda mikrousługa jest właścicielem jej modelu/danych](./media/image7.png)

**Rysunek 4 – 7**. Porównanie niezależność danych: monolityczne bazy danych w porównaniu z mikrousług

To podejście w scentralizowanej bazie danych początkowo wygląda prostsze i wydaje się umożliwiają wielokrotne użycie jednostek w różne podsystemy, aby wszystko, co jest zgodne. Ale w rzeczywistości jest za duży tabel, obsługujących wiele różne podsystemy zawierające atrybutów i kolumny, które nie są wymagane w większości przypadków. Przypomina to próba użycia tej samej fizycznej mapy górach dziennik krótki, biorąc podróży samochodu dzień długi i uczenia lokalizacji geograficznej.

Monolitycznych z zwykle jednej relacyjnej bazie danych ma dwie ważne korzyści: [Transakcje ACID](https://en.wikipedia.org/wiki/ACID) i języka SQL, zarówno roboczych we wszystkich tabelach i dane związane z aplikacją. Takie podejście umożliwia łatwe Napisz zapytanie, które łączy dane z wielu tabel.

Jednak dostęp do danych staje się bardziej złożone, po przeniesieniu do architektury mikrousług. Ale nawet wtedy, gdy transakcje ACID można lub powinny być używane w ramach ograniczonego kontekstu lub mikrousług, dane należące do poszczególnych mikrousług są prywatne tego mikrousług i może zostać oceniony jedynie za pośrednictwem jego interfejsu API mikrousług. Zawieranie danych gwarantuje, że mikrousługi są luźno powiązane i może się rozwijać, niezależnie od siebie nawzajem. Jeśli wiele usług zostały dostęp do tych samych danych, aktualizacje schematów wymaga przeprowadzenia skoordynowanych aktualizacji do wszystkich usług. Spowoduje to przerwanie Autonomia cyklu życia mikrousług. Ale struktur danych rozproszonych oznacza, że nie możesz wprowadzać pojedynczej transakcji ACID między mikrousług. Z kolei oznacza to, że podczas procesu biznesowego obejmuje wiele mikrousług, należy użyć spójności ostatecznej. Jest to znacznie trudniejsze do zaimplementowania niż proste sprzężenia SQL, ponieważ nie można utworzyć ograniczenia integralności, lub użyj transakcje rozproszone między osobne bazy danych, ponieważ wyjaśnimy w późniejszym czasie na. Podobnie wiele innych funkcji relacyjnej bazy danych nie są dostępne w wielu mikrousługach.

Kontynuowanie nawet, różne mikrousługi często używają różnych *rodzajów* baz danych. Nowoczesne aplikacje sklepu i proces różnych rodzajów danych oraz relacyjnej bazy danych nie zawsze jest najlepszym wyborem. W przypadku niektórych przypadków użycia, bazy danych NoSQL, takie jak Azure cosmos DB lub MongoDB obejmujące wygodniejszy modelu danych oraz oferuje lepszą wydajność i skalowalność niż bazy danych SQL, takich jak program SQL Server lub usługi Azure SQL Database. W innych przypadkach relacyjnej bazy danych jest nadal jest najlepszym rozwiązaniem. W związku z tym, aplikacje oparte na mikrousługach często używają kombinacji bazy danych SQL i NoSQL, która jest czasem nazywany [ubocznym](https://martinfowler.com/bliki/PolyglotPersistence.html) podejście.

Partycjonowane trwałego polyglot architektura do przechowywania danych ma wiele zalet. Obejmują one luźno powiązanych usług i lepszą wydajność, skalowalność, kosztów i możliwości zarządzania. Jednak może to wprowadzić niektóre wyzwania, zarządzania danych rozproszonych, jak wyjaśniono w "[identyfikowanie ograniczeń modelu domeny](identify-microservice-domain-model-boundaries.md)" później w tym rozdziale.

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>Relacja między mikrousług i wzorzec ograniczony kontekst

Pojęcie mikrousług jest pochodną [wzorzec ograniczony kontekst (BC)](https://martinfowler.com/bliki/BoundedContext.html) w [projektowania opartego na domenach (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design). DDD dotyczy dużych modeli przez podzielenie ich na wielu usług łączności biznesowej i są wyraźnie ich granice. Każdy BC musi mieć swój własny model i bazy danych. Podobnie każda mikrousługa jest właścicielem jej powiązane dane. Ponadto każdy BC zazwyczaj ma swój własny [wszechobecne języka](https://martinfowler.com/bliki/UbiquitousLanguage.html) ułatwiających komunikację między programistami i ekspertów z konkretnych dziedzin.

Te warunki (głównie domeny jednostek) w języku uniwersalnych może mieć różne nazwy w różnych kontekstach powiązana, jednostki nawet wtedy, gdy różne domeny udostępnianie tej samej tożsamości (czyli unikatowy identyfikator, który został użyty do odczytu jednostki magazynu). Na przykład w kontekstach ograniczonych profilu użytkownika, jednostka domeny użytkownika może udostępniać tożsamości jednostka domeny kupujący w kontekście szeregowania ograniczone.

Mikrousługi w związku z tym przypomina ograniczony kontekst, ale również określi, czy jest to usługa rozproszonej. Stworzona w oddzielnym procesie dla każdego kontekstu ograniczonego i musi używać protokoły rozproszonego zanotowanej wcześniej, takich jak HTTP/HTTPS, funkcja WebSockets, lub [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Wzorzec ograniczony kontekst, jednak nie określa czy kontekstu ograniczonego są usługami rozproszonymi lub jeśli jest po prostu logiczną granic (na przykład ogólny podsystemu) w aplikacji monolitycznej wdrożenia.

Jest ważne podkreślić, że zdefiniowanie usługi dla każdego kontekstu ograniczonego jest dobrym miejscem do rozpoczęcia. Ale nie trzeba ograniczać projektu do niego. Czasami należy projektować ograniczonego kontekstu lub firm mikrousług składa się z kilku usług fizycznych. Ale ostatecznie obu wzorców - ograniczony kontekst i mikrousługi są ściśle powiązane.

DDD korzyści płynące z mikrousług uzyskując rzeczywistych granic w formie rozproszonych mikrousług. Ale pomysły, takie jak udostępnianie nie modelu między mikrousługami co chcecie również w kontekście ograniczone.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Chris Richardson. Wzorzec: Bazy danych na usługę** \
  <https://microservices.io/patterns/data/database-per-service.html>

- **Martin Fowler. BoundedContext** \
  <https://martinfowler.com/bliki/BoundedContext.html>

- **Martin Fowler. PolyglotPersistence** \
  <https://martinfowler.com/bliki/PolyglotPersistence.html>

- **Alberto Brandolini. Strategiczne projektowania, które za pomocą kontekstu mapowania opartego na domenach** \
  <https://www.infoq.com/articles/ddd-contextmapping>

>[!div class="step-by-step"]
>[Poprzednie](microservices-architecture.md)
>[dalej](logical-versus-physical-architecture.md)
