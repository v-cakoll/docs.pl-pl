---
title: Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833854"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="de98c-103">Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach</span><span class="sxs-lookup"><span data-stu-id="de98c-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="de98c-104">Jak zauważono, należy po przeczytaniu w poprzednich sekcjach, platforma Azure jest Otwórz chmury, która oferuje wiele opcji do wyboru.</span><span class="sxs-lookup"><span data-stu-id="de98c-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="de98c-105">Można użyć optymalnego dopasowania do własnych potrzeb, jednak również prezentuje pytania o jakie produktu/technologii, należy używać w przypadku aplikacji konteneryzowanych.</span><span class="sxs-lookup"><span data-stu-id="de98c-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="de98c-106">Jako *domyślnie* zalecenia, poniżej przedstawiono główne kryteria, zaleca się w tych wskazówkach:</span><span class="sxs-lookup"><span data-stu-id="de98c-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="de98c-107">**Pojedynczy monolityczną aplikację:** Wybierz usługi Azure App Service</span><span class="sxs-lookup"><span data-stu-id="de98c-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="de98c-108">**Aplikacja N-warstwowa:** Wybierz koordynatorów, takich jak Azure Kubernetes Service (AKS) lub usługi App Service, jeśli masz jeden lub kilka usług zaplecza</span><span class="sxs-lookup"><span data-stu-id="de98c-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="de98c-109">**Mikrousługi:** Wybierz usługi AKS lub usługi Azure Web Apps for Containers</span><span class="sxs-lookup"><span data-stu-id="de98c-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="de98c-110">**Funkcje bezserwerowe & procedury obsługi zdarzeń:** Wybierz usługę Azure Functions</span><span class="sxs-lookup"><span data-stu-id="de98c-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="de98c-111">**Na dużą skalę usługi Batch:** Wybierz usługi Azure Batch</span><span class="sxs-lookup"><span data-stu-id="de98c-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="de98c-112">Jednak to zalecenie powinna zostać podjęta uszczypnięcia soli, jak wybór produktu będzie zależeć od określonej aplikacji potrzebom i właściwości.</span><span class="sxs-lookup"><span data-stu-id="de98c-112">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="de98c-113">Nie wszystkie aplikacje są takie same, nawet wtedy, gdy początkowo może wyglądać podobnych typów.</span><span class="sxs-lookup"><span data-stu-id="de98c-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="de98c-114">Po dogłębną analizę aplikacji potrzebom produktu wybrane mogą być inne.</span><span class="sxs-lookup"><span data-stu-id="de98c-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="de98c-115">Jednak jako punktu wyjścia, warto mieć początkową pomoc, z których można uruchomić oceny i testowania na podstawie niektórych priorytetu.</span><span class="sxs-lookup"><span data-stu-id="de98c-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="de98c-116">Na poniższej ilustracji widać podział różnych rodzajów aplikacji i ich idealne rozwiązanie Azure w scenariuszach hostingu.</span><span class="sxs-lookup"><span data-stu-id="de98c-116">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="de98c-117">[Poprzednie](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [dalej](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="de98c-117">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
