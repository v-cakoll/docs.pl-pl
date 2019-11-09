---
title: Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
ms.date: 05/04/2018
ms.openlocfilehash: 079c9c5ca02b6dc75214d63cb59afdead03d3190
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "73736998"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="f2890-103">Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach</span><span class="sxs-lookup"><span data-stu-id="f2890-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="f2890-104">Ponieważ zauważysz, że po przeczytaniu poprzednich sekcji platforma Azure to otwarta chmura oferująca wiele opcji.</span><span class="sxs-lookup"><span data-stu-id="f2890-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="f2890-105">Możesz jednak użyć najlepiej dopasowanej do Twoich potrzeb, a także zadać pytania dotyczące rodzaju produktu/technologii, które powinny być używane dla aplikacji w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="f2890-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="f2890-106">Zgodnie z zaleceniami *domyślnymi* , poniżej przedstawiono główne kryteria zalecane w niniejszych wskazówkach:</span><span class="sxs-lookup"><span data-stu-id="f2890-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="f2890-107">**Jednolite aplikacje:** Wybierz Azure App Service</span><span class="sxs-lookup"><span data-stu-id="f2890-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="f2890-108">**Aplikacja N-warstwowa:** Wybierz usługi Orchestrator, takie jak Azure Kubernetes Service (AKS) lub App Service, jeśli masz jedną lub kilka usług zaplecza</span><span class="sxs-lookup"><span data-stu-id="f2890-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS) or App Service if you have a single or a few back-end services</span></span>
- <span data-ttu-id="f2890-109">**Mikrousługi:** Wybierz AKS lub Web Apps platformy Azure dla kontenerów</span><span class="sxs-lookup"><span data-stu-id="f2890-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="f2890-110">**Funkcje Bezserwerowe & obsługi zdarzeń:** Wybierz Azure Functions</span><span class="sxs-lookup"><span data-stu-id="f2890-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="f2890-111">**Partia o dużej skali:** Wybierz Azure Batch</span><span class="sxs-lookup"><span data-stu-id="f2890-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="f2890-112">Jednakże to zalecenie powinno być podjęte z szczypania soli, ponieważ wybór produktu będzie zależeć od potrzeb i cech określonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2890-112">However, this recommendation should be taken with a pinch of salt, as the product's selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="f2890-113">Nie wszystkie aplikacje są takie same, nawet gdy początkowo mogą wyglądać podobnie.</span><span class="sxs-lookup"><span data-stu-id="f2890-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="f2890-114">Po dokładniejszej analizie potrzeb aplikacji wybrany produkt może być inny.</span><span class="sxs-lookup"><span data-stu-id="f2890-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="f2890-115">Jednak jako punkt początkowy warto uzyskać wstępne wskazówki, w których można rozpocząć ocenianie i testowanie w oparciu o określony priorytet.</span><span class="sxs-lookup"><span data-stu-id="f2890-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="f2890-116">Na rysunku 1 można zobaczyć podział różnych rodzajów aplikacji i ich idealne scenariusze hostingu platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="f2890-116">In Figure 1, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![Tabela, w której scenariusze hostingu platformy Azure są najlepsze dla różnych aplikacji.](./media/choosing-azure-compute-options-for-container-based-applications/azure-hosting-scenarios-for-apps.png)

> [!div class="step-by-step"]
> <span data-ttu-id="f2890-118">[Poprzedni](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [dalej](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="f2890-118">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
