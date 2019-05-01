---
title: Monitorowanie usług konteneryzowanych aplikacji
description: Dowiedz się, niektóre kluczowe aspekty monitorowania kontenera architektury
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 4553a35c8db6cfc46187525ef2ffc65cb3ba07c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922749"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="88a1b-103">Monitorowanie usług konteneryzowanych aplikacji</span><span class="sxs-lookup"><span data-stu-id="88a1b-103">Monitor containerized application services</span></span>

<span data-ttu-id="88a1b-104">Koniecznie dla aplikacji, podzielić na wiele kontenerów oraz mikrousług sposób monitorowanie i analizowanie zachowanie całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="88a1b-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="88a1b-105">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="88a1b-105">Azure Monitor</span></span>

<span data-ttu-id="88a1b-106">[Usługa Azure Monitor](https://azure.microsoft.com/services/monitor/) jest rozszerzalną usługą analizy, który monitoruje działającą aplikację.</span><span class="sxs-lookup"><span data-stu-id="88a1b-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="88a1b-107">Pomaga wykrywać i diagnozować problemy z wydajnością i zrozumienie, jak użytkownicy w rzeczywistości korzystają z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="88a1b-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="88a1b-108">Jest ona przeznaczona dla deweloperów z zamiarem pomaga usprawnić wydajność i użyteczność swoje aplikacje lub usługi.</span><span class="sxs-lookup"><span data-stu-id="88a1b-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="88a1b-109">Usługa Azure Monitor współpracuje z zarówno autonomiczne, jak i usług sieci web/aplikacji na różnych platformach, takich jak .NET, Java, Node.js i wielu innych platform hostowanych lokalnie lub w chmurze.</span><span class="sxs-lookup"><span data-stu-id="88a1b-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="88a1b-110">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="88a1b-110">Additional resources</span></span>

- <span data-ttu-id="88a1b-111">**Omówienie usługi Azure Monitor** \\</span><span class="sxs-lookup"><span data-stu-id="88a1b-111">**Overview of Azure Monitor** \\</span></span>
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="88a1b-112">**Co to jest usługa Application Insights?**</span><span class="sxs-lookup"><span data-stu-id="88a1b-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="88a1b-113">**Co to jest Azure monitorowanie metryk?**</span><span class="sxs-lookup"><span data-stu-id="88a1b-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="88a1b-114">**Rozwiązanie do monitorowania kontenerów w usłudze Azure Monitor** \\</span><span class="sxs-lookup"><span data-stu-id="88a1b-114">**Container Monitoring solution in Azure Monitor** \\</span></span>
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="88a1b-115">Usługi zabezpieczeń i kopii zapasowej</span><span class="sxs-lookup"><span data-stu-id="88a1b-115">Security and backup services</span></span>

<span data-ttu-id="88a1b-116">Istnieje wiele zadań pomocy technicznej z dużą liczbą szczegółowe informacje, które trzeba obsługiwać, aby upewnić się, że infrastruktura i aplikacje znajdują się w górnym więcej warunek do obsługi wymagań biznesowych i sytuacji staje się bardziej skomplikowane, w obszarze mikrousług, więc należy sposób ma wysokiego poziomu i szczegółowe widoki, gdy trzeba podjąć działania.</span><span class="sxs-lookup"><span data-stu-id="88a1b-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="88a1b-117">Platforma Azure oferuje narzędzia do zarządzania i zapewnić spójny widok cztery krytyczne aspekty w chmurze i lokalnych zasobów:</span><span class="sxs-lookup"><span data-stu-id="88a1b-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="88a1b-118">**Zabezpieczenia**.</span><span class="sxs-lookup"><span data-stu-id="88a1b-118">**Security**.</span></span> <span data-ttu-id="88a1b-119">Za pomocą [usługi Azure Security Center](https://azure.microsoft.com/services/security-center/).</span><span class="sxs-lookup"><span data-stu-id="88a1b-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="88a1b-120">Uzyskaj pełną widoczność i kontrolę nad ich zabezpieczeniami maszyn wirtualnych, aplikacji i obciążeń.</span><span class="sxs-lookup"><span data-stu-id="88a1b-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="88a1b-121">Scentralizuj Zarządzanie swoimi zasadami zabezpieczeń oraz Zintegruj istniejące procesy i narzędzia.</span><span class="sxs-lookup"><span data-stu-id="88a1b-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="88a1b-122">Wykrywaj rzeczywiste zagrożenia za pomocą zaawansowanych analiz.</span><span class="sxs-lookup"><span data-stu-id="88a1b-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="88a1b-123">**Kopia zapasowa**.</span><span class="sxs-lookup"><span data-stu-id="88a1b-123">**Backup**.</span></span> <span data-ttu-id="88a1b-124">Za pomocą [usługa Azure Backup](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="88a1b-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="88a1b-125">Unikaj firm kosztownych przerw w działaniu, cele zapewniania zgodności i chronić dane przed oprogramowaniem wymuszającym okup i błędami ludzkimi.</span><span class="sxs-lookup"><span data-stu-id="88a1b-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="88a1b-126">Zachowaj dane kopii zapasowej szyfrowane podczas przesyłania i magazynowanych.</span><span class="sxs-lookup"><span data-stu-id="88a1b-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="88a1b-127">Zapewnia dostęp na podstawie uwierzytelniania wieloskładnikowego, aby zapobiec nieautoryzowanemu użyciu.</span><span class="sxs-lookup"><span data-stu-id="88a1b-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="88a1b-128">**Zasobów lokalnych**.</span><span class="sxs-lookup"><span data-stu-id="88a1b-128">**On-premises resources**.</span></span> <span data-ttu-id="88a1b-129">Za pomocą [prawdziwie spójna chmura hybrydowa](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span><span class="sxs-lookup"><span data-stu-id="88a1b-129">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="88a1b-130">[Poprzednie](manage-production-docker-environments.md)
>[dalej](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="88a1b-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
