---
title: Rozproszone dane
description: Magazyn danych kontrastowych w aplikacjach monolitycznych i natywnych w chmurze.
author: robvet
ms.date: 04/24/2020
ms.openlocfilehash: 8a9f1478f1a46b2367df9372d4adaa3b4c711782
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82204697"
---
# <a name="distributed-data"></a>Rozproszone dane

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jak widać w tej książce, podejście natywne w chmurze zmienia sposób projektowania i wdrażania aplikacji oraz zarządzania nimi. Zmienia również sposób zarządzania i przechowywania danych.

Rysunek 5-1 kontrastuje różnice.

![Magazyn danych w aplikacjach natywnych w chmurze](./media/distributed-data.png)

**Rysunek 5-1**. Zarządzanie danymi w aplikacjach natywnych w chmurze

Doświadczeni deweloperzy mogą łatwo rozpoznać architekturę po lewej stronie rysunku 5-1. W tej *aplikacji monolitycznej*składniki usługi biznesowej współdzielą się ze sobą w warstwie usług udostępnionych, udostępniając dane z pojedynczej relacyjnej bazy danych.

W wielu przypadkach pojedyncza baza danych utrzymuje prostotę zarządzania danymi. Wykonywanie zapytań dotyczących danych w wielu tabelach jest proste. Zmiany w aktualizacjach danych lub ich wycofanie. [Transakcje kwasowe](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) gwarantują silną i natychmiastową spójność.

Projektowanie na potrzeby chmury w chmurze jest inne podejście. Zwróć uwagę na to, w jaki sposób funkcje biznesowe są segregowane w małych, niezależnych mikrousługach po prawej stronie rysunku 5-1. Każda mikrousługa hermetyzuje konkretną możliwość biznesową i własne dane. Monolityczna baza danych dekomponowa się do rozproszonego modelu danych z wieloma mniejszymi bazami danych, z których każda jest dostosowywana przy użyciu mikrousługi. Gdy dym jest wyczyszczony, zostanie nadana konstrukcja, która udostępnia *bazę danych na mikrousługi*.

## <a name="database-per-microservice-why"></a>Co to jest baza danych na mikrousługi, dlaczego?

Ta baza danych dla mikrousług zapewnia wiele korzyści, szczególnie w przypadku systemów, które muszą szybko rozwijać i obsługiwać ogromną skalę. Z tym modelem...

- Dane domeny są hermetyzowane w ramach usługi
- Schemat danych może się rozwijać bez bezpośredniego wpływu na inne usługi
- Każdy magazyn danych może być niezależnie skalowany
- Awaria magazynu danych w jednej usłudze nie wpłynie bezpośrednio na inne usługi

Rozdzielenie danych umożliwia również każdej mikrousługi implementację typu magazynu danych, który najlepiej jest zoptymalizowany pod kątem obciążenia, potrzeby magazynowania oraz wzorców odczytu i zapisu. Dostępne opcje to relacyjny, dokument, klucz-wartość, a nawet magazyn danych oparty na grafie.

Rysunek 5-2 przedstawia zasadę trwałości Polyglot w systemie macierzystym w chmurze.

![Trwałość danych Polyglot](./media/polyglot-data-persistence.png)

**Rysunek 5-2**. Trwałość danych Polyglot

Zwróć uwagę na poprzednie ilustracje, w jaki sposób poszczególne mikrousługi obsługują inny typ magazynu danych.

- Mikrousługa katalogu produktów korzysta z relacyjnej bazy danych, aby pomieścić rozbudowaną strukturę relacyjną danych źródłowych.
- Mikrousługa koszyka zakupów używa rozproszonej pamięci podręcznej, która obsługuje prosty magazyn danych o kluczowym poziomie.
- Mikrousługa porządkowania wykorzystuje bazę danych dokumentów NoSql dla operacji zapisu oraz wysoce nieznormalizowany magazyn klucz/wartość, aby uwzględnić duże ilości operacji odczytu.
  
Relacyjne bazy danych pozostają istotne dla mikrousług z danymi złożonymi, jednak bazy danych NoSQL uzyskały znaczną popularność. Zapewniają one ogromne skalowanie i wysoką dostępność. Ich charakter bez schematu pozwala deweloperom poruszać się od architektury klas danych z określonym typem i ORMs, co sprawia, że zmiany są kosztowne i czasochłonne. Obejmujemy bazy danych NoSQL w dalszej części tego rozdziału.

 Podczas hermetyzowania danych do oddzielnych mikrousług można zwiększyć elastyczność, wydajność i skalowalność, a także wiele wyzwań. W następnej sekcji omawiamy te wyzwania, a także wzorce i praktyki, które pomogą im je przezwyciężyć.  

