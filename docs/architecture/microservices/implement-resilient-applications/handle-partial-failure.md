---
title: Obsługa częściowych niepowodzeń
description: Dowiedz się, jak bezpiecznie obsługiwać częściowe błędy. Mikrousługi mogą nie być w pełni funkcjonalne, ale nadal może być w stanie wykonać niektóre przydatne pracy.
ms.date: 10/16/2018
ms.openlocfilehash: f00e5349df74b543deb6ac941c751cb130b3837c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73732959"
---
# <a name="handle-partial-failure"></a>Obsługa częściowej awarii

W systemach rozproszonych, takich jak aplikacje oparte na mikrousługach, istnieje zawsze obecne ryzyko częściowej awarii. Na przykład pojedyncza mikrousługa/kontener może zakończyć się niepowodzeniem lub może nie być dostępna do udzielenia odpowiedzi przez krótki czas lub pojedyncza maszyna wirtualna lub serwer może ulec awarii. Ponieważ klienci i usługi są oddzielnymi procesami, usługa może nie być w stanie odpowiedzieć w porę na żądanie klienta. Usługa może być przeciążona i odpowiadać bardzo powoli na żądania lub po prostu może być niedostępna przez krótki czas z powodu problemów z siecią.

Rozważmy na przykład stronę Szczegóły zamówienia z przykładowej aplikacji eShopOnContainers. Jeśli mikrousługa zamawiania nie odpowiada, gdy użytkownik próbuje przesłać zamówienie, zła implementacja procesu klienta (aplikacja sieci Web MVC) — na przykład, jeśli kod klienta miałby używać synchronicznych rpc bez uchyłania czasu — blokuje wątki przez czas nieokreślony oczekiwania na odpowiedź. Oprócz tworzenia złe środowisko użytkownika, każdy nie odpowiada oczekiwania zużywa lub blokuje wątku i wątków są niezwykle cenne w aplikacjach o wysokiej skalowalnej. Jeśli istnieje wiele zablokowanych wątków, ostatecznie w czasie wykonywania aplikacji może zabraknąć wątków. W takim przypadku aplikacja może stać się globalnie nie odpowiada, a nie tylko częściowo nie odpowiada, jak pokazano na rysunku 8-1.

![Diagram przedstawiający częściowe błędy.](./media/handle-partial-failure/partial-failures-diagram.png)

**Rysunek 8-1**. Częściowe błędy z powodu zależności, które wpływają na dostępność wątku usługi

W aplikacji opartej na dużych mikrousług wszelkie częściowe awarii mogą być wzmacniane, zwłaszcza jeśli większość interakcji mikrousług wewnętrznych opiera się na synchroniczne wywołania HTTP (który jest uważany za anty-pattern). Pomyśl o systemie, który odbiera miliony połączeń przychodzących dziennie. Jeśli system ma zły projekt, który jest oparty na długich łańcuchach synchronicznych wywołań HTTP, te wywołania przychodzące mogą spowodować o wiele więcej milionów wywołań wychodzących (załóżmy, że stosunek 1:4) do dziesiątek mikrousług wewnętrznych jako synchronicznych zależności. Ta sytuacja jest pokazana na rysunku \#8-2, szczególnie zależności 3, który uruchamia łańcuch, wywołując zależność #4. #5.

![Diagram przedstawiający wiele zależności rozproszonych.](./media/handle-partial-failure/multiple-distributed-dependencies.png)

**Rysunek 8-2**. Wpływ posiadania nieprawidłowej konstrukcji z długimi łańcuchami żądań HTTP

Sporadyczne awarie są gwarantowane w systemie rozproszonym i opartym na chmurze, nawet jeśli każda zależność ma doskonałą dostępność. To fakt, który musisz wziąć pod uwagę.

Jeśli nie projektujesz i nie wdrażasz technik zapewniających odporność na uszkodzenia, nawet niewielkie przestoje mogą być wzmacniane. Na przykład 50 zależności każdy z 99.99% dostępności spowodowałoby kilka godzin przestoju każdego miesiąca z powodu tego efektu tętnienia. Gdy zależność mikrousługi nie powiedzie się podczas obsługi dużej liczby żądań, ten błąd może szybko nasycić wszystkie dostępne wątki żądania w każdej usłudze i awarii całej aplikacji.

![Diagram przedstawiający częściową awarię wzmocnioną w mikrousługach.](./media/handle-partial-failure/partial-failure-amplified-microservices.png)

**Rysunek 8-3**. Częściowa awaria wzmocniona przez mikrousługi z długimi łańcuchami synchronicznych wywołań HTTP

Aby zminimalizować ten problem, w sekcji [Asynchronous mikrousługi integracji wymusić autonomię mikrousługi,](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy)w tym przewodniku zachęca do korzystania z komunikacji asynchronicznej w mikrousługach wewnętrznych.

Ponadto istotne jest, aby zaprojektować mikrousług i aplikacji klienckich do obsługi częściowych błędów, czyli do tworzenia odpornych mikrousług i aplikacji klienckich.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](partial-failure-strategies.md)
