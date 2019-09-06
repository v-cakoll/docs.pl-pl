---
title: Obsługa częściowych niepowodzeń
description: Dowiedz się, jak bezpiecznie obsługiwać częściowe błędy. Mikrousługa może nie być w pełni funkcjonalna, ale nadal może być w stanie wykonać kilka przydatnych zadań.
ms.date: 10/16/2018
ms.openlocfilehash: a667ad2e1456db7b5846023de27d3797dad58731
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296119"
---
# <a name="handle-partial-failure"></a>Błąd częściowej obsługi

W systemach rozproszonych, takich jak aplikacje oparte na mikrousługach, istnieje kiedykolwiek ryzyko częściowej awarii. Na przykład jedna mikrousługa/kontener może kończyć się niepowodzeniem lub może nie być dostępna do odpowiedzi przez krótki czas lub może ulec awarii Pojedyncza maszyna wirtualna lub serwer. Ponieważ klienci i usługi są oddzielnymi procesami, usługa może nie być w stanie odpowiedzieć na żądanie klienta w odpowiednim czasie. Usługa może być przeciążona i odpowiadać na żądania lub może po prostu nie być dostępna przez krótki czas ze względu na problemy z siecią.

Rozważmy na przykład stronę szczegóły zamówienia z przykładowej aplikacji eShopOnContainers. Jeśli mikrousługa porządkowania nie odpowiada, gdy użytkownik próbuje przesłać zamówienie, nieprawidłową implementację procesu klienta (aplikacji sieci Web MVC) — na przykład, jeśli kod klienta był używany synchronicznie zdalnych wywołań procedury bez limitu czasu — blokuje wątki w nieskończoność oczekiwanie na odpowiedź. Oprócz tworzenia nieprawidłowego środowiska użytkownika, każde nieodpowiadające na siebie oczekiwania zużywa lub blokuje wątek, a wątki są niezwykle cenne w wysoce skalowalnych aplikacjach. Jeśli istnieje wiele zablokowanych wątków, na koniec środowisko uruchomieniowe aplikacji może zostać uruchomione z wątków. W takim przypadku aplikacja może stać się globalnie nieodpowiadająca, a nie tylko częściowo nieodpowiadająca, jak pokazano na rysunku 8-1.

![Diagram przedstawiający poprzedni akapit](./media/image1.png)

**Rysunek 8-1**. Częściowe błędy spowodowane zależnościami, które wpływają na dostępność wątku usługi

W przypadku aplikacji opartych na mikrousługach można wzmocnić wszystkie częściowe awarie, zwłaszcza jeśli większość wewnętrznych interakcji mikrousług opiera się na synchronicznych wywołaniach HTTP (które są uznawane za antywzorców). Pomyśl o systemie, który odbiera miliony wywołań przychodzących dziennie. Jeśli system ma zły projekt oparty na długich łańcuchach synchronicznych wywołań HTTP, te wywołania przychodzące mogą spowodować powstanie więcej milionów wywołań wychodzących (Przypuśćmy współczynnik 1:4) do dziesiątek wewnętrznych mikrousług jako zależności synchroniczne. Ta sytuacja jest pokazana na rysunku 8-2, szczególnie \#w zależności od 3.

![Niewłaściwy projekt dla mikrousług aplikacji sieci Web, który zależy od łańcucha zależności od innych mikrousług](./media/image2.png)

**Rysunek 8-2**. Wpływ nieprawidłowego projektowania z długimi łańcuchami żądań HTTP

Przejściowy błąd jest gwarantowany w systemie rozproszonym i opartym na chmurze, nawet jeśli każda z tych zależności ma doskonałą dostępność. Jest to fakt, że należy wziąć pod uwagę.

Jeśli nie projektujesz i implementujmy techniki w celu zapewnienia odporności na uszkodzenia, to nawet małe przestoje mogą być wzmocnione. Na przykład 50 zależności z 99,99% dostępności spowodują kilka godzin przestoju każdego miesiąca z powodu tego efektu programu Ripple. Gdy zależność mikrousług kończy się niepowodzeniem podczas obsługi dużej liczby żądań, ten błąd może szybko zaszeregować wszystkie dostępne wątki żądań w poszczególnych usługach i spowodować awarię całej aplikacji.

![Częściowe błędy mogą być poważnie wzmocnione przez zależności łańcucha](./media/image3.png)

**Rysunek 8-3**. Częściowe niepowodzenie wzmacniane przez mikrousługi z długimi łańcuchami synchronicznych wywołań HTTP

Aby zminimalizować ten problem, w sekcji [asynchronicznej integracji mikrousług Wymuś autonomię mikrousługi](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy), w tym przewodniku zachęcamy do korzystania z komunikacji asynchronicznej przez mikrousługi wewnętrzne.

Ponadto istotne jest, aby zaprojektować mikrousługi i aplikacje klienckie w celu obsługi częściowych błędów — czyli do tworzenia odpornych mikrousług i aplikacji klienckich.

>[!div class="step-by-step"]
>[Poprzedni](index.md)Następny
>[](partial-failure-strategies.md)
