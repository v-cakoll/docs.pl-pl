---
title: "Implementowanie ponownych prób z wykładniczego wycofywania"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie ponownych prób z wykładniczego wycofywania"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7ed97b750d6e3f2aa5def72e90e070a49a7c0e63
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-retries-with-exponential-backoff"></a>Implementowanie ponownych prób z wykładniczego wycofywania

[*Ponowne próby z wykładniczego wycofywania* ](https://docs.microsoft.com/azure/architecture/patterns/retry) to technika, który próbuje ponowić próbę wykonania operacji, rośnie wykładniczo czas oczekiwania, aż do osiągnięcia maksymalnej liczby ponownych prób ( [wykładniczego wycofywania](https://en.wikipedia.org/wiki/Exponential_backoff)). Ta metoda obejmuje fakt, że zasobów w chmurze mogą sporadycznie być niedostępne dla więcej niż kilka sekund różnych przyczyn. Na przykład orchestrator może być przenoszenie kontener do innego węzła w klastrze równoważenia obciążenia. W tym czasie niektórych żądań może zakończyć się niepowodzeniem. Innym przykładem może być bazy danych, takich jak Azure SQL, w których bazy danych można przenieść na inny serwer obciążenia równoważenia, co powoduje bazy danych będzie dostępny za kilka sekund.

Istnieje wiele metod wdrożyć logikę ponownych prób z wykładniczego wycofywania.


>[!div class="step-by-step"]
[Poprzednie] (częściowe — błąd strategies.md) [dalej] (implement-resilient-entity-framework-core-sql-connections.md)
