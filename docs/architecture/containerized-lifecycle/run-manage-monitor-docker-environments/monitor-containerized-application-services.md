---
title: Monitorowanie usług konteneryzowanych aplikacji
description: Poznaj kluczowe aspekty architektury kontenerów monitorowania
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295620"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="45067-103">Monitorowanie usług konteneryzowanych aplikacji</span><span class="sxs-lookup"><span data-stu-id="45067-103">Monitor containerized application services</span></span>

<span data-ttu-id="45067-104">Najważniejsze dla aplikacji, które dzielą się na wiele kontenerów i mikrousług, aby można było monitorować i analizować zachowanie całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45067-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="45067-105">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="45067-105">Azure Monitor</span></span>

<span data-ttu-id="45067-106">[Azure monitor](https://azure.microsoft.com/services/monitor/) to rozszerzalna Usługa analityczna, która monitoruje działającą aplikację.</span><span class="sxs-lookup"><span data-stu-id="45067-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="45067-107">Pomaga wykrywać i diagnozować problemy z wydajnością oraz dowiedzieć się, co użytkownicy faktycznie robią z Twoją aplikacją.</span><span class="sxs-lookup"><span data-stu-id="45067-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="45067-108">Jest on przeznaczony dla deweloperów, z zamiarem ułatwienia ciągłego ulepszania wydajności i użyteczności usług lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45067-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="45067-109">Azure Monitor współpracuje z aplikacjami sieci Web/usług i autonomicznymi wersjami na wielu platformach, takich jak .NET, Java, Node. js i wiele innych platform hostowanych lokalnie lub w chmurze.</span><span class="sxs-lookup"><span data-stu-id="45067-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="45067-110">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="45067-110">Additional resources</span></span>

- <span data-ttu-id="45067-111">**Omówienie Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="45067-111">**Overview of Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="45067-112">**Co to jest usługa Application Insights?**</span><span class="sxs-lookup"><span data-stu-id="45067-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="45067-113">**Co to są metryki Azure Monitor?**</span><span class="sxs-lookup"><span data-stu-id="45067-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="45067-114">**Rozwiązanie do monitorowania kontenerów w Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="45067-114">**Container Monitoring solution in Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="45067-115">Usługi zabezpieczeń i tworzenia kopii zapasowych</span><span class="sxs-lookup"><span data-stu-id="45067-115">Security and backup services</span></span>

<span data-ttu-id="45067-116">Istnieje wiele zadań związanych z pomocą techniczną, które trzeba obsłużyć w celu zapewnienia, że Twoje aplikacje i infrastruktura są w stanie najwyższego poziomu, aby zapewnić obsługę potrzeb firmy, a sytuacja stanie się bardziej skomplikowana w obszarze mikrousług, dlatego konieczna jest metoda muszą mieć widok wysokiego poziomu i szczegółowe, gdy trzeba podjąć działania.</span><span class="sxs-lookup"><span data-stu-id="45067-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="45067-117">Platforma Azure oferuje narzędzia do zarządzania i zapewnienia ujednoliconego widoku czterech krytycznych aspektów zasobów w chmurze i lokalnych:</span><span class="sxs-lookup"><span data-stu-id="45067-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="45067-118">**Zabezpieczenia**.</span><span class="sxs-lookup"><span data-stu-id="45067-118">**Security**.</span></span> <span data-ttu-id="45067-119">Z [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span><span class="sxs-lookup"><span data-stu-id="45067-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="45067-120">Uzyskaj pełny wgląd i kontrolę nad zabezpieczeniami maszyn wirtualnych, aplikacji i obciążeń.</span><span class="sxs-lookup"><span data-stu-id="45067-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="45067-121">Scentralizowanie zarządzania zasadami zabezpieczeń oraz integrowanie istniejących procesów i narzędzi.</span><span class="sxs-lookup"><span data-stu-id="45067-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="45067-122">Wykrywaj prawdziwe zagrożenia dzięki zaawansowanej analizie.</span><span class="sxs-lookup"><span data-stu-id="45067-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="45067-123">**Kopia zapasowa**.</span><span class="sxs-lookup"><span data-stu-id="45067-123">**Backup**.</span></span> <span data-ttu-id="45067-124">Z [Azure Backup](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="45067-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="45067-125">Unikaj kosztownych przerw w działalności biznesowej, Poznaj cele zgodności i Chroń dane przed wirusami i błędami ludzkimi.</span><span class="sxs-lookup"><span data-stu-id="45067-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="45067-126">Przechowuj dane kopii zapasowej w trakcie przesyłania i przechowywania.</span><span class="sxs-lookup"><span data-stu-id="45067-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="45067-127">Upewnij się, że dostęp oparty na uwierzytelnianiu wieloskładnikowym uniemożliwia nieautoryzowane użycie.</span><span class="sxs-lookup"><span data-stu-id="45067-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="45067-128">**Zasoby lokalne**.</span><span class="sxs-lookup"><span data-stu-id="45067-128">**On-premises resources**.</span></span> <span data-ttu-id="45067-129">Dzięki [prawdziwie spójnej chmurze hybrydowej](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span><span class="sxs-lookup"><span data-stu-id="45067-129">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="45067-130">[Poprzedni](manage-production-docker-environments.md)Następny
>[](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="45067-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
