---
title: Niezależność danych na mikrousługi
description: Niezależność danych jest jednym z najważniejszych punktów mikrousług. Każda mikrousługa musi być jedynym właścicielem swojej bazy danych, udostępniając ją innym osobom. Oczywiście wszystkie wystąpienia mikrousług nawiązują połączenie z tą samą bazą danych o wysokiej dostępności.
ms.date: 09/20/2018
ms.openlocfilehash: 3261446a84038b7b634242b0a0737472965168de
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834464"
---
# <a name="data-sovereignty-per-microservice"></a>Niezależność danych na mikrousługi

Ważną regułą dla architektury mikrousług jest to, że każda mikrousługa musi być własnością swoich danych i logiki domeny. Tak samo jak Pełna aplikacja jest właścicielem swojej logiki i danych, dlatego musi każda mikrousługa była własnością logiki i danych w autonomicznym cyklu życia z niezależnym wdrożeniem na mikrousługę.

Oznacza to, że model koncepcyjny domeny będzie się różnić w zależności od podsystemów lub mikrousług. Należy rozważyć aplikacje dla przedsiębiorstw, w których aplikacje do zarządzania relacjami z klientami (CRM), podsystemów zakupów transakcyjnych i obsługi klienta obsługują poszczególne wywołania unikatowych atrybutów i danych jednostki klienta, a każdy z nich używa innego Ograniczony kontekst (BC).

