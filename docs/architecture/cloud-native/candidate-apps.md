---
title: Aplikacje kandydujące dla natywnych dla chmury
description: Dowiedz się, które typy aplikacji korzystają z podejścia natywnego dla chmury
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 8e58f5bd3aa0a4503ea73ab454e42e863eb0bb5d
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805610"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="da19f-103">Aplikacje kandydujące dla natywnych dla chmury</span><span class="sxs-lookup"><span data-stu-id="da19f-103">Candidate apps for cloud native</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="da19f-104">Spójrz na aplikacje w swoim portfolio.</span><span class="sxs-lookup"><span data-stu-id="da19f-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="da19f-105">Ile z nich kwalifikuje się do architektury natywnej dla chmury?</span><span class="sxs-lookup"><span data-stu-id="da19f-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="da19f-106">Wszystkie?</span><span class="sxs-lookup"><span data-stu-id="da19f-106">All of them?</span></span> <span data-ttu-id="da19f-107">Być może niektóre?</span><span class="sxs-lookup"><span data-stu-id="da19f-107">Perhaps some?</span></span>

<span data-ttu-id="da19f-108">Stosując analizę kosztów i korzyści, istnieje duża szansa, że większość nie będzie obsługiwać mocny tag cena wymagane do chmury rodzimych.</span><span class="sxs-lookup"><span data-stu-id="da19f-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="da19f-109">Koszt natywnego chmury znacznie przekroczy wartość biznesową aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da19f-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="da19f-110">Jaki typ aplikacji może być kandydatem do chmury natywnej?</span><span class="sxs-lookup"><span data-stu-id="da19f-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="da19f-111">Duży, strategiczny system dla przedsiębiorstw, który musi stale rozwijać możliwości/funkcje biznesowe</span><span class="sxs-lookup"><span data-stu-id="da19f-111">A large, strategic enterprise system that needs to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="da19f-112">Aplikacja, która wymaga dużej prędkości uwalniania - z dużą pewnością</span><span class="sxs-lookup"><span data-stu-id="da19f-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="da19f-113">System, w którym poszczególne funkcje muszą zostać uwolnione *bez* pełnego przemieszczenia całego systemu</span><span class="sxs-lookup"><span data-stu-id="da19f-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="da19f-114">Aplikacja opracowana przez zespoły z doświadczeniem w różnych stosach technologicznych</span><span class="sxs-lookup"><span data-stu-id="da19f-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="da19f-115">Aplikacja ze składnikami, które muszą być skalowane niezależnie</span><span class="sxs-lookup"><span data-stu-id="da19f-115">An application with components that must scale independently</span></span>

<span data-ttu-id="da19f-116">Następnie są starsze systemy.</span><span class="sxs-lookup"><span data-stu-id="da19f-116">Then there are legacy systems.</span></span> <span data-ttu-id="da19f-117">Chociaż wszyscy chcielibyśmy tworzyć nowe aplikacje, często jesteśmy odpowiedzialni za modernizację starszych obciążeń, które mają kluczowe znaczenie dla firmy.</span><span class="sxs-lookup"><span data-stu-id="da19f-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="da19f-118">Z biegiem czasu starsza aplikacja może być rozłożona na mikrousługi, konteneryzowane i ostatecznie "replatformed" do architektury natywnej chmury.</span><span class="sxs-lookup"><span data-stu-id="da19f-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="da19f-119">Modernizacja starszych aplikacji</span><span class="sxs-lookup"><span data-stu-id="da19f-119">Modernizing legacy apps</span></span>

<span data-ttu-id="da19f-120">Bezpłatna e-book firmy Microsoft [Modernizuj istniejące aplikacje platformy .NET za pomocą chmury Azure i kontenerów systemu Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) zawiera wskazówki dotyczące migracji obciążeń lokalnych do chmury.</span><span class="sxs-lookup"><span data-stu-id="da19f-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="da19f-121">Rysunek 1-10 pokazuje, że nie ma jednej, uniwersalnej strategii modernizacji starszych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da19f-121">Figure 1-10 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

![Strategie migracji starszych obciążeń](./media/strategies-for-migrating-legacy-workloads.png)

