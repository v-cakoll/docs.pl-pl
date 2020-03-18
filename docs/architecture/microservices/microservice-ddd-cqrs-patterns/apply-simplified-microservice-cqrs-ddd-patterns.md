---
title: Stosowanie uproszczonych wzorców CQRS i DDD w mikrousługach
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zrozumienie ogólnej relacji między wzorcami CQRS i DDD.
ms.date: 10/08/2018
ms.openlocfilehash: f42b553fd30fdffdc6e325b11740fe9162aab7c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834315"
---
# <a name="apply-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Stosowanie uproszczonych wzorców CQRS i DDD w mikrousługach

CQRS jest wzorcem architektury, który oddziela modele do odczytu i zapisu danych. Powiązany termin [Command Query Separation (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) został pierwotnie zdefiniowany przez Bertranda Meyera w jego książce *Object Oriented Software Construction*. Podstawową ideą jest to, że można podzielić operacje systemu na dwie ostro oddzielone kategorie:

- Kwerendy. Te zwracają wynik i nie zmieniają stanu systemu i są wolne od skutków ubocznych.

- Polecenia. Zmieniają one stan systemu.

CQS jest prosta koncepcja — chodzi o metody w tym samym obiekcie są zapytania lub polecenia. Każda metoda zwraca stan lub mutuje stan, ale nie oba. Nawet pojedynczy obiekt wzorca repozytorium może być zgodny z CQS. CQS można uznać za podstawową zasadę Dla CQRS.

[Command and Query Responsibility Segregation (CQRS)](https://martinfowler.com/bliki/CQRS.html) został wprowadzony przez Grega Younga i silnie promowany przez Udi Dahana i innych. Opiera się na zasadzie CQS, chociaż jest bardziej szczegółowy. Można go uznać za wzorzec na podstawie poleceń i zdarzeń oraz opcjonalnie na komunikatach asynchronicznych. W wielu przypadkach CQRS jest związane z bardziej zaawansowanych scenariuszy, takich jak posiadanie innej fizycznej bazy danych dla odczytów (kwerendy) niż dla zapisów (aktualizacje). Ponadto bardziej rozwinięty system CQRS może implementować [eventsourcing (ES)](https://martinfowler.com/eaaDev/EventSourcing.html) dla bazy danych aktualizacji, więc można przechowywać tylko zdarzenia w modelu domeny zamiast przechowywania danych o bieżącym stanie. Nie jest to jednak podejście zastosowane w tym przewodniku; używamy najprostszego podejścia CQRS, który polega tylko oddzielenie zapytań od poleceń.

Aspekt separacji CQRS jest osiągany przez grupowanie operacji kwerendy w jednej warstwie i poleceń w innej warstwie. Każda warstwa ma swój własny model danych (należy pamiętać, że mówimy modelu, niekoniecznie innej bazy danych) i jest zbudowany przy użyciu własnej kombinacji wzorców i technologii. Co ważniejsze dwie warstwy mogą znajdować się w tej samej warstwie lub mikrousługi, jak w przykładzie (mikrousługi zamawiania) używane dla tego przewodnika. Lub mogą być implementowane na różnych mikrousług lub procesów, dzięki czemu mogą być zoptymalizowane i skalowane w sposób oddzielnie bez wpływu na siebie nawzajem.

CQRS oznacza posiadanie dwóch obiektów dla operacji odczytu/zapisu, gdzie w innych kontekstach istnieje jeden. Istnieją powody, aby mieć nieznormalizowane odczyty bazy danych, które można dowiedzieć się o w bardziej zaawansowanej literaturze CQRS. Ale nie używamy tego podejścia w tym miejscu, gdzie celem jest mieć większą elastyczność w zapytaniach zamiast ograniczania zapytań z ograniczeniami z wzorców DDD, takich jak agregaty.

Przykładem tego rodzaju usługi jest mikrousługi zamawiania z aplikacji referencyjnej eShopOnContainers. Ta usługa implementuje mikrousługi na podstawie uproszczonego podejścia CQRS. Używa jednego źródła danych lub bazy danych, ale dwa modele logiczne oraz wzorce DDD dla domeny transakcyjnej, jak pokazano na rysunku 7-2.

![Diagram przedstawiający wysoki poziom uproszczonego CQRS i mikrousługi DDD.](./media/apply-simplified-microservice-cqrs-ddd-patterns/simplified-cqrs-ddd-microservice.png)

**Rysunek 7-2**. Uproszczona mikrousługa oparta na CQRS i DDD

Logiczne "Zamawianie" Microservice zawiera jego uporządkowanie bazy danych, które mogą być, ale nie musi być, ten sam host platformy Docker. Posiadanie bazy danych w tym samym hoście platformy Docker jest dobre dla rozwoju, ale nie dla produkcji.

Warstwą aplikacji może być sam interfejs API sieci Web. Ważnym aspektem projektu w tym miejscu jest to, że mikrousługa podzieliła zapytania i ViewModels (modele danych utworzone specjalnie dla aplikacji klienckich) z poleceń, modelu domeny i transakcji zgodnie z wzorcem CQRS. Takie podejście utrzymuje zapytania niezależne od ograniczeń i ograniczeń pochodzących z wzorców DDD, które mają sens tylko dla transakcji i aktualizacji, jak wyjaśniono w późniejszych sekcjach.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Grzegorz Young. Przechowywanie wersji w systemie pochodzącym z eventu** (bezpłatnie czytać e-bookonline) \
   <https://leanpub.com/esversioning/read>

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](eshoponcontainers-cqrs-ddd-microservice.md)
