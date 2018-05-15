---
title: Projektowanie i tworzenie wielu kontenera i Mikrousługi na podstawie aplikacji .NET
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Projektowanie i tworzenie wielu kontenera i Mikrousługi na podstawie aplikacji .NET
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 297a53d6d6d37b1fa4a0e021919c9df86edeca03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="a03a5-103">Projektowanie i tworzenie aplikacji na podstawie Mikrousługi i usługi kontenera platformy .NET</span><span class="sxs-lookup"><span data-stu-id="a03a5-103">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="a03a5-104">*Opracowywanie aplikacji konteneryzowanych mikrousługi oznacza, że są tworzenia wielu kontenera aplikacji. Jednak aplikacji kontenera usługi mogą być również prostsze — na przykład trójwarstwowa aplikacja — i nie może zostać utworzony przy użyciu architektury mikrousługi.*</span><span class="sxs-lookup"><span data-stu-id="a03a5-104">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="a03a5-105">Wcześniej możemy wywoływane pytanie "Jest Docker niezbędne podczas kompilowania architektury mikrousługi?"</span><span class="sxs-lookup"><span data-stu-id="a03a5-105">Earlier we raised the question “Is Docker necessary when building a microservice architecture?”</span></span> <span data-ttu-id="a03a5-106">Odpowiedź brzmi wyczyść nie.</span><span class="sxs-lookup"><span data-stu-id="a03a5-106">The answer is a clear no.</span></span> <span data-ttu-id="a03a5-107">Docker jest czynnik i oferuje istotne korzyści, ale kontenery i Docker nie są wymagane twardych dla mikrousług.</span><span class="sxs-lookup"><span data-stu-id="a03a5-107">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="a03a5-108">Na przykład można utworzyć aplikacji sieci mikrousług z lub bez Docker podczas korzystania z sieci szkieletowej usług Azure, obsługujący mikrousług uruchomione jako procesy prostego lub kontenery Docker.</span><span class="sxs-lookup"><span data-stu-id="a03a5-108">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="a03a5-109">Jednak jeśli wiesz, jak projektowanie i tworzenie aplikacji na podstawie mikrousług, opartą na Docker kontenerów, można do projektowania i opracowywania innych, łatwiejsze modelu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a03a5-109">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="a03a5-110">Na przykład może projektowania aplikacji trójwarstwowej wymagającego podejście wielu kontenera.</span><span class="sxs-lookup"><span data-stu-id="a03a5-110">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="a03a5-111">Z tego powodu i architektury mikrousługi są ważne trendu w świecie kontenera, w tej sekcji koncentruje się na implementacji architektury mikrousługi, za pomocą kontenerów Docker.</span><span class="sxs-lookup"><span data-stu-id="a03a5-111">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a03a5-112">[Poprzednie] (.. /containerize-NET-Framework-Applications/index.MD) [dalej] (ruch design.md mikrousługi aplikacji)</span><span class="sxs-lookup"><span data-stu-id="a03a5-112">[Previous] (../containerize-net-framework-applications/index.md) [Next] (microservice-application-design.md)</span></span>
