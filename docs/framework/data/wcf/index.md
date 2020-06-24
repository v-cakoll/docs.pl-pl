---
title: Usługi danych WCF 4.5
description: Informacje na temat Usługi danych programu WCF, składnika .NET Framework, który obsługuje usługi umożliwiające udostępnianie i używanie danych przy użyciu semantyki REST.
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: ca6b196e8c910f97ead6d1df5b6c0dd6c49c68a4
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247755"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="95330-103">Usługi danych WCF 4.5</span><span class="sxs-lookup"><span data-stu-id="95330-103">WCF Data Services 4.5</span></span>

<span data-ttu-id="95330-104">Usługi danych programu WCF (dawniej znany jako "ADO.NET Data Services") jest składnikiem .NET Framework, który umożliwia tworzenie usług korzystających z protokołu Open Data Protocol (OData) do udostępniania danych i korzystania z nich za pośrednictwem sieci Web lub intranet przy użyciu semantyki [przenoszenia stanu (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span><span class="sxs-lookup"><span data-stu-id="95330-104">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="95330-105">Usługa OData udostępnia dane jako zasoby, które są adresowane przez identyfikatory URI.</span><span class="sxs-lookup"><span data-stu-id="95330-105">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="95330-106">Dostęp do danych jest uzyskiwany i zmieniany przy użyciu standardowych czasowników HTTP GET, PUT, POST i DELETE.</span><span class="sxs-lookup"><span data-stu-id="95330-106">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="95330-107">Usługa OData używa Konwencji relacji jednostek [Entity Data Model](../adonet/entity-data-model.md) , aby udostępnić zasoby jako zestawy jednostek, które są powiązane ze skojarzeniami.</span><span class="sxs-lookup"><span data-stu-id="95330-107">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="95330-108">Usługi danych programu WCF używa protokołu OData do adresowania i aktualizacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="95330-108">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="95330-109">W ten sposób można uzyskać dostęp do tych usług z dowolnego klienta, który obsługuje protokół OData.</span><span class="sxs-lookup"><span data-stu-id="95330-109">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="95330-110">Usługa OData umożliwia żądanie i zapisanie danych w zasobach przy użyciu dobrze znanych formatów transferu: Atom, zestaw standardów do wymiany i aktualizowania danych jako XML, a JavaScript Object Notation (JSON), format wymiany danych oparty na tekście, który jest szeroko używany w aplikacjach AJAX.</span><span class="sxs-lookup"><span data-stu-id="95330-110">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="95330-111">Usługi danych programu WCF mogą uwidaczniać dane pochodzące z różnych źródeł jako źródła danych OData.</span><span class="sxs-lookup"><span data-stu-id="95330-111">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="95330-112">Narzędzia programu Visual Studio ułatwiają tworzenie usługi opartej na protokole OData przy użyciu modelu danych ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="95330-112">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="95330-113">Można również tworzyć źródła danych OData oparte na klasach środowiska uruchomieniowego języka wspólnego (CLR), a nawet z danymi z późnym wiązaniem lub bez typu.</span><span class="sxs-lookup"><span data-stu-id="95330-113">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="95330-114">Usługi danych programu WCF obejmuje również zestaw bibliotek klienckich, jeden dla ogólnych .NET Framework aplikacji klienckich, a drugi przeznaczony dla aplikacji opartych na technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="95330-114">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="95330-115">Te biblioteki klienckie zapewniają model programowania oparty na obiektach, gdy uzyskujesz dostęp do źródła danych OData ze środowisk, takich jak .NET Framework i Silverlight.</span><span class="sxs-lookup"><span data-stu-id="95330-115">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="95330-116">Gdzie należy zacząć?</span><span class="sxs-lookup"><span data-stu-id="95330-116">Where Should I Start?</span></span>

<span data-ttu-id="95330-117">W zależności od zainteresowań należy rozważyć wprowadzenie do Usługi danych programu WCF w jednym z poniższych tematów.</span><span class="sxs-lookup"><span data-stu-id="95330-117">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="95330-118">Chcę przeskoczyć do prawej strony...</span><span class="sxs-lookup"><span data-stu-id="95330-118">I want to jump right in...</span></span>

- [<span data-ttu-id="95330-119">Szybki start</span><span class="sxs-lookup"><span data-stu-id="95330-119">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="95330-120">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="95330-120">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="95330-121">Pokaż mi tylko jakiś kod...</span><span class="sxs-lookup"><span data-stu-id="95330-121">Just show me some code...</span></span>

- [<span data-ttu-id="95330-122">Szybki start</span><span class="sxs-lookup"><span data-stu-id="95330-122">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="95330-123">Instrukcje: Wykonywanie zapytań usługi danych</span><span class="sxs-lookup"><span data-stu-id="95330-123">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="95330-124">Instrukcje: Wiązanie danych do elementów systemu Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="95330-124">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="95330-125">Chcę dowiedzieć się więcej o usłudze OData...</span><span class="sxs-lookup"><span data-stu-id="95330-125">I want to know more about OData...</span></span>

- [<span data-ttu-id="95330-126">Oficjalny dokument: wprowadzenie do usługi OData</span><span class="sxs-lookup"><span data-stu-id="95330-126">White paper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="95330-127">Otwórz witrynę internetową protokołu danych</span><span class="sxs-lookup"><span data-stu-id="95330-127">Open Data Protocol website</span></span>](https://www.odata.org/)
- [<span data-ttu-id="95330-128">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="95330-128">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="95330-129">Chcę zobaczyć kompleksowe przykłady...</span><span class="sxs-lookup"><span data-stu-id="95330-129">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="95330-130">[Usługi danych programu WCF — Szybki Start](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="95330-130">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="95330-131">Zestaw SDK OData — przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="95330-131">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="95330-132">Jak integruje się z programem Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="95330-132">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="95330-133">Generowanie biblioteki klienta usługi danych</span><span class="sxs-lookup"><span data-stu-id="95330-133">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="95330-134">Tworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="95330-134">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="95330-135">Dostawca programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="95330-135">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="95330-136">Co mogę zrobić z nim?</span><span class="sxs-lookup"><span data-stu-id="95330-136">What can I do with it?</span></span>

- [<span data-ttu-id="95330-137">Omówienie</span><span class="sxs-lookup"><span data-stu-id="95330-137">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="95330-138">Scenariusze aplikacji</span><span class="sxs-lookup"><span data-stu-id="95330-138">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="95330-139">Chcę użyć LINQ...</span><span class="sxs-lookup"><span data-stu-id="95330-139">I want to use LINQ...</span></span>

- [<span data-ttu-id="95330-140">Wykonywanie zapytań do usługi danych</span><span class="sxs-lookup"><span data-stu-id="95330-140">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="95330-141">Zagadnienia dotyczące LINQ</span><span class="sxs-lookup"><span data-stu-id="95330-141">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="95330-142">Instrukcje: Wykonywanie zapytań usługi danych</span><span class="sxs-lookup"><span data-stu-id="95330-142">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="95330-143">Nadal potrzebuję więcej informacji...</span><span class="sxs-lookup"><span data-stu-id="95330-143">I still need some more information...</span></span>

- [<span data-ttu-id="95330-144">Blog zespołu Usługi danych programu WCF</span><span class="sxs-lookup"><span data-stu-id="95330-144">WCF Data Services Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/astoriateam/)

- [<span data-ttu-id="95330-145">Zasoby</span><span class="sxs-lookup"><span data-stu-id="95330-145">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="95330-146">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="95330-146">In This Section</span></span>

[<span data-ttu-id="95330-147">Omówienie</span><span class="sxs-lookup"><span data-stu-id="95330-147">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="95330-148">Zawiera przegląd funkcji dostępnych w Usługi danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="95330-148">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="95330-149">[Co nowego w Usługi danych programu WCF 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="95330-149">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="95330-150">Opisuje nowe funkcje w Usługi danych programu WCF i obsługę nowych funkcji OData.</span><span class="sxs-lookup"><span data-stu-id="95330-150">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="95330-151">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="95330-151">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="95330-152">Opisuje sposób udostępniania i korzystania ze źródeł danych OData przy użyciu Usługi danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="95330-152">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="95330-153">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="95330-153">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="95330-154">Opisuje sposób tworzenia i konfigurowania usługi danych, która udostępnia źródła strumieniowego OData.</span><span class="sxs-lookup"><span data-stu-id="95330-154">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="95330-155">Biblioteka klienta usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="95330-155">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="95330-156">Opisuje sposób używania bibliotek klienckich do korzystania ze źródeł danych OData z aplikacji klienckiej .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95330-156">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="95330-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95330-157">See also</span></span>

- [<span data-ttu-id="95330-158">Przenoszenie stanu reprezentacji (REST)</span><span class="sxs-lookup"><span data-stu-id="95330-158">Representational State Transfer (REST)</span></span>](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
