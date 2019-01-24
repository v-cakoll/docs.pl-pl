---
title: Usługi danych WCF 4.5
ms.date: 03/30/2017
helpviewer_keywords:
  - Astoria
  - 'WCF Data Services, getting started'
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="de68b-102">Usługi danych WCF 4.5</span><span class="sxs-lookup"><span data-stu-id="de68b-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="de68b-103">Usługi danych WCF (wcześniej znane jako "Architektury ADO.NET Data Services") jest składnikiem programu .NET Framework, która umożliwia tworzenie usług, które używają [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] do prezentowania i wykorzystywania danych w Internecie lub intranecie przy użyciu semantyki [ (REST) Representational state transfer](https://go.microsoft.com/fwlink/?LinkId=113919).</span><span class="sxs-lookup"><span data-stu-id="de68b-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span></span> <span data-ttu-id="de68b-104">OData przedstawia dane w postaci zasobów, które są adresowane przez identyfikatory URI.</span><span class="sxs-lookup"><span data-stu-id="de68b-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="de68b-105">Dane są dostępne i zmieniać przy użyciu standardowych poleceń HTTP elementu GET, PUT, POST i DELETE.</span><span class="sxs-lookup"><span data-stu-id="de68b-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="de68b-106">OData używa konwencji Relacja jednostki [modelu Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) aby uwidocznić zasoby jako zestawów jednostek, które są powiązane przez skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="de68b-106">OData uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="de68b-107">Usługi danych WCF korzysta z protokołu OData do adresowania i aktualizowania zasobów.</span><span class="sxs-lookup"><span data-stu-id="de68b-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="de68b-108">W ten sposób uzyskujesz dostęp do tych usług, za pomocą dowolnego klienta, który obsługuje OData.</span><span class="sxs-lookup"><span data-stu-id="de68b-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="de68b-109">OData pozwala na żądanie i zapisywania danych do zasobów przy użyciu dobrze znanych transferu formatów: Atom, zestaw standardów wymianę i aktualizowanie danych w formacie XML i JavaScript Object Notation (JSON), formatem wymiany danych tekstowych, często używane w aplikacji interfejsu AJAX.</span><span class="sxs-lookup"><span data-stu-id="de68b-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX application.</span></span>

<span data-ttu-id="de68b-110">Usługi danych WCF można ujawnić dane, które pochodzą z różnych źródeł, jako źródła OData.</span><span class="sxs-lookup"><span data-stu-id="de68b-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="de68b-111">Narzędzia programu Visual Studio ułatwiają tworzenie usługi OData przy użyciu modelu danych ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="de68b-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="de68b-112">Można również utworzyć źródła danych OData na podstawie wspólnej klasy środowiska uruchomieniowego (języka wspólnego CLR) języka i nawet z późnym wiązaniem lub bez danych.</span><span class="sxs-lookup"><span data-stu-id="de68b-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="de68b-113">Usługi danych WCF zawiera również zestaw bibliotek klienta dla głównej aplikacji klienta programu .NET Framework i inny wpis specjalnie dla aplikacji opartych na technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="de68b-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="de68b-114">Tych bibliotek klienckich zapewnia model programowania oparty na obiekt, gdy uzyskujesz dostęp do źródła danych ze środowisk, takich jak .NET Framework lub Silverlight jako technologii OData.</span><span class="sxs-lookup"><span data-stu-id="de68b-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="de68b-115">Gdzie mam zacząć?</span><span class="sxs-lookup"><span data-stu-id="de68b-115">Where Should I Start?</span></span>

<span data-ttu-id="de68b-116">W zależności od zainteresowaniach należy rozważyć wprowadzenie do usługi danych WCF w jeden z następujących tematów.</span><span class="sxs-lookup"><span data-stu-id="de68b-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="de68b-117">Chcę, aby przejść bezpośrednio...</span><span class="sxs-lookup"><span data-stu-id="de68b-117">I want to jump right in...</span></span>

