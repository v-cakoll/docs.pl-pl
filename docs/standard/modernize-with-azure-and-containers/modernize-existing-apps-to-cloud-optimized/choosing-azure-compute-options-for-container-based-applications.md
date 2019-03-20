---
title: Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: f251aecfeaf2421a5cecf218577369963bc736fb
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2019
ms.locfileid: "58186107"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="b7fee-103">Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach</span><span class="sxs-lookup"><span data-stu-id="b7fee-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="b7fee-104">Jak zauważono, należy po przeczytaniu w poprzednich sekcjach, platforma Azure jest Otwórz chmury, która oferuje wiele opcji do wyboru.</span><span class="sxs-lookup"><span data-stu-id="b7fee-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="b7fee-105">Można użyć optymalnego dopasowania do własnych potrzeb, jednak również prezentuje pytania o jakie produktu/technologii, należy używać w przypadku aplikacji konteneryzowanych.</span><span class="sxs-lookup"><span data-stu-id="b7fee-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="b7fee-106">Jako *domyślnie* zalecenia, poniżej przedstawiono główne kryteria, zaleca się w tych wskazówkach:</span><span class="sxs-lookup"><span data-stu-id="b7fee-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="b7fee-107">**Pojedynczy monolityczną aplikację:** Wybierz usługi Azure App Service</span><span class="sxs-lookup"><span data-stu-id="b7fee-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="b7fee-108">**Aplikacja N-warstwowa:** Wybierz koordynatorów, takich jak Azure Kubernetes Service (AKS), Usługa Service Fabric (CPP) lub usługi App Service, jeśli masz jeden lub kilka usług zaplecza</span><span class="sxs-lookup"><span data-stu-id="b7fee-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS), Service Fabric (SF) or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="b7fee-109">**Mikrousługi systemu Linux:** Wybierz usługi AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="b7fee-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
- <span data-ttu-id="b7fee-110">**Mikrousługi Windows:** Choose Service Fabric</span><span class="sxs-lookup"><span data-stu-id="b7fee-110">**Windows microservices:** Choose Service Fabric</span></span>
- <span data-ttu-id="b7fee-111">**Funkcje bezserwerowe & procedury obsługi zdarzeń:** Wybierz usługę Azure Functions</span><span class="sxs-lookup"><span data-stu-id="b7fee-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="b7fee-112">**Na dużą skalę usługi Batch:** Wybierz usługi Azure Batch</span><span class="sxs-lookup"><span data-stu-id="b7fee-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="b7fee-113">Jednak to zalecenie powinna zostać podjęta uszczypnięcia soli, jak wybór produktu będzie zależeć od określonej aplikacji potrzebom i właściwości.</span><span class="sxs-lookup"><span data-stu-id="b7fee-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="b7fee-114">Nie wszystkie aplikacje są takie same, nawet wtedy, gdy początkowo może wyglądać podobnych typów.</span><span class="sxs-lookup"><span data-stu-id="b7fee-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="b7fee-115">Po dogłębną analizę aplikacji potrzebom produktu wybrane mogą być inne.</span><span class="sxs-lookup"><span data-stu-id="b7fee-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="b7fee-116">Jednak jako punktu wyjścia, warto mieć początkową pomoc, z których można uruchomić oceny i testowania na podstawie niektórych priorytetu.</span><span class="sxs-lookup"><span data-stu-id="b7fee-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="b7fee-117">Na poniższej ilustracji można analizować bardziej globalnego podczas tabeli szczegółowych decyzji.</span><span class="sxs-lookup"><span data-stu-id="b7fee-117">In the next figure, you can analyze a more global while detailed decision table.</span></span>

![](./media/image8.5.png)

<span data-ttu-id="b7fee-118">Zwróć uwagę sposób, w jaki bazowego systemu operacyjnego (Windows vs. System Linux) można także współczynnik decyzji, zgodnie z niektórych koordynatorów są bardziej dojrzała na kontenery systemu Linux i innych kontenerów Windows.</span><span class="sxs-lookup"><span data-stu-id="b7fee-118">Notice how the underlying OS (Windows vs. Linux) can also be a decision factor as some orchestrators are more mature on Linux containers and other on Windows containers.</span></span> <span data-ttu-id="b7fee-119">Na przykład kontenery systemu Linux są bardzo dla dorosłych w usłudze Kubernetes (AKS na platformie Azure) ale mniej dojrzałe w usłudze Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="b7fee-119">For instance, Linux containers are very mature in Kubernetes (AKS in Azure) but less mature on Service Fabric.</span></span> <span data-ttu-id="b7fee-120">Z drugiej strony kontenery Windows są bardziej dojrzałych w usłudze Service Fabric (wydany w maja 2017 r.) i mniej dojrzałe w usłudze AKS.</span><span class="sxs-lookup"><span data-stu-id="b7fee-120">On the other hand, Windows Containers are more mature in Service Fabric (released in May 2017) and less mature in AKS.</span></span>

<span data-ttu-id="b7fee-121">Jednak te różnice w dojrzałości system operacyjny będzie w przyszłości zanikanie i wiele platform będą mieć porównywalne dojrzałości systemu operacyjnego i decyzji będzie określić więcej informacji na temat Preferencje na podstawie konkretnych cech, aplikacja może być konieczne lub oparte na każdej z platform ekosystem przyczyny.</span><span class="sxs-lookup"><span data-stu-id="b7fee-121">However, those differences in OS maturity will fade in the future and multiple platforms will have comparable OS maturity and the decision will lay more on preferences based on specific features your application might need or based on each platform's ecosystem reasons.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="b7fee-122">[Poprzednie](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [dalej](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="b7fee-122">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
