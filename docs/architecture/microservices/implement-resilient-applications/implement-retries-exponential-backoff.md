---
title: Zaimplementuj ponowną próbę przy użyciu wykładniczej wycofywania
description: Dowiedz się, jak zaimplementować ponowną próbę przy użyciu wykładniczej wycofywania.
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296064"
---
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="5e3c5-103">Zaimplementuj ponowną próbę przy użyciu wykładniczej wycofywania</span><span class="sxs-lookup"><span data-stu-id="5e3c5-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="5e3c5-104">[*Ponawianie prób przy użyciu wykładniczej wycofywania*](/azure/architecture/patterns/retry) jest techniką, która ponawia próbę wykonania operacji przy wykładniczie rosnącym czasie oczekiwania, osiągnięto maksymalną liczbę ponownych prób ( [wykładniczy wycofywania](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="5e3c5-104">[*Retries with exponential backoff*](/azure/architecture/patterns/retry) is a technique that retries an operation, with an exponentially increasing wait time, up to a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="5e3c5-105">Ta technika obejmuje fakt, że zasoby chmury mogą sporadycznie być niedostępne przez więcej niż kilka sekund z dowolnego powodu.</span><span class="sxs-lookup"><span data-stu-id="5e3c5-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="5e3c5-106">Na przykład Koordynator może przenieść kontener do innego węzła w klastrze w celu równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="5e3c5-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="5e3c5-107">W tym czasie niektóre żądania mogą zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5e3c5-107">During that time, some requests might fail.</span></span> <span data-ttu-id="5e3c5-108">Innym przykładem może być baza danych, taka jak SQL Azure, w której można przenieść bazę danych na inny serwer w celu zrównoważenia obciążenia, co powoduje, że baza danych jest niedostępna przez kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="5e3c5-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="5e3c5-109">Istnieje wiele metod implementacji logiki ponownych prób przy użyciu wykładniczej wycofywania.</span><span class="sxs-lookup"><span data-stu-id="5e3c5-109">There are many approaches to implement retries logic with exponential backoff.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5e3c5-110">[Poprzedni](partial-failure-strategies.md)
>[Następny](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="5e3c5-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
