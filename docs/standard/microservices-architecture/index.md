---
title: "Mikrousług .NET. Architektura aplikacji .NET konteneryzowanych"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Wstępne"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 87a4b9f2bb076eccfa79e2951e509a35461ff257
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="c90fb-105">Mikrousług .NET.</span><span class="sxs-lookup"><span data-stu-id="c90fb-105">.NET Microservices.</span></span> <span data-ttu-id="c90fb-106">Architektura aplikacji .NET konteneryzowanych</span><span class="sxs-lookup"><span data-stu-id="c90fb-106">Architecture for Containerized .NET Applications</span></span>

<span data-ttu-id="c90fb-107">Pobierz dostępne pod adresem: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="c90fb-107">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="c90fb-108">OPUBLIKOWANY PRZEZ</span><span class="sxs-lookup"><span data-stu-id="c90fb-108">PUBLISHED BY</span></span>

<span data-ttu-id="c90fb-109">Zespoły produktu Microsoft Developer dzielenia, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c90fb-109">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="c90fb-110">Dział Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="c90fb-110">A division of Microsoft Corporation</span></span>

<span data-ttu-id="c90fb-111">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="c90fb-111">One Microsoft Way</span></span>

<span data-ttu-id="c90fb-112">Redmond, Washington 98052-6399, USA</span><span class="sxs-lookup"><span data-stu-id="c90fb-112">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="c90fb-113">Copyright © 2017 przez firmę Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="c90fb-113">Copyright © 2017 by Microsoft Corporation</span></span>

<span data-ttu-id="c90fb-114">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="c90fb-114">All rights reserved.</span></span> <span data-ttu-id="c90fb-115">Nie części zawartości tej książki może odtworzyć lub przesyłane w jakimkolwiek formularzu, lub w jakikolwiek sposób bez pisemnej zgody wydawcy.</span><span class="sxs-lookup"><span data-stu-id="c90fb-115">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="c90fb-116">Ten podręcznik podano "jako — jest" i odzwierciedla widoków i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="c90fb-116">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="c90fb-117">Widoki, opinie i informacje wyrażone w tej książki, w tym adresy URL i innymi odwołaniami do witryn internetowych, mogą ulec zmianie bez uprzedzenia.</span><span class="sxs-lookup"><span data-stu-id="c90fb-117">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="c90fb-118">Niektóre przedstawione przykłady są udostępniane tylko do celów ilustracyjnych i są fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="c90fb-118">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="c90fb-119">Żadne rzeczywiste skojarzenia ani połączenia jest przeznaczony lub powinny być zakładane.</span><span class="sxs-lookup"><span data-stu-id="c90fb-119">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="c90fb-120">Microsoft i znakami, znajduje się na http://www.microsoft.com na stronie sieci Web "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c90fb-120">Microsoft and the trademarks listed at http://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="c90fb-121">Mac i system macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="c90fb-121">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="c90fb-122">Logo wieloryb Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używany przez uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="c90fb-122">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="c90fb-123">Wszystkie inne znaczniki i logo są własnością ich prawnych właścicieli.</span><span class="sxs-lookup"><span data-stu-id="c90fb-123">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="c90fb-124">Współautorzy:</span><span class="sxs-lookup"><span data-stu-id="c90fb-124">Co-Authors:</span></span>

> <span data-ttu-id="c90fb-125">**Cesarowi de la Torre**, Sr. PM zespołu produktu .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="c90fb-125">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="c90fb-126">**Rachunek Wagnera**, Sr. Deweloper zawartości, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="c90fb-126">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="c90fb-127">**Jan Rousos**, inżynier oprogramowania podmiot zabezpieczeń, zespołu DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c90fb-127">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="c90fb-128">Edytory:</span><span class="sxs-lookup"><span data-stu-id="c90fb-128">Editors:</span></span>

> <span data-ttu-id="c90fb-129">**Jan Pope**</span><span class="sxs-lookup"><span data-stu-id="c90fb-129">**Mike Pope**</span></span>
>
> <span data-ttu-id="c90fb-130">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="c90fb-130">**Steve Hoag**</span></span>

<span data-ttu-id="c90fb-131">Uczestnicy i osoby dokonujące przeglądu:</span><span class="sxs-lookup"><span data-stu-id="c90fb-131">Participants and reviewers:</span></span>

