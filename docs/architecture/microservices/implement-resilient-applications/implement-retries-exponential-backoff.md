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
# <a name="implement-retries-with-exponential-backoff"></a>Zaimplementuj ponowną próbę przy użyciu wykładniczej wycofywania

[*Ponawianie prób przy użyciu wykładniczej wycofywania*](/azure/architecture/patterns/retry) jest techniką, która ponawia próbę wykonania operacji przy wykładniczie rosnącym czasie oczekiwania, osiągnięto maksymalną liczbę ponownych prób ( [wykładniczy wycofywania](https://en.wikipedia.org/wiki/Exponential_backoff)). Ta technika obejmuje fakt, że zasoby chmury mogą sporadycznie być niedostępne przez więcej niż kilka sekund z dowolnego powodu. Na przykład Koordynator może przenieść kontener do innego węzła w klastrze w celu równoważenia obciążenia. W tym czasie niektóre żądania mogą zakończyć się niepowodzeniem. Innym przykładem może być baza danych, taka jak SQL Azure, w której można przenieść bazę danych na inny serwer w celu zrównoważenia obciążenia, co powoduje, że baza danych jest niedostępna przez kilka sekund.

Istnieje wiele metod implementacji logiki ponownych prób przy użyciu wykładniczej wycofywania.

>[!div class="step-by-step"]
>[Poprzedni](partial-failure-strategies.md)
>[Następny](implement-resilient-entity-framework-core-sql-connections.md)
