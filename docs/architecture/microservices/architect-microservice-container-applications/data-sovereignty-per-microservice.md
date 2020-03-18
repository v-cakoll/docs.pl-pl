---
title: Suwerenność danych przypadająca na mikrousługę
description: Suwerenność danych na mikrousługi jest jednym z kluczowych punktów mikrousług. Każda mikrousługa musi być jedynym właścicielem swojej bazy danych, udostępniając ją bez żadnych innych. Oczywiście wszystkie wystąpienia mikrousługi połączyć się z tej samej bazy danych o wysokiej dostępności.
ms.date: 09/20/2018
ms.openlocfilehash: f606d6314f38bf3e2c163871af432806dddc7446
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73191908"
---
# <a name="data-sovereignty-per-microservice"></a>Suwerenność danych przypadająca na mikrousługę

Ważną regułą dla architektury mikrousług jest, że każda mikrousługa musi być właścicielem danych domeny i logiki. Podobnie jak pełna aplikacja jest właścicielem logiki i danych, więc każda mikrousługa własnych logiki i danych w autonomicznym cyklu życia, z niezależnego wdrożenia na mikrousługi.

Oznacza to, że model koncepcyjny domeny będzie się różnić między podsystemami lub mikrousług. Należy wziąć pod uwagę aplikacje dla przedsiębiorstw, w których aplikacje do zarządzania relacjami z klientami (CRM), podsystemy zakupów transakcyjnych i podsystemy obsługi klienta każde wywołanie unikatowych atrybutów i danych encji klienta oraz gdzie każdy z nich wykorzystuje inne Ograniczony kontekst (BC).

