---
title: Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
ms.date: 05/04/2018
ms.openlocfilehash: d91cd279402dc24beb5f766c06cb85ac8d74f482
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758821"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="b56e7-103">Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach</span><span class="sxs-lookup"><span data-stu-id="b56e7-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="b56e7-104">Jak zauważono, należy po przeczytaniu w poprzednich sekcjach, platforma Azure jest Otwórz chmury, która oferuje wiele opcji do wyboru.</span><span class="sxs-lookup"><span data-stu-id="b56e7-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="b56e7-105">Można użyć optymalnego dopasowania do własnych potrzeb, jednak również prezentuje pytania o jakie produktu/technologii, należy używać w przypadku aplikacji konteneryzowanych.</span><span class="sxs-lookup"><span data-stu-id="b56e7-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="b56e7-106">Jako *domyślnie* zalecenia, poniżej przedstawiono główne kryteria, zaleca się w tych wskazówkach:</span><span class="sxs-lookup"><span data-stu-id="b56e7-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="b56e7-107">**Pojedynczy monolityczną aplikację:** Wybierz usługi Azure App Service</span><span class="sxs-lookup"><span data-stu-id="b56e7-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="b56e7-108">**Aplikacja N-warstwowa:** Wybierz koordynatorów, takich jak Azure Kubernetes Service (AKS) lub usługi App Service, jeśli masz jeden lub kilka usług zaplecza</span><span class="sxs-lookup"><span data-stu-id="b56e7-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="b56e7-109">**Mikrousługi systemu Linux:** Wybierz usługi AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="b56e7-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
- <span data-ttu-id="b56e7-110">**Mikrousługi Windows:** Wybierz usługi Azure Web Apps for Containers</span><span class="sxs-lookup"><span data-stu-id="b56e7-110">**Windows microservices:** Choose Azure Web Apps for Containers</span></span>
- <span data-ttu-id="b56e7-111">**Funkcje bezserwerowe & procedury obsługi zdarzeń:** Wybierz usługę Azure Functions</span><span class="sxs-lookup"><span data-stu-id="b56e7-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="b56e7-112">**Na dużą skalę usługi Batch:** Wybierz usługi Azure Batch</span><span class="sxs-lookup"><span data-stu-id="b56e7-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="b56e7-113">Jednak to zalecenie powinna zostać podjęta uszczypnięcia soli, jak wybór produktu będzie zależeć od określonej aplikacji potrzebom i właściwości.</span><span class="sxs-lookup"><span data-stu-id="b56e7-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="b56e7-114">Nie wszystkie aplikacje są takie same, nawet wtedy, gdy początkowo może wyglądać podobnych typów.</span><span class="sxs-lookup"><span data-stu-id="b56e7-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="b56e7-115">Po dogłębną analizę aplikacji potrzebom produktu wybrane mogą być inne.</span><span class="sxs-lookup"><span data-stu-id="b56e7-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="b56e7-116">Jednak jako punktu wyjścia, warto mieć początkową pomoc, z których można uruchomić oceny i testowania na podstawie niektórych priorytetu.</span><span class="sxs-lookup"><span data-stu-id="b56e7-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="b56e7-117">Na poniższej ilustracji widać podział różnych rodzajów aplikacji i ich idealne rozwiązanie Azure w scenariuszach hostingu.</span><span class="sxs-lookup"><span data-stu-id="b56e7-117">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="b56e7-118">[Poprzednie](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [dalej](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="b56e7-118">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
