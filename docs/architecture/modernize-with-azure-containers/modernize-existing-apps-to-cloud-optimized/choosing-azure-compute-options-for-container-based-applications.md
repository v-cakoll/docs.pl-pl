---
title: Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68677037"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="4f3e3-103">Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach</span><span class="sxs-lookup"><span data-stu-id="4f3e3-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="4f3e3-104">Ponieważ zauważysz, że po przeczytaniu poprzednich sekcji platforma Azure to otwarta chmura oferująca wiele opcji.</span><span class="sxs-lookup"><span data-stu-id="4f3e3-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="4f3e3-105">Możesz jednak użyć najlepiej dopasowanej do Twoich potrzeb, a także zadać pytania dotyczące rodzaju produktu/technologii, które powinny być używane dla aplikacji w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="4f3e3-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="4f3e3-106">Zgodnie z zaleceniami domyślnymi, poniżej przedstawiono główne kryteria zalecane w niniejszych wskazówkach:</span><span class="sxs-lookup"><span data-stu-id="4f3e3-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="4f3e3-107">**Jednolite aplikacje:** Wybierz Azure App Service</span><span class="sxs-lookup"><span data-stu-id="4f3e3-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="4f3e3-108">**Aplikacja N-warstwowa:** Wybierz usługi Orchestrator, takie jak Azure Kubernetes Service (AKS) lub App Service, jeśli masz jedną lub kilka usług zaplecza</span><span class="sxs-lookup"><span data-stu-id="4f3e3-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="4f3e3-109">**Mikrousług** Wybierz AKS lub Web Apps platformy Azure dla kontenerów</span><span class="sxs-lookup"><span data-stu-id="4f3e3-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="4f3e3-110">**Funkcje bezserwerowe & obsługi zdarzeń:** Wybierz Azure Functions</span><span class="sxs-lookup"><span data-stu-id="4f3e3-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="4f3e3-111">**Partia o dużej skali:** Wybierz Azure Batch</span><span class="sxs-lookup"><span data-stu-id="4f3e3-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="4f3e3-112">Jednakże to zalecenie powinno być podjęte z szczypania soli, ponieważ wybór produktu będzie zależeć od potrzeb i cech określonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4f3e3-112">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="4f3e3-113">Nie wszystkie aplikacje są takie same, nawet gdy początkowo mogą wyglądać podobnie.</span><span class="sxs-lookup"><span data-stu-id="4f3e3-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="4f3e3-114">Po dokładniejszej analizie potrzeb aplikacji wybrany produkt może być inny.</span><span class="sxs-lookup"><span data-stu-id="4f3e3-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="4f3e3-115">Jednak jako punkt początkowy warto uzyskać wstępne wskazówki, w których można rozpocząć ocenianie i testowanie w oparciu o określony priorytet.</span><span class="sxs-lookup"><span data-stu-id="4f3e3-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="4f3e3-116">Na następnym rysunku można zobaczyć podział różnych rodzajów aplikacji i ich idealne scenariusze hostingu platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="4f3e3-116">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="4f3e3-117">[Poprzedni](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)Następny
> [](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="4f3e3-117">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