> <span data-ttu-id="c90fb-132">**Jeffrey Ritcher**, Eng oprogramowania partnera, zespół Azure firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="c90fb-132">**Jeffrey Ritcher**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="c90fb-133">**Jimmy Bogard**, architektów główny na Headspring</span><span class="sxs-lookup"><span data-stu-id="c90fb-133">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="c90fb-134">**Udi Dahan**, twórcę i dyrektora generalnego, konkretnego oprogramowania</span><span class="sxs-lookup"><span data-stu-id="c90fb-134">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="c90fb-135">**Jimmy Nilsson**, wspólnej twórcę i Dyrektora Factor10</span><span class="sxs-lookup"><span data-stu-id="c90fb-135">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="c90fb-136">**Glenn Condron**, Sr. Menedżer programów ASP.NET zespołu</span><span class="sxs-lookup"><span data-stu-id="c90fb-136">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="c90fb-137">**Oznacz Fussell**, realizacji PM podmiot zabezpieczeń, zespół Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c90fb-137">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="c90fb-138">**Diego Vega**, realizacji PM, zespołu programu Entity Framework, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c90fb-138">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="c90fb-139">**Marcin Dorrans**, Sr. Menedżer programu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c90fb-139">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="c90fb-140">**Tomaszewski rowan**, Sr. Menedżer programów firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="c90fb-140">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="c90fb-141">**Ankit Asthana**, główny menedżer PM, .NET zespół firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="c90fb-141">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="c90fb-142">**Scott myśliwego**, PM Dyrektor partnera, .NET zespół firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="c90fb-142">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="c90fb-143">**Dylan Reisenberger**, architektów i deweloperów kierownictwo Polly</span><span class="sxs-lookup"><span data-stu-id="c90fb-143">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="c90fb-144">**Steve Smith**, wytwarzającym oprogramowania & Trainer na ASPSmith Ltd.</span><span class="sxs-lookup"><span data-stu-id="c90fb-144">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="c90fb-145">**Ian Cooper**, kodowania projektowania w Brighter</span><span class="sxs-lookup"><span data-stu-id="c90fb-145">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="c90fb-146">**Unai Zorrilla**, architektów i deweloperów kierownictwo zwykły pojęcia</span><span class="sxs-lookup"><span data-stu-id="c90fb-146">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="c90fb-147">**Tomasowi EDUARD**, deweloperów kierownictwo zwykły pojęcia</span><span class="sxs-lookup"><span data-stu-id="c90fb-147">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="c90fb-148">**Tomasowi Ramon**, deweloper pracujący u zwykły pojęcia</span><span class="sxs-lookup"><span data-stu-id="c90fb-148">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="c90fb-149">**Sanz Dominik**, deweloper pracujący u zwykły pojęcia</span><span class="sxs-lookup"><span data-stu-id="c90fb-149">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="c90fb-150">**Javier Valero**, dyrektora operacyjnego urzędnika na rozwiązanie Grupo</span><span class="sxs-lookup"><span data-stu-id="c90fb-150">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="c90fb-151">**Saint-Pierre proso**, Sr. Konsultanta firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="c90fb-151">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="c90fb-152">**Jan Friis**, Menedżer produktu, Inc Docker</span><span class="sxs-lookup"><span data-stu-id="c90fb-152">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="c90fb-153">**Lowell Charlesa**, inżynier oprogramowania, zespołu VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c90fb-153">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="c90fb-154">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="c90fb-154">Introduction</span></span>

<span data-ttu-id="c90fb-155">Przedsiębiorstwa są coraz bardziej realizująca oszczędności, rozwiązywania problemów z wdrażaniem i poprawy DevOps i produkcji operacje przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="c90fb-155">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="c90fb-156">Microsoft ma zostały udostępnia innowacje kontenera systemu Windows i Linux, tworząc produktów, takich jak usługi kontenera platformy Azure i usługi Azure Service Fabric i we współpracy z liderów branżowe, takie jak Docker, Mesosphere i Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c90fb-156">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="c90fb-157">Te produkty dostarczania kontenera rozwiązania, które ułatwiają tworzenie i wdrażanie aplikacji w chmurze szybkość i skalę, niezależnie od siebie platformy lub narzędzi.</span><span class="sxs-lookup"><span data-stu-id="c90fb-157">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="c90fb-158">Docker staje się coraz faktyczne standardowego w branży kontenera, obsługiwanych przez dostawców najbardziej znaczących w ekosystemami systemu Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="c90fb-158">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="c90fb-159">(Microsoft jest jeden z dostawców chmury głównego obsługi Docker). W przyszłości prawdopodobnie będzie wszechobecne w dowolnego centrum danych w chmurze lub lokalnie Docker.</span><span class="sxs-lookup"><span data-stu-id="c90fb-159">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="c90fb-160">Ponadto [mikrousług](https://martinfowler.com/articles/microservices.html) architektury jest pojawiających się jako rozwiązaniem ważne dla aplikacji rozproszonych krytycznym.</span><span class="sxs-lookup"><span data-stu-id="c90fb-160">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="c90fb-161">W architekturze na podstawie mikrousługi aplikacji jest oparty na zbiór usług, które mogą być opracowane, przetestowane, wdrożone i numerów wersji niezależnie.</span><span class="sxs-lookup"><span data-stu-id="c90fb-161">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="c90fb-162">O tym przewodniku</span><span class="sxs-lookup"><span data-stu-id="c90fb-162">About this guide</span></span>

