---
title: Aplikacje kandydujące dla chmury natywnej
description: Dowiedz się, które typy aplikacji korzystają z podejścia natywnego w chmurze
author: robvet
ms.date: 05/14/2020
ms.openlocfilehash: b907a17b2351bc4ffe49fd6eb6f5963b209d00db
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614243"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="b6bf8-103">Aplikacje kandydujące dla chmury natywnej</span><span class="sxs-lookup"><span data-stu-id="b6bf8-103">Candidate apps for cloud native</span></span>

<span data-ttu-id="b6bf8-104">Zobacz aplikacje w portfolio.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="b6bf8-105">Ile z nich kwalifikuje się do architektury natywnej w chmurze?</span><span class="sxs-lookup"><span data-stu-id="b6bf8-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="b6bf8-106">Wszystkie?</span><span class="sxs-lookup"><span data-stu-id="b6bf8-106">All of them?</span></span> <span data-ttu-id="b6bf8-107">Być może niektóre?</span><span class="sxs-lookup"><span data-stu-id="b6bf8-107">Perhaps some?</span></span>

<span data-ttu-id="b6bf8-108">W przypadku analizy kosztów/korzyści istnieje dobry szansa, że najprawdopodobniej Obsługa znacznika ceny Hefty musi być natywna w chmurze.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="b6bf8-109">Koszt chmury w chmurze znacznie przekracza wartość biznesową aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="b6bf8-110">Jakiego typu aplikacja może być kandydatem dla natywnej chmury?</span><span class="sxs-lookup"><span data-stu-id="b6bf8-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="b6bf8-111">Strategiczny system przedsiębiorstwa, który musi stale rozwijać możliwości i funkcje biznesowe</span><span class="sxs-lookup"><span data-stu-id="b6bf8-111">Strategic enterprise system that need to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="b6bf8-112">Aplikacja, która wymaga dużej szybkości wydania — z wysokim poziomem pewności</span><span class="sxs-lookup"><span data-stu-id="b6bf8-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="b6bf8-113">System, w którym poszczególne funkcje muszą zostać wydane *bez* pełnego ponownego wdrożenia całego systemu</span><span class="sxs-lookup"><span data-stu-id="b6bf8-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="b6bf8-114">Aplikacja opracowana przez zespoły z doświadczeniem w różnych stosach technologicznych</span><span class="sxs-lookup"><span data-stu-id="b6bf8-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="b6bf8-115">Aplikacja ze składnikami, które muszą być skalowane niezależnie</span><span class="sxs-lookup"><span data-stu-id="b6bf8-115">An application with components that must scale independently</span></span>

<span data-ttu-id="b6bf8-116">Następnie istnieją starsze systemy.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-116">Then there are legacy systems.</span></span> <span data-ttu-id="b6bf8-117">Mimo że chcielibyśmy utworzyć nowe aplikacje, często są odpowiedzialni za modernizację starszych obciążeń, które mają kluczowe znaczenie dla działalności firmy.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="b6bf8-118">W czasie Starsza aplikacja może zostać rozłączona do mikrousług, kontenerów i ostatecznie "replatformowo" do architektury natywnej w chmurze.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="b6bf8-119">Modernizacja starszych aplikacji</span><span class="sxs-lookup"><span data-stu-id="b6bf8-119">Modernizing legacy apps</span></span>

<span data-ttu-id="b6bf8-120">Bezpłatna książka elektroniczna firmy Microsoft umożliwia [modernizację istniejących aplikacji .NET w chmurze platformy Azure i kontenery systemu Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) zapewniają wskazówki dotyczące migrowania obciążeń lokalnych do chmury.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="b6bf8-121">Rysunek 1-10 pokazuje, że dla modernizacji starszych aplikacji nie istnieje jedna, jednokrotna strategia dopasowania.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-121">Figure 1-10 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

![Strategie migracji starszych obciążeń](./media/strategies-for-migrating-legacy-workloads.png)