<span data-ttu-id="da19f-123">**Rysunek 1-10**.</span><span class="sxs-lookup"><span data-stu-id="da19f-123">**Figure 1-10**.</span></span> <span data-ttu-id="da19f-124">Strategie migracji starszych obciążeń</span><span class="sxs-lookup"><span data-stu-id="da19f-124">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="da19f-125">Aplikacje monolityczne, które nie są krytyczne, w dużej mierze korzystają z szybkiej migracji[(Cloud Infrastructure-Ready).](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)</span><span class="sxs-lookup"><span data-stu-id="da19f-125">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) migration.</span></span> <span data-ttu-id="da19f-126">W tym miejscu obciążenie lokalne jest ponownie hostowane na maszynie Wirtualnej opartej na chmurze, bez zmian.</span><span class="sxs-lookup"><span data-stu-id="da19f-126">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="da19f-127">Takie podejście używa [modelu IaaS (Infrastruktura jako usługa).](https://azure.microsoft.com/overview/what-is-iaas/)</span><span class="sxs-lookup"><span data-stu-id="da19f-127">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="da19f-128">Platforma Azure zawiera kilka narzędzi, takich jak [Azure Migrate,](https://azure.microsoft.com/services/azure-migrate/) [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)i Usługa migracji bazy danych platformy [Azure,](https://azure.microsoft.com/campaigns/database-migration/) aby ułatwić taki ruch.</span><span class="sxs-lookup"><span data-stu-id="da19f-128">Azure includes several tools such as [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) to make such a move easier.</span></span> <span data-ttu-id="da19f-129">Chociaż ta strategia może przynieść pewne oszczędności, takie aplikacje zazwyczaj nie zostały zaprojektowany, aby odblokować i wykorzystać zalety chmury obliczeniowej.</span><span class="sxs-lookup"><span data-stu-id="da19f-129">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span>

<span data-ttu-id="da19f-130">Monolityczne aplikacje, które są często krytyczne dla firmy, korzystają z ulepszonej migracji lift-and-shift *(Cloud Optimized).*</span><span class="sxs-lookup"><span data-stu-id="da19f-130">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="da19f-131">Takie podejście obejmuje optymalizacje wdrażania, które umożliwiają kluczowe usługi w chmurze — bez zmiany podstawowej architektury aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da19f-131">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="da19f-132">Na przykład można [konteneryzować](https://docs.microsoft.com/virtualization/windowscontainers/about/) aplikację i wdrożyć ją w koordynatorze kontenerów, takich jak [usługi Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/)Services, omówione w dalszej części tej książki.</span><span class="sxs-lookup"><span data-stu-id="da19f-132">For example, you might [containerize](https://docs.microsoft.com/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="da19f-133">Raz w chmurze, aplikacja może korzystać z innych usług w chmurze, takich jak bazy danych, kolejki komunikatów, monitorowania i rozproszonego buforowania.</span><span class="sxs-lookup"><span data-stu-id="da19f-133">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="da19f-134">Wreszcie monolityczne aplikacje, które wykonują strategiczne funkcje przedsiębiorstwa, mogą najlepiej skorzystać z podejścia *natywnego w chmurze,* przedmiotu tej książki.</span><span class="sxs-lookup"><span data-stu-id="da19f-134">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="da19f-135">Takie podejście zapewnia zwinność i prędkość.</span><span class="sxs-lookup"><span data-stu-id="da19f-135">This approach provides agility and velocity.</span></span> <span data-ttu-id="da19f-136">Ale, to jest kosztem replatforming, rearchitecting i przepisywania kodu.</span><span class="sxs-lookup"><span data-stu-id="da19f-136">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="da19f-137">Jeśli ty i Twój zespół uważacie, że podejście natywne dla chmury jest właściwe, należy zracjonalizować decyzję w organizacji.</span><span class="sxs-lookup"><span data-stu-id="da19f-137">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="da19f-138">Jaki dokładnie jest problem biznesowy, który rozwiąże podejście natywne dla chmury?</span><span class="sxs-lookup"><span data-stu-id="da19f-138">What exactly is the business problem that a cloud-native approach will solve?</span></span> <span data-ttu-id="da19f-139">W jaki sposób będzie to zgodne z potrzebami biznesowymi?</span><span class="sxs-lookup"><span data-stu-id="da19f-139">How would it align with business needs?</span></span>

- <span data-ttu-id="da19f-140">Szybkie wydania funkcji ze zwiększoną pewnością siebie?</span><span class="sxs-lookup"><span data-stu-id="da19f-140">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="da19f-141">Skalowalność drobnoziarnista - bardziej efektywne wykorzystanie zasobów?</span><span class="sxs-lookup"><span data-stu-id="da19f-141">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="da19f-142">Zwiększona odporność systemu?</span><span class="sxs-lookup"><span data-stu-id="da19f-142">Improved system resiliency?</span></span>

- <span data-ttu-id="da19f-143">Poprawiono wydajność systemu?</span><span class="sxs-lookup"><span data-stu-id="da19f-143">Improved system performance?</span></span>

- <span data-ttu-id="da19f-144">Większy wgląd w operacje?</span><span class="sxs-lookup"><span data-stu-id="da19f-144">More visibility into operations?</span></span>

- <span data-ttu-id="da19f-145">Łączenie platform programistów i magazynów danych, aby uzyskać najlepsze narzędzie do pracy?</span><span class="sxs-lookup"><span data-stu-id="da19f-145">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="da19f-146">Przyszłościowa inwestycja w aplikację?</span><span class="sxs-lookup"><span data-stu-id="da19f-146">Future-proof application investment?</span></span>

<span data-ttu-id="da19f-147">Właściwa strategia migracji zależy od priorytetów organizacyjnych i systemów, na które kierujesz reklamy.</span><span class="sxs-lookup"><span data-stu-id="da19f-147">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="da19f-148">Dla wielu osób optymalizacja monolitycznej aplikacji w chmurze lub dodawanie usług gruboziarnistych do aplikacji n-warstwowej może być bardziej opłacalna.</span><span class="sxs-lookup"><span data-stu-id="da19f-148">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="da19f-149">W takich przypadkach nadal można w pełni korzystać z funkcji paaS w chmurze, takich jak te oferowane przez usługę Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="da19f-149">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="da19f-150">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="da19f-150">Summary</span></span>

<span data-ttu-id="da19f-151">W tym rozdziale wprowadziliśmy przetwarzanie natywne dla chmury.</span><span class="sxs-lookup"><span data-stu-id="da19f-151">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="da19f-152">Udostępniliśmy definicję wraz z kluczowymi funkcjami, które napędzają aplikację natywną dla chmury.</span><span class="sxs-lookup"><span data-stu-id="da19f-152">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="da19f-153">Przyjrzeliśmy się rodzajom wniosków, które mogą uzasadniać tę inwestycję i wysiłek.</span><span class="sxs-lookup"><span data-stu-id="da19f-153">We looked at the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="da19f-154">Wraz z wprowadzeniem za, teraz zanurzyć się w znacznie bardziej szczegółowe spojrzenie na natywnych chmury.</span><span class="sxs-lookup"><span data-stu-id="da19f-154">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="da19f-155">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="da19f-155">References</span></span>

- [<span data-ttu-id="da19f-156">Cloud Native Computing Foundation</span><span class="sxs-lookup"><span data-stu-id="da19f-156">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="da19f-157">Mikrousług .NET: Architektura konteneryzowanych aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="da19f-157">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="da19f-158">Modernizuj istniejące aplikacje platformy .NET za pomocą chmury Azure i kontenerów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="da19f-158">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="da19f-159">Cloud Native Patterns przez Cornelia Davis</span><span class="sxs-lookup"><span data-stu-id="da19f-159">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="da19f-160">Poza zastosowaniem dwunastoceli factor</span><span class="sxs-lookup"><span data-stu-id="da19f-160">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="da19f-161">Co to jest infrastruktura jako kod</span><span class="sxs-lookup"><span data-stu-id="da19f-161">What is Infrastructure as Code</span></span>](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="da19f-162">Mikro wdrożenie Uber Engineering: codzienne wdrażanie z ufnością</span><span class="sxs-lookup"><span data-stu-id="da19f-162">Uber Engineering's Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="da19f-163">Jak netflix wdraża kod</span><span class="sxs-lookup"><span data-stu-id="da19f-163">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="da19f-164">Kontrola przeciążenia do skalowania mikrousług WeChat</span><span class="sxs-lookup"><span data-stu-id="da19f-164">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
><span data-ttu-id="da19f-165">[Poprzedni](definition.md)
>[następny](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="da19f-165">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>
