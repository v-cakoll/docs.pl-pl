---
title: Baza danych na mikrousługę
description: Kontrast przechowywania danych w aplikacjach monolitycznych i natywnych dla chmury.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: c0c5611fa866d70f155e4bdad2eee1181b13c065
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141448"
---
# <a name="database-per-microservice"></a>Baza danych na mikrousługę

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jak widzieliśmy w całej tej książce, podejście natywne dla chmury zmienia sposób projektowania, wdrażania i zarządzania aplikacjami. Zmienia również sposób zarządzania i przechowywania danych.

Rysunek 5-1 kontrastuje różnice.

![Przechowywanie danych w aplikacjach natywnych dla chmury](./media/distributed-data.png)

**Rysunek 5-1**. Zarządzanie danymi w aplikacjach natywnych dla chmury

Doświadczeni deweloperzy z łatwością rozpoznają architekturę po lewej stronie rysunku 5-1. W tej *aplikacji monolityczne*, składniki usługi biznesowej kolokacji razem w warstwie usług udostępnionych, udostępnianie danych z jednej relcyjnej bazy danych.

Na wiele sposobów pojedyncza baza danych ułatwia zarządzanie danymi. Wykonywanie zapytań dotyczących danych w wielu tabelach jest proste. Zmiany w aktualizacji danych razem lub wszystkie one wycofać. [Transakcje ACID](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) gwarantują silną i natychmiastową spójność.

Projektowanie dla chmury rodzimych, mamy inne podejście. Po prawej stronie rysunku 5-1 należy zwrócić uwagę na sposób, w jaki funkcje biznesowe są segregowane w małe, niezależne mikrousługi. Każda mikrousługa hermetyzuje określone możliwości biznesowe i własne dane. Monolityczne bazy danych rozkłada się w modelu rozproszonych danych z wielu mniejszych baz danych, każdy dostosowanie do mikrousługi. Gdy dym czyści, wyłaniamy się z projektem, który udostępnia *bazy danych na mikrousługi*.

## <a name="why"></a>Dlaczego?

Ta baza danych na mikrousługi zapewnia wiele korzyści, szczególnie w przypadku systemów, które muszą szybko ewoluować i obsługiwać dużą skalę. Z tym modelem...

- Dane domeny są hermetyzowane w ramach usługi
- Schemat danych może ewoluować bez bezpośredniego wpływu na inne usługi
- Każdy magazyn danych może niezależnie skalować
- Awaria magazynu danych w jednej usłudze nie wpłynie bezpośrednio na inne usługi

Segregowanie danych umożliwia również każdej mikrousługi do zaimplementowania typu magazynu danych, który jest najlepiej zoptymalizowany pod kątem jego obciążenia, potrzeb magazynu i odczytu/zapisu wzorców. Dostępne opcje obejmują relacyjne, dokumentowe, kluczowe, a nawet oparte na wykresie magazyny danych.

Rysunek 5-2 przedstawia zasadę trwałości polyglot w systemie natywnym dla chmury.

![Trwałość danych polyglot](./media/polyglot-data-persistence.png)

**Rysunek 5-2**. Trwałość danych polyglot

Uwaga na poprzednim rysunku, jak każda mikrousługa obsługuje inny typ magazynu danych.

- Mikrousługi katalogu produktów zużywa relacyjnej bazy danych, aby pomieścić bogatą strukturę relacyjnej danych źródłowych.
- Mikrousługi koszyka zakupów zużywa rozproszonej pamięci podręcznej, która obsługuje jego prosty magazyn danych o wartości klucza.
- Mikrousługi zamawiania używa zarówno bazy danych dokumentów NoSql dla operacji zapisu wraz z magazynu kluczy/wartości wysoce nieznormalizowane, aby pomieścić duże ilości operacji odczytu.
  
Podczas gdy relacyjne bazy danych pozostają istotne dla mikrousług ze złożonymi danymi, bazy danych NoSQL zyskały znaczną popularność. Zapewniają one ogromną skalę i wysoką dostępność. Ich charakter bez schematu umożliwia deweloperom odejście od architektury typowane klasy danych i ORM, które sprawiają, że zmiany kosztowne i czasochłonne. Omówimy bazy danych NoSQL w dalszej części tego rozdziału.

 Hermetyzując dane w oddzielnych mikrousług może zwiększyć elastyczność, wydajność i skalowalność, również przedstawia wiele wyzwań. W następnej części omawiamy te wyzwania wraz ze wzorcami i praktykami, które pomogą je przezwyciężyć.  

## <a name="cross-service-queries"></a>Zapytania między usługami

