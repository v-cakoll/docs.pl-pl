---
title: Implementowanie ponownych prób z wykładniczego wycofywania
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie ponownych prób z wykładniczego wycofywania
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 7f909c6f81abce80bfdf118112271f1f87254793
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571426"
---
# <a name="implementing-retries-with-exponential-backoff"></a>Implementowanie ponownych prób z wykładniczego wycofywania

[*Ponowne próby z wykładniczego wycofywania* ](https://docs.microsoft.com/azure/architecture/patterns/retry) to technika, który próbuje ponowić próbę wykonania operacji, rośnie wykładniczo czas oczekiwania, aż do osiągnięcia maksymalnej liczby ponownych prób ( [wykładniczego wycofywania](https://en.wikipedia.org/wiki/Exponential_backoff) ). Ta metoda obejmuje fakt, że zasobów w chmurze mogą sporadycznie być niedostępne dla więcej niż kilka sekund różnych przyczyn. Na przykład orchestrator może być przenoszenie kontener do innego węzła w klastrze równoważenia obciążenia. W tym czasie niektórych żądań może zakończyć się niepowodzeniem. Innym przykładem może być bazy danych, takich jak Azure SQL, w których bazy danych można przenieść na inny serwer obciążenia równoważenia, co powoduje bazy danych będzie dostępny za kilka sekund.

Istnieje wiele metod wdrożyć logikę ponownych prób z wykładniczego wycofywania.


>[!div class="step-by-step"]
[Poprzednie] (częściowe — błąd strategies.md) [dalej] (implement-resilient-entity-framework-core-sql-connections.md)
