---
title: Mikrousługi .NET. Architektura konteneryzowanych aplikacji .NET
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Mikrousługi są moduły i niezależnie do wdrożenia usługi. Kontenery platformy docker (dla systemu Linux i Windows) można uprościć wdrażanie i testowanie przez tworzenie pakietów usługi i jego zależności w pojedynczą jednostkę, który następnie jest uruchamiany w środowisku izolowanym.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: 6b57f66068409ade24eecff636b9dd3f4084fd71
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516154"
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="a1029-105">Mikrousługi .NET.</span><span class="sxs-lookup"><span data-stu-id="a1029-105">.NET Microservices.</span></span> <span data-ttu-id="a1029-106">Architektura konteneryzowanych aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="a1029-106">Architecture for Containerized .NET Applications</span></span>

<span data-ttu-id="a1029-107">Pobierz dostępne pod adresem: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="a1029-107">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="a1029-108">OPUBLIKOWANE PRZEZ</span><span class="sxs-lookup"><span data-stu-id="a1029-108">PUBLISHED BY</span></span>

<span data-ttu-id="a1029-109">Zespoły produktu Microsoft Developer Division, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a1029-109">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="a1029-110">Dzielenie firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="a1029-110">A division of Microsoft Corporation</span></span>

<span data-ttu-id="a1029-111">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="a1029-111">One Microsoft Way</span></span>

<span data-ttu-id="a1029-112">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="a1029-112">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="a1029-113">Copyright © 2018 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="a1029-113">Copyright © 2018 by Microsoft Corporation</span></span>

<span data-ttu-id="a1029-114">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="a1029-114">All rights reserved.</span></span> <span data-ttu-id="a1029-115">Nie części zawartości tej książki może odtworzyć lub przenoszone w jakiejkolwiek formie lub za pomocą jakichkolwiek środków bez pisemnej zgody wydawcy.</span><span class="sxs-lookup"><span data-stu-id="a1029-115">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="a1029-116">Ten podręcznik jest dostarczany "jako — jest" i wyraża, widoki i opinie od autora.</span><span class="sxs-lookup"><span data-stu-id="a1029-116">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="a1029-117">Widoki, opinie i informacje wyrażone w tym podręczniku, w tym adresy URL i inne odnośniki do witryn internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="a1029-117">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="a1029-118">Niektóre przedstawione przykłady znajdują się wyłącznie do celów informacyjnych i są fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="a1029-118">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="a1029-119">Nie rzeczywiste skojarzenia ani powiązania nie są zamierzone ani powinny być zakładane.</span><span class="sxs-lookup"><span data-stu-id="a1029-119">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="a1029-120">Firma Microsoft i znaków towarowych, opisane w temacie http://www.microsoft.com na stronie sieci Web "Znakami" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a1029-120">Microsoft and the trademarks listed at http://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="a1029-121">Komputery Mac i z systemem macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="a1029-121">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="a1029-122">Logo whale platformy Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używane przez uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="a1029-122">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="a1029-123">Wszystkie inne znaki i logo są własnością ich prawnych właścicieli.</span><span class="sxs-lookup"><span data-stu-id="a1029-123">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="a1029-124">Współautorzy:</span><span class="sxs-lookup"><span data-stu-id="a1029-124">Co-Authors:</span></span>

> <span data-ttu-id="a1029-125">**Torre'a de la Cesarowi**, Stanowisko kierownicze wyższego PM, zespół produktu platformy .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="a1029-125">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="a1029-126">**Bill Wagnera**, Stanowisko kierownicze wyższego Deweloper zawartości C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="a1029-126">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="a1029-127">**Mike Rousos**, inżynier ds. oprogramowania jednostki, zespołu DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="a1029-127">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="a1029-128">Edytory:</span><span class="sxs-lookup"><span data-stu-id="a1029-128">Editors:</span></span>

> <span data-ttu-id="a1029-129">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="a1029-129">**Mike Pope**</span></span>
>
> <span data-ttu-id="a1029-130">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="a1029-130">**Steve Hoag**</span></span>

<span data-ttu-id="a1029-131">Uczestnicy i osób dokonujących przeglądu:</span><span class="sxs-lookup"><span data-stu-id="a1029-131">Participants and reviewers:</span></span>

