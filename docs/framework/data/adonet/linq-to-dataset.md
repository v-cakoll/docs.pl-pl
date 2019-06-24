---
title: LINQ do DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 36335f90c7850fa00a15e7112b7473637250c656
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306235"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="82239-102">LINQ do DataSet</span><span class="sxs-lookup"><span data-stu-id="82239-102">LINQ to DataSet</span></span>
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] <span data-ttu-id="82239-103">umożliwia łatwiejsze i szybsze zapytania przez dane buforowane w <xref:System.Data.DataSet> obiektu.</span><span class="sxs-lookup"><span data-stu-id="82239-103">makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="82239-104">W szczególności [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] upraszcza zapytań, dzięki czemu deweloperzy mogą pisać zapytania w języku programowania, a nie przy użyciu języka oddzielnego zapytania.</span><span class="sxs-lookup"><span data-stu-id="82239-104">Specifically, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="82239-105">Jest to szczególnie przydatne dla deweloperów programu Visual Studio, którzy mogą korzystać ze sprawdzania składni w czasie kompilacji, wpisując statycznych i IntelliSense pomoc techniczna jest świadczona przez program Visual Studio w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="82239-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] <span data-ttu-id="82239-106">może również służyć do wykonywania zapytań względem danych, który został dołączony z co najmniej jedno źródło danych.</span><span class="sxs-lookup"><span data-stu-id="82239-106">can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="82239-107">Dzięki temu wiele scenariuszy, które wymagają elastyczność w sposób dane są reprezentowane i obsługiwane, takich jak zapytania lokalnie zagregowanych danych i warstwy środkowej buforowanie w aplikacjach sieci Web.</span><span class="sxs-lookup"><span data-stu-id="82239-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="82239-108">W szczególności ogólne raportowanie, analiza i aplikacji analizy biznesowej wymagają tej metody do manipulowania.</span><span class="sxs-lookup"><span data-stu-id="82239-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="82239-109">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Funkcja jest widoczna przede wszystkim za pośrednictwem metody rozszerzające w <xref:System.Data.DataRowExtensions> i <xref:System.Data.DataTableExtensions> klasy.</span><span class="sxs-lookup"><span data-stu-id="82239-109">The [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] <span data-ttu-id="82239-110">opiera się na korzysta z istniejącej architektury ADO.NET i nie jest przeznaczona do zastąpienia ADO.NET w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82239-110">builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="82239-111">Istniejący kod ADO.NET będą w dalszym ciągu działać w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82239-111">Existing ADO.NET code will continue to function in a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] application.</span></span> <span data-ttu-id="82239-112">Relacje [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ADO.NET i danych magazynu jest zilustrowany na poniższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="82239-112">The relationship of [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![Diagram przedstawiający, że LINQ to DataSet jest oparty na dostawcy ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="82239-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="82239-114">In This Section</span></span>  
 [<span data-ttu-id="82239-115">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="82239-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="82239-116">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="82239-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="82239-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="82239-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="82239-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82239-118">See also</span></span>

- [<span data-ttu-id="82239-119">Zapytanie o języku zintegrowanym (LINQ) —C#</span><span class="sxs-lookup"><span data-stu-id="82239-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="82239-120">Zapytanie o języku zintegrowanym (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82239-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="82239-121">LINQ i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="82239-121">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [<span data-ttu-id="82239-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="82239-122">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
