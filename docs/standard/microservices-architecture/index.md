---
title: Mikrousług .NET. Architektura aplikacji .NET konteneryzowanych
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Wstępne
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: d4499384d63f11a1d78d0aa84749aed8ea554794
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="de353-104">Mikrousług .NET.</span><span class="sxs-lookup"><span data-stu-id="de353-104">.NET Microservices.</span></span> <span data-ttu-id="de353-105">Architektura aplikacji .NET konteneryzowanych</span><span class="sxs-lookup"><span data-stu-id="de353-105">Architecture for Containerized .NET Applications</span></span>

<span data-ttu-id="de353-106">Pobierz dostępne pod adresem: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="de353-106">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="de353-107">OPUBLIKOWANY PRZEZ</span><span class="sxs-lookup"><span data-stu-id="de353-107">PUBLISHED BY</span></span>

<span data-ttu-id="de353-108">Zespoły produktu Microsoft Developer dzielenia, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="de353-108">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="de353-109">Dział Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="de353-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="de353-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="de353-110">One Microsoft Way</span></span>

<span data-ttu-id="de353-111">Redmond, Washington 98052-6399, USA</span><span class="sxs-lookup"><span data-stu-id="de353-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="de353-112">Copyright © 2017 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="de353-112">Copyright © 2017 by Microsoft Corporation</span></span>

<span data-ttu-id="de353-113">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="de353-113">All rights reserved.</span></span> <span data-ttu-id="de353-114">Nie części zawartości tej książki może odtworzyć lub przesyłane w jakimkolwiek formularzu, lub w jakikolwiek sposób bez pisemnej zgody wydawcy.</span><span class="sxs-lookup"><span data-stu-id="de353-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="de353-115">Ten podręcznik podano "jako — jest" i odzwierciedla widoków i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="de353-115">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="de353-116">Widoki, opinie i informacje wyrażone w tej książki, w tym adresy URL i innymi odwołaniami do witryn internetowych, mogą ulec zmianie bez uprzedzenia.</span><span class="sxs-lookup"><span data-stu-id="de353-116">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="de353-117">Niektóre przedstawione przykłady są udostępniane tylko do celów ilustracyjnych i są fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="de353-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="de353-118">Żadne rzeczywiste skojarzenia ani połączenia jest przeznaczony lub powinny być zakładane.</span><span class="sxs-lookup"><span data-stu-id="de353-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="de353-119">Firma Microsoft i znakami, znajduje się na http://www.microsoft.com na stronie sieci Web "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="de353-119">Microsoft and the trademarks listed at http://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="de353-120">Mac i system macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="de353-120">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="de353-121">Logo wieloryb Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używany przez uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="de353-121">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="de353-122">Wszystkie inne znaczniki i logo są własnością ich prawnych właścicieli.</span><span class="sxs-lookup"><span data-stu-id="de353-122">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="de353-123">Współautorzy:</span><span class="sxs-lookup"><span data-stu-id="de353-123">Co-Authors:</span></span>

> <span data-ttu-id="de353-124">**Cesarowi de la Torre**, Sr. PM zespołu produktu .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="de353-124">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="de353-125">**Rachunek Wagnera**, Sr. Deweloper zawartości, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="de353-125">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="de353-126">**Jan Rousos**, inżynier oprogramowania podmiot zabezpieczeń, zespołu DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="de353-126">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="de353-127">Edytory:</span><span class="sxs-lookup"><span data-stu-id="de353-127">Editors:</span></span>

> <span data-ttu-id="de353-128">**Jan Pope**</span><span class="sxs-lookup"><span data-stu-id="de353-128">**Mike Pope**</span></span>
>
> <span data-ttu-id="de353-129">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="de353-129">**Steve Hoag**</span></span>

<span data-ttu-id="de353-130">Uczestnicy i osoby dokonujące przeglądu:</span><span class="sxs-lookup"><span data-stu-id="de353-130">Participants and reviewers:</span></span>

