---
title: Projektowanie i tworzenie aplikacji .NET opartych na wielu kontenerach i mikrousługach
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zrozumienie architektury zewnętrznej do projektowania i tworzenia aplikacji .NET opartych na wielu kontenerach i mikrousługach.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70296627"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Projektowanie i tworzenie aplikacji .NET opartych na wielu kontenerach i mikrousługach

*Tworzenie konteneryzowanych aplikacji mikrousług oznacza, że tworzysz aplikacje wielokontenerowe. Jednak aplikacja wielokontenerowa może być również prostsza — na przykład aplikacja trójwarstwowa — i może nie być zbudowana przy użyciu architektury mikrousług.*

Wcześniej podniesiono pytanie "Czy docker jest konieczne podczas tworzenia architektury mikrousług?" Odpowiedź jest jasna nie. Platforma Docker jest czynnikiem wspomagającym i może zapewnić znaczne korzyści, ale kontenery i platformy Docker nie są trudne wymagania dla mikrousług. Na przykład można utworzyć aplikację opartą na mikrousługach z platformą Docker lub bez niej podczas korzystania z sieci Szkieletusług platformy Azure, która obsługuje mikrousługi działające w prostych procesach lub jako kontenery platformy Docker.

Jeśli jednak wiesz, jak zaprojektować i opracować aplikację opartą na mikrousługach, która jest również oparta na kontenerach platformy Docker, będzie można zaprojektować i opracować dowolny inny, prostszy model aplikacji. Na przykład można zaprojektować aplikację trójwarstwową, która również wymaga podejścia wielokontenerowego. Z tego powodu i ponieważ architektury mikrousług są ważnym trendem w świecie kontenerów, w tej sekcji koncentruje się na implementacji architektury mikrousług przy użyciu kontenerów platformy Docker.

>[!div class="step-by-step"]
>[Poprzedni](../docker-application-development-process/docker-app-development-workflow.md)
>[następny](microservice-application-design.md)
