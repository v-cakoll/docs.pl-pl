---
title: Monitorowanie usług konteneryzowanych aplikacji
description: Poznaj niektóre kluczowe aspekty monitorowania architektur kontenerów
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295620"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="41114-103">Monitorowanie usług konteneryzowanych aplikacji</span><span class="sxs-lookup"><span data-stu-id="41114-103">Monitor containerized application services</span></span>

<span data-ttu-id="41114-104">Ma kluczowe znaczenie dla aplikacji podzielonych na wiele kontenerów i mikrousług, aby mieć sposób monitorowania i analizowania zachowania całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41114-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="41114-105">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="41114-105">Azure Monitor</span></span>

<span data-ttu-id="41114-106">[Usługa Azure Monitor](https://azure.microsoft.com/services/monitor/) to rozszerzalna usługa analityczna, która monitoruje aplikację na żywo.</span><span class="sxs-lookup"><span data-stu-id="41114-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="41114-107">Pomaga wykrywać i diagnozować problemy z wydajnością oraz zrozumieć, co użytkownicy faktycznie robią z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="41114-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="41114-108">Jest on przeznaczony dla deweloperów, z zamiarem pomaga stale poprawić wydajność i użyteczność usług lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41114-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="41114-109">Usługa Azure Monitor współpracuje zarówno z usługami sieci web/services, jak i aplikacjami autonomicznymi na wielu różnych platformach, takich jak .NET, Java, Node.js i wiele innych platform, hostowanych lokalnie lub w chmurze.</span><span class="sxs-lookup"><span data-stu-id="41114-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="41114-110">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="41114-110">Additional resources</span></span>

- <span data-ttu-id="41114-111">**Omówienie usługi Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="41114-111">**Overview of Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="41114-112">**Co to jest usługa Application Insights?**</span><span class="sxs-lookup"><span data-stu-id="41114-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="41114-113">**Co to są metryki usługi Azure Monitor?**</span><span class="sxs-lookup"><span data-stu-id="41114-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="41114-114">**Rozwiązanie do monitorowania kontenerów w usłudze Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="41114-114">**Container Monitoring solution in Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="41114-115">Usługi zabezpieczeń i tworzenia kopii zapasowych</span><span class="sxs-lookup"><span data-stu-id="41114-115">Security and backup services</span></span>

<span data-ttu-id="41114-116">Istnieje wiele obowiązków pomocy technicznej z dużą ilością szczegółów, które trzeba obsługiwać, aby upewnić się, że aplikacje i infrastruktura są w najwyższej kondycji do obsługi potrzeb biznesowych, a sytuacja staje się bardziej skomplikowana w dziedzinie mikrousług, więc potrzebujesz sposobu, aby mają zarówno widoki wysokiego, jak i szczegółowe, gdy trzeba podjąć działania.</span><span class="sxs-lookup"><span data-stu-id="41114-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="41114-117">Platforma Azure oferuje narzędzia do zarządzania i zapewnienia ujednoliconego widoku czterech krytycznych aspektów zarówno zasobów chmurowych, jak i lokalnych:</span><span class="sxs-lookup"><span data-stu-id="41114-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="41114-118">**Zabezpieczenia**.</span><span class="sxs-lookup"><span data-stu-id="41114-118">**Security**.</span></span> <span data-ttu-id="41114-119">Z [centrum zabezpieczeń platformy Azure](https://azure.microsoft.com/services/security-center/).</span><span class="sxs-lookup"><span data-stu-id="41114-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="41114-120">Uzyskaj pełną widoczność i kontrolę nad bezpieczeństwem maszyn wirtualnych, aplikacji i obciążeń.</span><span class="sxs-lookup"><span data-stu-id="41114-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="41114-121">Scentralizuj zarządzanie zasadami zabezpieczeń i zintegruj istniejące procesy i narzędzia.</span><span class="sxs-lookup"><span data-stu-id="41114-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="41114-122">Wykrywaj realne zagrożenia za pomocą zaawansowanych analiz.</span><span class="sxs-lookup"><span data-stu-id="41114-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="41114-123">**Kopia zapasowa**.</span><span class="sxs-lookup"><span data-stu-id="41114-123">**Backup**.</span></span> <span data-ttu-id="41114-124">Z [kopią zapasową platformy Azure](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="41114-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="41114-125">Unikaj kosztownych przerw w działalności, osiągaj cele w zakresie zgodności i chroń swoje dane przed oprogramowaniem wymuszającym okup i błędami ludzkimi.</span><span class="sxs-lookup"><span data-stu-id="41114-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="41114-126">Dane kopii zapasowej zaszyfruj podczas przesyłania i spoczynku.</span><span class="sxs-lookup"><span data-stu-id="41114-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="41114-127">Zapewnij dostęp na podstawie uwierzytelniania wieloskładnikowego, aby zapobiec nieautoryzowanemu użyciu.</span><span class="sxs-lookup"><span data-stu-id="41114-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="41114-128">**Zasoby lokalne**.</span><span class="sxs-lookup"><span data-stu-id="41114-128">**On-premises resources**.</span></span> <span data-ttu-id="41114-129">Z [prawdziwie spójną chmurą hybrydową.](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/)</span><span class="sxs-lookup"><span data-stu-id="41114-129">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="41114-130">[Poprzedni](manage-production-docker-environments.md)
>[następny](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="41114-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