> <span data-ttu-id="de353-131">**Jeffrey Richter**, Eng oprogramowania partnera, zespół Azure firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="de353-131">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="de353-132">**Jimmy Bogard**, architektów główny na Headspring</span><span class="sxs-lookup"><span data-stu-id="de353-132">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="de353-133">**Udi Dahan**, twórcę i dyrektora generalnego, konkretnego oprogramowania</span><span class="sxs-lookup"><span data-stu-id="de353-133">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="de353-134">**Jimmy Nilsson**, wspólnej twórcę i Dyrektora Factor10</span><span class="sxs-lookup"><span data-stu-id="de353-134">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="de353-135">**Glenn Condron**, Sr. Menedżer programów ASP.NET zespołu</span><span class="sxs-lookup"><span data-stu-id="de353-135">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="de353-136">**Oznacz Fussell**, realizacji PM podmiot zabezpieczeń, zespół Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="de353-136">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="de353-137">**Diego Vega**, realizacji PM, zespołu programu Entity Framework, Microsoft</span><span class="sxs-lookup"><span data-stu-id="de353-137">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="de353-138">**Marcin Dorrans**, Sr. Menedżer programu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="de353-138">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="de353-139">**Rowan Miller**, Sr. Menedżer programów firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="de353-139">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="de353-140">**Ankit Asthana**, główny menedżer PM, .NET zespół firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="de353-140">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="de353-141">**Scott myśliwego**, PM Dyrektor partnera, .NET zespół firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="de353-141">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="de353-142">**Dylan Reisenberger**, architektów i deweloperów kierownictwo Polly</span><span class="sxs-lookup"><span data-stu-id="de353-142">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="de353-143">**Steve Smith**, wytwarzającym oprogramowania & Trainer na ASPSmith Ltd.</span><span class="sxs-lookup"><span data-stu-id="de353-143">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="de353-144">**Ian Cooper**, kodowania projektowania w Brighter</span><span class="sxs-lookup"><span data-stu-id="de353-144">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="de353-145">**Unai Zorrilla**, architektów i deweloperów kierownictwo zwykły pojęcia</span><span class="sxs-lookup"><span data-stu-id="de353-145">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="de353-146">**Tomasowi EDUARD**, deweloperów kierownictwo zwykły pojęcia</span><span class="sxs-lookup"><span data-stu-id="de353-146">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="de353-147">**Tomasowi Ramon**, deweloper pracujący u zwykły pojęcia</span><span class="sxs-lookup"><span data-stu-id="de353-147">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="de353-148">**Sanz Dominik**, deweloper pracujący u zwykły pojęcia</span><span class="sxs-lookup"><span data-stu-id="de353-148">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="de353-149">**Javier Valero**, dyrektora operacyjnego urzędnika na rozwiązanie Grupo</span><span class="sxs-lookup"><span data-stu-id="de353-149">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="de353-150">**Saint-Pierre proso**, Sr. Consultant, Microsoft</span><span class="sxs-lookup"><span data-stu-id="de353-150">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="de353-151">**Jan Friis**, Menedżer produktu, Inc Docker</span><span class="sxs-lookup"><span data-stu-id="de353-151">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="de353-152">**Lowell Charlesa**, inżynier oprogramowania, zespołu VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="de353-152">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="de353-153">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="de353-153">Introduction</span></span>

