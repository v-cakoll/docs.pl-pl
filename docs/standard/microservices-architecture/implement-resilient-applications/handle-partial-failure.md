---
title: Obsługa częściowej awarii
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Obsługa częściowej awarii
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 26e3d6b4cd1df051c00cef4ee8370ca9c213363e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="handling-partial-failure"></a>Obsługa częściowej awarii

W systemach rozproszonych, takich jak aplikacje oparte na mikrousług istnieje ryzyko wszechobecne częściowej awarii. Na przykład jeden mikrousługi/kontener może zakończyć się niepowodzeniem lub mogą nie być dostępne do odpowiedzi przez krótki czas lub jednego serwera lub maszyny Wirtualnej może ulec awarii. Od klientów i usług są osobne procesy, usługi może nie być w stanie odpowiedzieć w odpowiednim momencie na żądanie klienta. Usługa może być przeciążona i odpowiada bardzo wolno do żądania lub po prostu nie mogą być niedostępne przez krótki czas z powodu problemów dotyczących sieci.

Na przykład należy wziąć pod uwagę strony szczegółów w kolejności od eShopOnContainers przykładowej aplikacji. Jeśli mikrousługi porządkowania nie odpowiada gdy użytkownik próbuje przesłać zamówienie, złą implementacją klasy procesu klienta (aplikacja sieci web MVC) — na przykład, jeśli kod klienta synchroniczne RPC za pomocą limitu czasu — umożliwia zablokowanie wątków nieskończoność Oczekiwanie na odpowiedź. Oprócz tworzenia płynność pracy, co nie odpowiada oczekiwania zużywa lub blokuje wątku i wątki są bardzo przydatne w aplikacjach wysokiej skalowalności. W przypadku wielu zablokowanych wątków po pewnym czasie poza wątków można uruchomić aplikacji w czasie wykonywania. W takim przypadku aplikacja może stać się globalny nie odpowiada, a nie tylko częściowo odpowiadać jako Pokaż w rysunek 10-1.

![](./media/image1.png)

**Rysunek 10-1**. Częściowe błędy z powodu zależności, które mają wpływ na dostępność wątku usługi

W dużych aplikacji na podstawie mikrousług jakiekolwiek niepowodzenie częściowe mogą jest rozszerzona, zwłaszcza, jeśli większość interakcji wewnętrzny mikrousług opiera się na synchroniczne wywołania HTTP (które uważa się przed wzorzec). Zastanów się systemu, który odbiera miliony przychodzące wywołania dziennie. Jeśli system ma zły projekt, który jest oparty na długie łańcuchy synchroniczne wywołania HTTP, te połączenia przychodzące może skutkować milionów więcej połączeń wychodzących (Załóżmy, że stosunek 1:4) dziesiątki wewnętrzny mikrousług jako synchroniczne zależności. Taka sytuacja jest wyświetlany w rysunek 10-2, szczególnie zależności \#3.

![](./media/image2.png)

**Rysunek 10-2**. Wpływ projektu niepoprawne o długie łańcuchy żądań HTTP

Sporadyczne niepowodzenia jest praktycznie gwarantowana w rozproszonej i w chmurze oparte na systemie, nawet jeśli doskonałej dostępności ma zależności, co się. Powinno to być faktów, które należy wziąć pod uwagę.

Jeśli nie projektowania i implementacji technik w celu zapewnienia odporności na uszkodzenia, można rozszerzone nawet małe awariami. Na przykład 50 zależności dostępności 99,99% spowoduje kilka godzin przestoju miesięcznie ze względu na to wpływ. Jeśli zależność mikrousługi nie powiodło się podczas obsługi dużej liczby żądań, błędu można szybko saturate — wszystkie wątki żądania dostępne w poszczególnych usług i awarii całej aplikacji.

![](./media/image3.png)

**Rysunek 10-3**. Częściowe niepowodzenie rozszerzone o mikrousług o długie łańcuchy synchroniczne wywołania HTTP

Aby zminimalizować ten problem, w sekcji "*integracji asynchroniczne mikrousługi wymusić Autonomia w mikrousługi*" (w tym rozdziale architektury), firma Microsoft zaleca użycia komunikacji asynchronicznej między wewnętrznego mikrousług. Firma Microsoft krótko opisano bardziej w następnej sekcji.

Ponadto ważne zaprojektowanie klienta i mikrousług aplikacji do obsługi błędów z częściowa jest — oznacza to, że tworzenie mikrousług odporne i klienta aplikacji.


>[!div class="step-by-step"]
[Poprzednie] (index.md) [dalej] (częściowe — błąd strategies.md)
