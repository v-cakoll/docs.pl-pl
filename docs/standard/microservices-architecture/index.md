---
title: Mikrousługi .NET. Architektura konteneryzowanych aplikacji .NET
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Mikrousługi są moduły i niezależnie do wdrożenia usługi. Kontenery platformy docker (dla systemu Linux i Windows) można uprościć wdrażanie i testowanie przez tworzenie pakietów usługi i jego zależności w pojedynczą jednostkę, który następnie jest uruchamiany w środowisku izolowanym.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: 38f638b76a38c470daf51cb7be8566feb4b6362f
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121366"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="231de-105">Mikrousługi .NET: Architektura konteneryzowanych aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="231de-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Okładki książki](./media/cover-small.png)

<span data-ttu-id="231de-107">**Wersja v2.1.02** — zaktualizowano w celu platformy ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="231de-107">**EDITION v2.1.02** - Updated to ASP.NET Core 2.1</span></span>

<span data-ttu-id="231de-108">Ten przewodnik stanowi wprowadzenie do tworzenia aplikacji opartych na mikrousługach i zarządzanie nimi przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="231de-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="231de-109">Omówiono w nim kwestie projektowania architektonicznego i zbliża się do wdrożenia przy użyciu platformy .NET Core i kontenerów rozwiązania Docker.</span><span class="sxs-lookup"><span data-stu-id="231de-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> 

<span data-ttu-id="231de-110">Aby ułatwić rozpoczęcie pracy, przewodnik koncentruje się na odwołanie kontenerowych nimi i aplikacji opartych na mikrousługach, która pozwala zapoznać się z.</span><span class="sxs-lookup"><span data-stu-id="231de-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="231de-111">Aplikacja referencyjna jest dostępna na [ramach aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="231de-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="231de-112">Linki akcji</span><span class="sxs-lookup"><span data-stu-id="231de-112">Action links</span></span>

* <span data-ttu-id="231de-113">Pobierz tę książkę elektroniczną w wybranym przez Ciebie formacie: | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-epub) |</span><span class="sxs-lookup"><span data-stu-id="231de-113">Download this eBook in your format of choice: | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-epub) |</span></span>

