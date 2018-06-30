---
title: Implementowanie ponownych prób z wykładniczego wycofywania
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie ponownych prób z wykładniczego wycofywania
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ee5dd711484ba7861eedbd9613fda1209736d5b6
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106921"
---
# <a name="implementing-retries-with-exponential-backoff"></a><span data-ttu-id="a9964-103">Implementowanie ponownych prób z wykładniczego wycofywania</span><span class="sxs-lookup"><span data-stu-id="a9964-103">Implementing retries with exponential backoff</span></span>

<span data-ttu-id="a9964-104">[*Ponowne próby z wykładniczego wycofywania* ](https://docs.microsoft.com/azure/architecture/patterns/retry) to technika, który próbuje ponowić próbę wykonania operacji, rośnie wykładniczo czas oczekiwania, aż do osiągnięcia maksymalnej liczby ponownych prób ( [wykładniczego wycofywania](https://en.wikipedia.org/wiki/Exponential_backoff) ).</span><span class="sxs-lookup"><span data-stu-id="a9964-104">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="a9964-105">Ta metoda obejmuje fakt, że zasobów w chmurze mogą sporadycznie być niedostępne dla więcej niż kilka sekund różnych przyczyn.</span><span class="sxs-lookup"><span data-stu-id="a9964-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="a9964-106">Na przykład orchestrator może być przenoszenie kontener do innego węzła w klastrze równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="a9964-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="a9964-107">W tym czasie niektórych żądań może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a9964-107">During that time, some requests might fail.</span></span> <span data-ttu-id="a9964-108">Innym przykładem może być bazy danych, takich jak Azure SQL, w których bazy danych można przenieść na inny serwer obciążenia równoważenia, co powoduje bazy danych będzie dostępny za kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="a9964-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="a9964-109">Istnieje wiele metod wdrożyć logikę ponownych prób z wykładniczego wycofywania.</span><span class="sxs-lookup"><span data-stu-id="a9964-109">There are many approaches to implement retries logic with exponential backoff.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a9964-110">[Poprzednie](partial-failure-strategies.md)
[dalej](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="a9964-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
