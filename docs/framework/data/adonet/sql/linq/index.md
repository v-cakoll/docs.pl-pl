---
title: LINQ do SQL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 62f7a3b0fcefa9eb6f5b56d96217a9988a193104
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="linq-to-sql"></a><span data-ttu-id="576f7-102">LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="576f7-102">LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="576f7-103">wchodzi w skład [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] wersji 3.5, która zapewnia infrastrukturę środowiska wykonawczego do zarządzania jako obiekty relacyjnej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="576f7-103"> is a component of [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] version 3.5 that provides a run-time infrastructure for managing relational data as objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="576f7-104">Danych relacyjnych pojawia się jako kolekcja tabel dwuwymiarowa (*relacji* lub *płaskim pliki*), gdzie wspólnych kolumn są tabele powiązane ze sobą.</span><span class="sxs-lookup"><span data-stu-id="576f7-104">Relational data appears as a collection of two-dimensional tables (*relations* or *flat files*), where common columns relate tables to each other.</span></span> <span data-ttu-id="576f7-105">Aby użyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] efektywnie musi posiadać pewną znajomość podstawowych zasad relacyjnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="576f7-105">To use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] effectively, you must have some familiarity with the underlying principles of relational databases.</span></span>  
  
 <span data-ttu-id="576f7-106">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], modelu danych relacyjnej bazy danych jest mapowany na model obiektowy wyrażone w języku programowania dewelopera.</span><span class="sxs-lookup"><span data-stu-id="576f7-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="576f7-107">Po uruchomieniu aplikacji, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przekłada się na SQL języku zintegrowanym zapytania w modelu obiektów i wysyła je do bazy danych do wykonania.</span><span class="sxs-lookup"><span data-stu-id="576f7-107">When the application runs, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates into SQL the language-integrated queries in the object model and sends them to the database for execution.</span></span> <span data-ttu-id="576f7-108">Gdy baza danych zwraca wyniki, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy je do obiektów, które można pracować w języku programowania.</span><span class="sxs-lookup"><span data-stu-id="576f7-108">When the database returns the results, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates them back to objects that you can work with in your own programming language.</span></span>  
  
 <span data-ttu-id="576f7-109">Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] jest zwykle używany [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], który udostępnia interfejs użytkownika wykonywania wielu funkcji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="576f7-109">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], which provides a user interface for implementing many of the features of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="576f7-110">Dokumentacji, która jest zawarta w tej wersji programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] opisano podstawowe bloki konstrukcyjne, procesów i techniki potrzebne do tworzenia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="576f7-110">The documentation that is included with this release of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] describes the basic building blocks, processes, and techniques you need for building [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="576f7-111">Możesz również wyszukać Microsoft Docs określonych problemów i mogą uczestniczyć w [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), gdzie można omawiać bardziej złożonych tematów szczegółowo z ekspertami.</span><span class="sxs-lookup"><span data-stu-id="576f7-111">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="576f7-112">Na koniec [LINQ do SQL: .NET Language-Integrated zapytania dla danych relacyjnych](http://go.microsoft.com/fwlink/?LinkId=93205) oficjalny dokument zawierający szczegóły [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologii, wraz z [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] i przykładów kodu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="576f7-112">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="576f7-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="576f7-113">In This Section</span></span>  
 [<span data-ttu-id="576f7-114">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="576f7-114">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 <span data-ttu-id="576f7-115">Zawiera omówienie skrócone [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wraz z informacjami o tym, jak rozpocząć pracę przy użyciu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="576f7-115">Provides a condensed overview of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] along with information about how to get started using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="576f7-116">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="576f7-116">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="576f7-117">Zawiera opis czynności mapowania, zapytanie, aktualizowanie, debugowanie i podobne zadania.</span><span class="sxs-lookup"><span data-stu-id="576f7-117">Provides steps for mapping, querying, updating, debugging, and similar tasks.</span></span>  
  
 [<span data-ttu-id="576f7-118">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="576f7-118">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 <span data-ttu-id="576f7-119">Udostępnia informacje na temat kilka aspektów [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="576f7-119">Provides reference information about several aspects of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="576f7-120">Tematy zawierają mapowanie typu środowiska CLR SQL, standardowe Translacja Operator zapytania i inne.</span><span class="sxs-lookup"><span data-stu-id="576f7-120">Topics include SQL-CLR Type Mapping, Standard Query Operator Translation, and more.</span></span>  
  
 [<span data-ttu-id="576f7-121">Przykłady</span><span class="sxs-lookup"><span data-stu-id="576f7-121">Samples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 <span data-ttu-id="576f7-122">Zawiera łącza do [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] i przykłady dotyczące języka C#.</span><span class="sxs-lookup"><span data-stu-id="576f7-122">Provides links to [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# samples.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="576f7-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="576f7-123">Related Sections</span></span>  
 [<span data-ttu-id="576f7-124">LINQ (zapytania o języku zintegrowanym)</span><span class="sxs-lookup"><span data-stu-id="576f7-124">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 <span data-ttu-id="576f7-125">Zawiera omówienie [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologii.</span><span class="sxs-lookup"><span data-stu-id="576f7-125">Provides an overview of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologies.</span></span>  
  
 [<span data-ttu-id="576f7-126">LINQ</span><span class="sxs-lookup"><span data-stu-id="576f7-126">LINQ</span></span>](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="576f7-127">W tym artykule opisano [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologii [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] użytkowników.</span><span class="sxs-lookup"><span data-stu-id="576f7-127">Describes [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologies for [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] users.</span></span>  
  
 [<span data-ttu-id="576f7-128">LINQ do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="576f7-128">LINQ to ADO.NET</span></span>](http://msdn.microsoft.com/library/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 <span data-ttu-id="576f7-129">Łączy się [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] portalu.</span><span class="sxs-lookup"><span data-stu-id="576f7-129">Links to the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] portal.</span></span>  
  
 [<span data-ttu-id="576f7-130">LINQ do SQL — wskazówki</span><span class="sxs-lookup"><span data-stu-id="576f7-130">LINQ to SQL Walkthroughs</span></span>](http://msdn.microsoft.com/library/308e66ac-f704-4e00-9b4e-7af0045a2374)  
 <span data-ttu-id="576f7-131">Przedstawiono wskazówki dostępne dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="576f7-131">Lists walkthroughs available for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="576f7-132">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="576f7-132">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 <span data-ttu-id="576f7-133">Opisuje sposób pobierania przykładowe bazy danych używane w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="576f7-133">Describes how to download sample databases used in the documentation.</span></span>  
  
 [<span data-ttu-id="576f7-134">LinqDataSource Technology Overview</span><span class="sxs-lookup"><span data-stu-id="576f7-134">LinqDataSource Technology Overview</span></span>](http://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136)  
 <span data-ttu-id="576f7-135">Opisuje sposób <xref:System.Web.UI.WebControls.LinqDataSource> kontrolować ujawnia [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] dla deweloperów sieci Web za pośrednictwem [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] architektura formantu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="576f7-135">Describes how the <xref:System.Web.UI.WebControls.LinqDataSource> control exposes [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] to Web developers through the [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] data-source control architecture.</span></span>
