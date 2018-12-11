---
title: Implementowanie ponownych prób z wykorzystaniem wykładniczego wycofywania
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Implementowanie ponownych prób z wykorzystaniem wykładniczego wycofywania
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: e0758ee8fe28cb45ecd35ad07ddc738c12614973
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148772"
---
# <a name="implement-retries-with-exponential-backoff"></a>Implementowanie ponownych prób z wykorzystaniem wykładniczego wycofywania

[*Ponowne próby z wykorzystaniem wykładniczego wycofywania* ](https://docs.microsoft.com/azure/architecture/patterns/retry) jest techniką, która podejmuje próbę operacji z wykładniczo rosnącym czas oczekiwania, aż do osiągnięcia maksymalnej liczby ponownych prób ( [wykładniczego wycofywania](https://en.wikipedia.org/wiki/Exponential_backoff) ). Metoda ta wykorzystuje fakt, że zasoby w chmurze może sporadycznie być niedostępne dla więcej niż kilku sekund z dowolnego powodu. Na przykład koordynatora może być przenoszenie kontenera do innego węzła w klastrze równoważenia obciążenia. W tym czasie niektórych żądań może zakończyć się niepowodzeniem. Innym przykładem może być bazy danych, takich jak Azure SQL, w których bazy danych mogą być przenoszone do innego serwera dla Równoważenie obciążenia, co powoduje bazy danych będzie dostępny przez kilka sekund.

Dostępnych jest wiele metod, aby zaimplementować logikę ponowień z wykorzystaniem wykładniczego wycofywania.

>[!div class="step-by-step"]
>[Poprzednie](partial-failure-strategies.md)
>[dalej](implement-resilient-entity-framework-core-sql-connections.md)