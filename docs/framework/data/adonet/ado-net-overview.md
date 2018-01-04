---
title: "ADO.NET — omówienie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e18115e460bf546c2fd6263e4671457a3da68f65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="adonet-overview"></a><span data-ttu-id="a8387-102">ADO.NET — omówienie</span><span class="sxs-lookup"><span data-stu-id="a8387-102">ADO.NET Overview</span></span>
<span data-ttu-id="a8387-103">ADO.NET zapewnia spójny dostęp do źródeł danych, takich jak SQL Server i XML, a także do źródeł danych za pośrednictwem OLE DB i ODBC.</span><span class="sxs-lookup"><span data-stu-id="a8387-103">ADO.NET provides consistent access to data sources such as SQL Server and XML, and to data sources exposed through OLE DB and ODBC.</span></span> <span data-ttu-id="a8387-104">Udostępnianie danych aplikacji użytkownika umożliwia ADO.NET połączenia z tych źródeł danych i pobrać, obsługi i aktualizować danych, które zawierają.</span><span class="sxs-lookup"><span data-stu-id="a8387-104">Data-sharing consumer applications can use ADO.NET to connect to these data sources and retrieve, handle, and update the data that they contain.</span></span>  
  
 <span data-ttu-id="a8387-105">ADO.NET oddziela dostęp do danych z manipulowania danymi na osobne składniki, które mogą być używane pojedynczo lub w połączeniu.</span><span class="sxs-lookup"><span data-stu-id="a8387-105">ADO.NET separates data access from data manipulation into discrete components that can be used separately or in tandem.</span></span> <span data-ttu-id="a8387-106">ADO.NET zawiera dostawcy danych .NET Framework dla połączenia z bazą danych, wykonywania poleceń i pobierania wyników.</span><span class="sxs-lookup"><span data-stu-id="a8387-106">ADO.NET includes .NET Framework data providers for connecting to a database, executing commands, and retrieving results.</span></span> <span data-ttu-id="a8387-107">Wyniki są albo przetwarzane bezpośrednio, umieszczone w ADO.NET <xref:System.Data.DataSet> obiekt, aby zostać uwidoczniona dla użytkownika w sposób ad hoc, połączeniu z danymi z wielu źródeł lub przekazywane między warstwami.</span><span class="sxs-lookup"><span data-stu-id="a8387-107">Those results are either processed directly, placed in an ADO.NET <xref:System.Data.DataSet> object in order to be exposed to the user in an ad hoc manner, combined with data from multiple sources, or passed between tiers.</span></span> <span data-ttu-id="a8387-108">`DataSet` Obiektu można również użyć niezależnie od dostawcy danych .NET Framework do zarządzania dane lokalne aplikacji lub z XML.</span><span class="sxs-lookup"><span data-stu-id="a8387-108">The `DataSet` object can also be used independently of a .NET Framework data provider to manage data local to the application or sourced from XML.</span></span>  
  
 <span data-ttu-id="a8387-109">Klasy ADO.NET znajdują się w System.Data.dll i są zintegrowane z klasami XML w System.Xml.dll.</span><span class="sxs-lookup"><span data-stu-id="a8387-109">The ADO.NET classes are found in System.Data.dll, and are integrated with the XML classes found in System.Xml.dll.</span></span> <span data-ttu-id="a8387-110">Aby uzyskać przykładowy kod, który nawiązuje połączenie z bazą danych, pobiera dane z niego, a następnie wyświetla dane w oknie konsoli, zobacz [przykłady kodu ADO.NET](../../../../docs/framework/data/adonet/ado-net-code-examples.md).</span><span class="sxs-lookup"><span data-stu-id="a8387-110">For sample code that connects to a database, retrieves data from it, and then displays that data in a console window, see [ADO.NET Code Examples](../../../../docs/framework/data/adonet/ado-net-code-examples.md).</span></span>  
  
 <span data-ttu-id="a8387-111">ADO.NET zapewnia funkcje dla deweloperów, którzy napisać kod zarządzany, które są podobne do funkcji dla deweloperów model (COM) obiektu składnik macierzysty przez obiektów ADO (ActiveX Data).</span><span class="sxs-lookup"><span data-stu-id="a8387-111">ADO.NET provides functionality to developers who write managed code similar to the functionality provided to native component object model (COM) developers by ActiveX Data Objects (ADO).</span></span> <span data-ttu-id="a8387-112">Zalecane jest użycie ADO.NET, nie ADO do uzyskiwania dostępu do danych w aplikacjach .NET.</span><span class="sxs-lookup"><span data-stu-id="a8387-112">We recommend that you use ADO.NET, not ADO, for accessing data in your .NET applications.</span></span>  
  
 <span data-ttu-id="a8387-113">ADO.NET zapewnia najprostszą metodę dostępu do danych w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8387-113">ADO.NET provides the most direct method of data access within the .NET Framework.</span></span> <span data-ttu-id="a8387-114">Na wyższym poziomie abstrakcji, który umożliwia aplikacjom obsługę model koncepcyjny zamiast odpowiedni model magazynu, zobacz [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).</span><span class="sxs-lookup"><span data-stu-id="a8387-114">For a higher-level abstraction that allows applications to work against a conceptual model instead of the underlying storage model, see the [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).</span></span>  
  
 <span data-ttu-id="a8387-115">**Zasady zachowania poufności informacji**: zestawy System.Data.dll, System.Data.Design.dll System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll i System.Data.DataSetExtensions.dll nie rozróżnia danych prywatnych i prywatnej z systemem innym niż dane użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a8387-115">**Privacy Statement**: The System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll, and System.Data.DataSetExtensions.dll assemblies do not distinguish between a user's private data and non-private data.</span></span>  <span data-ttu-id="a8387-116">Te zestawy nie zbierania, przechowywania lub transportu danych prywatnych dowolnego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a8387-116">These assemblies do not collect, store, or transport any user's private data.</span></span> <span data-ttu-id="a8387-117">Jednak aplikacje innych firm mogą zbierać, przechowywania lub transportu prywatnych danych użytkownika za pomocą tych zestawów.</span><span class="sxs-lookup"><span data-stu-id="a8387-117">However, third-party applications might collect, store, or transport a user's private data using these assemblies.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8387-118">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a8387-118">In This Section</span></span>  
 [<span data-ttu-id="a8387-119">Architektura ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8387-119">ADO.NET Architecture</span></span>](../../../../docs/framework/data/adonet/ado-net-architecture.md)  
 <span data-ttu-id="a8387-120">Zawiera omówienie architektury i składników programu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a8387-120">Provides an overview of the architecture and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="a8387-121">Opcje technologii ADO.NET i wskazówki</span><span class="sxs-lookup"><span data-stu-id="a8387-121">ADO.NET Technology Options and Guidelines</span></span>](../../../../docs/framework/data/adonet/ado-net-technology-options-and-guidelines.md)  
 <span data-ttu-id="a8387-122">Zawiera opis produktów i technologii zawartych w platformę danych jednostki.</span><span class="sxs-lookup"><span data-stu-id="a8387-122">Describes the products and technologies included with the Entity Data Platform.</span></span>  
  
 [<span data-ttu-id="a8387-123">LINQ i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8387-123">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 <span data-ttu-id="a8387-124">W tym artykule opisano, jak język Language-Integrated zapytania (LINQ) jest zaimplementowana w ADO.NET oraz linki do powiązanych tematów.</span><span class="sxs-lookup"><span data-stu-id="a8387-124">Describes how Language-Integrated Query (LINQ) is implemented in ADO.NET and provides links to relevant topics.</span></span>  
  
 [<span data-ttu-id="a8387-125">Dostawcy danych .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a8387-125">.NET Framework Data Providers</span></span>](../../../../docs/framework/data/adonet/data-providers.md)  
 <span data-ttu-id="a8387-126">Omówienie projektowania dostawcy danych .NET Framework i dostawców danych .NET Framework, które są dołączone do ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a8387-126">Provides an overview of the design of the .NET Framework data provider and of the .NET Framework data providers that are included with ADO.NET.</span></span>  
  
 [<span data-ttu-id="a8387-127">Zestawy danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8387-127">ADO.NET DataSets</span></span>](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 <span data-ttu-id="a8387-128">Zawiera omówienie `DataSet` projektowania i składniki.</span><span class="sxs-lookup"><span data-stu-id="a8387-128">Provides an overview of the `DataSet` design and components.</span></span>  
  
 [<span data-ttu-id="a8387-129">Wykonywanie równoczesne w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8387-129">Side-by-Side Execution in ADO.NET</span></span>](../../../../docs/framework/data/adonet/side-by-side-execution.md)  
 <span data-ttu-id="a8387-130">W tym artykule omówiono różnice w wersji ADO.NET i ich wpływ na wykonanie side-by-side oraz zgodności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a8387-130">Discusses differences in ADO.NET versions and their effect on side-by-side execution and application compatibility.</span></span>  
  
 [<span data-ttu-id="a8387-131">Przykłady kodu ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8387-131">ADO.NET Code Examples</span></span>](../../../../docs/framework/data/adonet/ado-net-code-examples.md)  
 <span data-ttu-id="a8387-132">Zawiera przykłady kodu, które służą do pobierania danych przy użyciu dostawcy danych ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a8387-132">Provides code samples that retrieve data using the ADO.NET data providers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a8387-133">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a8387-133">Related Sections</span></span>  
 [<span data-ttu-id="a8387-134">Nowości w programie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8387-134">What's New in ADO.NET</span></span>](../../../../docs/framework/data/adonet/whats-new.md)  
 <span data-ttu-id="a8387-135">Zawiera funkcje, które są nowością w programie [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8387-135">Introduces features that are new in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 [<span data-ttu-id="a8387-136">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8387-136">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="a8387-137">Opisuje bezpieczne praktyk kodowania, przy użyciu pakietu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a8387-137">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="a8387-138">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8387-138">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 <span data-ttu-id="a8387-139">Opisuje mapowanie typu danych między typami danych .NET Framework i dostawcy danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8387-139">Describes data type mappings between .NET Framework data types and the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="a8387-140">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8387-140">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="a8387-141">Informacje dotyczące połączenia ze źródłem danych, pobieranie danych i modyfikowania danych.</span><span class="sxs-lookup"><span data-stu-id="a8387-141">Describes how to connect to a data source, retrieve data, and modify data.</span></span> <span data-ttu-id="a8387-142">Obejmuje to `DataReaders` i `DataAdapters`.</span><span class="sxs-lookup"><span data-stu-id="a8387-142">This includes `DataReaders` and `DataAdapters`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8387-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8387-143">See Also</span></span>  
 [<span data-ttu-id="a8387-144">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8387-144">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="a8387-145">Uzyskiwanie dostępu do danych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a8387-145">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)  
 [<span data-ttu-id="a8387-146">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="a8387-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
