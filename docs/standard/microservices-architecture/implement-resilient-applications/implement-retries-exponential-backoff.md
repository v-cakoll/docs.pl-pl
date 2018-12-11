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
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="6ab2e-103">Implementowanie ponownych prób z wykorzystaniem wykładniczego wycofywania</span><span class="sxs-lookup"><span data-stu-id="6ab2e-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="6ab2e-104">[*Ponowne próby z wykorzystaniem wykładniczego wycofywania* ](https://docs.microsoft.com/azure/architecture/patterns/retry) jest techniką, która podejmuje próbę operacji z wykładniczo rosnącym czas oczekiwania, aż do osiągnięcia maksymalnej liczby ponownych prób ( [wykładniczego wycofywania](https://en.wikipedia.org/wiki/Exponential_backoff) ).</span><span class="sxs-lookup"><span data-stu-id="6ab2e-104">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="6ab2e-105">Metoda ta wykorzystuje fakt, że zasoby w chmurze może sporadycznie być niedostępne dla więcej niż kilku sekund z dowolnego powodu.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="6ab2e-106">Na przykład koordynatora może być przenoszenie kontenera do innego węzła w klastrze równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="6ab2e-107">W tym czasie niektórych żądań może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-107">During that time, some requests might fail.</span></span> <span data-ttu-id="6ab2e-108">Innym przykładem może być bazy danych, takich jak Azure SQL, w których bazy danych mogą być przenoszone do innego serwera dla Równoważenie obciążenia, co powoduje bazy danych będzie dostępny przez kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="6ab2e-109">Dostępnych jest wiele metod, aby zaimplementować logikę ponowień z wykorzystaniem wykładniczego wycofywania.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-109">There are many approaches to implement retries logic with exponential backoff.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6ab2e-110">[Poprzednie](partial-failure-strategies.md)
>[dalej](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="6ab2e-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>