> <span data-ttu-id="a1029-132">**Jeffrey Richter**, rozwoju oprogramowania partnerem, zespół platformy Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="a1029-132">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="a1029-133">**Jimmy Bogard**, Dyrektor ds. architektury w Headspring</span><span class="sxs-lookup"><span data-stu-id="a1029-133">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="a1029-134">**Udi Dahan**, założyciel i Dyrektor Generalny, konkretnego oprogramowania</span><span class="sxs-lookup"><span data-stu-id="a1029-134">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="a1029-135">**Jimmy Nilsson**, współzałożyciel i Dyrektor Generalny firmy z Factor10</span><span class="sxs-lookup"><span data-stu-id="a1029-135">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="a1029-136">**Glenn Condron**, Stanowisko kierownicze wyższego Menedżer programu, zespół programu ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a1029-136">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="a1029-137">**Oznacz Fussell**, Kierownik jednostki PM, zespół usługi Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="a1029-137">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="a1029-138">**Diego Vega**, kierownik PM, platformy Entity Framework zespołu firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="a1029-138">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="a1029-139">**Marcin Dorrans**, Stanowisko kierownicze wyższego Menedżer programów zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a1029-139">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="a1029-140">**Rowan Miller**, Sr. Menedżer programów firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="a1029-140">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="a1029-141">**Ankit Asthana**, główny menedżer PM, zespołem platformy .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="a1029-141">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="a1029-142">**Scott Hunter**, Dyrektor ds. partnerów PM, zespołem platformy .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="a1029-142">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="a1029-143">**Dylan Reisenberger**, architekt i Kierownik Dev w Polly</span><span class="sxs-lookup"><span data-stu-id="a1029-143">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="a1029-144">**Steve Smith**, wytwarzającym oprogramowanie & Trainer na ASPSmith Ltd.</span><span class="sxs-lookup"><span data-stu-id="a1029-144">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="a1029-145">**Ian Cooper**, kodowania architektury w Brighter</span><span class="sxs-lookup"><span data-stu-id="a1029-145">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="a1029-146">**Unai Zorrilla**, architekt i Kierownik Dev w Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="a1029-146">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="a1029-147">**Tomasowi EDUARD**, kierownictwo Dev Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="a1029-147">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="a1029-148">**Tomasowi Ramon**, deweloper pracujący u Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="a1029-148">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="a1029-149">**David Sanz**, deweloper pracujący u Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="a1029-149">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="a1029-150">**Javier Valero**, Dyrektor operacyjny ds. na rozwiązanie Grupo</span><span class="sxs-lookup"><span data-stu-id="a1029-150">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="a1029-151">**Pierre proso**, Stanowisko kierownicze wyższego Consultant, Microsoft</span><span class="sxs-lookup"><span data-stu-id="a1029-151">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="a1029-152">**Michael Friis**, Menedżer produktu, Inc platformy Docker</span><span class="sxs-lookup"><span data-stu-id="a1029-152">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="a1029-153">**Charles Lowell**, inżynier ds. oprogramowania, zespołu CAT programu VS, Microsoft</span><span class="sxs-lookup"><span data-stu-id="a1029-153">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="a1029-154">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="a1029-154">Introduction</span></span>

