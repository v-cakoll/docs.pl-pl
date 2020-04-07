---
title: Stosowanie uproszczonych wzorców CQRS i DDD w mikrousługach
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Zrozumienie ogólnej relacji między wzorcami CQRS i DDD.
ms.date: 10/08/2018
ms.openlocfilehash: e4e36bafff39f5f30d6371ed7c113322a85c3362
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805593"
---
# <a name="apply-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Stosowanie uproszczonych wzorców CQRS i DDD w mikrousługach

CQRS jest wzorcem architektury, który oddziela modele do odczytu i zapisu danych. Powiązany termin [Command Query Separation (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) został pierwotnie zdefiniowany przez Bertranda Meyera w swojej książce *Object Oriented Software Construction*. Podstawową ideą jest to, że można podzielić operacje systemu na dwie kategorie ostro oddzielone:

- Kwerendy. Te zwracają wynik i nie zmieniają stanu systemu, i są wolne od skutków ubocznych.

- Polecenia. Zmieniają one stan systemu.

CQS jest prosta koncepcja: chodzi o metody w tym samym obiekcie są kwerendy lub polecenia. Każda metoda zwraca stan lub mutuje stan, ale nie oba. Nawet pojedynczy obiekt wzorca repozytorium może być zgodny z CQS. CQS można uznać za podstawową zasadę dla CQRS.

[Command and Query Responsibility Segregation (CQRS)](https://martinfowler.com/bliki/CQRS.html) został wprowadzony przez Grega Younga i silnie promowany przez Udi Dahan i innych. Opiera się na zasadzie CQS, chociaż jest bardziej szczegółowa. Można uznać wzorzec na podstawie poleceń i zdarzeń oraz opcjonalnie na komunikaty asynchroniczne. W wielu przypadkach CQRS jest związane z bardziej zaawansowanych scenariuszy, takich jak o innej fizycznej bazy danych dla odczytów (kwerend) niż dla zapisów (aktualizacje). Ponadto bardziej rozwinięty system CQRS może implementować [usługi event-sourcing (ES)](https://martinfowler.com/eaaDev/EventSourcing.html) dla bazy danych aktualizacji, więc zdarzenia będą przechowywane tylko w modelu domeny zamiast przechowywania bieżących danych o stanie. Jednak to podejście nie jest używane w tym przewodniku. W tym przewodniku użyto najprostszego podejścia CQRS, które polega tylko na oddzieleniu zapytań od poleceń.

Aspekt separacji CQRS jest osiągany przez grupowanie operacji kwerendy w jednej warstwie i poleceń w innej warstwie. Każda warstwa ma swój własny model danych (należy pamiętać, że mówimy modelu, niekoniecznie innej bazy danych) i jest zbudowany przy użyciu własnej kombinacji wzorców i technologii. Co ważniejsze, dwie warstwy mogą znajdować się w tej samej warstwie lub mikrousługach, jak w przykładzie (zamawianie mikrousług) używane dla tego przewodnika. Lub mogą być implementowane na różnych mikrousług lub procesów, dzięki czemu mogą być optymalizowane i skalowane w poziomie oddzielnie bez wpływu na siebie nawzajem.

CQRS oznacza posiadanie dwóch obiektów dla operacji odczytu/zapisu, gdzie w innych kontekstach istnieje jeden. Istnieją powody, aby mieć zdenormalizowane odczyty bazy danych, które można dowiedzieć się o bardziej zaawansowanej literatury CQRS. Ale nie używamy tego podejścia w tym miejscu, gdzie celem jest mieć większą elastyczność w kwerendach zamiast ograniczania zapytań z ograniczeniami z wzorców DDD, takich jak agregacje.

Przykładem tego rodzaju usługi jest zamawiania mikrousługi z aplikacji referencyjnej eShopOnContainers. Ta usługa implementuje mikrousługi na podstawie uproszczonego podejścia CQRS. Używa jednego źródła danych lub bazy danych, ale dwa modele logiczne plus wzorce DDD dla domeny transakcyjnej, jak pokazano na rysunku 7-2.

![Diagram przedstawiający mikrousługi uproszczone CQRS i DDD na wysokim poziomie.](./media/apply-simplified-microservice-cqrs-ddd-patterns/simplified-cqrs-ddd-microservice.png)

**Rysunek 7-2**. Uproszczona mikrousługa oparta na CQRS i DDD

Logiczne "Zamawianie" Mikrousługa zawiera jego zamawiania bazy danych, które mogą być, ale nie musi być, tego samego hosta platformy Docker. Posiadanie bazy danych w tym samym hoście platformy Docker jest dobre dla rozwoju, ale nie dla produkcji.

Warstwą aplikacji może być sam internetowy interfejs API. Ważnym aspektem projektu w tym miejscu jest, że mikrousługa ma podzielić zapytania i ViewModels (modele danych specjalnie utworzone dla aplikacji klienckich) z poleceń, modelu domeny i transakcji po wzorzec CQRS. Takie podejście utrzymuje zapytania niezależne od ograniczeń i ograniczeń pochodzących z wzorców DDD, które mają sens tylko dla transakcji i aktualizacji, jak wyjaśniono w późniejszych sekcjach.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Greg Young. Przechowywanie wersji w systemie event sourced** (free to read online e-book) \
   <https://leanpub.com/esversioning/read>

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](eshoponcontainers-cqrs-ddd-microservice.md)
