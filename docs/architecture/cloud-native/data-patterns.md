---
title: Wzorce danych natywnych w chmurze
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Wzorce danych natywnych w chmurze
ms.date: 06/30/2019
ms.openlocfilehash: 8fc5a09dca61e6644fdcaa692ff1a21f40ebf179
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183414"
---
# <a name="cloud-native-data-patterns"></a>Wzorce danych natywnych w chmurze

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Zdecentralizowane dane mogą prowadzić do zwiększenia wydajności, skalowalności i oszczędności kosztów, a także wiele wyzwań. Wykonywanie zapytań dotyczących danych w mikrousługach jest złożone. Transakcja, która obejmuje mikrousługi, musi być zarządzana programowo, ponieważ transakcje rozproszone nie są obsługiwane w aplikacjach natywnych w chmurze. Przenosisz ze świata *natychmiastowej spójności* do *spójności ostatecznej*.

Omawiamy te wyzwania teraz.

## <a name="cross-service-queries"></a>Zapytania międzyusługowe

Jak aplikacja wykonuje zapytania dotyczące danych, które są rozłożone na wiele niezależnych mikrousług?

Na rysunku 5-4 przedstawiono ten scenariusz.

![Wykonywanie zapytań na mikrousługach](./media/cross-service-query.png)

**Rysunek 5-4**. Wykonywanie zapytań na mikrousługach

Zwróć uwagę na to, jak na powyższym rysunku zobaczymy mikrousługę koszyka zakupów, która dodaje element do koszyka zakupów użytkownika. Chociaż magazyn danych koszyka zakupów zawiera tabelę koszyka i lineItem, nie zawiera danych o produkcie ani cenach, ponieważ te elementy znajdują się w mikrousługach produktu i cen. Aby dodać element, usługa koszyka zakupów potrzebuje danych produktu i cennika. Jakie są opcje uzyskiwania informacji o produkcie i cenach?

Rysunek 5-5 przedstawia mikrousługi koszyka zakupów bezpośrednie wywołanie protokołu HTTP zarówno do wykazu produktów, jak i mikrousług cenowych.

![Bezpośrednia komunikacja http](./media/direct-http-communication.png)

**Rysunek 5-5**. Bezpośrednia komunikacja HTTP

Chociaż jest to możliwe do wdrożenia, w rozdziale 4 opisano sposób bezpośredniego wywoływania protokołu HTTP w mikrousługach, a nie jako dobre rozwiązanie.

Możemy zaimplementować mikrousługę agregatora przedstawioną na rysunku 5-6.

![Mikrousługa agregatora](./media/aggregator-microservice.png)

**Rysunek 5-6.** Mikrousługa agregatora

Chociaż to podejście hermetyzuje przepływ pracy operacji biznesowej w pojedynczej mikrousłudze, zwiększa złożoność i nadal prowadzi bezpośrednie wywołania HTTP.

