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
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="369c9-103">Implementowanie ponownych prób przy wykładniczym wycofywanie</span><span class="sxs-lookup"><span data-stu-id="369c9-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="369c9-104">[*Ponownych prób z wykładniczego wycofywania*](/azure/architecture/patterns/retry) jest techniką, która ponawia próbę operacji, z wykładniczo zwiększenie czasu oczekiwania, do maksymalnej liczby ponownych prób została osiągnięta [(wykładnicze wycofywania).](https://en.wikipedia.org/wiki/Exponential_backoff)</span><span class="sxs-lookup"><span data-stu-id="369c9-104">[*Retries with exponential backoff*](/azure/architecture/patterns/retry) is a technique that retries an operation, with an exponentially increasing wait time, up to a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="369c9-105">Ta technika obejmuje fakt, że zasoby w chmurze mogą być sporadycznie niedostępne przez więcej niż kilka sekund z jakiegokolwiek powodu.</span><span class="sxs-lookup"><span data-stu-id="369c9-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="369c9-106">Na przykład koordynator może przenosić kontener do innego węzła w klastrze w celu równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="369c9-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="369c9-107">W tym czasie niektóre żądania mogą zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="369c9-107">During that time, some requests might fail.</span></span> <span data-ttu-id="369c9-108">Innym przykładem może być baza danych, takich jak SQL Azure, gdzie bazy danych można przenieść do innego serwera w celu równoważenia obciążenia, powodując bazy danych, które mają być niedostępne przez kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="369c9-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="369c9-109">Istnieje wiele metod implementowania logiki ponownych prób z wykładniczym wycofywaniem.</span><span class="sxs-lookup"><span data-stu-id="369c9-109">There are many approaches to implement retries logic with exponential backoff.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="369c9-110">[Poprzedni](partial-failure-strategies.md)
>[następny](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="369c9-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
