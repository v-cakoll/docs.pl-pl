---
title: Obsługa częściowych niepowodzeń
description: Dowiedz się, jak bezpiecznie obsługiwać częściowe awarie. Mikrousługi może nie być w pełni funkcjonalny, ale nadal może być w stanie wykonać kilka przydatnych prac.
ms.date: 10/16/2018
ms.openlocfilehash: 0300719360e1a2500db0af8454c91fdfe2e5b09b
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988873"
---
# <a name="handle-partial-failure"></a>Obsługa częściowego błędu

W systemach rozproszonych, takich jak aplikacje oparte na mikrousługach, istnieje zawsze obecne ryzyko częściowej awarii. Na przykład pojedyncza mikrousługa/kontener może zakończyć się niepowodzeniem lub może nie być dostępna do odpowiadania przez krótki czas lub jedna maszyna wirtualna lub serwer może ulec awarii. Ponieważ klienci i usługi są oddzielne procesy, usługa może nie być w stanie odpowiedzieć w odpowiednim czasie na żądanie klienta. Usługa może być przeciążona i odpowiadać bardzo powoli na żądania lub może po prostu nie być dostępna przez krótki czas z powodu problemów z siecią.

Rozważmy na przykład stronę Szczegóły zamówienia z przykładowej aplikacji eShopOnContainers. Jeśli mikrousługa zamawiania nie odpowiada, gdy użytkownik próbuje przesłać zamówienie, nieprawidłowa implementacja procesu klienta (aplikacji sieci web MVC) — na przykład, jeśli kod klienta miał używać synchronicznych kontrolerów RPC bez limitu czasu — blokuje wątki przez czas nieokreślony oczekujących na odpowiedź. Oprócz tworzenia złe środowisko użytkownika, każdy nie odpowiada czekać zużywa lub blokuje wątku i wątki są niezwykle cenne w wysoce skalowalnych aplikacji. Jeśli istnieje wiele zablokowanych wątków, po pewnym czasie wykonywania aplikacji może zabraknąć wątków. W takim przypadku aplikacja może stać się globalnie nie odpowiada, a nie tylko częściowo nie odpowiada, jak pokazano na rysunku 8-1.

![Diagram przedstawiający częściowe awarie.](./media/handle-partial-failure/partial-failures-diagram.png)

**Rysunek 8-1**. Częściowe awarie z powodu zależności, które wpływają na dostępność wątku usługi

W aplikacji opartej na dużych mikrousług można wzmocnić wszelkie częściowe awarie, zwłaszcza jeśli większość interakcji mikrousług wewnętrznych jest oparta na synchronicznego wywołania HTTP (który jest uważany za wzorzec antywłaściwczy). Pomyśl o systemie, który odbiera miliony połączeń przychodzących dziennie. Jeśli system ma zły projekt, który jest oparty na długich łańcuchach synchronicznych wywołań HTTP, te wywołania przychodzące może spowodować wiele więcej milionów połączeń wychodzących (załóżmy, że stosunek 1:4) do dziesiątek wewnętrznych mikrousług jako synchroniczne zależności. Ta sytuacja jest pokazana na rysunku 8-2, zwłaszcza zależności \#3, który uruchamia łańcuch, wywołując zależność #4. które #5.

![Diagram przedstawiający wiele zależności rozproszonych.](./media/handle-partial-failure/multiple-distributed-dependencies.png)

**Rysunek 8-2**. Wpływ nieprawidłowego projektu zawierającego długie łańcuchy żądań HTTP

Sporadyczne awarie są gwarantowane w systemie rozproszonym i opartym na chmurze, nawet jeśli każda zależność ma doskonałą dostępność. To fakt, który musisz wziąć pod uwagę.

Jeśli nie zaprojektujesz i nie wdrożysz technik zapewniających odporność na uszkodzenia, nawet małe przestoje mogą zostać wzmocnione. Na przykład 50 zależności każdy z 99,99% dostępności spowodowałoby kilka godzin przestojów każdego miesiąca z powodu tego efektu tętnienia. Gdy zależność mikrousługi ulegnie awarii podczas obsługi dużej liczby żądań, ten błąd może szybko nasycić wszystkie dostępne wątki żądań w każdej usłudze i upaść całą aplikację.

![Diagram przedstawiający częściowe awarii wzmocnione w mikrousługach.](./media/handle-partial-failure/partial-failure-amplified-microservices.png)

**Rysunek 8-3**. Częściowa awaria wzmacniana przez mikrousługi z długimi łańcuchami synchroniczne wywołań HTTP

Aby zminimalizować ten problem, w sekcji [Integracja mikrousług asynchronicznych wymusza autonomię mikrousług,](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy)w tym przewodniku zachęca do korzystania z komunikacji asynchronicznej w mikrousługach wewnętrznych.

Ponadto ważne jest, aby zaprojektować mikrousług i aplikacji klienckich do obsługi częściowych awarii, czyli do tworzenia odpornych mikrousług i aplikacji klienckich.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](partial-failure-strategies.md)
