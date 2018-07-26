---
title: Implementowanie ponownych prób z wykorzystaniem wykładniczego wycofywania
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Implementowanie ponownych prób z wykorzystaniem wykładniczego wycofywania
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: a5ab15299ecb501691c26bbc6d377e22a38ee51e
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874367"
---
# <a name="implement-retries-with-exponential-backoff"></a>Implementowanie ponownych prób z wykorzystaniem wykładniczego wycofywania

[*Ponowne próby z wykorzystaniem wykładniczego wycofywania* ](https://docs.microsoft.com/azure/architecture/patterns/retry) jest techniką, która podejmuje próbę operacji z wykładniczo rosnącym czas oczekiwania, aż do osiągnięcia maksymalnej liczby ponownych prób ( [wykładniczego wycofywania](https://en.wikipedia.org/wiki/Exponential_backoff) ). Metoda ta wykorzystuje fakt, że zasoby w chmurze może sporadycznie być niedostępne dla więcej niż kilku sekund z dowolnego powodu. Na przykład koordynatora może być przenoszenie kontenera do innego węzła w klastrze równoważenia obciążenia. W tym czasie niektórych żądań może zakończyć się niepowodzeniem. Innym przykładem może być bazy danych, takich jak Azure SQL, w których bazy danych mogą być przenoszone do innego serwera dla Równoważenie obciążenia, co powoduje bazy danych będzie dostępny przez kilka sekund.

Dostępnych jest wiele metod, aby zaimplementować logikę ponowień z wykorzystaniem wykładniczego wycofywania.


>[!div class="step-by-step"]
[Poprzednie](partial-failure-strategies.md)
[dalej](implement-resilient-entity-framework-core-sql-connections.md)