Zasada ta jest podobna w [projekcie opartym na domenie (DDD),](https://en.wikipedia.org/wiki/Domain-driven_design)gdzie każdy [ograniczony kontekst](https://martinfowler.com/bliki/BoundedContext.html) lub autonomiczny podsystem lub usługa musi posiadać swój model domeny (dane oraz logikę i zachowanie). Każdy kontekst ograniczony DDD koreluje z jedną mikrousługą biznesową (jedną lub kilkoma usługami). Ten punkt o wzorzec kontekstu ograniczone go jest rozwijany w następnej sekcji.

Z drugiej strony tradycyjne (monolityczne dane) podejście stosowane w wielu aplikacjach jest mieć jedną scentralizowaną bazę danych lub tylko kilka baz danych. Jest to często znormalizowana baza danych SQL, która jest używana dla całej aplikacji i wszystkich jej wewnętrznych podsystemów, jak pokazano na rysunku 4-7.

![Diagram przedstawiający dwa podejścia do bazy danych.](./media/data-sovereignty-per-microservice/data-sovereignty-comparison.png)

**Rysunek 4-7**. Porównanie suwerenności danych: monolityczna baza danych a mikrousługi

W tradycyjnym podejściu istnieje jedna baza danych współużytkowana przez wszystkie usługi, zazwyczaj w architekturze warstwowej. W podejściu mikrousług każda mikrousługa jest właścicielem swojego modelu/danych. Podejście scentralizowanej bazy danych początkowo wygląda prościej i wydaje się umożliwiać ponowne użycie jednostek w różnych podsystemach, aby wszystko było spójne. Ale rzeczywistość jest w końcu z ogromnymi tabelami, które obsługują wiele różnych podsystemów i które zawierają atrybuty i kolumny, które nie są potrzebne w większości przypadków. To jak próba użycia tej samej fizycznej mapy do wędrowania krótkim szlakiem, jednodniowej podróży samochodem i nauki geografii.

Monolityczne aplikacji z zazwyczaj jednej relacyjnej bazy danych ma dwie ważne korzyści: [transakcje ACID](https://en.wikipedia.org/wiki/ACID) i języka SQL, zarówno pracy we wszystkich tabelach i danych związanych z aplikacją. Takie podejście umożliwia łatwe pisanie kwerendy, która łączy dane z wielu tabel.

Jednak dostęp do danych staje się znacznie bardziej skomplikowane po przejściu do architektury mikrousług. Nawet w przypadku korzystania z transakcji ACID w ramach mikrousługi lub ograniczonego kontekstu, ważne jest, aby wziąć pod uwagę, że dane należące do każdej mikrousługi jest prywatny do tej mikrousługi i powinny być dostępne tylko synchronicznie za pośrednictwem swoich punktów końcowych interfejsu API(REST, gRPC, SOAP, itp.) lub asynchronicznie za pośrednictwem wiadomości (AMQP lub podobne).

Hermetyzowanie danych zapewnia, że mikrousługi są luźno sprzężeni i mogą ewoluować niezależnie od siebie. Jeśli wiele usług uzyskiwało dostęp do tych samych danych, aktualizacje schematu wymagałyby skoordynowanych aktualizacji wszystkich usług. Spowoduje to przerwanie autonomii cyklu życia mikrousług. Ale struktury danych rozproszonych oznacza, że nie można dokonać pojedynczej transakcji ACID w mikrousługach. To z kolei oznacza, że należy użyć spójności ostatecznej, gdy proces biznesowy obejmuje wiele mikrousług. Jest to znacznie trudniejsze do zaimplementowania niż proste sprzężenia SQL, ponieważ nie można utworzyć ograniczenia integralności lub użyć rozproszonych transakcji między oddzielnymi bazami danych, jak wyjaśnimy później. Podobnie wiele innych funkcji relacyjnej bazy danych nie są dostępne w wielu mikrousług.

Idąc jeszcze dalej, różne mikrousługi często używają różnych *rodzajów* baz danych. Nowoczesne aplikacje przechowują i przetwarzają różne rodzaje danych, a relacyjna baza danych nie zawsze jest najlepszym wyborem. W niektórych przypadkach użycia baza danych NoSQL, taka jak Usługa Azure CosmosDB lub MongoDB, może mieć wygodniejszy model danych i oferować lepszą wydajność i skalowalność niż baza danych SQL, taka jak SQL Server lub Azure SQL Database. W innych przypadkach relacyjnej bazy danych jest nadal najlepszym rozwiązaniem. W związku z tym aplikacje oparte na mikrousługach często używają mieszaniny baz danych SQL i NoSQL, która jest czasami nazywana podejściem [trwałości polyglot.](https://martinfowler.com/bliki/PolyglotPersistence.html)

Architektura partycjonowana, polyglot-trwałe dla magazynu danych ma wiele zalet. Należą do nich luźno powiązane usługi i lepsza wydajność, skalowalność, koszty i możliwości zarządzania. Może jednak wprowadzić pewne wyzwania związane z zarządzaniem danymi rozproszonymi, jak wyjaśniono w "[Identyfikowanie granic modelu domeny](identify-microservice-domain-model-boundaries.md)" w dalszej części tego rozdziału.

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>Relacja między mikrousługami a wzorcem kontekstu ograniczonego

Pojęcie mikrousługi pochodzi od [wzorca ograniczonego kontekstu (BC)](https://martinfowler.com/bliki/BoundedContext.html) w [projekcie opartym na domenie (DDD).](https://en.wikipedia.org/wiki/Domain-driven_design) DDD zajmuje się dużymi modelami, dzieląc je na wiele kontrolerów BC i wyraźnie o swoich granicach. Każdy bc musi mieć swój własny model i bazy danych; podobnie każda mikrousługa jest właścicielem powiązanych danych. Ponadto, każdy BC zwykle ma swój własny [wszechobecny język,](https://martinfowler.com/bliki/UbiquitousLanguage.html) aby pomóc w komunikacji między programistami i ekspertami domeny.

Te terminy (głównie jednostki domeny) w wszechobecnym języku mogą mieć różne nazwy w różnych kontekstach ograniczonych, nawet jeśli różne jednostki domeny mają tę samą tożsamość (czyli unikatowy identyfikator używany do odczytywania jednostki z magazynu). Na przykład w kontekście ograniczonym profilu użytkownika jednostka domeny użytkownika może udostępniać tożsamość jednostce domeny kupującego w kontekście ograniczonym.

Mikrousługi jest zatem jak ograniczony kontekst, ale określa również, że jest to usługa rozproszona. Jest on zbudowany jako oddzielny proces dla każdego ograniczonego kontekstu i musi używać protokołów rozproszonych zauważyć wcześniej, takich jak HTTP/HTTPS, WebSockets lub [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Wzorzec kontekstu ograniczonego nie określa jednak, czy ograniczony kontekst jest usługą rozproszoną, czy też jest to po prostu logiczna granica (na przykład ogólny podsystem) w aplikacji wdrażania monolitycznego.

Ważne jest, aby podkreślić, że definiowanie usługi dla każdego ograniczonego kontekstu jest dobrym miejscem do rozpoczęcia. Ale nie musisz ograniczać do niego swojego projektu. Czasami należy zaprojektować ograniczony kontekst lub mikrousługi biznesowej składa się z kilku usług fizycznych. Ale ostatecznie oba wzorce -Bounded Context i mikrousługi— są ściśle powiązane.

DDD korzyści z mikrousług, uzyskując prawdziwe granice w postaci mikrousług rozproszonych. Ale pomysły, takie jak nie udostępnianie modelu między mikrousług są to, co chcesz również w kontekście ograniczone.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Chris Richardson. Wzorzec: Baza danych na usługę** \
  <https://microservices.io/patterns/data/database-per-service.html>

- **Martin Fowler. Ograniczony kontekst** \
  <https://martinfowler.com/bliki/BoundedContext.html>

- **Martin Fowler. PolyglotWytrwałość** \
  <https://martinfowler.com/bliki/PolyglotPersistence.html>

- **Alberto Brandolini. Strategiczny projekt oparty na domenie z mapowaniem kontekstu** \
  <https://www.infoq.com/articles/ddd-contextmapping>

>[!div class="step-by-step"]
>[Poprzedni](microservices-architecture.md)
>[następny](logical-versus-physical-architecture.md)
