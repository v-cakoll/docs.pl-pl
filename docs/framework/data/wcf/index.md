---
title: "Usługi danych WCF 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d1ef95ac84872b2cc39ec3a93abab10c39cd7738
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="f389a-102">Usługi danych WCF 4.5</span><span class="sxs-lookup"><span data-stu-id="f389a-102">WCF Data Services 4.5</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="f389a-103">(wcześniej znane jako "Usług danych ADO.NET") jest składnikiem programu .NET Framework, która umożliwia tworzenie usług, które używają [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] do ujawnia i konsumowania danych za pośrednictwem sieci Web lub intranet przy użyciu semantykę [representational stanu Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919).</span><span class="sxs-lookup"><span data-stu-id="f389a-103"> (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919).</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="f389a-104">przedstawia dane w postaci zasobów, które są adresowane przez identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="f389a-104"> exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="f389a-105">Dane są dostępne i zmieniać przy użyciu standardowych poleceń HTTP z GET, PUT, POST i DELETE.</span><span class="sxs-lookup"><span data-stu-id="f389a-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="f389a-106">używa konwencji Relacja jednostki z [modelu Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) do udostępnienia zasobów jako zestawy jednostek, które są powiązane przez skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="f389a-106"> uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="f389a-107">używa [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu adresowania i aktualizowanie zasobów.</span><span class="sxs-lookup"><span data-stu-id="f389a-107"> uses the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocol for addressing and updating resources.</span></span> <span data-ttu-id="f389a-108">W ten sposób można dostępu tych usług za pomocą dowolnego klienta, który obsługuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f389a-108">In this way, you can access these services from any client that supports [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="f389a-109">pozwala na żądanie i zapisać dane do zasobów przy użyciu formatów transferowania dobrze znanego: Atom, zbiór standardów wymiany i aktualizowanie danych jako XML i JavaScript Object Notation (JSON), format wymiany danych tekstowych bardzo często używane w aplikacji interfejsu AJAX.</span><span class="sxs-lookup"><span data-stu-id="f389a-109"> enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX application.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="f389a-110">można ujawniać dane, które pochodzą z różnych źródeł jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="f389a-110"> can expose data that originates from various sources as [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span> <span data-ttu-id="f389a-111">Program Visual Studio tools ułatwiają tworzenie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie usługi przy użyciu modelu danych programu ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="f389a-111">Visual Studio tools make it easier for you to create an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="f389a-112">Można również utworzyć [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych na podstawie wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) klas i danych nawet późnym wiązaniem lub wyrażeniami bez typu.</span><span class="sxs-lookup"><span data-stu-id="f389a-112">You can also create [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="f389a-113">zawiera także zestaw bibliotek klienta, jedno dla aplikacji klienckich, ogólne .NET Framework i jedno specjalnie dla aplikacji opartych na technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="f389a-113"> also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="f389a-114">Te biblioteki klienta zapewniają model programowania obiektu, gdy uzyskujesz dostęp do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych ze środowisk, takich jak .NET Framework i Silverlight.</span><span class="sxs-lookup"><span data-stu-id="f389a-114">These client libraries provide an object-based programming model when you access an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from environments such as the .NET Framework and Silverlight.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="f389a-115">Gdzie powinna zaczynać?</span><span class="sxs-lookup"><span data-stu-id="f389a-115">Where Should I Start?</span></span>  
 <span data-ttu-id="f389a-116">W zależności od zainteresowania, należy rozważyć wprowadzenie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] w następujących tematach.</span><span class="sxs-lookup"><span data-stu-id="f389a-116">Depending on your interests, consider getting started with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] in one of the following topics.</span></span>  
  
 <span data-ttu-id="f389a-117">Chcę, aby od razu...</span><span class="sxs-lookup"><span data-stu-id="f389a-117">I want to jump right in…</span></span>  
 -   [<span data-ttu-id="f389a-118">Szybki Start</span><span class="sxs-lookup"><span data-stu-id="f389a-118">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [<span data-ttu-id="f389a-119">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f389a-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [<span data-ttu-id="f389a-120">Szybki start Silverlight</span><span class="sxs-lookup"><span data-stu-id="f389a-120">Silverlight Quickstart</span></span>](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [<span data-ttu-id="f389a-121">Szybki start Silverlight dla systemu Windows Phone programowanie</span><span class="sxs-lookup"><span data-stu-id="f389a-121">Silverlight Quickstart for Windows Phone Development</span></span>](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 <span data-ttu-id="f389a-122">Po prostu Pokaż kodu...</span><span class="sxs-lookup"><span data-stu-id="f389a-122">Just show me some code…</span></span>  
 -   [<span data-ttu-id="f389a-123">Szybki Start</span><span class="sxs-lookup"><span data-stu-id="f389a-123">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [<span data-ttu-id="f389a-124">Porady: wykonywanie zapytań usługi danych</span><span class="sxs-lookup"><span data-stu-id="f389a-124">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [<span data-ttu-id="f389a-125">Porady: wiązanie danych do systemu Windows Presentation Foundation elementów</span><span class="sxs-lookup"><span data-stu-id="f389a-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 <span data-ttu-id="f389a-126">Chcę, aby dowiedzieć się więcej o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]...</span><span class="sxs-lookup"><span data-stu-id="f389a-126">I want to know more about [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]…</span></span>  
 -   [<span data-ttu-id="f389a-127">Oficjalny dokument: Wprowadzenie do OData</span><span class="sxs-lookup"><span data-stu-id="f389a-127">Whitepaper: Introducing OData</span></span>](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [<span data-ttu-id="f389a-128">Otwórz witrynę sieci Web protokołu danych</span><span class="sxs-lookup"><span data-stu-id="f389a-128">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [<span data-ttu-id="f389a-129">OData: zestaw SDK</span><span class="sxs-lookup"><span data-stu-id="f389a-129">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [<span data-ttu-id="f389a-130">OData: Często zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="f389a-130">OData: Frequently Asked Questions</span></span>](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 <span data-ttu-id="f389a-131">Chcę obejrzeć wideo niektóre...</span><span class="sxs-lookup"><span data-stu-id="f389a-131">I want to watch some videos…</span></span>  
 -   [<span data-ttu-id="f389a-132">Przewodnik dla początkujących do usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="f389a-132">Beginner's Guide to WCF Data Services</span></span>](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [<span data-ttu-id="f389a-133">Filmy wideo dewelopera usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="f389a-133">WCF Data Services Developer Videos</span></span>](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [<span data-ttu-id="f389a-134">OData: Witryna sieci Web deweloperów</span><span class="sxs-lookup"><span data-stu-id="f389a-134">OData: Developers Web site</span></span>](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 <span data-ttu-id="f389a-135">Aby wyświetlić przykłady end-to-end</span><span class="sxs-lookup"><span data-stu-id="f389a-135">I want to see end-to-end samples</span></span>  
 -   [<span data-ttu-id="f389a-136">Przykłady dokumentacji w galerii przykładów MSDN usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="f389a-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [<span data-ttu-id="f389a-137">Inne WCF Data Services próbek w galerii przykładów MSDN</span><span class="sxs-lookup"><span data-stu-id="f389a-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](http://go.microsoft.com/fwlink/?LinkId=220866)  
  
-   [<span data-ttu-id="f389a-138">OData: zestaw SDK</span><span class="sxs-lookup"><span data-stu-id="f389a-138">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 <span data-ttu-id="f389a-139">Jak można je zintegrować z programem Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="f389a-139">How does it integrate with Visual Studio?</span></span>  
 -   [<span data-ttu-id="f389a-140">Generowanie biblioteki klienta usługi danych</span><span class="sxs-lookup"><span data-stu-id="f389a-140">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [<span data-ttu-id="f389a-141">Tworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="f389a-141">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [<span data-ttu-id="f389a-142">Dostawcy programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="f389a-142">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 <span data-ttu-id="f389a-143">Co można zrobić z nim?</span><span class="sxs-lookup"><span data-stu-id="f389a-143">What can I do with it?</span></span>  
 -   [<span data-ttu-id="f389a-144">Omówienie</span><span class="sxs-lookup"><span data-stu-id="f389a-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [<span data-ttu-id="f389a-145">Oficjalny dokument: Wprowadzenie do OData</span><span class="sxs-lookup"><span data-stu-id="f389a-145">Whitepaper: Introducing OData</span></span>](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [<span data-ttu-id="f389a-146">Scenariusze aplikacji</span><span class="sxs-lookup"><span data-stu-id="f389a-146">Application Scenarios</span></span>](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 <span data-ttu-id="f389a-147">Chcę użyć Silverlight...</span><span class="sxs-lookup"><span data-stu-id="f389a-147">I want to use Silverlight…</span></span>  
 -   [<span data-ttu-id="f389a-148">Szybki start Silverlight</span><span class="sxs-lookup"><span data-stu-id="f389a-148">Silverlight Quickstart</span></span>](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [<span data-ttu-id="f389a-149">Usługi danych WCF (platformy Silverlight)</span><span class="sxs-lookup"><span data-stu-id="f389a-149">WCF Data Services (Silverlight)</span></span>](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [<span data-ttu-id="f389a-150">Wprowadzenie do programu Silverlight</span><span class="sxs-lookup"><span data-stu-id="f389a-150">Getting Started with Silverlight</span></span>](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 <span data-ttu-id="f389a-151">Chcę utworzyć aplikację Windows Phone...</span><span class="sxs-lookup"><span data-stu-id="f389a-151">I want to create a Windows Phone application…</span></span>  
 -   [<span data-ttu-id="f389a-152">Szybki start Silverlight dla systemu Windows Phone programowanie</span><span class="sxs-lookup"><span data-stu-id="f389a-152">Silverlight Quickstart for Windows Phone Development</span></span>](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [<span data-ttu-id="f389a-153">Open Data Protocol (OData) klienta dla Windows Phone</span><span class="sxs-lookup"><span data-stu-id="f389a-153">Open Data Protocol (OData) Client for Windows Phone</span></span>](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 <span data-ttu-id="f389a-154">Chcę użyć LINQ...</span><span class="sxs-lookup"><span data-stu-id="f389a-154">I want to use LINQ…</span></span>  
 -   [<span data-ttu-id="f389a-155">Zapytanie usługi danych</span><span class="sxs-lookup"><span data-stu-id="f389a-155">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [<span data-ttu-id="f389a-156">Zagadnienia dotyczące LINQ</span><span class="sxs-lookup"><span data-stu-id="f389a-156">LINQ Considerations</span></span>](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [<span data-ttu-id="f389a-157">Porady: wykonywanie zapytań usługi danych</span><span class="sxs-lookup"><span data-stu-id="f389a-157">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 <span data-ttu-id="f389a-158">Wciąż potrzebuję więcej informacji...</span><span class="sxs-lookup"><span data-stu-id="f389a-158">I still need some more information…</span></span>  
 -   [<span data-ttu-id="f389a-159">Blog zespołu usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="f389a-159">WCF Data Services Team Blog</span></span>](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [<span data-ttu-id="f389a-160">Zasoby</span><span class="sxs-lookup"><span data-stu-id="f389a-160">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [<span data-ttu-id="f389a-161">Centrum deweloperów usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="f389a-161">WCF Data Services Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [<span data-ttu-id="f389a-162">Otwórz witrynę sieci Web protokołu danych</span><span class="sxs-lookup"><span data-stu-id="f389a-162">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a><span data-ttu-id="f389a-163">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f389a-163">In This Section</span></span>  
 [<span data-ttu-id="f389a-164">Omówienie</span><span class="sxs-lookup"><span data-stu-id="f389a-164">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 <span data-ttu-id="f389a-165">Zawiera omówienie funkcji i możliwości, które są dostępne w [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f389a-165">Provides an overview of the features and functionality available in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="f389a-166">What's New in usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="f389a-166">What's New in WCF Data Services</span></span>](http://msdn.microsoft.com/en-us/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 <span data-ttu-id="f389a-167">Zawiera opis nowych funkcji w [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] i obsługę nowych [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] funkcji.</span><span class="sxs-lookup"><span data-stu-id="f389a-167">Describes new functionality in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and support for new [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] features.</span></span>  
  
 [<span data-ttu-id="f389a-168">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f389a-168">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 <span data-ttu-id="f389a-169">Opisuje sposób ujawniać i korzystanie z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f389a-169">Describes how to expose and consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds by using [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="f389a-170">Definiowanie usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="f389a-170">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 <span data-ttu-id="f389a-171">Opisuje sposób tworzenia i konfigurowania usługi danych, który ujawnia [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="f389a-171">Describes how to create and configure a data service that exposes [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span>  
  
 [<span data-ttu-id="f389a-172">Biblioteka klienta usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="f389a-172">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 <span data-ttu-id="f389a-173">Informacje dotyczące używania bibliotek klienckich zużyje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł z aplikacją kliencką programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f389a-173">Describes how to use client libraries to consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds from a .NET Framework client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f389a-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f389a-174">See Also</span></span>  
 [<span data-ttu-id="f389a-175">Representational State Transfer (REST)</span><span class="sxs-lookup"><span data-stu-id="f389a-175">Representational State Transfer (REST)</span></span>](http://go.microsoft.com/fwlink/?LinkId=113919)
