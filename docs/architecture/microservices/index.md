---
title: Mikrousługi platformy .NET. architektura konteneryzowanych aplikacji .NET
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Mikrousługi są modularne i niezależnie do wdrożenia usługi. Kontenery platformy Docker (dla systemów Linux i Windows) upraszczają wdrażanie i testowanie poprzez zgrupowanie usługi i jej zależności w pojedynczą jednostkę, która jest uruchamiana w środowisku izolowanym.
ms.date: 01/07/2019
ms.openlocfilehash: dcfff8b06dc77b47e6586ea82c82acc30a5cf3df
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848867"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="34fb2-105">Mikrousługi .NET: architektura konteneryzowanych aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="34fb2-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Pokrycie książki](./media/cover-small.png)

<span data-ttu-id="34fb2-107">**Wersja 2.2** — zaktualizowane do ASP.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="34fb2-107">**EDITION v2.2** - Updated to ASP.NET Core 2.2</span></span>

<span data-ttu-id="34fb2-108">Ten przewodnik stanowi wprowadzenie do tworzenia aplikacji opartych na mikrousługach i zarządzania nimi przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="34fb2-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="34fb2-109">Omówiono podejścia projektowania i implementacji architektury przy użyciu programu .NET Core i kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="34fb2-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> 

<span data-ttu-id="34fb2-110">Aby ułatwić rozpoczęcie pracy, przewodnik koncentruje się na odniesieniu do aplikacji opartej na kontenerach i mikrousługach, które można eksplorować.</span><span class="sxs-lookup"><span data-stu-id="34fb2-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="34fb2-111">Aplikacja referencyjna jest dostępna w repozytorium GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .</span><span class="sxs-lookup"><span data-stu-id="34fb2-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="34fb2-112">Linki akcji</span><span class="sxs-lookup"><span data-stu-id="34fb2-112">Action links</span></span>