Mikrousługi są niezależne i koncentrują się na określonych możliwościach funkcjonalnych, takich jak spis, wysyłka lub zamawianie, często wymagają integracji z innymi mikrousługami. Często integracja obejmuje jedną mikrousługę *wykonywania zapytań* innej dla danych. Rysunek 5-3 przedstawia scenariusz.

![Wykonywanie zapytań w mikrousługach](./media/cross-service-query.png)

**Rysunek 5-3**. Wykonywanie zapytań w mikrousługach

Na powyższym rysunku widzimy mikrousługi koszyka zakupów, który dodaje element do koszyka zakupów użytkownika. Magazyn danych dla tej mikrousługi zawiera dane koszyka i elementu zamówienia, ale nie przechowuje danych o produktach ani cenach. Zamiast tego te elementy danych są własnością mikrousług katalogu i cen. Stanowi to problem. W jaki sposób mikrousługa koszyka zakupów może dodać produkt do koszyka zakupów użytkownika, gdy nie ma produktu ani danych cenowych w swojej bazie danych?

Jedną z opcji omówionych w rozdziale 4 jest [bezpośrednie wywołanie HTTP](service-to-service-communication.md#queries) z koszyka do mikrousług katalogu i cen. Jednak w rozdziale 4 powiedzieliśmy synchroniczne HTTP wywołuje *kilka* mikrousług razem, zmniejszając ich autonomię i zmniejszając ich korzyści architektoniczne.

Możemy również zaimplementować wzorzec żądania i odpowiedzi z oddzielnymi kolejkami przychodzącymi i wychodzącymi dla każdej usługi. Jednak ten wzorzec jest skomplikowane i wymaga hydraulika skorelować żądania i odpowiedzi wiadomości.
Podczas gdy nie rozłączyć wywołania mikrousługi zaplecza, usługa wywołująca musi nadal synchronicznie czekać na zakończenie wywołania. Przeciążenie sieci, błędy przejściowe lub przeciążenie mikrousługi i może spowodować długotrwałe, a nawet nie powiodło się operacje.

Zamiast tego powszechnie akceptowanym wzorcem do usuwania zależności między usługami jest [zmaterializowany wzorzec widoku,](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)pokazany na rysunku 5-4.

![Zmaterializowany wzór widoku](./media/materialized-view-pattern.png)

**Rysunek 5-4**. Zmaterializowany wzór widoku

Za pomocą tego wzorca umieszczasię tabelę danych lokalnych (znaną jako *model odczytu)* w usłudze koszyka zakupów. Ta tabela zawiera nieznormalizowaną kopię danych potrzebnych z mikrousług produktu i cen. Kopiowanie danych bezpośrednio do mikrousługi koszyka zakupów eliminuje konieczność kosztownych wywołań między usługami. Dzięki danym lokalnym do usługi, można poprawić czas reakcji usługi i niezawodność. Ponadto posiadanie własnej kopii danych sprawia, że usługa koszyka jest bardziej odporna. Jeśli usługa katalogu powinna stać się niedostępna, nie wpłynie bezpośrednio na usługę koszyka. Koszyk może kontynuować działanie z danymi z własnego sklepu.

Haczyk z tego podejścia jest to, że masz teraz zduplikowane dane w systemie. Jednak *strategicznie* duplikowanie danych w systemach natywnych dla chmury jest utrwaloną praktyką i nie jest uważane za anty-wzorzec lub złe praktyki. Należy pamiętać, że *jedna i tylko jedna usługa* może posiadać zestaw danych i mieć nad nim uprawnienia. Po zaktualizowaniu systemu rekordów należy zsynchronizować modele odczytu. Synchronizacja jest zazwyczaj implementowana za pośrednictwem wiadomości asynchronicznych z [wzorcem publikowania/subskrybowania,](service-to-service-communication.md#events)jak pokazano na rysunku 5.4.

## <a name="distributed-transactions"></a>Transakcje rozproszone

Podczas wykonywania zapytań danych w mikrousługach jest trudne, implementowanie transakcji w kilku mikrousług jest jeszcze bardziej złożone. Nieodłączne wyzwanie zachowania spójności danych w niezależnych źródłach danych w różnych mikrousług nie można zaniżać. Brak transakcji rozproszonych w aplikacjach natywnych dla chmury oznacza, że należy programowo zarządzać transakcjami rozproszonymi. Przechodzisz ze świata *natychmiastowej spójności* do *ostatecznej spójności.*

Rysunek 5-5 pokazuje problem.

![Transakcja w strukturze sagi](./media/saga-transaction-operation.png)

**Rysunek 5-5**. Implementowanie transakcji w mikrousługach

Na powyższym rysunku pięć niezależnych mikrousług uczestniczyć w transakcji rozproszonej, która tworzy zamówienie. Każda mikrousługa utrzymuje własny magazyn danych i implementuje transakcję lokalną dla swojego magazynu. Aby utworzyć zamówienie, transakcja lokalna dla *każdej* mikrousługi poszczególnych musi się powieść lub *wszystkie* muszą przerwać i wycofać operację. Podczas gdy wbudowana obsługa transakcyjna jest dostępna wewnątrz każdej mikrousługi, nie ma żadnej obsługi transakcji rozproszonej, która będzie się rozciągać we wszystkich pięciu usługach, aby zachować spójność danych.

Zamiast tego należy skonstruować tę transakcję rozproszoną *programowo*.

Popularnym wzorcem dodawania rozproszonej obsługi transakcyjnej jest wzór Saga. Jest implementowana przez grupowanie transakcji lokalnych razem programowo i sekwencyjnie wywołując każdy z nich. Jeśli którakolwiek z transakcji lokalnych nie powiedzie się, Saga przerywa operację i wywołuje zestaw [transakcji kompensacyjnych](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction). Transakcje kompensacyjne cofają zmiany wprowadzone przez poprzednie transakcje lokalne i przywracają spójność danych. Rysunek 5-6 przedstawia nieudaną transakcję ze wzorem Saga.

![Wycofaj się w sagę wzór](./media/saga-rollback-operation.png)

**Rysunek 5-6**. Wycofywanie transakcji

Na poprzedniej rysunku *operacja Aktualizuj spis* uchylić się w mikrousługi zapasów. Saga wywołuje zestaw transakcji kompensacyjnych (na czerwono), aby dostosować liczbę zapasów, anulować płatności i zamówienia i zwrócić dane dla każdej mikrousługi z powrotem do stanu spójnego.

Wzorce sagi są zazwyczaj choreografia jako seria powiązanych wydarzeń lub zaaranżowane jako zestaw powiązanych poleceń. W rozdziale 4 omówiliśmy wzorzec agregatora usług, który byłby podstawą zaaranżowanej implementacji sagi. Omówiliśmy również eventing wraz z usługi Azure Service Bus i azure event grid tematów, które będą podstawą dla implementacji sagi choreografia.

## <a name="high-volume-data"></a>Dane o dużej objętości

Duże aplikacje natywne dla chmury często obsługują wymagania dotyczące danych o dużej objętości. W tych scenariuszach tradycyjne techniki przechowywania danych może spowodować wąskie gardła. W przypadku złożonych systemów wdrażanych na dużą skalę zarówno segregacja odpowiedzialności za polecenia, jak i kwerendy (CQRS) i pozyskiwanie zdarzeń może zwiększyć wydajność aplikacji.  

### <a name="cqrs"></a>CQRS

[CQRS](https://docs.microsoft.com/azure/architecture/patterns/cqrs), to wzorzec architektoniczny, który może pomóc zmaksymalizować wydajność, skalowalność i zabezpieczenia. Wzorzec oddziela operacje, które odczytują dane z tych operacji, które zapisują dane.

W przypadku normalnych scenariuszy ten sam model jednostki i obiekt repozytorium danych są używane zarówno dla operacji odczytu, *jak* i zapisu.

Jednak scenariusz danych o dużej objętości może korzystać z oddzielnych modeli i tabel danych dla odczytów i zapisów. Aby zwiększyć wydajność, operacja odczytu może kwerendy przeciwko wysoce nieznormalizowane reprezentacji danych, aby uniknąć kosztownych powtarzających się sprzężeń tabeli i blokad tabeli. Operacja *zapisu,* znana jako *polecenie,* będzie aktualizowana względem w pełni znormalizowanej reprezentacji danych, która gwarantowałaby spójność. Następnie należy zaimplementować mechanizm, aby zachować obie reprezentacje w synchronizacji. Zazwyczaj za każdym razem, gdy tabela zapisu jest modyfikowany, publikuje zdarzenie, które replikuje modyfikacji do tabeli odczytu.

Rysunek 5-7 przedstawia implementację wzorca CQRS.

![Segregacja odpowiedzialności za polecenia i kwerendy](./media/cqrs-implementation.png)

**Rysunek 5-7**. Wdrożenie CQRS

Na poprzedniej rysunku zaimplementowano oddzielne modele poleceń i zapytań. Każda operacja zapisu danych jest zapisywana w magazynie zapisu, a następnie propagowana do magazynu odczytu. Należy zwrócić szczególną uwagę na to, jak proces propagacji danych działa na zasadzie [spójności ostatecznej](http://www.cloudcomputingpatterns.org/eventual_consistency/). Model odczytu ostatecznie synchronizuje się z modelem zapisu, ale może występować pewne opóźnienia w procesie. Omówimy spójność ostateczną w następnej sekcji.

Ta separacja umożliwia odczyty i zapisy do skalowania niezależnie. Operacje odczytu używają schematu zoptymalizowanego pod kątem kwerend, podczas gdy zapisy używają schematu zoptymalizowanego pod kątem aktualizacji. Kwerendy odczytu są sprzeczne z danymi nieznormalizowanych, podczas gdy złożona logika biznesowa może być stosowana do modelu zapisu. Jak również można nałożyć ściślejsze zabezpieczenia na operacje zapisu niż te narażające odczyty.

Implementowanie CQRS może zwiększyć wydajność aplikacji dla usług natywnych dla chmury. Jednak powoduje to bardziej złożony projekt. Zastosuj tę zasadę ostrożnie i strategicznie do tych sekcji aplikacji natywnej dla chmury, które będą z niej korzystać. Aby uzyskać więcej informacji na temat CQRS, zobacz książkę Microsoft [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/apply-simplified-microservice-cqrs-ddd-patterns).

### <a name="event-sourcing"></a>Pozyskiwanie zdarzeń

Inne podejście do optymalizacji scenariuszy danych o dużej objętości obejmuje [pozyskiwanie zdarzeń.](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

System zazwyczaj przechowuje bieżący stan jednostki danych. Jeśli użytkownik zmieni swój numer telefonu, na przykład rekord klienta zostanie zaktualizowany o nowy numer. Zawsze znamy bieżący stan jednostki danych, ale każda aktualizacja zastępuje poprzedni stan.

W większości przypadków ten model działa dobrze. Jednak w systemach o dużej objętości obciążenie wynikające z operacji blokowania transakcyjnego i częstych aktualizacji może mieć wpływ na wydajność bazy danych, czas reakcji i skalowalność ograniczenia.

Pozyskiwanie zdarzeń ma inne podejście do przechwytywania danych. Każda operacja, która wpływa na dane jest utrwaliony do magazynu zdarzeń. Zamiast aktualizować stan rekordu danych, dołączamy każdą zmianę do sekwencyjnej listy przeszłych zdarzeń - podobnie jak w księdze księgowej. Magazyn zdarzeń staje się systemem rekordów danych. Jest on używany do propagowania różnych zmaterializowanych widoków w kontekście ograniczone mikrousługi. Rysunek 5.8 przedstawia wzór.

![Określanie źródła zdarzeń](./media/event-sourcing.png)

**Rysunek 5-8**. Określanie źródła zdarzeń

Na poprzednim rysunku należy zwrócić uwagę na to, jak każdy wpis (na niebiesko) koszyka użytkownika jest dołączany do bazowego magazynu zdarzeń. W sąsiednim widoku zmaterializowanym system wyświetla bieżący stan, odtwarzając wszystkie zdarzenia skojarzone z każdym koszykiem. Ten widok lub model odczytu jest następnie udostępniane z powrotem do interfejsu interfejsu. Zdarzenia mogą być również zintegrowane z zewnętrznymi systemami i aplikacjami lub badane w celu określenia bieżącego stanu jednostki. Dzięki takiemu podejściu zachowujesz historię. Wiesz nie tylko bieżący stan jednostki, ale także sposób osiągnięcia tego stanu.

Mechanicznie rzecz biorąc, pozyskiwanie zdarzeń upraszcza model zapisu. Nie ma żadnych aktualizacji ani usuwania. Dołączanie każdego wpisu danych jako zdarzenia niezmiennego minimalizuje konflikty rywalizacji, blokowania i współbieżności skojarzone z relacyjnymi bazami danych. Tworzenie modeli odczytu ze zmaterializowanym wzorcem widoku umożliwia oddzielenie widoku od modelu zapisu i wybranie najlepszego magazynu danych w celu optymalizacji potrzeb interfejsu użytkownika aplikacji.

Dla tego wzorca należy wziąć pod uwagę magazyn danych, który bezpośrednio obsługuje pozyskiwanie zdarzeń. Dobrymi kandydatami są usługi Azure Cosmos DB, MongoDB, Cassandra, CouchDB i RavenDB.

Podobnie jak w przypadku wszystkich wzorców i technologii, wdrażaj strategicznie i w razie potrzeby. Pozyskiwanie zdarzeń może zapewnić zwiększoną wydajność i skalowalność, ale kosztem złożoności i krzywej uczenia się.

>[!div class="step-by-step"]
>[Poprzedni](service-mesh-communication-infrastructure.md)
>[następny](relational-vs-nosql-data.md)
