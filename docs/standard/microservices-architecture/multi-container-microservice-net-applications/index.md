---
title: Projektowanie i tworzenie wielu kontenerach i Mikrousługach na podstawie aplikacji .NET
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Informacje na temat architektury zewnętrznych do projektowania i tworzenia wielu kontenerach i Mikrousługach .NET aplikacji.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 3bbf746aa9c0b66a097b8c4df2964b5679342fd0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973631"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Projektowanie i opracowywanie aplikacji obsługującej wiele kontenerów i opartych na Mikrousługach .NET

*Tworzenie aplikacji konteneryzowanych mikrousług oznacza, że tworzysz wielokontenerowych aplikacji. Jednak aplikację obsługującą wiele kontenerów może być również prostsze — na przykład trójwarstwowej aplikacji — i może nie być kompilowane przy użyciu architektury mikrousług.*

Wcześniej zgłoszone możemy pytanie "Jest Docker niezbędne podczas tworzenia architektury mikrousług?" Odpowiedź brzmi wyczyść nie. Platforma docker jest włącznik i może zapewnić znaczne korzyści, ale kontenery i Docker nie są to bezwględnie wymagane dla mikrousług. Na przykład można utworzyć aplikacji opartych na mikrousługach z lub bez platformy Docker przy użyciu usługi Azure Service Fabric, który obsługuje mikrousługi uruchomiona jako proste procesy lub jako kontenery platformy Docker.

Jednak jeśli wiesz, jak projektowanie i opracowywanie aplikacji opartych na mikrousługach, który również opiera się na kontenery platformy Docker, można projektować i tworzyć inne, prostsze modelu aplikacji. Na przykład można zaprojektować aplikacji trójwarstwowej, która wymaga również podejście obsługującej wiele kontenerów. Z tego powodu a ponieważ architektur mikrousług są ważne trendów w środowisku kontenera, ta sekcja koncentruje się na implementacji architektury mikrousług, za pomocą kontenerów platformy Docker.

>[!div class="step-by-step"]
>[Poprzednie](../docker-application-development-process/docker-app-development-workflow.md)
>[dalej](microservice-application-design.md)