<span data-ttu-id="b6bf8-123">**Rysunek 1-10**.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-123">**Figure 1-10**.</span></span> <span data-ttu-id="b6bf8-124">Strategie migracji starszych obciążeń</span><span class="sxs-lookup"><span data-stu-id="b6bf8-124">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="b6bf8-125">Wbudowane aplikacje, które nie mają krytycznego znaczenia, korzystają z szybkiej migracji podnoszenia i przesunięć ([gotowej do infrastruktury w chmurze](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)).</span><span class="sxs-lookup"><span data-stu-id="b6bf8-125">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) migration.</span></span> <span data-ttu-id="b6bf8-126">W tym miejscu obciążenie lokalne jest hostowane na maszynie wirtualnej opartej na chmurze bez zmian.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-126">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="b6bf8-127">To podejście używa [modelu IaaS (infrastruktura jako usługa)](https://azure.microsoft.com/overview/what-is-iaas/).</span><span class="sxs-lookup"><span data-stu-id="b6bf8-127">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="b6bf8-128">Platforma Azure oferuje kilka narzędzi, takich jak [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)i [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) , aby ułatwić takie przenoszenie.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-128">Azure includes several tools such as [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) to make such a move easier.</span></span> <span data-ttu-id="b6bf8-129">Chociaż ta strategia może przynieść pewne oszczędności, takie aplikacje zwykle nie zostały zaprojektowane w celu odblokowania i wykorzystania zalet chmury obliczeniowej.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-129">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span>

<span data-ttu-id="b6bf8-130">Monolityczne aplikacje mające kluczowe znaczenie dla korzyści z często biznesowej z rozszerzonej migracji podniesienia i przesunięcia (*zoptymalizowane pod kątem chmury*).</span><span class="sxs-lookup"><span data-stu-id="b6bf8-130">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="b6bf8-131">Takie podejście obejmuje optymalizacje wdrożenia, które umożliwiają korzystanie z kluczowych usług Cloud Services — bez konieczności zmiany podstawowej architektury aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-131">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="b6bf8-132">Na przykład możesz [konteneryzowanie](https://docs.microsoft.com/virtualization/windowscontainers/about/) aplikację i wdrożyć ją w usłudze Orchestrator Containers, takiej jak [usługi Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), omówionej w dalszej części tej książki.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-132">For example, you might [containerize](https://docs.microsoft.com/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="b6bf8-133">W chmurze aplikacja może korzystać z innych usług w chmurze, takich jak bazy danych, kolejki komunikatów, monitorowanie i rozproszone buforowanie.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-133">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="b6bf8-134">Na koniec aplikacje monolityczne, które wykonują strategiczne funkcje korporacyjne, mogą najlepiej korzystać z *natywnych rozwiązań chmurowych* .</span><span class="sxs-lookup"><span data-stu-id="b6bf8-134">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="b6bf8-135">Takie podejście zapewnia elastyczność i szybkość pracy.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-135">This approach provides agility and velocity.</span></span> <span data-ttu-id="b6bf8-136">Jest to jednak koszt przetworzenia platformy, ponownej architektury i ponownego pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-136">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="b6bf8-137">Jeśli ty i Twój zespół uzna, że podejście natywne w chmurze jest odpowiednie, behooves Ci, aby usprawnić podejmowanie decyzji w organizacji.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-137">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="b6bf8-138">Jaki jest dokładnie problem biznesowy, który zostanie rozwiązany przez natywne rozwiązanie w chmurze?</span><span class="sxs-lookup"><span data-stu-id="b6bf8-138">What exactly is the business problem that a cloud-native approach will solve?</span></span> <span data-ttu-id="b6bf8-139">Jak będzie ono wyrównane z potrzebami biznesowymi?</span><span class="sxs-lookup"><span data-stu-id="b6bf8-139">How would it align with business needs?</span></span>

- <span data-ttu-id="b6bf8-140">Szybkie wydania funkcji ze zwiększonym zaufaniem?</span><span class="sxs-lookup"><span data-stu-id="b6bf8-140">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="b6bf8-141">Szczegółowa skalowalność — bardziej wydajne użycie zasobów?</span><span class="sxs-lookup"><span data-stu-id="b6bf8-141">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="b6bf8-142">Zwiększona odporność systemu?</span><span class="sxs-lookup"><span data-stu-id="b6bf8-142">Improved system resiliency?</span></span>

- <span data-ttu-id="b6bf8-143">Lepsza wydajność systemu?</span><span class="sxs-lookup"><span data-stu-id="b6bf8-143">Improved system performance?</span></span>

- <span data-ttu-id="b6bf8-144">Widzisz więcej operacji?</span><span class="sxs-lookup"><span data-stu-id="b6bf8-144">More visibility into operations?</span></span>

- <span data-ttu-id="b6bf8-145">Czy program Blend platform deweloperskich i magazynów danych ma dotrzeć do najlepszego narzędzia dla tego zadania?</span><span class="sxs-lookup"><span data-stu-id="b6bf8-145">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="b6bf8-146">W przyszłości poświadczanie aplikacji?</span><span class="sxs-lookup"><span data-stu-id="b6bf8-146">Future-proof application investment?</span></span>

<span data-ttu-id="b6bf8-147">Właściwa Strategia migracji zależy od priorytetów organizacyjnych i systemów, do których są ukierunkowane.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-147">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="b6bf8-148">Dla wielu z nich może być bardziej opłacalne, aby zoptymalizować aplikację w chmurze lub dodać duże usługi do aplikacji N-warstwowej.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-148">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="b6bf8-149">W takich przypadkach można nadal korzystać z funkcji PaaS w chmurze, takich jak te oferowane przez Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-149">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="b6bf8-150">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="b6bf8-150">Summary</span></span>

<span data-ttu-id="b6bf8-151">W tym rozdziale wprowadziliśmy przetwarzanie natywne w chmurze.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-151">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="b6bf8-152">Firma Microsoft udostępniła definicje wraz z kluczowymi funkcjami, które zapewniają aplikację natywną w chmurze.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-152">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="b6bf8-153">Przeszukamy typy aplikacji, które mogą uzasadniać te inwestycje i nakłady pracy.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-153">We looked at the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="b6bf8-154">Po wprowadzeniu tych informacji szczegółowemy bardziej szczegółowy wgląd w chmurę w chmurze.</span><span class="sxs-lookup"><span data-stu-id="b6bf8-154">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="b6bf8-155">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="b6bf8-155">References</span></span>

- [<span data-ttu-id="b6bf8-156">Natywna platforma obliczeniowa w chmurze</span><span class="sxs-lookup"><span data-stu-id="b6bf8-156">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="b6bf8-157">Mikrousługi platformy .NET: architektura dla kontenerów aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="b6bf8-157">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="b6bf8-158">Modernizacja istniejących aplikacji platformy .NET za pomocą chmury platformy Azure i kontenerów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b6bf8-158">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="b6bf8-159">Natywne wzorce chmury według Cornelia Davis</span><span class="sxs-lookup"><span data-stu-id="b6bf8-159">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="b6bf8-160">Poza aplikacją 12-Składnikową</span><span class="sxs-lookup"><span data-stu-id="b6bf8-160">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="b6bf8-161">Co to jest infrastruktura jako kod</span><span class="sxs-lookup"><span data-stu-id="b6bf8-161">What is Infrastructure as Code</span></span>](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="b6bf8-162">Micro Deploying inżyniera Uber: wdrażanie codziennie z pewnością</span><span class="sxs-lookup"><span data-stu-id="b6bf8-162">Uber Engineering's Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="b6bf8-163">Jak Netflix wdraża kod</span><span class="sxs-lookup"><span data-stu-id="b6bf8-163">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="b6bf8-164">Kontrola przeciążenia na potrzeby skalowania mikrousług WeChat</span><span class="sxs-lookup"><span data-stu-id="b6bf8-164">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
><span data-ttu-id="b6bf8-165">[Poprzedni](definition.md) 
> [Dalej](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="b6bf8-165">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>