## <a name="cross-service-queries"></a>Zapytania międzyusługowe

Chociaż mikrousługi są niezależne i skupiają się na określonych możliwościach funkcjonalnych, takich jak spis, wysyłka lub porządkowanie, często wymagają integracji z innymi mikrousługami. Często integracja obejmuje jednokrotne *wykonywanie zapytań* dotyczących danych. Na rysunku 5-3 przedstawiono scenariusz.

![Wykonywanie zapytań na mikrousługach](./media/cross-service-query.png)

**Rysunek 5-3**. Wykonywanie zapytań na mikrousługach

Na powyższym rysunku zostanie wyświetlona mikrousługa koszyka zakupów, która dodaje element do koszyka zakupów użytkownika. Chociaż magazyn danych dla tej mikrousługi zawiera dane dotyczące koszyka i wiersza, nie zachowuje danych o produkcie ani cenniku. Zamiast tego te elementy danych należą do wykazu i mikrousług cenowych. Spowoduje to problem. Jak mikrousługa koszyka zakupów dodaje produkt do koszyka zakupów użytkownika, gdy nie zawiera on produktu ani cennika w swojej bazie danych?

Jedną z opcji omówioną w rozdziale 4 jest [bezpośrednie wywołanie protokołu HTTP](service-to-service-communication.md#queries) z koszyka zakupów do wykazu i mikrousług cenowych. Jednakże w rozdziale 4 firma Microsoft poinformowała o synchronicznych *wywołaniach* http, które dzielą się wspólnie, zmniejszając ich autonomię i ograniczając zalety architektury.

Możemy również zaimplementować wzorzec żądanie-odpowiedź z oddzielnymi kolejkami ruchu przychodzącego i wychodzącego dla każdej usługi. Jednak ten wzorzec jest skomplikowany i wymaga instalacji wodociągowej do skorelowania komunikatów żądań i odpowiedzi.
Podczas oddzielania wywołań mikrousług zaplecza usługa wywołująca musi nadal przeprowadzić synchroniczną oczekiwanie na zakończenie wywołania. Przeciążenie sieci, awarie przejściowe lub przeciążona mikrousługa, co może skutkować długotrwałymi operacjami i nawet niepowodzeniem.

Zamiast tego powszechnie akceptowany wzorzec do usuwania zależności między usługami jest [wzorcem widoku materiałowego](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)pokazanym na rysunku 5-4.

![Wzorzec widoku materiałowego](./media/materialized-view-pattern.png)

**Rysunek 5-4**. Wzorzec widoku materiałowego

Przy użyciu tego wzorca należy umieścić lokalną tabelę danych (nazywaną *modelem odczytu*) w usłudze koszyka zakupów. Ta tabela zawiera nieznormalizowaną kopię danych wymaganych z mikrousług produktu i cen. Kopiowanie danych bezpośrednio do usługi koszyka zakupów eliminuje konieczność kosztownych połączeń między usługami. W przypadku danych lokalnych usługi można poprawić czas odpowiedzi i niezawodność usługi. Ponadto posiadanie własnej kopii danych powoduje, że usługa koszyka zakupów bardziej odporna na błędy. Jeśli usługa wykazu powinna stać się niedostępna, nie wpłynie ona bezpośrednio na usługę koszyka zakupów. Koszyk może nadal działać z danymi ze swojego własnego magazynu.

Catch z tym podejściem polega na tym, że masz teraz duplikaty danych w systemie. Jednak *strategicznie* duplikowanie danych w systemach natywnych w chmurze jest ustanowioną zasadą i nie jest uznawane za antywzorców lub złe rozwiązanie. Należy pamiętać, że *jedna i tylko jedna usługa* może być własnością zestawu danych i mieć przez niego uprawnienia. Podczas aktualizowania systemu rekordów należy synchronizować modele odczytywania. Synchronizacja jest zwykle implementowana za pośrednictwem asynchronicznej obsługi komunikatów ze [wzorcem publikowania/subskrybowania](service-to-service-communication.md#events), jak pokazano na rysunku 5,4.

## <a name="distributed-transactions"></a>Transakcje rozproszone

Podczas wykonywania zapytań dotyczących danych w mikrousługach jest trudne, implementacja transakcji na kilku mikrousług jest jeszcze bardziej skomplikowana. Niezależne wyzwanie związane z konserwacją spójności danych w przypadku różnych mikrousług nie mogą być niezgodne. Brak transakcji rozproszonych w aplikacjach natywnych w chmurze oznacza, że konieczne jest programowe zarządzanie transakcjami rozproszonymi. Przenosisz ze świata *natychmiastowej spójności* do tej *spójności ostatecznej*.

Rysunek 5-5 pokazuje problem.

![Transakcja w wzorcu Saga](./media/saga-transaction-operation.png)

**Rysunek 5-5**. Implementowanie transakcji w mikrousługach

Na powyższym rysunku pięć niezależnych mikrousług uczestniczy w transakcji rozproszonej, która tworzy zamówienie. Każda mikrousługa utrzymuje własny magazyn danych i implementuje lokalną transakcję dla swojego magazynu. Aby można było utworzyć zamówienie, lokalna transakcja dla *każdej* z mikrousług musi się powieść lub *wszystkie* muszą zostać przerwane i wycofane. Wbudowana obsługa transakcyjna jest dostępna w ramach poszczególnych mikrousług, ale nie jest obsługiwana transakcja rozproszona obejmująca wszystkie pięć usług w celu zachowania spójności danych.

Zamiast tego należy skonstruować tę transakcję rozproszoną *programowo*.

Popularnym wzorcem dodawania rozproszonej obsługi transakcyjnej jest wzorzec Saga. Jest to implementowane przez grupowanie transakcji lokalnych razem programowo i sekwencyjnie wywoływanie każdego z nich. Jeśli dowolna transakcja lokalna zakończy się niepowodzeniem, Saga przerywa operację i wywołuje zestaw [kompensowania transakcji](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction). Kompensowanie transakcji cofa zmiany dokonane przez poprzednie transakcje lokalne i przywraca spójność danych. Rysunek 5-6 pokazuje nieudaną transakcję ze wzorcem Saga.

![Wycofywanie w wzorcu Saga](./media/saga-rollback-operation.png)

**Rysunek 5-6**. Wycofywanie transakcji

Na powyższym rysunku operacja *aktualizacji spisu* nie powiodła się w Mikrousłudze spisu. Saga wywołuje zbiór transakcji kompensacyjnych (czerwony), aby dostosować liczbę spisów, anulować płatność i zamówienie i zwrócić dane dla każdej mikrousługi z powrotem do spójnego stanu.

Wzorce Saga są zwykle choreographed jako serie powiązanych zdarzeń lub zorganizowane jako zestaw powiązanych poleceń. W rozdziale 4 opisano wzorzec agregatora usług, który byłby podstawą dla zorganizowanej implementacji Saga. Omawiamy również zdarzenia dotyczące Azure Service Bus i Azure Event Grid tematów, które byłyby podstawą dla implementacji choreographed Saga.

## <a name="high-volume-data"></a>Duże ilości danych

Duże aplikacje natywne w chmurze często obsługują wymagania dotyczące dużej ilości danych. W tych scenariuszach tradycyjne techniki magazynowania danych mogą spowodować wąskie gardła. W przypadku złożonych systemów, które wdrażają w dużej skali, zarówno Command and Query Responsibility Segregation (CQRS), jak i źródła zdarzeń mogą zwiększyć wydajność aplikacji.  

### <a name="cqrs"></a>CQRS

[CQRS](https://docs.microsoft.com/azure/architecture/patterns/cqrs), to wzorzec architektoniczny, który może pomóc zmaksymalizować wydajność, skalowalność i bezpieczeństwo. Wzorzec oddziela operacje odczytujące dane z tych operacji, które zapisują dane.

W normalnych *scenariuszach do operacji odczytu i* zapisu są używane te same obiekty modelu jednostki i repozytorium danych.

Jednak scenariusz dużej ilości danych może korzystać z oddzielnych modeli i tabel danych do odczytu i zapisu. Aby zwiększyć wydajność, operacja odczytu może badać wysoce nieznormalizowaną reprezentację danych, aby uniknąć kosztownych sprzężeń między tabelami i blokad tabeli. Operacja *zapisu* , znana jako *polecenie*, będzie aktualizowana względem w pełni znormalizowanej reprezentacji danych, które gwarantują spójność. Następnie należy zaimplementować mechanizm, aby zachować obie reprezentacje w synchronizacji. Zazwyczaj zawsze, gdy tabela zapis jest modyfikowana, publikuje zdarzenie, które replikuje modyfikację tabeli Odczytaj.

Na rysunku 5-7 przedstawiono implementację wzorca CQRS.

![Command and Query Responsibility Segregation](./media/cqrs-implementation.png)

**Rysunek 5-7**. Implementacja CQRS

Na poprzednim rysunku zaimplementowane są osobne modele poleceń i zapytań. Każda operacja zapisu danych jest zapisywana w magazynie zapisu, a następnie propagowana do magazynu odczytu. Zwróć szczególną uwagę na to, jak proces propagacji danych działa na zasadzie [spójności ostatecznej](http://www.cloudcomputingpatterns.org/eventual_consistency/). Model odczytu ostatecznie synchronizuje się z modelem zapisu, ale może wystąpić pewne opóźnienie w procesie. Omawiana jest spójność ostateczna w następnej sekcji.

To Separacja umożliwia niezależne skalowanie odczytów i zapisów. Operacje odczytu używają schematu zoptymalizowanego pod kątem zapytań, podczas gdy zapisy używają schematu zoptymalizowanego pod kątem aktualizacji. Zapytania odczytu przechodzą na nieznormalizowane dane, podczas gdy złożona logika biznesowa może być stosowana do modelu zapisu. Ponadto można nałożyć ściślejsze zabezpieczenia na operacje zapisu niż te, które uwidaczniają odczyty.

Wdrożenie CQRS może zwiększyć wydajność aplikacji dla usług natywnych w chmurze. Jednak powoduje to bardziej skomplikowany projekt. Zastosuj tę zasadę starannie i strategicznie do tych sekcji aplikacji natywnej w chmurze, która będzie z niej korzystać. Aby uzyskać więcej informacji na temat CQRS, zobacz temat [Usługa .NET dla usługi Microsoft Books: architektura dla kontenerów aplikacji .NET](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/apply-simplified-microservice-cqrs-ddd-patterns).

### <a name="event-sourcing"></a>Określanie źródła zdarzeń

Innym podejściem do optymalizowania scenariuszy danych o wysokiej ilości obejmuje Określanie [źródła zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

System zazwyczaj zapisuje bieżący stan jednostki danych. Jeśli użytkownik zmieni swój numer telefonu, na przykład rekord klienta zostanie zaktualizowany przy użyciu nowej liczby. Zawsze wiemy bieżący stan jednostki danych, ale każda aktualizacja zastępuje poprzedni stan.

W większości przypadków ten model działa prawidłowo. Jednak w systemach o dużych ilościach koszty związane z blokowaniem transakcyjnym i częste operacje aktualizacji mogą mieć wpływ na wydajność bazy danych, czas odpowiedzi i ograniczanie skalowalności.

Źródłem zdarzeń jest inne podejście do przechwytywania danych. Każda operacja wpływająca na dane jest utrwalana w magazynie zdarzeń. Zamiast aktualizować stan rekordu danych, dołączamy każdą zmianę do sekwencyjnej listy przeszłych wydarzeń — podobnie jak w przypadku księgi rachunkowej. Magazyn zdarzeń jest systemem rejestrowania danych. Służy do propagowania różnorodnych widoków w ramach ograniczonego kontekstu mikrousługi. Rysunek 5,8 pokazuje wzorzec.

![Określanie źródła zdarzeń](./media/event-sourcing.png)

**Rysunek 5-8**. Określanie źródła zdarzeń

Na poprzedniej ilustracji należy zwrócić uwagę na to, jak każdy wpis (niebieski) dla koszyka zakupów użytkownika jest dołączany do podstawowego magazynu zdarzeń. W sąsiednim widoku, system projektuje bieżący stan przez odtwarzanie wszystkich zdarzeń skojarzonych z każdym koszykiem. Ten widok lub model odczytywania jest następnie ujawniany z powrotem do interfejsu użytkownika. Zdarzenia mogą być również zintegrowane z systemami zewnętrznymi i aplikacjami lub z kwerendą w celu określenia bieżącego stanu jednostki. W tym podejściu należy zachować historię. Wiadomo, że nie jest tylko bieżący stan jednostki, ale również został osiągnięty ten stan.

W sposób mechaniczny, źródłem zdarzeń jest uproszczenie modelu zapisu. Brak aktualizacji lub usunięć. Dołączanie każdego wpisu danych jako niezmienne zdarzenie minimalizuje rywalizację, blokowanie i konflikty współbieżności związane z relacyjnymi bazami danych. Kompilowanie modeli odczytu z wzorcem widoku materiałowego umożliwia oddzielenie widoku od modelu zapisu i wybranie najlepszego magazynu danych w celu zoptymalizowania potrzeb interfejsu użytkownika aplikacji.

Dla tego wzorca należy wziąć pod uwagę magazyn danych, który bezpośrednio obsługuje określanie źródła zdarzeń. Azure Cosmos DB, MongoDB, Cassandra, CouchDB i RavenDB są dobrymi kandydatami.

Podobnie jak w przypadku wszystkich wzorców i technologii, należy zaimplementować strategiczne i w razie konieczności. Chociaż źródłem zdarzeń może być zwiększona wydajność i skalowalność, zapewnia ona koszt złożoności i krzywą szkoleniową.

>[!div class="step-by-step"]
>[Poprzedni](service-mesh-communication-infrastructure.md)
>[Następny](relational-vs-nosql-data.md)