-   [<span data-ttu-id="de68b-118">Szybki start</span><span class="sxs-lookup"><span data-stu-id="de68b-118">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [<span data-ttu-id="de68b-119">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="de68b-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

-   [<span data-ttu-id="de68b-120">Szybki start Silverlight</span><span class="sxs-lookup"><span data-stu-id="de68b-120">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [<span data-ttu-id="de68b-121">Szybki start Silverlight dla systemu Windows Phone rozwoju</span><span class="sxs-lookup"><span data-stu-id="de68b-121">Silverlight Quickstart for Windows Phone Development</span></span>](https://go.microsoft.com/fwlink/?LinkID=214535)

<span data-ttu-id="de68b-122">Po prostu Pokaż kodu...</span><span class="sxs-lookup"><span data-stu-id="de68b-122">Just show me some code...</span></span>

-   [<span data-ttu-id="de68b-123">Szybki start</span><span class="sxs-lookup"><span data-stu-id="de68b-123">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [<span data-ttu-id="de68b-124">Instrukcje: Wykonywanie zapytań usługi danych</span><span class="sxs-lookup"><span data-stu-id="de68b-124">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

-   [<span data-ttu-id="de68b-125">Instrukcje: Powiąż dane z programu Windows Presentation Foundation elementów</span><span class="sxs-lookup"><span data-stu-id="de68b-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="de68b-126">Chcę dowiedzieć się więcej o OData...</span><span class="sxs-lookup"><span data-stu-id="de68b-126">I want to know more about OData...</span></span>

 -   [<span data-ttu-id="de68b-127">Oficjalny dokument: Wprowadzenie do protokołu OData</span><span class="sxs-lookup"><span data-stu-id="de68b-127">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [<span data-ttu-id="de68b-128">Otwórz witrynę sieci Web protokołu danych</span><span class="sxs-lookup"><span data-stu-id="de68b-128">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

-   [<span data-ttu-id="de68b-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="de68b-129">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

-   [<span data-ttu-id="de68b-130">OData: Często zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="de68b-130">OData: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/?LinkId=185867)

<span data-ttu-id="de68b-131">Chcę obejrzeć niektóre filmy wideo...</span><span class="sxs-lookup"><span data-stu-id="de68b-131">I want to watch some videos...</span></span>

-   [<span data-ttu-id="de68b-132">Przewodnik dla początkujących do usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="de68b-132">Beginner's Guide to WCF Data Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=220864)

-   [<span data-ttu-id="de68b-133">Filmy dla deweloperów usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="de68b-133">WCF Data Services Developer Videos</span></span>](https://go.microsoft.com/fwlink/?LinkId=220861)

-   [<span data-ttu-id="de68b-134">OData: Witryny sieci Web deweloperów</span><span class="sxs-lookup"><span data-stu-id="de68b-134">OData: Developers Web site</span></span>](https://go.microsoft.com/fwlink/?LinkId=185866)

<span data-ttu-id="de68b-135">Chcę wyświetlić przykłady end-to-end...</span><span class="sxs-lookup"><span data-stu-id="de68b-135">I want to see end-to-end samples...</span></span>

-   [<span data-ttu-id="de68b-136">Usługi WCF Data Services — przykłady dokumentacji w galerii przykładów MSDN</span><span class="sxs-lookup"><span data-stu-id="de68b-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkID=220865)

-   [<span data-ttu-id="de68b-137">Inne usługi WCF Data Services — przykłady w galerii przykładów MSDN</span><span class="sxs-lookup"><span data-stu-id="de68b-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkId=220866)

-   [<span data-ttu-id="de68b-138">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="de68b-138">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

<span data-ttu-id="de68b-139">Jak można je zintegrować z programem Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="de68b-139">How does it integrate with Visual Studio?</span></span>

-   [<span data-ttu-id="de68b-140">Generowanie biblioteki klienta usługi danych</span><span class="sxs-lookup"><span data-stu-id="de68b-140">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)

-   [<span data-ttu-id="de68b-141">Tworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="de68b-141">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

-   [<span data-ttu-id="de68b-142">Dostawca programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="de68b-142">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="de68b-143">Co można zrobić z nim?</span><span class="sxs-lookup"><span data-stu-id="de68b-143">What can I do with it?</span></span>

-   [<span data-ttu-id="de68b-144">Omówienie</span><span class="sxs-lookup"><span data-stu-id="de68b-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

-   [<span data-ttu-id="de68b-145">Oficjalny dokument: Wprowadzenie do protokołu OData</span><span class="sxs-lookup"><span data-stu-id="de68b-145">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [<span data-ttu-id="de68b-146">Scenariusze aplikacji</span><span class="sxs-lookup"><span data-stu-id="de68b-146">Application Scenarios</span></span>](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)

<span data-ttu-id="de68b-147">Chcę użyć Silverlight...</span><span class="sxs-lookup"><span data-stu-id="de68b-147">I want to use Silverlight...</span></span>

-   [<span data-ttu-id="de68b-148">Szybki start Silverlight</span><span class="sxs-lookup"><span data-stu-id="de68b-148">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [<span data-ttu-id="de68b-149">WCF Data Services (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="de68b-149">WCF Data Services (Silverlight)</span></span>](https://go.microsoft.com/fwlink/?LinkID=143149)

-   [<span data-ttu-id="de68b-150">Wprowadzenie do programu Silverlight</span><span class="sxs-lookup"><span data-stu-id="de68b-150">Getting Started with Silverlight</span></span>](https://go.microsoft.com/fwlink/?LinkId=148366)

<span data-ttu-id="de68b-151">Chcę użyć LINQ...</span><span class="sxs-lookup"><span data-stu-id="de68b-151">I want to use LINQ...</span></span>

-   [<span data-ttu-id="de68b-152">Wykonywanie zapytań do usługi danych</span><span class="sxs-lookup"><span data-stu-id="de68b-152">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)

-   [<span data-ttu-id="de68b-153">Zagadnienia dotyczące LINQ</span><span class="sxs-lookup"><span data-stu-id="de68b-153">LINQ Considerations</span></span>](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

-   [<span data-ttu-id="de68b-154">Instrukcje: Wykonywanie zapytań usługi danych</span><span class="sxs-lookup"><span data-stu-id="de68b-154">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="de68b-155">Mi nadal potrzebne pewne dodatkowe informacje...</span><span class="sxs-lookup"><span data-stu-id="de68b-155">I still need some more information...</span></span>

-   [<span data-ttu-id="de68b-156">Blog zespołu usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="de68b-156">WCF Data Services Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=150511)

-   [<span data-ttu-id="de68b-157">Zasoby</span><span class="sxs-lookup"><span data-stu-id="de68b-157">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

-   [<span data-ttu-id="de68b-158">Centrum deweloperów usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="de68b-158">WCF Data Services Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=220868)

-   [<span data-ttu-id="de68b-159">Otwórz witrynę sieci Web protokołu danych</span><span class="sxs-lookup"><span data-stu-id="de68b-159">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a><span data-ttu-id="de68b-160">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="de68b-160">In This Section</span></span>

 [<span data-ttu-id="de68b-161">Omówienie</span><span class="sxs-lookup"><span data-stu-id="de68b-161">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

 <span data-ttu-id="de68b-162">Zawiera omówienie funkcji i funkcji dostępnych w usługach danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="de68b-162">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

 [<span data-ttu-id="de68b-163">What's New in usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="de68b-163">What's New in WCF Data Services</span></span>](https://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)

 <span data-ttu-id="de68b-164">W tym artykule opisano nowe funkcje w usługach danych programu WCF i obsługę nowych funkcji OData.</span><span class="sxs-lookup"><span data-stu-id="de68b-164">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

 [<span data-ttu-id="de68b-165">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="de68b-165">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

 <span data-ttu-id="de68b-166">Zawiera opis sposobu prezentowania i wykorzystywania źródeł danych usługi OData przy użyciu usługi danych WCF.</span><span class="sxs-lookup"><span data-stu-id="de68b-166">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

 [<span data-ttu-id="de68b-167">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="de68b-167">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)

 <span data-ttu-id="de68b-168">W tym artykule opisano sposób tworzenia i konfigurowania usługi danych, która udostępnia źródłami danych OData.</span><span class="sxs-lookup"><span data-stu-id="de68b-168">Describes how to create and configure a data service that exposes OData feeds.</span></span>

 [<span data-ttu-id="de68b-169">Biblioteka klienta usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="de68b-169">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)

 <span data-ttu-id="de68b-170">W tym artykule opisano, jak używać tych źródeł od aplikacji klienckiej .NET Framework za pomocą biblioteki klienta.</span><span class="sxs-lookup"><span data-stu-id="de68b-170">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="de68b-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de68b-171">See also</span></span>

- [<span data-ttu-id="de68b-172">Representational State Transfer (REST)</span><span class="sxs-lookup"><span data-stu-id="de68b-172">Representational State Transfer (REST)</span></span>](https://go.microsoft.com/fwlink/?LinkId=113919)
