---
title: Mikrousługi platformy .NET. architektura konteneryzowanych aplikacji .NET
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Mikrousługi są modularne i niezależnie do wdrożenia usługi. Kontenery platformy Docker (dla systemów Linux i Windows) upraszczają wdrażanie i testowanie poprzez zgrupowanie usługi i jej zależności w pojedynczą jednostkę, która jest uruchamiana w środowisku izolowanym.
ms.date: 01/30/2020
ms.openlocfilehash: 5da167de1ffd2169aea44b9872281e71c87927b1
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502634"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="59cd3-105">Mikrousługi platformy .NET: architektura dla kontenerów aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="59cd3-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Pokrycie książki](./media/cover-small.png)

<span data-ttu-id="59cd3-107">**Edition w wersji 3.1** — zaktualizowany do ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="59cd3-107">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="59cd3-108">Ten przewodnik stanowi wprowadzenie do tworzenia aplikacji opartych na mikrousługach i zarządzania nimi przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="59cd3-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="59cd3-109">Omówiono podejścia projektowania i implementacji architektury przy użyciu programu .NET Core i kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="59cd3-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span>

<span data-ttu-id="59cd3-110">Aby ułatwić rozpoczęcie pracy, przewodnik koncentruje się na odniesieniu do aplikacji opartej na kontenerach i mikrousługach, które można eksplorować.</span><span class="sxs-lookup"><span data-stu-id="59cd3-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="59cd3-111">Aplikacja referencyjna jest dostępna w repozytorium GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .</span><span class="sxs-lookup"><span data-stu-id="59cd3-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="59cd3-112">Linki akcji</span><span class="sxs-lookup"><span data-stu-id="59cd3-112">Action links</span></span>

- <span data-ttu-id="59cd3-113">Pobierz tę książkę elektroniczną w wybranym formacie (tylko w języku angielskim): | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-epub) |</span><span class="sxs-lookup"><span data-stu-id="59cd3-113">Download this e-book in your format of choice (English version only): | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-epub) |</span></span>

