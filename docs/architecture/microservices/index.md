---
title: Mikrousług .NET. architektura konteneryzowanych aplikacji .NET
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Mikrousługi są usługi modułowe i niezależnie wdrażalne. Kontenery platformy Docker (dla systemów Linux i Windows) upraszczają wdrażanie i testowanie, łącząc usługę i jej zależności w jedną jednostkę, która jest następnie uruchamiana w odizolowanym środowisku.
ms.date: 01/30/2020
ms.openlocfilehash: 9cdd5556f92e1acde540b647e7b68628a3ecf67f
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988794"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="471f1-105">Mikrousługi .NET: architektura konteneryzowanych aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="471f1-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Okładka książki](./media/cover-small.png)

<span data-ttu-id="471f1-107">**EDITION v3.1** - Zaktualizowano do ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="471f1-107">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="471f1-108">Ten przewodnik jest wprowadzenie do tworzenia aplikacji opartych na mikrousług i zarządzania nimi przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="471f1-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="471f1-109">Omówiono w nim metody projektowania i implementacji architektury przy użyciu kontenerów .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="471f1-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span>

<span data-ttu-id="471f1-110">Aby ułatwić rozpoczęcie pracy, przewodnik koncentruje się na aplikacji konteneryzowanej i opartej na mikrousługach, którą można eksplorować.</span><span class="sxs-lookup"><span data-stu-id="471f1-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="471f1-111">Aplikacja referencyjna jest dostępna w repozytorium [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub.</span><span class="sxs-lookup"><span data-stu-id="471f1-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="471f1-112">Łącza akcji</span><span class="sxs-lookup"><span data-stu-id="471f1-112">Action links</span></span>

