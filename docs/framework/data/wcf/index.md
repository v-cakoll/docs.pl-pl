---
title: Usługi danych WCF 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: aace683b1a105445b5a3ba3de0a6a671859588b5
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937445"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="add23-102">Usługi danych WCF 4.5</span><span class="sxs-lookup"><span data-stu-id="add23-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="add23-103">Usługi danych programu WCF (dawniej znany jako "ADO.NET Data Services") jest składnikiem .NET Framework, który umożliwia tworzenie usług korzystających z protokołu Open Data Protocol (OData) do udostępniania danych i korzystania z nich za pośrednictwem sieci Web lub intranet przy użyciu semantyki [przenoszenia stanu (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span><span class="sxs-lookup"><span data-stu-id="add23-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="add23-104">Usługa OData udostępnia dane jako zasoby, które są adresowane przez identyfikatory URI.</span><span class="sxs-lookup"><span data-stu-id="add23-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="add23-105">Dostęp do danych jest uzyskiwany i zmieniany przy użyciu standardowych czasowników HTTP GET, PUT, POST i DELETE.</span><span class="sxs-lookup"><span data-stu-id="add23-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="add23-106">Usługa OData używa Konwencji relacji jednostek [Entity Data Model](../adonet/entity-data-model.md) , aby udostępnić zasoby jako zestawy jednostek, które są powiązane ze skojarzeniami.</span><span class="sxs-lookup"><span data-stu-id="add23-106">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="add23-107">Usługi danych programu WCF używa protokołu OData do adresowania i aktualizacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="add23-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="add23-108">W ten sposób można uzyskać dostęp do tych usług z dowolnego klienta, który obsługuje protokół OData.</span><span class="sxs-lookup"><span data-stu-id="add23-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="add23-109">Usługa OData umożliwia żądanie i zapisanie danych w zasobach przy użyciu dobrze znanych formatów transferu: Atom, zestaw standardów do wymiany i aktualizowania danych jako XML, a JavaScript Object Notation (JSON), format wymiany danych oparty na tekście, który jest szeroko używany w technologii AJAX zastosowania.</span><span class="sxs-lookup"><span data-stu-id="add23-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="add23-110">Usługi danych programu WCF mogą uwidaczniać dane pochodzące z różnych źródeł jako źródła danych OData.</span><span class="sxs-lookup"><span data-stu-id="add23-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="add23-111">Narzędzia programu Visual Studio ułatwiają tworzenie usługi opartej na protokole OData przy użyciu modelu danych ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="add23-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="add23-112">Można również tworzyć źródła danych OData oparte na klasach środowiska uruchomieniowego języka wspólnego (CLR), a nawet z danymi z późnym wiązaniem lub bez typu.</span><span class="sxs-lookup"><span data-stu-id="add23-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="add23-113">Usługi danych programu WCF obejmuje również zestaw bibliotek klienckich, jeden dla ogólnych .NET Framework aplikacji klienckich, a drugi przeznaczony dla aplikacji opartych na technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="add23-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="add23-114">Te biblioteki klienckie zapewniają model programowania oparty na obiektach, gdy uzyskujesz dostęp do źródła danych OData ze środowisk, takich jak .NET Framework i Silverlight.</span><span class="sxs-lookup"><span data-stu-id="add23-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="add23-115">Gdzie należy zacząć?</span><span class="sxs-lookup"><span data-stu-id="add23-115">Where Should I Start?</span></span>

<span data-ttu-id="add23-116">W zależności od zainteresowań należy rozważyć wprowadzenie do Usługi danych programu WCF w jednym z poniższych tematów.</span><span class="sxs-lookup"><span data-stu-id="add23-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="add23-117">Chcę przeskoczyć do prawej strony...</span><span class="sxs-lookup"><span data-stu-id="add23-117">I want to jump right in...</span></span>

- [<span data-ttu-id="add23-118">Szybki start</span><span class="sxs-lookup"><span data-stu-id="add23-118">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="add23-119">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="add23-119">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="add23-120">Pokaż mi tylko jakiś kod...</span><span class="sxs-lookup"><span data-stu-id="add23-120">Just show me some code...</span></span>

- [<span data-ttu-id="add23-121">Szybki start</span><span class="sxs-lookup"><span data-stu-id="add23-121">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="add23-122">Instrukcje: Wykonywanie zapytań usługi danych</span><span class="sxs-lookup"><span data-stu-id="add23-122">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="add23-123">Instrukcje: Wiązanie danych do elementów systemu Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="add23-123">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="add23-124">Chcę dowiedzieć się więcej o usłudze OData...</span><span class="sxs-lookup"><span data-stu-id="add23-124">I want to know more about OData...</span></span>

- [<span data-ttu-id="add23-125">Oficjalny dokument: wprowadzenie do usługi OData</span><span class="sxs-lookup"><span data-stu-id="add23-125">White paper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="add23-126">Otwórz witrynę internetową protokołu danych</span><span class="sxs-lookup"><span data-stu-id="add23-126">Open Data Protocol website</span></span>](https://www.odata.org/)
- [<span data-ttu-id="add23-127">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="add23-127">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="add23-128">Chcę zobaczyć kompleksowe przykłady...</span><span class="sxs-lookup"><span data-stu-id="add23-128">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="add23-129">[Usługi danych programu WCF — Szybki Start](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="add23-129">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="add23-130">Zestaw SDK OData — przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="add23-130">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="add23-131">Jak integruje się z programem Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="add23-131">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="add23-132">Generowanie biblioteki klienta usługi danych</span><span class="sxs-lookup"><span data-stu-id="add23-132">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="add23-133">Tworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="add23-133">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="add23-134">Dostawca programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="add23-134">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="add23-135">Co mogę zrobić z nim?</span><span class="sxs-lookup"><span data-stu-id="add23-135">What can I do with it?</span></span>

- [<span data-ttu-id="add23-136">Omówienie</span><span class="sxs-lookup"><span data-stu-id="add23-136">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="add23-137">Scenariusze aplikacji</span><span class="sxs-lookup"><span data-stu-id="add23-137">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="add23-138">Chcę użyć LINQ...</span><span class="sxs-lookup"><span data-stu-id="add23-138">I want to use LINQ...</span></span>

- [<span data-ttu-id="add23-139">Wykonywanie zapytań do usługi danych</span><span class="sxs-lookup"><span data-stu-id="add23-139">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="add23-140">Zagadnienia dotyczące LINQ</span><span class="sxs-lookup"><span data-stu-id="add23-140">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="add23-141">Instrukcje: Wykonywanie zapytań usługi danych</span><span class="sxs-lookup"><span data-stu-id="add23-141">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="add23-142">Nadal potrzebuję więcej informacji...</span><span class="sxs-lookup"><span data-stu-id="add23-142">I still need some more information...</span></span>

- [<span data-ttu-id="add23-143">Blog zespołu Usługi danych programu WCF</span><span class="sxs-lookup"><span data-stu-id="add23-143">WCF Data Services Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/astoriateam/)

- [<span data-ttu-id="add23-144">Zasoby</span><span class="sxs-lookup"><span data-stu-id="add23-144">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="add23-145">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="add23-145">In This Section</span></span>

[<span data-ttu-id="add23-146">Omówienie</span><span class="sxs-lookup"><span data-stu-id="add23-146">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="add23-147">Zawiera przegląd funkcji dostępnych w Usługi danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="add23-147">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="add23-148">[Co nowego w Usługi danych programu WCF 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="add23-148">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="add23-149">Opisuje nowe funkcje w Usługi danych programu WCF i obsługę nowych funkcji OData.</span><span class="sxs-lookup"><span data-stu-id="add23-149">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="add23-150">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="add23-150">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="add23-151">Opisuje sposób udostępniania i korzystania ze źródeł danych OData przy użyciu Usługi danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="add23-151">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="add23-152">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="add23-152">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="add23-153">Opisuje sposób tworzenia i konfigurowania usługi danych, która udostępnia źródła strumieniowego OData.</span><span class="sxs-lookup"><span data-stu-id="add23-153">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="add23-154">Biblioteka klienta usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="add23-154">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="add23-155">Opisuje sposób używania bibliotek klienckich do korzystania ze źródeł danych OData z aplikacji klienckiej .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="add23-155">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="add23-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="add23-156">See also</span></span>

- [<span data-ttu-id="add23-157">Przenoszenie stanu reprezentacji (REST)</span><span class="sxs-lookup"><span data-stu-id="add23-157">Representational State Transfer (REST)</span></span>](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
