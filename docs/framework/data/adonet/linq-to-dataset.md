---
title: LINQ do DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 75ab1e733915349c64742e1a9c1142cad988ade0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-dataset"></a><span data-ttu-id="c822a-102">LINQ do DataSet</span><span class="sxs-lookup"><span data-stu-id="c822a-102">LINQ to DataSet</span></span>
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="c822a-103">umożliwia łatwiejsze i szybsze zapytania za pośrednictwem danych w pamięci podręcznej <xref:System.Data.DataSet> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c822a-103"> makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="c822a-104">W szczególności [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] upraszcza zapytań umożliwia deweloperom pisać zapytania od języka programowania, a nie przy użyciu języka osobne zapytania.</span><span class="sxs-lookup"><span data-stu-id="c822a-104">Specifically, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="c822a-105">Jest to szczególnie przydatne w przypadku [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] deweloperów, którzy mogą teraz wykorzystać sprawdzanie składni kompilacji, wpisując statycznych, i obsługę funkcji IntelliSense udostępniane przez [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] w swoich zapytań.</span><span class="sxs-lookup"><span data-stu-id="c822a-105">This is especially useful for [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] in their queries.</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="c822a-106">może również służyć do zapytanie dotyczące danych, które zostały skonsolidowane z jednego lub więcej źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="c822a-106"> can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="c822a-107">Dzięki temu wiele scenariuszy, które wymagają elastyczność jak dane są reprezentowane i obsługi, takie jak wykonywanie kwerend lokalnie zagregowanych danych i warstwy środkowej buforowanie w aplikacjach sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c822a-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="c822a-108">W szczególności ogólnego raportowania, analizy i aplikacji analizy biznesowej wymagają tej metody manipulacji.</span><span class="sxs-lookup"><span data-stu-id="c822a-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="c822a-109">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Funkcji jest uwidaczniana, przede wszystkim za pośrednictwem metody rozszerzenia w <xref:System.Data.DataRowExtensions> i <xref:System.Data.DataTableExtensions> klasy.</span><span class="sxs-lookup"><span data-stu-id="c822a-109">The [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="c822a-110">oparty na i wykorzystuje istniejące [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architektury, a nie jako zamiennik [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c822a-110"> builds on and uses the existing [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architecture, and is not meant to replace [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] in application code.</span></span> <span data-ttu-id="c822a-111">Istniejący kod ADO.NET 2.0 będą nadal działać w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c822a-111">Existing ADO.NET 2.0 code will continue to function in a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] application.</span></span> <span data-ttu-id="c822a-112">Relacja z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] do [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] i magazynu danych przedstawiono na poniższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="c822a-112">The relationship of [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] and the data store is illustrated in the following diagram.</span></span>  
  
 <span data-ttu-id="c822a-113">![LINQ do DataSet jest oparta na dostawcy ADO.NET](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span><span class="sxs-lookup"><span data-stu-id="c822a-113">![LINQ to DataSet is based on the ADO.NET Provider](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c822a-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c822a-114">In This Section</span></span>  
 [<span data-ttu-id="c822a-115">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="c822a-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="c822a-116">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="c822a-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="c822a-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="c822a-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="c822a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c822a-118">See Also</span></span>  
 [<span data-ttu-id="c822a-119">LINQ (zapytania o języku zintegrowanym)</span><span class="sxs-lookup"><span data-stu-id="c822a-119">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="c822a-120">LINQ i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c822a-120">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [<span data-ttu-id="c822a-121">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c822a-121">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
