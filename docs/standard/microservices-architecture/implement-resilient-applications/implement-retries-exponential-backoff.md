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
# <a name="implementing-retries-with-exponential-backoff"></a><span data-ttu-id="291db-103">Implementowanie ponownych prób z wykładniczego wycofywania</span><span class="sxs-lookup"><span data-stu-id="291db-103">Implementing retries with exponential backoff</span></span>

<span data-ttu-id="291db-104">[*Ponowne próby z wykładniczego wycofywania* ](https://docs.microsoft.com/azure/architecture/patterns/retry) to technika, który próbuje ponowić próbę wykonania operacji, rośnie wykładniczo czas oczekiwania, aż do osiągnięcia maksymalnej liczby ponownych prób ( [wykładniczego wycofywania](https://en.wikipedia.org/wiki/Exponential_backoff) ).</span><span class="sxs-lookup"><span data-stu-id="291db-104">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="291db-105">Ta metoda obejmuje fakt, że zasobów w chmurze mogą sporadycznie być niedostępne dla więcej niż kilka sekund różnych przyczyn.</span><span class="sxs-lookup"><span data-stu-id="291db-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="291db-106">Na przykład orchestrator może być przenoszenie kontener do innego węzła w klastrze równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="291db-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="291db-107">W tym czasie niektórych żądań może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="291db-107">During that time, some requests might fail.</span></span> <span data-ttu-id="291db-108">Innym przykładem może być bazy danych, takich jak Azure SQL, w których bazy danych można przenieść na inny serwer obciążenia równoważenia, co powoduje bazy danych będzie dostępny za kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="291db-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="291db-109">Istnieje wiele metod wdrożyć logikę ponownych prób z wykładniczego wycofywania.</span><span class="sxs-lookup"><span data-stu-id="291db-109">There are many approaches to implement retries logic with exponential backoff.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="291db-110">[Poprzednie] (częściowe — błąd strategies.md) [dalej] (implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="291db-110">[Previous] (partial-failure-strategies.md) [Next] (implement-resilient-entity-framework-core-sql-connections.md)</span></span>
