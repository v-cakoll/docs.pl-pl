---
title: Modernizowanie aplikacji za pomocą monitorowania i telemetrii
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Modernizowanie aplikacji za pomocą monitorowania i telemetrii
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: cd54861600127191b852e0a966baae6e0fe7914e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012117"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a><span data-ttu-id="10b22-103">Modernizowanie aplikacji za pomocą monitorowania i telemetrii</span><span class="sxs-lookup"><span data-stu-id="10b22-103">Modernize your apps with monitoring and telemetry</span></span>

<span data-ttu-id="10b22-104">Po uruchomieniu aplikacji w środowisku produkcyjnym, jest krytyczny, że masz szczegółowe dane na temat jaka jest wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="10b22-104">When you run an application in production, it's critical that you have insights about how your application is performing.</span></span> <span data-ttu-id="10b22-105">Czy wykonuje na wysokim poziomie?</span><span class="sxs-lookup"><span data-stu-id="10b22-105">Is it performing at a high level?</span></span> <span data-ttu-id="10b22-106">Użytkownicy pojawiają się błędy, lub jest aplikacją stabilne i niezawodne?</span><span class="sxs-lookup"><span data-stu-id="10b22-106">Are users getting errors, or is the application stable and reliable?</span></span> <span data-ttu-id="10b22-107">Należy zaawansowanego monitorowania wydajności, zaawansowanym alerty i pulpity nawigacyjne, aby mieć pewność, że aplikacja jest dostępne i działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="10b22-107">You need rich performance monitoring, powerful alerting, and dashboards to help ensure that your application is available and performing as expected.</span></span> <span data-ttu-id="10b22-108">Należy również można szybko sprawdzić, czy jest problem, należy określić, ilu klientów dotyczy problem, a następnie przeprowadzić analizę głównej przyczyny problemu i rozwiąż problem.</span><span class="sxs-lookup"><span data-stu-id="10b22-108">You also need to be able to see quickly if there's a problem, determine how many customers are affected, and perform a root-cause analysis to find and fix the issue.</span></span>

## <a name="monitor-your-application-with-application-insights"></a><span data-ttu-id="10b22-109">Monitorowanie aplikacji za pomocą usługi Application Insights</span><span class="sxs-lookup"><span data-stu-id="10b22-109">Monitor your application with Application Insights</span></span>

<span data-ttu-id="10b22-110">Usługa Application Insights jest rozszerzalną usługę zarządzania wydajnością aplikacji (APM) dla deweloperów sieci web, którzy pracują na wielu platformach.</span><span class="sxs-lookup"><span data-stu-id="10b22-110">Application Insights is an extensible Application Performance Management (APM) service for web developers who work on multiple platforms.</span></span> <span data-ttu-id="10b22-111">Umożliwia monitorowanie aplikacji sieci web na żywo.</span><span class="sxs-lookup"><span data-stu-id="10b22-111">Use it to monitor your live web application.</span></span> <span data-ttu-id="10b22-112">Usługa Application Insights automatycznie wykrywa anomalie wydajność.</span><span class="sxs-lookup"><span data-stu-id="10b22-112">Application Insights automatically detects performance anomalies.</span></span> <span data-ttu-id="10b22-113">Obejmuje ona zaawansowane funkcje analityczne narzędzia ułatwiające diagnozowanie problemów i aby lepiej zrozumieć, jak użytkownicy w rzeczywistości korzystają z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="10b22-113">It includes powerful analytics tools to help you diagnose issues, and to help you understand what users actually do with your app.</span></span> <span data-ttu-id="10b22-114">Usługa Application Insights jest przeznaczony do pomagają w ciągłym udoskonalaniu wydajności i użyteczności.</span><span class="sxs-lookup"><span data-stu-id="10b22-114">Application Insights is designed to help you continuously improve performance and usability.</span></span> <span data-ttu-id="10b22-115">Działa to w przypadku aplikacji na różnych platformach, w tym .NET, Node.js i J2EE, czy hostowanych lokalnie lub w chmurze.</span><span class="sxs-lookup"><span data-stu-id="10b22-115">It works for apps on a wide variety of platforms, including .NET, Node.js, and J2EE, whether hosted on-premises or in the cloud.</span></span> <span data-ttu-id="10b22-116">Application Insights integruje się z procesy metodyki DevOps i ma punkty połączenia z szeroką gamą narzędzi programistycznych.</span><span class="sxs-lookup"><span data-stu-id="10b22-116">Application Insights integrates with your DevOps processes, and has connection points to a variety of development tools.</span></span>

