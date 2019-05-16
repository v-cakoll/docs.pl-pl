---
title: Implementowanie ponownych prób z wykorzystaniem wykładniczego wycofywania
description: Dowiedz się, jak zaimplementować ponawianie próby z wykorzystaniem wykładniczego wycofywania.
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644211"
---
# <a name="implement-retries-with-exponential-backoff"></a>Implementowanie ponownych prób z wykorzystaniem wykładniczego wycofywania

[*Ponawiają próby z wykorzystaniem wykładniczego wycofywania* ](/azure/architecture/patterns/retry) to technika, która ponawia operację z wykładniczo rosnącym czas oczekiwania, aż do maksymalnej liczby ponownych prób osiągnęła ( [wykładniczego wycofywania](https://en.wikipedia.org/wiki/Exponential_backoff)). Metoda ta wykorzystuje fakt, że zasoby w chmurze może sporadycznie być niedostępne dla więcej niż kilku sekund z dowolnego powodu. Na przykład koordynatora może być przenoszenie kontenera do innego węzła w klastrze równoważenia obciążenia. W tym czasie niektórych żądań może zakończyć się niepowodzeniem. Innym przykładem może być bazy danych, takich jak Azure SQL, w których bazy danych mogą być przenoszone do innego serwera dla Równoważenie obciążenia, co powoduje bazy danych będzie dostępny przez kilka sekund.

Dostępnych jest wiele metod, aby zaimplementować logikę ponowień z wykorzystaniem wykładniczego wycofywania.

>[!div class="step-by-step"]
>[Poprzednie](partial-failure-strategies.md)
>[dalej](implement-resilient-entity-framework-core-sql-connections.md)
