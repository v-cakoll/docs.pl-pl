---
title: Usługi danych WCF 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 1ce152b84f17a35982a75f54b5418623ba39210f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975232"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="2fb08-102">Usługi danych WCF 4.5</span><span class="sxs-lookup"><span data-stu-id="2fb08-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="2fb08-103">Usługi danych programu WCF (dawniej znany jako "ADO.NET Data Services") jest składnikiem .NET Framework, który umożliwia tworzenie usług korzystających z protokołu Open Data Protocol (OData) do udostępniania danych i korzystania z nich za pośrednictwem sieci Web lub intranet przy użyciu semantyki [przenoszenia stanu (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span><span class="sxs-lookup"><span data-stu-id="2fb08-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span></span> <span data-ttu-id="2fb08-104">Usługa OData udostępnia dane jako zasoby, które są adresowane przez identyfikatory URI.</span><span class="sxs-lookup"><span data-stu-id="2fb08-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="2fb08-105">Dostęp do danych jest uzyskiwany i zmieniany przy użyciu standardowych czasowników HTTP GET, PUT, POST i DELETE.</span><span class="sxs-lookup"><span data-stu-id="2fb08-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="2fb08-106">Usługa OData używa Konwencji relacji jednostek [Entity Data Model](../adonet/entity-data-model.md) , aby udostępnić zasoby jako zestawy jednostek, które są powiązane ze skojarzeniami.</span><span class="sxs-lookup"><span data-stu-id="2fb08-106">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="2fb08-107">Usługi danych programu WCF używa protokołu OData do adresowania i aktualizacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="2fb08-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="2fb08-108">W ten sposób można uzyskać dostęp do tych usług z dowolnego klienta, który obsługuje protokół OData.</span><span class="sxs-lookup"><span data-stu-id="2fb08-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="2fb08-109">Usługa OData umożliwia żądanie i zapisanie danych w zasobach przy użyciu dobrze znanych formatów transferu: Atom, zestaw standardów do wymiany i aktualizowania danych jako XML, a JavaScript Object Notation (JSON), format wymiany danych oparty na tekście, który jest szeroko używany w technologii AJAX zastosowania.</span><span class="sxs-lookup"><span data-stu-id="2fb08-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="2fb08-110">Usługi danych programu WCF mogą uwidaczniać dane pochodzące z różnych źródeł jako źródła danych OData.</span><span class="sxs-lookup"><span data-stu-id="2fb08-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="2fb08-111">Narzędzia programu Visual Studio ułatwiają tworzenie usługi opartej na protokole OData przy użyciu modelu danych ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2fb08-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="2fb08-112">Można również tworzyć źródła danych OData oparte na klasach środowiska uruchomieniowego języka wspólnego (CLR), a nawet z danymi z późnym wiązaniem lub bez typu.</span><span class="sxs-lookup"><span data-stu-id="2fb08-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="2fb08-113">Usługi danych programu WCF obejmuje również zestaw bibliotek klienckich, jeden dla ogólnych .NET Framework aplikacji klienckich, a drugi przeznaczony dla aplikacji opartych na technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="2fb08-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="2fb08-114">Te biblioteki klienckie zapewniają model programowania oparty na obiektach, gdy uzyskujesz dostęp do źródła danych OData ze środowisk, takich jak .NET Framework i Silverlight.</span><span class="sxs-lookup"><span data-stu-id="2fb08-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="2fb08-115">Gdzie należy zacząć?</span><span class="sxs-lookup"><span data-stu-id="2fb08-115">Where Should I Start?</span></span>

<span data-ttu-id="2fb08-116">W zależności od zainteresowań należy rozważyć wprowadzenie do Usługi danych programu WCF w jednym z poniższych tematów.</span><span class="sxs-lookup"><span data-stu-id="2fb08-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="2fb08-117">Chcę przeskoczyć do prawej strony...</span><span class="sxs-lookup"><span data-stu-id="2fb08-117">I want to jump right in...</span></span>

- [<span data-ttu-id="2fb08-118">Szybki start</span><span class="sxs-lookup"><span data-stu-id="2fb08-118">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="2fb08-119">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="2fb08-119">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

- [<span data-ttu-id="2fb08-120">Silverlight — Szybki Start</span><span class="sxs-lookup"><span data-stu-id="2fb08-120">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

- [<span data-ttu-id="2fb08-121">Samouczek szybki start dla programu Windows Phone Development</span><span class="sxs-lookup"><span data-stu-id="2fb08-121">Silverlight Quickstart for Windows Phone Development</span></span>](https://go.microsoft.com/fwlink/?LinkID=214535)

<span data-ttu-id="2fb08-122">Pokaż mi tylko jakiś kod...</span><span class="sxs-lookup"><span data-stu-id="2fb08-122">Just show me some code...</span></span>

- [<span data-ttu-id="2fb08-123">Szybki start</span><span class="sxs-lookup"><span data-stu-id="2fb08-123">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="2fb08-124">Instrukcje: Wykonywanie zapytań usługi danych</span><span class="sxs-lookup"><span data-stu-id="2fb08-124">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="2fb08-125">Instrukcje: Wiązanie danych do elementów systemu Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="2fb08-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="2fb08-126">Chcę dowiedzieć się więcej o usłudze OData...</span><span class="sxs-lookup"><span data-stu-id="2fb08-126">I want to know more about OData...</span></span>

- [<span data-ttu-id="2fb08-127">Oficjalny dokument: wprowadzenie do usługi OData</span><span class="sxs-lookup"><span data-stu-id="2fb08-127">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- [<span data-ttu-id="2fb08-128">Otwórz witrynę sieci Web protokołu Data Protocol</span><span class="sxs-lookup"><span data-stu-id="2fb08-128">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

- [<span data-ttu-id="2fb08-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="2fb08-129">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

- [<span data-ttu-id="2fb08-130">OData: często zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="2fb08-130">OData: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/?LinkId=185867)

<span data-ttu-id="2fb08-131">Chcę obejrzeć kilka filmów wideo...</span><span class="sxs-lookup"><span data-stu-id="2fb08-131">I want to watch some videos...</span></span>

- [<span data-ttu-id="2fb08-132">Przewodnik dla początkujących Usługi danych programu WCF</span><span class="sxs-lookup"><span data-stu-id="2fb08-132">Beginner's Guide to WCF Data Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=220864)

- [<span data-ttu-id="2fb08-133">Film wideo dla deweloperów Usługi danych programu WCF</span><span class="sxs-lookup"><span data-stu-id="2fb08-133">WCF Data Services Developer Videos</span></span>](https://go.microsoft.com/fwlink/?LinkId=220861)

- [<span data-ttu-id="2fb08-134">OData: Witryna sieci Web programistów</span><span class="sxs-lookup"><span data-stu-id="2fb08-134">OData: Developers Web site</span></span>](https://go.microsoft.com/fwlink/?LinkId=185866)

<span data-ttu-id="2fb08-135">Chcę zobaczyć kompleksowe przykłady...</span><span class="sxs-lookup"><span data-stu-id="2fb08-135">I want to see end-to-end samples...</span></span>

- [<span data-ttu-id="2fb08-136">Przykłady dokumentacji Usługi danych programu WCF w galerii przykładów MSDN</span><span class="sxs-lookup"><span data-stu-id="2fb08-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkID=220865)

- [<span data-ttu-id="2fb08-137">Inne przykłady Usługi danych programu WCF w galerii przykładów MSDN</span><span class="sxs-lookup"><span data-stu-id="2fb08-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkId=220866)

- [<span data-ttu-id="2fb08-138">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="2fb08-138">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

<span data-ttu-id="2fb08-139">Jak integruje się z programem Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="2fb08-139">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="2fb08-140">Generowanie biblioteki klienta usługi danych</span><span class="sxs-lookup"><span data-stu-id="2fb08-140">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="2fb08-141">Tworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="2fb08-141">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="2fb08-142">Dostawca programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2fb08-142">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="2fb08-143">Co mogę zrobić z nim?</span><span class="sxs-lookup"><span data-stu-id="2fb08-143">What can I do with it?</span></span>

- [<span data-ttu-id="2fb08-144">Omówienie</span><span class="sxs-lookup"><span data-stu-id="2fb08-144">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="2fb08-145">Oficjalny dokument: wprowadzenie do usługi OData</span><span class="sxs-lookup"><span data-stu-id="2fb08-145">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- [<span data-ttu-id="2fb08-146">Scenariusze aplikacji</span><span class="sxs-lookup"><span data-stu-id="2fb08-146">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="2fb08-147">Chcę użyć programu Silverlight...</span><span class="sxs-lookup"><span data-stu-id="2fb08-147">I want to use Silverlight...</span></span>

- [<span data-ttu-id="2fb08-148">Silverlight — Szybki Start</span><span class="sxs-lookup"><span data-stu-id="2fb08-148">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

- [<span data-ttu-id="2fb08-149">Usługi danych programu WCF (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="2fb08-149">WCF Data Services (Silverlight)</span></span>](https://go.microsoft.com/fwlink/?LinkID=143149)

- [<span data-ttu-id="2fb08-150">Wprowadzenie z technologią Silverlight</span><span class="sxs-lookup"><span data-stu-id="2fb08-150">Getting Started with Silverlight</span></span>](https://go.microsoft.com/fwlink/?LinkId=148366)

<span data-ttu-id="2fb08-151">Chcę użyć LINQ...</span><span class="sxs-lookup"><span data-stu-id="2fb08-151">I want to use LINQ...</span></span>

- [<span data-ttu-id="2fb08-152">Wykonywanie zapytań do usługi danych</span><span class="sxs-lookup"><span data-stu-id="2fb08-152">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="2fb08-153">Zagadnienia dotyczące LINQ</span><span class="sxs-lookup"><span data-stu-id="2fb08-153">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="2fb08-154">Instrukcje: Wykonywanie zapytań usługi danych</span><span class="sxs-lookup"><span data-stu-id="2fb08-154">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="2fb08-155">Nadal potrzebuję więcej informacji...</span><span class="sxs-lookup"><span data-stu-id="2fb08-155">I still need some more information...</span></span>

- [<span data-ttu-id="2fb08-156">Blog zespołu Usługi danych programu WCF</span><span class="sxs-lookup"><span data-stu-id="2fb08-156">WCF Data Services Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=150511)

- [<span data-ttu-id="2fb08-157">Zasoby</span><span class="sxs-lookup"><span data-stu-id="2fb08-157">Resources</span></span>](wcf-data-services-resources.md)

- [<span data-ttu-id="2fb08-158">Centrum deweloperów Usługi danych programu WCF</span><span class="sxs-lookup"><span data-stu-id="2fb08-158">WCF Data Services Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=220868)

- [<span data-ttu-id="2fb08-159">Otwórz witrynę sieci Web protokołu Data Protocol</span><span class="sxs-lookup"><span data-stu-id="2fb08-159">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a><span data-ttu-id="2fb08-160">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2fb08-160">In This Section</span></span>

[<span data-ttu-id="2fb08-161">Omówienie</span><span class="sxs-lookup"><span data-stu-id="2fb08-161">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="2fb08-162">Zawiera przegląd funkcji dostępnych w Usługi danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="2fb08-162">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="2fb08-163">[Co nowego w Usługi danych programu WCF 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="2fb08-163">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="2fb08-164">Opisuje nowe funkcje w Usługi danych programu WCF i obsługę nowych funkcji OData.</span><span class="sxs-lookup"><span data-stu-id="2fb08-164">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="2fb08-165">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="2fb08-165">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="2fb08-166">Opisuje sposób udostępniania i korzystania ze źródeł danych OData przy użyciu Usługi danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="2fb08-166">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="2fb08-167">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="2fb08-167">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="2fb08-168">Opisuje sposób tworzenia i konfigurowania usługi danych, która udostępnia źródła strumieniowego OData.</span><span class="sxs-lookup"><span data-stu-id="2fb08-168">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="2fb08-169">Biblioteka klienta usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="2fb08-169">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="2fb08-170">Opisuje sposób używania bibliotek klienckich do korzystania ze źródeł danych OData z aplikacji klienckiej .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2fb08-170">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fb08-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2fb08-171">See also</span></span>

- [<span data-ttu-id="2fb08-172">Przenoszenie stanu reprezentacji (REST)</span><span class="sxs-lookup"><span data-stu-id="2fb08-172">Representational State Transfer (REST)</span></span>](https://go.microsoft.com/fwlink/?LinkId=113919)