<span data-ttu-id="10b22-117">Rysunek 4 – 10 przedstawia przykład sposobu usługi Application Insights monitoruje aplikację, i jak udostępnia te informacje do pulpitu nawigacyjnego.</span><span class="sxs-lookup"><span data-stu-id="10b22-117">Figure 4-10 shows an example of how Application Insights monitors your application and how it surfaces those insights to a dashboard.</span></span>

![Pulpit nawigacyjny monitorowania usługi Application Insights](./media/image10.png)

> <span data-ttu-id="10b22-119">**Rysunek 4 – 10.**</span><span class="sxs-lookup"><span data-stu-id="10b22-119">**Figure 4-10.**</span></span> <span data-ttu-id="10b22-120">Pulpit nawigacyjny monitorowania usługi Application Insights</span><span class="sxs-lookup"><span data-stu-id="10b22-120">Application Insights monitoring dashboard</span></span>

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a><span data-ttu-id="10b22-121">Monitorowanie infrastruktury za pomocą usługi Log Analytics i rozwiązania do monitorowania kontenerów platformy Docker</span><span class="sxs-lookup"><span data-stu-id="10b22-121">Monitor your Docker infrastructure with Log Analytics and its Container Monitoring solution</span></span>

<span data-ttu-id="10b22-122">[Usługa Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) jest częścią [Microsoft Azure ogólnego rozwiązania do monitorowania](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview).</span><span class="sxs-lookup"><span data-stu-id="10b22-122">[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) is part of the [Microsoft Azure overall monitoring solution](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview).</span></span> <span data-ttu-id="10b22-123">Warto również usługi [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview).</span><span class="sxs-lookup"><span data-stu-id="10b22-123">It's also a service in [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview).</span></span> <span data-ttu-id="10b22-124">Usługa log Analytics monitoruje chmury i środowiskach lokalnych (OMS i lokalnych), aby pomóc w zachowaniu dostępności i wydajności.</span><span class="sxs-lookup"><span data-stu-id="10b22-124">Log Analytics monitors cloud and on-premises environments (OMS for on-premises) to help maintain availability and performance.</span></span> <span data-ttu-id="10b22-125">Zbiera ona dane generowane przez zasoby w środowiskach chmurowych i lokalnych oraz inne narzędzia do monitorowania, aby przeprowadzać analizę na podstawie wielu źródeł.</span><span class="sxs-lookup"><span data-stu-id="10b22-125">It collects data generated by resources in your cloud and on-premises environments and from other monitoring tools to provide analysis across multiple sources.</span></span>

