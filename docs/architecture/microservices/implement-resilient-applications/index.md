---
title: Implementowanie aplikacji odpornych na błędy
description: Dowiedz się więcej o odporności, podstawowej koncepcji w architekturze mikrousług. Musisz wiedzieć, jak bezpiecznie obsługiwać błędy przejściowe, ponieważ wystąpią.
ms.date: 10/16/2018
ms.openlocfilehash: 766349e72389f848b0a741b020707cc7acf3410d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296061"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="3398d-104">Implementuj aplikacje odporne</span><span class="sxs-lookup"><span data-stu-id="3398d-104">Implement Resilient Applications</span></span>

<span data-ttu-id="3398d-105">*Aplikacje mikrousługowe i oparte na chmurze muszą obejmować częściowe awarie, które wystąpiły w przyszłości. Musisz zaprojektować aplikację, aby była odporna na błędy częściowe.*</span><span class="sxs-lookup"><span data-stu-id="3398d-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="3398d-106">Odporność to zdolność do odzyskiwania po awarii i kontynuowania działania.</span><span class="sxs-lookup"><span data-stu-id="3398d-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="3398d-107">Nie ma ona wpływu na błędy, ale akceptuje fakt, że awarie i odpowiadanie na nie są w taki sposób, aby uniknąć przestoju lub utraty danych.</span><span class="sxs-lookup"><span data-stu-id="3398d-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="3398d-108">Celem odporności jest przywrócenie aplikacji do stanu w pełni funkcjonalnym po awarii.</span><span class="sxs-lookup"><span data-stu-id="3398d-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="3398d-109">Jest to trudne do zaprojektowania i wdrożenia aplikacji opartej na mikrousługach.</span><span class="sxs-lookup"><span data-stu-id="3398d-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="3398d-110">Jednak należy również zachować swoją aplikację w środowisku, w którym niektóre różne błędy są pewne.</span><span class="sxs-lookup"><span data-stu-id="3398d-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="3398d-111">W związku z tym aplikacja powinna być odporna na błędy.</span><span class="sxs-lookup"><span data-stu-id="3398d-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="3398d-112">Powinna być zaprojektowana tak, aby sprostać częściowym błędom, takim jak awaria sieci lub węzły lub maszyny wirtualne, które uległy awarii w chmurze.</span><span class="sxs-lookup"><span data-stu-id="3398d-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="3398d-113">Nawet mikrousługi (kontenery) przenoszone do innego węzła w klastrze mogą spowodować sporadyczne krótkie błędy w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3398d-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="3398d-114">Wiele pojedynczych składników aplikacji powinna również zawierać funkcje monitorowania kondycji.</span><span class="sxs-lookup"><span data-stu-id="3398d-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="3398d-115">Postępując zgodnie z wytycznymi w tym rozdziale, można utworzyć aplikację, która może działać bezproblemowo pomimo przejściowego przestoju lub normalnego hiccupsu w przypadku wdrożeń złożonych i opartych na chmurze.</span><span class="sxs-lookup"><span data-stu-id="3398d-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3398d-116">[Poprzedni](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[Następny](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="3398d-116">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>