- <span data-ttu-id="59cd3-114">Klonowanie/rozwidlenie aplikacji referencyjnej [eShopOnContainers w witrynie GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="59cd3-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="59cd3-115">Obejrzyj [film wprowadzający w witrynie Channel 9](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="59cd3-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="59cd3-116">Uzyskaj informacje o [architekturze mikrousług](https://aka.ms/MicroservicesArchitecture) od razu</span><span class="sxs-lookup"><span data-stu-id="59cd3-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="59cd3-117">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="59cd3-117">Introduction</span></span>

<span data-ttu-id="59cd3-118">Przedsiębiorstwa są coraz bardziej kosztowne, rozwiązując problemy z wdrażaniem i ulepszają operacje DevOps i produkcyjne przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="59cd3-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="59cd3-119">Firma Microsoft wyłączyła innowacje dotyczące kontenerów dla systemów Windows i Linux, tworząc produkty takie jak Azure Kubernetes Service i Azure Service Fabric, a przez partnerskie liderów branżowych, takich jak Docker, mesosphere i Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="59cd3-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="59cd3-120">Te produkty dostarczają rozwiązania kontenerów, które ułatwiają firmom Kompilowanie i wdrażanie aplikacji na dużą skalę i skalowalność, niezależnie od ich wyboru platformy lub narzędzi.</span><span class="sxs-lookup"><span data-stu-id="59cd3-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="59cd3-121">Platforma Docker staje się niefaktycznym standardem w branży kontenerów, która jest obsługiwana przez najbardziej znaczących dostawców w ekosystemach systemów Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="59cd3-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="59cd3-122">(Firma Microsoft jest jednym z głównych dostawców chmury obsługujących platformę Docker). W przyszłości platforma Docker będzie prawdopodobnie ogólnie oparta na dowolnym centrum danych w chmurze lub lokalnie.</span><span class="sxs-lookup"><span data-stu-id="59cd3-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="59cd3-123">Ponadto architektura [mikrousług](https://martinfowler.com/articles/microservices.html) pojawia się jako ważne podejście do rozproszonych aplikacji o krytycznym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="59cd3-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="59cd3-124">W architekturze mikrousług aplikacja jest tworzona na podstawie kolekcji usług, które mogą być opracowane, przetestowane, wdrożone i niezależne od wersji.</span><span class="sxs-lookup"><span data-stu-id="59cd3-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="59cd3-125">O tym przewodniku</span><span class="sxs-lookup"><span data-stu-id="59cd3-125">About this guide</span></span>

<span data-ttu-id="59cd3-126">Ten przewodnik stanowi wprowadzenie do tworzenia aplikacji opartych na mikrousługach i zarządzania nimi przy użyciu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="59cd3-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="59cd3-127">Omówiono podejścia projektowania i implementacji architektury przy użyciu programu .NET Core i kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="59cd3-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="59cd3-128">Aby ułatwić rozpoczęcie pracy z kontenerami i mikrousług, przewodnik koncentruje się na odwołaniach do aplikacji opartych na kontenerach i mikrousługach, które można eksplorować.</span><span class="sxs-lookup"><span data-stu-id="59cd3-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="59cd3-129">Przykładowa aplikacja jest dostępna w repozytorium GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .</span><span class="sxs-lookup"><span data-stu-id="59cd3-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="59cd3-130">Ten przewodnik zawiera podstawowe wskazówki dotyczące programowania i architektury w środowisku programistycznym, które koncentrują się na dwóch technologiach: Docker i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="59cd3-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="59cd3-131">Naszym zamiarem jest zapoznanie się z tym przewodnikiem, gdy myślisz o projekcie aplikacji bez skoncentrowania się na infrastrukturze (w chmurze lub lokalnie) w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="59cd3-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="59cd3-132">Decyzje o infrastrukturze będą podejmowane później, podczas tworzenia aplikacji gotowych do produkcji.</span><span class="sxs-lookup"><span data-stu-id="59cd3-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="59cd3-133">W związku z tym ten przewodnik jest przeznaczony dla infrastruktury niezależny od i większej ilości środowiska programistycznego.</span><span class="sxs-lookup"><span data-stu-id="59cd3-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="59cd3-134">Po przeprowadzeniu tego przewodnika następnym krokiem jest zapoznanie się z mikrousługami gotowymi do produkcji na Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="59cd3-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="59cd3-135">Wersja</span><span class="sxs-lookup"><span data-stu-id="59cd3-135">Version</span></span>

<span data-ttu-id="59cd3-136">Ten przewodnik został zmieniony w celu uwzględnienia wersji **programu .NET Core 3,1** wraz z wieloma dodatkowymi aktualizacjami związanymi z tym samymi "" Wave "technologiami (czyli platformą Azure i dodatkowymi technologiami innych firm), które są zgodne z wersją platformy .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="59cd3-136">This guide has been revised to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="59cd3-137">Dlatego też wersja książki została zaktualizowana do wersji **3,1**.</span><span class="sxs-lookup"><span data-stu-id="59cd3-137">That’s why the book version has also been updated to version **3.1**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="59cd3-138">Czym nie obejmuje ten przewodnik</span><span class="sxs-lookup"><span data-stu-id="59cd3-138">What this guide does not cover</span></span>

<span data-ttu-id="59cd3-139">Ten przewodnik nie koncentruje się na potoku cyklu życia aplikacji, DevOps, ciągłej integracji/ciągłego wdrażania lub pracy zespołu.</span><span class="sxs-lookup"><span data-stu-id="59cd3-139">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="59cd3-140">Przewodnik uzupełniający [zadokowany cykl życia aplikacji platformy Docker z platformą i narzędziami firmy Microsoft](https://aka.ms/dockerlifecycleebook) koncentrują się na tym temacie.</span><span class="sxs-lookup"><span data-stu-id="59cd3-140">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="59cd3-141">Bieżący przewodnik nie zawiera również szczegółowych informacji dotyczących implementacji infrastruktury platformy Azure, takich jak informacje dotyczące określonych koordynatorów.</span><span class="sxs-lookup"><span data-stu-id="59cd3-141">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="59cd3-142">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="59cd3-142">Additional resources</span></span>

- <span data-ttu-id="59cd3-143">**Cykl życia aplikacji platformy Docker w kontenerze z platformą i narzędziami firmy Microsoft (do** pobrania książek elektronicznych)</span><span class="sxs-lookup"><span data-stu-id="59cd3-143">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="59cd3-144">Kto powinien korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="59cd3-144">Who should use this guide</span></span>

<span data-ttu-id="59cd3-145">Ten przewodnik został napisany dla deweloperów i architektów rozwiązań, które są nowe dla tworzenia aplikacji opartych na platformie Docker oraz architektury opartej na mikrousługach.</span><span class="sxs-lookup"><span data-stu-id="59cd3-145">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="59cd3-146">Ten przewodnik jest przeznaczony dla Ciebie, jeśli chcesz dowiedzieć się, jak architektować, projektować i wdrażać aplikacje do weryfikacji koncepcji za pomocą technologii programistycznych firmy Microsoft (ze specjalnym skoncentrowaniem się na platformie .NET Core) i z kontenerami platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="59cd3-146">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="59cd3-147">Ten przewodnik będzie również przydatny, jeśli jesteś specjalistą ds. decyzji, na przykład z architektem przedsiębiorstwa, który chce zapoznać się z architekturą i technologią, przed podjęciem decyzji o wyborze podejścia do nowych i nowoczesnych aplikacji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="59cd3-147">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="59cd3-148">Jak korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="59cd3-148">How to use this guide</span></span>

<span data-ttu-id="59cd3-149">Pierwsza część tego przewodnika zawiera wprowadzenie do kontenerów platformy Docker, w jaki sposób można wybrać platformę .NET Core i .NET Framework jako strukturę programistyczną oraz Omówienie mikrousług.</span><span class="sxs-lookup"><span data-stu-id="59cd3-149">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="59cd3-150">Ta zawartość jest przeznaczony dla architektów i osób podejmujących decyzje techniczne, którzy chcą zapoznać się z omówieniem, ale nie muszą skupić się na szczegółach implementacji kodu.</span><span class="sxs-lookup"><span data-stu-id="59cd3-150">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="59cd3-151">Druga część przewodnika rozpoczyna się od [procesu opracowywania aplikacji opartych na platformie Docker](./docker-application-development-process/index.md) .</span><span class="sxs-lookup"><span data-stu-id="59cd3-151">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="59cd3-152">Koncentruje się na wzorcach deweloperskich i mikrousług związanych z wdrażaniem aplikacji przy użyciu oprogramowania .NET Core i Docker.</span><span class="sxs-lookup"><span data-stu-id="59cd3-152">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="59cd3-153">Ta sekcja będzie najbardziej interesująca dla deweloperów i architektów, którzy chcą skupić się na kodzie oraz o wzorcach i szczegółach implementacji.</span><span class="sxs-lookup"><span data-stu-id="59cd3-153">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="59cd3-154">Powiązana mikrousługa i aplikacja referencyjna oparta na kontenerach: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="59cd3-154">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="59cd3-155">Aplikacja eShopOnContainers to aplikacja referencyjna Open Source dla platformy .NET Core i mikrousług, która została zaprojektowana do wdrożenia przy użyciu kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="59cd3-155">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="59cd3-156">Aplikacja składa się z wielu podsystemów, w tym kilku frontonów interfejsu użytkownika w postaci elektronicznej (aplikacji sieci Web MVC, SPA sieci Web i natywnej aplikacji mobilnej).</span><span class="sxs-lookup"><span data-stu-id="59cd3-156">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="59cd3-157">Obejmuje ona również mikrousługi i kontenery zaplecza dla wszystkich wymaganych operacji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="59cd3-157">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="59cd3-158">Celem aplikacji jest zaprezentowanie wzorców architektonicznych.</span><span class="sxs-lookup"><span data-stu-id="59cd3-158">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="59cd3-159">**Nie jest to szablon gotowy** do uruchomienia aplikacji w rzeczywistości.</span><span class="sxs-lookup"><span data-stu-id="59cd3-159">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="59cd3-160">W rzeczywistości aplikacja jest w stanie stałego stanu beta, ponieważ jest również używana do testowania nowych potencjalnie interesujących technologii w miarę ich wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="59cd3-160">In fact, the application is in a permanent beta state, as it’s also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="59cd3-161">Wyślij nam swoją opinię.</span><span class="sxs-lookup"><span data-stu-id="59cd3-161">Send us your feedback!</span></span>

<span data-ttu-id="59cd3-162">Utworzyliśmy ten przewodnik, aby ułatwić zrozumienie architektury aplikacji i mikrousług w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="59cd3-162">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="59cd3-163">Przewodnik i powiązana aplikacja referencyjna będą rozwijane, więc będziemy nam powitać Twoją opinię.</span><span class="sxs-lookup"><span data-stu-id="59cd3-163">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="59cd3-164">Jeśli masz komentarze dotyczące tego, jak można ulepszyć ten przewodnik, wyślij je do:</span><span class="sxs-lookup"><span data-stu-id="59cd3-164">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a><span data-ttu-id="59cd3-165">Środki</span><span class="sxs-lookup"><span data-stu-id="59cd3-165">Credits</span></span>

<span data-ttu-id="59cd3-166">Współautorzy:</span><span class="sxs-lookup"><span data-stu-id="59cd3-166">Co-Authors:</span></span>

> <span data-ttu-id="59cd3-167">**Cesar de La Torre**, SR. PM, zespół produktu .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="59cd3-167">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="59cd3-168">**Bill Wagner**, SR. Content Developer, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="59cd3-168">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="59cd3-169">**Jan Rousos**, główny inżynier ds. oprogramowania, DevDiv kot, firma Microsoft</span><span class="sxs-lookup"><span data-stu-id="59cd3-169">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="59cd3-170">Edytory</span><span class="sxs-lookup"><span data-stu-id="59cd3-170">Editors:</span></span>

> <span data-ttu-id="59cd3-171">**Jan Pope**</span><span class="sxs-lookup"><span data-stu-id="59cd3-171">**Mike Pope**</span></span>
>
> <span data-ttu-id="59cd3-172">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="59cd3-172">**Steve Hoag**</span></span>

<span data-ttu-id="59cd3-173">Uczestnicy i recenzenci:</span><span class="sxs-lookup"><span data-stu-id="59cd3-173">Participants and reviewers:</span></span>

> <span data-ttu-id="59cd3-174">**Jeffrey Richter**, partner Software aparatu, Azure Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="59cd3-174">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="59cd3-175">**Jimmy Bogard**, główny architekt w headspring</span><span class="sxs-lookup"><span data-stu-id="59cd3-175">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="59cd3-176">**UDI Dahan**, założyciel & dyrektor naczelny, szczególne oprogramowanie</span><span class="sxs-lookup"><span data-stu-id="59cd3-176">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="59cd3-177">**Jimmy Nilsson**, współzałożyciel i dyrektor naczelny Factor10</span><span class="sxs-lookup"><span data-stu-id="59cd3-177">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="59cd3-178">**Glenn Condron**, SR. Program Manager, zespół ASP.NET</span><span class="sxs-lookup"><span data-stu-id="59cd3-178">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="59cd3-179">**Mark Fussell**, podmiotu z potencjalnym klientem PM, Azure Service Fabric Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="59cd3-179">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="59cd3-180">**Diego Vega**, klient PM, Entity Framework zespół, Microsoft</span><span class="sxs-lookup"><span data-stu-id="59cd3-180">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="59cd3-181">**Marcin Dorrans**, SR. Security — Menedżer programów</span><span class="sxs-lookup"><span data-stu-id="59cd3-181">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="59cd3-182">**Rowan Miller**, SR. Program Manager, Microsoft</span><span class="sxs-lookup"><span data-stu-id="59cd3-182">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="59cd3-183">**Autor Ankit Asthana**, kierownik ds. platformy PM, zespół .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="59cd3-183">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="59cd3-184">**Scott myśliwy**, dyrektor ds. partnerów, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="59cd3-184">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="59cd3-185">**Nish Anil**, SR. Program Manager, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="59cd3-185">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="59cd3-186">**Dylan Reisenberger**, architekt i dev ołów w Polly</span><span class="sxs-lookup"><span data-stu-id="59cd3-186">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="59cd3-187">**Steve "ardalis" Smith** — architekt oprogramowania i Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="59cd3-187">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="59cd3-188">**Ian Cooper**, architekt programowania na jaśniejszy</span><span class="sxs-lookup"><span data-stu-id="59cd3-188">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="59cd3-189">**Unai Zorrilla**, architekt i dev ołów z zwykłymi pojęciami</span><span class="sxs-lookup"><span data-stu-id="59cd3-189">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="59cd3-190">**Eduard Tomas**, dev ołów z zwykłymi pojęciami</span><span class="sxs-lookup"><span data-stu-id="59cd3-190">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="59cd3-191">**Ramon Tomas**, deweloper z zwykłymi pojęciami</span><span class="sxs-lookup"><span data-stu-id="59cd3-191">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="59cd3-192">**David Sanz**, deweloper z zwykłymi pojęciami</span><span class="sxs-lookup"><span data-stu-id="59cd3-192">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="59cd3-193">**Javier Valero**, dyrektor ds. operacyjnych w Grupo Solutio</span><span class="sxs-lookup"><span data-stu-id="59cd3-193">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="59cd3-194">**Pierre Millet**, SR. konsultant, Microsoft</span><span class="sxs-lookup"><span data-stu-id="59cd3-194">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="59cd3-195">**Michael Friis**, menedżer produktu, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="59cd3-195">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="59cd3-196">**Charles Lowell**, inżynier ds. oprogramowania, zespół programu vs Cat, Microsoft</span><span class="sxs-lookup"><span data-stu-id="59cd3-196">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="59cd3-197">**Miguel Veloso**, inżynier ds. opracowywania oprogramowania z zwykłymi pojęciami</span><span class="sxs-lookup"><span data-stu-id="59cd3-197">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>

## <a name="copyright"></a><span data-ttu-id="59cd3-198">Prawo</span><span class="sxs-lookup"><span data-stu-id="59cd3-198">Copyright</span></span>

<span data-ttu-id="59cd3-199">Pobieranie dostępne o: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="59cd3-199">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="59cd3-200">OPUBLIKOWANO PRZEZ</span><span class="sxs-lookup"><span data-stu-id="59cd3-200">PUBLISHED BY</span></span>

<span data-ttu-id="59cd3-201">Dział deweloperów firmy Microsoft, zespoły produktów .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="59cd3-201">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="59cd3-202">Dział firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="59cd3-202">A division of Microsoft Corporation</span></span>

<span data-ttu-id="59cd3-203">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="59cd3-203">One Microsoft Way</span></span>

<span data-ttu-id="59cd3-204">Redmond, Waszyngton 98052-6399</span><span class="sxs-lookup"><span data-stu-id="59cd3-204">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="59cd3-205">Prawa autorskie © 2020 przez firmę Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="59cd3-205">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="59cd3-206">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="59cd3-206">All rights reserved.</span></span> <span data-ttu-id="59cd3-207">Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.</span><span class="sxs-lookup"><span data-stu-id="59cd3-207">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="59cd3-208">Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="59cd3-208">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="59cd3-209">Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="59cd3-209">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="59cd3-210">Niektóre przykłady opisane w niniejszym dokumencie są dostępne tylko dla ilustracji i są fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="59cd3-210">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="59cd3-211">Żadne prawdziwe skojarzenie lub połączenie nie jest zamierzone ani nie powinno zostać wywnioskowane.</span><span class="sxs-lookup"><span data-stu-id="59cd3-211">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="59cd3-212">Firma Microsoft i znaki towarowe wymienione w <https://www.microsoft.com> na stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="59cd3-212">Microsoft and the trademarks listed at <https://www.microsoft.com> on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="59cd3-213">Komputery Mac i macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="59cd3-213">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="59cd3-214">Logo Docker Whale jest zastrzeżonym znakiem towarowym platformy Docker, Inc. używanym przez uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="59cd3-214">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="59cd3-215">Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="59cd3-215">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="59cd3-216">Dalej</span><span class="sxs-lookup"><span data-stu-id="59cd3-216">Next</span></span>](container-docker-introduction/index.md)