- <span data-ttu-id="34fb2-113">Pobierz tę książkę elektroniczną w wybranym formacie: | [Plik PDF](https://aka.ms/microservicesebook) [](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-epub) [mobi](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-mobi)EPUB  |  |  |</span><span class="sxs-lookup"><span data-stu-id="34fb2-113">Download this eBook in your format of choice: | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-epub) |</span></span>

- <span data-ttu-id="34fb2-114">Klonowanie/rozwidlenie aplikacji referencyjnej [eShopOnContainers w witrynie GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="34fb2-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>
 
- <span data-ttu-id="34fb2-115">Obejrzyj [film wprowadzający w witrynie Channel 9](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="34fb2-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="34fb2-116">Uzyskaj informacje o [architekturze mikrousług](https://aka.ms/MicroservicesArchitecture) od razu</span><span class="sxs-lookup"><span data-stu-id="34fb2-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="34fb2-117">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="34fb2-117">Introduction</span></span>

<span data-ttu-id="34fb2-118">Przedsiębiorstwa są coraz bardziej kosztowne, rozwiązując problemy z wdrażaniem i ulepszają operacje DevOps i produkcyjne przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="34fb2-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="34fb2-119">Firma Microsoft wyłączyła innowacje dotyczące kontenerów dla systemów Windows i Linux, tworząc produkty takie jak Azure Kubernetes Service i Azure Service Fabric, a przez partnerskie liderów branżowych, takich jak Docker, mesosphere i Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="34fb2-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="34fb2-120">Te produkty dostarczają rozwiązania kontenerów, które ułatwiają firmom Kompilowanie i wdrażanie aplikacji na dużą skalę i skalowalność, niezależnie od ich wyboru platformy lub narzędzi.</span><span class="sxs-lookup"><span data-stu-id="34fb2-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="34fb2-121">Platforma Docker staje się niefaktycznym standardem w branży kontenerów, która jest obsługiwana przez najbardziej znaczących dostawców w ekosystemach systemów Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="34fb2-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="34fb2-122">(Firma Microsoft jest jednym z głównych dostawców chmury obsługujących platformę Docker). W przyszłości platforma Docker będzie prawdopodobnie ogólnie oparta na dowolnym centrum danych w chmurze lub lokalnie.</span><span class="sxs-lookup"><span data-stu-id="34fb2-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="34fb2-123">Ponadto architektura [mikrousług](https://martinfowler.com/articles/microservices.html) pojawia się jako ważne podejście do rozproszonych aplikacji o krytycznym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="34fb2-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="34fb2-124">W architekturze mikrousług aplikacja jest tworzona na podstawie kolekcji usług, które mogą być opracowane, przetestowane, wdrożone i niezależne od wersji.</span><span class="sxs-lookup"><span data-stu-id="34fb2-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="34fb2-125">Informacje o tym przewodniku</span><span class="sxs-lookup"><span data-stu-id="34fb2-125">About this guide</span></span>

<span data-ttu-id="34fb2-126">Ten przewodnik stanowi wprowadzenie do tworzenia aplikacji opartych na mikrousługach i zarządzania nimi przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="34fb2-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="34fb2-127">Omówiono podejścia projektowania i implementacji architektury przy użyciu programu .NET Core i kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="34fb2-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="34fb2-128">Aby ułatwić rozpoczęcie pracy z kontenerami i mikrousług, przewodnik koncentruje się na odwołaniach do aplikacji opartych na kontenerach i mikrousługach, które można eksplorować.</span><span class="sxs-lookup"><span data-stu-id="34fb2-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="34fb2-129">Przykładowa aplikacja jest dostępna w repozytorium GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .</span><span class="sxs-lookup"><span data-stu-id="34fb2-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="34fb2-130">Ten przewodnik zawiera podstawowe wskazówki dotyczące programowania i architektury w środowisku programistycznym, które koncentrują się na dwóch technologiach: Docker i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="34fb2-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="34fb2-131">Naszym zamiarem jest zapoznanie się z tym przewodnikiem, gdy myślisz o projekcie aplikacji bez skoncentrowania się na infrastrukturze (w chmurze lub lokalnie) w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="34fb2-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="34fb2-132">Decyzje o infrastrukturze będą podejmowane później, podczas tworzenia aplikacji gotowych do produkcji.</span><span class="sxs-lookup"><span data-stu-id="34fb2-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="34fb2-133">W związku z tym ten przewodnik jest przeznaczony dla infrastruktury niezależny od i większej ilości środowiska programistycznego.</span><span class="sxs-lookup"><span data-stu-id="34fb2-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="34fb2-134">Po przeprowadzeniu tego przewodnika następnym krokiem jest zapoznanie się z mikrousługami gotowymi do produkcji na Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="34fb2-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="34fb2-135">Wersja</span><span class="sxs-lookup"><span data-stu-id="34fb2-135">Version</span></span>

<span data-ttu-id="34fb2-136">Ten przewodnik został zmieniony w taki sposób, aby objęł **platformę .NET Core 2,2** i wiele dodatkowych aktualizacji odnoszących się do tych samych "technologii".</span><span class="sxs-lookup"><span data-stu-id="34fb2-136">This guide has been revised to cover **.NET Core 2.2** version plus many additional updates related to the same “wave” of technologies (that is.</span></span> <span data-ttu-id="34fb2-137">Platformę Azure i dodatkowe technologie innych firm, które są zgodne z platformą .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="34fb2-137">Azure and additional 3rd party technologies) coinciding in time with .NET Core 2.2.</span></span> <span data-ttu-id="34fb2-138">Dlatego też wersja książki została zaktualizowana do wersji **2,2**.</span><span class="sxs-lookup"><span data-stu-id="34fb2-138">That’s why the book version has also been updated to version **2.2**.</span></span> 

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="34fb2-139">Czym nie obejmuje ten przewodnik</span><span class="sxs-lookup"><span data-stu-id="34fb2-139">What this guide does not cover</span></span>

<span data-ttu-id="34fb2-140">Ten przewodnik nie koncentruje się na potoku cyklu życia aplikacji, DevOps, ciągłej integracji/ciągłego wdrażania lub pracy zespołu.</span><span class="sxs-lookup"><span data-stu-id="34fb2-140">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="34fb2-141">Przewodnik uzupełniający [zadokowany cykl życia aplikacji platformy Docker z platformą i narzędziami firmy Microsoft](https://aka.ms/dockerlifecycleebook) koncentrują się na tym temacie.</span><span class="sxs-lookup"><span data-stu-id="34fb2-141">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="34fb2-142">Bieżący przewodnik nie zawiera również szczegółowych informacji dotyczących implementacji infrastruktury platformy Azure, takich jak informacje dotyczące określonych koordynatorów.</span><span class="sxs-lookup"><span data-stu-id="34fb2-142">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="34fb2-143">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="34fb2-143">Additional resources</span></span>

- <span data-ttu-id="34fb2-144">**Cykl życia aplikacji platformy Docker w kontenerze i narzędziach firmy Microsoft** (książka elektroniczna do pobrania)</span><span class="sxs-lookup"><span data-stu-id="34fb2-144">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="34fb2-145">Kto powinien korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="34fb2-145">Who should use this guide</span></span>

<span data-ttu-id="34fb2-146">Ten przewodnik został napisany dla deweloperów i architektów rozwiązań, które są nowe dla tworzenia aplikacji opartych na platformie Docker oraz architektury opartej na mikrousługach.</span><span class="sxs-lookup"><span data-stu-id="34fb2-146">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="34fb2-147">Ten przewodnik jest przeznaczony dla Ciebie, jeśli chcesz dowiedzieć się, jak architektować, projektować i wdrażać aplikacje do weryfikacji koncepcji za pomocą technologii programistycznych firmy Microsoft (ze specjalnym skoncentrowaniem się na platformie .NET Core) i z kontenerami platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="34fb2-147">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="34fb2-148">Ten przewodnik będzie również przydatny, jeśli jesteś specjalistą ds. decyzji, na przykład z architektem przedsiębiorstwa, który chce zapoznać się z architekturą i technologią, przed podjęciem decyzji o wyborze podejścia do nowych i nowoczesnych aplikacji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="34fb2-148">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="34fb2-149">Jak korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="34fb2-149">How to use this guide</span></span>

<span data-ttu-id="34fb2-150">Pierwsza część tego przewodnika zawiera wprowadzenie do kontenerów platformy Docker, w jaki sposób można wybrać platformę .NET Core i .NET Framework jako strukturę programistyczną oraz Omówienie mikrousług.</span><span class="sxs-lookup"><span data-stu-id="34fb2-150">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="34fb2-151">Ta zawartość jest przeznaczony dla architektów i osób podejmujących decyzje techniczne, którzy chcą zapoznać się z omówieniem, ale nie muszą skupić się na szczegółach implementacji kodu.</span><span class="sxs-lookup"><span data-stu-id="34fb2-151">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="34fb2-152">Druga część przewodnika rozpoczyna się od [procesu opracowywania aplikacji opartych na platformie Docker](./docker-application-development-process/index.md) .</span><span class="sxs-lookup"><span data-stu-id="34fb2-152">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="34fb2-153">Koncentruje się na wzorcach deweloperskich i mikrousług związanych z wdrażaniem aplikacji przy użyciu oprogramowania .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="34fb2-153">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="34fb2-154">Ta sekcja będzie najbardziej interesująca dla deweloperów i architektów, którzy chcą skupić się na kodzie oraz o wzorcach i szczegółach implementacji.</span><span class="sxs-lookup"><span data-stu-id="34fb2-154">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="34fb2-155">Powiązana mikrousługa i aplikacja referencyjna oparta na kontenerach: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="34fb2-155">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="34fb2-156">Aplikacja eShopOnContainers to aplikacja referencyjna Open Source dla platformy .NET Core i mikrousług, która została zaprojektowana do wdrożenia przy użyciu kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="34fb2-156">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="34fb2-157">Aplikacja składa się z wielu podsystemów, w tym kilku frontonów interfejsu użytkownika w postaci elektronicznej (aplikacji sieci Web MVC, SPA sieci Web i natywnej aplikacji mobilnej).</span><span class="sxs-lookup"><span data-stu-id="34fb2-157">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="34fb2-158">Obejmuje ona również mikrousługi i kontenery zaplecza dla wszystkich wymaganych operacji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="34fb2-158">It also includes the back-end microservices and containers for all required server-side operations.</span></span> 

<span data-ttu-id="34fb2-159">Celem aplikacji jest zaprezentowanie wzorców architektonicznych.</span><span class="sxs-lookup"><span data-stu-id="34fb2-159">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="34fb2-160">**Nie jest to szablon gotowy** do uruchomienia aplikacji w rzeczywistości.</span><span class="sxs-lookup"><span data-stu-id="34fb2-160">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="34fb2-161">W rzeczywistości aplikacja jest w stanie stałego stanu beta, ponieważ jest również używana do testowania nowych potencjalnie interesujących technologii w miarę ich wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="34fb2-161">In fact, the application is in a permanent beta state, as it’s also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="34fb2-162">Wyślij nam swoją opinię.</span><span class="sxs-lookup"><span data-stu-id="34fb2-162">Send us your feedback!</span></span>

<span data-ttu-id="34fb2-163">Utworzyliśmy ten przewodnik, aby ułatwić zrozumienie architektury aplikacji i mikrousług w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="34fb2-163">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="34fb2-164">Przewodnik i powiązana aplikacja referencyjna będą rozwijane, więc będziemy nam powitać Twoją opinię.</span><span class="sxs-lookup"><span data-stu-id="34fb2-164">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="34fb2-165">Jeśli masz komentarze dotyczące tego, jak można ulepszyć ten przewodnik, wyślij je do:</span><span class="sxs-lookup"><span data-stu-id="34fb2-165">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a><span data-ttu-id="34fb2-166">Napisy końcowe</span><span class="sxs-lookup"><span data-stu-id="34fb2-166">Credits</span></span>

<span data-ttu-id="34fb2-167">Współautorzy:</span><span class="sxs-lookup"><span data-stu-id="34fb2-167">Co-Authors:</span></span>

> <span data-ttu-id="34fb2-168">**Cesar de La Torre**, SR. PM, zespół produktu .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="34fb2-168">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="34fb2-169">**Bill Wagner**, SR. Content Developer, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="34fb2-169">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="34fb2-170">**Jan Rousos**, główny inżynier ds. oprogramowania, DevDiv kot, firma Microsoft</span><span class="sxs-lookup"><span data-stu-id="34fb2-170">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="34fb2-171">Edytory</span><span class="sxs-lookup"><span data-stu-id="34fb2-171">Editors:</span></span>

> <span data-ttu-id="34fb2-172">**Jan Pope**</span><span class="sxs-lookup"><span data-stu-id="34fb2-172">**Mike Pope**</span></span>
>
> <span data-ttu-id="34fb2-173">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="34fb2-173">**Steve Hoag**</span></span>

<span data-ttu-id="34fb2-174">Uczestnicy i recenzenci:</span><span class="sxs-lookup"><span data-stu-id="34fb2-174">Participants and reviewers:</span></span>

> <span data-ttu-id="34fb2-175">**Jeffrey Richter**, partner Software aparatu, Azure Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="34fb2-175">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="34fb2-176">**Jimmy Bogard**, główny architekt w headspring</span><span class="sxs-lookup"><span data-stu-id="34fb2-176">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="34fb2-177">**UDI Dahan**, założyciel & dyrektor naczelny, szczególne oprogramowanie</span><span class="sxs-lookup"><span data-stu-id="34fb2-177">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="34fb2-178">**Jimmy Nilsson**, współzałożyciel i dyrektor naczelny Factor10</span><span class="sxs-lookup"><span data-stu-id="34fb2-178">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="34fb2-179">**Glenn Condron**, SR. Program Manager, zespół ASP.NET</span><span class="sxs-lookup"><span data-stu-id="34fb2-179">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="34fb2-180">**Mark Fussell**, podmiotu z potencjalnym klientem PM, Azure Service Fabric Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="34fb2-180">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="34fb2-181">**Diego Vega**, klient PM, Entity Framework zespół, Microsoft</span><span class="sxs-lookup"><span data-stu-id="34fb2-181">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="34fb2-182">**Marcin Dorrans**, SR. Security — Menedżer programów</span><span class="sxs-lookup"><span data-stu-id="34fb2-182">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="34fb2-183">**Rowan Miller**, SR. Program Manager, Microsoft</span><span class="sxs-lookup"><span data-stu-id="34fb2-183">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="34fb2-184">**Autor Ankit Asthana**, kierownik ds. platformy PM, zespół .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="34fb2-184">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="34fb2-185">**Scott myśliwy**, dyrektor ds. partnerów, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="34fb2-185">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="34fb2-186">**Nish Anil**, SR. Program Manager, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="34fb2-186">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="34fb2-187">**Dylan Reisenberger**, architekt i dev ołów w Polly</span><span class="sxs-lookup"><span data-stu-id="34fb2-187">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="34fb2-188">**Steve "ardalis" Smith** — architekt oprogramowania i Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="34fb2-188">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="34fb2-189">**Ian Cooper**, architekt programowania na jaśniejszy</span><span class="sxs-lookup"><span data-stu-id="34fb2-189">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="34fb2-190">**Unai Zorrilla**, architekt i dev ołów z zwykłymi pojęciami</span><span class="sxs-lookup"><span data-stu-id="34fb2-190">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="34fb2-191">**Eduard Tomas**, dev ołów z zwykłymi pojęciami</span><span class="sxs-lookup"><span data-stu-id="34fb2-191">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="34fb2-192">**Ramon Tomas**, deweloper z zwykłymi pojęciami</span><span class="sxs-lookup"><span data-stu-id="34fb2-192">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="34fb2-193">**David Sanz**, deweloper z zwykłymi pojęciami</span><span class="sxs-lookup"><span data-stu-id="34fb2-193">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="34fb2-194">**Javier Valero**, dyrektor ds. operacyjnych w Grupo Solutio</span><span class="sxs-lookup"><span data-stu-id="34fb2-194">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="34fb2-195">**Pierre Millet**, SR. konsultant, Microsoft</span><span class="sxs-lookup"><span data-stu-id="34fb2-195">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="34fb2-196">**Michael Friis**, menedżer produktu, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="34fb2-196">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="34fb2-197">**Charles Lowell**, inżynier ds. oprogramowania, zespół programu vs Cat, Microsoft</span><span class="sxs-lookup"><span data-stu-id="34fb2-197">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="34fb2-198">**Miguel Veloso**, SR. konsultant z wyzwaniami Turing</span><span class="sxs-lookup"><span data-stu-id="34fb2-198">**Miguel Veloso**, Sr. Consultant at Turing Challenge</span></span>

## <a name="copyright"></a><span data-ttu-id="34fb2-199">Prawo</span><span class="sxs-lookup"><span data-stu-id="34fb2-199">Copyright</span></span>

<span data-ttu-id="34fb2-200">Pobieranie dostępne o:<https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="34fb2-200">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="34fb2-201">OPUBLIKOWANO PRZEZ</span><span class="sxs-lookup"><span data-stu-id="34fb2-201">PUBLISHED BY</span></span>

<span data-ttu-id="34fb2-202">Dział deweloperów firmy Microsoft, zespoły produktów .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="34fb2-202">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="34fb2-203">Dział firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="34fb2-203">A division of Microsoft Corporation</span></span>

<span data-ttu-id="34fb2-204">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="34fb2-204">One Microsoft Way</span></span>

<span data-ttu-id="34fb2-205">Redmond, Waszyngton 98052-6399</span><span class="sxs-lookup"><span data-stu-id="34fb2-205">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="34fb2-206">Prawa autorskie © 2019 przez firmę Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="34fb2-206">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="34fb2-207">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="34fb2-207">All rights reserved.</span></span> <span data-ttu-id="34fb2-208">Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.</span><span class="sxs-lookup"><span data-stu-id="34fb2-208">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="34fb2-209">Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="34fb2-209">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="34fb2-210">Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="34fb2-210">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="34fb2-211">Niektóre przykłady opisane w niniejszym dokumencie są dostępne tylko dla ilustracji i są fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="34fb2-211">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="34fb2-212">Żadne prawdziwe skojarzenie lub połączenie nie jest zamierzone ani nie powinno zostać wywnioskowane.</span><span class="sxs-lookup"><span data-stu-id="34fb2-212">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="34fb2-213">Firma Microsoft i znaki towarowe <https://www.microsoft.com> wymienione na stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34fb2-213">Microsoft and the trademarks listed at <https://www.microsoft.com> on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="34fb2-214">Komputery Mac i macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="34fb2-214">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="34fb2-215">Logo Docker Whale jest zastrzeżonym znakiem towarowym platformy Docker, Inc. Używane przez uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="34fb2-215">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="34fb2-216">Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="34fb2-216">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="34fb2-217">Next</span><span class="sxs-lookup"><span data-stu-id="34fb2-217">Next</span></span>](container-docker-introduction/index.md)