- <span data-ttu-id="471f1-113">Ten e-book jest również dostępny w formacie PDF (tylko w wersji angielskiej) [Pobierz](https://aka.ms/microservicesebook)</span><span class="sxs-lookup"><span data-stu-id="471f1-113">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/microservicesebook)</span></span>

- <span data-ttu-id="471f1-114">Klonuj/rozwidli aplikację referencyjną [eShopOnContainers w usłudze GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="471f1-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="471f1-115">Obejrzyj [film wprowadzający na kanale 9](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="471f1-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="471f1-116">Zapoznaj się z [architekturą mikrousług](https://aka.ms/MicroservicesArchitecture) od razu</span><span class="sxs-lookup"><span data-stu-id="471f1-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="471f1-117">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="471f1-117">Introduction</span></span>

<span data-ttu-id="471f1-118">Przedsiębiorstwa coraz częściej zdają sobie sprawę z oszczędności kosztów, rozwiązywania problemów z wdrażaniem oraz ulepszania operacji devops i produkcyjnych przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="471f1-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="471f1-119">Firma Microsoft wypuszcza innowacje kontenerów dla systemów Windows i Linux, tworząc produkty, takie jak usługa Azure Kubernetes i sieć szkieletowa azure, oraz współpracując z liderami branży, takimi jak Docker, Mesosphere i Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="471f1-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="471f1-120">Produkty te dostarczają rozwiązania kontenerowe, które pomagają firmom tworzyć i wdrażać aplikacje w chmurze z szybkością i skalą, niezależnie od ich wyboru platformy lub narzędzi.</span><span class="sxs-lookup"><span data-stu-id="471f1-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="471f1-121">Docker staje się de facto standardem w branży kontenerów, obsługiwanym przez najważniejszych dostawców w ekosystemach windows i linux.</span><span class="sxs-lookup"><span data-stu-id="471f1-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="471f1-122">(Firma Microsoft jest jednym z głównych dostawców chmury obsługujących platformę Docker). W przyszłości docker będzie prawdopodobnie wszechobecne w dowolnym centrum danych w chmurze lub lokalnie.</span><span class="sxs-lookup"><span data-stu-id="471f1-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="471f1-123">Ponadto architektura [mikrousług](https://martinfowler.com/articles/microservices.html) pojawia się jako ważne podejście do rozproszonych aplikacji o znaczeniu krytycznym.</span><span class="sxs-lookup"><span data-stu-id="471f1-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="471f1-124">W architekturze opartej na mikrousługach aplikacja jest oparta na kolekcji usług, które można opracować, przetestować, wdrożyć i wersjona niezależnie.</span><span class="sxs-lookup"><span data-stu-id="471f1-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="471f1-125">O tym przewodniku</span><span class="sxs-lookup"><span data-stu-id="471f1-125">About this guide</span></span>

<span data-ttu-id="471f1-126">Ten przewodnik jest wprowadzenie do tworzenia aplikacji opartych na mikrousług i zarządzania nimi przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="471f1-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="471f1-127">Omówiono w nim metody projektowania i implementacji architektury przy użyciu kontenerów .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="471f1-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="471f1-128">Aby ułatwić rozpoczęcie pracy z kontenerów i mikrousług, przewodnik koncentruje się na odwołanie konteneryzowanych i aplikacji opartych na mikrousługach, które można eksplorować.</span><span class="sxs-lookup"><span data-stu-id="471f1-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="471f1-129">Przykładowa aplikacja jest dostępna w repozytorium [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub.</span><span class="sxs-lookup"><span data-stu-id="471f1-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="471f1-130">Ten przewodnik zawiera podstawowe wskazówki dotyczące rozwoju i architektury przede wszystkim na poziomie środowiska programistycznego z naciskiem na dwie technologie: Docker i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="471f1-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="471f1-131">Naszym zamiarem jest przeczytanie tego przewodnika, gdy myślisz o projekcie aplikacji bez koncentrowania się na infrastrukturze (w chmurze lub lokalnie) środowiska produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="471f1-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="471f1-132">Decyzje dotyczące infrastruktury podejmą później podczas tworzenia aplikacji gotowych do produkcji.</span><span class="sxs-lookup"><span data-stu-id="471f1-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="471f1-133">W związku z tym ten przewodnik ma być niezależny od infrastruktury i bardziej zorientowane na środowisko rozwoju.</span><span class="sxs-lookup"><span data-stu-id="471f1-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="471f1-134">Po zapoznaniu się z tym przewodnikiem następnym krokiem będzie zapoznanie się z mikrousługami gotowymi do produkcji na platformie Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="471f1-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="471f1-135">Wersja</span><span class="sxs-lookup"><span data-stu-id="471f1-135">Version</span></span>

<span data-ttu-id="471f1-136">Ten przewodnik został zmieniony w celu uwzględnienia wersji **.NET Core 3.1** wraz z wieloma dodatkowymi aktualizacjami związanymi z tą samą "falą" technologii (czyli platformy Azure i dodatkowych technologii innych firm) zbiegającą się w czasie z wydaniem .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="471f1-136">This guide has been revised to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="471f1-137">Dlatego wersja książki została również zaktualizowana do wersji **3.1**.</span><span class="sxs-lookup"><span data-stu-id="471f1-137">That’s why the book version has also been updated to version **3.1**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="471f1-138">Co ten przewodnik nie obejmuje</span><span class="sxs-lookup"><span data-stu-id="471f1-138">What this guide does not cover</span></span>

<span data-ttu-id="471f1-139">Ten przewodnik nie koncentruje się na cyklu życia aplikacji, DevOps, potoki ciągłej integracji/ciągłego wdrażania lub pracy zespołowej.</span><span class="sxs-lookup"><span data-stu-id="471f1-139">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="471f1-140">Uzupełniający przewodnik [Konteneryzowany cykl życia aplikacji platformy Docker z platformą i narzędziami firmy Microsoft](https://aka.ms/dockerlifecycleebook) koncentruje się na tym temacie.</span><span class="sxs-lookup"><span data-stu-id="471f1-140">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="471f1-141">Bieżący przewodnik również nie zawiera szczegółów implementacji infrastruktury platformy Azure, takich jak informacje na temat określonych koordynatorów.</span><span class="sxs-lookup"><span data-stu-id="471f1-141">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="471f1-142">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="471f1-142">Additional resources</span></span>

- <span data-ttu-id="471f1-143">**Konteneryzowany cykl życia aplikacji platformy Docker za pomocą platformy Microsoft i narzędzi** (e-book do pobrania)</span><span class="sxs-lookup"><span data-stu-id="471f1-143">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="471f1-144">Kto powinien korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="471f1-144">Who should use this guide</span></span>

<span data-ttu-id="471f1-145">Napisaliśmy ten przewodnik dla deweloperów i architektów rozwiązań, którzy są nowicjuszami w tworzeniu aplikacji opartych na platformie Docker i architekturze opartej na mikrousługach.</span><span class="sxs-lookup"><span data-stu-id="471f1-145">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="471f1-146">Ten przewodnik jest dla Ciebie, jeśli chcesz dowiedzieć się, jak projektować, projektować i implementować aplikacje proof-of-concept za pomocą technologii programisty firmy Microsoft (ze szczególnym uwzględnieniem programu .NET Core) i kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="471f1-146">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="471f1-147">Ten przewodnik jest również przydatny, jeśli jesteś decydentem technicznym, takim jak architekt przedsiębiorstwa, który chce przeglądu architektury i technologii, zanim zdecydujesz, jakie podejście wybrać dla nowych i nowoczesnych aplikacji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="471f1-147">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="471f1-148">Jak korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="471f1-148">How to use this guide</span></span>

<span data-ttu-id="471f1-149">Pierwsza część tego przewodnika przedstawia kontenery platformy Docker, omówiono sposób wyboru między .NET Core i .NET Framework jako platformę rozwoju i zawiera omówienie mikrousług.</span><span class="sxs-lookup"><span data-stu-id="471f1-149">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="471f1-150">Ta zawartość jest dla architektów i decydentów technicznych, którzy chcą przeglądu, ale nie trzeba skupić się na szczegóły implementacji kodu.</span><span class="sxs-lookup"><span data-stu-id="471f1-150">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="471f1-151">Druga część przewodnika rozpoczyna się od [procesu osiągnięć dla aplikacji opartych na platformie Docker.](./docker-application-development-process/index.md)</span><span class="sxs-lookup"><span data-stu-id="471f1-151">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="471f1-152">Koncentruje się na rozwoju i wzorców mikrousług do implementowania aplikacji przy użyciu platformy .NET Core i platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="471f1-152">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="471f1-153">Ta sekcja będzie najbardziej interesujące dla deweloperów i architektów, którzy chcą skupić się na kod i wzorce i szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="471f1-153">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="471f1-154">Powiązana mikrousługa i aplikacja referencyjna oparta na kontenerach: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="471f1-154">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="471f1-155">Aplikacja eShopOnContainers jest aplikacją referencyjną typu open source dla platformy .NET Core i mikrousług, która jest przeznaczona do wdrażania przy użyciu kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="471f1-155">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="471f1-156">Aplikacja składa się z wielu podsystemów, w tym kilku frontów interfejsu użytkownika sklepu internetowego (aplikacji MVC sieci Web, web SPA i natywnej aplikacji mobilnej).</span><span class="sxs-lookup"><span data-stu-id="471f1-156">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="471f1-157">Zawiera również mikrousług zaplecza i kontenerów dla wszystkich wymaganych operacji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="471f1-157">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="471f1-158">Celem aplikacji jest zaprezentowanie wzorców architektonicznych.</span><span class="sxs-lookup"><span data-stu-id="471f1-158">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="471f1-159">**NIE JEST SZABLONEM GOTOWYM** DO PRODUKCJI, aby uruchamiać aplikacje w świecie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="471f1-159">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="471f1-160">W zasadzie aplikacja jest w stanie stałej wersji beta, ponieważ służy również do testowania nowych potencjalnie interesujących technologii, gdy się pojawiają.</span><span class="sxs-lookup"><span data-stu-id="471f1-160">In fact, the application is in a permanent beta state, as it's also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="471f1-161">Napisz do nas!</span><span class="sxs-lookup"><span data-stu-id="471f1-161">Send us your feedback!</span></span>

<span data-ttu-id="471f1-162">Napisaliśmy ten przewodnik, aby pomóc Ci zrozumieć architekturę konteneryzowanych aplikacji i mikrousług w .NET.</span><span class="sxs-lookup"><span data-stu-id="471f1-162">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="471f1-163">Przewodnik i powiązana aplikacja referencyjna będą ewoluować, więc czekamy na Twoją opinię!</span><span class="sxs-lookup"><span data-stu-id="471f1-163">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="471f1-164">Jeśli masz uwagi dotyczące tego przewodnika można <https://aka.ms/ebookfeedback>ulepszyć, prześlij opinię na .</span><span class="sxs-lookup"><span data-stu-id="471f1-164">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="471f1-165">Środki</span><span class="sxs-lookup"><span data-stu-id="471f1-165">Credits</span></span>

<span data-ttu-id="471f1-166">Współautorzy:</span><span class="sxs-lookup"><span data-stu-id="471f1-166">Co-Authors:</span></span>

> <span data-ttu-id="471f1-167">**Cesar de la Torre**, Sr. PM, zespół produktów .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="471f1-167">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="471f1-168">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="471f1-168">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="471f1-169">**Mike Rousos**, główny inżynier oprogramowania, zespół DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="471f1-169">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="471f1-170">Edytory:</span><span class="sxs-lookup"><span data-stu-id="471f1-170">Editors:</span></span>

> <span data-ttu-id="471f1-171">**Michał Papież**</span><span class="sxs-lookup"><span data-stu-id="471f1-171">**Mike Pope**</span></span>
>
> <span data-ttu-id="471f1-172">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="471f1-172">**Steve Hoag**</span></span>

<span data-ttu-id="471f1-173">Uczestnicy i recenzenci:</span><span class="sxs-lookup"><span data-stu-id="471f1-173">Participants and reviewers:</span></span>

> <span data-ttu-id="471f1-174">**Jeffrey Richter**, Partner Software Eng, zespół platformy Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="471f1-174">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="471f1-175">**Jimmy Bogard**, Chief Architect w: Headspring</span><span class="sxs-lookup"><span data-stu-id="471f1-175">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="471f1-176">**Udi Dahan**, założyciel & CEO, Szczególne oprogramowanie</span><span class="sxs-lookup"><span data-stu-id="471f1-176">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="471f1-177">**Jimmy Nilsson**, współzałożyciel i dyrektor generalny Factor10</span><span class="sxs-lookup"><span data-stu-id="471f1-177">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="471f1-178">**Glenn Condron**, Sr. Program Manager, zespół ASP.NET</span><span class="sxs-lookup"><span data-stu-id="471f1-178">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="471f1-179">**Mark Fussell**, główny kierownik PM, zespół sieci szkieletowej usług Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="471f1-179">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="471f1-180">**Diego Vega**, PM Lead, zespół Entity Framework, Microsoft</span><span class="sxs-lookup"><span data-stu-id="471f1-180">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="471f1-181">**Barry Dorrans**, Sr. Security Program Manager</span><span class="sxs-lookup"><span data-stu-id="471f1-181">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="471f1-182">**Rowan Miller**, Sr. Program Manager, Microsoft</span><span class="sxs-lookup"><span data-stu-id="471f1-182">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="471f1-183">**Ankit Asthana**, Główny Menedżer PM, zespół .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="471f1-183">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="471f1-184">**Scott Hunter**, Dyrektor Handlowy PM, zespół .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="471f1-184">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="471f1-185">**Nish Anil**, Sr. Program Manager, zespół .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="471f1-185">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="471f1-186">**Dylan Reisenberger**, Architect and Dev Lead w: Polly</span><span class="sxs-lookup"><span data-stu-id="471f1-186">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="471f1-187">**Steve "ardalis" Smith** - Architekt oprogramowania i trener - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="471f1-187">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="471f1-188">**Ian Cooper**, Coding Architect w: Brighter</span><span class="sxs-lookup"><span data-stu-id="471f1-188">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="471f1-189">**Unai Zorrilla**, Architekt i Dev Lead w Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="471f1-189">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="471f1-190">**Eduard Tomas**, Dev Lead w: Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="471f1-190">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="471f1-191">**Ramon Tomas**, Developer w: Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="471f1-191">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="471f1-192">**David Sanz**, Developer w: Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="471f1-192">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="471f1-193">**Javier Valero**, Chief Operating Officer w Grupo Solutio</span><span class="sxs-lookup"><span data-stu-id="471f1-193">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="471f1-194">**Pierre Proso**, Sr. Konsultant, Microsoft</span><span class="sxs-lookup"><span data-stu-id="471f1-194">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="471f1-195">**Michael Friis**, Menedżer produktu, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="471f1-195">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="471f1-196">**Charles Lowell**, inżynier oprogramowania, zespół VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="471f1-196">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="471f1-197">**Miguel Veloso**, Software Development Engineer w: Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="471f1-197">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>

## <a name="copyright"></a><span data-ttu-id="471f1-198">Prawa autorskie</span><span class="sxs-lookup"><span data-stu-id="471f1-198">Copyright</span></span>

<span data-ttu-id="471f1-199">OPUBLIKOWANA PRZEZ</span><span class="sxs-lookup"><span data-stu-id="471f1-199">PUBLISHED BY</span></span>

<span data-ttu-id="471f1-200">Zespoły produktów Microsoft Developer Division, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="471f1-200">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="471f1-201">Oddział firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="471f1-201">A division of Microsoft Corporation</span></span>

<span data-ttu-id="471f1-202">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="471f1-202">One Microsoft Way</span></span>

<span data-ttu-id="471f1-203">Redmond, Waszyngton 98052-6399</span><span class="sxs-lookup"><span data-stu-id="471f1-203">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="471f1-204">Prawa autorskie © 2020 roku przez Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="471f1-204">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="471f1-205">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="471f1-205">All rights reserved.</span></span> <span data-ttu-id="471f1-206">Żadna część zawartości tej książki nie może być powielana ani przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.</span><span class="sxs-lookup"><span data-stu-id="471f1-206">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="471f1-207">Książka ta jest dostarczana "tak jak jest" i wyraża poglądy i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="471f1-207">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="471f1-208">Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="471f1-208">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="471f1-209">Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="471f1-209">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="471f1-210">Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.</span><span class="sxs-lookup"><span data-stu-id="471f1-210">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="471f1-211">Firma Microsoft i znaki <https://www.microsoft.com> towarowe wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="471f1-211">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="471f1-212">Mac i macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="471f1-212">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="471f1-213">Logo docker wielorybów jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używany za zgodą.</span><span class="sxs-lookup"><span data-stu-id="471f1-213">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="471f1-214">Wszystkie inne znaki i logo są własnością ich odpowiednich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="471f1-214">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="471f1-215">Dalej</span><span class="sxs-lookup"><span data-stu-id="471f1-215">Next</span></span>](container-docker-introduction/index.md)