<span data-ttu-id="c90fb-163">Ten przewodnik jest wprowadzenie do tworzenia aplikacji opartych na mikrousług oraz zarządzania nimi przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="c90fb-163">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="c90fb-164">Zawarto informacje projektowania architektonicznego i implementacja zbliża się przy użyciu kontenerów .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="c90fb-164">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="c90fb-165">Aby ułatwić wprowadzenie kontenery i mikrousług przewodnik koncentruje się na odwołanie konteneryzowanych i aplikacji na podstawie mikrousługi Ci poznać platformę.</span><span class="sxs-lookup"><span data-stu-id="c90fb-165">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="c90fb-166">Przykładowa aplikacja jest dostępna w [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="c90fb-166">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="c90fb-167">Ten przewodnik zawiera podstawowych rozwoju i wskazówki architektury przede wszystkim na poziomie środowisko rozwoju nacisk na dwie technologie: Docker i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c90fb-167">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="c90fb-168">Zamierzone jest przeczytaniu tego przewodnika, w przypadku o projektu aplikacji bez koncentrujących się na infrastrukturę (chmurze lub lokalnie) środowiska produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="c90fb-168">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="c90fb-169">Zostanie podejmowaniu decyzji dotyczących infrastruktury później, podczas tworzenia aplikacji gotowych do produkcji.</span><span class="sxs-lookup"><span data-stu-id="c90fb-169">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="c90fb-170">W związku z tym niniejszy przewodnik jest przeznaczony jako infrastruktury o niesprecyzowanym i bardziej programowanie środowiska skoncentrowane na.</span><span class="sxs-lookup"><span data-stu-id="c90fb-170">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="c90fb-171">Po ma badać w tym przewodniku, następnym krokiem jest więcej informacji na temat mikrousług gotowe do produkcji w systemie Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="c90fb-171">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="c90fb-172">Czego ten przewodnik nie obejmuje</span><span class="sxs-lookup"><span data-stu-id="c90fb-172">What this guide does not cover</span></span>

<span data-ttu-id="c90fb-173">Ten przewodnik nie skupić się na cyklu życia aplikacji, metodyki DevOps, potoki CI/CD lub pracy zespołu.</span><span class="sxs-lookup"><span data-stu-id="c90fb-173">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="c90fb-174">Przewodnik uzupełniający [konteneryzowanych cyklem życia aplikacji Docker z platformy firmy Microsoft i narzędziami](https://aka.ms/dockerlifecycleebook) koncentruje się na ten temat.</span><span class="sxs-lookup"><span data-stu-id="c90fb-174">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="c90fb-175">Przewodnik bieżącego również nie szczegółowo wdrożenia infrastruktury platformy Azure, takich jak informacje o określonym orchestrators.</span><span class="sxs-lookup"><span data-stu-id="c90fb-175">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c90fb-176">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="c90fb-176">Additional resources</span></span>

-   <span data-ttu-id="c90fb-177">**Konteneryzowanych cyklem życia aplikacji Docker z platformy firmy Microsoft i narzędziami** (do pobrania Książka elektroniczna) [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="c90fb-177">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="c90fb-178">Kto powinien używać ten przewodnik</span><span class="sxs-lookup"><span data-stu-id="c90fb-178">Who should use this guide</span></span>

<span data-ttu-id="c90fb-179">Napisaliśmy ten przewodnik dla deweloperów i architekci rozwiązań, nowi do tworzenia aplikacji opartych na Docker i architektura oparta na mikrousług.</span><span class="sxs-lookup"><span data-stu-id="c90fb-179">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="c90fb-180">Ten przewodnik jest, aby dowiedzieć się, jak zaprojektować, projektowania i wdrażania aplikacji Weryfikacja koncepcji przy użyciu technologii rozwoju firmy Microsoft (z szczególną uwagę na .NET Core) i z kontenerami Docker.</span><span class="sxs-lookup"><span data-stu-id="c90fb-180">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="c90fb-181">Zostanie również znaleźć przydatne tego przewodnika, jeśli jesteś osobą podejmującą decyzje technicznych, takich jak architekta organizacji, którzy chcą architekturę i omówienie technologii przed zdecyduj, jakie podejście, aby wybrać nowy i nowoczesne aplikacje rozproszone.</span><span class="sxs-lookup"><span data-stu-id="c90fb-181">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="c90fb-182">Jak używać tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="c90fb-182">How to use this guide</span></span>

<span data-ttu-id="c90fb-183">Pierwsza część tego przewodnika wprowadza kontenery Docker omówiono sposób wybrać oprogramowanie .NET Core i .NET Framework jako platforma programistyczna i zawiera omówienie mikrousług.</span><span class="sxs-lookup"><span data-stu-id="c90fb-183">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="c90fb-184">Ta zawartość jest dla architektów i technicznych inne osoby podejmujące decyzje potrzebują Przegląd, ale który nie ma potrzeby skupić się na szczegóły implementacji kodu.</span><span class="sxs-lookup"><span data-stu-id="c90fb-184">This content is for architects and technical decision makers who want an overview but who do not need to focus on code implementation details.</span></span>

<span data-ttu-id="c90fb-185">Rozpoczyna się od drugiej części przewodnika [aplikacji opartych na proces Docker](#ch_dev_process_for_docker_based_apps) sekcji.</span><span class="sxs-lookup"><span data-stu-id="c90fb-185">The second part of the guide starts with the [Development process for Docker based applications](#ch_dev_process_for_docker_based_apps) section.</span></span> <span data-ttu-id="c90fb-186">Głównie wzorce programowania i mikrousługi wdrażania aplikacji przy użyciu platformy .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="c90fb-186">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="c90fb-187">W tej sekcji będzie najbardziej przydatnych dla deweloperów i architektów, którzy mają być fokus na kod i wzorce i szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="c90fb-187">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="c90fb-188">Związane z mikrousługi i aplikacji na podstawie kontenera odwołania: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="c90fb-188">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="c90fb-189">Aplikacja eShopOnContainers jest aplikacja odwołania dla platformy .NET Core i mikrousług przeznaczonego do wdrożenia przy użyciu kontenerów Docker.</span><span class="sxs-lookup"><span data-stu-id="c90fb-189">The eShopOnContainers application is a reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="c90fb-190">Aplikacja składa się z wielu podsystemami, łącznie z kilku Sklep internetowy interfejsu użytkownika frontonu zakończenia (aplikacja sieci Web i natywnych aplikacji mobilnej).</span><span class="sxs-lookup"><span data-stu-id="c90fb-190">The application consists of multiple subsystems, including several e-store UI front ends (a Web app and a native mobile app).</span></span> <span data-ttu-id="c90fb-191">Zawiera także mikrousług zaplecza i kontenerami dla wszystkich wymaganych operacji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="c90fb-191">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="c90fb-192">Ten mikrousługi i aplikacja kontenera kod źródłowy jest typu open source dostępny na [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="c90fb-192">This microservice and container-based application source code is open source and available at the [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub repo.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="c90fb-193">Wyślij nam swoją opinię!</span><span class="sxs-lookup"><span data-stu-id="c90fb-193">Send us your feedback!</span></span>

<span data-ttu-id="c90fb-194">Napisaliśmy tego przewodnika, aby ułatwić zrozumienie architektury konteneryzowanych aplikacji i mikrousług w .NET.</span><span class="sxs-lookup"><span data-stu-id="c90fb-194">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="c90fb-195">Przewodnik i powiązanego odwołania aplikacji będzie można rozwijają, więc chętnie poznamy Twoją opinię!</span><span class="sxs-lookup"><span data-stu-id="c90fb-195">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="c90fb-196">Jeśli masz komentarze na temat sposobu w tym przewodniku można zwiększyć, wyślij je do:</span><span class="sxs-lookup"><span data-stu-id="c90fb-196">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
<span data-ttu-id="c90fb-197">[Next] (kontenera — docker — wprowadzenie/index.md)</span><span class="sxs-lookup"><span data-stu-id="c90fb-197">[Next] (container-docker-introduction/index.md)</span></span>