<span data-ttu-id="de353-154">Przedsiębiorstwa są coraz bardziej realizująca oszczędności, rozwiązywania problemów z wdrażaniem i poprawy DevOps i produkcji operacje przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="de353-154">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="de353-155">Microsoft ma zostały udostępnia innowacje kontenera systemu Windows i Linux, tworząc produktów, takich jak usługi kontenera platformy Azure i usługi Azure Service Fabric i we współpracy z liderów branżowe, takie jak Docker, Mesosphere i Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="de353-155">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="de353-156">Te produkty dostarczania kontenera rozwiązania, które ułatwiają tworzenie i wdrażanie aplikacji w chmurze szybkość i skalę, niezależnie od siebie platformy lub narzędzi.</span><span class="sxs-lookup"><span data-stu-id="de353-156">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="de353-157">Docker staje się coraz faktyczne standardowego w branży kontenera, obsługiwanych przez dostawców najbardziej znaczących w ekosystemami systemu Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="de353-157">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="de353-158">(Microsoft jest jeden z dostawców chmury głównego obsługi Docker). W przyszłości prawdopodobnie będzie wszechobecne w dowolnego centrum danych w chmurze lub lokalnie Docker.</span><span class="sxs-lookup"><span data-stu-id="de353-158">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="de353-159">Ponadto [mikrousług](https://martinfowler.com/articles/microservices.html) architektury jest pojawiających się jako rozwiązaniem ważne dla aplikacji rozproszonych krytycznym.</span><span class="sxs-lookup"><span data-stu-id="de353-159">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="de353-160">W architekturze na podstawie mikrousługi aplikacji jest oparty na zbiór usług, które mogą być opracowane, przetestowane, wdrożone i numerów wersji niezależnie.</span><span class="sxs-lookup"><span data-stu-id="de353-160">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="de353-161">O tym przewodniku</span><span class="sxs-lookup"><span data-stu-id="de353-161">About this guide</span></span>

<span data-ttu-id="de353-162">Ten przewodnik jest wprowadzenie do tworzenia aplikacji opartych na mikrousług oraz zarządzania nimi przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="de353-162">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="de353-163">Zawarto informacje projektowania architektonicznego i implementacja zbliża się przy użyciu kontenerów .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="de353-163">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="de353-164">Aby ułatwić wprowadzenie kontenery i mikrousług przewodnik koncentruje się na odwołanie konteneryzowanych i aplikacji na podstawie mikrousługi Ci poznać platformę.</span><span class="sxs-lookup"><span data-stu-id="de353-164">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="de353-165">Przykładowa aplikacja jest dostępna w [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="de353-165">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="de353-166">Ten przewodnik zawiera podstawowych rozwoju i wskazówki architektury przede wszystkim na poziomie środowisko rozwoju nacisk na dwie technologie: Docker i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="de353-166">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="de353-167">Zamierzone jest przeczytaniu tego przewodnika, w przypadku o projektu aplikacji bez koncentrujących się na infrastrukturę (chmurze lub lokalnie) środowiska produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="de353-167">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="de353-168">Zostanie podejmowaniu decyzji dotyczących infrastruktury później, podczas tworzenia aplikacji gotowych do produkcji.</span><span class="sxs-lookup"><span data-stu-id="de353-168">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="de353-169">W związku z tym niniejszy przewodnik jest przeznaczony jako infrastruktury o niesprecyzowanym i bardziej programowanie środowiska skoncentrowane na.</span><span class="sxs-lookup"><span data-stu-id="de353-169">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="de353-170">Po ma badać w tym przewodniku, następnym krokiem jest więcej informacji na temat mikrousług gotowe do produkcji w systemie Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="de353-170">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="de353-171">Czego ten przewodnik nie obejmuje</span><span class="sxs-lookup"><span data-stu-id="de353-171">What this guide does not cover</span></span>

<span data-ttu-id="de353-172">Ten przewodnik nie skupić się na cyklu życia aplikacji, metodyki DevOps, potoki CI/CD lub pracy zespołu.</span><span class="sxs-lookup"><span data-stu-id="de353-172">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="de353-173">Przewodnik uzupełniający [konteneryzowanych cyklem życia aplikacji Docker z platformy firmy Microsoft i narzędziami](https://aka.ms/dockerlifecycleebook) koncentruje się na ten temat.</span><span class="sxs-lookup"><span data-stu-id="de353-173">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="de353-174">Przewodnik bieżącego również nie szczegółowo wdrożenia infrastruktury platformy Azure, takich jak informacje o określonym orchestrators.</span><span class="sxs-lookup"><span data-stu-id="de353-174">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="de353-175">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="de353-175">Additional resources</span></span>

-   <span data-ttu-id="de353-176">**Konteneryzowanych cyklem życia aplikacji Docker z platformy firmy Microsoft i narzędziami** (do pobrania Książka elektroniczna) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="de353-176">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="de353-177">Kto powinien używać ten przewodnik</span><span class="sxs-lookup"><span data-stu-id="de353-177">Who should use this guide</span></span>

<span data-ttu-id="de353-178">Napisaliśmy ten przewodnik dla deweloperów i architekci rozwiązań, nowi do tworzenia aplikacji opartych na Docker i architektura oparta na mikrousług.</span><span class="sxs-lookup"><span data-stu-id="de353-178">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="de353-179">Ten przewodnik jest, aby dowiedzieć się, jak zaprojektować, projektowania i wdrażania aplikacji Weryfikacja koncepcji przy użyciu technologii rozwoju firmy Microsoft (z szczególną uwagę na .NET Core) i z kontenerami Docker.</span><span class="sxs-lookup"><span data-stu-id="de353-179">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="de353-180">Zostanie również znaleźć przydatne tego przewodnika, jeśli jesteś osobą podejmującą decyzje technicznych, takich jak architekta organizacji, którzy chcą architekturę i omówienie technologii przed zdecyduj, jakie podejście, aby wybrać nowy i nowoczesne aplikacje rozproszone.</span><span class="sxs-lookup"><span data-stu-id="de353-180">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="de353-181">Jak używać tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="de353-181">How to use this guide</span></span>

<span data-ttu-id="de353-182">Pierwsza część tego przewodnika wprowadza kontenery Docker omówiono sposób wybrać oprogramowanie .NET Core i .NET Framework jako platforma programistyczna i zawiera omówienie mikrousług.</span><span class="sxs-lookup"><span data-stu-id="de353-182">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="de353-183">Ta zawartość jest dla architektów i technicznych inne osoby podejmujące decyzje potrzebują Przegląd, ale który nie ma potrzeby skupić się na szczegóły implementacji kodu.</span><span class="sxs-lookup"><span data-stu-id="de353-183">This content is for architects and technical decision makers who want an overview but who do not need to focus on code implementation details.</span></span>

<span data-ttu-id="de353-184">Rozpoczyna się od drugiej części przewodnika [aplikacji opartych na proces Docker](#ch_dev_process_for_docker_based_apps) sekcji.</span><span class="sxs-lookup"><span data-stu-id="de353-184">The second part of the guide starts with the [Development process for Docker based applications](#ch_dev_process_for_docker_based_apps) section.</span></span> <span data-ttu-id="de353-185">Głównie wzorce programowania i mikrousługi wdrażania aplikacji przy użyciu platformy .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="de353-185">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="de353-186">W tej sekcji będzie najbardziej przydatnych dla deweloperów i architektów, którzy mają być fokus na kod i wzorce i szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="de353-186">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="de353-187">Związane z mikrousługi i aplikacji na podstawie kontenera odwołania: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="de353-187">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="de353-188">Aplikacja eShopOnContainers jest aplikacja odwołania dla platformy .NET Core i mikrousług przeznaczonego do wdrożenia przy użyciu kontenerów Docker.</span><span class="sxs-lookup"><span data-stu-id="de353-188">The eShopOnContainers application is a reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="de353-189">Aplikacja składa się z wielu podsystemami, łącznie z kilku Sklep internetowy interfejsu użytkownika frontonu zakończenia (aplikacja sieci Web i natywnych aplikacji mobilnej).</span><span class="sxs-lookup"><span data-stu-id="de353-189">The application consists of multiple subsystems, including several e-store UI front ends (a Web app and a native mobile app).</span></span> <span data-ttu-id="de353-190">Zawiera także mikrousług zaplecza i kontenerami dla wszystkich wymaganych operacji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="de353-190">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="de353-191">Ten mikrousługi i aplikacja kontenera kod źródłowy jest typu open source dostępny na [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="de353-191">This microservice and container-based application source code is open source and available at the [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub repo.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="de353-192">Wyślij nam swoją opinię!</span><span class="sxs-lookup"><span data-stu-id="de353-192">Send us your feedback!</span></span>

<span data-ttu-id="de353-193">Napisaliśmy tego przewodnika, aby ułatwić zrozumienie architektury konteneryzowanych aplikacji i mikrousług w .NET.</span><span class="sxs-lookup"><span data-stu-id="de353-193">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="de353-194">Przewodnik i powiązanego odwołania aplikacji będzie można rozwijają, więc chętnie poznamy Twoją opinię!</span><span class="sxs-lookup"><span data-stu-id="de353-194">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="de353-195">Jeśli masz komentarze na temat sposobu w tym przewodniku można zwiększyć, wyślij je do:</span><span class="sxs-lookup"><span data-stu-id="de353-195">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
<span data-ttu-id="de353-196">[Next] (kontenera — docker — wprowadzenie/index.md)</span><span class="sxs-lookup"><span data-stu-id="de353-196">[Next] (container-docker-introduction/index.md)</span></span>
