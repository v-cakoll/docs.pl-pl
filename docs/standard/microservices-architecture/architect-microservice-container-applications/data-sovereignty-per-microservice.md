---
title: Suwerenności danych na mikrousługi
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Suwerenności danych na mikrousługi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: d739cc33dec372f6bd9569c05d034dcd25be8395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="data-sovereignty-per-microservice"></a>Suwerenności danych na mikrousługi

Ważne reguły dla architektury mikrousług jest, czy każdy mikrousługi musi być właścicielem jego danych domeny i logiki. Tak samo, jak Pełna aplikacji jest właścicielem jego logikę i dane, więc musi każdego mikrousługi właścicielem jego logikę i dane w ramach autonomicznej cykl życia, niezależnie od wdrożenia na mikrousługi.

Oznacza to, że model koncepcyjny domeny będą się różnić między podsystemami lub mikrousług. Należy wziąć pod uwagę aplikacje dla przedsiębiorstw, gdzie relacji Zarządzanie Klientami aplikacji klienta, transakcyjne zakupu podsystemów i podsystemy Obsługa klienta każde wywołanie na atrybuty obiektu unikatowy klienta i dane, a każdy wykorzystuje inny Ograniczone kontekstu (BC).

Ta zasada jest podobna [projektowanie oparte na domenie (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design), gdzie każdego [ograniczone kontekstu](https://martinfowler.com/bliki/BoundedContext.html) lub podsystemu autonomicznego lub usługi musi być właścicielem jego model domeny (danych oraz logiki i zachowanie). Każdy kontekst ograniczone DDD są powiązane z jedną mikrousługi business (co najmniej jednej usługi). (Możemy rozwiń w tym punkcie o wzorcu ograniczone kontekstu w następnej sekcji.)

Z drugiej strony podejście tradycyjnych (dane wbudowanymi) używany w wielu aplikacjach ma kilka baz danych lub jeden scentralizowanej bazie danych. Często jest znormalizowane bazy danych SQL, używany dla całej aplikacji i wszystkich jego podsystemów wewnętrznych, jak pokazano w rysunek 4-7.

![](./media/image7.png)

**Rysunek 4-7**. Porównanie suwerenności danych: wbudowanymi bazy danych i mikrousług

Podejście scentralizowanej bazie danych początkowo wygląda prostszy i wydaje się, aby umożliwić ponowne użycie jednostek w różne podsystemy do wszystkich spójne. Ale rzeczywistego jest na końcu dużych tabel, obsługujących wiele różne podsystemy zawierające atrybuty i kolumny, które nie są wymagane w większości przypadków. Przypomina to próby Użyj tej samej fizycznej mapy piesze krótkich ślad, biorąc podróży samochodu long dnia i uczenia geograficznych.

Wbudowanymi aplikacji zwykle pojedynczego relacyjna baza danych ma dwa istotne zalety: [transakcje ACID](https://en.wikipedia.org/wiki/ACID) i języka SQL, zarówno pracy we wszystkich tabelach i dane związane z aplikacji. Takie podejście umożliwia łatwe Napisz zapytanie, które łączy dane z wielu tabel.

Jednak dostęp do danych staje się bardziej złożonej, w przypadku przenoszenia do architektury mikrousług. Jednak nawet wtedy, gdy transakcje ACID można lub powinny być używane w ramach mikrousługi lub ograniczonych kontekstu, danych należących do każdego mikrousługi jest oznaczony jako prywatny tego mikrousługi i można uzyskać tylko za pośrednictwem jej interfejsu API mikrousługi. Zawieranie danych gwarantuje, że mikrousług są luźno powiązane i mogą rozwijać, niezależnie od siebie. Jeśli wiele usług zostały dostęp do tych samych danych, aktualizacje schematu wymagają skoordynowanego aktualizacji do wszystkich usług. Spowoduje to przerwanie Autonomia cyklu życia mikrousługi. Ale struktur danych rozproszonych oznacza, że nie można wprowadzić pojedynczej transakcji ACID między mikrousług. Z kolei oznacza to, że należy użyć spójność ostateczna, gdy proces biznesowy obejmuje wiele mikrousług. To jest trudniejsze do zaimplementowania niż proste sprzężenia SQL; Podobnie wielu innych funkcji relacyjnej bazy danych nie są dostępne w wielu mikrousług.

Kontynuowanie nawet, różnych mikrousług często używają różnych *rodzajów* baz danych. Nowoczesne aplikacje sklepu i procesu różnych rodzajów danych oraz relacyjnej bazy danych nie zawsze jest najlepszym rozwiązaniem. Dla niektórych zastosowań, bazą danych NoSQL, takie jak usługa Azure DocumentDB lub baza danych MongoDB może mieć wygodniejsze modelu danych i oferuje lepszą wydajność i skalowalność niż baza danych SQL, takich jak SQL Server lub baza danych SQL Azure. W pozostałych przypadkach relacyjnej bazy danych nadal jest najlepszym rozwiązaniem. W związku z tym aplikacji opartych na mikrousług często używają kombinację bazy danych SQL i NoSQL, który jest czasami nazywany [polyglot trwałości](https://martinfowler.com/bliki/PolyglotPersistence.html) podejście.

Podzielone na partycje, trwałe polyglot architektury do przechowywania danych ma wiele korzyści. Obejmują one luźno powiązanych usług i lepszą wydajność, skalowalność, kosztów i możliwości zarządzania. Jednak go mogą stać się pewne wyzwania zarządzania danych rozproszonych, ponieważ Wyjaśnijmy w "[identyfikujące model domeny granice](#identifying-domain-model-boundaries-for-each-microservice)" dalej w tym rozdziale.

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>Relacja między mikrousług i wzorzec ograniczone kontekstu

Pojęcie mikrousługi pochodną [wzorzec kontekstu ograniczone (BC)](https://martinfowler.com/bliki/BoundedContext.html) w [projektowanie oparte na domenie (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design). DDD dotyczy dużych modeli przez podzielenie ich na wielu usług łączności biznesowej, a w rezultacie jawne o ich granic. Każdy BC musi mieć własne modelu i bazy danych. Podobnie każda mikrousługi właścicielem jego danych powiązanych. Ponadto każdy BC zwykle ma własną [powszechny języka](https://martinfowler.com/bliki/UbiquitousLanguage.html) ułatwiające komunikację między programistami i ekspertów domeny.

Te warunki (głównie domeny jednostek) w języku uniwersalnych może mieć różne nazwy elementu w różnych kontekstach ograniczone, nawet wtedy, gdy różne domeny jednostek udział tej samej tożsamości (to znaczy Unikatowy identyfikator, który jest używany do odczytu jednostki z magazynu). Na przykład w kontekście ograniczony profil użytkownika, jednostką domeny użytkownika może udostępniać tożsamości jednostką domeny nabywców w kontekście porządkowania ograniczone.

Mikrousługi w związku z tym przypomina kontekst ograniczone, ale również określa, że jest rozproszonego usługi. Jest ona wbudowana procesów odrębnych dla każdego z ograniczonym kontekstu i protokoły rozproszonego wspomniano wcześniej, takich jak HTTP/HTTPS, Websocket, należy użyć lub [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Wzorzec ograniczone kontekstu, jednak nie określa czy kontekst ograniczone są usługami rozproszonymi, lub jeśli jest to po prostu granicę logiczne (na przykład ogólny podsystemu) aplikacji wbudowanymi wdrożenia.

Jest ważne wyróżnić, że definiowanie usługi dla każdego z ograniczonym kontekstu jest dobrym miejscem do rozpoczęcia. Ale nie trzeba ograniczyć projektu do niego. Czasami należy projektować kontekst ograniczone lub business mikrousługi składa się z kilku usług fizycznych. Ale ostatecznie oba wzorce — ograniczone kontekstu i mikrousługi — są ściśle powiązane.

DDD korzyści z mikrousług pobierając rzeczywistych granic w formie mikrousług rozproszonych. Ale pomysły, takie jak udostępnianie nie modelu między mikrousług co również ma w kontekście ograniczone.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Krzysztof Richardson. Wzorzec: Bazy danych usługi**
    [*https://microservices.io/patterns/data/database-per-service.html*](https://microservices.io/patterns/data/database-per-service.html)

-   **Pole Fowler. BoundedContext**
    [*https://martinfowler.com/bliki/BoundedContext.html*](https://martinfowler.com/bliki/BoundedContext.html)

-   **Pole Fowler. PolyglotPersistence**
    [*https://martinfowler.com/bliki/PolyglotPersistence.html*](https://martinfowler.com/bliki/PolyglotPersistence.html)

-   **Alberto Brandolini. Strategiczne domeny na projekt z mapowaniem kontekstu**
    [*https://www.infoq.com/articles/ddd-contextmapping*](https://www.infoq.com/articles/ddd-contextmapping)


>[!div class="step-by-step"]
[Poprzednie] (mikrousług architecture.md) [dalej] (logiczne i fizycznych architecture.md)
