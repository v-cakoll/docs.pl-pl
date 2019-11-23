---
title: Stosowanie uproszczonych wzorców CQRS i DDD w mikrousługach
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z ogólną relacją między wzorcami CQRS i DDD.
ms.date: 10/08/2018
ms.openlocfilehash: f42b553fd30fdffdc6e325b11740fe9162aab7c8
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834315"
---
# <a name="apply-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Stosowanie uproszczonych wzorców CQRS i DDD w mikrousłudze

CQRS to wzorzec architektoniczny, który oddziela modele umożliwiające odczytywanie i zapisywanie danych. Pokrewna funkcja [separacji zapytań (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) została pierwotnie zdefiniowana przez Bertrand Meyer w swojej *konstrukcji oprogramowania zorientowanego na oprogramowanie*. Podstawowy pomysł polega na tym, że operacje systemu można podzielić na dwie kategorie oddzielone od siebie:

- Wybiera. Zwracają one wynik i nie zmieniają stanu systemu i są wolne od efektów ubocznych.

- Polecenia. Zmiana stanu systemu.

CQS jest prostą koncepcją — dotyczy to metod w ramach tego samego obiektu, które są zapytania lub polecenia. Każda metoda zwraca stan lub mutację, ale nie oba. Nawet obiekt wzorca pojedynczego repozytorium może być zgodny z CQS. CQS może być traktowana jako podstawowa zasada dla CQRS.

[Command and Query Responsibility Segregation (CQRS)](https://martinfowler.com/bliki/CQRS.html) zostało wprowadzone przez Grega młodych i silnie podwyższone przez UDI Dahan i inne. Jest on oparty na zasadzie CQS, chociaż jest bardziej szczegółowy. Może być traktowany jako wzorzec oparty na poleceniach i zdarzeniach oraz opcjonalnie w komunikatach asynchronicznych. W wielu przypadkach CQRS jest związany z bardziej zaawansowanymi scenariuszami, takimi jak posiadanie innej fizycznej bazy danych do odczytu (zapytania) niż w przypadku operacji zapisu (aktualizacje). Ponadto bardziej rozwijający się system CQRS może implementować [źródła zdarzeń](https://martinfowler.com/eaaDev/EventSourcing.html) dla bazy danych aktualizacji, dzięki czemu można przechowywać tylko zdarzenia w modelu domeny zamiast przechowywać bieżące dane stanu. Nie jest to jednak podejście użyte w tym przewodniku; Stosujemy najprostszą metodę CQRS, która składa się z tylko oddzielania zapytań od poleceń.

Aspekt separacji CQRS jest osiągany przez grupowanie operacji zapytania w jednej warstwie i polecenia w innej warstwie. Każda warstwa ma własny model danych (należy pamiętać, że model, niekoniecznie inną bazę danych) i jest zbudowany przy użyciu własnej kombinacji wzorców i technologii. Co więcej, dwie warstwy mogą znajdować się w tej samej warstwie lub mikrousługach, jak w przykładzie (porządkowanie mikrousługi) używanej w tym przewodniku. Lub mogą być implementowane w różnych mikrousługach lub procesach, dzięki czemu można je zoptymalizować i skalować niezależnie bez wpływania na siebie.

CQRS oznacza, że istnieją dwa obiekty dla operacji odczytu/zapisu, gdzie w innych kontekstach. Istnieją powody, aby mieć nieznormalizowaną odczytywaną bazę danych, którą możesz poznać w bardziej zaawansowanych literaturach CQRS. Ale nie korzystamy z tego podejścia w tym miejscu, gdzie cel ma większą elastyczność w zapytaniach, zamiast ograniczać zapytania z ograniczeniami wzorców DDD, takimi jak agregaty.

Przykładem tego rodzaju usługi jest kolejność mikrousług z eShopOnContainers odwołania do aplikacji. Ta usługa implementuje mikrousługi na podstawie uproszczonego podejścia CQRS. Używa jednego źródła danych lub bazy danych, ale dwa modele logiczne Plus w przypadku domen transakcyjnych, jak pokazano na rysunku 7-2.

![Diagram przedstawiający uproszczony CQRS i DDD mikrousług.](./media/apply-simplified-microservice-cqrs-ddd-patterns/simplified-cqrs-ddd-microservice.png)

**Rysunek 7-2**. Uproszczona mikrousługa oparta na CQRS i DDD

Mikrousługa logiczna "porządkowanie" obejmuje jej bazę danych porządkowania, która może być, ale nie musi być tym samym hostem platformy Docker. Baza danych znajdująca się na tym samym hoście platformy Docker jest dobrym rozwiązaniem do programowania, ale nie dla środowiska produkcyjnego.

Warstwa aplikacji może być interfejsem API sieci Web. Ważnym aspektem projektowym jest to, że mikrousługa dzieli zapytania i modele widoków (modele danych specjalnie utworzone dla aplikacji klienckich) z poleceń, modelu domeny i transakcji po wzorcu CQRS. Takie podejście utrzymuje zapytania niezależne od ograniczeń i ograniczeń pochodzących z wzorców DDD, które mają sens tylko w przypadku transakcji i aktualizacji, jak wyjaśniono w kolejnych sekcjach.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Greg Young. Przechowywanie wersji w systemie źródła zdarzeń** (bezpłatny do odczytu online — książka elektroniczna) \
   <https://leanpub.com/esversioning/read>

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[Następny](eshoponcontainers-cqrs-ddd-microservice.md)
