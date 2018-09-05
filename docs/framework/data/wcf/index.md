---
title: Usługi danych WCF 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 9ece2fe051855d0fd39556f56a4343ead2c437bc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565801"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="98c01-102">Usługi danych WCF 4.5</span><span class="sxs-lookup"><span data-stu-id="98c01-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="98c01-103">Usługi danych WCF (wcześniej znane jako "Architektury ADO.NET Data Services") jest składnikiem programu .NET Framework, która umożliwia tworzenie usług, które używają [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] do prezentowania i wykorzystywania danych w Internecie lub intranecie przy użyciu semantyki [ (REST) Representational state transfer](https://go.microsoft.com/fwlink/?LinkId=113919).</span><span class="sxs-lookup"><span data-stu-id="98c01-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span></span> <span data-ttu-id="98c01-104">OData przedstawia dane w postaci zasobów, które są adresowane przez identyfikatory URI.</span><span class="sxs-lookup"><span data-stu-id="98c01-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="98c01-105">Dane są dostępne i zmieniać przy użyciu standardowych poleceń HTTP elementu GET, PUT, POST i DELETE.</span><span class="sxs-lookup"><span data-stu-id="98c01-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="98c01-106">OData używa konwencji Relacja jednostki [modelu Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) aby uwidocznić zasoby jako zestawów jednostek, które są powiązane przez skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="98c01-106">OData uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="98c01-107">Usługi danych WCF korzysta z protokołu OData do adresowania i aktualizowania zasobów.</span><span class="sxs-lookup"><span data-stu-id="98c01-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="98c01-108">W ten sposób uzyskujesz dostęp do tych usług, za pomocą dowolnego klienta, który obsługuje OData.</span><span class="sxs-lookup"><span data-stu-id="98c01-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="98c01-109">OData pozwala na żądania i zapisać dane do zasobów przy użyciu formatów transferowania dobrze znanych: Atom, zestaw standardów wymianę i aktualizowanie danych w formacie XML i JavaScript Object Notation (JSON), formatem wymiany danych tekstowych, często używane w technologii AJAX aplikacja.</span><span class="sxs-lookup"><span data-stu-id="98c01-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX application.</span></span>

<span data-ttu-id="98c01-110">Usługi danych WCF można ujawnić dane, które pochodzą z różnych źródeł, jako źródła OData.</span><span class="sxs-lookup"><span data-stu-id="98c01-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="98c01-111">Narzędzia programu Visual Studio ułatwiają tworzenie usługi OData przy użyciu modelu danych ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="98c01-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="98c01-112">Można również utworzyć źródła danych OData na podstawie wspólnej klasy środowiska uruchomieniowego (języka wspólnego CLR) języka i nawet z późnym wiązaniem lub bez danych.</span><span class="sxs-lookup"><span data-stu-id="98c01-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="98c01-113">Usługi danych WCF zawiera również zestaw bibliotek klienta dla głównej aplikacji klienta programu .NET Framework i inny wpis specjalnie dla aplikacji opartych na technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="98c01-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="98c01-114">Tych bibliotek klienckich zapewnia model programowania oparty na obiekt, gdy uzyskujesz dostęp do źródła danych ze środowisk, takich jak .NET Framework lub Silverlight jako technologii OData.</span><span class="sxs-lookup"><span data-stu-id="98c01-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="98c01-115">Gdzie mam zacząć?</span><span class="sxs-lookup"><span data-stu-id="98c01-115">Where Should I Start?</span></span>

<span data-ttu-id="98c01-116">W zależności od zainteresowaniach należy rozważyć wprowadzenie do usługi danych WCF w jeden z następujących tematów.</span><span class="sxs-lookup"><span data-stu-id="98c01-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="98c01-117">Chcę, aby przejść bezpośrednio...</span><span class="sxs-lookup"><span data-stu-id="98c01-117">I want to jump right in...</span></span>

-   [<span data-ttu-id="98c01-118">Szybki start</span><span class="sxs-lookup"><span data-stu-id="98c01-118">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [<span data-ttu-id="98c01-119">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="98c01-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

-   [<span data-ttu-id="98c01-120">Szybki start Silverlight</span><span class="sxs-lookup"><span data-stu-id="98c01-120">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [<span data-ttu-id="98c01-121">Szybki start Silverlight dla systemu Windows Phone rozwoju</span><span class="sxs-lookup"><span data-stu-id="98c01-121">Silverlight Quickstart for Windows Phone Development</span></span>](https://go.microsoft.com/fwlink/?LinkID=214535)

<span data-ttu-id="98c01-122">Po prostu Pokaż kodu...</span><span class="sxs-lookup"><span data-stu-id="98c01-122">Just show me some code...</span></span>

-   [<span data-ttu-id="98c01-123">Szybki start</span><span class="sxs-lookup"><span data-stu-id="98c01-123">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [<span data-ttu-id="98c01-124">Instrukcje: Wykonywanie zapytań usługi danych</span><span class="sxs-lookup"><span data-stu-id="98c01-124">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

-   [<span data-ttu-id="98c01-125">Instrukcje: Wiązanie danych do elementów systemu Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="98c01-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="98c01-126">Chcę dowiedzieć się więcej o OData...</span><span class="sxs-lookup"><span data-stu-id="98c01-126">I want to know more about OData...</span></span>

 -   [<span data-ttu-id="98c01-127">Oficjalny dokument: Wprowadzenie do protokołu OData</span><span class="sxs-lookup"><span data-stu-id="98c01-127">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [<span data-ttu-id="98c01-128">Otwórz witrynę sieci Web protokołu danych</span><span class="sxs-lookup"><span data-stu-id="98c01-128">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

-   [<span data-ttu-id="98c01-129">OData: zestaw SDK</span><span class="sxs-lookup"><span data-stu-id="98c01-129">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

-   [<span data-ttu-id="98c01-130">OData: Często zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="98c01-130">OData: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/?LinkId=185867)

<span data-ttu-id="98c01-131">Chcę obejrzeć niektóre filmy wideo...</span><span class="sxs-lookup"><span data-stu-id="98c01-131">I want to watch some videos...</span></span>

-   [<span data-ttu-id="98c01-132">Przewodnik dla początkujących do usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="98c01-132">Beginner's Guide to WCF Data Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=220864)

-   [<span data-ttu-id="98c01-133">Filmy dla deweloperów usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="98c01-133">WCF Data Services Developer Videos</span></span>](https://go.microsoft.com/fwlink/?LinkId=220861)

-   [<span data-ttu-id="98c01-134">OData: Witryny sieci Web deweloperów</span><span class="sxs-lookup"><span data-stu-id="98c01-134">OData: Developers Web site</span></span>](https://go.microsoft.com/fwlink/?LinkId=185866)

<span data-ttu-id="98c01-135">Chcę wyświetlić przykłady end-to-end...</span><span class="sxs-lookup"><span data-stu-id="98c01-135">I want to see end-to-end samples...</span></span>

-   [<span data-ttu-id="98c01-136">Usługi WCF Data Services — przykłady dokumentacji w galerii przykładów MSDN</span><span class="sxs-lookup"><span data-stu-id="98c01-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkID=220865)

-   [<span data-ttu-id="98c01-137">Inne usługi WCF Data Services — przykłady w galerii przykładów MSDN</span><span class="sxs-lookup"><span data-stu-id="98c01-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkId=220866)

-   [<span data-ttu-id="98c01-138">OData: zestaw SDK</span><span class="sxs-lookup"><span data-stu-id="98c01-138">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

<span data-ttu-id="98c01-139">Jak można je zintegrować z programem Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="98c01-139">How does it integrate with Visual Studio?</span></span>

-   [<span data-ttu-id="98c01-140">Generowanie biblioteki klienta usługi danych</span><span class="sxs-lookup"><span data-stu-id="98c01-140">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)

-   [<span data-ttu-id="98c01-141">Tworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="98c01-141">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

-   [<span data-ttu-id="98c01-142">Dostawca programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="98c01-142">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="98c01-143">Co można zrobić z nim?</span><span class="sxs-lookup"><span data-stu-id="98c01-143">What can I do with it?</span></span>

-   [<span data-ttu-id="98c01-144">Omówienie</span><span class="sxs-lookup"><span data-stu-id="98c01-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

-   [<span data-ttu-id="98c01-145">Oficjalny dokument: Wprowadzenie do protokołu OData</span><span class="sxs-lookup"><span data-stu-id="98c01-145">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [<span data-ttu-id="98c01-146">Scenariusze aplikacji</span><span class="sxs-lookup"><span data-stu-id="98c01-146">Application Scenarios</span></span>](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)

<span data-ttu-id="98c01-147">Chcę użyć Silverlight...</span><span class="sxs-lookup"><span data-stu-id="98c01-147">I want to use Silverlight...</span></span>

-   [<span data-ttu-id="98c01-148">Szybki start Silverlight</span><span class="sxs-lookup"><span data-stu-id="98c01-148">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [<span data-ttu-id="98c01-149">WCF Data Services (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="98c01-149">WCF Data Services (Silverlight)</span></span>](https://go.microsoft.com/fwlink/?LinkID=143149)

-   [<span data-ttu-id="98c01-150">Wprowadzenie do programu Silverlight</span><span class="sxs-lookup"><span data-stu-id="98c01-150">Getting Started with Silverlight</span></span>](https://go.microsoft.com/fwlink/?LinkId=148366)

<span data-ttu-id="98c01-151">Chcę użyć LINQ...</span><span class="sxs-lookup"><span data-stu-id="98c01-151">I want to use LINQ...</span></span>

-   [<span data-ttu-id="98c01-152">Wykonywanie zapytań do usługi danych</span><span class="sxs-lookup"><span data-stu-id="98c01-152">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)

-   [<span data-ttu-id="98c01-153">Zagadnienia dotyczące LINQ</span><span class="sxs-lookup"><span data-stu-id="98c01-153">LINQ Considerations</span></span>](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

-   [<span data-ttu-id="98c01-154">Instrukcje: Wykonywanie zapytań usługi danych</span><span class="sxs-lookup"><span data-stu-id="98c01-154">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="98c01-155">Mi nadal potrzebne pewne dodatkowe informacje...</span><span class="sxs-lookup"><span data-stu-id="98c01-155">I still need some more information...</span></span>

-   [<span data-ttu-id="98c01-156">Blog zespołu usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="98c01-156">WCF Data Services Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=150511)

-   [<span data-ttu-id="98c01-157">Zasoby</span><span class="sxs-lookup"><span data-stu-id="98c01-157">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

-   [<span data-ttu-id="98c01-158">Centrum deweloperów usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="98c01-158">WCF Data Services Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=220868)

-   [<span data-ttu-id="98c01-159">Otwórz witrynę sieci Web protokołu danych</span><span class="sxs-lookup"><span data-stu-id="98c01-159">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a><span data-ttu-id="98c01-160">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="98c01-160">In This Section</span></span>

 [<span data-ttu-id="98c01-161">Omówienie</span><span class="sxs-lookup"><span data-stu-id="98c01-161">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

 <span data-ttu-id="98c01-162">Zawiera omówienie funkcji i funkcji dostępnych w usługach danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="98c01-162">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

 [<span data-ttu-id="98c01-163">What's New in usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="98c01-163">What's New in WCF Data Services</span></span>](https://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)

 <span data-ttu-id="98c01-164">W tym artykule opisano nowe funkcje w usługach danych programu WCF i obsługę nowych funkcji OData.</span><span class="sxs-lookup"><span data-stu-id="98c01-164">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

 [<span data-ttu-id="98c01-165">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="98c01-165">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

 <span data-ttu-id="98c01-166">Zawiera opis sposobu prezentowania i wykorzystywania źródeł danych usługi OData przy użyciu usługi danych WCF.</span><span class="sxs-lookup"><span data-stu-id="98c01-166">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

 [<span data-ttu-id="98c01-167">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="98c01-167">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)

 <span data-ttu-id="98c01-168">W tym artykule opisano sposób tworzenia i konfigurowania usługi danych, która udostępnia źródłami danych OData.</span><span class="sxs-lookup"><span data-stu-id="98c01-168">Describes how to create and configure a data service that exposes OData feeds.</span></span>

 [<span data-ttu-id="98c01-169">Biblioteka klienta usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="98c01-169">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)

 <span data-ttu-id="98c01-170">W tym artykule opisano, jak używać tych źródeł od aplikacji klienckiej .NET Framework za pomocą biblioteki klienta.</span><span class="sxs-lookup"><span data-stu-id="98c01-170">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="98c01-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98c01-171">See Also</span></span>

- [<span data-ttu-id="98c01-172">Representational State Transfer (REST)</span><span class="sxs-lookup"><span data-stu-id="98c01-172">Representational State Transfer (REST)</span></span>](https://go.microsoft.com/fwlink/?LinkId=113919)
