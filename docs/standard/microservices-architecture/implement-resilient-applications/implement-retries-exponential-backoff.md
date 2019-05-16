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
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="e935d-103">Implementowanie ponownych prób z wykorzystaniem wykładniczego wycofywania</span><span class="sxs-lookup"><span data-stu-id="e935d-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="e935d-104">[*Ponawiają próby z wykorzystaniem wykładniczego wycofywania* ](/azure/architecture/patterns/retry) to technika, która ponawia operację z wykładniczo rosnącym czas oczekiwania, aż do maksymalnej liczby ponownych prób osiągnęła ( [wykładniczego wycofywania](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="e935d-104">[*Retries with exponential backoff*](/azure/architecture/patterns/retry) is a technique that retries an operation, with an exponentially increasing wait time, up to a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="e935d-105">Metoda ta wykorzystuje fakt, że zasoby w chmurze może sporadycznie być niedostępne dla więcej niż kilku sekund z dowolnego powodu.</span><span class="sxs-lookup"><span data-stu-id="e935d-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="e935d-106">Na przykład koordynatora może być przenoszenie kontenera do innego węzła w klastrze równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="e935d-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="e935d-107">W tym czasie niektórych żądań może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="e935d-107">During that time, some requests might fail.</span></span> <span data-ttu-id="e935d-108">Innym przykładem może być bazy danych, takich jak Azure SQL, w których bazy danych mogą być przenoszone do innego serwera dla Równoważenie obciążenia, co powoduje bazy danych będzie dostępny przez kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="e935d-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="e935d-109">Dostępnych jest wiele metod, aby zaimplementować logikę ponowień z wykorzystaniem wykładniczego wycofywania.</span><span class="sxs-lookup"><span data-stu-id="e935d-109">There are many approaches to implement retries logic with exponential backoff.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e935d-110">[Poprzednie](partial-failure-strategies.md)
>[dalej](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="e935d-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