Ta zasada jest podobna do [projektu opartego na domenie (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design), gdzie każdy [powiązany kontekst](https://martinfowler.com/bliki/BoundedContext.html) lub podsystem autonomiczny lub usługa musi być własnym modelem domeny (dane oraz logika i zachowanie). Każdy kontekst związany z DDD korelacji jest skorelowany z jedną mikrousługą biznesową (jedną lub kilkoma usługami). Ten punkt dotyczący powiązanego wzorca kontekstu jest rozwinięty w następnej sekcji.

Z drugiej strony podejście tradycyjne (monolityczne dane) używane w wielu aplikacjach ma jedną scentralizowaną bazę danych lub kilka baz danych. Jest to często znormalizowana baza danych SQL, która jest używana dla całej aplikacji i wszystkich jej wewnętrznych podsystemów, jak pokazano na rysunku 4-7.

![Diagram przedstawiający dwa podejścia do bazy danych.](./media/data-sovereignty-per-microservice/data-sovereignty-comparison.png)

**Rysunek 4-7**. Porównanie suwerenności danych: monolityczna baza danych a mikrousługi

W tradycyjnym podejściu istnieje pojedyncza baza danych współdzielona przez wszystkie usługi, zazwyczaj w architekturze warstwowej. W podejściu mikrousług każda mikrousługa posiada swój model/dane. Scentralizowane podejście do bazy danych początkowo wygląda prostsze i wygląda na to, aby umożliwić ponowne użycie jednostek w różnych podsystemach, aby zapewnić spójność wszystkich elementów. Jednak rzeczywistość ma duże tabele, które obsługują wiele różnych podsystemów i zawiera atrybuty i kolumny, które nie są potrzebne w większości przypadków. Jest to podobne do próby użycia tej samej mapy fizycznej dla górach krótkiej, co zajmuje się codziennym podróżem i nauką geograficzną.

Aplikacja monolityczna z zazwyczaj jedną relacyjną bazą danych ma dwie istotne zalety: [transakcje kwasowe](https://en.wikipedia.org/wiki/ACID) i język SQL — zarówno pracujące we wszystkich tabelach, jak i danych związanych z Twoją aplikacją. Takie podejście umożliwia łatwe pisanie zapytania, które łączy dane z wielu tabel.

Jednak dostęp do danych jest znacznie bardziej skomplikowany po przejściu do architektury mikrousług. Jednak nawet w przypadku, gdy w ramach mikrousług lub ograniczonego kontekstu nie można używać transakcji KWASowych, dane należące do każdej mikrousługi są prywatne dla tej mikrousługi i można uzyskać do nich dostęp tylko za pośrednictwem interfejsu API mikrousług. Hermetyzowanie danych gwarantuje, że mikrousługi są luźno powiązane i mogą być od siebie niezależne. Jeśli wiele usług uzyskuje dostęp do tych samych danych, aktualizacje schematu wymagają skoordynowanej aktualizacji do wszystkich usług. Spowoduje to przerwanie autonomii cyklu życia mikrousług. Jednak rozproszone struktury danych oznaczają, że nie można wykonać jednej KWAŚNej transakcji na mikrousługach. To z kolei oznacza, że należy użyć spójności ostatecznej, gdy proces biznesowy obejmuje wiele mikrousług. Jest to znacznie trudniejsze do zaimplementowania niż proste sprzężenia SQL, ponieważ nie można utworzyć ograniczeń integralności ani używać transakcji rozproszonych między oddzielnymi bazami danych, ponieważ wyjaśnimy to później. Podobnie wiele innych funkcji relacyjnych baz danych nie jest dostępnych w wielu mikrousługach.

Jeszcze więcej, różne mikrousługi często używają różnych *rodzajów* baz danych. Nowoczesne aplikacje przechowują i przetwarzają różne rodzaje danych, a relacyjna baza danych nie zawsze jest najlepszym wyborem. W przypadku niektórych przypadków użycia baza danych NoSQL, taka jak Azure CosmosDB lub MongoDB, może mieć wygodniejszy model danych i zapewnia lepszą wydajność i skalowalność niż baza danych SQL, taka jak SQL Server lub Azure SQL Database. W innych przypadkach relacyjna baza danych jest nadal najlepszym rozwiązaniem. W związku z tym aplikacje oparte na mikrousługach często używają kombinacji baz danych SQL i NoSQL, które są czasami nazywane podejściem [trwałości Polyglot](https://martinfowler.com/bliki/PolyglotPersistence.html) .

Polyglot — stała architektura dla magazynu danych ma wiele korzyści. Obejmują one luźno powiązane usługi i lepszą wydajność, skalowalność, koszty i możliwości zarządzania. Można jednak wprowadzić pewne wyzwania związane z zarządzaniem danymi, jak wyjaśniono w dalszej części tego rozdziału "[Identyfikowanie granic modelu domeny](identify-microservice-domain-model-boundaries.md)".

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>Relacja między mikrousługami i ograniczonym wzorcem kontekstu

Koncepcja mikrousługi pochodzi ze [wzorca powiązanego kontekstu (BC)](https://martinfowler.com/bliki/BoundedContext.html) w [projekcie opartym na domenie (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design). DDD zajmuje się dużymi modelami, dzieląc je na wiele usług BCs i w sposób jawny w zakresie ich granic. Każda BC musi mieć własny model i bazę danych; podobnie każda mikrousługa posiada odpowiednie dane. Ponadto każda BC ma zazwyczaj własny, powszechny [Język](https://martinfowler.com/bliki/UbiquitousLanguage.html) , aby pomóc w komunikacji między deweloperami oprogramowania i ekspertami domeny.

Te warunki (głównie jednostki domeny) w powszechnym języku mogą mieć różne nazwy w różnych powiązanych kontekstach, nawet jeśli różne jednostki domeny mają tę samą tożsamość (czyli unikatowy identyfikator używany do odczytywania jednostki z magazynu). Na przykład w ograniczonym kontekście profilu użytkownika jednostka domeny użytkownika może współużytkować tożsamość z jednostką domeny kupca w kontekście porządkowania.

Mikrousługa jest tak jak w przypadku kontekstu ograniczonego, ale określa również, że jest to usługa rozproszona. Jest on zbudowany jako oddzielny proces dla każdego powiązanego kontekstu i musi korzystać z wymienionych wcześniej protokołów rozproszonych, takich jak HTTP/HTTPS, WebSockets lub [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Jednak powiązany wzorzec kontekstu nie określa, czy powiązany kontekst jest usługą rozproszoną, czy też jest po prostu granicą logiczną (taką jak podsystem generyczną) w ramach aplikacji ze specyfikatorem litym.

Należy zaznaczyć, że zdefiniowanie usługi dla każdego powiązanego kontekstu jest dobrym miejscem do uruchomienia. Ale nie musisz ograniczać projektu do niego. Czasami musisz zaprojektować ograniczony kontekst lub mikrousługę biznesową składającą się z kilku usług fizycznych. Jednak zarówno kontekst, jak i mikrousługa powiązane z wzorcem są ściśle powiązane.

DDD zalety mikrousług, uzyskując rzeczywiste granice w postaci rozproszonych mikrousług. Jednak pomysły, takie jak nieudostępniające modelu między mikrousługami, są również potrzebne w ograniczonym kontekście.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Krzysztof Richardson. Wzorzec: baza danych na usługę** \
  <https://microservices.io/patterns/data/database-per-service.html>

- **Fowlera Martin. BoundedContext** \
  <https://martinfowler.com/bliki/BoundedContext.html>

- **Fowlera Martin. PolyglotPersistence** \
  <https://martinfowler.com/bliki/PolyglotPersistence.html>

- **Alberto Brandolini. Projekt strategiczny oparty na domenie z mapowaniem kontekstu** \
  <https://www.infoq.com/articles/ddd-contextmapping>

>[!div class="step-by-step"]
>[Poprzedni](microservices-architecture.md)
>[dalej](logical-versus-physical-architecture.md)