<span data-ttu-id="a1029-155">Przedsiębiorstwa są coraz bardziej zawierającemu oszczędności kosztów, rozwiązywania problemów z wdrażaniem i poprawy operacje operacji deweloperskich i produkcyjnych przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="a1029-155">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="a1029-156">Microsoft ma zostały udostępnia innowacje kontenera dla Windows i Linux, tworząc produktów, takich jak Azure Container Service i Azure Service Fabric i Zostań partnerem liderów branży, takich jak Docker, Mesosphere i Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="a1029-156">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="a1029-157">Te produkty dostarczanie rozwiązań do obsługi kontenerów, które ułatwiają tworzenie i wdrażanie aplikacji w chmurze prędkość i skalę, niezależnie od wybranych przez nich platformy lub narzędzia.</span><span class="sxs-lookup"><span data-stu-id="a1029-157">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="a1029-158">Docker staje się de facto standardem w branży kontenera, obsługiwane przez najważniejszych dostawców w ekosystemów Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="a1029-158">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="a1029-159">(Firma Microsoft jest jeden z dostawców chmury głównego obsługi platformy Docker). W przyszłości Docker prawdopodobnie będzie wszechobecne w dowolnych centrach danych w chmurze lub lokalnie.</span><span class="sxs-lookup"><span data-stu-id="a1029-159">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="a1029-160">Ponadto [mikrousług](https://martinfowler.com/articles/microservices.html) architektury jest pojawiających się jako ważne podejście do rozproszonych aplikacji o kluczowym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="a1029-160">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="a1029-161">W przypadku opartych na mikrousługach architektury aplikacji bazuje na zbiór usług, które mogą być tworzone, przetestowane, wdrożone i kontrolą wersji niezależnie.</span><span class="sxs-lookup"><span data-stu-id="a1029-161">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="a1029-162">Przewodnik — informacje</span><span class="sxs-lookup"><span data-stu-id="a1029-162">About this guide</span></span>

<span data-ttu-id="a1029-163">Ten przewodnik stanowi wprowadzenie do tworzenia aplikacji opartych na mikrousługach i zarządzanie nimi przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="a1029-163">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="a1029-164">Omówiono w nim kwestie projektowania architektonicznego i zbliża się do wdrożenia przy użyciu platformy .NET Core i kontenerów rozwiązania Docker.</span><span class="sxs-lookup"><span data-stu-id="a1029-164">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="a1029-165">Aby ułatwić rozpoczęcie korzystania z kontenerów i mikrousług, przewodnik koncentruje się na odwołanie kontenerowych nimi i aplikacji opartych na mikrousługach, która pozwala zapoznać się z.</span><span class="sxs-lookup"><span data-stu-id="a1029-165">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="a1029-166">Przykładowa aplikacja jest dostępna w [ramach aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="a1029-166">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="a1029-167">Ten przewodnik zawiera podstawowe rozwoju i wskazówki dotyczące architektury, przede wszystkim na poziomie środowiska programowania skupiając się na dwie technologie: platforma Docker i platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a1029-167">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="a1029-168">Zamierzone jest, że przeczytaniem tego przewodnika, jeśli zastanawiasz się nad projektu aplikacji bez konieczności zajmowania się infrastrukturą (w chmurze lub lokalnie) środowiska produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="a1029-168">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="a1029-169">Będzie decyzje dotyczące infrastruktury później, podczas tworzenia aplikacji gotowych do produkcji.</span><span class="sxs-lookup"><span data-stu-id="a1029-169">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="a1029-170">W związku z tym ten przewodnik jest przeznaczony jako niezależny od infrastruktury bardziej rozwoju środowiska — skoncentrowane na.</span><span class="sxs-lookup"><span data-stu-id="a1029-170">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="a1029-171">Po mają materiałami tego przewodnika, następnym krokiem jest więcej informacji na temat mikrousług gotowe do produkcji w systemie Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="a1029-171">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="a1029-172">Co ten przewodnik nie obejmuje</span><span class="sxs-lookup"><span data-stu-id="a1029-172">What this guide does not cover</span></span>

<span data-ttu-id="a1029-173">Ten przewodnik koncentruje się na cykl życia aplikacji, infrastruktury DevOps i potoków ciągłej integracji/ciągłego wdrażania lub pracy zespołu.</span><span class="sxs-lookup"><span data-stu-id="a1029-173">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="a1029-174">Przewodnik uzupełniający [kontenerowych nimi Docker cyklem życia aplikacji za pomocą platformy firmy Microsoft i narzędzi](https://aka.ms/dockerlifecycleebook) koncentruje się na ten temat.</span><span class="sxs-lookup"><span data-stu-id="a1029-174">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="a1029-175">Przewodnik bieżącego nie udostępniają szczegółów implementacji w infrastrukturze platformy Azure, takich jak informacje o określonych koordynatorów.</span><span class="sxs-lookup"><span data-stu-id="a1029-175">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a1029-176">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="a1029-176">Additional resources</span></span>

-   <span data-ttu-id="a1029-177">**Kontenerowych nimi cykl życia aplikacji platformy Docker przy użyciu platformy firmy Microsoft i narzędzi** (do pobrania Książka elektroniczna) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="a1029-177">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="a1029-178">Kto powinien używać tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="a1029-178">Who should use this guide</span></span>

<span data-ttu-id="a1029-179">Napisaliśmy ten przewodnik dla deweloperów i architektów rozwiązań, którzy są nowe, do tworzenia aplikacji opartych na platformie Docker i opartych na mikrousługach architektury.</span><span class="sxs-lookup"><span data-stu-id="a1029-179">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="a1029-180">Ten przewodnik jest przeznaczony dla możesz Jeśli chcesz dowiedzieć się, jak zaprojektować, projektowania i implementacji aplikacji weryfikacji koncepcji przy użyciu technologii firmy Microsoft (kładąc szczególny nacisk na platformie .NET Core) i z kontenerami aparatu Docker.</span><span class="sxs-lookup"><span data-stu-id="a1029-180">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="a1029-181">Można również znaleźć w przewodniku przydatne, jeśli jesteś osobą podejmującą decyzje techniczne, np. architektury przedsiębiorstwa, który chce architekturę i omówienie technologii przed zdecyduj, jakie podejście do wybrania dla nowych i nowoczesnych aplikacji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="a1029-181">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="a1029-182">Jak używać tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="a1029-182">How to use this guide</span></span>

<span data-ttu-id="a1029-183">Pierwszej części tego przewodnika wprowadza kontenerów platformy Docker, w tym artykule omówiono jak dokonać wyboru między programem.NET Core i .NET Framework jako architektura deweloperska i zawiera omówienie mikrousług.</span><span class="sxs-lookup"><span data-stu-id="a1029-183">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="a1029-184">Ta zawartość jest dla architektów i osób podejmujących decyzje techniczne, potrzebują Przegląd, ale nie potrzebujących kto się skupić na szczegóły implementacji kodu.</span><span class="sxs-lookup"><span data-stu-id="a1029-184">This content is for architects and technical decision makers who want an overview but who do not need to focus on code implementation details.</span></span>

<span data-ttu-id="a1029-185">Druga sekcja przewodnika zaczyna się od [aplikacji opartych na proces programistyczny dla platformy Docker](#ch_dev_process_for_docker_based_apps) sekcji.</span><span class="sxs-lookup"><span data-stu-id="a1029-185">The second part of the guide starts with the [Development process for Docker based applications](#ch_dev_process_for_docker_based_apps) section.</span></span> <span data-ttu-id="a1029-186">Koncentruje się ona na rozwój i mikrousług wzorce dotyczące wdrażania aplikacji przy użyciu platformy .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="a1029-186">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="a1029-187">W tej sekcji będzie najbardziej przydatnych dla deweloperów i architektów, którzy chcą skupić się na kodzie, a także na wzorców i szczegółów implementacji.</span><span class="sxs-lookup"><span data-stu-id="a1029-187">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="a1029-188">Związanych z mikrousług i aplikacji opartych na kontenerach referencyjnej: ramach aplikacji eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="a1029-188">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="a1029-189">Aplikacja w ramach aplikacji eShopOnContainers jest aplikacją odwołania dla platformy .NET Core i mikrousług, który jest przeznaczony do wdrożenia przy użyciu kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="a1029-189">The eShopOnContainers application is a reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="a1029-190">Aplikacja składa się z wiele podsystemów, w tym kilka Sklep internetowy interfejs użytkownika Frontony (aplikacja sieci Web i natywnych aplikacji mobilnych).</span><span class="sxs-lookup"><span data-stu-id="a1029-190">The application consists of multiple subsystems, including several e-store UI front ends (a Web app and a native mobile app).</span></span> <span data-ttu-id="a1029-191">Zawiera także zaplecza mikrousług i kontenerów wszystkich wymaganych operacji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="a1029-191">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="a1029-192">Ten mikrousług i aplikacji opartych na kontenerach kod źródłowy jest typu open source i są dostępne pod adresem [ramach aplikacji eShopOnContainers](https://aka.ms/MicroservicesArchitecture) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="a1029-192">This microservice and container-based application source code is open source and available at the [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) GitHub repo.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="a1029-193">Wyślij nam swoją opinię!</span><span class="sxs-lookup"><span data-stu-id="a1029-193">Send us your feedback!</span></span>

<span data-ttu-id="a1029-194">Napisaliśmy tego przewodnika, aby lepiej zrozumieć architekturę konteneryzowane aplikacje i mikrousług na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="a1029-194">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="a1029-195">Przewodnik i powiązane odwołania aplikacji będzie można rozwijają, więc chętnie poznamy Twoją opinię!</span><span class="sxs-lookup"><span data-stu-id="a1029-195">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="a1029-196">Jeśli masz komentarze na temat sposobu ten przewodnik można zwiększyć, wyślij je do:</span><span class="sxs-lookup"><span data-stu-id="a1029-196">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
[<span data-ttu-id="a1029-197">Next</span><span class="sxs-lookup"><span data-stu-id="a1029-197">Next</span></span>](container-docker-introduction/index.md)