<span data-ttu-id="10b22-126">W odniesieniu do dzienników infrastruktury platformy Azure, usługi Log Analytics jako usługi platformy Azure pozyskuje dane dzienników i metryk z innymi usługami platformy Azure (za pośrednictwem [usługi Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), maszyn wirtualnych platformy Azure, kontenery platformy Docker i w środowisku lokalnym lub inne elementy infrastruktury chmury.</span><span class="sxs-lookup"><span data-stu-id="10b22-126">In relation to Azure infrastructure logs, Log Analytics, as an Azure service, ingests log and metric data from other Azure services (via [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure VMs, Docker containers, and on-premises or other cloud infrastructures.</span></span> <span data-ttu-id="10b22-127">Usługa log Analytics oferuje elastyczne wyszukiwania i dzienników out-gotową do analiz na podstawie tych danych.</span><span class="sxs-lookup"><span data-stu-id="10b22-127">Log Analytics offers flexible log search and out-of-the box analytics on top of this data.</span></span> <span data-ttu-id="10b22-128">Zapewnia ona zaawansowanych narzędzi służących do analizowania danych w źródłach, umożliwia złożonych zapytań we wszystkich dzienników i aktywnie może on informować na podstawie określonych warunków.</span><span class="sxs-lookup"><span data-stu-id="10b22-128">It provides rich tools that you can use to analyze data across sources, it allows complex queries across all logs, and it can proactively alert based on specified conditions.</span></span> <span data-ttu-id="10b22-129">Można nawet zbierania niestandardowych danych w centralnym repozytorium usługi Log Analytics, gdzie można wykonywać zapytania i wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="10b22-129">You can even collect custom data in the central Log Analytics repository, where you can query and visualize it.</span></span> <span data-ttu-id="10b22-130">Możesz również korzystać z zalet rozwiązania wbudowanej usługi Log Analytics, aby natychmiast uzyskać wgląd w zabezpieczenia i funkcje infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="10b22-130">You also can take advantage of the Log Analytics built-in solutions to immediately gain insights into the security and functionality of your infrastructure.</span></span>

<span data-ttu-id="10b22-131">Można dostęp do usługi Log Analytics za pośrednictwem portalu pakietu OMS lub witryny Azure portal, które działają w dowolnej przeglądarce, i zapewnia dostęp do ustawień konfiguracji oraz wielu narzędzi służących do analizowania i korzystania z zebranych danych.</span><span class="sxs-lookup"><span data-stu-id="10b22-131">You can access Log Analytics through the OMS portal or the Azure portal, which run in any browser, and provide you with access to configuration settings and multiple tools to analyze and act on collected data.</span></span>

<span data-ttu-id="10b22-132">[Rozwiązanie do monitorowania kontenerów](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) w usłudze Log Analytics ułatwia wyświetlanie i zarządzanie hostów platformy Docker i kontenerów Windows w obrębie jednej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="10b22-132">The [Container Monitoring solution](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) in Log Analytics helps you view and manage your Docker and Windows Container hosts in a single location.</span></span> <span data-ttu-id="10b22-133">To rozwiązanie przedstawia, kontenery, które są uruchomione, jakie obraz kontenera są one uruchamiane i gdzie są uruchomione kontenery.</span><span class="sxs-lookup"><span data-stu-id="10b22-133">The solution shows which containers are running, what container image they're running, and where containers are running.</span></span> <span data-ttu-id="10b22-134">Można wyświetlić szczegółowe informacje inspekcji, włącznie z poleceniami, które są używane z kontenerami.</span><span class="sxs-lookup"><span data-stu-id="10b22-134">You can view detailed audit information, including commands that are being used with containers.</span></span> <span data-ttu-id="10b22-135">Możesz również rozwiązać kontenerów, wyświetlania i przeszukiwania scentralizowanych dzienników, bez konieczności zdalnie wyświetlić hostów platformy Docker lub Windows.</span><span class="sxs-lookup"><span data-stu-id="10b22-135">You also can troubleshoot containers by viewing and searching centralized logs, without needing to remotely view Docker or Windows hosts.</span></span> <span data-ttu-id="10b22-136">Możesz znaleźć kontenerów, które mogą być hałas i korzystanie z nich nadmiar zasobów na hoście.</span><span class="sxs-lookup"><span data-stu-id="10b22-136">You can find containers that might be noisy and consuming excess resources on a host.</span></span> <span data-ttu-id="10b22-137">Ponadto można wyświetlić, scentralizowane procesora CPU, pamięci, magazynu i użycia sieci i informacje o wydajności dla kontenerów.</span><span class="sxs-lookup"><span data-stu-id="10b22-137">Additionally, you can view centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span> <span data-ttu-id="10b22-138">Na komputerach z systemem Windows, można scentralizować i porównać dzienników z systemu Windows Server, Hyper-V i kontenery platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="10b22-138">On computers running Windows, you can centralize and compare logs from Windows Server, Hyper-V, and Docker containers.</span></span> <span data-ttu-id="10b22-139">Rozwiązanie obsługuje następujące koordynatorów kontenerów:</span><span class="sxs-lookup"><span data-stu-id="10b22-139">The solution supports the following container orchestrators:</span></span>

- <span data-ttu-id="10b22-140">Docker Swarm</span><span class="sxs-lookup"><span data-stu-id="10b22-140">Docker Swarm</span></span>

- <span data-ttu-id="10b22-141">DC/OS</span><span class="sxs-lookup"><span data-stu-id="10b22-141">DC/OS</span></span>

- <span data-ttu-id="10b22-142">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="10b22-142">Kubernetes</span></span>

- <span data-ttu-id="10b22-143">Service Fabric</span><span class="sxs-lookup"><span data-stu-id="10b22-143">Service Fabric</span></span>

- <span data-ttu-id="10b22-144">Red Hat OpenShift</span><span class="sxs-lookup"><span data-stu-id="10b22-144">Red Hat OpenShift</span></span>

<span data-ttu-id="10b22-145">Rysunek 4 – 11 przedstawiono relacje między różnymi hostach kontenerów i agentów i OMS.</span><span class="sxs-lookup"><span data-stu-id="10b22-145">Figure 4-11 shows the relationships between various container hosts and agents and OMS.</span></span>

![Rozwiązanie do monitorowania kontenerów analizy dzienników](./media/image11.png)

> <span data-ttu-id="10b22-147">**Rysunek 4 – 11.**</span><span class="sxs-lookup"><span data-stu-id="10b22-147">**Figure 4-11.**</span></span> <span data-ttu-id="10b22-148">Rozwiązanie do monitorowania kontenerów analizy dzienników</span><span class="sxs-lookup"><span data-stu-id="10b22-148">Log Analytics Container Monitoring solution</span></span>

<span data-ttu-id="10b22-149">Można użyć do rozwiązania monitorowanie kontenerów usługi Log Analytics:</span><span class="sxs-lookup"><span data-stu-id="10b22-149">You can use the Log Analytics Container Monitoring solution to:</span></span>

- <span data-ttu-id="10b22-150">Wyświetlone informacje o wszystkich hostach kontenerów w jednej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="10b22-150">See information about all container hosts in a single location.</span></span>

- <span data-ttu-id="10b22-151">Kontenery, które są uruchomione, obrazu są one uruchamiane i gdzie są one uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="10b22-151">Know which containers are running, what image they're running, and where they're running.</span></span>

- <span data-ttu-id="10b22-152">Zobacz dziennik inspekcji dla działań w kontenerach.</span><span class="sxs-lookup"><span data-stu-id="10b22-152">See an audit trail for actions on containers.</span></span>

- <span data-ttu-id="10b22-153">Rozwiązywanie problemów, wyświetlania i przeszukiwania scentralizowanych dzienników bez zdalne logowanie do hostów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="10b22-153">Troubleshoot by viewing and searching centralized logs without remote login to the Docker hosts.</span></span>

- <span data-ttu-id="10b22-154">Znajdź kontenerów, które mogą być "hałaśliwym sąsiadów" i zużywałoby nadmiar zasobów na hoście.</span><span class="sxs-lookup"><span data-stu-id="10b22-154">Find containers that might be "noisy neighbors," and be consuming excess resources on a host.</span></span>

- <span data-ttu-id="10b22-155">Wyświetl scentralizowane procesora CPU, pamięci, magazynu i użycia sieci i informacje o wydajności dla kontenerów.</span><span class="sxs-lookup"><span data-stu-id="10b22-155">View centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="10b22-156">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="10b22-156">Additional resources</span></span>

- <span data-ttu-id="10b22-157">**Omówienie monitorowania na platformie Microsoft Azure**</span><span class="sxs-lookup"><span data-stu-id="10b22-157">**Overview of monitoring in Microsoft Azure**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="10b22-158">**Co to jest usługa Application Insights?**</span><span class="sxs-lookup"><span data-stu-id="10b22-158">**What is Application Insights?**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="10b22-159">**Co to jest usługa Log Analytics?**</span><span class="sxs-lookup"><span data-stu-id="10b22-159">**What is Log Analytics?**</span></span>

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- <span data-ttu-id="10b22-160">**Rozwiązanie do monitorowania kontenerów w usłudze Azure Monitor**</span><span class="sxs-lookup"><span data-stu-id="10b22-160">**Container Monitoring solution in Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- <span data-ttu-id="10b22-161">**Omówienie usługi Azure Monitor**</span><span class="sxs-lookup"><span data-stu-id="10b22-161">**Overview of Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="10b22-162">**Co to jest Operations Management Suite (OMS)?**</span><span class="sxs-lookup"><span data-stu-id="10b22-162">**What is Operations Management Suite (OMS)?**</span></span>

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

- <span data-ttu-id="10b22-163">**Monitorowanie kontenerów systemu Windows Server w usłudze Service Fabric za pomocą pakietu OMS**</span><span class="sxs-lookup"><span data-stu-id="10b22-163">**Monitoring Windows Server containers in Service Fabric with OMS**</span></span>

<https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver>

>[!div class="step-by-step"]
><span data-ttu-id="10b22-164">[Poprzednie](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[dalej](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="10b22-164">[Previous](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Next](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span></span>
