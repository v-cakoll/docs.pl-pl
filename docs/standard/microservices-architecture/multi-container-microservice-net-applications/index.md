---
title: Projektowanie i tworzenie wielu kontenerach i Mikrousługach na podstawie aplikacji .NET
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Informacje na temat architektury zewnętrznych do projektowania i tworzenia wielu kontenerach i Mikrousługach .NET aplikacji.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 3bbf746aa9c0b66a097b8c4df2964b5679342fd0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144146"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="1b0b0-103">Projektowanie i opracowywanie aplikacji obsługującej wiele kontenerów i opartych na Mikrousługach .NET</span><span class="sxs-lookup"><span data-stu-id="1b0b0-103">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="1b0b0-104">*Tworzenie aplikacji konteneryzowanych mikrousług oznacza, że tworzysz wielokontenerowych aplikacji. Jednak aplikację obsługującą wiele kontenerów może być również prostsze — na przykład trójwarstwowej aplikacji — i może nie być kompilowane przy użyciu architektury mikrousług.*</span><span class="sxs-lookup"><span data-stu-id="1b0b0-104">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="1b0b0-105">Wcześniej zgłoszone możemy pytanie "Jest Docker niezbędne podczas tworzenia architektury mikrousług?"</span><span class="sxs-lookup"><span data-stu-id="1b0b0-105">Earlier we raised the question "Is Docker necessary when building a microservice architecture?"</span></span> <span data-ttu-id="1b0b0-106">Odpowiedź brzmi wyczyść nie.</span><span class="sxs-lookup"><span data-stu-id="1b0b0-106">The answer is a clear no.</span></span> <span data-ttu-id="1b0b0-107">Platforma docker jest włącznik i może zapewnić znaczne korzyści, ale kontenery i Docker nie są to bezwględnie wymagane dla mikrousług.</span><span class="sxs-lookup"><span data-stu-id="1b0b0-107">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="1b0b0-108">Na przykład można utworzyć aplikacji opartych na mikrousługach z lub bez platformy Docker przy użyciu usługi Azure Service Fabric, który obsługuje mikrousługi uruchomiona jako proste procesy lub jako kontenery platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="1b0b0-108">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="1b0b0-109">Jednak jeśli wiesz, jak projektowanie i opracowywanie aplikacji opartych na mikrousługach, który również opiera się na kontenery platformy Docker, można projektować i tworzyć inne, prostsze modelu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1b0b0-109">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="1b0b0-110">Na przykład można zaprojektować aplikacji trójwarstwowej, która wymaga również podejście obsługującej wiele kontenerów.</span><span class="sxs-lookup"><span data-stu-id="1b0b0-110">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="1b0b0-111">Z tego powodu a ponieważ architektur mikrousług są ważne trendów w środowisku kontenera, ta sekcja koncentruje się na implementacji architektury mikrousług, za pomocą kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="1b0b0-111">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1b0b0-112">[Poprzednie](../docker-application-development-process/docker-app-development-workflow.md)
>[dalej](microservice-application-design.md)</span><span class="sxs-lookup"><span data-stu-id="1b0b0-112">[Previous](../docker-application-development-process/docker-app-development-workflow.md)
[Next](microservice-application-design.md)</span></span>