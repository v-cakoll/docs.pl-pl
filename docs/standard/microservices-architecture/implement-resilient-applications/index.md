---
title: Implementowanie aplikacji odpornych na błędy
description: Więcej informacji na temat odporności, ideą w architekturze mikrousług. Należy znać sposób poprawnego działania obsługi błędów przejściowych, ponieważ będą one występować.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 00724509ba6e027ef73f72bfb6f85b8ec0aa9d25
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362746"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="6d243-104">Implementowanie aplikacji odpornych na błędy</span><span class="sxs-lookup"><span data-stu-id="6d243-104">Implement Resilient Applications</span></span>

<span data-ttu-id="6d243-105">*Na mikrousługach i aplikacji działających w chmurze musi obejmować częściowe błędy, które na pewno zostanie przeprowadzona po pewnym czasie. Należy zaprojektować aplikację, aby była odporna na awarie, którym te częściowe.*</span><span class="sxs-lookup"><span data-stu-id="6d243-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="6d243-106">Odporność to zdolność do odzyskiwania po awarii i kontynuowania działania.</span><span class="sxs-lookup"><span data-stu-id="6d243-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="6d243-107">Nie o unikanie błędów, ale przyjmuje fakt, że będą zdarzać się błędy i reagowanie na ich w taki sposób, aby uniknąć przestoju lub utraty danych.</span><span class="sxs-lookup"><span data-stu-id="6d243-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="6d243-108">Celem odporności jest przywrócenie aplikacji do stanu pełnej funkcjonalności po wystąpieniu awarii.</span><span class="sxs-lookup"><span data-stu-id="6d243-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="6d243-109">Jest trudne do projektowania i wdrażania aplikacji opartych na mikrousługach.</span><span class="sxs-lookup"><span data-stu-id="6d243-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="6d243-110">Jednak trzeba będzie również nadal uruchomiony w środowisku jakieś awarii w przypadku niektórych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d243-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="6d243-111">W związku z tym aplikacja powinna być odporne na błędy.</span><span class="sxs-lookup"><span data-stu-id="6d243-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="6d243-112">Powinny zostać tak zaprojektowane do radzenia sobie z błędami częściowych, takich jak awarii sieci lub węzłów lub awarii w chmurze maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="6d243-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="6d243-113">Nawet mikrousługi (kontenery) jest przenoszony do innego węzła w klastrze może powodować sporadyczne błędy krótki w ramach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d243-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="6d243-114">Wielu pojedynczych składników aplikacji powinien również zawierać funkcje monitorowania kondycji.</span><span class="sxs-lookup"><span data-stu-id="6d243-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="6d243-115">Postępując zgodnie z wytycznymi podanymi w tym rozdziale, można utworzyć aplikację, która można sprawnie współpracować z autora przejściowy przestój lub skalujący normalne, które występują we wdrożeniach złożone i oparte na chmurze.</span><span class="sxs-lookup"><span data-stu-id="6d243-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6d243-116">[Poprzednie](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[dalej](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="6d243-116">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>