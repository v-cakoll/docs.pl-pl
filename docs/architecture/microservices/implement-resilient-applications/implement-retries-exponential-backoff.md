---
title: Implementowanie ponownych prób przy wykładniczym wycofywanie
description: Dowiedz się, jak zaimplementować ponownych prób z wykładniczego wycofywania.
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296064"
---
# <a name="implement-retries-with-exponential-backoff"></a>Implementowanie ponownych prób przy wykładniczym wycofywanie

[*Ponownych prób z wykładniczego wycofywania*](/azure/architecture/patterns/retry) jest techniką, która ponawia próbę operacji, z wykładniczo zwiększenie czasu oczekiwania, do maksymalnej liczby ponownych prób została osiągnięta [(wykładnicze wycofywania).](https://en.wikipedia.org/wiki/Exponential_backoff) Ta technika obejmuje fakt, że zasoby w chmurze mogą być sporadycznie niedostępne przez więcej niż kilka sekund z jakiegokolwiek powodu. Na przykład koordynator może przenosić kontener do innego węzła w klastrze w celu równoważenia obciążenia. W tym czasie niektóre żądania mogą zakończyć się niepowodzeniem. Innym przykładem może być baza danych, takich jak SQL Azure, gdzie bazy danych można przenieść do innego serwera w celu równoważenia obciążenia, powodując bazy danych, które mają być niedostępne przez kilka sekund.

Istnieje wiele metod implementowania logiki ponownych prób z wykładniczym wycofywaniem.

>[!div class="step-by-step"]
>[Poprzedni](partial-failure-strategies.md)
>[następny](implement-resilient-entity-framework-core-sql-connections.md)