* <span data-ttu-id="231de-114">Klon/rozwidlenia aplikacja referencyjna [ramach aplikacji eShopOnContainers w witrynie GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="231de-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>
 
* <span data-ttu-id="231de-115">Obejrzyj [klip wideo w witrynie Channel 9](http://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="231de-115">Watch the [introductory video on Channel 9](http://aka.ms/microservices-video)</span></span>

* <span data-ttu-id="231de-116">Ustal, jakimi [architektury Mikrousług](http://aka.ms/MicroservicesArchitecture) natychmiast</span><span class="sxs-lookup"><span data-stu-id="231de-116">Get to know the [Microservices Architecture](http://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="231de-117">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="231de-117">Introduction</span></span>

<span data-ttu-id="231de-118">Przedsiębiorstwa są coraz bardziej zawierającemu oszczędności kosztów, rozwiązywania problemów z wdrażaniem i poprawy operacje operacji deweloperskich i produkcyjnych przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="231de-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="231de-119">Microsoft ma zostały udostępnia innowacje kontenera dla Windows i Linux, tworząc produktów, takich jak Azure Container Service i Azure Service Fabric i Zostań partnerem liderów branży, takich jak Docker, Mesosphere i Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="231de-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="231de-120">Te produkty dostarczanie rozwiązań do obsługi kontenerów, które ułatwiają tworzenie i wdrażanie aplikacji w chmurze prędkość i skalę, niezależnie od wybranych przez nich platformy lub narzędzia.</span><span class="sxs-lookup"><span data-stu-id="231de-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="231de-121">Docker staje się de facto standardem w branży kontenera, obsługiwane przez najważniejszych dostawców w ekosystemów Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="231de-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="231de-122">(Firma Microsoft jest jeden z dostawców chmury głównego obsługi platformy Docker). W przyszłości Docker prawdopodobnie będzie wszechobecne w dowolnych centrach danych w chmurze lub lokalnie.</span><span class="sxs-lookup"><span data-stu-id="231de-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="231de-123">Ponadto [mikrousług](https://martinfowler.com/articles/microservices.html) architektury jest pojawiających się jako ważne podejście do rozproszonych aplikacji o kluczowym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="231de-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="231de-124">W przypadku opartych na mikrousługach architektury aplikacji bazuje na zbiór usług, które mogą być tworzone, przetestowane, wdrożone i kontrolą wersji niezależnie.</span><span class="sxs-lookup"><span data-stu-id="231de-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="231de-125">Przewodnik — informacje</span><span class="sxs-lookup"><span data-stu-id="231de-125">About this guide</span></span>

<span data-ttu-id="231de-126">Ten przewodnik stanowi wprowadzenie do tworzenia aplikacji opartych na mikrousługach i zarządzanie nimi przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="231de-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="231de-127">Omówiono w nim kwestie projektowania architektonicznego i zbliża się do wdrożenia przy użyciu platformy .NET Core i kontenerów rozwiązania Docker.</span><span class="sxs-lookup"><span data-stu-id="231de-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="231de-128">Aby ułatwić rozpoczęcie korzystania z kontenerów i mikrousług, przewodnik koncentruje się na odwołanie kontenerowych nimi i aplikacji opartych na mikrousługach, która pozwala zapoznać się z.</span><span class="sxs-lookup"><span data-stu-id="231de-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="231de-129">Przykładowa aplikacja jest dostępna w [ramach aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="231de-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="231de-130">Ten przewodnik zawiera podstawowe rozwoju i wskazówki dotyczące architektury, przede wszystkim na poziomie środowiska programowania skupiając się na dwie technologie: platforma Docker i platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="231de-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="231de-131">Zamierzone jest, że przeczytaniem tego przewodnika, jeśli zastanawiasz się nad projektu aplikacji bez konieczności zajmowania się infrastrukturą (w chmurze lub lokalnie) środowiska produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="231de-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="231de-132">Będzie decyzje dotyczące infrastruktury później, podczas tworzenia aplikacji gotowych do produkcji.</span><span class="sxs-lookup"><span data-stu-id="231de-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="231de-133">W związku z tym ten przewodnik jest przeznaczony jako niezależny od infrastruktury bardziej rozwoju środowiska — skoncentrowane na.</span><span class="sxs-lookup"><span data-stu-id="231de-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="231de-134">Po mają materiałami tego przewodnika, następnym krokiem jest więcej informacji na temat mikrousług gotowe do produkcji w systemie Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="231de-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="231de-135">Wersja</span><span class="sxs-lookup"><span data-stu-id="231de-135">Version</span></span>

<span data-ttu-id="231de-136">Ten przewodnik został zaktualizowany w celu pokrycia **platformy .NET Core 2.1** wersji oraz wiele dodatkowe aktualizacje związane z takie same "wave" technologii (czyli.</span><span class="sxs-lookup"><span data-stu-id="231de-136">This guide has been revised to cover **.NET Core 2.1** version plus many additional updates related to the same “wave” of technologies (that is.</span></span> <span data-ttu-id="231de-137">Azure wraz z dodatkowymi 3 innych firm technologii) odpowiedzialnego w czasie za pomocą platformy .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="231de-137">Azure and additional 3rd party technologies) coinciding in time with .NET Core 2.1.</span></span> <span data-ttu-id="231de-138">Dlatego wersji książki został także zaktualizowany do wersji **2.1**.</span><span class="sxs-lookup"><span data-stu-id="231de-138">That’s why the book version has also been updated to version **2.1**.</span></span> 

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="231de-139">Co ten przewodnik nie obejmuje</span><span class="sxs-lookup"><span data-stu-id="231de-139">What this guide does not cover</span></span>

<span data-ttu-id="231de-140">Ten przewodnik koncentruje się na cykl życia aplikacji, infrastruktury DevOps i potoków ciągłej integracji/ciągłego wdrażania lub pracy zespołu.</span><span class="sxs-lookup"><span data-stu-id="231de-140">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="231de-141">Przewodnik uzupełniający [kontenerowych nimi Docker cyklem życia aplikacji za pomocą platformy firmy Microsoft i narzędzi](https://aka.ms/dockerlifecycleebook) koncentruje się na ten temat.</span><span class="sxs-lookup"><span data-stu-id="231de-141">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="231de-142">Przewodnik bieżącego nie udostępniają szczegółów implementacji w infrastrukturze platformy Azure, takich jak informacje o określonych koordynatorów.</span><span class="sxs-lookup"><span data-stu-id="231de-142">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="231de-143">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="231de-143">Additional resources</span></span>

-   <span data-ttu-id="231de-144">**Kontenerowych nimi cykl życia aplikacji platformy Docker przy użyciu platformy firmy Microsoft i narzędzi** (do pobrania Książka elektroniczna)</span><span class="sxs-lookup"><span data-stu-id="231de-144">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

## <a name="who-should-use-this-guide"></a><span data-ttu-id="231de-145">Kto powinien używać tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="231de-145">Who should use this guide</span></span>

<span data-ttu-id="231de-146">Napisaliśmy ten przewodnik dla deweloperów i architektów rozwiązań, którzy są nowe, do tworzenia aplikacji opartych na platformie Docker i opartych na mikrousługach architektury.</span><span class="sxs-lookup"><span data-stu-id="231de-146">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="231de-147">Ten przewodnik jest przeznaczony dla możesz Jeśli chcesz dowiedzieć się, jak zaprojektować, projektowania i implementacji aplikacji weryfikacji koncepcji przy użyciu technologii firmy Microsoft (kładąc szczególny nacisk na platformie .NET Core) i z kontenerami aparatu Docker.</span><span class="sxs-lookup"><span data-stu-id="231de-147">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="231de-148">Można również znaleźć w przewodniku przydatne, jeśli jesteś osobą podejmującą decyzje techniczne, np. architektury przedsiębiorstwa, który chce architekturę i omówienie technologii przed zdecyduj, jakie podejście do wybrania dla nowych i nowoczesnych aplikacji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="231de-148">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="231de-149">Jak używać tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="231de-149">How to use this guide</span></span>

<span data-ttu-id="231de-150">Pierwszej części tego przewodnika wprowadza kontenerów platformy Docker, w tym artykule omówiono jak dokonać wyboru między programem.NET Core i .NET Framework jako architektura deweloperska i zawiera omówienie mikrousług.</span><span class="sxs-lookup"><span data-stu-id="231de-150">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="231de-151">Ta zawartość jest dla architektów i technicznych inne osoby podejmujące decyzje, którzy mają Przegląd, ale nie muszą skoncentrować się na szczegóły implementacji kodu.</span><span class="sxs-lookup"><span data-stu-id="231de-151">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="231de-152">Druga sekcja przewodnika zaczyna się od [aplikacji opartych na proces programistyczny dla platformy Docker](./docker-application-development-process/index.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="231de-152">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="231de-153">Koncentruje się ona na rozwój i mikrousług wzorce dotyczące wdrażania aplikacji przy użyciu platformy .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="231de-153">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="231de-154">W tej sekcji będzie najbardziej przydatnych dla deweloperów i architektów, którzy chcą skupić się na kodzie, a także na wzorców i szczegółów implementacji.</span><span class="sxs-lookup"><span data-stu-id="231de-154">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="231de-155">Związanych z mikrousług i aplikacji opartych na kontenerach referencyjnej: ramach aplikacji eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="231de-155">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="231de-156">Aplikacji w ramach aplikacji eShopOnContainers to aplikacja typu open-source odwołania dla platformy .NET Core i mikrousług, który jest przeznaczony do wdrożenia przy użyciu kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="231de-156">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="231de-157">Aplikacja składa się z wiele podsystemów, w tym kilka Sklep internetowy interfejs użytkownika Frontony (aplikacji sieci Web MVC, SPA internetowych i natywnych aplikacji mobilnych).</span><span class="sxs-lookup"><span data-stu-id="231de-157">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="231de-158">Zawiera także zaplecza mikrousług i kontenerów wszystkich wymaganych operacji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="231de-158">It also includes the back-end microservices and containers for all required server-side operations.</span></span> 

<span data-ttu-id="231de-159">Aplikacja ma na celu prezentowania wzorców architektonicznych.</span><span class="sxs-lookup"><span data-stu-id="231de-159">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="231de-160">**GOTOWE do produkcji szablonu dla IT nie jest** do uruchamiania aplikacji w rzeczywistych warunkach.</span><span class="sxs-lookup"><span data-stu-id="231de-160">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="231de-161">W rzeczywistości aplikacja jest w stanie stałe w wersji beta, także jest używane do testowania nowych technologii potencjalnie interesujące, ponieważ są one wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="231de-161">In fact, the application is in a permanent beta state, as it’s also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="231de-162">Wyślij nam swoją opinię!</span><span class="sxs-lookup"><span data-stu-id="231de-162">Send us your feedback!</span></span>

<span data-ttu-id="231de-163">Napisaliśmy tego przewodnika, aby lepiej zrozumieć architekturę konteneryzowane aplikacje i mikrousług na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="231de-163">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="231de-164">Przewodnik i powiązane odwołania aplikacji będzie można rozwijają, więc chętnie poznamy Twoją opinię!</span><span class="sxs-lookup"><span data-stu-id="231de-164">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="231de-165">Jeśli masz komentarze na temat sposobu ten przewodnik można zwiększyć, wyślij je do:</span><span class="sxs-lookup"><span data-stu-id="231de-165">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a><span data-ttu-id="231de-166">Środki na korzystanie z</span><span class="sxs-lookup"><span data-stu-id="231de-166">Credits</span></span>

<span data-ttu-id="231de-167">Współautorzy:</span><span class="sxs-lookup"><span data-stu-id="231de-167">Co-Authors:</span></span>

> <span data-ttu-id="231de-168">**Torre'a de la Cesarowi**, Stanowisko kierownicze wyższego PM, zespół produktu platformy .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="231de-168">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="231de-169">**Bill Wagnera**, Stanowisko kierownicze wyższego Deweloper zawartości C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="231de-169">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="231de-170">**Mike Rousos**, inżynier ds. oprogramowania jednostki, zespołu DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="231de-170">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="231de-171">Edytory:</span><span class="sxs-lookup"><span data-stu-id="231de-171">Editors:</span></span>

> <span data-ttu-id="231de-172">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="231de-172">**Mike Pope**</span></span>
>
> <span data-ttu-id="231de-173">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="231de-173">**Steve Hoag**</span></span>

<span data-ttu-id="231de-174">Uczestnicy i osób dokonujących przeglądu:</span><span class="sxs-lookup"><span data-stu-id="231de-174">Participants and reviewers:</span></span>

> <span data-ttu-id="231de-175">**Jeffrey Richter**, rozwoju oprogramowania partnerem, zespół platformy Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="231de-175">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="231de-176">**Jimmy Bogard**, Dyrektor ds. architektury w Headspring</span><span class="sxs-lookup"><span data-stu-id="231de-176">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="231de-177">**Udi Dahan**, założyciel i Dyrektor Generalny, konkretnego oprogramowania</span><span class="sxs-lookup"><span data-stu-id="231de-177">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="231de-178">**Jimmy Nilsson**, współzałożyciel i Dyrektor Generalny firmy z Factor10</span><span class="sxs-lookup"><span data-stu-id="231de-178">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="231de-179">**Glenn Condron**, Stanowisko kierownicze wyższego Menedżer programu, zespół programu ASP.NET</span><span class="sxs-lookup"><span data-stu-id="231de-179">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="231de-180">**Oznacz Fussell**, Kierownik jednostki PM, zespół usługi Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="231de-180">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="231de-181">**Diego Vega**, kierownik PM, platformy Entity Framework zespołu firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="231de-181">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="231de-182">**Marcin Dorrans**, Stanowisko kierownicze wyższego Menedżer programów zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="231de-182">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="231de-183">**Rowan Miller**, Sr. Menedżer programów firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="231de-183">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="231de-184">**Ankit Asthana**, główny menedżer PM, zespołem platformy .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="231de-184">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="231de-185">**Scott Hunter**, Dyrektor ds. partnerów PM, zespołem platformy .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="231de-185">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="231de-186">**Dylan Reisenberger**, architekt i Kierownik Dev w Polly</span><span class="sxs-lookup"><span data-stu-id="231de-186">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="231de-187">**Steve Smith**, wytwarzającym oprogramowanie & Trainer na ASPSmith Ltd.</span><span class="sxs-lookup"><span data-stu-id="231de-187">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="231de-188">**Ian Cooper**, kodowania architektury w Brighter</span><span class="sxs-lookup"><span data-stu-id="231de-188">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="231de-189">**Unai Zorrilla**, architekt i Kierownik Dev w Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="231de-189">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="231de-190">**Tomasowi EDUARD**, kierownictwo Dev Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="231de-190">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="231de-191">**Tomasowi Ramon**, deweloper pracujący u Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="231de-191">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="231de-192">**David Sanz**, deweloper pracujący u Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="231de-192">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="231de-193">**Javier Valero**, Dyrektor operacyjny ds. na rozwiązanie Grupo</span><span class="sxs-lookup"><span data-stu-id="231de-193">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="231de-194">**Pierre proso**, Stanowisko kierownicze wyższego Consultant, Microsoft</span><span class="sxs-lookup"><span data-stu-id="231de-194">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="231de-195">**Michael Friis**, Menedżer produktu, Inc platformy Docker</span><span class="sxs-lookup"><span data-stu-id="231de-195">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="231de-196">**Charles Lowell**, inżynier ds. oprogramowania, zespołu CAT programu VS, Microsoft</span><span class="sxs-lookup"><span data-stu-id="231de-196">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="231de-197">**Miguel Veloso**, Stanowisko kierownicze wyższego Konsultant na żądanie Turing</span><span class="sxs-lookup"><span data-stu-id="231de-197">**Miguel Veloso**, Sr. Consultant at Turing Challenge</span></span>


## <a name="copyright"></a><span data-ttu-id="231de-198">Prawa autorskie</span><span class="sxs-lookup"><span data-stu-id="231de-198">Copyright</span></span>

<span data-ttu-id="231de-199">Pobierz dostępne pod adresem: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="231de-199">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="231de-200">OPUBLIKOWANE PRZEZ</span><span class="sxs-lookup"><span data-stu-id="231de-200">PUBLISHED BY</span></span>

<span data-ttu-id="231de-201">Zespoły produktu Microsoft Developer Division, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="231de-201">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="231de-202">Dzielenie firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="231de-202">A division of Microsoft Corporation</span></span>

<span data-ttu-id="231de-203">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="231de-203">One Microsoft Way</span></span>

<span data-ttu-id="231de-204">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="231de-204">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="231de-205">Copyright © 2018 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="231de-205">Copyright © 2018 by Microsoft Corporation</span></span>

<span data-ttu-id="231de-206">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="231de-206">All rights reserved.</span></span> <span data-ttu-id="231de-207">Nie części zawartości tej książki może odtworzyć lub przenoszone w jakiejkolwiek formie lub za pomocą jakichkolwiek środków bez pisemnej zgody wydawcy.</span><span class="sxs-lookup"><span data-stu-id="231de-207">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="231de-208">Ten podręcznik jest dostarczany "jako — jest" i wyraża, widoki i opinie od autora.</span><span class="sxs-lookup"><span data-stu-id="231de-208">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="231de-209">Widoki, opinie i informacje wyrażone w tym podręczniku, w tym adresy URL i inne odnośniki do witryn internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="231de-209">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="231de-210">Niektóre przedstawione przykłady znajdują się wyłącznie do celów informacyjnych i są fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="231de-210">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="231de-211">Nie rzeczywiste skojarzenia ani powiązania nie są zamierzone ani powinny być zakładane.</span><span class="sxs-lookup"><span data-stu-id="231de-211">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="231de-212">Firma Microsoft i znaków towarowych, opisane w temacie <https://www.microsoft.com> na stronie sieci Web "Znakami" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="231de-212">Microsoft and the trademarks listed at <https://www.microsoft.com> on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="231de-213">Komputery Mac i z systemem macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="231de-213">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="231de-214">Logo whale platformy Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używane przez uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="231de-214">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="231de-215">Wszystkie inne znaki i logo są własnością ich prawnych właścicieli.</span><span class="sxs-lookup"><span data-stu-id="231de-215">All other marks and logos are property of their respective owners.</span></span>


>[!div class="step-by-step"]
[<span data-ttu-id="231de-216">Next</span><span class="sxs-lookup"><span data-stu-id="231de-216">Next</span></span>](container-docker-introduction/index.md)
