---
title: Projektowanie i opracowywanie aplikacji .NET opartych na wielokontenerach i mikrousługach
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z zewnętrzną architekturą projektowania i opracowywania aplikacji .NET opartych na wielokontenerach i mikrousługach.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296627"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Projektowanie i opracowywanie aplikacji .NET opartych na mikrokontenerach i mikrousługach

*Opracowywanie aplikacji mikrousług kontenerowych oznacza, że tworzysz aplikacje wielokontenerowe. Jednak aplikacja obejmująca wiele kontenerów może być również łatwiejsza — na przykład aplikacji trójwarstwowej — i może nie być skompilowana przy użyciu architektury mikrousług.*

Wcześniej zgłoszono pytanie "czy platforma Docker jest konieczna podczas kompilowania architektury mikrousług?". Odpowiedź jest niezrozumiała. Docker to włącznik i może zapewnić znaczne korzyści, ale kontenery i platforma Docker nie są twardym wymaganiem dla mikrousług. Przykładowo można utworzyć aplikację opartą na mikrousługach z platformą Docker lub bez niej podczas korzystania z usługi Azure Service Fabric, która obsługuje mikrousługi działające jako procesy proste lub kontenery Docker.

Jeśli jednak wiesz, jak projektować i opracowywać aplikację opartą na mikrousługach, która jest również oparta na kontenerach platformy Docker, będziesz mieć możliwość projektowania i opracowywania dowolnego innego, prostszego modelu aplikacji. Na przykład można zaprojektować aplikację trójwarstwowej, która wymaga również podejścia obejmującego wiele kontenerów. Ze względu na to, że architektury mikrousług są istotną tendencją w obrębie świata kontenera, ta sekcja koncentruje się na implementacji architektury mikrousług przy użyciu kontenerów platformy Docker.

>[!div class="step-by-step"]
>[Poprzedni](../docker-application-development-process/docker-app-development-workflow.md)
>[Następny](microservice-application-design.md)
