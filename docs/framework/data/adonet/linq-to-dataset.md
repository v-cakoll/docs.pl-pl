---
title: LINQ do DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 4995512336ee9eb6e33df011757ed533db57e76e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783790"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="b6e56-102">LINQ do DataSet</span><span class="sxs-lookup"><span data-stu-id="b6e56-102">LINQ to DataSet</span></span>
<span data-ttu-id="b6e56-103">LINQ to DataSet ułatwia i przyspiesza wykonywanie zapytań dotyczących danych w pamięci podręcznej <xref:System.Data.DataSet> w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="b6e56-103">LINQ to DataSet makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="b6e56-104">W LINQ to DataSet upraszczają zapytania, umożliwiając deweloperom Pisanie zapytań w języku programowania, a nie za pomocą oddzielnego języka zapytań.</span><span class="sxs-lookup"><span data-stu-id="b6e56-104">Specifically, LINQ to DataSet simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="b6e56-105">Jest to szczególnie przydatne w przypadku deweloperów programu Visual Studio, którzy mogą teraz korzystać z sprawdzania składni w czasie kompilacji, pisania statycznego i obsługi technologii IntelliSense dostarczonych przez program Visual Studio w swoich zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="b6e56-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="b6e56-106">LINQ to DataSet można również użyć do wykonywania zapytań dotyczących danych, które zostały skonsolidowane z co najmniej jednego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b6e56-106">LINQ to DataSet can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="b6e56-107">Pozwala to na wiele scenariuszy, które wymagają elastyczności w zakresie reprezentowania i obsługi danych, takich jak wykonywanie zapytań dotyczących danych zagregowanych lokalnie i buforowanie warstwy środkowej w aplikacjach sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b6e56-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="b6e56-108">W szczególności, ogólne raporty, analizy i aplikacje analizy biznesowej wymagają tej metody manipulowania.</span><span class="sxs-lookup"><span data-stu-id="b6e56-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="b6e56-109">Funkcje LINQ to DataSet są udostępniane głównie przez metody rozszerzające w <xref:System.Data.DataRowExtensions> klasach i. <xref:System.Data.DataTableExtensions></span><span class="sxs-lookup"><span data-stu-id="b6e56-109">The LINQ to DataSet functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> <span data-ttu-id="b6e56-110">LINQ to DataSet kompiluje na platformie i używa istniejącej architektury ADO.NET i nie jest przeznaczony do zastępowania ADO.NET w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6e56-110">LINQ to DataSet builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="b6e56-111">Istniejący kod ADO.NET będzie nadal działać w aplikacji LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="b6e56-111">Existing ADO.NET code will continue to function in a LINQ to DataSet application.</span></span> <span data-ttu-id="b6e56-112">Relacja LINQ to DataSet do ADO.NET i magazyn danych przedstawiono na poniższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="b6e56-112">The relationship of LINQ to DataSet to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![Diagram przedstawiający, że LINQ to DataSet jest oparty na dostawcy ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="b6e56-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b6e56-114">In This Section</span></span>  
 [<span data-ttu-id="b6e56-115">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="b6e56-115">Getting Started</span></span>](getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="b6e56-116">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="b6e56-116">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="b6e56-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="b6e56-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="b6e56-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6e56-118">See also</span></span>

- [<span data-ttu-id="b6e56-119">Language-Integrated Query (LINQ) —C#</span><span class="sxs-lookup"><span data-stu-id="b6e56-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="b6e56-120">Zapytanie zintegrowane z językiem (LINQ) — Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b6e56-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="b6e56-121">LINQ i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6e56-121">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="b6e56-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6e56-122">ADO.NET</span></span>](index.md)
