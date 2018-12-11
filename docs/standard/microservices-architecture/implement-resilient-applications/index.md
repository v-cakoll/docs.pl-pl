---
title: Implementowanie aplikacji odpornych na błędy
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Implementowanie aplikacji odpornych na błędy
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: ec79221f0238d61f1ca1b2b7c58b1e16be7f4df4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130797"
---
# <a name="implementing-resilient-applications"></a><span data-ttu-id="eb9d8-103">Implementowanie aplikacji odpornych na błędy</span><span class="sxs-lookup"><span data-stu-id="eb9d8-103">Implementing Resilient Applications</span></span>

<span data-ttu-id="eb9d8-104">*Na mikrousługach i aplikacji działających w chmurze musi obejmować częściowe błędy, które na pewno zostanie przeprowadzona po pewnym czasie. Należy tak zaprojektować aplikację, więc będą odporne na awarie, którym te częściowe.*</span><span class="sxs-lookup"><span data-stu-id="eb9d8-104">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You need to design your application so it will be resilient to those partial failures.*</span></span>

<span data-ttu-id="eb9d8-105">Odporność to zdolność do odzyskiwania po awarii i kontynuowania działania.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-105">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="eb9d8-106">Nie jest o unikanie błędów, ale przyjmuje fakt, że będą zdarzać się błędy i reagowanie na ich w taki sposób, aby uniknąć przestoju lub utraty danych.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-106">It is not about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="eb9d8-107">Celem odporności jest przywrócenie aplikacji do stanu pełnej funkcjonalności po wystąpieniu awarii.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-107">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="eb9d8-108">Jest trudne do projektowania i wdrażania aplikacji opartych na mikrousługach.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-108">It is challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="eb9d8-109">Jednak trzeba będzie również nadal uruchomiony w środowisku jakieś awarii w przypadku niektórych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-109">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="eb9d8-110">W związku z tym aplikacja powinna być odporne na błędy.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-110">Therefore, your application should be resilient.</span></span> <span data-ttu-id="eb9d8-111">Powinny zostać tak zaprojektowane do radzenia sobie z błędami częściowych, takich jak awarii sieci lub węzłów lub awarii w chmurze maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-111">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="eb9d8-112">Nawet mikrousługi (kontenery) jest przenoszony do innego węzła w klastrze może powodować sporadyczne błędy krótki w ramach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-112">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="eb9d8-113">Wielu pojedynczych składników aplikacji powinien również zawierać funkcje monitorowania kondycji.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-113">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="eb9d8-114">Postępując zgodnie z wytycznymi podanymi w tym rozdziale, można utworzyć aplikację, która można sprawnie współpracować z autora przejściowy przestój lub skalujący normalne, które występują we wdrożeniach złożone i oparte na chmurze.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-114">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="eb9d8-115">[Poprzednie](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[dalej](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="eb9d8-115">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>