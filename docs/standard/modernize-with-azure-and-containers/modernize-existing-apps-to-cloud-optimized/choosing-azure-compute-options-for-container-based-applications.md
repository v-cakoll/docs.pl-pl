---
title: Wybieranie platformy obliczeń platformy Azure dla aplikacji kontenera
description: Modernizacji istniejących aplikacji .NET z kontenerami chmury Azure i systemu Windows | Wybieranie platformy obliczeń platformy Azure dla aplikacji kontenera
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: ebf022a52aaaf95ae335976f5e097921b0ac8006
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958243"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="9c973-103">Wybieranie platformy obliczeń platformy Azure dla aplikacji kontenera</span><span class="sxs-lookup"><span data-stu-id="9c973-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="9c973-104">Jak można zauważyć po odczytaniu w poprzednich sekcjach, platforma Azure jest Otwórz chmury, które oferuje wiele wyborów.</span><span class="sxs-lookup"><span data-stu-id="9c973-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="9c973-105">Można użyć najlepiej spełnia Twoje potrzeby, jednak również powierzchni pytania o jakie/technologii produktów należy używać konteneryzowanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c973-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="9c973-106">Jako *domyślnie* zalecenia, poniżej przedstawiono główne kryteria zalecane w tych wskazówkach:</span><span class="sxs-lookup"><span data-stu-id="9c973-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

  - <span data-ttu-id="9c973-107">**Jednej aplikacji wbudowanymi:** wybierz usługi aplikacji Azure</span><span class="sxs-lookup"><span data-stu-id="9c973-107">**Single monolithic app:** Choose Azure App Service</span></span>
  - <span data-ttu-id="9c973-108">**N-warstwowa aplikacja:** wybierz orchestrators, takie jak usługi Kubernetes Azure (AKS), usługa sieci szkieletowej (CPP) lub usługi aplikacji, jeśli masz jedną lub kilka usług zaplecza</span><span class="sxs-lookup"><span data-stu-id="9c973-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS), Service Fabric (SF) or App Service if you have a single or few back-end services</span></span>
  - <span data-ttu-id="9c973-109">**Linux mikrousług:** wybierz AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="9c973-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
  - <span data-ttu-id="9c973-110">**Mikrousług systemu Windows:** wybierz sieci szkieletowej usług</span><span class="sxs-lookup"><span data-stu-id="9c973-110">**Windows microservices:** Choose Service Fabric</span></span>
  - <span data-ttu-id="9c973-111">**Funkcje niekorzystającą & procedury obsługi zdarzeń:** wybierz usługi Azure Functions</span><span class="sxs-lookup"><span data-stu-id="9c973-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
  - <span data-ttu-id="9c973-112">**Na dużą skalę partii:** wybierz partii zadań Azure</span><span class="sxs-lookup"><span data-stu-id="9c973-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="9c973-113">Jednak tego zalecenia należy zwrócić na powiększanie soli, jak wybór produktu będzie zależeć od potrzeb i właściwości określonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c973-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="9c973-114">Nie wszystkie aplikacje są takie same, nawet wtedy, gdy początkowo może wyglądać podobnych typów.</span><span class="sxs-lookup"><span data-stu-id="9c973-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="9c973-115">Po dokładniejszej analizy potrzeb aplikacji zaznaczono produkt może być różne.</span><span class="sxs-lookup"><span data-stu-id="9c973-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="9c973-116">Jednak jako punkt początkowy, warto mieć początkowej wskazówek, z którym rozpoczęcia ewaluacji i testowania na podstawie określonych priorytetu.</span><span class="sxs-lookup"><span data-stu-id="9c973-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="9c973-117">Następny rysunek można analizować bardziej globalnego podczas tabeli szczegółowe decyzji.</span><span class="sxs-lookup"><span data-stu-id="9c973-117">In the next figure, you can analyze a more global while detailed decision table.</span></span>

![](./media/image8.5.png)

<span data-ttu-id="9c973-118">Powiadomienie jak podstawowego systemu operacyjnego (w porównaniu z systemem Windows. Linux) można także współczynnik decyzji, niektóre orchestrators są bardziej dojrzałe Linux kontenerów i innych kontenerów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9c973-118">Notice how the underlying OS (Windows vs. Linux) can also be a decision factor as some orchestrators are more mature on Linux containers and other on Windows containers.</span></span> <span data-ttu-id="9c973-119">Na przykład kontenery Linux są bardzo dojrzałe w Kubernetes (AKS na platformie Azure) ale mniej dojrzałe w sieci szkieletowej usług.</span><span class="sxs-lookup"><span data-stu-id="9c973-119">For instance, Linux containers are very mature in Kubernetes (AKS in Azure) but less mature on Service Fabric.</span></span> <span data-ttu-id="9c973-120">Z drugiej strony kontenery systemu Windows są bardziej dojrzałe w sieci szkieletowej usług (wydane w 2017 maja) i mniej dojrzałe w AKS.</span><span class="sxs-lookup"><span data-stu-id="9c973-120">On the other hand, Windows Containers are more mature in Service Fabric (released in May 2017) and less mature in AKS.</span></span>

<span data-ttu-id="9c973-121">Jednak różnic w dojrzałości system operacyjny będzie w przyszłości zanikania i wielu platform będą mieli porównywalne dojrzałości systemu operacyjnego i decyzja będzie leżą więcej informacji na temat Preferencje na podstawie konkretnych cech aplikacji może być konieczne lub oparte na każdej z platform ekosystemu przyczyny.</span><span class="sxs-lookup"><span data-stu-id="9c973-121">However, those differences in OS maturity will fade in the future and multiple platforms will have comparable OS maturity and the decision will lay more on preferences based on specific features your application might need or based on each platform's ecosystem reasons.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="9c973-122">[Poprzednie](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[dalej](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="9c973-122">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