Typowym podejściem do wykonywania zapytań wykonywanych przez wiele usług jest użycie [wzorca widoku materiałowego](https://docs.microsoft.com/azure/architecture/patterns/materialized-view), pokazanego na rysunku 5-7.

![Wzorzec widoku materiałowego](./media/materialized-view-pattern.png)

**Figure5-7**. Wzorzec widoku materiałowego

Za pomocą tego wzorca bezpośrednio umieszczasz tabelę lokalną (nazywaną *modelem odczytu*) w usłudze koszyka zakupów, która zawiera nieznormalizowaną kopię danych, która jest wymagana od mikrousług produktu i cen. Umieszczenie tych danych w ramach usługi koszyka zakupów eliminuje konieczność wywoływania kosztownych wywołań międzyusługowych. W przypadku danych lokalnych dla usługi można poprawić czas odpowiedzi i niezawodność.

Catch z tym podejściem ma teraz duplikaty danych w systemie. W systemach natywnych w chmurze duplikaty danych nie są uznawane za [Antywzorzec](https://en.wikipedia.org/wiki/Anti-pattern) i są zwykle zaimplementowane w systemach natywnych w chmurze. Jednak jeden i tylko jeden system może być właścicielem dowolnego zestawu danych i należy zaimplementować mechanizm synchronizacji dla systemu rejestrowania, aby zaktualizować wszystkie skojarzone modele odczytu, gdy następuje zmiana danych źródłowych.

## <a name="transactional-support"></a>Obsługa transakcyjna

Podczas gdy zapytania między mikrousługami są trudne, wdrożenie transakcji w mikrousługach może być skomplikowane. Nieodłączne wyzwanie związane z utrzymywaniem spójności danych między źródłami danych znajdującymi się w różnych mikrousługach nie jest możliwe. Rysunek 5-8 pokazuje problem.

![Transakcja w wzorcu Saga](./media/saga-transaction-operation.png)

**Rysunek 5-8**. Implementowanie transakcji w mikrousługach

Zwróć uwagę na to, jak w poprzednim rysunku pięciu niezależnych mikrousług wszyscy uczestniczą w rozproszonej transakcji *tworzenia zamówienia* . Jednakże transakcja dla każdego z pięciu poszczególnych mikrousług musi się powieść lub wszystkie muszą przerwać operację. Wbudowana obsługa transakcyjna jest dostępna w ramach każdej mikrousług, ale nie jest obsługiwana transakcja rozproszona w ramach wszystkich pięciu usług.

Ponieważ obsługa transakcyjna jest istotna dla tej operacji, aby zachować spójność danych w poszczególnych mikrousługach, należy programowo skonstruować transakcję rozproszoną.

Popularnym wzorcem do programistycznego dodawania obsługi transakcyjnej jest [wzorzec Saga](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/). Jest to implementowane przez grupowanie transakcji lokalnych razem i sekwencyjne wywoływanie każdego z nich. Jeśli transakcja lokalna nie powiedzie się, Saga przerywa operację i wywołuje zestaw [kompensowania transakcji](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction) , aby cofnąć zmiany wprowadzone przez poprzednie transakcje lokalne. Rysunek 5-9 pokazuje nieudaną transakcję ze wzorcem Saga.

![Wycofywanie w wzorcu Saga](./media/saga-rollback-operation.png)

**Rysunek 5-9**. Wycofywanie transakcji

Zwróć uwagę na to, jak na poprzednim rysunku operacja *GenerateContent* nie powiodła się w mikrousłudze muzycznej. Saga wywołuje kompensowanie transakcji (czerwony) do usunięcia zawartości, anuluje płatność i anuluje zamówienie, zwracając dane dla każdej mikrousługi z powrotem do spójnego stanu.

Wzorce Saga są zwykle choreographed jako serie powiązanych zdarzeń lub zorganizowane jako zestaw powiązanych poleceń.

## <a name="cqrs-pattern"></a>Wzorzec CQRS

CQRS, lub [Command and Query Responsibility Segregation](https://docs.microsoft.com/azure/architecture/patterns/cqrs), to wzorzec architektoniczny, który oddziela operacje odczytujące dane z tych, które zapisują dane. Ten wzorzec może pomóc w maksymalizacji wydajności, skalowalności i bezpieczeństwa.

W normalnych scenariuszach dostępu do danych implementowany jest jeden model (obiekt jednostki i repozytorium), który wykonuje *operacje odczytu i* zapisu danych.

Jednak bardziej zaawansowany scenariusz dostępu do danych może korzystać z oddzielnych modeli i tabel danych do odczytu i zapisu. Aby zwiększyć wydajność, operacja odczytu, znana jako *zapytanie*, może wykonywać zapytania względem wysoce nieznormalizowanej reprezentacji danych, aby uniknąć kosztownych sprzężeń między tabelami. Podczas gdy operacja *zapisu* , znana jako *polecenie*, może być aktualizowana względem w pełni znormalizowanej reprezentacji danych. Następnie należy zaimplementować mechanizm, aby zachować obie reprezentacje w synchronizacji. Zazwyczaj zawsze, gdy tabela zapisu zostanie zmodyfikowana, wywołuje zdarzenie, które replikuje modyfikację danych do tabeli Odczytaj.

Na rysunku 5-10 przedstawiono implementację wzorca CQRS.

![Implementacja CQRS](./media/cqrs-implementation.png)

**Rysunek 5-10**. Implementacja CQRS

Zwróć uwagę na to, jak w poprzednim rysunku są implementowane poszczególne modele poleceń i zapytań. Ponadto każda operacja zapisu danych jest zapisywana w magazynie zapisu, a następnie propagowana do magazynu odczytu. Należy zwrócić szczególną uwagę na to, jak proces propagacji działa zgodnie z zasadą [spójności ostatecznej](https://www.cloudcomputingpatterns.org/eventual_consistency/), podczas gdy model odczytu ostatecznie synchronizuje się z modelem zapisu, ale może wystąpić pewne opóźnienia w procesie.

Wdrożenie separacji pozwala na skalowanie odczytów i zapisów oddzielnie. Ponadto można nałożyć ściślejsze zabezpieczenia na operacje zapisu niż w przypadku operacji odczytu.

Zwykle wzorce CQRS są stosowane do ograniczonych sekcji systemu w zależności od konkretnych potrzeb.

## <a name="relational-vs-nosql"></a>Relacyjne vs NoSQL

Nie można zastanowić się nad wpływem technologii [NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) , szczególnie w przypadku rozproszonych systemów natywnych w chmurze. Rozprzestrzenianie się nowych technologii danych w tym miejscu ma zakłócone rozwiązania, które są dostępne tylko w odniesieniu do relacyjnych baz danych.

Z jednej strony relacyjne bazy danych były powszechnie rozpowszechnioną technologią dla dekad. Są one dojrzałe, sprawdzone i szeroko implementowane. Konkurencyjne produkty bazy danych, doświadczenie i narzędzia abounds. Relacyjne bazy danych zapewniają magazyn powiązanych tabel danych. Te tabele mają stały schemat, za pomocą programu SQL (Structured Query Language) można zarządzać danymi i mieć zapewniony [kwas](https://www.geeksforgeeks.org/acid-properties-in-dbms/) (znany także jako niepodzielność, spójność, izolacja i trwałość).

Bazy danych bez programu SQL po drugiej stronie zapoznaj się z tematem magazyny o wysokiej wydajności, nierelacyjne. Są one w programie Excel w ich łatwość użycia, skalowalności, odporności i dostępności. Zamiast sprzęgać tabele znormalizowanych danych, NoSQL przechowuje własne opisy (bez schematu) dane zazwyczaj w dokumentach JSON. Nie oferują one gwarancji [kwaśnych](https://www.geeksforgeeks.org/acid-properties-in-dbms/) .

Sposób zrozumienia różnic między tymi typami baz danych można znaleźć w [theorem Cap](https://towardsdatascience.com/cap-theorem-and-distributed-database-management-systems-5c2be977950e), zestaw zasad, które mogą być stosowane do systemów rozproszonych, które są przechowywane w stanie. Rysunek 5-11 pokazuje trzy właściwości CAP theorem.

![Theorem CAP](./media/cap-theorem.png)

**Rysunek 5-11**. Theorem zakończenia

Theorem stwierdza, że każdy rozproszony system danych będzie oferować kompromis między spójnością, dostępnością i tolerancją partycji oraz że każda baza danych może zagwarantować tylko dwie z trzech właściwości:

- *Spójność*: każdy węzeł w klastrze będzie odpowiadał na najnowsze dane, nawet jeśli wymaga zablokowania żądania do momentu, aż wszystkie repliki zostaną prawidłowo zaktualizowane.

- *Dostępność*: każdy węzeł zwróci odpowiedź w rozsądnym czasie, nawet jeśli ta odpowiedź nie jest najnowszą ilością danych.

- *Tolerancja partycji*: gwarantuje, że system będzie kontynuował działanie, jeśli węzeł ulegnie awarii lub utraci połączenie z innym.

Relacyjne bazy danych wykazują spójność i dostępność, ale nie tolerancję partycji. Partycjonowanie relacyjnej bazy danych, takiej jak fragmentowania, jest trudne i może mieć wpływ na wydajność.

Z drugiej strony bazy danych NoSQL zwykle wykazują tolerancję partycji, znaną jako skalowalność i wysoką dostępność. Ponieważ theorem CAP określa, można mieć tylko dwie z trzech zasad i utracić Właściwość spójności.

Bazy danych NoSQL są dystrybuowane i często skalowane na serwerach asortymentu. Takie działanie może zapewnić doskonałą dostępność, zarówno w regionie, jak i w regionach geograficznych, przy niższych kosztach. Dane mogą być partycjonowane i replikowane na tych maszynach, na węzłach, w celu zapewnienia nadmiarowości i odporności na uszkodzenia. Minusem jest spójna. Zmiana danych w jednym węźle NoSQL może zająć trochę czasu do innych węzłów. Zazwyczaj węzeł bazy danych NoSQL będzie dostarczać natychmiastową odpowiedź do zapytania, nawet jeśli dane, które są obecnie wysyłane, są przestarzałe i nie zostały jeszcze zaktualizowane.

Jest to znana [spójność ostateczna](https://www.cloudcomputingpatterns.org/eventual_consistency/), charakterystyczną dla rozproszonych systemów danych, w której nie są obsługiwane transakcje kwasowe. Jest to krótkie opóźnienie między aktualizacją elementu danych i czasu potrzebnego do propagowania tej aktualizacji do poszczególnych węzłów repliki. W przypadku zaktualizowania elementu produktu w bazie danych NoSQL w Stany Zjednoczone, ale w tym samym czasie zapytanie o ten sam element danych z węzła repliki w Europie, można pobrać wcześniejsze informacje o produkcie — do momentu zaktualizowania węzła Europejskiego przy zmianie produktu. W związku z tym, że jest to spowodowane [silną spójnością](https://en.wikipedia.org/wiki/Strong_consistency), oczekiwanie na zaktualizowanie wszystkich węzłów repliki przed zwróceniem wyników zapytania, można obsługiwać ogromny rozmiar i ilość ruchu sieciowego, ale z możliwością przedsprzedaży starszych danych.

Bazy danych NoSQL można klasyfikować według następujących czterech modeli: 

- *Magazyn dokumentów* (MongoDB, CouchDB, Couchbase): dane (i odpowiadające im metadane) są przechowywane w nierelacyjny sposób w nieznormalizowanych dokumentach opartych na notacji JSON w bazie danych.

- *Magazyn kluczy/wartości* (Redis, Riak, Memcached): dane są przechowywane w prostych parach klucz-wartość z operacjami systemu wykonywanymi przy użyciu unikatowego klucza dostępu, który jest mapowany na wartość danych użytkownika.

- *Magazyn szerokiej kolumny* (HBase, Cassandra): powiązane dane są przechowywane w formacie kolumnowy jako zestaw par zagnieżdżonych/wartości w jednej kolumnie z danymi, które są zwykle pobierane jako pojedyncze jednostki bez konieczności sprzęgania wielu tabel jednocześnie.

- *Sklepy grafów* (Neo4j, Titan): dane są przechowywane jako graficzna reprezentacja w węźle wraz z krawędziami określającymi relację między węzłami.

Bazy danych NoSQL można zoptymalizować pod kątem obsługi danych na dużą skalę, zwłaszcza wtedy, gdy dane są stosunkowo proste. Bazę danych NoSQL należy wziąć pod uwagę w przypadku:

- Obciążenie wymaga dużej skali i dużej współbieżności.
- Masz dużą liczbę użytkowników.
- Dane można wyrazić po prostu bez relacji.
- Konieczne jest geograficznie dystrybuowanie danych.
- Nie potrzebujesz gwarancji KWAŚNych.
- Zostanie wdrożony na sprzęcie z asortymentami.

Następnie należy wziąć pod uwagę relacyjną bazę danych, gdy:

- Twoje obciążenia wymagają średniego na dużą skalę.
- Współbieżność nie jest istotna.
- Są konieczne gwarancje KWAŚNe.
- Dane są najlepiej wyrażone w sposób relacyjny.
- Aplikacja zostanie wdrożona na dużym sprzęcie.

Następnie zapoznaj się z magazynem danych w chmurze platformy Azure.

>[!div class="step-by-step"]
>[Poprzedni](distributed-data.md)
>[Następny](azure-data-storage.md)
